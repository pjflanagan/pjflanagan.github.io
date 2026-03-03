---
layout: post
date: 2025-11-01
title: 6-Bit Color Wheel
description: A color picker
categories: tool
image: https://github.com/pjflanagan/6-bit-color-wheel/raw/gh-pages/screenshot.png
github: https://github.com/pjflanagan/6-bit-color-wheel
website: https://www.flanny.app/6-bit-color-wheel/
---

In late 2025, I found myself working on a fun and creative project: to build a new watch face for my **Garmin** watch. I found after wearing a smartwatch for most of a year that I didn't enjoy any of the default faces and I wanted to build my own. So I started making watch faces.

## The Problem

My Garmin is only capable of displaying 6-bit colors. That means colors like `#FF0000` and `#AA0000` can be displayed, but colors in between like `#B80000` cannot be displayed. When trying to display a color in between, the watch would just render it as whatever color is closer. This meant I had to be careful when picking colors to use.

I found a website that lists and displays [a 6-bit color palette](https://lospec.com/palette-list/6-bit-rgb), but it's hard to see how those colors relate and compare to one another in a simple grid. I wanted to see if I could create a tool that would help me visualize and compare those colors in a more meaningful way. I decided instead to build a dedicated 3D color cube that would allow me to see all of the colors at once. 

![6-Bit Color Cube](https://github.com/pjflanagan/6-bit-color-wheel/raw/gh-pages/screenshot.png)

## Technical Evolution

To achieve this, I created a 4x4 grid of colors that sits on top of the layer below, 4 layers high. I also added hover effects to highlight the layer you are interested in and hide the others.

This project was simple and served its purpose. I had been incredibly useful for my own design work, helping me find the perfect colors for each Garmin watch face. 

![Garmin watch faces](https://github.com/pjflanagan/garmin-chinese-watchface/raw/main/images/HeroImage.jpg)
