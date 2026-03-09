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

## Posts

{% assign lablife_posts = site.categories.lab-life %}
{% for post in lablife_posts %}
### [{{ post.title }}]({{ post.url | relative_url }})

{% if post.image %}
<a href="{{ post.url | relative_url }}">
  <img src="{{ post.image | relative_url }}" alt="{{ post.title }}" style="max-width: 420px; height: auto; border-radius: 10px; margin-bottom: 1rem;">
</a>
{% endif %}

{{ post.excerpt }}

---

{% endfor %}

### 📸 Gallery
*(Add photos here)*

<img src="/assets/images/life_placeholder.png" alt="Lab Life photo" width="700" style="border-radius:12px;">

---

### 📌 Want to join us?
If you are interested in joining CRE Lab, feel free to contact us.
