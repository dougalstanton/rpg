---
layout: home
---

The write-ups from a bunch of solo table-top roleplaying games that I have played.

<dl>
{% assign allseries = site.reports | groupby: "series" %}
{% for series in allseries %}
  {% if series.size == 1 %}
  {% assign report = series.item[0] %}
  <dt>
    <a href="{{ report.url | relative_url }}">{{ report.title }}</a> ({{ report.system }})
  </dt>
  <dd>{{ report.summary | markdownify }}</dd>
  {% if report.adventure %}
  <dd>Following <i>{{ report.adventure.title }}</i> by {{ report.adventure.author }}</dd>
  {% endif %}
  {% else %}
  <dt>{{ report.title }} ({{ report.system }})</dt>
  Session 
  {% for episode in series.item | sort: "session" %}
  <a href="{{ episode.url | relative_url }}">{{ episode.session }}</a>{% unless forloop.last %},{% endunless %}
  {% endfor %}
{% endfor %}
</dl>
