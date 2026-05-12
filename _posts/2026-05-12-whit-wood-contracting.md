---
layout: post
date: 2026-05-12
title: Whit Wood Contracting
description: A contractor site powered by Notion
categories: web live
image: /assets/posts/2026/whit.jpg
github:
website: https://whit-wood-contracting.vercel.app/
---

A friend of mine runs a general contracting business out of Durham, NC — kitchens, decks, bathrooms, the whole range. He needed a site that looked professional but, more importantly, one he could actually update himself without needing to call me every time he got a new testimonial or wanted to tweak his services copy.

That constraint drove every decision I made. He was paying close to $200 a year for a Squarespace website that he didn't like. How could I make that number 0?

## Bones

While I mostly like to build apps, I've done a few more informational websites in the recent past. I did one for [my wedding]() and one for my [brother-in-law]().

While I can just recode anything on my wedding website whenever I wanted, my brother-in-law has to be able to update his own website.

To do that, I set up a few APIs that access his Google Calendar and a Blogger blog. From there he can rewrite copy and update events.

I duplicated this repo and passed it to Claude. We would use a similar approach to manage this site's content as well.

## Notion as a CMS

The backend is Notion. His content — testimonials, services, any page copy that might change — lives in a Notion database that he already knows how to use. The site pulls from it via ISR and API's on page load via the Notion API.

The upside is real: he doesn't need to touch code, clone a repo, or wait on me. He edits a row in Notion and it goes live. For a small business owner who just wants to run his business, that's the right abstraction.

## Keeping It Simple on the Front

The site itself is a straightforward static site deployed on Vercel. No heavy framework, no unnecessary moving parts. For a contractor landing page, performance and clarity matter more than interactivity — someone on a phone in a driveway should be able to find a phone number fast.

## Future

I would love to build more sites like this, while apps are fun, content rich and people oriented sites feel more like what the internet was truly for. If I were to seriously start building restaurant websites or pages for other businesses I would consider using Contentful or building with Decap CMS.
