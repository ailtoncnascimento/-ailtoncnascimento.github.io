---
title: Miscelânea
icon: fas fa-feather-pointed
order: 3
---

Textos avulsos: matemática recreativa e curiosidades, reminiscências, poesias e variedades.

{% for post in site.posts %}
- **[{{ post.title }}]({{ post.url }})** — <small>{{ post.date | date: "%d/%m/%Y" }}</small>
{% endfor %}

{% if site.posts.size == 0 %}
*Nenhum texto publicado ainda.*
{% endif %}
