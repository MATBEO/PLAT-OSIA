---
title: align
layout: collection
permalink: /align/
collection: align
---

{% assign cell_posts = site.posts | where_exp:"post", "post.categories contains 'Align'" %}

<h2>Articles classés sous « Align »</h2>
<ul>
  {% for post in cell_posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>