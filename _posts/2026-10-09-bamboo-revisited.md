---
slug: bamboo-revisited
layout: post
date: 2026-10-09
title: Bamboo
description: A collection of Mandarin learning tools
categories: web live
image: https://bamboo.flanny.app/opengraph-image.png
github: https://github.com/pjflanagan/bamboo
website: https://bamboo.flanny.app
---

**This article is in progress**

I've built this project a few times now. The [first version of Bamboo](/blog/2020/bamboo/) was a full React app with accounts, a database and a Chrome extension. It was built using Mongodb Stitch, which no longer exists. More recently I built [Study Mandarin](/blog/2025/study-mandarin/), a deliberately under-engineered site made of plain HTML and jQuery. It also has a useful Chrome Extension built around it.

Study Mandarin came out of a lesson the first Bamboo taught me: I was spending more time building the tool than using it. So I resolved to keep it simple and spend my time studying instead.

But AI has come a long way since then. It's useful to study with, and it's useful to build with. Now I can have both: a well-built tool, and time to actually use it.

So I rebuilt Bamboo with both philosophies in mind. Make it work well and help me learn, but spend more time using it than building it.

## What's in It

The new Bamboo brings the pages from Study Mandarin forward into one Next.js app:

- A home page with my daily tasks
- Flashcards, with sets I can make progress on
- A reading tool that shows the pronunciation of each character
- Songs
- A Zhuyin trainer

It defaults to Traditional characters, with Simplified as an option. It also borrows from both of its predecessors: the light theme is the green and paper look of the original Bamboo, and the dark theme is the neon style from Study Mandarin.

The flashcards, songs and dictionary live as plain files in the public repo, and the site reads them at runtime. Adding a new flashcard set is just editing a CSV and pushing, with no rebuild.
