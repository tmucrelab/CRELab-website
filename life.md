---
layout: single
title: "Lab Life"
permalink: /life/
classes: wide
---

## Life at CRE Lab

We believe great science happens in a supportive and collaborative environment.  
Here are some moments from our lab life — seminars, group meetings, celebrations, and more.

---
<div class="life-grid">
{% assign lablife_posts = site.categories.lab-life %}
{% for post in lablife_posts %}
  <article class="life-card">
    <a href="{{ post.url | relative_url }}" class="life-card__media">
      <div class="life-card__slider">
        {% if post.slider_images %}
          {% for img in post.slider_images %}
            <img
              src="{{ img | relative_url }}"
              alt="{{ post.title }}"
              class="life-card__img {% if forloop.first %}is-active{% endif %}">
          {% endfor %}
        {% elsif post.image %}
          <img
            src="{{ post.image | relative_url }}"
            alt="{{ post.title }}"
            class="life-card__img is-active">
        {% endif %}
      </div>
    </a>

    <div class="life-card__content">
      <h3 class="life-card__title">
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h3>

      <p class="life-card__date">{{ post.date | date: "%Y.%m.%d" }}</p>

      <div class="life-card__excerpt">
        {{ post.summary }}
      </div>
    </div>
  </article>
{% endfor %}
</div>

<script>
document.addEventListener("DOMContentLoaded", function () {
  const sliders = document.querySelectorAll(".life-card__slider");

  sliders.forEach((slider) => {
    const images = slider.querySelectorAll(".life-card__img");
    let current = 0;

    if (images.length <= 1) return;

    setInterval(() => {
      images[current].classList.remove("is-active");
      current = (current + 1) % images.length;
      images[current].classList.add("is-active");
    }, 2500);
  });
});
</script>

---

### 📌 Want to join us?
If you are interested in joining CRE Lab, feel free to contact us.
