---
title: "Photos"
permalink: "/photos/"
layout: page
---

# Travel Photo Gallery 📸

<div class="photo-grid-container">
  {% for post in site.posts reversed %}
    {% assign lines = post.content | split: '![' %}
    {% for line in lines %}
      {% if line contains 'images/mobile' %}
        {% assign parts = line | split: '](../assets/' %}
        {% if parts.size > 1 %}
          {% assign alt_text = parts[0] %}
          {% assign img_path_part = parts[1] | split: ')' | first %}
          {% assign img_path = '/assets/' | append: img_path_part %}
          
          <div class="grid-photo-item" onclick="openLightbox('{{ img_path | relative_url }}', '{{ alt_text | escape }}', '{{ post.title | escape }}', '{{ post.date | date: "%B %d, %Y" }}', '{{ post.country }}', '{{ post.url | relative_url }}')">
            <img src="{{ img_path | relative_url }}" alt="{{ alt_text }}" loading="lazy">
          </div>
        {% endif %}
      {% endif %}
    {% endfor %}
  {% endfor %}
</div>

<!-- Lightbox Modal -->
<div id="lightbox" class="lightbox" onclick="closeLightbox()">
  <div class="lightbox-content" onclick="event.stopPropagation()">
    <span class="lightbox-close" onclick="closeLightbox()">&times;</span>
    <img id="lightbox-image" src="" alt="">
    <div class="lightbox-footer">
      <p id="lightbox-caption"></p>
      <p id="lightbox-info"><a id="lightbox-link" href="">View full post</a></p>
    </div>
  </div>
</div>

<div class="photo-stats">
  {% assign total_images = 0 %}
  {% assign countries = site.posts | map: 'country' | uniq | compact %}
  {% for post in site.posts %}
    {% assign post_content = post.content | split: 'images/mobile' %}
    {% assign post_images = post_content.size | minus: 1 %}
    {% assign total_images = total_images | plus: post_images %}
  {% endfor %}
  
  <p><strong>{{ total_images }}</strong> photos from <strong>{{ countries.size }}</strong> countries</p>
</div>

<script>
function openLightbox(imageSrc, caption, postTitle, postDate, country, postUrl) {
  document.getElementById('lightbox').style.display = 'flex';
  document.getElementById('lightbox-image').src = imageSrc;
  document.getElementById('lightbox-caption').textContent = caption || 'Travel photo';
  
  let info = postTitle + ' • ' + postDate;
  if (country) {
    info += ' • ' + country;
  }
  document.getElementById('lightbox-info').innerHTML = info + ' • <a href="' + postUrl + '">View full post</a>';
  document.getElementById('lightbox-link').href = postUrl;
  
  // Prevent body scroll when lightbox is open
  document.body.style.overflow = 'hidden';
}

function closeLightbox() {
  document.getElementById('lightbox').style.display = 'none';
  document.body.style.overflow = 'auto';
}

// Close lightbox with Escape key
document.addEventListener('keydown', function(event) {
  if (event.key === 'Escape') {
    closeLightbox();
  }
});
</script>
