---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: index
title: Home
---

# **Hi!**
I'm Miguel. You can call me an uber-generalist.
I work for Le Wagon now.


It would be cool to be able to display posts over here.

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
