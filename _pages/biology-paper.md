---
title: "논문리뷰"
layout: single
permalink: /biology/paper/
sidebar:
    nav: "sidebar-main"
---

{% assign posts = site.posts | where: "categories", "biology" | where: "subcategories", "논문리뷰"%}
{% for post in posts %}
    {% include archive-single.html post=post type="list" %}
{% endfor %}