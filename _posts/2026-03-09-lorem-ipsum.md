---
layout: single
title: "Lorem ipsum"
date: 2026-03-09
categories: [lab-life]
tags: [event, lab-life]
# image: /assets/assets/images/test-event-2.png
permalink: /life/lorem-ipsum/
classes: wide

# 自訂會顯示在縮圖的文章摘要
summary: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."

gallery:
  - /assets/assets/images/test-event-1.jpg
  - /assets/assets/images/test-event-2.png
  - /assets/assets/images/test-event-3.jpg

# excerpt_separator: <!--more-->
---

<div class="simple-slider post-slider">
  <div class="simple-slider__track">
    <div class="simple-slider__slides">
      {% for img in page.gallery %}
        <div class="simple-slider__img {% if forloop.first %}is-active{% endif %}">
          <img src="{{ img | relative_url }}" alt="{{ page.title }} image {{ forloop.index }}">
        </div>
      {% endfor %}
    </div>

    <button class="simple-slider__arrow simple-slider__arrow--prev" type="button" aria-label="Previous slide">
      &#10094;
    </button>
    <button class="simple-slider__arrow simple-slider__arrow--next" type="button" aria-label="Next slide">
      &#10095;
    </button>

    <div class="simple-slider__dots"></div>
  </div>
</div>

<!-- ![Lorem ipsum]({{ '/assets/assets/images/test-event-2.png' | relative_url }}) -->

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.

Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.

## Photo Gallery

<div class="post-gallery">
  {% for img in page.gallery %}
    <a href="{{ img | relative_url }}" class="post-gallery__item">
      <img src="{{ img | relative_url }}" alt="{{ page.title }} thumbnail {{ forloop.index }}">
    </a>
  {% endfor %}
</div>

<div class="lightbox" id="lightbox">
  <button class="lightbox__close" type="button" aria-label="Close image">&times;</button>
  <img src="" alt="Expanded image" id="lightbox-img">
</div>

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

    if (dotsWrap) {
      slides.forEach((_, i) => {
        const dot = document.createElement("button");
        dot.type = "button";
        dot.className = "simple-slider__dot" + (i === 0 ? " is-active" : "");
        dot.setAttribute("aria-label", `Go to slide ${i + 1}`);
        dot.addEventListener("click", () => {
          stopSlider();
          showSlide(i);
          startSlider();
        });
        dotsWrap.appendChild(dot);
      });
    }

    if (prevBtn) {
      prevBtn.addEventListener("click", () => {
        stopSlider();
        prevSlide();
        startSlider();
      });
    }

    if (nextBtn) {
      nextBtn.addEventListener("click", () => {
        stopSlider();
        nextSlide();
        startSlider();
      });
    }

    slider.addEventListener("mouseenter", stopSlider);
    slider.addEventListener("mouseleave", startSlider);

    showSlide(0);
    startSlider();
  });
});
</script>

<script>
document.addEventListener("DOMContentLoaded", function () {
  const lightbox = document.getElementById("lightbox");
  const lightboxImg = document.getElementById("lightbox-img");
  const closeBtn = lightbox.querySelector(".lightbox__close");
  const items = document.querySelectorAll(".post-gallery__item");

  items.forEach((item) => {
    item.addEventListener("click", function (e) {
      e.preventDefault();
      lightboxImg.src = item.getAttribute("href");
      lightbox.classList.add("is-open");
    });
  });

  closeBtn.addEventListener("click", function () {
    lightbox.classList.remove("is-open");
    lightboxImg.src = "";
  });

  lightbox.addEventListener("click", function (e) {
    if (e.target === lightbox) {
      lightbox.classList.remove("is-open");
      lightboxImg.src = "";
    }
  });
});
</script>
