---
title: "Photos"
permalink: "/photos/"
layout: page
---

---
title: "Photos"
permalink: "/photos/"
layout: page
---

# Travel Photo Gallery 📸

<div class="photo-grid-container">
  <!-- Korea Photos -->
  <div class="grid-photo-item" onclick="openLightbox('/assets/images/mobile/20241129_214639.jpg', 'First day photo', 'Første dag', 'August 01, 2025', 'Korea', '/2025-08-01-First-Day-In-Korea/')">
    <img src="/assets/images/mobile/20241129_214639.jpg" alt="First day photo" loading="lazy">
  </div>
  
  <div class="grid-photo-item" onclick="openLightbox('/assets/images/mobile/20250730_061913.jpg', 'Travel photo', 'Travel memories', 'July 30, 2025', 'Korea', '#')">
    <img src="/assets/images/mobile/20250730_061913.jpg" alt="Travel photo" loading="lazy">
  </div>
  
  <!-- Add more photos automatically from posts -->
  {% comment %}
  {% for post in site.posts reversed %}
    {% if post.content contains 'assets/images/mobile' %}
      {% assign post_content = post.content | split: '![' %}
      {% for content_part in post_content %}
        {% if content_part contains 'assets/images/mobile' %}
          {% assign img_info = content_part | split: '](../assets/images/mobile/' %}
          {% if img_info.size > 1 %}
            {% assign alt_text = img_info[0] %}
            {% assign img_file = img_info[1] | split: ')' | first %}
            
            <div class="grid-photo-item" onclick="openLightbox('/assets/images/mobile/{{ img_file }}', '{{ alt_text | escape }}', '{{ post.title | escape }}', '{{ post.date | date: "%B %d, %Y" }}', '{{ post.country }}', '{{ post.url | relative_url }}')">
              <img src="/assets/images/mobile/{{ img_file }}" alt="{{ alt_text }}" loading="lazy">
            </div>
          {% endif %}
        {% endif %}
      {% endfor %}
    {% endif %}
  {% endfor %}
  {% endcomment %}
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
  <p><strong>2</strong> photos from <strong>1</strong> country</p>
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
