---
title: Test Pages
---
# Test Pages

The tags listed below should automatically appear on the linked test pages.
Each tag is linked to a tag page that lists all the pages and posts currently 
using it, together with any `description` set in the front matter.

For #[Tag D], no separate tag page has been created, so its uses are listed
on the main [tags index] page; for #[Tag Z], in contrast, a tag page has been
created but the tag has not been used.

- [Test Page A](test-a.html) tags: #[Tag A], #[Tag B]
- [Test Page B](test-b.html) tags: #[Tag b], #[Tag a]
- [Test Page C](test-c.html) tags: #[Tag C], #[Tag A]
- [Test Page D](test-d.html) tags: #[Tag D]
- [Test Page E](test-e.html) tags empty
- [Test Page F](test-f.html) no tags
- [Test Page G](test-g.html) tags: #[Tag A], #[tag-b], #[tag-a], #[Tag C], #[Tag-A], #[Tag A], #[tag-a]
- [Welcome Post]({{ site.url }}{{ site.baseurl }}/jekyll/update/2020/05/19/welcome-to-jekyll.html) tags: #[Tag A], #[Tag B]

[Tags Index]: {{ site.url }}{{ site.baseurl }}/tag/
[tag-a]: {{ site.url }}{{ site.baseurl }}/tag/tag-a
[Tag A]: {{ site.url }}{{ site.baseurl }}/tag/tag-a
[tag-b]: {{ site.url }}{{ site.baseurl }}/tag/tag-b
[Tag B]: {{ site.url }}{{ site.baseurl }}/tag/tag-b
[Tag C]: {{ site.url }}{{ site.baseurl }}/tag/tag-c
[Tag D]: {{ site.url }}{{ site.baseurl }}/tag/#tag-d
[Tag Z]: {{ site.url }}{{ site.baseurl }}/tag/tag-z
