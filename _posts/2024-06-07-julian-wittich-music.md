---
layout: post
date: 2024-06-07
title: Julian Wittich Musician Website
description: A based site
image: /assets/posts/2024/julian-wittich-music.jpg
github: https://github.com/pjflanagan/julianwittichmusic
website: https://julianwittich.com
---

My brother-in-law needed a musician website to be more findable. Rather than him paying for Squarespace I built him a website myself. 

Since the website is relatively simple, I wanted there to be a fun interactive feature. I decided the divider between the main photo and the sidebar would be a set of 4 pluckable bass strings.

## Canvas

Try moving your mouse across the strings to see them vibrate. The algorithm is simple but effective. We create a `pullPoint` at where the mouse is and calculate a `to` point on the opposite end of the guitar string and slightly towards the center. Once the string is pulled "too far," we release the string and the `pullPoint` moves towards the `to` point until it reaches it. Then a new `to` point is created on the opposite end and slightly down. The process repeats until we are at equilibrium. 

<iframe src="https://giphy.com/embed/MDjTQ9jRJbocyl3pew" width="480" height="438" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/programming-canvas-html5-MDjTQ9jRJbocyl3pew">via GIPHY</a></p>

This was my first time using a clear background canvas on top of a website. I love how this is a small interactive feature and is not too distracting. I especially love how when you pull the furthest right string the sidebar comes with it (notice how you can pull it to reveal or cover the background, like curtains).

## Editable

An important part of this project was for Julian to be able to edit the app on his own, without having to edit any HTML or Markdown files. I came up with two ways for him to do that, all through his Google account:
- Blogger
- Calendar

Using Blogger he can update a few different blog posts that populate the content of the page. NextJS caches this to improve load time. Using Google Calendar he can update when his events are and even include links to buy tickets.

![Example Event](https://raw.githubusercontent.com/pjflanagan/julianwittichmusic/main/readme/ExampleEvent.png)

