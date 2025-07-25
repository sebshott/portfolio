---
layout: home-page
title: Gallery
permalink: /gallery/
---

<style>
/* Gallery Grid Styles */
.gallery-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

.gallery-grid {
  columns: 4;
  column-gap: 20px;
  margin-top: 20px;
}

@media (max-width: 1024px) {
  .gallery-grid {
    columns: 3;
  }
}

@media (max-width: 768px) {
  .gallery-grid {
    columns: 2;
  }
}

@media (max-width: 480px) {
  .gallery-grid {
    columns: 1;
  }
}

.gallery-item {
  break-inside: avoid;
  margin-bottom: 20px;
  cursor: pointer;
  transition: transform 0.3s ease;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  background: white;
  position: relative;
}

.gallery-item:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 24px rgba(0,0,0,0.15);
}

/* Varied heights for Pinterest effect */
.gallery-item:nth-child(3n+1) img {
  height: 200px;
}

.gallery-item:nth-child(3n+2) img {
  height: 280px;
}

.gallery-item:nth-child(3n+3) img {
  height: 320px;
}

.gallery-item:nth-child(7n+1) img {
  height: 350px;
}

.gallery-item:nth-child(11n+1) img {
  height: 240px;
}

.gallery-item img {
  width: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.3s ease;
}

.gallery-item:hover img {
  transform: scale(1.05);
}

.gallery-item-title {
  padding: 15px;
  font-size: 14px;
  font-weight: 600;
  color: #333;
  text-align: left;
  line-height: 1.3;
  background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
}

/* Special styling for video items */
.gallery-item.video-item {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.gallery-item.video-item .gallery-item-title {
  color: white;
  background: rgba(255,255,255,0.1);
  backdrop-filter: blur(10px);
}

/* Lightbox Styles */
.lightbox {
  display: none;
  position: fixed;
  z-index: 9999;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0,0,0,0.8);
}

.lightbox-content {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  max-width: 90vw;
  max-height: 90vh;
  text-align: center;
}

.lightbox-image {
  max-width: 100%;
  max-height: 75vh;
  object-fit: contain;
  display: block;
  margin: 0 auto;
}

.lightbox-video {
  width: 80vw;
  height: 45vw;
  max-width: 800px;
  max-height: 450px;
  display: block;
  margin: 0 auto;
}

.lightbox-close {
  position: absolute;
  top: 15px;
  right: 25px;
  color: white;
  font-size: 35px;
  font-weight: bold;
  cursor: pointer;
  background: rgba(0,0,0,0.5);
  border-radius: 50%;
  width: 45px;
  height: 45px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.3s ease;
}

.lightbox-close:hover {
  background: rgba(0,0,0,0.8);
}

.lightbox-info {
  color: white;
  margin-top: 20px;
  text-align: center;
}

.lightbox-title {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 10px;
}

.lightbox-description {
  font-size: 16px;
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.4;
}
</style>

<div class="gallery-container">
  <h1>Project Gallery</h1>
  <p>Visual showcase of VDC projects, technologies, and innovations</p>
  
  <div class="gallery-grid">
    {% for item in site.data.gallery %}
      {% if item.type == "image" %}
        <div class="gallery-item" onclick="openLightbox('{{ "/assets/img/" | append: item.image | prepend: site.baseurl }}', '{{ item.title }}', '{{ item.description }}', 'image')">
          <img src="{{ "/assets/img/" | append: item.image | prepend: site.baseurl }}" alt="{{ item.title }}">
          <div class="gallery-item-title">{{ item.title }}</div>
        </div>
      {% elsif item.type == "video" %}
        <div class="gallery-item" onclick="openLightbox('{{ item.video }}', '{{ item.title }}', '{{ item.description }}', 'video')">
          <div style="background: linear-gradient(45deg, #667eea 0%, #764ba2 100%); height: 250px; display: flex; align-items: center; justify-content: center; color: white; font-size: 48px;">
            ▶
          </div>
          <div class="gallery-item-title">{{ item.title }}</div>
        </div>
      {% endif %}
    {% endfor %}
  </div>
</div>

<div id="lightbox" class="lightbox" onclick="closeLightbox()">
  <div class="lightbox-content" onclick="event.stopPropagation()">
    <span class="lightbox-close" onclick="closeLightbox()">&times;</span>
    <img id="lightbox-image" class="lightbox-image" src="" alt="" style="display: none;">
    <iframe id="lightbox-video" class="lightbox-video" src="" frameborder="0" allowfullscreen style="display: none;"></iframe>
    <div class="lightbox-info">
      <div id="lightbox-title" class="lightbox-title"></div>
      <div id="lightbox-description" class="lightbox-description"></div>
    </div>
  </div>
</div>

<script>
function openLightbox(src, title, description, type) {
  document.getElementById('lightbox').style.display = 'block';
  document.getElementById('lightbox-title').textContent = title;
  document.getElementById('lightbox-description').textContent = description;
  
  if (type === 'image') {
    document.getElementById('lightbox-image').src = src;
    document.getElementById('lightbox-image').style.display = 'block';
    document.getElementById('lightbox-video').style.display = 'none';
  } else if (type === 'video') {
    document.getElementById('lightbox-video').src = src;
    document.getElementById('lightbox-video').style.display = 'block';
    document.getElementById('lightbox-image').style.display = 'none';
  }
  
  document.body.style.overflow = 'hidden';
}

function closeLightbox() {
  document.getElementById('lightbox').style.display = 'none';
  document.getElementById('lightbox-video').src = '';
  document.body.style.overflow = 'auto';
}

document.addEventListener('keydown', function(event) {
  if (event.key === 'Escape') {
    closeLightbox();
  }
});
</script>
