---
layout: page
title: "Blog"
description: Thoughts on things and things I've made
image: https://camo.githubusercontent.com/f3d2c49012869603dbd75aa77f0f753a215fb808f5b151b543484250310d4f12/68747470733a2f2f706a666c616e6167616e2e6d652f696d672f736f6369616c2f736f6369616c2e706e67
---

# Blog

<div class="blog-carousel">
  {% for post in site.data.blog_featured %}
  {% include blog-carousel-item.html slug=post.slug tag=post.tag %}
  {% endfor %}
</div>

<h2>All Posts</h2>
{% assign all_categories = site.posts | map: "categories" | join: "," | split: "," | uniq | sort %}
<div class="category-filter">
  <div class="category-pill active" data-category="all">All</div>
  {% for category in all_categories %}
    <div class="category-pill" data-category="{{ category }}">{{ category | capitalize }}</div>
  {% endfor %}
</div>


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
