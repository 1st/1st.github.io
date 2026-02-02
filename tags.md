---
layout: default
title: Tags
permalink: /tags
---
<main class="container article">
  <header class="article-header">
    <h1 class="article-title">Tags</h1>
    <div class="article-meta">Browse posts by topic.</div>
  </header>

  <article class="content">
    <div class="tag-row" style="margin-bottom: 18px;">
      {% assign sorted_tags = site.tags | sort %}
      {% for tag in sorted_tags %}
        <a class="tag" href="#{{ tag[0] | slugify }}">{{ tag[0] }}</a>
      {% endfor %}
    </div>

    {% for tag in sorted_tags %}
      <h2 id="{{ tag[0] | slugify }}">{{ tag[0] }}</h2>
      <ul>
        {% for post in tag[1] %}
          <li>
            <a href="{{ post.url }}">{{ post.title }}</a>
            <span class="meta"> · {{ post.date | date: "%B %-d, %Y" }}</span>
          </li>
        {% endfor %}
      </ul>
    {% endfor %}
  </article>
</main>
