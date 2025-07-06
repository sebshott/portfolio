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
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

@media (max-width: 768px) {
  .gallery-grid {
    grid-template-columns: repeat(auto
