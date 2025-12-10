---
layout: page
title: Calendar
description: Listing of course modules and topics.
---

# Cronograma del curso

## Tema 1 - Lógica proposicional

{% for module in site.modules %}
{% if module.slug == 'week-01' or module.slug == 'week-02' %}
{{ module }}
{% endif %}
{% endfor %}

## Tema 2 - Lógica cuantificacional

{% for module in site.modules %}
{% if module.slug == 'week-03' %}
{{ module }}
{% endif %}
{% endfor %}

{% for module in site.modules %}
{% if module.slug == 'week-04' %}
{{ module }}
{% endif %}
{% endfor %}
