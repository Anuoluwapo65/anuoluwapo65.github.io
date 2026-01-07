---
layout: page
title: projects
permalink: /projects/
description: A growing collection of your cool projects.
nav: true
nav_order: 3
display_categories: [work, fun]
horizontal: false
---

<!-- pages/projects.md -->
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
   **{{ category }}**
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  {% capture projects_row %}
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
  {% endcapture %}
  {{ projects_row | markdownify }}
  {% else %}
  {% capture projects_row %}
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  {% endcapture %}
  {{ projects_row | markdownify }}
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  {% capture projects_row %}
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
  {% endcapture %}
  {{ projects_row | markdownify }}
  {% else %}
  {% capture projects_row %}
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  {% endcapture %}
  {{ projects_row | markdownify }}
  {% endif %}
{% endif %}
