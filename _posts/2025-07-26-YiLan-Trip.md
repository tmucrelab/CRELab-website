---
# ===== 基本文章資訊 =====
layout: single
title: "YiLan Trip"
date: 2025-07-26

categories: [lab-life]
tags: [event, lab-life]
event_type: social   # seminar / social / academic
# 文章網址
# 建議和 title 對應
permalink: /life/20250726-YiLan-Trip/

# 讓頁面使用較寬版面
classes: wide

# ===== Lab Life 頁面卡片摘要 =====
# 這段會顯示在 /life/ 的卡片介紹
summary: "Trip to YiLan with lab members."

# ===== 上方照片輪播 (Slider) =====
# 這裡只放圖片，會自動輪播
slider_images:
  - /assets/assets/images/test-event-1.jpg
  - /assets/assets/images/test-event-2.png
  - /assets/assets/images/test-event-3.jpg

# ===== Photo Gallery (文章下方集錦) =====
# 支援：橫式照片、直式照片、影片
gallery_items:
  # 橫式照片
  - type: image
    src: /assets/assets/images//test-event-1.jpg
    orientation: landscape
  # 直式照片
  - type: image
    src: /assets/assets/images/test-straight-photo.jpg
    orientation: portrait
  # 影片
  - type: video
    src: /assets/assets/images/test-video-straight.mp4
    poster: /assets/assets/images/test-straight-photo.jpg
---

<!-- ===================================================== -->
<!--                     Photo Slider                      -->
<!-- ===================================================== -->

<div class="simple-slider post-slider">
  <div class="simple-slider__track">
    <div class="simple-slider__slides">
      {% for img in page.slider_images %}
        <div class="simple-slider__img {% if forloop.first %}is-active{% endif %}">
          <img src="{{ img | relative_url }}" alt="{{ page.title }} image {{ forloop.index }}">
        </div>
      {% endfor %}
    </div>

    <!-- 左右箭頭 -->
    <button class="simple-slider__arrow simple-slider__arrow--prev" type="button">
      &#10094;
    </button>
    <button class="simple-slider__arrow simple-slider__arrow--next" type="button">
      &#10095;
    </button>

    <!-- 小圓點導航 -->
    <div class="simple-slider__dots"></div>
  </div>
</div>

<!-- ===================================================== -->
<!--                     Article Text                      -->
<!-- ===================================================== -->

Write the main description of the event here.

You can add multiple paragraphs describing the event, seminar,
meeting, celebration, or conference.

Example:
Our lab held a seminar discussing the latest research on cancer
evolution and resistance mechanisms. Members of the lab presented
their work and exchanged ideas with visiting researchers.

<!-- ===================================================== -->
<!--                     Photo Gallery                     -->
<!-- ===================================================== -->

## Photo Gallery
<div class="post-gallery">
  {% for item in page.gallery_items %}
    {% if item.type == "image" %}
      <a href="{{ item.src | relative_url }}"
         class="post-gallery__item {% if item.orientation == 'portrait' %}is-portrait{% endif %}"
         data-type="image">
        <img src="{{ item.src | relative_url }}"
             alt="{{ page.title }} thumbnail {{ forloop.index }}">
      </a>

    {% elsif item.type == "video" %}
      <a href="{{ item.src | relative_url }}"
         class="post-gallery__item is-video"
         data-type="video"
         {% if item.poster %}data-poster="{{ item.poster | relative_url }}"{% endif %}>
        {% if item.poster %}
          <img src="{{ item.poster | relative_url }}"
               alt="{{ page.title }} video thumbnail {{ forloop.index }}">
        {% else %}
          <div class="post-gallery__video-placeholder">Video</div>
        {% endif %}
        <span class="post-gallery__video-badge">▶</span>
      </a>
    {% endif %}
  {% endfor %}
</div>

<!-- ===================================================== -->
<!--                   Lightbox，集錦                       -->
<!-- ===================================================== -->

