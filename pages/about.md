---
layout: page
title: About
description: 勤奋的程序员
keywords: Nieh, 冰笑
comments: true
menu: About
permalink: /about/
---

I'm NiehXiaoBin. 


## Me

{% for website in site.data.social %}
* {{ website.sitename }}：[@{{ website.name }}]({{ website.url }})
{% endfor %}

## Skill Keywords

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
