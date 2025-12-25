---
layout:      page
title:       Flanny Apps Blog
description: Thoughts on things I've made
image:       ""
---

# Blog Posts

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
