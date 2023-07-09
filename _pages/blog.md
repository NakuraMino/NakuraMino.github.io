---
layout: blog
title: Blog
description: English majors look away
permalink: /blog
header: Writings
---
<div class="post-list"> 
    <li class="post-meta">
        {% assign sorted_posts = site.posts | sort: 'date' | reverse %}
        {% for post in sorted_posts %}
            {% if post.ready %}
            <ul>
                <div class="container">
                    <div class="row"> 
                        <div class="col-8">
                            <h5 class="font-weight-bold"><a href="{{ post.url }}"> {{ post.title }}</a></h5>
                            <p> {{ post.date | date: "%b %-d, %Y" }} </p>
                            {% if post.description %}
                            <p> {{ post.description }} </p>
                            {% endif %}
                        </div>
                        <div class="col">
                            <img class="img-fluid z-depth-1 rounded" src="{{ post.icon | prepend: '/assets/images/blog/' | relative_url }}">
                        </div>
                    </div>
                </div>
            </ul>
            {% endif %}
        {% endfor %}
    </li>
</div>