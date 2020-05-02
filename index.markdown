---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: index
title: Home
---

<h1> Hi! </h1>
<p> I am an all round product guy with a background in psychology and organizational development. Today, I help out with designing the best tech learning experiences I can, building an agile team and tinkering with code. Currently taking care of Product and Growth at Le Wagon in Singapore</p>

<ul class="">
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
