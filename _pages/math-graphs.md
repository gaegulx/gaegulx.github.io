---
title: "그래프이론"
layout: single
permalink: /math/graphs/
sidebar:
    nav: "sidebar-main"
---

{% assign posts = site.posts | where_exp: "post", "post.categories contains 'math' and post.subcategories contains '그래프이론'" %}

{% for post in posts %}
  {% include archive-single.html post=post type="list" %}
{% endfor %}