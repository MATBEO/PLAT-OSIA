---
title: multiplex
layout: collection
permalink: /multiplex/
collection: multiplex
---

{% assign cell_posts = site.posts | where_exp:"post", "post.categories contains 'Multiplex'" %}

<h2>Articles classés sous « Multiplex »</h2>
<ul>
  {% for post in cell_posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>