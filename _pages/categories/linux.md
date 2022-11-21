---
layout: archive
permalink: categories/linux
title: "Linux"

author_profile: true
sidebar_main: true
sidebar:
  nav: "docs"
---

{% assign posts = site.categories.Linux %}
{% for post in posts %}
{% include custom-archive-single.html type=entries_layout %}
{% endfor %}
