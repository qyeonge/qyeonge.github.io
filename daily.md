---
layout: page
title: Daily
permalink: /daily/
---

<ul>
  {% assign daily_posts = site.categories.daily %}
  {% for post in daily_posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <small> — {{ post.date | date: "%Y-%m-%d" }}</small>
    </li>
  {% endfor %}
</ul>

{% if site.categories.daily == nil or site.categories.daily.size == 0 %}
<p>No daily posts yet.</p>
{% endif %}
