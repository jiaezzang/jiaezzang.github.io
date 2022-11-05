---
layout: archive
permalink: categories/git
title: "GIT"

author_profile: true
sidebar_main: true
sidebar:
  nav: "docs"
---

{% assign posts = site.categories.Git %}
{% for post in posts %}
{% include custom-archive-single.html type=entries_layout %}
{% endfor %}
