---
layout: default
title: Tags
description: Tag cloud and descriptions
---
# Tag cloud

The tag cloud lists all used tags in alphabetical order. The size of the text
is related to the number of times the tag is used; the exact number is shown
on the tag pages, and in the list below.

{% include tags/cloud.html %}

# Tag index

Each tag is listed below, together with the number of pages on which it is used,
and its description (if any). The site maintainer can add a description for
the tag `NAME` by including it in the front matter of the file `_tag/NAME.md`.

{% include tags/descriptions.html %}

# New tags

If a section for a new tag `NAME` is shown below, the site maintainer should
copy the tag page template file from `tag/TAG.md` to `/_tag/NAME.md`. 
Optionally, text can be added to the `description` field of the tag page; the
default for the `title` field for all tags is set to "Tag index" in `config.yml`,
and can be overridden for individual tags.

{% include tags/new.html %}
