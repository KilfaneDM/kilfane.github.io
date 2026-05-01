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
.photo-grid img {
  width: 100%;
  height: 250px;
  object-fit: cover;
}
</style>

<div class="photo-grid">
{% assign images = site.static_files | where_exp: "file", "file.path contains page.gallery_path" %}
{% for image in images %}
  <img src="{{ image.path }}" alt="photo">
{% endfor %}
</div>