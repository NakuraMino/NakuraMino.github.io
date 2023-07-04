---
layout: default
permalink: /projects.html
---

<h1> My Projects </h1>
<h4> It ain't much, but it's honest work </h4>

<ul> 
    {% for proj in site.projects %}
    <li>
        <h2><a href="{{ proj.url }}"> {{ proj.title }}</a></h2>
        {{ proj.excerpt }}
    </li>
    {% endfor %}
</ul>