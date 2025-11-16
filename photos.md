---
layout: page
title: "Photos"
permalink: /photos/
---

<link rel="stylesheet" href="{{ '/assets/css/photos.css' | relative_url }}" />

# Photos

{% assign pics = site.static_files | where_exp: "f", "f.path contains '/assets/images/mobile/'" | sort: "path" %}
{% if pics and pics.size > 0 %}
<div class="gallery">
  {% for file in pics %}
  <figure class="photo">
    <a href="{{ file.path | relative_url }}" target="_blank" rel="noopener">
      <img src="{{ file.path | relative_url }}" alt="{{ file.name }}" loading="lazy" />
    </a>
    <figcaption>{{ file.name }}</figcaption>
  </figure>
  {% endfor %}
</div>
{% else %}
<p>No photos found in the pictures folder.</p>
{% endif %}