---
layout: page
title: Blog
subtitle: Research notes on plant breeding, data science, and crop improvement
permalink: /blog/
---

<div class="posts-list">
  {% for post in site.posts %}
  <article class="post-preview">
    <a href="{{ post.url | relative_url }}">
      {% if post.thumbnail-img %}
      <img class="post-preview-img" src="{{ post.thumbnail-img | relative_url }}" alt="{{ post.title }} cover image">
      {% endif %}
      <h2 class="post-title">{{ post.title }}</h2>
      {% if post.subtitle %}<h3 class="post-subtitle">{{ post.subtitle }}</h3>{% endif %}
    </a>
    <p class="post-meta">Posted on {{ post.date | date: "%B %-d, %Y" }}</p>
    {% if post.excerpt %}<p class="post-entry">{{ post.excerpt | strip_html | truncatewords: 45 }}</p>{% endif %}
  </article>
  {% endfor %}
</div>
