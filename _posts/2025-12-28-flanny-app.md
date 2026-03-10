---
slug: flanny-app
layout: post
date: 2025-12-28
title: Flanny App Redesign
description: A homepage for my pages
categories: web live
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

## Why Jekyll over Gatsby

My original blog used Gatsby, which is a React-based static site generator. Gatsby is powerful, but it requires a full Node.js build pipeline and a Netlify deployment to publish even a one-line change. For a personal blog that I update sporadically, that friction added up. Every post meant waiting for a build.

Jekyll, on the other hand, is natively supported by GitHub Pages. Push to main and the site updates in seconds. No build step, no Netlify dashboard, no queued deployment. For a blog where I'm already managing GitHub repos for everything else, this felt much more natural.

The tradeoff is that Jekyll is less flexible — no React components, no GraphQL data layer. But for a blog that's mostly Markdown and images, that flexibility wasn't something I was actually using in Gatsby anyway. The simpler tool turned out to be the better fit.

## Reflections on the Migration

Moving posts from Gatsby to Jekyll mostly meant reformatting frontmatter and updating image paths. The bigger task was building out the Jekyll theme from scratch to match the look I wanted. Jekyll's Liquid templating is more limited than React, but for layouts and includes it works well.

The home button script ended up being one of my favorite parts of this project. The idea of a single `<script>` tag that injects a persistent, branded element into any page — no npm, no bundler, no configuration — felt like the right amount of engineering for the problem.
