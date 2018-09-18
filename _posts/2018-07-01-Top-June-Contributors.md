---
layout: post
title:  "Top June Contributors"
month: 2018-06
month-text: "June 2018"
---

**The Awards for {{page.month-text}} go to...**

* [Top Pull Request Creators](#top-pull-request-creators)
* [Top Pull Request Reviewers](#top-pull-request-reviewers)

## Top Pull Request Creators
These individuals created the most Pull Requests in {{page.month-text}}. For information on how these totals were calculated, see the [README]({{site.github.repository_url}}/blob/master/README.md)
{% assign dataset=site.data[page.month].pr-creators %}
{% include pr-awards-table.html %}

## Top Pull Request Reviewers
These individuals reviewed the most Pull Requests in {{page.month-text}}. For information on how these totals were calculated, see the [README]({{site.github.repository_url}}/blob/master/README.md)
{% assign dataset=site.data[page.month].pr-reviewers %}
{% include pr-awards-table.html %}
