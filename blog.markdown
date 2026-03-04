---
layout: page
title: "Blog"
description: Thoughts on things and things I've made
image: https://camo.githubusercontent.com/f3d2c49012869603dbd75aa77f0f753a215fb808f5b151b543484250310d4f12/68747470733a2f2f706a666c616e6167616e2e6d652f696d672f736f6369616c2f736f6369616c2e706e67
---

# Blog

Welcome to the **Flanny Apps Blog**. This blog is many things for me: a bit of a portfolio, a bit of a journal, and a "final resting place" for projects both active and retired. 

Here you will find deep dives into the technical challenges I've faced, retrospectives on past projects from my school days, and tutorials on modern web development. I believe that every project has a story to tell, whether it's a simple script or a full-scale web application.


  <h2>Featured</h2>

  <div class="filter-section">
    <h3>Live Apps</h3>
    <p>Read about apps you can visit / download!</p>
    <div class="post-link-large-holder">
    {% include post-link-large.html slug="garmin-cyberpunk-watchface" %}
    {% include post-link-large.html slug="ohword" %}
    </div>
  </div>

  <div class="filter-section">
    <h3>Past Projects</h3>
    <p>Some inactive but rewarding projects.</p>
    <div class="post-link-large-holder">
    {% include post-link-large.html slug="nuclear-codes" %}
    {% include post-link-large.html slug="bamboo" %}
    </div>
  </div>

  <div class="filter-section">
    <h3>Thoughts and Tutorials</h3>
    <div class="post-link-large-holder">
    {% include post-link-large.html slug="gen-ai" %}
    {% include post-link-large.html slug="simple-socket-games" %}
    </div>
  </div>

  <div class="filter-section">
    <h3>Tools</h3>
    <p>Maybe you'll find something useful.</p>
    <div class="post-link-large-holder">
    {% include post-link-large.html slug="merge-reminders" %}
    {% include post-link-large.html slug="nightpro-for-gopro" %}
    </div>
  </div>

  <h2>All Posts</h2>
{% assign all_categories = site.posts | map: "categories" | join: "," | split: "," | uniq | sort %}
<div class="category-filter">
  <div class="category-pill active" data-category="all">All</div>
  {% for category in all_categories %}
    <div class="category-pill" data-category="{{ category }}">{{ category | capitalize }}</div>
  {% endfor %}
</div>

<div class="filter-section">

  <div id="posts-container">
    {% assign years = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}
    {% for year in years %}
      <div class="filter-section year-group" data-year="{{ year.name }}">
        <h3>{{ year.name }}</h3>
        <ul>
          {% for post in year.items %}
            <li class="post-item" data-categories="{{ post.categories | join: ',' }}">
              <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
              - {{ post.description }}
            </li>
          {% endfor %}
        </ul>
      </div>
    {% endfor %}
  </div>
</div>

<script>
document.querySelectorAll('.category-pill').forEach(pill => {
  pill.addEventListener('click', () => {
    // Update active pill
    document.querySelectorAll('.category-pill').forEach(p => p.classList.remove('active'));
    pill.classList.add('active');

    const selectedCategory = pill.getAttribute('data-category');
    
    // Filter posts
    const postItems = document.querySelectorAll('.post-item');
    postItems.forEach(item => {
      const categories = item.getAttribute('data-categories').split(',');
      if (selectedCategory === 'all' || categories.includes(selectedCategory)) {
        item.style.display = '';
      } else {
        item.style.display = 'none';
      }
    });

    // Recursively hide empty filter sections
    const updateVisibility = (section) => {
      const items = section.querySelectorAll('.post-item');
      const hasVisibleItems = Array.from(items).some(i => i.style.display !== 'none');
      
      if (!hasVisibleItems && items.length > 0) {
        section.style.display = 'none';
      } else {
        section.style.display = '';
      }
    };

    document.querySelectorAll('.filter-section').forEach(section => {
      updateVisibility(section);
    });
  });
});
</script>
