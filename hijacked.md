---
layout: page
title: List of Hijacked Journals
shorttitle: Hijacked
permalink: /hijacked/
source: hijacked
---

This is a list of journals that appear to have been hijacked, meaning that their websites or branding have been co-opted by a predatory journal or publisher. 

{% assign letters = "a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z" | split: "," %}
{% assign numbers = "1,2,3,4,5,6,7,8,9,0" | split: "," %}

{% capture initials %}
  {% for thing in site.data.hijacked %}
    {{ thing.hijacked | remove: "The " | slice: 0, 1 | downcase }}
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
</ul>
<br/>

<table class="2col">
{% for letter in inits %}
{% if letters contains letter %}
  {% for thing in site.data.hijacked %}
  {% if letter == " " or numbers contains letter %}
    {% continue %}
  {% else %}
    {% if forloop.first %}
<tr>
  <th style="text-align:left"><h1 id="{{ letter | upcase }}">{{ letter | upcase }}</h1></th>
</tr>
<tr>
  <th style="text-align:left">Hijacked Journal</th>
  <th style="text-align:left">Authentic Journal</th>
</tr>
    {% endif %}
    {% assign initial = thing.hijacked | remove: "The " | slice: 0, 1 | downcase %}
    {% if initial == letter %}
<tr>
  <td><a href="{{ thing.hijackedurl }}" target="_blank">{{ thing.hijacked }}{% if thing.hijackedabbr %}&nbsp;({{ thing.hijackedabbr }}){% endif %}</a>{% if thing.althijackedurl %}&nbsp;[<a href="{{ thing.althijackedurl }}" target="_blank">alt. URL</a>]{% endif %}</td>
  <td><a href="{{ thing.authenticurl }}" target="_blank">{{ thing.authentic }}{% if thing.authenticabbr %}&nbsp;({{ thing.abbr }}){% endif %}</a>{% if thing.altauthenticurl %}&nbsp;[<a href="{{ thing.altauthenticurl }}" target="_blank">alt. URL</a>]{% endif %}</td>
</tr>
    {% endif %}
    {% if forloop.last %}
<tr>
  <td>
    <br/>
    <a href="#">Return to top</a>
  </td>
</tr>
    {% endif %}
{% endif %}
  {% endfor %}
{% endif %}
{% endfor %}
</table>
<br/>
<ul class="listpage">
{% for letter in inits %}
<li><a href="#{{ letter | upcase }}">{{ letter | upcase }}</a></li>
{% endfor %}
{% comment %}<li><a href="#0-9">0-9</a></li>{% endcomment %}
</ul>
