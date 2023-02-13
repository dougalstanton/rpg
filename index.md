---
layout: home
---

The write-ups from a bunch of solo table-top roleplaying games that I have played.

<dl>
{% assign allseries = site.reports | groupby: "series" %}
{% for series in allseries %}
  {% if series.size == 1 %}
    {% assign report = series.items[0] %}
    <dt>
      <a href="{{ report.url | relative_url }}">{{ report.title }}</a> ({{ report.system }})
    </dt>
    <dd>{{ report.summary | markdownify }}</dd>
    {% if report.adventure %}
      <dd>Following <i>{{ report.adventure.title }}</i> by {{ report.adventure.author }}</dd>
    {% endif %}
  {% else %}
    <dt>{{ series.title }} ({{ series.items[0].system }})</dt>
    {% assign episodes = series.items | sort: "items.session" %}
    Session 
    {% for episode in episodes %}
      <a href="{{ episode.url | relative_url }}">{{ episode.session }}</a>{% unless forloop.last %},{% endunless %}
    {% endfor %}
  {% endif %}
{% endfor %}
</dl>
