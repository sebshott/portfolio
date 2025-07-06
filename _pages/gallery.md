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
  columns: 3;
  column-gap: 20px;
  margin-top: 20px;
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
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

.gallery-item:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 16px rgba(0,0,0,0.2);
}

.gallery-item img {
  width: 100%;
  height: auto;
  display: block;
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
  position: relative;
  margin: 5% auto;
  max-width: 90%;
  max-height: 80%;
  text-align: center;
}

.lightbox-image {
  max-width: 100%;
  max-height: 70vh;
  object-fit: contain;
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
    <!-- T-Bar Generator -->
    <div class="gallery-item" onclick="openLightbox('{{ "/assets/img/tbar-generator.png" | prepend: site.baseurl }}', 'T-Bar Generator', 'Dynamo script for automated ceiling system modeling')">
      <img src="{{ "/assets/img/tbar-generator.png" | prepend: site.baseurl }}" alt="T-Bar Generator">
    </div>
    
    <!-- Lowe County Lab -->
    <div class="gallery-item" onclick="openLightbox('{{ "/assets/img/lowe-county-lab.jpg" | prepend: site.baseurl }}', 'Lowe County Public Health Lab', 'Integrated VDC workflows with Revizto, Dusty robotics, and AR visualization')">
      <img src="{{ "/assets/img/lowe-county-lab.jpg" | prepend: site.baseurl }}" alt="Lowe County Lab">
    </div>
    
    <!-- Callan Ridge -->
    <div class="gallery-item" onclick="openLightbox('{{ "/assets/img/callan-ridge-hero.jpg" | prepend: site.baseurl }}', 'Healthpeak Callan Ridge', 'Design-build coordination with stud rail penetration modeling')">
      <img src="{{ "/assets/img/callan-ridge-hero.jpg" | prepend: site.baseurl }}" alt="Callan Ridge">
    </div>
    
    <!-- Fireproofing Generator -->
    <div class="gallery-item" onclick="openLightbox('{{ "/assets/img/fireproofing-generator.jpg" | prepend: site.baseurl }}', 'Fireproofing Generator', 'Automated structural fireproofing clearance modeling')">
      <img src="{{ "/assets/img/fireproofing-generator.jpg" | prepend: site.baseurl }}" alt="Fireproofing Generator">
    </div>
    
    <!-- Add more items as needed -->
  </div>
</div>

<!-- Lightbox Modal -->
<div id="lightbox" class="
