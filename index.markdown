---
layout: home
title: Flanny Apps
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
    <a href="{{ app.url }}" target="_blank">
      {{ app.name }}
    </a> - {{ app.description }}
  </li>
{% endfor %}
</ul>

### Non-Web Apps

<ul>
{% for app in site.data.non_web_apps %}
  <li>
    <a href="{{ app.url }}" target="_blank">
      {{ app.name }}
    </a> - {{ app.description }}
  </li>
{% endfor %}
</ul>


## Blog

My blog is primarily afterthoughts on projects I've completed with a few tutorials and musings on the state of tech thrown in. [See all posts](/blog).

### Highlights

<div class="post-link-large-holder">
  {% include post-link-large.html slug="garmin-cyberpunk-watchface" %}
  {% include post-link-large.html slug="ohword" %}
  {% include post-link-large.html slug="gen-ai" %}
  {% include post-link-large.html slug="pacpuf" %}
</div>

### More Posts

<ul>
  {% include post-link-li.html slug="breadcrumbs" %}
  {% include post-link-li.html slug="haiku-bot" %}
  {% include post-link-li.html slug="mta-clock" %}
  {% include post-link-li.html slug="yes-chef" %}
  {% include post-link-li.html slug="cat-laser" %}
</ul>
