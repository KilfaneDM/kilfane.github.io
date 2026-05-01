---
layout: single
title: "Photography"
permalink: /ground/
gallery_path: assets/images/ground
---

<style>
.photo-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
}
.photo-grid a img {
  width: auto;
  height: 100%;
  object-fit: contain;
}

/* Lightbox */
.lightbox {
  display: none;
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.9);
  z-index: 9999;
  align-items: center;
  justify-content: center;
}
.lightbox.active { display: flex; }
.lightbox img {
  max-width: 90%;
  max-height: 90vh;
  object-fit: contain;
}
.lightbox-close {
  position: fixed;
  top: 20px; right: 30px;
  color: white;
  font-size: 40px;
  cursor: pointer;
}
</style>

<div class="lightbox" id="lightbox">
  <span class="lightbox-close" onclick="closeLightbox()">×</span>
  <img id="lightbox-img" src="" alt="">
</div>

<div class="photo-grid">
{% assign images = site.static_files | where_exp: "file", "file.path contains page.gallery_path" %}
{% for image in images %}
  <a onclick="openLightbox('{{ image.path }}')">
    <img src="{{ image.path }}" alt="photo">
  </a>
{% endfor %}
</div>

<script>
function openLightbox(src) {
  document.getElementById('lightbox-img').src = src;
  document.getElementById('lightbox').classList.add('active');
}
function closeLightbox() {
  document.getElementById('lightbox').classList.remove('active');
}
document.getElementById('lightbox').addEventListener('click', function(e) {
  if (e.target === this) closeLightbox();
});
</script>