---
layout: page
title: "Blog"
description: Thoughts on things and things I've made
image: https://camo.githubusercontent.com/f3d2c49012869603dbd75aa77f0f753a215fb808f5b151b543484250310d4f12/68747470733a2f2f706a666c616e6167616e2e6d652f696d672f736f6369616c2f736f6369616c2e706e67
---

# Blog

Welcome to the **Flanny Apps Blog**. This blog is many things for me: a bit of a portfolio, a bit of a journal, and a "final resting place" for projects both active and retired. 

Here you will find deep dives into the technical challenges I've faced, retrospectives on past projects from my school days, and tutorials on modern web development. I believe that every project has a story to tell, whether it's a simple script or a full-scale web application.

## Featured

### Live Apps

Read about apps you can visit / download!

<div class="post-link-large-holder">
{% include post-link-large.html slug="garmin-cyberpunk-watchface" %}
{% include post-link-large.html slug="ohword" %}
</div>

### Past Projects

Some inactive but rewarding projects.

<div class="post-link-large-holder">
{% include post-link-large.html slug="nuclear-codes" %}
{% include post-link-large.html slug="bamboo" %}
</div>

### Thoughts and Tutorials

<div class="post-link-large-holder">
{% include post-link-large.html slug="gen-ai" %}
{% include post-link-large.html slug="simple-socket-games" %}
</div>

### Tools

Maybe you'll find something useful.

<div class="post-link-large-holder">
{% include post-link-large.html slug="merge-reminders" %}
{% include post-link-large.html slug="nightpro-for-gopro" %}
</div>

## All Posts

<!-- CONSIDER: -->
  <!-- {% for post in year.items %}
    {% if post.highlight == true %}
      {% include post-link-large.html slug=post.slug %}
    {% endif %}
  {% endfor %} -->
{% assign years = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}
{% for year in years %}
  <h3>{{ year.name }}</h3>
  <ul>
    {% for post in year.items %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        - {{ post.description }}
      </li>
    {% endfor %}
  </ul>
{% endfor %}
