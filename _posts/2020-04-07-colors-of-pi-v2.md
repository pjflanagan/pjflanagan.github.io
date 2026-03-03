---
layout: post
date: 2020-04-07
title: Colors of Pi - v2
description: A visualization of Pi
category: art
image: https://raw.githubusercontent.com/pjflanagan/colors-of-pi/gh-pages/src/img/social-tw.png
github: https://github.com/pjflanagan/colors-of-pi
website: https://www.flanny.app/colors-of-pi/
---

During the early days of the COVID-19 pandemic, like many other developers, I found myself with a lot of spare time and a sudden urge to revisit old projects. I felt compelled to [rebuild a site](/blog/2015/colors-of-pi) I worked on many years ago, and **Colors of Pi - v2** was the result. 

## The Old Way vs. The New Way

In the original version, the entire visualization was pre-rendered by a Python script and saved as a massive HTML file. This was inefficient, hard to maintain, and severely impacted load time.

For the second version, I moved the logic to the client side. Instead of pre-rendering everything, the webpage now loads a text file containing the digits of Pi (or other irrational numbers like Euler's number or the Golden Ratio) and updates the display to show it. This shift not only made the site much more lightweight but also significantly more flexible. 

## Key Improvements

One of the biggest changes was how the numbers were displayed. In version one, the digits were hidden, and the focus was entirely on the colors. In version two, I decided to overlay the actual digits directly onto the colors themselves. This simple change allows the user to "read" Pi in its entirety while also appreciating the visual representation of those numbers. 

To be honest, I'm still not entirely sure if this is a total improvement over the first version. One drawback of the new approach is that colors now load one at a time as they're needed. If a user is zoomed way out, the page can appear half-blank for a few seconds as the browser works to catch up. 

Despite those minor issues, version two is a much more robust and sustainable project. It was a great exercise in modernizing an old idea and reminding myself of how much my technical skills have evolved over the past five years.

