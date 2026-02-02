---
title: Jekyll + GitHub Actions in 3 Steps
category: DevOps
tags:
  - GitHub
---

If you want a Markdown-first blog on GitHub Pages with automatic builds, Jekyll plus Actions is the shortest path. Here is the core setup you need.

## 1. Add a Jekyll config

Create `_config.yml` with the basics:

```yml
title: 1st Engineering Blog
url: "https://1st.github.io"
permalink: /:categories/:title/
markdown: kramdown
```

## 2. Put posts in `_posts`

Each post is Markdown with front matter:

```md
---
title: My First Post
category: notes
---

Hello world.
```

## 3. Add a GitHub Actions workflow

Use the official Pages actions:

```yml
name: Build and deploy Jekyll site

on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v5
      - uses: actions/jekyll-build-pages@v1
        with:
          source: .
          destination: ./_site
      - uses: actions/upload-pages-artifact@v3
  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - id: deployment
        uses: actions/deploy-pages@v4
```

That is it. Push to `main` and GitHub Pages builds the site.
