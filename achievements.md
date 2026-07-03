---
layout: page
title: "Achievements"
---

<p>
	Awards, talks, lectures, and other dissemination activities, in reverse chronological order.
	Op-eds and articles are listed under <a href="{{ "/writing_popular" | relative_url }}">Popular Writing</a>.
</p>

{% assign award_entries = site.achievements | where: "category", "award" | sort: 'date' | reverse %}
{% assign dissemination_entries = site.achievements | where: "category", "dissemination" | sort: 'date' | reverse %}

{% if award_entries.size > 0 %}
<h2>Awards and Prizes</h2>
<ul style="list-style:none; padding-left:0;">
	{% for item in award_entries %}
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
{% endif %}

{% if dissemination_entries.size > 0 %}
<h2>Dissemination and Teaching</h2>
<ul style="list-style:none; padding-left:0;">
	{% for item in dissemination_entries %}
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
{% endif %}

{% if award_entries.size == 0 and dissemination_entries.size == 0 %}
<p>Nothing here yet. Check back soon.</p>
{% endif %}
