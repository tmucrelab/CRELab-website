---
layout: single
title: "Lab Life"
permalink: /life/
classes: wide
---

## Life at CRE Lab

We believe great science happens in a supportive and collaborative environment.  
Here are moments from seminars, collaborations, conferences, and lab gatherings.

{% assign life_posts = site.categories.lab-life | sort: "date" | reverse %}

<section class="life-timeline">
  {% for post in life_posts %}
    <article class="life-timeline__item">
      <div class="life-timeline__rail">
        <div class="life-timeline__dot"></div>
      </div>

      <div class="life-timeline__main">
        <div class="life-timeline__header">
          <time class="life-timeline__date" datetime="{{ post.date | date_to_xmlschema }}">
            {{ post.date | date: "%Y.%m.%d" }}
          </time>

          <span class="life-timeline__tag">
            {% if post.event_type == "academic" or post.event_type == "seminar" %}
              Academic
            {% else %}
              Social
            {% endif %}
          </span>
        </div>

        <h2 class="life-timeline__title">
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </h2>

        <div class="life-timeline__preview">
          {% if post.slider_images or post.image %}
            <a href="{{ post.url | relative_url }}" class="life-timeline__thumbLink">
              <div class="life-timeline__thumbSlider">
                {% if post.slider_images %}
                  {% for img in post.slider_images %}
                    <img
                      src="{{ img | relative_url }}"
                      alt="{{ post.title }}"
                      class="life-timeline__thumb {% if forloop.first %}is-active{% endif %}">
                  {% endfor %}
                {% elsif post.image %}
                  <img
                    src="{{ post.image | relative_url }}"
                    alt="{{ post.title }}"
                    class="life-timeline__thumb is-active">
                {% endif %}
              </div>
            </a>
          {% endif %}

          <div class="life-timeline__excerpt">
            {{ post.summary }}
          </div>
        </div>
      </div>
    </article>
  {% endfor %}
</section>

### 📌 Want to join us?

If you are interested in joining CRE Lab, feel free to contact us.

<script>
document.addEventListener("DOMContentLoaded", function () {
  const sliders = document.querySelectorAll(".life-timeline__thumbSlider");

  sliders.forEach((slider) => {
    const images = slider.querySelectorAll(".life-timeline__thumb");
    let current = 0;

    if (images.length <= 1) return;

    setInterval(() => {
      images[current].classList.remove("is-active");
      current = (current + 1) % images.length;
      images[current].classList.add("is-active");
    }, 3000);
  });
});
</script>
