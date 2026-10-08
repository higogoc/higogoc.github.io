---
permalink: /
title: "Creating unbiased AI technologies for the medical field"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

{% for paragraph in site.data.profile.bio %}{{ paragraph }}

{% endfor %}

<ul class="ap-chips">
{%- for keyword in site.data.profile.keywords %}
  <li>{{ keyword }}</li>
{%- endfor %}
</ul>

## Research

{% for theme in site.data.research %}
<div class="ap-theme">
  <h3 class="ap-theme__title">{{ theme.title }}</h3>
  <p class="ap-theme__summary">{{ theme.summary }}</p>
  {%- if theme.topics %}
  <ul>
  {%- for topic in theme.topics %}
    <li>{{ topic }}</li>
  {%- endfor %}
  </ul>
  {%- endif %}
  {%- if theme.keywords %}
  <ul class="ap-chips">
  {%- for keyword in theme.keywords %}
    <li>{{ keyword }}</li>
  {%- endfor %}
  </ul>
  {%- endif %}
  {%- if theme.links %}
  <p class="ap-entry__links">
  {%- for link in theme.links %}<a href="{{ link.href }}">{{ link.label }}</a>{% endfor %}
  </p>
  {%- endif %}
</div>
{% endfor %}

## News

<div class="ap-news">
{%- for item in site.data.news %}
  <div class="ap-news__date">{{ item.date }}</div>
  <div class="ap-news__body">
    {%- if item.tag %}<span class="ap-news__tag">{{ item.tag }}</span>{% endif -%}
    {{ item.text }}
    {%- if item.outlet %} <a href="{{ item.href }}">{{ item.outlet }}</a>
    {%- elsif item.href %} <a href="{{ item.href }}">Link</a>{% endif %}
  </div>
{%- endfor %}
</div>
