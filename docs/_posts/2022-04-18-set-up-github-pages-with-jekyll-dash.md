---
layout: post
title:  "How I set up my GitHub Pages with jekyll-dash theme"
date:   2022-04-17 22:49:20 +0200
categories: GitHub pages, jekyll, remote theme
---

I recently set up this personal web site with [GitHub Pages](https://pages.github.com). The default setup with `minima` theme is simple and easy, but I wanted to have a cool theme from http://jekyllthemes.org. The [jekyll-dash](https://github.com/bitbrain/jekyll-dash) theme looked good, so I tried to set it up, but hit few issues. In this post, I will share what were the issues and how I resolved them.

# Setup `jekyll-dash` theme

Set up a GitHub supported theme is just easy (https://pages.github.com/themes/). But what I wanted to set up was not a supported theme by GitHub, but one from a http://jekyllthemes.org. This means I needed to manually edit `_config.yml`.

It seems like there is a way to include the theme's gem in `Gemfile` and let a GitHub Action build the pages, but it requires a bit of manual set up and a few trials to get it up and running. Fortunately there is a simpler way to integrate a custom theme. In the `_config.yml` we can define `remote-theme` and it handles everything to get a custom theme up and running (https://github.blog/2017-11-29-use-any-theme-with-github-pages/).

For the [jekyll-dash](https://github.com/bitbrain/jekyll-dash) theme, it is sufficient to add

```yml
remote_theme: bitbrain/jekyll-dash
```

in `_config.yml`. Then the GitHub Action will build the pages with the theme integrated. We do not need to update `Gemfile`, either.

In order to add a few more `jekyll-dash` specific settings, we should define `dash`. For example we can retrieve avatar with `avatar_source` definition, and integrate [Disqus](https://disqus.com) with `disqus`. The whole `_config.yml` including `dash` configuration you can find in https://github.com/taki-on/taki-on.github.io/blob/main/docs/_config.yml

# Fixing `no posts` issue

`index.markdown` -> `index.html`

