--- 
title:      项目
layout:     default
---

<span class="article-title">项目</span>

<p />
<div class="article-content">
	{% for project in site.projects %}
		<span class="article-content-title"><a href="{{ project.url }}" target="_blank">{{ project.name }}</a></span>
		<br /><span>项目主页：<a href="{{ project.url }}" target="_blank">{{ project.url }}</a></span>
		<br /><span>项目介绍：<a href="{{ project.file }}">{{ project.file }}</a></span>
		{% if project.demo %}
		<br /><span>项目演示：<a href="{{ project.demo }}" target="_blank">{{ project.demo }}</a></span>
		{% endif %}
		<br /><span>一句话描述：{{ project.description }}</span>
		<br />
		<br />
	{% endfor %}
</div>