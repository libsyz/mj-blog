---
layout: page
title: Coda
permalink: /coda/
---

Coda is the final act of an opera. It gives the audience time to reflect and digest.
I leave small musings and reflections. Sometimes I manage to make sense.

<ul class="">
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
