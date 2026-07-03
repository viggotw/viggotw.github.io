---
layout: page
title: "Public Engagement"
---

<p>
	Op-eds, media appearances, podcasts, talks, and blog posts.
</p>

<ul>
  {% assign all_items = site.posts | concat: site.links %}
  {% assign sorted_items = all_items | sort: 'date' | reverse %}
  {% for item in sorted_items %}
    <li style="margin-bottom:1em;">
      {% if item.kind %}
        <strong>{{ item.kind | upcase }}:</strong>
      {% elsif item.external_url %}
        <strong>LINK:</strong>
      {% else %}
        <strong>BLOG:</strong>
      {% endif %}
      {% if item.external_url %}
        <a href="{{ item.external_url }}" target="_blank">{{ item.title }}</a>
      {% elsif item.collection == "posts" %}
        <a href="{{ item.url | relative_url }}">{{ item.title }}</a>
      {% else %}
        {{ item.title }}
      {% endif %}
      <br>
      <small>{% if item.display_date %}{{ item.display_date }}{% else %}{{ item.date | date: "%Y-%m-%d" }}{% endif %}</small><br>
      {% if item.summary %}
        {{ item.summary }}
      {% endif %}
    </li>
  {% endfor %}
</ul>
