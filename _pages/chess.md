---
layout: blog
title: Chess
description: If you don't play chess, this blog will make no sense to you.
header: Chess
permalink: /chess
---

<div class="post-list"> 
    <li class="post-meta">
        {% assign sorted_posts = site.chess | sort: 'date' | reverse %}
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
                        {%- assign icon_path = post.icon | prepend: '/assets/images/chess/' -%}
                        {%- assign icon_class = 'icon img-fluid z-depth-1 rounded' -%}
                        {%- assign max_height = '70px' -%}
                        <div class="float-right col-sm-2"> {% include image.html path=icon_path class=icon_class max-height=max_height%} </div>
                    </div>
                </div>
            </ul>
            {% endif %}
        {% endfor %}
    </li>
</div>