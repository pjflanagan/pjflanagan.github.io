---
layout: post
date: 2014-01-21
title: Twitter Follow Bot
description: "A violation of Twitter's API use policy"
categories: web

image: /assets/posts/2014/twitter-follow-bot/twitter-code.jpg
github: https://github.com/pjflanagan/TwitterFollowBot
website:
---

I was once a big Twitter user, trying to get popular for being "internet funny." Of course, that meant I wanted a following to validate my jokes. As a teenager with newfound programming skills, I saw a shortcut: I could build a tool to trick people into following me back.

This was my first time using the Twitter API, and really my first time interacting with any RESTful API. I wrote a program in C++ and ran it on a noisy, old desktop computer at home. I would leave it running all day while I was at school. letting it turn me into an influencer.

![Server](/assets/posts/2014/twitter-follow-bot/twitter-server.jpg)

The logic was simple but effective: I would enter a "seed" account (usually a celebrity with a similar audience to what I wanted), fetch their list of followers, and then my bot would follow those users. A while later, it would unfollow them to keep my follow-to-follower ratio in my favor. 

![Output](/assets/posts/2014/twitter-follow-bot/twitter-output.jpg)

It worked surprisingly well. After a few weeks of constant uptime, I reached about 1,000 "unearned" followers. However, the success was short-lived. Twitter's automated systems eventually flagged the aggressive follow/unfollow patterns. They put an end to the bot by revoking my API keys.

This project was a major learning milestone for me. This was my first time creating a server that had constant tasks to handle and my first time using an API. Later, I'd improve the program, in hopes of minimizing API abuse, but it was still pretty ineffective. Eventually, I realized that true engagement shouldn't be automated, but earned, and I decommissioned the bot. 



