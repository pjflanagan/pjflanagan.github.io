---
layout: post
date: 2018-08-04
title: Tragedize
description: "For free: Chrome Extension, never installed"
image: https://raw.githubusercontent.com/pjflanagan/tragedize/master/img/promo_tile.png
github: https://github.com/pjflanagan/tragedize
website: https://chrome.google.com/webstore/detail/tragedize/indpmljpafokipipkgblbjbdmdfiboje
---

In the world of literature, there's a famous six-word story that's often attributed to Ernest Hemingway: **"For sale: baby shoes, never worn."** It's a miniature tragedy that has lost it's impact in a world that has already meme-d it thousands to times over. I found myself wondering what it would look like if I brought that intended level of gravity and poetic depth to the mundane world of online shopping. 

## A Poetic Experiment

For a fun little Chrome Extension experiment, I decided to do just that. **Tragedize** was a simple browser extension that focused on a single website: **Zappos**. When a user with the extension installed visited the an item's page on Zappos, the extension would programmatically alter the product titles, replacing the standard descriptions with something a bit more evocative and, well, tragic. 

## Technical Implementation

The extension was a simple exercise in content script injection and DOM manipulation. I had to write a script that would scan the page for the product title section and then manipulate that into a new string.

## Screenshots

![Screenshot Converse](https://raw.githubusercontent.com/pjflanagan/tragedize/master/img/screenshots/0.png)

![Screenshot Timberland](https://raw.githubusercontent.com/pjflanagan/tragedize/master/img/screenshots/1.png)

## Looking Back

While **Tragedize** was never intended to be a serious or even a particularly useful tool, it was a fun way to explore the intersection of literature and the modern web. It was also a great introduction to the world of Chrome Extension development, which I would later use for more practical projects. This project taught me the value of simple, focused experimentation and how even a small, silly idea can be a great way to learn a new set of technical skills. 

> For free: Chrome extension, never installed.
