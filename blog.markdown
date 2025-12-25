---
layout:      page
title:       Flanny Apps Blog
description: Thoughts on things I've made
image:       ""
---

# Posts

## Top Posts

<!-- TODO: a few image posts, maybe 6 -->


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
