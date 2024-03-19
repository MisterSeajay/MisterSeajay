---
layout: post
title: Learning about GitHub Pages
---

I'm starting to add GitHub pages to this "site", i.e. a personal page in GitHub.
This page is a short collection of notes about how I managed it, especially if
there were any gotchas even when following the official documentation.

## Official Documentation

It's probably best to open and read these pages first, then come back to the
notes below:

* [GitHub Pages Documentation](https://docs.github.com/en/pages)
* [About GitHub Pages and Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll)
* [Adding a theme using Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-a-theme-to-your-github-pages-site-using-jekyll)

## Setting up

You enable GitHub pages via the **Settings** for your repository, where there
should be a **Pages** option in the menu at the left hand side.

### Custom domain

In brief, GitHub allows users to host pages under the _owner.github.io_ domain,
where _owner_ is your GitHub username. You can use your own custom domain if you
want. If you want to use a custom domain name you need to set up a CNAME in your
own domain that points to _owner.github.io_.

### Document structure

I have chosen to put my documents in the `/docs/` subfolder in my **main**
branch, rather than use a separate `gh-pages` branch, at least for now. It seems
a more intuitive to just use one branch from a personal GitHub Pages site.

## Jekyll

Formatting for GitHub pages is provided by Jekyll, which can transform Markdown
(and other markups) into themed websites, with little more than a few lines of
YAML at the top of each page (known as _Front Matter_) and/or in a
`/docs/_config.yml` file.

### Defaults

Simply adding the `index.md` file in the `/docs/` folder seems to have created
a simple site.

## Front Matter

Each page in the Jekyll-themed site should have some lines of YAML at the very
top, known as _Front Matter_.

* [Front Matter documentation](https://jekyllrb.com/docs/front-matter/)
