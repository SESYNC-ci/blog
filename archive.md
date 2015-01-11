---
layout: default
title: Archive
parmalink: /archive
---

<div class="post">
  <h2>{{page.title}}</h2>
  {% for post in site.posts %}
    {% capture year %}{{ post.date | date: '%Y'}}{% endcapture %}
    {% unless pyear == year %}
      {% if pyear %}
        </ul>
      {% endif %}
      <h3>{{ year }}</h3>
      <ul>
    {% endunless %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% assign pyear = year %}
  {% endfor %}
</div>
