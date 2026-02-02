---
layout: default
title: Articles
permalink: /articles
---
<main class="container article">
  <header class="article-header">
    <h1 class="article-title">All articles</h1>
    {% assign oldest_post = site.posts | last %}
    <div class="article-meta">
      Newest to oldest. {{ site.posts.size }} total, first published {{ oldest_post.date | date: "%B %-d, %Y" }}.
    </div>
  </header>

  <section class="section">
    <h2 class="section-title">Latest</h2>
    <div class="post-grid">
      {% for post in site.posts limit:12 %}
      <article class="card">
        {% if post.category %}
          <div class="category-label">{{ post.category | capitalize }}</div>
        {% endif %}
        <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
        <p class="meta">
          <span class="meta-pill">{{ post.date | date: "%B %-d, %Y" }}</span>
          {{ post.excerpt | strip_html | truncate: 120 }}
        </p>
        {% if post.tags %}
        <div class="tag-row">
          {% for tag in post.tags %}
            <a class="tag" href="/tags#{{ tag | slugify }}">{{ tag }}</a>
          {% endfor %}
        </div>
        {% endif %}
      </article>
      {% endfor %}
    </div>
  </section>

  {% if site.posts.size > 12 %}
  <article class="content" style="margin-top: 28px;">
    <h2>More articles</h2>
    <ul>
      {% for post in site.posts offset:12 %}
        <li>
          <a href="{{ post.url }}">{{ post.title }}</a>
          <span class="meta"> · {{ post.date | date: "%B %-d, %Y" }}</span>
          {% if post.category %}
            <span class="meta"> · {{ post.category | capitalize }}</span>
          {% endif %}
        </li>
      {% endfor %}
    </ul>
  </article>
  {% endif %}
</main>
