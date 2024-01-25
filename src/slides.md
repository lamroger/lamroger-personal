---
layout: layouts/slides.njk
title: Slides
---

# Slides

{%- for slideDeck in slides %}
- [{{ slideDeck.name }}](</files/slides/{{ slideDeck.name }}.pdf>)
{%- endfor %}
