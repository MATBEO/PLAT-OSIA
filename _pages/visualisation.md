---
layout: collection
permalink: /visualisation/
collection: visualisation
---

{% assign cell_posts = site.posts | where_exp:"post", "post.categories contains 'Visualisation'" %}

<h2>Articles classés sous « Visualisation »</h2>
<ul>
  {% for post in cell_posts %}
    <li>
      <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>