---
layout: page
title: "Academic Writing"
---

<p>
	Peer-reviewed articles, working papers, and other scholarly pieces.
</p>

{% assign publications = site.publications | sort: 'date' | reverse %}
{% if publications.size > 0 %}
<ul style="list-style:none; padding-left:0;">
	{% for pub in publications %}
		<li style="margin-bottom:1.5em;">
			{% if pub.external_url %}
				<strong><a href="{{ pub.external_url }}" target="_blank" rel="noopener">{{ pub.title }}</a></strong>
			{% elsif pub.pdf %}
				<strong><a href="{{ pub.pdf | relative_url }}" target="_blank" rel="noopener">{{ pub.title }}</a></strong>
			{% else %}
				<strong><a href="{{ pub.url | relative_url }}">{{ pub.title }}</a></strong>
			{% endif %}
			<br>
			{% assign has_meta = false %}
					<small>
						{% if pub.authors %}
							{% assign author_list = pub.authors | arrayify %}
							{{ author_list | join: ", " }}
					{% assign has_meta = true %}
				{% endif %}
				{% if pub.venue %}
					{% if has_meta %} · {% endif %}<em>{{ pub.venue }}</em>
					{% assign has_meta = true %}
				{% endif %}
				{% if pub.date %}
					{% if has_meta %} · {% endif %}{{ pub.date | date: "%Y-%m-%d" }}
					{% assign has_meta = true %}
				{% endif %}
			</small>
			{% if pub.summary %}
				<br>
				{{ pub.summary }}
			{% endif %}
			{% assign has_links = pub.pdf or pub.external_url or pub.doi %}
			{% if has_links %}
				<div style="margin-top:0.4em;">
					{% if pub.pdf %}
						<a href="{{ pub.pdf | relative_url }}" target="_blank" rel="noopener">PDF</a>
					{% endif %}
					{% if pub.external_url %}
						{% if pub.pdf %} · {% endif %}
						<a href="{{ pub.external_url }}" target="_blank" rel="noopener">Publisher</a>
					{% endif %}
					{% if pub.doi %}
						{% if pub.pdf or pub.external_url %} · {% endif %}
						<a href="https://doi.org/{{ pub.doi }}" target="_blank" rel="noopener">DOI</a>
					{% endif %}
				</div>
			{% endif %}
		</li>
	{% endfor %}
</ul>
{% else %}
<p>No publications added yet. In the meantime, check out my profile on <a href="https://www.researchgate.net/profile/Viggo-Wivestad" target="_blank" rel="noopener">ResearchGate</a>.</p>
{% endif %}
