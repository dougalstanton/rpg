---
layout: single
title: How?
---

These are the separate games rules and supplements that I have used. Some games might not appear here because they are self-contained games. They will appear as 'Other' on the main page.

{% for system in site.date.systems %}
- [{{ system.title}}]({{ system.url }})
  - {{ system.author }}
  - {{ system.description }}
{% endfor %}
