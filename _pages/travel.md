---
layout: page
title: Journey to middle east
permalink: /travel/
description: When I was 20 years old, I traveled several countries(mostly middle east) for historical sites, as a big fan of history. This experience ultimately lead me to physics.
nav: true
nav_order: 5
display_categories: [First trip, Second trip, Third trip]
horizontal: false
---

<!-- pages/travel.md -->
<div class="travel">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized travel -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category" style="color: black;">{{ category }}</h2>
  </a>
  {% assign categorized_travel = site.travel | where: "category", category %}
  {% assign sorted_travel = categorized_travel | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_travel %}
      {% include travel_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-4">
    {% for project in sorted_travel %}
      {% include travel.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display travel without categories -->

{% assign sorted_travel = site.travel | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_travel %}
      {% include travel_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_travel %}
      {% include travel.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
