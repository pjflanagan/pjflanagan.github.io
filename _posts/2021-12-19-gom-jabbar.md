---
layout: post
date: 2021-12-19
title: Gom Jabbar
description: A Dune video game
image: https://www.flanny.app/gom-jabbar/img/social/social-fb.png
github: 
website: https://www.flanny.app/gom-jabbar/
---

One of my ongoing goals as a developer is to create something that reaches a wide audience, even if it's only for a brief moment. I've always been fascinated by how small, viral projects can take on a life of their own. **Gom Jabbar** was an attempt at capitalizing on a pop-culture moment, specifically the release of the first *Dune* movie in 2021. 

## The Concept

For those who haven't read Frank Herbert's novel (I liked it) or seen the film (I loved it), the "Gom Jabbar" is a high-stakes test of a person's humanity. A character must place their hand in a box that induces intense, psychological pain. If they pull their hand out, they are instantly killed by a poisoned needle. 

I thought this was the perfect setup for a simple, browser-based "game." The premise is easy: just place your cursor inside the "box" on the screen. As long as the cursor remains inside, the background of the page will flash with distorted and surreal images representing pain and scenes from the *Dune* universe. If you can keep your hand in long enough, you "survive." If you flinch and pull your cursor out, the game ends, and you lose. 

## Technical Implementation

The game was a fun exercise in creating an immersive, sensory experience with minimal code. I used JavaScript to track the `onmouseenter` and `onmouseleave` events on the central "box" element. To create the "pain" effect, I used a randomized array of high-contrast images and CSS filters to create a strobing, hallucinatory visual style. 

The most new part of this for me was using CSS in 3D to create a box. There are not a whole lot of places where using 3D CSS is used online, so I was happy to put it to use here.

While **Gom Jabbar** didn't end up going viral as I had hoped, it was a great way to experiment with building a project around a specific cultural moment, something I intend on doing again the next time it I have an idea for one. Even if only a handful of people played it, I had a blast bringing a small piece of Arrakis to the web. 
