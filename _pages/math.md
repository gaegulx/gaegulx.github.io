---
title: "Math"
layout: single
permalink: /math/
sidebar:
    nav: "sidebar-main"
---

{% assign posts = site.posts | where: "categories", "math" %}
{% for post in posts %}
    {% include archive-single.html post=post type="list" %}
{% endfor %}