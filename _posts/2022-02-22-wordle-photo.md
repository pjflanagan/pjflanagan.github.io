---
layout: post
date: 2022-02-22
title: Wordle Photo
description: A Wordle expansion pack
categories: tool
image: https://www.flanny.app/wordle-photo/img/social/fb.png
github: 
website: https://www.flanny.app/wordle-photo/
---

In early 2022, the world was obsessed with Wordle. I was no exception, and like everyone else, I was constantly sharing my scores on social media. One day, I noticed that the pattern of green and yellow emojis in my share score looked almost like a tiny, pixelated picture. That's when I had a fun idea: what if you could intentionally "draw" a picture with your Wordle score? 

## The Concept

I started playing a kind of "reverse-Wordle." Since I already knew the daily word, I wanted to see if I could find a sequence of five-letter words that would generate a specific pattern of colors on my way to the final answer. For example, if the word of the day was `SMILE`, what words would I have to guess to draw a smiley face in my share results? 

![A Smiley](https://www.flanny.app/wordle-photo/img/screenshots/smile.png)

## Technical Implementation

Figuring out the (in)correct guesses to draw a picture would be an easy thing for a computer to solve. **Wordle Photo** is a tool that takes a 5x6 grid of colors as an input, along with the daily word, and then searches a list of five-letter words to find a sequence that will produce that pattern. 

The biggest technical challenge was handling the Wordle rules themselves. I had to write a script that would accurately simulate how the color feedback is generated (e.g., if a word has two 'E's but only one is in the final answer, only one box is yellow). Then, I used a backtracking algorithm to find a set of words that would satisfy the visual constraints of the grid while still being valid English words. 

This project was a fun way to engage with the Wordle trend and explore Wordle as an artistic medium (although maybe not as well as [others](https://www.instagram.com/reel/DU28SctAnfD/)). 
