---
layout: post
title:  "Top July Contributors"
month: 2018-07
month-text: "July 2018"
software: DSpace
---
**The {{page.software}} Awards for {{page.month-text}} go to...**

{% comment %}Include monthly-awards.md and convert to HTML{% endcomment %}
{% capture monthly-awards %}{% include monthly-awards.md %}{% endcapture %}
{{ monthly-awards | markdownify }}
