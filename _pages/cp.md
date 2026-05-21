---
title: "Competitive Programming"
layout: single
permalink: /cp/
author_profile: true
---

{% for post in site.posts %}
  {% if post.categories contains "cp" %}
    {% include archive-single.html type="list" %}
  {% endif %}
{% endfor %}