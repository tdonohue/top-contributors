---
layout: post
title:  "Top August Contributors"
month: 2018-08
month-text: "August 2018"
---

**The Awards for {{page.month-text}} go to...**

* [Top Pull Request Creators](#top-pr-creators)
* [Top Pull Request Reviewers](#top-pr-reviewers)

# Top PR Creators
These individuals created the most Pull Requests in {{page.month-text}}. For information on how these totals were calculated, see the [README](README.md)
{% assign dataset=site.data[page.month].pr-creators %}
{% include pr-awards-table.html %}

# Top PR Reviewers
These individuals reviewed the most Pull Requests in {{page.month-text}}. For information on how these totals were calculated, see the [README](README.md)
{% assign dataset=site.data[page.month].pr-reviewers %}
{% include pr-awards-table.html %}
