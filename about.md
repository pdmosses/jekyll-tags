---
layout: page
title: About
permalink: /about/
---
# About this website

Jekyll collects [tags and categories](https://jekyllrb.com/docs/posts/#tags-and-categories)
from the front matter of all blog posts, and makes them available via `site.tags`.
However, Jekyll does not provide any support at all for tags on ordinary pages,
nor on collections. Jekyll also leaves it to the user to create a page listing
all the current tags, and for each tag, to list all the posts that have been
tagged with it.

This website uses Liquid code to support collection of tags on ordinary pages.
It includes a [tag index] page, which displays a cloud of all used tags,
visualising how frequently each tag is used. It also provides a template for
creating pages that list all the pages (and posts) tagged by individual tags.
Both the tag index page and the tag page template are in Markdown, and their
contents can easily be adjusted by users who are not familiar with Liquid.

Tags here are converted internally to so-called slugs. For example, the tags
`Topic A` and `Topic-A` are both converted to the slug `topic-a`. This avoids
duplication of tags due to case differences. (Jekyll normally treats tags
on posts literally.)

The Liquid code implementing support for tags is theme-independent. To display
tags on the pages (and posts) where they are used, however, requires some
theme-dependent customisation. Adding display of tags to the basic Jekyll theme 
[Minima](https://github.com/jekyll/minima) involved inserting one line in a copy
of the default layout, and adding a few lines of CSS to style the display.

These web pages are generated on GitHub pages.

## User Guide

The [user guide] gives an overview of the API for adding tag support to 
Jekyll websites.

## Demonstrations

The [test pages] show how some simple test tags appear on dummy test pages.

The [demo] folder contains an extensively-tagged collection of dummy pages:
it has 97 tags, with several tags used more than 100 times.

The [profiling] data shows the overhead due to tag processing.

## Issues

Reports of any difficulties with using the code provided here are welcome,
and can be submitted as issues on the [project site on GitHub].

## Acknowledgements

Previous projects have shown how to implement enhanced tag support for posts
in Jekyll, and provided inspiration for this project. The contribution of the
present project is an implementation of tag support including non-post pages,
and facilitation of the creation of a collection of tag pages.

[Tag Index]: {{ site.url }}{{ site.baseurl }}/tag/
[User Guide]: {{ site.url }}{{ site.baseurl }}/docs/user-guide/
[Jekyll]: https://jekyllrb.com
[Liquid]: https://jekyllrb.com/docs/liquid/
[Test Pages]: {{ site.url }}{{ site.baseurl }}/docs/test/
[Demo]: {{ site.url }}{{ site.baseurl }}/docs/demo/
[Profiling]: {{ site.url }}{{ site.baseurl }}/docs/user-guide/profile.html
[project site on GitHub]: https://github.com/pdmosses/tags
