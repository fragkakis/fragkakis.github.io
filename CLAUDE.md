# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based personal website and blog hosted on GitHub Pages at fragkakis.org. It uses the Minimal Mistakes theme (v4.26.2) via remote theme.

## Build and Development Commands

```bash
# Install dependencies
gem install github-pages

# Run local development server
jekyll serve
# Site available at http://127.0.0.1:4000/

# Build site without serving
jekyll build
```

GitHub Pages automatically builds and deploys on push to master branch.

## Architecture

**Theme**: Minimal Mistakes remote theme (`mmistakes/minimal-mistakes@4.26.2`)

**Content Structure**:
- `_posts/` - Blog posts (format: `YYYY-MM-DD-Title.md`)
- `_pages/` - Static pages (about, blog listing, projects)
- `images/` - Static image assets
- `_includes/` - Custom includes (e.g., vimeoPlayer.html)
- `_data/` - Navigation and UI text configuration

**Key Configuration**:
- `_config.yml` - Site settings, theme config, plugins, front matter defaults
- `_data/navigation.yml` - Main navigation menu
- `Gemfile` - Ruby dependencies (github-pages gem)

## Conventions

**Blog Posts**:
- Use front matter with `layout: single` (set by default)
- Reference images: `{{ site.baseurl }}/images/filename.png`
- Embed Vimeo videos: `{% include vimeoPlayer.html id=VIDEO_ID %}`

**Layouts Used**:
- `splash` - Homepage with feature rows
- `single` - Standard post/page layout
- `home` - Blog listing with pagination

**Plugins**: jekyll-remote-theme, jekyll-paginate, jekyll-sitemap, jekyll-feed, jekyll-include-cache
