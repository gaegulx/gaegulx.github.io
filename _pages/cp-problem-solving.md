---
title: "문제풀이"
layout: single
permalink: /cp/problem_solving/
author_profile: true
---

{% for post in site.posts %}
  {% if post.categories contains "cp" and post.subcategories contains "ps" %}
    {% include archive-single.html type="list" %}
  {% endif %}
{% endfor %}