---
layout: post
date: 2015-04-01
title: Tyrannosaurus Text
description: A js plugin
categories:
image: https://github.com/pjflanagan/tyrannosaurusText/raw/gh-pages/tText.png
github: https://github.com/pjflanagan/tyrannosaurusText
website:
---

In the early days of responsive web design, I found myself constantly struggling with the same problem: how do you make different lengths of text occupy the exact same width without manually adjusting the font size every single time? Whether it was a headline, a banner, or a logo, I wanted a simple and automated way to ensure that the text would always fit perfectly within its container. 

## A Simple Solution

**Tyrannosaurus Text** was my attempt at building a lightweight JavaScript plugin to solve this exact problem. I wanted a tool that would allow me to set a target width for any piece of text and then have the script automatically adjust the font size until that width was reached. 

## Technical Implementation

Building the plugin was a great exercise in understanding how browsers handle text rendering and font scaling. I had to write a script that would programmatically measure the width of a text string and then use a simple loop to incrementally increase or decrease the `font-size` CSS property until the text matched the target width. 

The implementation was designed to be as simple as possible. After including the necessary JS and CSS files, you could apply the effect to any element by simply calling the `tText()` function:

{% highlight html %}
<script type="text/javascript" src="tyrannosaurusText.js"></script>
<link rel="stylesheet" type="text/css" href="tyrannosaurusText.css">

<div class="class-name">TYRANNOSAURUS TEXT</div> 
<div class="class-name">SEVENTY MILLION YEARS_AGO</div>
{% endhighlight %}

{% highlight javascript %}
new tText("class-name", width).set();
{% endhighlight %}

## Why the Name?

The name **Tyrannosaurus Text** was originally just a silly placeholder that I used while I was testing the script, but it eventually stuck. 

## Use Case

This was never used by anyone, anywhere. Even me. Simply because there is no use case for it. Anyone who would take the time to set this up could have saved time by just setting the font sizes manually. Still a fun project to see working though.

