---
layout: single
title: "Drone Photography"
permalink: /drone/
gallery_path: assets/images/drone
---

{% assign images = site.static_files | where_exp: "file", "file.path contains page.gallery_path" %}
{% for image in images %}
  ![photo]({{ image.path }})
{% endfor %}