---
layout: home
title: Home
description: A collection of apps I've worked on
image: ""
---

# Flanny Apps

Please enjoy a collection of websites and apps I've made over the years! If you want to know more about me check out my [portfolio](https://pjflanagan.me).

## Apps

### Favorites

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
  {% include post-link-large.html slug="garmin-cyberpunk-watchface" %}
  {% include post-link-large.html slug="ohword" %}
  {% include post-link-large.html slug="hanafuda" %}
  {% include post-link-large.html slug="rollerblade-bag" %}
</div>

### More Posts

<ul>
  {% include post-link-li.html slug="garmin-asset-generator" %}
  {% include post-link-li.html slug="yes-chef" %}
  {% include post-link-li.html slug="mta-clock" %}
  {% include post-link-li.html slug="arcade-cabinets" %}
  {% include post-link-li.html slug="blackjack-simulator-go" %}
</ul>

<hr />

## Tools & Tech

While I love building things for the web, I also enjoy exploring different platforms and tools. Here are some of the technologies I've been working with lately:

- **Languages:** TypeScript, Python, Go, Swift, Monkey C (for Garmin)
- **Frameworks:** React, Svelte, Express, FastAPI
- **Creative Tools:** HTML5 Canvas, Three.js, Figma
- **Hardware:** Arduino, Raspberry Pi, Custom Arcade Cabinets
