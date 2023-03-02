---
layout: single
title: How?
header:
  overlay_image: "/assets/images/fox-hyde-Jsh4l4KpCw4-unsplash.jpg"
  overlay_color: "#000"
  overlay_filter: "0.2"
  caption: "Photo: [Fox & Hyde](https://unsplash.com/photos/Jsh4l4KpCw4)"
---

These are the separate games rules and supplements that I have used. Some games might not appear here because they are self-contained games. They will appear as 'Other' on the main page.

{% for block in site.data.systems %}
{% assign system = block[0] %}
- [{{ system.title}}]({{ system.url }})
  - {{ system.author }}
  - {{ system.description }}
{% endfor %}
