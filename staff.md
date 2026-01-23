---
layout: page
title: Staff
description: A listing of all the course staff members.
nav_order: 5
---

# Staff

## Docentes de planta

{% assign instructors = site.staffers | where: 'role', 'Docente de planta' %}
{% for staffer in instructors %}
{{ staffer }}
{% endfor %}

## Docentes de cátedra

{% assign instructors = site.staffers | where: 'role', 'Docente de catedra' %}
{% for staffer in instructors %}
{{ staffer }}
{% endfor %}
