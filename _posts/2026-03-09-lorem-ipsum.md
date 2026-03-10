---
layout: single
title: "Lorem ipsum"
date: 2026-03-09
categories: [lab-life]
tags: [event, lab-life]
image: /assets/assets/images/test-event-2.png
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
<!--more-->

Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.

## Photo Gallery

<div class="post-gallery">
  {% for img in page.gallery %}
    <a href="{{ img | relative_url }}" class="post-gallery__item" target="_blank">
      <img src="{{ img | relative_url }}" alt="{{ page.title }} thumbnail {{ forloop.index }}">
    </a>
  {% endfor %}
</div>
