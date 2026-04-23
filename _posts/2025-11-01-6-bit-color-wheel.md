---
layout: post
date: 2025-11-01
title: 6-Bit Color Wheel
description: A 3D color cube the 6-bit color palette
categories: tool garmin
image: https://github.com/pjflanagan/6-bit-color-wheel/raw/gh-pages/screenshot.png
github: https://github.com/pjflanagan/6-bit-color-wheel
website: https://www.flanny.app/6-bit-color-wheel/
---

In late 2025, I found myself working on a fun and creative project: to build a new watch face for my **Garmin** watch. I found after wearing a smartwatch for most of a year that I didn't enjoy any of the default faces and I wanted to build my own. So I started making watch faces.

## The Problem

My Garmin is only capable of displaying 6-bit colors. That means colors like `#FF0000` and `#AA0000` can be displayed, but colors in between like `#B80000` cannot be displayed. When trying to display a color in between, the watch would just render it as whatever color is closer. This meant I had to be careful when picking colors to use.

I found a website that lists and displays [a 6-bit color palette](https://lospec.com/palette-list/6-bit-rgb), but it's hard to see how those colors relate and compare to one another in a simple grid. I wanted to see if I could create a tool that would help me visualize and compare those colors in a more meaningful way. I decided instead to build a dedicated 3D color cube that would allow me to see all of the colors at once. 

## How the Color Cube Works

A 6-bit RGB color space has 4 possible values per channel (0, 85, 170, 255), giving 4×4×4 = 64 total colors. The cube represents this literally: a 4×4×4 grid where X is red, Y is green, and Z is blue. Each cell in the grid is filled with its corresponding color.


## Technical Implementation

To make a 3D cube readable in 2D, I render it as 4 stacked layers. Each layer is a 4×4 grid of color swatches representing one value of the blue channel. Hovering a layer highlights it and dims the others, which helps when comparing colors across a single blue value.

The cube is rendered in plain HTML and CSS — no canvas, no WebGL. Each swatch is a `div` with a background color. The layering effect uses `opacity` transitions on hover. It's simple enough that the whole project is a single HTML file.


![6-Bit Color Cube with one of the middle layers hovered to focus](https://github.com/pjflanagan/6-bit-color-wheel/raw/gh-pages/screenshot.png)

This project was simple and served its purpose. I had been incredibly useful for my own design work, helping me find the perfect colors for each Garmin watch face. 

## What I Actually Used It For

The main use case was finding colors that sit near each other in the color space, which helps when creating gradients or color schemes that stay within the 6-bit palette. For example, if I want a dark blue-to-teal gradient, I can look at the blue layer and find a path through adjacent cells that ends at something close to teal.

Picking from a flat list of 64 hex codes, doesn't give you that spatial relationship. The cube does.

![Garmin watch faces](https://github.com/pjflanagan/garmin-chinese-watchface/raw/main/images/HeroImage.jpg)