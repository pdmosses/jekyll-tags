{%- comment -%}
  Use {% include tags/page.md slug=STRING %}
  for a Markdown section summary of tags with the specified slug,
  including a list of links to pages and posts that have such a tag.

  When the slug parameter is omitted, the name of the including file is used.
{%- endcomment -%}

{%- assign current_page_slug = page.url | split: "/" | last -%}

{%- assign page_slug = include.slug | default: current_page_slug -%}

{% include tags/tagged_pages.html slug=page_slug %}

## #{{ page_slug }}

{% assign tag_url = page_slug | prepend: "/tag/" -%}
{%- if tag_url == page.url -%}
{{ page.description }}
{%- endif %}

Uses: {{ tagged_pages.size }}

{% for tagged_page in tagged_pages %}

- <a href="{{ site.url }}{{ site.baseurl }}{{ tagged_page.url }}">{{ tagged_page.title }}</a>

  Tags: 
  {%- for tag_3 in tagged_page.tags %}
  \#{% include tags/tag_link.html tag=tag_3 %}
  {%- endfor %}

  {{ tagged_page.description }}
{% endfor %}

{%- assign current_page_slug = nil -%}
{%- assign page_slug = nil -%}
{%- assign tag_url = nil -%}
{%- assign tagged_page = nil -%}
{%- assign tagged_pages = nil -%}
