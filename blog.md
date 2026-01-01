---
layout: default
title: "Blog"
permalink: /blog/
---

<div class="page-header">
  <div class="container">
    <h1>{{ page.title }}</h1>
    <p class="page-description">Thoughts, insights, and updates on AI research and development.</p>
  </div>
</div>

<div class="container">
  <div class="blog-list">
    {% if site.posts.size > 0 %}
      {% for post in site.posts %}
      <article class="blog-card">
        <a href="{{ post.url | relative_url }}">
          {% if post.thumbnail %}
            <img src="{{ post.thumbnail | relative_url }}" alt="{{ post.title }}" class="blog-card-image">
          {% else %}
            {% assign first_image = post.content | split: '<img ' | slice: 1 %}
            {% if first_image %}
              {% assign img_src = first_image | split: 'src="' | slice: 1 | first | split: '"' | first %}
              {% if img_src %}
                <img src="{{ img_src | relative_url }}" alt="{{ post.title }}" class="blog-card-image">
              {% else %}
                <img src="{{ '/assets/img/default-thumb.svg' | relative_url }}" alt="{{ post.title }}" class="blog-card-image">
              {% endif %}
            {% else %}
              <img src="{{ '/assets/img/default-thumb.svg' | relative_url }}" alt="{{ post.title }}" class="blog-card-image">
            {% endif %}
          {% endif %}

          <div class="blog-card-content">
            <h2 class="blog-card-title">{{ post.title }}</h2>
            <p class="blog-card-date">{{ post.date | date: "%B %d, %Y" }}</p>
            <p class="blog-card-excerpt">{{ post.excerpt | strip_html | truncate: 120 }}</p>
          </div>
        </a>
      </article>
      {% endfor %}
    {% else %}
      <div class="empty-state" style="text-align: center; padding: 4rem 0;">
        <h2 style="color: #6b7280; margin-bottom: 1rem;">Coming Soon</h2>
        <p style="color: #9ca3af; font-size: 1.1rem;">Blog posts will be published here in the future. Stay tuned for insights on AI research, blockchain applications, and data science discoveries.</p>
      </div>
    {% endif %}
  </div>
</div>
