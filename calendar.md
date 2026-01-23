---
layout: page
title: Cronograma
description: Listing of course modules and topics.
nav_order: 3
---

# Cronograma del curso

## Tema 1 - Lógica proposicional

{% for module in site.modules %}
{% if module.slug == 'week-01' or module.slug == 'week-02' or module.slug == 'week-03' or module.slug == 'week-04' or module.slug == 'week-05' %}
{{ module }}
{% endif %}
{% endfor %}

## Tema 2 - Lógica cuantificacional

Aca vamos
