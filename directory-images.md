---
layout: default
title: Image Assets
---

# Image Assets

{% assign jpg_files = site.static_files | where: "extname", ".jpg" %}
{% assign jpeg_files = site.static_files | where: "extname", ".jpeg" %}
{% assign png_files = site.static_files | where: "extname", ".png" %}
{% assign gif_files = site.static_files | where: "extname", ".gif" %}
{% assign webp_files = site.static_files | where: "extname", ".webp" %}

{% assign image_files = jpg_files | concat: jpeg_files | concat: png_files | concat: gif_files | concat: webp_files %}
{% assign images_in_folder = image_files | where_exp: "file", "file.path contains '/assets/images/'" %}

{% for image in images_in_folder %}
- [{{ image.name }}]({{ image.path | relative_url }})
{% endfor %}