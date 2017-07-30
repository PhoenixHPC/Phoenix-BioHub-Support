---
layout: page 
title: Announcements
---
<ul class="announcements">
  {% for announcement in site.announcements %}
 
    {% unless announcement.next %}
      <h3>{{ announcement.date | date: '%Y' }} </h3>
    {% else %}
      {% capture year %}{{ announcement.date | date: '%Y' }}{% endcapture %}
      {% capture nyear %}{{ announcement.next.date | date: '%Y' }}{% endcapture %}
      {% if year != nyear %}
        <h3>{{ announcement.date | date: '%Y' }}</h3>
      {% endif %}
    {% endunless %}

    <li itemscope>
      <a href="{{ site.github.url }}{{ announcement.url }}">{{ announcement.title }}</a>
      <p class="announcement-date"><span><i class="fa fa-calendar" aria-hidden="true"></i> {{ announcement.date | date: "%B %-d" }}</span></p>
    </li>

  {% endfor %}
</ul>

