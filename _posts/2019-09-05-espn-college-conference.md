---
slug: espn-college-conference
layout: post
date: 2019-09-05
title: ESPN College Conference
description: "A Chrome extension"
image: https://github.com/pjflanagan/espn-college-conference/blob/master/img/example.png?raw=true
github: https://github.com/pjflanagan/espn-college-conference/tree/master
website: https://pjflanagan.me
---

It's a tale as old as time in the world of college sports: the SEC (Southeastern Conference) is widely considered to be the best at college football. But are they *really* that much better than everyone else? That's the question I, along with every other fan in the Big Ten (B1G), found myself asking every single Saturday in the fall. 

## A Simple Solution

I decided to create a small but effective tool to help settle the debate. **ESPN College Conference** was a Chrome extension that added a dedicated "Conference" column to the ESPN college football rankings page. By making this data point more prominent, fans could easily see which conferences were dominating the Top 25 at any given time. 

![Logo](https://github.com/pjflanagan/espn-college-conference/blob/master/img/promo_tile.png?raw=true)

## Technical Implementation

Building the extension was a simple matter of DOM manipulation. I had to write a script that would wait for the ESPN rankings table to load, then programmatically inject a new header and new cells for every row in the table. I also had to map every college team in the rankings to its respective conference, which was a bit of a manual process but well worth the effort for the clarity it provided. 

![Screenshot](https://github.com/pjflanagan/espn-college-conference/blob/master/img/example.png?raw=true)

## The Fate of the Extension

In 2024, the Big Ten regrouped to add a few more teams. The resulting confusion might have prompted ESPN to add a conference column to their rankings by default. While this made my Chrome extension redundant and therefore out of date, I was glad to see that such a simple and useful feature finally became a standard part of the ESPN experience. This project was a great lesson in identifying a small gap in a popular product and building a targeted solution to fill it—even if that solution only had a limited shelf life. 
