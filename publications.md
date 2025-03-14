---
layout: default
title: Publications
---

# Publications

{% assign sorted_years = site.data.publications | map: "year" | uniq | sort | reverse %}

{% for year in sorted_years %}

## {{ year }}

{% for pub in site.data.publications %}
{% if pub.year == year %}

<div class="publication">
  {% if pub.doi %}
  <h3><a href="{{ pub.doi }}">{{ pub.title }}</a></h3>
  {% else %}
  <h3>{{ pub.title }}</h3>
  {% endif %}
  <p class="publication-authors">{{ pub.authors }}</p>
  <p class="publication-venue">{{ pub.venue }} {% if pub.copyright %}&#124; {{ pub.copyright }}{% endif %}</p>
  {% if pub.pdf %}
  <a href="{{ pub.pdf }}" class="resource-link">PDF</a>
  {% endif %}
</div>
    {% endif %}
  {% endfor %}
{% endfor %}
