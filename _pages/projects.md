---
layout: default
title: projects
permalink: /projects/
---

<div class="header-bar">
  <h1>My Pet Projects</h1>
  <h2>Oh no I'm embarrassed</h2>
</div>

<ul class="post-list">
 {% assign sorted = site.projects | sort: 'date' | reverse %}
  {% for project in sorted %}
    <li>
      <h4><a class="post-title" href="{{ project.url | prepend: site.baseurl | prepend: site.url }}">{{ project.title }}</a></h4>
      <p class="post-meta">{{ project.date | date: '%B %-d, %Y — %H:%M' }}</p>
      <p>{{ project.description }}</p>
    </li>
  {% endfor %}
</ul>

{% include pagination.html %}