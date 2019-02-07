---
layout: default
title: Home
---

{% for post in site.posts %}
<div class="post-preview">
  <a href="{{ post.url }}">
    <h2 class="post-title"> {{ post.title }} </h2>
    <h3 class="post-subtitle"> {{ post.subtitle } </h3>
  </a>
  <p class="post-meta">Posted by <a href="#"> {{ site.author }}</a> on {{ page.date | date: "%b %d, %Y"}}</p>
</div>
<hr>
{% endfor %}
