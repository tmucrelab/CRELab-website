---
# ===== 基本文章資訊 =====
layout: single
title: "Hallowen Party"
date: 2025-10-14

categories: [lab-life]
tags: [event, lab-life]
event_type: social   # seminar / social / academic
# 文章網址
# 建議和 title 對應
permalink: /life/20251014-halloween-party/

# 讓頁面使用較寬版面
classes: wide

# ===== Lab Life 頁面卡片摘要 =====
# 這段會顯示在 /life/ 的卡片介紹
summary: "Halloween party."

# ===== 上方照片輪播 (Slider) =====
# 這裡只放圖片，會自動輪播
slider_images:
  - /assets/assets/images/Lab-Life/2025-10-14-Halloween-Party/2025-10-14-Halloween-Party-01.jpg
  - /assets/assets/images/Lab-Life/2025-10-14-Halloween-Party/2025-10-14-Halloween-Party-02.jpg

# ===== Photo Gallery (文章下方集錦) =====
# 支援：橫式照片、直式照片、影片
gallery_items:
  - type: image
    src: /assets/assets/images/Lab-Life/2025-10-14-Halloween-Party/2025-10-14-Halloween-Party-01.jpg
    orientation: landscape

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

Professor YC gave a talk.

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

<div class="post-lightbox" id="post-lightbox" hidden>
  <button class="post-lightbox__close" type="button" aria-label="Close media">&times;</button>

  <button class="post-lightbox__nav post-lightbox__nav--prev" type="button" aria-label="Previous media">
    &#10094;
  </button>

  <div class="post-lightbox__inner">
    <img src="" alt="Expanded image" id="post-lightbox-img">

    <video id="post-lightbox-video" controls playsinline>
      <source src="" type="video/mp4">
    </video>
  </div>

  <button class="post-lightbox__nav post-lightbox__nav--next" type="button" aria-label="Next media">
    &#10095;
  </button>
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
  const lightbox = document.getElementById("post-lightbox");
  const lightboxInner = lightbox.querySelector(".post-lightbox__inner");
  const lightboxImg = document.getElementById("post-lightbox-img");
  const lightboxVideo = document.getElementById("post-lightbox-video");
  const lightboxVideoSource = lightboxVideo.querySelector("source");
  const closeBtn = lightbox.querySelector(".post-lightbox__close");
  const prevBtn = lightbox.querySelector(".post-lightbox__nav--prev");
  const nextBtn = lightbox.querySelector(".post-lightbox__nav--next");
  const items = Array.from(document.querySelectorAll(".post-gallery__item"));

  let currentIndex = -1;

  function closeLightbox() {
    lightboxImg.src = "";
    lightboxImg.style.display = "none";

    lightboxVideo.pause();
    lightboxVideoSource.src = "";
    lightboxVideo.load();
    lightboxVideo.style.display = "none";

    lightbox.hidden = true;
    document.body.classList.remove("post-lightbox-open");
    currentIndex = -1;
  }

  function openImage(src) {
    lightboxVideo.pause();
    lightboxVideoSource.src = "";
    lightboxVideo.load();
    lightboxVideo.style.display = "none";

    lightboxImg.src = src;
    lightboxImg.style.display = "block";
  }

  function openVideo(src) {
    lightboxImg.src = "";
    lightboxImg.style.display = "none";

    lightboxVideoSource.src = src;
    lightboxVideo.load();
    lightboxVideo.style.display = "block";
  }

  function showItem(index) {
    if (items.length === 0) return;

    if (index < 0) {
      index = items.length - 1;
    }

    if (index >= items.length) {
      index = 0;
    }

    currentIndex = index;

    const item = items[currentIndex];
    const type = item.dataset.type;
    const href = item.getAttribute("href");

    if (type === "video") {
      openVideo(href);
    } else {
      openImage(href);
    }

    lightbox.hidden = false;
    document.body.classList.add("post-lightbox-open");
  }

  function showPrev() {
    if (currentIndex === -1) return;
    showItem(currentIndex - 1);
  }

  function showNext() {
    if (currentIndex === -1) return;
    showItem(currentIndex + 1);
  }

  items.forEach((item, index) => {
    item.addEventListener("click", function (e) {
      e.preventDefault();
      e.stopPropagation();
      e.stopImmediatePropagation();
      showItem(index);
    });
  });

  closeBtn.addEventListener("click", function (e) {
    e.preventDefault();
    e.stopPropagation();
    e.stopImmediatePropagation();
    closeLightbox();
  });

  prevBtn.addEventListener("click", function (e) {
    e.preventDefault();
    e.stopPropagation();
    showPrev();
  });

  nextBtn.addEventListener("click", function (e) {
    e.preventDefault();
    e.stopPropagation();
    showNext();
  });

  lightbox.addEventListener("click", function (e) {
    if (!lightboxInner.contains(e.target) &&
        !prevBtn.contains(e.target) &&
        !nextBtn.contains(e.target) &&
        !closeBtn.contains(e.target)) {
      closeLightbox();
    }
  });

  document.addEventListener("keydown", function (e) {
    if (lightbox.hidden) return;

    if (e.key === "Escape") {
      closeLightbox();
    } else if (e.key === "ArrowLeft") {
      showPrev();
    } else if (e.key === "ArrowRight") {
      showNext();
    }
  });
});
</script>
