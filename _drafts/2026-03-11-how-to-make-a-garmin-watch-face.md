---
slug: how-to-make-a-garmin-watch-face
layout: post
date: 2026-03-11
title: How to Make a Garmin Watch Face
description: A practical guide to building and publishing a custom Garmin watch face with Connect IQ and Monkey C
categories: garmin tutorial
image: /assets/posts/2025/cyberpunk/promo-image.png
github:
website:
---

Making a Garmin watch face is one of the more rewarding programming projects I've done. You get to wear something you built around on your wrist. In that sense it's much closer to the physical world than building a website — it shows up every time you check the time.

In this post I'll walk through everything I've learned from building the [Chinese Watch Face](/blog/2025/garmin-chinese-watchface/) and [Cyberpunk Watch Face](/blog/2025/garmin-cyberpunk-watchface/): environment setup, project structure, the drawing API, the quirks to watch out for, and how to publish to the Connect IQ store.

## Setup

### Monkey C and VSCode

Garmin watch faces are written in **Monkey C**, a proprietary language that looks and feels like a stripped-down version of Java. It has classes, methods, and a standard library (called `Toybox`) that gives you access to health data, weather, device sensors, and everything else you'd want to display on a watch face.

I recommend setting up in VSCode. Garmin publishes an official [Monkey C extension](https://marketplace.visualstudio.com/items?itemName=garmin.monkey-c) that gives you syntax highlighting, autocomplete, build commands, and the simulator — all in one place. You'll also need to install the **Connect IQ SDK** through the extension's SDK manager. Pick the latest stable version.

Some guides recommend using Eclipse. I'd skip it. The VSCode extension is well-maintained and significantly less painful.

Once installed, you can generate a new watch face project from the command palette: `Monkey C: Create a new project`. Select "Watch Face" as the app type. This scaffolds the folder structure for you.

### The Developer Account

To publish (and to run on a real device), you need a free Garmin developer account at [developer.garmin.com](https://developer.garmin.com). Once registered, you generate a developer key from the portal. The VSCode extension will prompt you for this key the first time you try to build.

## Project Structure

A Monkey C watch face project looks like this:

```
my-watch-face/
  manifest.xml
  monkey.jungle
  source/
    MyWatchFace.mc
    MyWatchFaceView.mc
  resources/
    drawables/
      drawables.xml
    fonts/
      fonts.xml
    images/
    strings/
      strings.xml
    properties.xml
    settings.xml
```

**`manifest.xml`** is the most important configuration file. It lists which Garmin devices your watch face supports, what permissions it needs (weather, heart rate, activity data, etc.), and metadata like the app name and version. You'll come back to this file often as you add features or expand device support.

**`monkey.jungle`** is the build configuration. This is where you map devices to resource folders, which is how you handle different screen sizes (more on this below).

**`source/`** contains your Monkey C code. The generated project gives you two files: an `Application` class that is the entry point, and a `View` class where all the drawing happens. You'll spend almost all your time in the View.

**`resources/`** contains everything that isn't code. Fonts, images, strings, and settings are all declared here in XML files.

## The Drawing API

The `View` class has three lifecycle methods you'll use:

```java
// Called once when the view is created. Use this to load resources.
function initialize() {}

// Called when the layout is set. Cache fonts, bitmaps, and dimensions here.
function onLayout(dc as Dc) as Void {}

// Called every second (or on demand). This is where you draw.
function onUpdate(dc as Dc) as Void {}
```

The `dc` parameter in `onUpdate` is a Device Context — the drawing surface. If you've used the HTML5 Canvas API before, this will feel immediately familiar. The primitives are similar:

```java
// Drawing basics
dc.setColor(Graphics.COLOR_WHITE, Graphics.COLOR_BLACK);
dc.clear();

dc.drawLine(x1, y1, x2, y2);
dc.drawCircle(cx, cy, radius);
dc.fillCircle(cx, cy, radius);
dc.fillPolygon([[x1,y1], [x2,y2], [x3,y3]]);

// Text
dc.drawText(x, y, font, "Hello", Graphics.TEXT_JUSTIFY_CENTER);

// Bitmaps
dc.drawBitmap(x, y, bitmap);
```

The coordinate system has (0, 0) at the top-left corner. Round watch screens are still represented as a square coordinate space — a 416x416 circle is addressed as a 416x416 grid, with the corners being offscreen.

One key difference from the Canvas API: **you cannot draw incrementally**. Every call to `onUpdate` should redraw the entire screen from scratch. Don't assume anything from the previous frame is still there.

## Device Sizes

This is Garmin's biggest quirk. There are over a dozen supported screen resolutions, ranging from 240x240 on older Forerunner models to 454x454 on newer AMOLED devices like the Epix. Some screens are round, some are square.

The way to handle this is with the **`monkey.jungle` build file**. You can create a separate resource folder for each device (or group of devices with the same resolution), and the build system will use the right one automatically.

```
project.manifest = manifest.xml

# Default resources used by all devices
base.resourcePath = resources

# Device-specific overrides
fenix6.resourcePath = resources-416x416
vivoactive4.resourcePath = resources-260x260
```

For background images and any asset that needs to be exactly the right size, you'll need a separate copy per resolution. This is exactly the problem I built the [Garmin Asset Generator](/blog/2025/garmin-asset-generator/) to solve — it takes your source images and generates correctly-sized versions for every target device in one command.

For elements you draw in code (lines, circles, text), you can make them resolution-aware by reading the screen dimensions at runtime:

```java
var width = dc.getWidth();
var height = dc.getHeight();
var cx = width / 2;
var cy = height / 2;
```

## Colors

On non-AMOLED Garmin devices, the display is limited to **6-bit color** — that means only 4 possible values per RGB channel (0, 85, 170, 255), for a total of 64 colors. Colors you specify that fall between those values get rounded to the nearest available color, sometimes in ugly ways.

The constants in `Graphics` cover the common ones: `COLOR_RED`, `COLOR_BLUE`, `COLOR_GREEN`, `COLOR_YELLOW`, `COLOR_WHITE`, `COLOR_BLACK`, and a handful of others. For custom colors, use hex values — but stay within the 6-bit palette or the result will look wrong on device.

To help with color selection, I built a [6-Bit Color Wheel](/blog/2025/6-bit-color-wheel/) tool that shows all 64 available colors arranged in a 3D cube so you can see how they relate to each other spatially.

AMOLED devices (like the Epix series) have full-color displays, so this limitation doesn't apply to them. If you're targeting only AMOLED devices you can use any color you like.

## Fonts

Fonts are the other major constraint. You cannot use arbitrary system fonts or load a `.ttf` at runtime. Every font you use must be declared as a **bitmap font** in your resources — the font is rasterized at build time at a specific size, and that's the size you get.

Declare fonts in `fonts.xml`:

```xml
<fonts>
  <font id="font_medium" filename="fonts/roboto-medium.ttf"
        antialias="true" filter="0123456789:AMP " />
</fonts>
```

The `filter` attribute is important: only the characters listed will be included in the bitmap. This keeps the app's memory footprint small. If you only need to display digits and colons for a clock, you don't need the full alphabet.

Load and use the font in code:

```java
var font = Application.loadResource(Rez.Fonts.font_medium);
dc.drawText(cx, cy, font, "12:00", Graphics.TEXT_JUSTIFY_CENTER);
```

Because fonts are bitmapped at a fixed size, there's no way to scale them at runtime. If you need the same font at two different sizes, declare it twice in `fonts.xml` at the two sizes you need.

## Running the App

The VSCode extension comes with a **simulator** that runs your watch face without needing a physical device. From the command palette, run `Monkey C: Run Current Application`. It will ask you to select a target device (pick one that matches your manifest) and launch the simulator window.

The simulator is good but not perfect. Some sensors (like weather) return mock data, and the rendering can differ slightly from hardware. Before publishing, it's worth installing the `.prg` file directly on a real watch to catch any issues.

To sideload to a physical device: build in debug mode, connect the watch via USB, and copy the compiled `.prg` file to the `GARMIN/Apps` folder on the device. The watch picks it up automatically when you disconnect.

## Helpful Resources

#### Device List

The Connect IQ SDK documentation includes a full list of supported devices with their screen sizes and shapes. I also maintain a `DEVICES.md` in the [Garmin Asset Generator repo](https://github.com/pjflanagan/garmin-asset-generator) with the devices I've targeted and their resolutions.

#### Chinese Character Rendering

If you want to display Chinese (or any non-Latin script that Garmin doesn't bundle on Western devices), the [garmin-tilemapper](https://github.com/sunpazed/garmin-tilemapper) library provides a sprite sheet approach. Characters are stored as a bitmap atlas and rendered by looking up coordinates. It's how I display the time in Chinese in the [Chinese Watch Face](/blog/2025/garmin-chinese-watchface/).

#### Connect IQ API Reference

Garmin's official API reference is at [developer.garmin.com/connect-iq/api-docs](https://developer.garmin.com/connect-iq/api-docs/). The `Toybox.WatchUi`, `Toybox.ActivityMonitor`, and `Toybox.Weather` namespaces are the ones you'll use most for watch faces.

## Going Live

### Publishing to the Connect IQ Store

When you're ready to publish, build in release mode: `Monkey C: Build Current Application (Release)`. This produces a signed `.iq` file using your developer key.

Go to the [Connect IQ Developer Portal](https://apps.garmin.com/developer) and create a new app listing. You'll need:
- A name and description
- At least one screenshot per supported device (the store is picky about dimensions)
- A promo image (1050x400 pixels)
- Your `.iq` file

Garmin reviews submissions manually. Turnaround for me has been 2–5 business days. They check that the app doesn't crash on launch for each supported device, that it follows their content policies, and that the metadata matches the actual functionality.

The most common reason for rejection is supporting a device in the manifest that you haven't actually tested. If your app crashes on a device you listed, it gets rejected. Only list devices you've verified work in the simulator.

### Updates

Releasing an update is the same process: build a new `.iq`, go to the portal, and upload a new version to your existing listing. Users with your watch face installed will get the update automatically through the Connect IQ mobile app.

### Error Monitoring

Once your app is live, the developer portal shows crash reports from users. Each crash includes the device model, app version, and a stack trace. The stack traces reference line numbers in your compiled code rather than your source, so they take some decoding — but they're usually enough to identify the problem.

A common crash source: accessing a sensor value that the specific device doesn't support. If you call `ActivityMonitor.getInfo().bodyBattery` on a device that doesn't have body battery, you get a null reference error. Always check that data fields are non-null before drawing them.

---

That's the full picture. The learning curve is front-loaded — the tooling setup and device size problem take some patience — but once you're past that the actual development loop is fast and fun. The simulator makes iteration quick, and there's something uniquely satisfying about seeing your code on your wrist.
