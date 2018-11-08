---
layout: post
title:  "Top October Contributors"
month: 2018-10
month-text: "October 2018"
software: DSpace
---
**The {{page.software}} Awards for {{page.month-text}} go to...**

{% comment %}Include monthly-awards.md and convert to HTML{% endcomment %}
{% capture monthly-awards %}{% include monthly-awards.md %}{% endcapture %}
{{ monthly-awards | markdownify }}
