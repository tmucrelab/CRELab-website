---
layout: single
title: "Research"
permalink: /research/
classes: wide
---

## Research at CRE Lab

Our research explores how cancers evolve under therapeutic pressure and develop resistance.  
Below are three major project directions currently featured on the site.

<hr>

<section class="research-project" id="project-a">
  <div class="research-project__text">
    <h2>Project A</h2>

    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
    </p>
  </div>

  <div class="simple-slider research-slider" data-slider="project-a">
    <div class="simple-slider__track">
      <div class="simple-slider__slides">
        
        <button
          type="button"
          class="simple-slider__img is-active research-lightbox-trigger"
          data-full="{{ '/assets/assets/images/test-research-1.jpg' | relative_url }}"
          aria-label="Open Project A image 1">
          <img src="{{ '/assets/assets/images/test-research-1.jpg' | relative_url }}" alt="Project A image 1">
        </button>

        <button
          type="button"
          class="simple-slider__img research-lightbox-trigger"
          data-full="{{ '/assets/assets/images/test-research-2.jpeg' | relative_url }}"
          aria-label="Open Project A image 2">
          <img src="{{ '/assets/assets/images/test-research-2.jpeg' | relative_url }}" alt="Project A image 2">
        </button>

        <button
          type="button"
          class="simple-slider__img research-lightbox-trigger"
          data-full="{{ '/assets/assets/images/test-research-3.jpg' | relative_url }}"
          aria-label="Open Project A image 3">
          <img src="{{ '/assets/assets/images/test-research-3.jpg' | relative_url }}" alt="Project A image 3">
        </button>

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
</section>

<hr>

<section class="research-project" id="project-b">
  <div class="research-project__text">
    <h2>Project B</h2>

    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
    </p>
  </div>

  <div class="simple-slider research-slider" data-slider="project-b">
    <div class="simple-slider__track">
      <div class="simple-slider__slides">

        <button
          type="button"
          class="simple-slider__img is-active research-lightbox-trigger"
          data-full="{{ '/assets/assets/images/test-research-1.jpg' | relative_url }}"
          aria-label="Open Project B image 1">
          <img src="{{ '/assets/assets/images/test-research-1.jpg' | relative_url }}" alt="Project B image 1">
        </button>

        <button
          type="button"
          class="simple-slider__img research-lightbox-trigger"
          data-full="{{ '/assets/assets/images/test-research-2.jpeg' | relative_url }}"
          aria-label="Open Project B image 2">
          <img src="{{ '/assets/assets/images/test-research-2.jpeg' | relative_url }}" alt="Project B image 2">
        </button>

        <button
          type="button"
          class="simple-slider__img research-lightbox-trigger"
          data-full="{{ '/assets/assets/images/test-research-3.jpg' | relative_url }}"
          aria-label="Open Project B image 3">
          <img src="{{ '/assets/assets/images/test-research-3.jpg' | relative_url }}" alt="Project B image 3">
        </button>

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
</section>

<hr>

<section class="research-project" id="project-c">
  <div class="research-project__text">
    <h2>Project C</h2>

    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
    </p>
  </div>

  <div class="simple-slider research-slider" data-slider="project-c">
    <div class="simple-slider__track">
      <div class="simple-slider__slides">

        <button
          type="button"
          class="simple-slider__img is-active research-lightbox-trigger"
          data-full="{{ '/assets/assets/images/test-research-1.jpg' | relative_url }}"
          aria-label="Open Project C image 1">
          <img src="{{ '/assets/assets/images/test-research-1.jpg' | relative_url }}" alt="Project C image 1">
        </button>

        <button
          type="button"
          class="simple-slider__img research-lightbox-trigger"
          data-full="{{ '/assets/assets/images/test-research-2.jpeg' | relative_url }}"
          aria-label="Open Project C image 2">
          <img src="{{ '/assets/assets/images/test-research-2.jpeg' | relative_url }}" alt="Project C image 2">
        </button>

        <button
          type="button"
          class="simple-slider__img research-lightbox-trigger"
          data-full="{{ '/assets/assets/images/test-research-3.jpg' | relative_url }}"
          aria-label="Open Project C image 3">
          <img src="{{ '/assets/assets/images/test-research-3.jpg' | relative_url }}" alt="Project C image 3">
        </button>

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
</section>

