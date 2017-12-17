---
layout: page
title: Downloads
---

### Available Downloads
<ul class="downloads">
  {% for download in site.downloads %}

    {% unless download.next %}
      <h3>{{ download.date | date: '%Y' }} </h3>
    {% else %}
      {% capture year %}{{ download.date | date: '%Y' }}{% endcapture %}
      {% capture nyear %}{{ download.next.date | date: '%Y' }}{% endcapture %}
      {% if year != nyear %}
        <h3>{{ download.date | date: '%Y' }}</h3>
      {% endif %}
    {% endunless %}

    <li itemscope>
      <a href="{{ site.github.url }}{{ download.url }}">{{ download.title }}</a>
      <p class="download-date"><span><i class="fa fa-calendar" aria-hidden="true"></i> {{ download.date | date: "%B %-d" }}</span></p>
    </li>

  {% endfor %}
</ul>

