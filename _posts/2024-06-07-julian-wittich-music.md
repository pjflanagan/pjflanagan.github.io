---
layout: post
date: 2024-06-07
title: Julian Wittich Musician Website
description: A bass musician website
categories: web live
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

An important part of this project was for Julian to be able to edit the app on his own, without having to edit any HTML or Markdown files. Most solutions to this are a CMS (like WordPress or Contentful), but setting one up and maintaining it felt like overkill. 

So, I came up with two ways for him to do that, all through his Google account:
- Blogger
- Calendar

Blogger is Google's free blogging platform, and it has a public API. Each section of Julian's site (bio, press quotes, upcoming info) is a separate Blogger post. He edits the post in Blogger's familiar editor and the site pulls the updated content on page load. NextJS caches it so there's no latency for visitors.

Google Calendar works similarly — Julian adds events with titles, dates, times, and optional ticket URLs as calendar entries. The site fetches upcoming events from the public calendar feed. No custom admin panel required.

![Example event entry in Google Calendar](https://raw.githubusercontent.com/pjflanagan/julianwittichmusic/main/readme/ExampleEvent.png)

## Reflections

Building for someone else's ongoing use is different from building for yourself. I had to think about what happens when I'm unavailable, when the tools change, or when Julian wants to add something I didn't plan for. The Google-as-CMS approach holds up well because both Blogger and Google Calendar are mature, well-documented tools Julian already knows how to use.

The bass string animation remains the part I'm most proud of. It's a small detail that most visitors probably interact with for about ten seconds, but those ten seconds feel like discovering something rather than just scrolling past a photo.

