---
layout: single
title: "Lab Life"
permalink: /life/
classes: wide
---

## Life at CRE Lab

We believe great science happens in a supportive and collaborative environment.  
Here are moments from seminars, collaborations, conferences, and lab gatherings.

---

# ==============================
# SEMINARS & TALKS
# ==============================

<section class="life-section">
<h2>Seminars & Talks</h2>

<p>
Seminars and invited talks organized by the CRE Lab, including guest speakers,
research seminars, and scientific discussions hosted by our group.
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

---

# ==============================
# LAB SOCIAL EVENTS
# ==============================

<section class="life-section">
<h2>Lab Social Events</h2>

<p>
Moments from lab gatherings, celebrations, and social activities that help
strengthen collaboration and friendship within the CRE Lab.
</p>

<div class="life-grid">
{% assign social_posts = site.categories.lab-life | where: "event_type", "social" | sort: "date" | reverse %}

{% for post in social_posts %}
  <article class="life-card">
    <a href="{{ post.url | relative_url }}" class="life-card__media">
      <div class="life-card__slider">
        {% for img in post.slider_images %}

          <img
            src="{{ img | relative_url }}"
            alt="{{ post.title }}"
            class="life-card__img {% if forloop.first %}is-active{% endif %}">

        {% endfor %}
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

---

# ==============================
# ACADEMIC EVENTS
# ==============================

<section class="life-section">

<h2>Academic Events</h2>

<p>
Academic activities related to our research interests, including conferences,
workshops, and scientific meetings attended by members of the CRE Lab.
</p>

<div class="life-grid">

{% assign academic_posts = site.categories.lab-life | where: "event_type", "academic" | sort: "date" | reverse %}

{% for post in academic_posts %}
  <article class="life-card">
    <a href="{{ post.url | relative_url }}" class="life-card__media">
      <div class="life-card__slider">
        {% for img in post.slider_images %}

          <img
            src="{{ img | relative_url }}"
            alt="{{ post.title }}"
            class="life-card__img {% if forloop.first %}is-active{% endif %}">

        {% endfor %}
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

---

### 📌 Want to join us?

If you are interested in joining CRE Lab, feel free to contact us.
