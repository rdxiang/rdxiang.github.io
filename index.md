---
layout: archive
permalink: /
title: "Welcome"
date: 
modified:
excerpt: 
image:
  feature:
  teaser:
  thumb:
ads: false
---


It' a blog everyone! My name's Rachel, I'm a student at the University of Michigan who likes writing about comupter science, art, and ocasionally other things. After a year long haitus, I'm now (hopefully) returning to writing regularly.


<a href="http://rachelxiang.com/" target="_blank">My portfolio</a>

---

<div class="tiles">
{% for post in site.posts %}
	{% include post-grid.html %}
{% endfor %}
</div><!-- /.tiles --> 