<div class="research-lightbox" id="research-lightbox" hidden>
  <button class="research-lightbox__close" type="button" aria-label="Close image">&times;</button>

  <div class="research-lightbox__inner">
    <img src="" alt="Expanded research image" id="research-lightbox-img">
  </div>
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
      const next = (current + 1) % slides.length;
      showSlide(next);
    }

    function prevSlide() {
      const prev = (current - 1 + slides.length) % slides.length;
      showSlide(prev);
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

  const lightbox = document.getElementById("research-lightbox");
  const lightboxImg = document.getElementById("research-lightbox-img");
  const lightboxInner = lightbox.querySelector(".research-lightbox__inner");
  const closeBtn = lightbox.querySelector(".research-lightbox__close");
  const triggers = document.querySelectorAll(".research-lightbox-trigger");

  function openLightbox(src) {
    lightboxImg.src = src;
    lightbox.hidden = false;
    document.body.classList.add("research-lightbox-open");
  }

  function closeLightbox() {
    lightboxImg.src = "";
    lightbox.hidden = true;
    document.body.classList.remove("research-lightbox-open");
  }

  triggers.forEach((item) => {
    item.addEventListener("click", function (e) {
      e.preventDefault();
      e.stopPropagation();
      e.stopImmediatePropagation();

      const src = item.dataset.full;
      openLightbox(src);
    });
  });

  closeBtn.addEventListener("click", function (e) {
    e.preventDefault();
    e.stopPropagation();
    e.stopImmediatePropagation();
    closeLightbox();
  });

  lightbox.addEventListener("click", function (e) {
    if (!lightboxInner.contains(e.target)) {
      closeLightbox();
    }
  });

  document.addEventListener("keydown", function (e) {
    if (e.key === "Escape" && !lightbox.hidden) {
      closeLightbox();
    }
  });
});
</script>


<!--
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
      const next = (current + 1) % slides.length;
      showSlide(next);
    }

    function prevSlide() {
      const prev = (current - 1 + slides.length) % slides.length;
      showSlide(prev);
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
-->

<!--
## Research at CRE Lab

The CRE Lab focuses on understanding **Cancer Resistance Evolution**,  
investigating how cancer cells adapt to therapeutic pressure through  
molecular, transcriptional, and metabolic remodeling.

Our research integrates experimental cancer biology with advanced cellular models to uncover mechanisms underlying therapy resistance.

---

## 🔬 Research Themes

### 1. Cancer Resistance Evolution
We study how cancer cells evolve under therapeutic pressure, focusing on adaptive strategies that enable survival and resistance to treatment.

- Evolutionary dynamics of therapy resistance  
- Transcriptional and epigenetic remodeling  
- Cellular plasticity in cancer progression  

---

### 2. Prostate Cancer Biology
Prostate cancer serves as a primary disease model in our lab.

- Castration-resistant prostate cancer (CRPC)  
- Neuroendocrine differentiation  
- Treatment-induced phenotypic switching  

---

### 3. Organoid Models and Metabolic Remodeling
We use 3D organoid systems to better recapitulate tumor architecture and microenvironment.

- Prostate cancer organoids  
- Lipid metabolism and metabolic adaptation  
- Therapy-induced metabolic rewiring  

---

## 🧬 Experimental Approaches

- 2D and 3D cancer cell culture  
- Patient-derived and cell line–derived organoids  
- Lipidomics and metabolic profiling  
- Transcriptomic and epigenetic analyses  

---

## 🧠 Long-term Goals
Our long-term goal is to identify fundamental principles governing cancer resistance evolution and to uncover vulnerabilities that can be exploited for improved therapeutic strategies.
-->
