---
slug: flanny-app
layout: post
date: 2025-12-28
title: Flanny App Redesign
description: A homepage for my pages
image: 
github: https://github.com/pjflanagan/pjflanagan.github.io/
website: https://flanny.app
---

Over the years I've made a slew of web projects, ranging from simple one pages to complex applications. Outside of a blog that I used to keep next to my portfolio page, my projects never quite had a home.

That's why I've decided to revamp `flanny.app` into a homepage where all my projects can be easily found. 

## Moving the blog

Since `flanny.app` is going to be the homepage of all my apps, I felt it was appropriate for it also to host the blog about those apps. Before the blog was in Markdown files in Gatsby. Blog updates required a new Netlify build and release (which is time consuming). I decided I would take advantage of Github Page's and Jekyll to host this blog.

After some copy pasting, frontmatter editing, and custom component building, the blog was off of my portfolio and onto `flanny.app`

## Home button script

Now that there is a home page for all Flanny apps, it was natural to want to add a way to get to that home page. To do this I thought it would be neat to make a simple script that can be pasted into any existing app (like adding a jQuery or a Google Font). The home button is a simple html element that looks like a planet. It takes minimal configuration (if any) and only needs a `script` tag to implement.

Check out the [Github repo](https://github.com/pjflanagan/flanny-app-home-button) and [examples](https://www.flanny.app/flanny-app-home-button/) 
