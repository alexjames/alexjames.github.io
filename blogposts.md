---
title: "Blog"
permalink: "/blog/"
layout: page
---

## Github Pages

Just fork this [repository](https://github.com/niklasbuschmann/contrast) to `your_username.github.io` and adjust the `_config.yml` to use with [Github Pages](https://pages.github.com/) and your page is done.

## Features

 - dark mode
 - [KaTeX](https://katex.org) included
 - no external ressources
 - optional sidebar
 - archive page
 - syntax highlighting
 - supports comments via [disqus](https://disqus.com/) or [isso](http://posativ.org/isso/)

## Installation

To run locally [install Ruby](https://www.ruby-lang.org/en/documentation/installation/) and then run:

```
git clone https://github.com/niklasbuschmann/contrast.git
cd contrast
gem install bundler jekyll jekyll-feed
bundle exec jekyll serve
```