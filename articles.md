---
layout: default
title: Articles
permalink: /articles
---
<main class="container article">
  <header class="article-header">
    <h1 class="article-title">All articles</h1>
    <div class="article-meta">Newest to oldest.</div>
  </header>

  <article class="content">
    <ul>
      {% for post in site.posts %}
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
</main>
