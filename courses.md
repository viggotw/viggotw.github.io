---
layout: page
title: Courses
---

<p>
	Workshops and lecture formats that blend technical depth with practical guidance. Reach out if you'd like to run one
	of these sessions for your team or event.
</p>

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
				{% if course.language %}
					{% if has_meta %} · {% endif %}{{ course.language | upcase }}
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
			{% if course.learning_objectives %}
				{% assign objectives = course.learning_objectives | arrayify %}
				{% if objectives != empty %}
					<ul>
						{% for objective in objectives %}
							<li>{{ objective }}</li>
						{% endfor %}
					</ul>
				{% endif %}
			{% endif %}
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