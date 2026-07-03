---
layout: page
title: Courses and Lectures
---

<p>
	Workshops and lecture formats that blend technical depth with practical guidance. Reach out if you'd like to run one
	of these sessions for your team or event.
</p>

<h2>Courses</h2>

{% assign course_entries = site.courses | sort: 'order' %}
{% if course_entries.size > 0 %}
<div class="course-list">
	{% for course in course_entries %}
		<section style="margin-bottom:2em;">
			<h3>
				<a href="{{ course.url | relative_url }}">{{ course.title }}</a>
			</h3>
			{% if course.summary %}
				<p>{{ course.summary }}</p>
			{% endif %}
			{% assign has_meta = false %}
			<small>
				{% if course.format %}
					{{ course.format }}
					{% assign has_meta = true %}
				{% endif %}
				{% if course.duration %}
					{% if has_meta %} · {% endif %}{{ course.duration }}
					{% assign has_meta = true %}
				{% endif %}
				{% if course.audience %}
					{% assign audience_list = course.audience | arrayify %}
					{% if audience_list != empty %}
						{% if has_meta %} · {% endif %}For {{ audience_list | join: ", " }}
						{% assign has_meta = true %}
					{% endif %}
				{% endif %}
			</small>
		</section>
	{% endfor %}
</div>
{% else %}
<p>No courses published yet. Check back soon.</p>
{% endif %}

<p>
	Interested in one of these courses or a bespoke session? <a href="{{ "/contact" | relative_url }}">Get in touch</a>
	to discuss formats, availability, and pricing.
</p>

{% assign lecture_entries = site.lectures | sort: 'date' | reverse %}
{% if lecture_entries.size > 0 %}
<h2>Lectures and Guest Teaching</h2>
<ul style="list-style:none; padding-left:0;">
	{% for item in lecture_entries %}
		<li style="margin-bottom:1.2em;">
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
		</li>
	{% endfor %}
</ul>
{% endif %}