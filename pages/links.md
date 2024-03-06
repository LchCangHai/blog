---
layout: page
title: 链接
description: 没有链接的博客是孤独的
keywords: 友情链接
comments: true
menu: 链接
permalink: /links/
---

### 自我介绍
<ul>
{% for self in site.data.links %}
  {% if self.src == 'self' %}
  <li><a href="{{ self.url }}" target="_blank">{{ self.name}}</a></li>
  {% endif %}
{% endfor %}
</ul>

---

### 朋友

<ul>
{% for link in site.data.links %}
  {% if link.src == 'life' %}
  <li><a href="{{ link.url }}" target="_blank">{{ link.name}}</a></li>
  {% endif %}
{% endfor %}
</ul>

---

### 资源

##### &ensp; | 图书

<ul>
{% for link in site.data.links_my %}
  {% if link.src == 'resource' %}
    {% if link.src1 == 'book' %}
    <li><a href="{{ link.url }}" target="_blank">{{ link.name}}</a></li>
    {% endif %}
  {% endif %}
{% endfor %}
</ul>

---

### 收藏

##### &ensp; | VPN

<ul>
{% for link in site.data.links_my %}
  {% if link.src == 'collect' %}
    {% if link.src2 == 'vpn %}
    <li><a href="{{ link.url }}" target="_blank">{{ link.name}}</a></li>
    {% endif %}
  {% endif %}
{% endfor %}
</ul>