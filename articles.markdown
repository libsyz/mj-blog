---
layout: page
title: Articles
permalink: /articles/
---

Larger explorations of topics that interest me. Mostly using it as a channel for learning and satisfying my curiosity. From Service Design to Performance Psychology, it's a free for all.


<div>
{% for post in site.posts %}
  {% if post.categories contains "articles" %}

      <h5><a href="{{ post.url }}">{{ post.title }}</a></h5>

  {% endif %}
{% endfor %}
</div>

