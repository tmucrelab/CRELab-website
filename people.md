---
layout: single
title: "People"
permalink: /people/
classes: wide
---

<section class="people-section">
  <div class="people-list people-list--leaders">
    <div class="people-leader-card">
      <h2 class="people-section__title">Principal Investigator</h2>

      {% assign items = site.people | where: "role", "pi" | sort: "order" %}
      {% for p in items %}
        <article class="person">
          <a class="person__photoLink" href="{{ p.url | relative_url }}" aria-label="View profile: {{ p.name }}">
            <img
              class="person__photo"
              src="{{ p.photo | relative_url }}"
              alt="{{ p.name }}"
              {% if p.thumb_position %}style="object-position: {{ p.thumb_position }};"{% endif %}>
          </a>

          <div class="person__meta">
            <h3 class="person__name">
              <a href="{{ p.url | relative_url }}">{{ p.name }}</a>
            </h3>

            {% if p.dept or p.org %}
              <p class="person__title">
                {% if p.dept %}{{ p.dept }}<br>{% endif %}
                {% if p.org %}{{ p.org }}{% endif %}
              </p>
            {% endif %}
          </div>
        </article>
      {% endfor %}
    </div>


    <div class="people-leader-card">
      <h2 class="people-section__title">Co-Mentor</h2>

      {% assign items = site.people | where: "role", "comentor" | sort: "order" %}
      {% for p in items %}
        <article class="person">
          <a class="person__photoLink" href="{{ p.url | relative_url }}" aria-label="View profile: {{ p.name }}">
            <img
              class="person__photo"
              src="{{ p.photo | relative_url }}"
              alt="{{ p.name }}"
              {% if p.thumb_position %}style="object-position: {{ p.thumb_position }};"{% endif %}>
          </a>

          <div class="person__meta">
            <h3 class="person__name">
              <a href="{{ p.url | relative_url }}">{{ p.name }}</a>
            </h3>

            {% if p.dept or p.org %}
              <p class="person__title">
                {% if p.dept %}{{ p.dept }}<br>{% endif %}
                {% if p.org %}{{ p.org }}{% endif %}
              </p>
            {% endif %}
          </div>
        </article>
      {% endfor %}
    </div>
  </div>
</section>


<section class="people-section">
  <h2 class="people-section__title">Lab Manager</h2>

  <div class="people-list">
    {% assign items = site.people | where: "role", "labmanager" | sort: "order" %}
    {% for p in items %}
      <article class="person">
        <a class="person__photoLink" href="{{ p.url | relative_url }}" aria-label="View profile: {{ p.name }}">
          <img
              class="person__photo"
              src="{{ p.photo | relative_url }}"
              alt="{{ p.name }}"
              {% if p.thumb_position %}style="object-position: {{ p.thumb_position }};"{% endif %}>
        </a>

        <div class="person__meta">
          <h3 class="person__name">
            <a href="{{ p.url | relative_url }}">{{ p.name }}</a>
          </h3> 

          {% if p.dept or p.org %}
            <p class="person__title">
              {% if p.dept %}{{ p.dept }}<br>{% endif %}
              {% if p.org %}{{ p.org }}{% endif %}
            </p>
          {% endif %}
        </div>
      </article>
    {% endfor %}
  </div>
</section>


<section class="people-section">
  <h2 class="people-section__title">Members</h2>

  <div class="people-list">
    {% assign items = site.people | where: "role", "member" | sort: "order" %}
    {% for p in items %}
      <article class="person">
        <a class="person__photoLink" href="{{ p.url | relative_url }}" aria-label="View profile: {{ p.name }}">
          <img
              class="person__photo"
              src="{{ p.photo | relative_url }}"
              alt="{{ p.name }}"
              {% if p.thumb_position %}style="object-position: {{ p.thumb_position }};"{% endif %}>
        </a>

        <div class="person__meta">
          <h3 class="person__name">
            <a href="{{ p.url | relative_url }}">{{ p.name }}</a>
          </h3> 

          {% if p.dept or p.org %}
            <p class="person__title">
              {% if p.dept %}{{ p.dept }}<br>{% endif %}
              {% if p.org %}{{ p.org }}{% endif %}
            </p>
          {% endif %}
        </div>
      </article>
    {% endfor %}
  </div>
</section>


<section class="people-section">
  <h2 class="people-section__title">Former Members</h2>

  <div class="people-list">
    {% assign items = site.people | where: "role", "formermembers" | sort: "order" %}
    {% for p in items %}
      <article class="person">
         <!-- Former members 照片 (不可點擊) -->
         <div class="person__photoLink">
           
          <img 
            class="person__photo"
            src="{{ p.photo | relative_url }}"
            alt="{{ p.name }}"
            {% if p.thumb_position %}style="object-position: {{ p.thumb_position }};"{% endif %}>
        </div>

        <div class="person__meta">
          <!-- 名字不加連結 -->
          <h3 class="person__name">
            {{ p.name }}
          </h3>

          {% if p.dept or p.org %}
            <p class="person__title">
              {% if p.dept %}{{ p.dept }}<br>{% endif %}
              {% if p.org %}{{ p.org }}{% endif %}
            </p>
          {% endif %}
        </div>
      </article>
    {% endfor %}
  </div>
</section>

