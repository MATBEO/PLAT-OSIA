---
title: cell
layout: collection
permalink: /cell/
collection: cell
entries_layout: grid
classes: wide
---

{% assign cell_posts = site.posts | where:"categories", "Cell" %}

{% comment %}
Si vos posts définissent la catégorie « Cell » dans leur front matter (par exemple :
categories: [Cell] ou categories: Cell), utilisez la syntaxe ci-dessous.
{% endcomment %}

{% assign cell_posts = site.posts | where_exp:"post", "post.categories contains 'Cell'" %}

<h2>Articles classés sous « Cell »</h2>
<ul>
  {% for post in cell_posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <small> - {{ post.date | date: "%d %B %Y" }}</small>
    </li>
  {% endfor %}
</ul>