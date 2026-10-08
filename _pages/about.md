---
permalink: /
title: "Seoi Jeong - Homepage"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

{% for paragraph in site.data.profile.bio %}{{ paragraph | markdownify | remove: "<p>" | remove: "</p>" | strip }}

{% endfor %}

<ul class="ap-chips">
{%- for keyword in site.data.profile.keywords %}
  <li>{{ keyword }}</li>
{%- endfor %}
</ul>

## News

<div class="ap-news">
{%- for item in site.data.news %}
  <div class="ap-news__date">{{ item.date }}</div>
  <div class="ap-news__body">
    {%- if item.tag %}<span class="ap-news__tag">{{ item.tag }}</span>{% endif -%}
    {{ item.text | markdownify | remove: "<p>" | remove: "</p>" | strip }}
    {%- if item.outlet %} <a href="{{ item.href }}">{{ item.outlet }}</a>
    {%- elsif item.href %} <a href="{{ item.href }}">Link</a>{% endif %}
  </div>
{%- endfor %}
</div>
