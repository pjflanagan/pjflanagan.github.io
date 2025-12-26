---
layout: page
title: Flanny Apps Blog
description: Thoughts on things I've made
image: ""
---

# Posts

## Top Posts

<div class="post-link-large-holder">
{% include post-link-large.html slug=garmin-cyberpunk-watchface %}
{% include post-link-large.html slug="ohword" %}
{% include post-link-large.html slug="gen-ai" %}
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
