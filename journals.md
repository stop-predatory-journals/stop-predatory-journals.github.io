---
layout: page
title: List of Predatory Journals
shorttitle: Journals
permalink: /journals/
source: journals
---

This is a list of possibly [predatory journals](https://en.wikipedia.org/wiki/Predatory_open_access_publishing). 
The kernel for this list was extracted from the archive of Beall's list at [web.archive.org](https://web.archive.org/web/20170111172309/https://scholarlyoa.com/individual-journals/). 
It will be updated as new information or suggested edits are submitted or found by the maintainers of this site. 

This list is only for individual journals. 
See the other list for [publishers](/publishers/) potentially engaging in predatory practices.

{% assign letters = "a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z" | split: "," %}
{% assign numbers = "1,2,3,4,5,6,7,8,9,0" | split: "," %}

{% capture initials %}
  {% for thing in site.data.journals %}
    {{ thing.name | remove: "The " | slice: 0, 1 | downcase }}
  {% endfor %}  
{% endcapture %}

{% assign inits = initials | split: '' | uniq | sort %}

<ul class="listpage">
{% for letter in inits %}
{% unless numbers contains letter %}
<li><a href="#{{ letter | upcase }}">{{ letter | upcase }}</a></li>
{% else %}
{% continue %}
{% endunless %}
{% endfor %}
{% comment %}<li><a href="#0-9">0-9</a></li>{% endcomment %}
</ul>
<br/>

{% for letter in inits %}
{% if letters contains letter %}
  {% for thing in site.data.journals %}
    {% if letter == " " or numbers contains letter %}{% continue %}
    {% else %}
    {% if forloop.first %}
<h1 id="{{ letter | upcase }}" class="listpage">{{ letter | upcase }}</h1>
<ul>
    {% endif %}
    {% assign initial = thing.name | remove: "The " | slice: 0, 1 | downcase %}
    {% if initial == letter %}
<li><a href="{{ thing.url }}" target="_blank">{{ thing.name }}{% if thing.abbr %}&nbsp;({{ thing.abbr }}){% endif %}</a>{% if thing.alturl %}&nbsp;[<a href="{{ thing.alturl }}" target="_blank">alt. URL</a>]{% endif %}</li>
    {% endif %}
    {% if forloop.last %}
</ul>
<a href="#">Return to top</a>
    {% endif %}
  {% endif %}
  {% endfor %}
{% endif %}
{% endfor %}
<br/>
<ul class="listpage">
{% for letter in inits %}
<li><a href="#{{ letter | upcase }}">{{ letter | upcase }}</a></li>
{% endfor %}
{% comment %}<li><a href="#0-9">0-9</a></li>{% endcomment %}
</ul>
