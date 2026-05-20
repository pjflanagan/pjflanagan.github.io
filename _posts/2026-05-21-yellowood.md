---
layout: post
date: 2026-05-21
title: Yellowood
description: An interactive fiction platform
categories: game live
image: https://raw.githubusercontent.com/pjflanagan/yellowood/refs/heads/main/public/img/social/yellowood-social.webp
github: 
website: https://yellowood.flanny.app
---

Yellowood started as an editor for text based adventure games (see [Yes, Chef!](blog/2025/yes-chef/)). I was to be the only user, so I hid it behind an admin token that I could set to prove it was me.

I showed to project to a friend of mine and he was more impressed with the editor than the game itself. He suggested that the editor is what I really should be putting out there.

Some time passed, coding agents got really good. I decided to revisit.

## Rename and New Features

I named the project Yellowood, a reference to the Robert Frost poem about choosing a path.

After that, I asked Claude to help me with all sorts of things that needed to happen:
- Add user accounts
- Add login and home pages
- Add a user page for managing stories
- Unify the page styles into a single collection of elements
- Add a guide page with components
- Create onboarding features like username and how to callouts
- Migrate to Firebase
- Add an admin page
- And so, so much more...

## Technical Things

### Firebase

I usually deploy projects on Netlify. It's simple and has a generous free tier. But as this project and my goals for it grew, it became apparent that I needed more.

For one, I was running into DB startup issues. Netlify instances have a timeout and need to restart often if traffic is low. Connecting to Mongodb would sometimes timeout, leading to 500 errors.
The best fix for this was switching to Firebase, which is always on. This got rid of the timeout error and 

I usually don't like the overwhelming consoles like Azure and AWS for smaller personal projects, but I found that Firebase is quite reserved. Google must have set it up in such a way that Firebase is your application's core, and if you want a fancy AI plugin you can link it to the much more feature rich Google Cloud. 

I also don't love having to pay for hosting when this is just in the hobby stage. All of my other projects take advantage of free tiers. Firebase requires a credit card at signup, but is transparent about charging and so far I've spent less than $1.

Firebase has everything I'd want as this project continues to grow too. Things like file storage, user authentication (if I ever don't like my current implementation), and backend functions.

I probably will continue to use Netlify and Vercel for small future projects, but if I ever want to set up 

### Posthog

This was my first time trying Posthog. I usually just use Google Analytics because I'm only interested in pageviews. But for this project I wanted a more in-depth view of what is going on.

I added flowcharts for signups, watched screen recordings of users playing, and added insights for what pages have errors.

While coding is the fun page, if I want users to really use this site, monitoring like this is necessary. Posthog is a fun option with a solid free tier.



## UX Things

### Onboarding

There are a lot of features on this website, and especially in the editor. Getting a user from the homepage, to logged in and writing a story is the ultimate goal here.

...

### The Guide Page

This was a fun page to implement. A helpful guide can...


## Writing Stories

I added a few different games (like this one about [sneaking water through TSA](https://yellowood.flanny.app/u/yellowood/tsa)) so first time users could see what the site's aim was.

## Growing Users

This is the hardest part of any project for me. I've had games