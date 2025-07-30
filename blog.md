---
layout: default
title: "Blog"
---

<div class="blog-posts">
  {% for post in site.posts %}
    <article class="blog-post-preview">
      <header>
        <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
        {% include meta.html post=post %}
      </header>
      
      <div class="post-content">
        {{ post.excerpt }}
      </div>
      
      <div class="read-more">
        <a href="{{ post.url | relative_url }}" class="read-more-btn">Read More →</a>
      </div>
    </article>
  {% endfor %}
</div>
