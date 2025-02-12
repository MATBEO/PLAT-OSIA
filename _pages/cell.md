---
layout: collection
permalink: /cell/
collection: cell
---

{% assign cell_posts = site.posts | where_exp:"post", "post.categories contains 'Cell'" %}

<h2>Articles classés sous « cell »</h2>
<ul>
  {% for post in cell_posts %}
    <li>
      <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>