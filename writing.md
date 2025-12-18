---
layout: page
title: "/writing"
permalink: /writing
---

### Technical Posts

{% assign technical_posts = site.posts | where: "category", "technical" %}
{% for post in technical_posts %}
- [{{ post.date | date: "%Y-%m-%d" }}] [{{ post.title }}]({{ post.url }})
{% endfor %}


### Lukewarm Takes

{% assign technical_posts = site.posts | where: "category", "takes" %}
{% for post in technical_posts %}
- [{{ post.date | date: "%Y-%m-%d" }}] [{{ post.title }}]({{ post.url }})
{% endfor %}


### Creative Writing

{% assign creative_posts = site.posts | where: "category", "creative" %}
{% for post in creative_posts %}
- [{{ post.date | date: "%Y-%m-%d" }}] [{{ post.title }}]({{ post.url }})
{% endfor %}

### Running Blog

{% assign creative_posts = site.posts | where: "category", "running" %}
{% for post in creative_posts %}
- [{{ post.date | date: "%Y-%m-%d" }}] [{{ post.title }}]({{ post.url }})
{% endfor %}