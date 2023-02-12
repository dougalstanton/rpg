---
layout: home
---

The write-ups from a bunch of solo table-top roleplaying games that I have played.

<dl>
{% for report in site.reports %}
  <dt>
    <a href="{{ report.url }}">{{ report.title }}</a>
  </dt>
  <dd>{{ report.summary | markdownify }}</dd>
{% endfor %}
</dl>
