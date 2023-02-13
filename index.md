---
layout: home
---

The write-ups from a bunch of solo table-top roleplaying games that I have played.

{% assign oneshots = site.reports | where_exp:"i", "i.series == nil" %}
{% assign multiple = site.reports | where_exp:"i", "i.series" %}

{{ oneshots.size }} one shots and {{ multiple.size }} continuing sessions.

<dl>
  {% for r in oneshots %}
  
  <dt><a href="{{ r.url | relative_url }}">{{ r.title }}</a>{% if r.system %} ({{ r.system }}){% endif %}</dt>
    {% if r.summary %}
  <dd>{{ r.summary }}</dd>
    {% endif %}
    {% if r.adventure %}
  <dd>Following <i>{{ r.adventure.title }}</i> by {{ r.adventure.author }}</dd>
    {% endif %}
    
  {% endfor %}

  {% assign grouped = multiple | group_by: "series" %}
  {% for campaign in grouped %}  

  <dt>{{ campaign.name }} ({{ campaign.items[0].system }})</dt>
    {% assign episodes = campaign.items | sort: "session" %}

    {% for episode in episodes %}
  <dd>Session {{ episode.session }}.
    <a href="{{ episode.url | relative_url }}">{{ episode.title }}</a>
  </dd>
    {% endfor %}
  {% endfor %}
  
</dl>
