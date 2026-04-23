---
layout: home
title: Home
description: A collection of apps I've worked on
image: https://camo.githubusercontent.com/f3d2c49012869603dbd75aa77f0f753a215fb808f5b151b543484250310d4f12/68747470733a2f2f706a666c616e6167616e2e6d652f696d672f736f6369616c2f736f6369616c2e706e67
---

# Flanny Apps

<div class="app-link-large-holder">
  {% for app in site.data.favorite_apps %}
  {% include app-link-large.html app=app %}
  {% endfor %}
</div>

### More Web Apps

<ul>
{% for app in site.data.other_apps %}
  <li>
    <a href="{{ app.url }}" target="_blank">{{ app.name }}</a> - {{ app.description }}
  </li>
{% endfor %}
</ul>

### Non-Web Apps

<ul>
{% for app in site.data.non_web_apps %}
  <li>
    <a href="{{ app.url }}" target="_blank">{{ app.name }}</a> - {{ app.description }}
  </li>
{% endfor %}
</ul>

## Blog

My blog is primarily afterthoughts on projects I've completed with a few tutorials and musings on the state of tech thrown in. [See all posts](/blog).

### Highlights

<div class="post-link-large-holder">
  {% include post-link-large.html slug="how-to-make-a-garmin-watch-face" %}
  {% include post-link-large.html slug="garmin-cyberpunk-watchface" %}
  {% include post-link-large.html slug="ohword" %}
  {% include post-link-large.html slug="yes-chef" %}
</div>

### More Posts

<ul>
  {% include post-link-li.html slug="garmin-asset-generator" %}
  {% include post-link-li.html slug="simple-socket-games" %}
  {% include post-link-li.html slug="merge-reminders" %}
  {% include post-link-li.html slug="nyt-crossword-plus" %}
  {% include post-link-li.html slug="cat-laser" %}
  {% include post-link-li.html slug="metrocard-phone-charger" %}
</ul>
