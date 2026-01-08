---
tags:
  - literature/{{itemType}}
citekey: {{citekey}}
title: "{{title}}"
year: {{date | default("Unknown")}}
authors: {{authors}}
---
---

## Reading Notes
{% persist "reading_notes" %}

{% endpersist %}

---

## Annotations
{% for page, pageAnnotations in annotations | groupby("pageLabel") %}
### Page {{page}}
{% persist "page_" + page %}
{% endpersist %}
{% for annotation in pageAnnotations %}
{%- if annotation.imageRelativePath %}
> [!figure]
> ![[{{annotation.imageRelativePath}}]]{% if annotation.comment %}
> *{{annotation.comment}}*{% endif %}

{%- elif annotation.annotatedText %}
{%- set calloutType = "note" -%}
{%- if annotation.color == "#ff6666" -%}{%- set calloutType = "critical" -%}
{%- elif annotation.color == "#5fb236" -%}{%- set calloutType = "definition" -%}
{%- elif annotation.color == "#2ea8e5" -%}{%- set calloutType = "question" -%}
{%- elif annotation.color == "#ffd400" -%}{%- set calloutType = "highlight" -%}
{%- endif %}
> [!{{calloutType}}]
> {{annotation.annotatedText | replace("\n", "\n> ")}}{% if annotation.comment %}
> *{{annotation.comment}}*{% endif %}

{%- elif annotation.comment %}
> [!memo]
> {{annotation.comment | replace("\n", "\n> ")}}

{%- endif %}
{% endfor %}
{% endfor %}

---

## Summary
{% persist "summary" %}

{% endpersist %}
