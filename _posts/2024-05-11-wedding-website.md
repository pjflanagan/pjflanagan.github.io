---
layout: post
date: 2024-05-11
title: Wedding Website
description: An event site for my wife and I
categories: web
image: https://www.flanny.app/JacquelineAndPeter/img/intro_engagement.jpg
github: https://github.com/pjflanagan/JacquelineAndPeter
website: https://www.flanny.app/JacquelineAndPeter/
---

For my wedding I wanted to program the website myself. It was nice to return to building a website just using CSS and jQuery.

I went for a simple one page scrolling sidebar slideshow, similar to an example I found elsewhere. I picked a red and gold theme.

Some of my favorite components/features are:
- The "See more" buttons
- The slideshow that changes based on markers
- The scroll to a point
- The footer that is tucked behind the sidebar body (much like this blog has)

I don't often program websites with this much information, its amazing how good a full bodied website can look.

## The One-Page Scroll Layout

The layout uses a fixed main content area and a scrollable sidebar (which is a common template on theknot.com). As you scroll through sections, the photo that takes up most of the screen changes. Getting that effect right was a matter of adding tags to specific elements with data about what photo to change to.

## Building With Real Content

Most of my projects are tools or visuals, there isn't much informative content there. Building a website for an actual event with real logistics was a fun change of pace. There were details that needed to be right, links to external resources, and tons of photos.

## Going Vanilla

Returning to plain CSS and jQuery after years of React and TypeScript felt refreshing. No state management, no component lifecycle, no build step. For a project with a clear scope and a hard deadline (the wedding), the simplicity was an asset.

## Google Icons

I used Google Icons from Google Fonts, which are incredibly interesting. They sub in a font that looks like a section of an icon
so that the whole word look like the font. You can tell because you can copy an icon and it will paste as the word. For example,
the `book` icon would be segmented into 4 parts, the `b` becoming the left part of the left page, the `k` the right part of the 
right page, the `o`'s make the left and right side of the spine.
