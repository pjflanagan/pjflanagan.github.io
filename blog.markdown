---
layout: page
title: "Flanny Apps: Blog"
description: Thoughts on things I've made
image: ""
---

# Blog

## Featured

### Live Apps

<div class="post-link-large-holder">
{% include post-link-large.html slug=garmin-cyberpunk-watchface %}
{% include post-link-large.html slug="ohword" %}
</div>

### Past Projects

<div class="post-link-large-holder">
{% include post-link-large.html slug="nuclear-codes" %}
{% include post-link-large.html slug="bamboo" %}
</div>

### Thoughts and Tutorials

<div class="post-link-large-holder">
{% include post-link-large.html slug="gen-ai" %}
{% include post-link-large.html slug="simple-socket-games" %}
</div>

## All Posts

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
