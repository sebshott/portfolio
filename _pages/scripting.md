---
layout: home-page
title: Parametric Scripting
permalink: /scripting/
---

<ol class="post-card-box clearfix">
  {% for post in site.posts %}
  {% if post.categories contains 'scripting' %}
  <li>
    <div class="post-card">
      <a href="{{post.url | prepend: site.baseurl}}" class="post-card-image" style="background-image: url( {{ "/assets/img/" | prepend: site.baseurl | append : post.img}} )">
      </a>
      <div class="post-card-body">
        {% for tag in post.tags %}
        <a href="{{site.baseurl}}/tags#{{tag}}" class="tag">|&#32;{{ tag }}</a>
        {% endfor %}
        <a href="{{post.url | prepend: site.baseurl}}" class="post-card-link"><h3 class="post-card-title">{{post.title}}</h3></a>
      </div>
    </div>
  </li>
  {% endif %}
  {% endfor %}
</ol>
