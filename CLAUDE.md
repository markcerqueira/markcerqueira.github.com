# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A Jekyll-based personal blog (mark.gg) by Mark Cerqueira. GitHub Pages automatically builds and deploys from the `main` branch.

## Commands

```bash
# Serve locally with auto-reload
jekyll serve --watch

# Reset RubyGem state if things break
mv Gemfile.lock Gemfile.lock.backup && sudo bundle clean --force && bundle install

# Rebuild bundled CSS after editing any individual CSS file in public/css/
cat public/css/poole.css public/css/syntax.css public/css/lanyon.css public/css/tags.css public/css/v1.css > public/css/bundle.css
```

## Architecture

- **`_posts/YYYY/`** — Blog posts as Markdown files named `YYYY-MM-DD-slug.md`, organized by year
- **`_layouts/`** — Three layouts: `default.html` (base), `post.html` (wraps default), `page.html` (wraps default)
- **`_includes/`** — Partials: `head.html` and `sidebar.html`
- **`_config.yml`** — Site config; defines per-year image path variables (e.g., `site.images2025`) and end-of-post blurb variables (`site.managing_management`, `site.manager_reads`)
- **`assets/posts/YYYY/`** — Post images organized by year; referenced via `{{ site.imagesYYYY }}/MM-DD/filename.jpg`
- **Standalone pages** — `about.md`, `resume.md`, `projects.html`, `fitness.html`, `pai.html`, `pai-relato.html`, `twitch.md`, etc. at the root level

## Post Front Matter

```yaml
---
layout: post
title: "Post Title"
description: ""
category:
tags: [tag1, tag2]
---
```

## Image Convention in Posts

Images use inline HTML with site config variables:
```html
<div>
    <img class="rounded-corners" style="max-width: {{ site.default_image_width }}; border: 1px; margin-top: 24px;" src="{{ site.images2025 }}/MM-DD/filename.jpg"/>
    <p class="caption-text" style="line-height: 1.5em; margin-bottom: 24px;"><strong>Caption text</strong></p>
</div>
```

When adding images for a new year, add the corresponding variable to `_config.yml` (e.g., `images2026: "/assets/posts/2026"`).
