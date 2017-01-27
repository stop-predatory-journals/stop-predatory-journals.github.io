---
layout: page
title: List of Misleading and Fake Metrics
shorttitle: Metrics
permalink: /metrics/
source: metrics
---

This is a list of possibly misleading metrics. 

Metrics are judged to be misleading if they meet the following criteria:

1. The website for the metric is nontransparent and provides little information about itself such as location, management team and its experience, other company information, and the like
2. The company charges journals for inclusion in the list.
3. The values (scores) for most or all of the journals on the list increase each year.
4. The company uses Google Scholar as its database for calculating metrics (Google Scholar does not screen for quality and indexes predatory journals)
5. The metric uses the term “[impact factor](https://web.archive.org/web/20170111172311/https://en.wikipedia.org/wiki/Impact_factor)” in its name.
6. The methodology for calculating the value is contrived, unscientific, or unoriginal.
7. The company exists solely for the purpose of earning money from questionable journals that use the gold open-access model. The company charges the journals and assigns them a value, and then the journals use the number to help increase article submissions and therefore revenue. Alternatively, the company exists as a front for an existing publisher and assigns values to that publisher’s journals.

{% assign letters = "a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z" | split: "," %}
{% assign numbers = "1,2,3,4,5,6,7,8,9,0" | split: "," %}

{% capture initials %}
  {% for thing in site.data.metrics %}
    {{ thing.name | remove: "The " | slice: 0, 1 | downcase }}
  {% endfor %}  
{% endcapture %}

{% assign inits = initials | split: '' | uniq %}

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
  {% for thing in site.data.metrics %}
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
