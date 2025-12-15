---
layout: page
title: Photo
permalink: /photo/
---

<style>
  .photo-grid{
    display:grid;
    grid-template-columns:repeat(3, minmax(0,1fr));
    gap:12px;
  }
  .photo-grid a{display:block}
  .photo-grid img{
    width:100%;
    height:240px;
    object-fit:cover;
    border-radius:14px;
    display:block;
  }
  @media (max-width:900px){
    .photo-grid{grid-template-columns:repeat(2,1fr)}
    .photo-grid img{height:220px}
  }
  @media (max-width:560px){
    .photo-grid{grid-template-columns:1fr}
    .photo-grid img{height:260px}
  }

  /* lightbox */
  .lb{
    position:fixed; inset:0;
    background:rgba(0,0,0,.8);
    display:none; align-items:center; justify-content:center;
    padding:24px;
    z-index:9999;
  }
  .lb.open{display:flex}
  .lb img{max-width:95vw; max-height:90vh; border-radius:14px}
</style>

<div class="photo-grid">
  {% assign photos = site.categories.photo %}
  {% for post in photos %}
    {% if post.image %}
      <a href="{{ post.image | relative_url }}" class="lb-open" aria-label="{{ post.title }}">
        <img src="{{ post.image | relative_url }}" alt="{{ post.title }}">
      </a>
    {% endif %}
  {% endfor %}
</div>

<div class="lb" id="lightbox" role="dialog" aria-modal="true">
  <img id="lightboxImg" alt="">
</div>

<script>
  (function(){
    const lb = document.getElementById('lightbox');
    const lbImg = document.getElementById('lightboxImg');

    document.querySelectorAll('.lb-open').forEach(a=>{
      a.addEventListener('click', (e)=>{
        e.preventDefault();
        lbImg.src = a.getAttribute('href');
        lb.classList.add('open');
      });
    });

    lb.addEventListener('click', ()=> lb.classList.remove('open'));
    document.addEventListener('keydown', (e)=>{
      if(e.key === 'Escape') lb.classList.remove('open');
    });
  })();
</script>
