---
title: "Algorithm"
layout: archive
permalink: /categories/algorithm/
author_progile: true
sidebar_main: true
---

{% assign posts = site.categories.algorithm %}
{% for post in posts%}
{% include archive-single.html type=page.entries_layout %}
{% endfor %}