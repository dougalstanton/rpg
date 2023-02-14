---
layout: page
title: Solo RPG Reports
---

The write-ups from a bunch of solo table-top roleplaying games that I have played.

{% assign oneshots = site.reports | where_exp:"i", "i.series == nil" %}
{% assign multiple = site.reports | where_exp:"i", "i.series" %}

<div>
  {% for r in oneshots %}
  
  <p><strong><a href="{{ r.url | relative_url }}">{{ r.title }}</a></strong>{% if r.system %} ({{ r.system }}){% endif %}</p>
    
  <p>{% if r.summary %}{{ r.summary }}{% endif %}
     {% if r.adventure %}<br/>Following <i>{{ r.adventure.title }}</i> by {{ r.adventure.author }}{% endif %}
  </p>
    
  {% endfor %}

  {% assign grouped = multiple | group_by: "series" %}
  {% for campaign in grouped %}  
    {% assign episodes = campaign.items | sort: "session" %}
  <p><strong>{{ campaign.name }} ({{ episodes[0].system }})</strong>
    {% if episodes[0].description %}
  <p>{{ episodes[0].description }}</p>
    {% endif %}
    {% for episode in episodes %}
  <ul>
  <li>Session {{ episode.session }}. <a href="{{ episode.url | relative_url }}">{{ episode.title }}</a> &mdash; {{ episode.summary }}</li>
  </ul>
    {% endfor %}
  {% endfor %}
  
</div>
