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

This project was a simple attempt at a plugin. I'm not sure if there was a simple way to make long and short text occupy the same width (or if there is one now). But I felt it would be a useful feature to be able to do easily.

I wrote a simple file that can be included in HTML.

{% highlight html %}
<script type="text/javascript" src="tyrannosaurusText.js"></script>
<link rel="stylesheet" type="text/css" href="tyrannosaurusText.css">

<div class="class-name">TYRANNOSAURUS TEXT</div> 
<div class="class-name">SEVENTY MILLION YEARS_AGO</div>
{% endhighlight %}

Then by setting the width using `tText()` the width of the font size of the text would be increased or decreased until it is the specified width.

{% highlight javascript %}
new tText("class-name",width).set();
{% endhighlight %}

The name Tyrannosaurus Text was just a cute example that worked well for this use case.
