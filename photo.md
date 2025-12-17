---
layout: page
title: Photo
permalink: /photo/
---

<style>
  .photo-grid{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:12px}
  .photo-grid a{display:block}
  .photo-grid img{width:100%;height:240px;object-fit:cover;border-radius:14px;display:block}
  @media (max-width:900px){.photo-grid{grid-template-columns:repeat(2,1fr)}}
  @media (max-width:560px){.photo-grid{grid-template-columns:1fr}}
  dialog#lb{border:0;border-radius:14px;max-width:min(92vw,1100px);padding:0}
  dialog#lb::backdrop{background:rgba(0,0,0,.75)}
  #lb img{width:100%;height:auto;display:block}
</style>

<div class="photo-grid">
  {% assign posts = site.categories.photo %}
  {% for post in posts %}
    <a href="{{ post.url | relative_url }}"
       class="thumb"
       data-full="{{ post.image | relative_url }}">
      <img src="{{ post.image | relative_url }}" alt="{{ post.title }}">
    </a>
  {% endfor %}
</div>

<dialog id="lb" aria-label="Image preview">
  <img id="lbImg" alt="">
</dialog>

<script>
  const lb = document.getElementById('lb');
  const lbImg = document.getElementById('lbImg');

  document.querySelectorAll('.thumb').forEach(a => {
    a.addEventListener('click', (e) => {
      // 포스트 페이지로 이동 대신 "크게 보기" 실행
      e.preventDefault();
      const full = a.getAttribute('data-full');
      lbImg.src = full;
      lb.showModal();
    });
  });

  lb.addEventListener('click', () => lb.close());
</script>
