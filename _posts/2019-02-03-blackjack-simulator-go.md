---
slug: blackjack-simulator-go
layout: post
date: 2019-02-03
title: Blackjack Simulator Go
description: "Double down"
categories: 
image: /assets/posts/2018/vegas.jpg
github: https://github.com/pjflanagan/blackjack-simulator-go
website:
---

I was at it again. After finishing my [Blackjack Simulator](/blog/2018/blackjack-simulator/) using C++, I decided it was time to revisit the project while learning a new language: **Go**. 

## Why Go?

I had been using Go a lot at work, and found that I was better at it than I had been at C++. While my original C++ simulator worked fine, I wanted to see if I could make add more features in a Go version. Maybe this time I'd actually learn how to count some cards.

## The Simulator

The core logic remains similar to the original project. I implemented the same player "brains":
- **Random**: Makes decisions at random (usually loses quickly).
- **Basic Strategy**: Follows the mathematically optimal moves for any given hand.
- **Card Counter**: Tracks the ratio of high cards to low cards and adjusts bets and play style accordingly.
- **Human**: Allows for interactive play to test your own skills.

## Unrealized Goals

I wanted to use the Random player to create my own blackjack strategy table. I've seen some really interesting [Youtube videos](https://www.youtube.com/watch?v=jCF-Btu5ZCk) calculating basic strategy. But I thought it would be cool to run a simulation that could reproduce the same table through thousands and thousands of hands.

## Conclusion

Just like the first time, I spent so much time optimizing the code and playing with the language features that I didn't actually spend any time using the tool to learn Blackjack. But I did learn a lot about Go, and for me, that's always a winning hand.
