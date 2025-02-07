---
title: pattern
layout: collection
permalink: /pattern/
collection: pattern
---

{% assign cell_posts = site.posts | where_exp:"post", "post.categories contains 'Pattern'" %}

<h2>Articles classés sous « Pattern »</h2>
<ul>
  {% for post in cell_posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>