---
slug: garmin-asset-generator
layout: post
date: 2025-11-17
title: Garmin Asset Generator
description: Automating background generation for all Garmin screen sizes
image: /assets/posts/2025/cyberpunk/promo-image.png
github: https://github.com/pjflanagan/garmin-asset-generator
website: 
---

Building watch faces like my [Chinese](/blog/2025/garmin-chinese-watchface/) and [Cyberpunk](/blog/2025/garmin-cyberpunk-watchface/) designs is a lot of fun, but also very tedious. One of the biggest challenges is Garmin's many screen sizes and resolutions.

## The Problem

Garmin doesn't have a single screen size. There are at least a dozen different resolutions, from 240x240 on older devices to 454x454 on the newest Amoled ones. Some are square, some are round. If you want your watch face to look good on all of them, you have to manually resize all your background assets.

## The Solution

I built a Python-based **Garmin Asset Generator** to solve this.

## Features

- **Background Generation**: Can draw two different gradient background patterns by taking two colors.
- **Image Resizer**: Accepts a percentage of the screen the image should fill (e.g., a logo should be 20% of the screen width).
- **Documentation**: Includes a `DEVICES.md` file to record which devices have which screen size and shape

By using this tool, I can focus more on the design and logic of my watch faces and less on the repetitive task of exporting dozens of images.

## Future Features

- **Splash logo generation**: Each device has specific sizing for the splash icon, and I want this tool to be able to handle that.
- **More docs**: Including links to other docs, tutorials, color guides, and font tools can make the repo a great companion to have while developing a Garmin app.
