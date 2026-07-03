---
layout: page
title: "Achievements"
---

<p>
	Awards and prizes, in reverse chronological order. Talks, media appearances, and op-eds are listed under
	<a href="{{ "/writing_popular" | relative_url }}">Public Engagement</a>, and lectures and teaching under
	<a href="{{ "/courses" | relative_url }}">Courses and Lectures</a>.
</p>

{% assign achievement_entries = site.achievements | sort: 'date' | reverse %}
{% if achievement_entries.size > 0 %}
<ul style="list-style:none; padding-left:0;">
	{% for item in achievement_entries %}
		<li style="margin-bottom:1.5em;">
			<strong>{{ item.title }}</strong>
			<br>
			{% assign has_meta = false %}
			<small>
				{% if item.venue %}
					<em>{{ item.venue }}</em>
					{% assign has_meta = true %}
				{% endif %}
				{% if item.display_date %}
					{% if has_meta %} · {% endif %}{{ item.display_date }}
				{% elsif item.date %}
					{% if has_meta %} · {% endif %}{{ item.date | date: "%B %Y" }}
				{% endif %}
			</small>
			{% assign body = item.content | strip %}
			{% if body != "" %}
				<div style="margin-top:0.4em;">
					{{ body | markdownify }}
				</div>
			{% endif %}
			{% if item.links %}
				<div style="margin-top:0.4em;">
					{% for link in item.links %}
						{% unless forloop.first %} · {% endunless %}
						<a href="{{ link.url }}" target="_blank" rel="noopener">{{ link.label }}</a>
					{% endfor %}
				</div>
			{% endif %}
		</li>
	{% endfor %}
</ul>
{% else %}
<p>Nothing here yet. Check back soon.</p>
{% endif %}
