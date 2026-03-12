---
layout: single
title: "Lab Life"
permalink: /life/
classes: wide
---

## Life at CRE Lab

We believe great science happens in a supportive and collaborative environment.  
Here are moments from seminars, collaborations, conferences, and lab gatherings.

<!-- ============================== -->
<!--         RECENT EVENTS          -->
<!-- ============================== -->

<section class="life-section">
  <h2>Recent Events</h2>

  <p>
    The latest moments from CRE Lab, including seminars, social gatherings,
    and academic activities. This section automatically displays the three
    most recent events across all categories.
  </p>

  <div class="life-grid">
    {% assign recent_posts = site.categories.lab-life | sort: "date" | reverse %}

    {% for post in recent_posts limit: 3 %}
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
</section>

<hr>

<!-- ============================== -->
<!--        SEMINARS & TALKS        -->
<!-- ============================== -->

<section class="life-section">
  <h2>Seminars & Talks</h2>

  <p>
    Seminars and invited talks organized by the CRE Lab, including guest speakers,
    invited lectures, and internal research seminars hosted by our group.
  </p>

  <div class="life-grid">
    {% assign seminar_posts = site.categories.lab-life | where: "event_type", "seminar" | sort: "date" | reverse %}

    {% for post in seminar_posts %}
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
</section>

<hr>

<!-- ============================== -->
<!--       LAB SOCIAL EVENTS        -->
<!-- ============================== -->

<section class="life-section">
  <h2>Lab Social Events</h2>

  <p>
    Moments from dinners, celebrations, gatherings, and other social activities
    that strengthen friendship and collaboration within the CRE Lab.
  </p>

  <div class="life-grid">
    {% assign social_posts = site.categories.lab-life | where: "event_type", "social" | sort: "date" | reverse %}

    {% for post in social_posts %}
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
</section>

<hr>

<!-- ============================== -->
<!--        ACADEMIC EVENTS         -->
<!-- ============================== -->

<section class="life-section">
  <h2>Academic Events</h2>

  <p>
    Academic activities related to our research interests, including conferences,
    workshops, symposia, and scientific meetings attended by CRE Lab members.
  </p>

  <div class="life-grid">
    {% assign academic_posts = site.categories.lab-life | where: "event_type", "academic" | sort: "date" | reverse %}

    {% for post in academic_posts %}
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
</section>

<hr>

### 📌 Want to join us?

If you are interested in joining CRE Lab, feel free to contact us.

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
    }, 3000);
  });
});
</script>
