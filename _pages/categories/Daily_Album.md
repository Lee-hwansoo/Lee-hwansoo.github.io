---
title: "Album"
layout: archive
permalink: categories/daily/album
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.Album %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
