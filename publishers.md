---
layout: listpage
title: List of Predatory Publishers
shorttitle: Publishers
permalink: /publishers/
source: publishers
---

This is a list of possibly [predatory publishers](https://en.wikipedia.org/wiki/Predatory_open_access_publishing). 
The kernel for this list was extracted from the archive of Beall's List at [web.archive.org](https://web.archive.org/web/20170111172306/https://scholarlyoa.com/publishers/). 
It will be updated as new information or suggested edits are submitted or found by the maintainers of this site. 

This is a list of publishers that may be engaging in predatory practices. 
See the other list for [individual journals](/journals/) potentially engaging in predatory practices.

{% assign letters = "a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z" | split: "," %}
{% assign numbers = "1,2,3,4,5,6,7,8,9,0" | split: "," %}

<ul class="listpage">
{% for letter in letters %}
<li><a href="#{{ letter | upcase }}">{{ letter | upcase }}</a></li>
{% endfor %}
<li><a href="#0-9">0-9</a></li>
</ul>

{% for letter in letters %}
  {% for thing in site.data.publishers %}
    {% if forloop.first %}
<h1 id="{{ letter | upcase }}" class="listpage">{{ letter | upcase }}</h1>
<ul>
    {% endif %}
    {% assign initial = thing.name | slice: 0, 1 | downcase %}
    {% if initial == letter %}
<li><a href="{{ thing.url }}" target="_blank">{{ thing.name }}{% if thing.abbr %}&nbsp;({{ thing.abbr }}){% endif %}</a></li>
    {% endif %}
    {% if forloop.last %}
</ul>
<a href="#">Return to top</a>
    {% endif %}
  {% endfor %}
{% endfor %}
<h1 id="0-9">0-9</h1>
<ul>
{% for number in numbers %}
  {% for thing in site.data.publishers %}
    {% assign initial = thing.name | slice: 0, 1 | downcase %}
    {% if initial == number %}
<li><a href="{{ thing.url }}" target="_blank">{{ thing.name }}{% if thing.abbr %}&nbsp;({{ thing.abbr }}){% endif %}</a></li>
    {% endif %}
  {% endfor %}
{% endfor %}
</ul>

<ul class="listpage">
{% for letter in letters %}
<li><a href="#{{ letter | upcase }}">{{ letter | upcase }}</a></li>
{% endfor %}
<li><a href="#0-9">0-9</a></li>
</ul>