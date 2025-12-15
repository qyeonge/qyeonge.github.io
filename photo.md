---
layout: page
title: Photo
permalink: /photo/
---

<ul>
  {% for post in site.categories.photo %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <small> — {{ post.date | date: "%Y-%m-%d" }}</small>
    </li>
  {% endfor %}
</ul>
