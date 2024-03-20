---
layout: post
title: "GitHub: Full minima functionality enabled"
categories:
  - GitHub
tags:
  - GitHub Pages
  - Jekyll
---

I have solved the problems I was having with the Jekyll configuration for my
GitHub Pages. It seems that the version of the **minima** theme used by GitHub
is an older release; it was necessary to use a `remote-theme` setting to pull
down the latest version of the theme to support all the documented features.

The breakthrough was as simple as reading the **_config.yml** file used by the
GitHub Pages for the **jekyll/minima** theme itself:

* https://github.com/jekyll/minima/blob/master/_config.yml

## Configuration changes

All that was really needed was to comment out the `theme` setting and replace
it with a `remote-theme` setting, like so:

``` yaml
# As of November 2023, GitHub Pages still uses Minima 2.5.1
# (https://pages.github.com/versions/). 
# If you want to use the latest Minima version on GitHub Pages, use the
# following setting and add comment out the "theme: minima" line.
remote_theme: jekyll/minima
# theme: minima
```

## Features enabled

This has ensured that the following features (and probably some others I
haven't found) now work:

* Skins
* Social media icons & links
