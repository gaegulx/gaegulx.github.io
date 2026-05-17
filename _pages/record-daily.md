---
title: "일기"
layout: single
permalink: record/daily/
sidebar:
    nav: "sidebar-main"
---

{% assign posts = site.posts | where: "categories", "record" | where: "subcategories", "일기"%}
{% for post in posts %}
    {% include archive-single.html post=post type="list" %}
{% endfor %}