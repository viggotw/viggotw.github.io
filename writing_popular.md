---
layout: page
title: "Popular Writing"
---

<h2>Popular Writing</h2>

<ul>
  {% assign all_items = site.posts | concat: site.links %}
  {% assign sorted_items = all_items | sort: 'date' | reverse %}
  {% for item in sorted_items %}
    <li style="margin-bottom:1em;">
      {% if item.external_url %}
        <strong>LINK:</strong>
        <a href="{{ item.external_url }}" target="_blank">{{ item.title }}</a>
      {% else %}
        <strong>BLOG:</strong>
        <a href="{{ item.url | relative_url }}">{{ item.title }}</a>
      {% endif %}
      <br>
      <small>{{ item.date | date: "%Y-%m-%d" }}</small><br>
      {% if item.summary %}
        {{ item.summary }}
      {% endif %}
    </li>
  {% endfor %}
</ul>
