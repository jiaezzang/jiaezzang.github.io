---
layout: archive
permalink: categories/Ruby
title: "Ruby"

author_profile: true
sidebar_main: true
sidebar:
  nav: "docs"
---

{% assign posts = site.categories.Ruby %}
{% for post in posts %}
{% include custom-archive-single.html type=entries_layout %}
{% endfor %}
