---
layout: site
title: How?
---

These are the systems that I return to, either because they are games I enjoy playing or they provide tools, settings or other procedures which I find useful. Games that I have just played once and that I don't anticipate replaying will not appear here. These are the games in the catch-all 'Others' games on the front page.

{% for block in site.data.systems %}
{% assign system = block[1] %}
- [{{ system.title}}]({{ system.url }})
  - {{ system.author }}
  - {{ system.description }}
{% endfor %}
