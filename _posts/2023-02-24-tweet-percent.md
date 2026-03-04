---
layout: post
date: 2023-02-24
title: Tweet Percent
description: An honest statistic
categories: 
image: https://raw.githubusercontent.com/pjflanagan/TweetPercent/main/img/promo_tile.png
github: https://github.com/pjflanagan/TweetPercent
website: https://chrome.google.com/webstore/detail/tweet-percent/dhfljnmkpcpmacaffjcplpdpggkmojhf?hl=en&authuser=0
---

In late 2022, after Elon Musk bought Twitter. One of the most visible changes he implemented was the addition of public "view counts" to every tweet. This move was widely seen as a way to satisfy his most ardent supporters, who felt that their reach wasn't being accurately reflected by simple likes and retweets. As with most social media metrics, it was designed to give users a bigger, more impressive number to look at, creating a false sense of engagement. Truly pathetic. 

## A Reality Check

I found this focus on raw view counts to be a bit misleading. After all, if a tweet has a million views but only a handful of likes, is it really that successful? I decided to build a Chrome extension called **Tweet Percent** to provide a bit of much-needed context to these new metrics. 

The extension is designed to automatically calculate and display the number of likes and retweets as a percentage of the total view count. By reframing the data in this way, it's easy to see the actual "conversion rate" of a tweet and get a more honest look at how much a piece of content is actually resonating with its audience. 

![Example tweet of Elon Musk getting 0.73% likes on a tweet](https://github.com/pjflanagan/TweetPercent/blob/main/img/screenshots/3.png?raw=true)

## Technical Implementation

Building the extension was a simple exercise in building a content script that could handle a highly dynamic website like Twitter. I had to write a script that would continuously monitor the DOM for new tweets as the user scrolled and then inject the percentage calculations into the correct places. 

One of the bigger challenges was handling the way Twitter's UI is built. In order for "the bit" to be funny I had to make sure the percentages were formatted correctly and looked like a natural part of the Twitter interface. 

This project was a great way to engage with a major cultural moment and poke fun at overvaluing social media metrics.