<div class="lightbox" id="lightbox">
  <button class="lightbox__close" type="button">&times;</button>

  <img src="" alt="Expanded image" id="lightbox-img">

  <video id="lightbox-video" controls playsinline>
    <source src="" type="video/mp4">
  </video>
</div>

<!-- ===================================================== -->
<!--                     Slider Script                     -->
<!-- ===================================================== -->

<script>
document.addEventListener("DOMContentLoaded", function () {
  const sliders = document.querySelectorAll(".simple-slider");

  sliders.forEach((slider) => {
    const slides = slider.querySelectorAll(".simple-slider__img");
    const prevBtn = slider.querySelector(".simple-slider__arrow--prev");
    const nextBtn = slider.querySelector(".simple-slider__arrow--next");
    const dotsWrap = slider.querySelector(".simple-slider__dots");

    let current = 0;
    let intervalId = null;

    if (slides.length <= 1) return;


    function showSlide(index) {
      slides.forEach((slide, i) => {
        slide.classList.toggle("is-active", i === index);
      });

      const dots = dotsWrap.querySelectorAll(".simple-slider__dot");
      dots.forEach((dot, i) => {
        dot.classList.toggle("is-active", i === index);
      });

      current = index;
    }

    function nextSlide() {
      showSlide((current + 1) % slides.length);
    }

    function prevSlide() {
      showSlide((current - 1 + slides.length) % slides.length);
    }

    function startSlider() {
      if (intervalId) return;
      intervalId = setInterval(nextSlide, 3000);
    }

    function stopSlider() {
      clearInterval(intervalId);
      intervalId = null;
    }

    slides.forEach((_, i) => {
      const dot = document.createElement("button");
      dot.className = "simple-slider__dot" + (i === 0 ? " is-active" : "");
      dot.addEventListener("click", () => {
        stopSlider();
        showSlide(i);
        startSlider();
      });

      dotsWrap.appendChild(dot);
    });

    prevBtn.addEventListener("click", () => {
      stopSlider();
      prevSlide();
      startSlider();
    });

    nextBtn.addEventListener("click", () => {
      stopSlider();
      nextSlide();
      startSlider();
    });

    slider.addEventListener("mouseenter", stopSlider);
    slider.addEventListener("mouseleave", startSlider);

    showSlide(0);
    startSlider();
  });
});
</script>

<!-- ===================================================== -->
<!--                    Gallery Lightbox                   -->
<!-- ===================================================== -->

<script>
document.addEventListener("DOMContentLoaded", function () {
  const lightbox = document.getElementById("lightbox");
  const lightboxImg = document.getElementById("lightbox-img");
  const lightboxVideo = document.getElementById("lightbox-video");
  const lightboxVideoSource = lightboxVideo.querySelector("source");
  const closeBtn = lightbox.querySelector(".lightbox__close");
  const items = document.querySelectorAll(".post-gallery__item");


  function closeLightbox() {
    lightbox.classList.remove("is-open");
    lightboxImg.src = "";
    lightboxImg.style.display = "none";

    lightboxVideo.pause();
    lightboxVideoSource.src = "";
    lightboxVideo.load();
    lightboxVideo.style.display = "none";
  }

  items.forEach((item) => {
    item.addEventListener("click", function (e) {
      e.preventDefault();

      const type = item.dataset.type;
      const href = item.getAttribute("href");

      if (type === "video") {
        lightboxImg.style.display = "none";
        
        lightboxVideoSource.src = href;
        lightboxVideo.load();
        lightboxVideo.style.display = "block";
        
      } else {
        lightboxVideo.pause();
        lightboxVideoSource.src = "";
        lightboxVideo.load();
        lightboxVideo.style.display = "none";

        lightboxImg.src = href;
        lightboxImg.style.display = "block";
      }

      lightbox.classList.add("is-open");
    });
  });

  closeBtn.addEventListener("click", closeLightbox);

  lightbox.addEventListener("click", function (e) {
    if (e.target === lightbox) {
      closeLightbox();
    }
  });
});
</script>
