---
title: User Guide
description: an overview of the API for adding tag support to Jekyll websites 
---
# User Guide

This guide indicates how to add support for tags on pages (and extra support for
tags on posts) to a static website generated using Jekyll.

The reader is assumed to be familiar with [Jekyll] and [Liquid].

## Folders

Create the following files and folders:

- [`_includes/tags/*`](https://github.com/pdmosses/tags/tree/master/_includes/tags/): 
  partials for implementing tag support in Liquid (10 files)
  
  - `page.md` is included in the source page for a single tag; the text and layout
    can be freely updated

- [`_layouts/default.html`](https://github.com/pdmosses/tags/tree/master/_layouts/default.html):
  needs to be customised to show links to tag pages on tagged pages;
  this is a copy from the Minima theme, just adding the inclusion of `tags/nav.html`

- [`tag/*`](https://github.com/pdmosses/tags/tree/master/tag/):
  
  - `index.md` is the source for the tag overview page; the text and layout
    can be freely updated
  
  - `TAG.md` is a template for the source page of a single tag; additional
    front matter or text can be added

- [`_tag/`](https://github.com/pdmosses/tags/tree/master/_tag/): 
  the folder for the collection of tag page sources; all file names should be
  in slugified form
  
  - when `/_tag/NAME.md` is a copy of `/tag/TAG.md`, the tag page that lists
  all pages tagged with `NAME` (or with tags whose slugified form is `NAME`)
  is output at URL `.../tag/NAME`

The current version of `tag/index.md` combines the tag cloud, the list of all
tag descriptions, and the listings of any tags that do not have separate pages.
To show these items on different pages, the Liquid code in `includes/tags/`
would need to be updated.

## Configuration

Update the file `_config.yml` by adding the following lines:

```yaml
exclude:
  - tag/TAG.md

collections:
  tag:
    output: true
    permalink: /:collection/:name

defaults:
  -
    scope:
      path: ""
      type: "tag"
    values:
      title: "Tag index"
      layout: "default"
      excerpt: "List of tagged pages"
```

The defaults for the tag pages can be changed. The default for `excerpt` is
an optimisation: processing the page for each tag involves inspecting all
pages in `site.pages`, to find the pages with corresponding tags; and
when the tag pages do not have explicit excerpt fields, it appears that
Jekyll processes them twice.

## Implementation

The tag support is implemented entirely in Liquid using the partials in
[`_includes/tags/`](https://github.com/pdmosses/tags/tree/master/_includes/tags/): 

- [`_includes/tags/cloud.html`](https://github.com/pdmosses/tags/tree/master/_includes/tags/cloud.html)
  gives an HTML paragraph containing a sequence of space-separated HTML links,
  each scaled according to the number of uses.
  
- [`_includes/tags/descriptions.html`](https://github.com/pdmosses/tags/tree/master/_includes/tags/descriptions.html)
  gives an HTML description list showing all tags and how many times each is used.
  
- [`_includes/tags/new.html`](https://github.com/pdmosses/tags/tree/master/_includes/tags/new.html)
  gives HTML sections listing tags that do not have pages in `/_tag/`.

- [`_includes/tags/page.md`](https://github.com/pdmosses/tags/tree/master/_includes/tags/page.md)
  gives a Markdown section summary of tags with the specified slug,
  including a list of links to pages and posts that have such a tag.

- [`/tag/index.md`](https://github.com/pdmosses/tags/tree/master/tag/index.md)
  gives Markdown sections for a tag cloud, a list of tag descriptions, and
  listings of tags that do not have pages in `/_tag/`.

The remaining partials are used in the above files for low-level formatting
and to initialise variables to derived data. 

The [profiling] data shows the overhead due to tag processing. Some of it may be
due to extensive use of inclusion of partials.

[Profiling]: {{ site.url }}{{ site.baseurl }}/docs/user-guide/profile.html

[Jekyll]: https://jekyllrb.com
[Liquid]: https://jekyllrb.com/docs/liquid/
