---
layout: page
title: Dev TIL
permalink: /dev-til/
---

Small tutorials and how-to's from small learnings. Mostly focused on ruby, rails and python.

<div>
{% for post in site.posts %}
  {% if post.categories contains "til" %}

      <h5><a href="{{ post.url }}">{{ post.title }}</a></h5>

  {% endif %}
{% endfor %}
</div>


