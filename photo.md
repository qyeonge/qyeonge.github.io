---
layout: page
title: Photo
permalink: /photo/
---

<style>
  .photo-grid{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:12px}
  .photo-grid img{width:100%;height:240px;object-fit:cover;border-radius:14px;display:block}
  @media (max-width:900px){.photo-grid{grid-template-columns:repeat(2,1fr)}}
  @media (max-width:560px){.photo-grid{grid-template-columns:1fr}}
</style>

<div class="photo-grid">
  {% for post in site.categories.photo %}
    <a href="{{ post.url | relative_url }}" data-full="{{ post.image | relative_url }}" class="photo-item">
      <img src="{{ post.image | relative_url }}" alt="{{ post.title }}">
    </a>
  {% endfor %}
</div>
