---
layout: single
title: "Photography"
permalink: /ground/
gallery_path: assets/images/ground
---

{% assign images = site.static_files | where_exp: "file", "file.path contains page.gallery_path" %}
{% for image in images %}
  ![photo]({{ image.path }})
{% endfor %}