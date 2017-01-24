---
layout: page
title: List of Predatory Journals
shorttitle: Journals
permalink: /journals/
source: journals
---

{% assign letters = "a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w" | split: "," %}
{% assign numbers = "1,2,3,4,5,6,7,8,9,0" | split: "," %}

<ul class="listpage">
{% for letter in letters %}
<li><a href="#{{ letter | upcase }}">{{ letter | upcase }}</a></li>
{% endfor %}
{% comment %}<li><a href="#0-9">0-9</a></li>{% endcomment %}
</ul>

{% for letter in letters %}
  {% for thing in site.data.journals %}
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
{% comment %}<h1 id="0-9">0-9</h1>
<ul>
{% for number in numbers %}
  {% for thing in site.data.journals %}
    {% assign initial = thing.name | slice: 0, 1 | downcase %}
    {% if initial == number %}
<li><a href="{{ thing.url }}" target="_blank">{{ thing.name }}{% if thing.abbr %}&nbsp;({{ thing.abbr }}){% endif %}</a></li>
    {% endif %}
  {% endfor %}
{% endfor %}
</ul>{% endcomment %}

<ul class="listpage">
{% for letter in letters %}
<li><a href="#{{ letter | upcase }}">{{ letter | upcase }}</a></li>
{% endfor %}
{% comment %}<li><a href="#0-9">0-9</a></li>{% endcomment %}
</ul>