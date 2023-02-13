---
layout: home
---

The write-ups from a bunch of solo table-top roleplaying games that I have played.

<dl>
  {% for report in site.reports %}
  
    {% unless report.series %}
  <dt><a href="{{ report.url | relative_url }}">{{ report.title }}</a>{% if report.system %}({% report.system %}){% endif %}</dt>
  <dd>{{ report.summary }}</dd>
      {% if report.adventure %}
  <dd>Following <i>{{ report.adventure.title }}</i> by {{ report.adventure.author }}</dd>
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
