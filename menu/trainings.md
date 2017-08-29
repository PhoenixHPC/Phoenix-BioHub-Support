---
layout: page
title:  Workshops
---

#### Phoenix Team @ UofA offers many training programs and workshops. Following list contains past and present training materials.

<ul class="training">
  {% for training in site.trainings reversed%}

    {% unless training.next %}
      <h3>{{ training.date | date: '%Y' }} </h3>
    {% else %}
      {% capture year %}{{ training.date | date: '%Y' }}{% endcapture %}
      {% capture nyear %}{{ training.next.date | date: '%Y' }}{% endcapture %}
      {% if year != nyear %}
        <h3>{{ training.date | date: '%Y' }}</h3>
      {% endif %}
    {% endunless %}

    <li trainingitemscope>
      <a href="{{ site.github.url }}{{ training.url }}">{{ training.title }}</a>
      <p class="training-date"><span><i class="fa fa-calendar" aria-hidden="true"></i> {{ training.date | date: "%B %-d" }}</span></p>
    </li>

  {% endfor %}
</ul>
