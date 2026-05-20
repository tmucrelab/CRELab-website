---
layout: single
title: "Awards & News"
permalink: /awards-news/
classes: wide
---

## Awards & News

Highlights of awards, recognitions, media mentions, and important updates from CRE Lab.

{% assign all_news = site.awards_news | sort: "date" | reverse %}

<div class="news-index-list">
  {% for item in all_news %}
    <article class="news-index-item">
      <span class="news-index-item__date">
        {{ item.date | date: "%Y.%m.%d" }}
      </span>

      <a class="news-index-item__title" href="{{ item.url | relative_url }}">
        {{ item.title }}
      </a>
    </article>
  {% endfor %}
</div>

<!--
<div class="news-index-list">
  {% for item in all_news %}
    <article class="news-index-item">
      <span class="news-index-item__date">
        {{ item.date | date: "%Y.%m.%d" }}
      </span>

      <h2 class="news-index-item__title">
        <a href="{{ item.url | relative_url }}">
          {{ item.title }}
        </a>
      </h2>

      {% if item.excerpt %}
        <div class="news-index-item__excerpt">
          {{ item.excerpt | strip_html | truncate: 180 }}
        </div>
      {% endif %}
      
    </article>
    <hr>
  {% endfor %}
</div>
-->

<!--
<section id="item-1">
  <h2>Item 1</h2>
  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
</section>

<hr>

<section id="item-2">
  <h2>Item 2</h2>
  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
</section>

<hr>

<section id="item-3">
  <h2>Item 3</h2>
  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
</section>

<hr>

<section id="item-4">
  <h2>Item 4</h2>
  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
</section>

<hr>

<section id="item-5">
  <h2>Item 5</h2>
  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
</section>
-->
