---
layout: collection
permalink: /align/
collection: align
---

{% assign cell_posts = site.posts | where_exp:"post", "post.categories contains 'Alignement'" %}

<h2>Articles classés sous « Alignement »</h2>
<ul>
  {% for post in cell_posts %}
    <li>
      <a href="{{ site.baseurl }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>