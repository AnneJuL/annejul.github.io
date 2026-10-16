---
layout: single
title: "Pictures"
permalink: /pictures/
author_profile: true
---

*Some pictures from my different field experiences. © A.J. Laberge*

<div class="gallery-grid">
  <img src="/images/gallery/photo1.jpg" alt="Field photo" onclick="openLightbox(this)">
  <img src="/images/gallery/photo2.jpg" alt="Field photo" onclick="openLightbox(this)">
  <img src="/images/gallery/photo3.jpg" alt="Field photo" onclick="openLightbox(this)">
  <img src="/images/gallery/photo4.jpg" alt="Field photo" onclick="openLightbox(this)">
  <img src="/images/gallery/photo5.jpg" alt="Field photo" onclick="openLightbox(this)">
  <img src="/images/gallery/photo6.jpg" alt="Field photo" onclick="openLightbox(this)">
</div>

<!-- Lightbox modal -->
<div id="lightbox" onclick="closeLightbox()">
  <span id="lb-prev" onclick="event.stopPropagation(); changePhoto(-1)">&#10094;</span>
  <img id="lb-img" src="">
  <span id="lb-next" onclick="event.stopPropagation(); changePhoto(1)">&#10095;</span>
</div>

<style>
.gallery-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
  margin-top: 20px;
}
.gallery-grid img {
  width: 100%;
  height: 220px;
  object-fit: cover;
  cursor: pointer;
  border-radius: 4px;
  transition: opacity 0.2s;
}
.gallery-grid img:hover { opacity: 0.85; }

#lightbox {
  display: none;
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.9);
  z-index: 9999;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}
#lightbox.active { display: flex; }
#lb-img {
  max-width: 90%;
  max-height: 90vh;
  object-fit: contain;
  border-radius: 4px;
}
#lb-prev, #lb-next {
  color: white;
  font-size: 2.5rem;
  padding: 20px;
  cursor: pointer;
  user-select: none;
  position: absolute;
}
#lb-prev { left: 10px; }
#lb-next { right: 10px; }
</style>

<script>
let photos = [];
let current = 0;

function openLightbox(img) {
  photos = Array.from(document.querySelectorAll('.gallery-grid img'));
  current = photos.indexOf(img);
  document.getElementById('lb-img').src = img.src;
  document.getElementById('lightbox').classList.add('active');
}
function closeLightbox() {
  document.getElementById('lightbox').classList.remove('active');
}
function changePhoto(dir) {
  current = (current + dir + photos.length) % photos.length;
  document.getElementById('lb-img').src = photos[current].src;
}
document.addEventListener('keydown', e => {
  if (e.key === 'ArrowRight') changePhoto(1);
  if (e.key === 'ArrowLeft') changePhoto(-1);
  if (e.key === 'Escape') closeLightbox();
});
</script>
