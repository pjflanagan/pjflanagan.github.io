---
layout: post
date: 2022-01-06
title: NYT Crossword Plus
description: A stat sheet
image: https://nytcrosswordplus.flanny.app/img/social.png
github: https://github.com/pjflanagan/nyt-crossword-plus
website: https://nytcrosswordplus.flanny.app/group/test
---

The Daily Mini has been a race my friends and I have been playing against each other in for years. Being runners, we love both competition and data, so we have always wanted a more advanced leaderboard than the one on the NYT. So, I created NYT Crossword Plus.

## Method

This project is made up of several parts:
1. A webscraper for obtaining data
2. An API for updating and fetching data
3. A website for viewing data
4. A Discord messaging bot

### 1. Scraper

In order for any of this to work, I'd need to obtain the crossword data somehow. 

At first, I created a simple Chrome extension that updates a database whenever I load the leaderboard page. Of course, this depended going to the page manually so the times could be updated, so it was not an ideal solution for a webscraper. 

I ended up finding someone who had made a similar project with a working webscraper. A friend of mine helped fix it up and got it to run on Google Cloud once daily before the crossword closes. Now our times can reliably be recorded.

### 2 & 3. Web

The main value add of this project is the more advanced leaderboard. The NYT only offers a leaderboard each day, but does not have any tracking throughout time. 

Our leaderboard would have a graph over time, superlatives, and stats chart. 
- The graph shows who won each day, and how much better than the group they did
- Superlatives track who is on a win streak, who is the best on average, who did it the fastest
- The stats chart allows you to find data about yourself

![Group Leaderboard](/assets/posts/2022/nyt-crossword-plus/2-group-1.png)

The chart was great because there are many ways of viewing who is "best," giving multiple people points to pride themselves on. The Power Index was a stat of my own invention that averages a place percent and time percent. 

{% highlight typescript %}
const placeScore = (participantCount - place) / participantCount;
const timeScore = (slowestTime - time) / (slowestTime - fastestTime);
return (placeScore + timeScore) / 2;
{% endhighlight %}

![Group Leaderboard Chart](/assets/posts/2022/nyt-crossword-plus/2-group-2.png)

The home page contains some info and links, the more interesting page is the group view. You can see a [test group online here](https://nytcrosswordplus.flanny.app/group/test).

![Home Page](/assets/posts/2022/nyt-crossword-plus/1-home.png)

As a backup for missed entries (the scraper ran a few minutes before the end of the day), I added an admin page for manual entries.

#### NextJS

I decided I wanted to experiment with NextJS for this project. NextJS has a few features I was excited to use:

- Serverless functions built in, which was important for making a robust API
- Generated pages from folder structure, which I found helpful for making `/group/<name>` routes
- Server Side Props, I ended up not using these because it increased the page load time, however I hope to use this feature at another point in the future

I loved working with NextJS, since this project it has become my framework of choice.

#### Ant Design and Rechart

I typically am a bit stubborn about doing it myself when it comes to web development projects. I find working with a UI framework to be limiting. If a framework is not robust enough, making changes can be tedious. Margins and padding all have default values and changing them can feel hacky.

But, for this project, my focus was much more on the information itself, and not how it looked. So I found a framework I was really fond of. [Ant Design](https://ant.design/) is a very clean framework with a lot of useful data entry features like autocomplete, calendars, sortable tables. It made perfect sense to use for this project.

I also really wanted a visual element, so I went with [Rechart](https://recharts.github.io/) to make a graph. This was easy to use and is capable of some customization.

### Discord Bot

I also wanted this project to announce winners to my friend group. To make the Discord bot, I decided to use Autocode, because it is free and easy to setup (linking Discord and running daily). All I had to make was an endpoint for it to read daily stats, and the rest was just formatting.

![Discord Bot](/assets/posts/2022/nyt-crossword-plus/3-discord.png)


## Project Future

The biggest point of failure for this project is the auto scrapper. The NYT does not want bots accessing the webpage, and any webpage redesigns would require the scrapper to be updated. In the future I think the best fix for this would be allowing my friends access to the Chrome extension that updates the data. This redundancy would make updates more frequently and easily get around NYT bot checks, but would still be susceptible to redesigns.

The other problem with the auto scrapper is that is only has access to one account, meaning only my friends can have data in the system. I built this website to support groups, but only I can make them. If someone else wanted to use this for their friends they would not be able to create that group, or scrape their own data for it. A public Chrome extension could help fix this.

The last change I'd make if I were to restart this project would be to not use Autocode. Autocode is a cool little service, but Netlify supports Cron jobs, and that seems more reliable and git friendly.
