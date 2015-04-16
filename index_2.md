---
layout: default
title: 大漠留香的博客
---

<h2>{{ page.title }}</h2>
<p>最新文章</p>
<ul>
  {% for post in site.posts %}
    <li>{{ post.date | date_to_string }} <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

New lists.

<ul>
  {% for post in site.posts %}
    <a  href='{{ post.url }}' class="list-group-item pjaxlink clearfix"> {{post.title}} </a>
	<span class="badge" align="right">{{ post.date | date:"%Y年%m月%d日" }}</span>
  {% endfor %}
</ul>



---
layout: default
title: 大漠留香的博客
---

<h2>{{ page.title }}</h2>
<p>最新文章</p>
<ul>
  {% for post in site.posts %}
    <li>{{ post.date | date_to_string }} <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

New lists.

<ul>
  {% for post in site.posts %}
    <a  href='{{ post.url }}' class="list-group-item pjaxlink clearfix"> {{post.title}} </a>
	<span class="badge" align="right">{{ post.date | date:"%Y年%m月%d日" }}</span>
  {% endfor %}
</ul>






