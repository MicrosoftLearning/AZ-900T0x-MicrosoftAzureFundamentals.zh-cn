---
title: 在线托管说明
permalink: index.html
layout: home
---

# 内容目录

指向各个演练的超链接。讲师可以选择将演练用作演示或学生实验室。 

## 演练

{% assign wts = site.pages | where_exp:"page", "page.url contains '/Instructions/Walkthroughs'" %}
| 模块 | 演练 |
| --- | --- | 
{% for activity in wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

