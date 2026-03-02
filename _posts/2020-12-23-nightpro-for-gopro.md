---
layout: post
date: 2020-12-23
title: NightPro For GoPro
description: A Python package for merging nightlapse photos into video
image: /assets/posts/2020/nightpro-for-gopro.jpg
github: https://github.com/pjflanagan/nightpro-for-gopro
website: https://pypi.org/project/nightpro-for-gopro/
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/jZyszParsmc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

I originally purchased a GoPro to film myself rollerblading, but as I started experimenting with the camera's settings, I found that I also really enjoyed its nightlapse features. There's something incredibly satisfying about setting up a tripod, pointing it at the night sky, and letting the camera capture the subtle movements of the stars while I'm asleep. 

## Project Reasons

GoPro's nightlapse mode is wonderful, but it saves files in a way that isn't immediately useful. Rather than automatically stitching the images into a single video file (the way standard GoPro timelapses do), nightlapses are saved as a series of thousands of individual JPEG photos. Merging them all into a cohesive video manually required a tedious and brittle `ffmpeg` command that I had to look up every single time:

{% highlight bash %}
ffmpeg -r 32 -start_number <number> -i ./<folder>/G00%d.JPG -vcodec libx264 -pix_fmt yuv420p <name>.mp4
{% endhighlight %}

I decided to create **NightPro** as a Python package to automate this entire workflow. Instead of manually finding folder names and start numbers, NightPro scans your directory, identifies sets of related images, and runs the necessary processing to turn them into high-quality MP4 videos. 

## Technical Implementation

The tool is built with Python and leverages `ffmpeg` under the hood, but it handles a few things that command alone requires you to do yourself. For instance, it can automatically detect the start and end of a nightlapse so you don't have to write file names into the command. It even handles the "zero-padding" in GoPro filenames, which can be tricky when a lapse spans across multiple folders or thousands of files. 

After installation via `pip`, the entire process is reduced to a single command:

{% highlight bash %}
nightpro
{% endhighlight %}

This project was a great lesson in "scratching your own itch." By automating a repetitive 10-minute task, I've saved myself hours of frustration and made it much more likely that I'll actually share the nightlapses I capture. Now, I can go from a memory card full of loose photos to a finished, shareable video in seconds. 