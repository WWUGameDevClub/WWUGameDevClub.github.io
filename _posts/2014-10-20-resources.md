---
title: Resources
---

This is where you'll find a listing of all the resources the club has compiled for other members to use.

### Table of contents

{% comment %}It's important that the template is formatted like it is so that the markdown comes out correctly.{% endcomment %}
{% for category in site.data.resources %}
- [{{ category.name }}](#{{ category.name|slugify }}){% for entry in category.entries %}
    - [{{ entry.name }}](#{{ category.name|slugify }}-{{ entry.name|slugify }}){% endfor %}{% endfor %}

{% for category in site.data.resources %}

### <a name="{{ category.name|slugify }}">{{ category.name }}</a>

{{ category.description }}

{% for entry in category.entries %}

#### <a name="{{ category.name|slugify }}-{{ entry.name|slugify }}">{{ entry.name }}</a>

{{ entry.description }}

{% endfor %}
{% endfor %}
