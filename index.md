---
layout: home
---

The write-ups from a bunch of solo table-top roleplaying games that I have played.

<dl>
  {% for r in site.reports %}
  
    {% unless r.series %}
  <dt><a href="{{ r.url | relative_url }}">{{ r.title }}</a>{% if r.system %}({% r.system %}){% endif %}</dt>
  <dd>{{ r.summary }}</dd>
      {% if r.adventure %}
  <dd>Following <i>{{ r.adventure.title }}</i> by {{ r.adventure.author }}</dd>
      {% endif %}
    {% endunless %}
    
  {% endfor %}
  
  {% assign multiples = site.reports | where: "series" | groupby: "series" %}
  {% for campaign in multiples %}
  <dt>{{ campaign.name }} ({{ campaign.items[0].system }})</dt>
    {% assign episodes = campaign.items | sort: "session" %}
    {% for episode in episodes %}
  <dd>Session {{ episode.session }}.
    <a href="{{ episode.url | relative_url }}">{{ episode.title }}</a>
  </dd>
    {% endfor %}
  {% endfor %}
</dl>
