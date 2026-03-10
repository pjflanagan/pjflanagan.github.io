---
layout: post
date: 2025-11-12
title: Garmin Chinese Watch Face
description: A Garmin watch face that displays the time in Chinese characters
categories: garmin
image: https://github.com/pjflanagan/garmin-chinese-watchface/raw/main/images/HeroImage.jpg
github: https://github.com/pjflanagan/garmin-chinese-watchface
website: https://apps.garmin.com/apps/c0748c90-06ef-4a73-94c5-4d2e51b02659
---

This year I bought a Garmin to help me train for a half marathon (and hopefully a full marathon in the future).
I like some of the watch faces available on the the Garmin store, including a [watch face](https://github.com/starryalley/garmin-mandarin-clock) I found that displays the time in Chinese. 

Drawing with the Garmin SDK is a lot like the HTML5 Canvas, so I felt like I could add some decorations to the watch face I already liked. 

I added waves, in the style of how clouds are often drawn in Asian art to the background. It is reminiscent of how dive watches often have wave backgrounds too. I also added a seconds hand ring to give the watch some motion.

![Garmin Chinese Watch Face](https://services.garmin.com/appsLibraryExternalServices/api/screenshots/6e5edbd8-7332-4915-aa86-fcd2d0004826)

> 現在是幾點

## Garmin Connect IQ Store Description

View the time in Chinese, great for students! Watch features a second hand and a decorative wave background.

NOTE: This watchface does NOT require a APAC/Taiwan/China/HK model to be able to display Chinese.


## Garmin Tilemapper

Garmin only installs Chinese on watches sold in Chinese speaking countries. That means in order to display Chinese we need to "install" it ourselves. There is a wonderful library that has already done that called [garmin-tilemapper](https://github.com/sunpazed/garmin-tilemapper).

This library includes a sprite sheet with enough Chinese characters to display the time and the code needed to go from a character like `中` to the coordinates in the application.

## Developing for Connect IQ

Garmin's development environment is called Connect IQ, and the language used is a proprietary one called Monkey C. It's a stripped-down, C-like language with a small standard library and strict memory constraints — watch faces run with very limited RAM and processing power.

The drawing API is where the HTML5 Canvas parallel is strongest. You get a device context, a coordinate system, and a set of drawing primitives: `drawLine`, `drawCircle`, `fillPolygon`, and so on. If you've ever drawn something on a canvas, the mental model transfers well.

With my experience making `<canvas>` art, the wave background was something I was well equipped to make. The waves are drawn as a collection of arcs, connected by lines, with other lines to block parts of it.

## Publishing to the Connect IQ Store

Getting the watch face onto the Garmin Connect IQ store required signing up for a developer account and submitting through Garmin's portal. The review process did not take long.

I plan on creating more watch faces in the future, and I quite like wearing a watch, especially one with my own art on it.
