---
title: "Photos"
permalink: "/photos/"
layout: page
---

# Travel Photo Gallery 📸

All the amazing photos from my travel adventures, automatically collected from my blog posts!

<div class="photo-gallery">
  {% for post in site.posts reversed %}
    {% capture post_images %}
      {% assign images_found = false %}
      {% assign content_lines = post.content | split: '![' %}
      {% for line in content_lines %}
        {% if line contains 'images/mobile' %}
          {% assign images_found = true %}
          {% break %}
        {% endif %}
      {% endfor %}
      {{ images_found }}
    {% endcapture %}
    
    {% if post_images contains 'true' %}
      <div class="photo-section">
        <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
        <p class="photo-date">{{ post.date | date: "%B %d, %Y" }}{% if post.country %} • {{ post.country }}{% endif %}</p>
        
        <div class="photo-grid">
          {% assign lines = post.content | split: '![' %}
          {% for line in lines %}
            {% if line contains 'images/mobile' %}
              {% assign parts = line | split: '](../assets/' %}
              {% if parts.size > 1 %}
                {% assign alt_text = parts[0] %}
                {% assign img_path_part = parts[1] | split: ')' | first %}
                {% assign img_path = '/assets/' | append: img_path_part %}
                
                <div class="photo-item">
                  <img src="{{ img_path | relative_url }}" alt="{{ alt_text }}" loading="lazy">
                  {% if alt_text != '' %}
                    <p class="photo-caption">{{ alt_text }}</p>
                  {% endif %}
                </div>
              {% endif %}
            {% endif %}
          {% endfor %}
        </div>
      </div>
    {% endif %}
  {% endfor %}
</div>

<div class="photo-stats">
  {% assign total_images = 0 %}
  {% assign countries = site.posts | map: 'country' | uniq | compact %}
  {% for post in site.posts %}
    {% assign post_content = post.content | split: 'images/mobile' %}
    {% assign post_images = post_content.size | minus: 1 %}
    {% assign total_images = total_images | plus: post_images %}
  {% endfor %}
  
  <p><strong>{{ total_images }}</strong> photos • <strong>{{ site.posts.size }}</strong> trips • <strong>{{ countries.size }}</strong> countries</p>
</div>
