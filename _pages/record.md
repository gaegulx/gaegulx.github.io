---
title: "Record"
layout: single
permalink: /record/
sidebar:
    nav: "sidebar-main"
---

{% assign posts = site.posts | where: "categories", "record" %}
{% for post in posts %}
    {% include archive-single.html post=post type="list" %}
{% endfor %}