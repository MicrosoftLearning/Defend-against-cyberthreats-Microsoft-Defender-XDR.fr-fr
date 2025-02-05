---
title: Instructions de l’exercice
permalink: index.html
layout: home
---

# Exercices

Cette page répertorie des exercices associés au contenu de compétences Microsoft disponible sur [Microsoft Learn](https://learn.microsoft.com).

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Labs'" %} {% for activity in labs  %}
- [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }}) {% endfor %}

