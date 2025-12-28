---
layout: page
title: Video
permalink: /video/
---

<style>
.video-grid{
  display:grid;
  grid-template-columns:repeat(3,minmax(0,1fr));
  gap:16px;
}
.video-grid a{text-decoration:none;color:inherit}
.video-grid img{
  width:100%;
  height:200px;
  object-fit:cover;
  border-radius:14px;
  display:block;
}
.caption{
  font-size:14px;
  margin-top:6px;
}
@media (max-width:900px){
  .video-grid{grid-template-columns:repeat(2,1fr)}
}
@media (max-width:560px){
  .video-grid{grid-template-columns:1fr}
}
</style>

<div class="video-grid">
  {% for post in site.categories.video %}
    <a href="{{ post.url | relative_url }}">
      <img src="{{ post.thumbnail }}" alt="{{ post.title }}">
      <div class="caption">{{ post.title }}</div>
    </a>
  {% endfor %}
</div>
