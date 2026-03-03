---
layout: page
title: "Blog"
description: Thoughts on things I've made
image: ""
---

# Blog

This blog is many things for me. A bit of a portfolio, a bit of a journal, a bit of "final resting place" for projects.

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
