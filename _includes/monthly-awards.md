* [Top Pull Request Creators](#top-pull-request-creators)
* [Top Pull Request Reviewers](#top-pull-request-reviewers)

## Top Pull Request Creators
These individuals created the most Pull Requests in {{page.month-text}}. For information on how these totals were calculated, see the [README]({{site.github.repository_url}}/blob/master/README.md)
{% assign filename=page.software | append: "-pr-creators" %}
{% assign dataset=site.data[page.month][filename] %}
{% include pr-awards-table.html %}

## Top Pull Request Reviewers
These individuals reviewed the most Pull Requests in {{page.month-text}}. For information on how these totals were calculated, see the [README]({{site.github.repository_url}}/blob/master/README.md)
{% assign filename=page.software | append: "-pr-reviewers" %}
{% assign dataset=site.data[page.month][filename] %}
{% include pr-awards-table.html %}
