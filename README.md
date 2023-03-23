---
date: 2023-02-28 12:30:18
update: 2023-03-20 13:03:13
---
# Publisher plugin for MkDocs

[![PyPI version](https://badge.fury.io/py/mkdocs-blog-in.svg)](https://badge.fury.io/py/mkdocs-blog-in)
[![Github All Releases](https://img.shields.io/github/downloads/mkusz/mkdocs-blog-in/total.svg)]()

Publishing platform plugins for [MkDocs](https://www.mkdocs.org/) that include:

- pub-auto-nav - building site navigation right from files (no need for manual definition in config)
- pub-blog - adds blogging capability,
- pub-minifier - file size optimization (good for SEO and overall page size optimization).

## Installation

```commandline
pip install mkdocs-publisher
```

## Basic usage

> **Note**
> As a base for any development, mkdocs-material theme was used. If you are willing to use any other theme, you may (or may not) face some issues. If this happens, please submit an issue.

> **Warning**
> Consider this plugin as a beta, so before any use make sure you have a backup of your data.

If you have found any issue, have an idea for a feature, please submit an issue.

## Image optimization

Image optimization is needed for optimal web speed loading that is needed for better scoring on search engines (part of proper SEO). The best image optimization that reduce image file size but not image quality.

Since 2 most used image formats are PNG and JPEG, this plugin offers an image optimization option. Tools used for image optimization were chosen to fulfill both main image optimization purposes: high quality with small file size.

## Features

List of included features (more documentation is needed):

- automatic blog post index page generation with blog post teasers based on delimiter inside a blog post and own template (delimiter can be changed in plugin config in mkdocs.yaml),
- blog post/page update date based on blog post metadata,
- separate directory for blog post documents with auto-generated separate navigation (blog posts are sorted from newest to oldest)
- home page set to blog post index with possibility to rename,
- auto-adding link to full blog post from blog post index file (under each post that has teaser delimiter, if delimiter is not present, then full post is inside post index file, but is preserved in blog post navigation and site map).
- added sub-pages for blog posts: archive, categories, tags

## How To

[TODO]

## Todo's

A full list of planned developments can be found on [this documentation page](docs/05_dev/01_todo.md).

## Version history

### 0.4.0

General:

- changed: project rename
- added: cross configuration of blog and auto-nav plugins:
  - blog does not add auto-nav meta files
  - auto-nav automatically adds blog directory to skipped directories since it will be built by blog
  - if one of the plugins is not enabled, other is not using its values
- add: documentation

Blog:

- added: possibility to choose a blog as a starting page with option to define manually blog in nav configuration
- added: `slug` config option for setting an entire blog's main directory URL
- changed: internal file structure refactor with new global plugin config (BlogConfig class) that will help with further development with small fixes and improvements
- changed: blog subdirectory navigation creation (entry path needs to be equal to subdirectory name)
- fixed: live reload infinite loop during `serve` caused by temporary files created and removed in blog directory
- fixed: navigation is no longer overridden by a blog (if there is no other nav, blog will create on with recent posts as a main page)

Minifier (new plugin):

- added: PNG image minifier (using: pngquant and oxipng)
- added: JPG image minifier (using: mozjpeg)
- added: SVG image minifier (using: svgo)
- added: HTML file minifier (using: html-minifier)
- added: CSS file minifier (using: postcss with plugins: cssnano, svgo)
- added: JS file minifier (using: uglifyjs)

Auto-nav (new plugin):

- added: build navigation based on file names
- added: directory metadata and additional settings can be set in a frontmatter of `*.md` file (default to `README.md`)
- added: configuration of sort prefix delimiter
- added: sort prefix removal in URL and site files
- added: read file title from `title` meta data key

### 0.3.0 - 2023.02.20

- fixed: for wrong directory structure in site-packages after install

### 0.2.0 - 2023.02.19

- added: sub-pages for archive, categories, blog
- added: configurable blog posts pagination with page navigation
- added: interface language change: EN and PL (help wanted with more languages)
- added: possibility to override for all interface text elements

### 0.1.0 - initial release

- added: blog post update date based on metadata
- added: blog post URL link based on metadata
- added: blog post tags and categories based on metadata
- added: support for blog post teaser
- added: auto generation of blog posts navigation
