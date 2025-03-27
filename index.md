---
title: تمارين التنقيب عن المعرفة في Azure
permalink: index.html
layout: home
---

<link rel="stylesheet" href="/assets/styles.css">
# تمارين التنقيب عن المعرفة في Azure

تم تصميم التدريبات التالية لدعم الوحدات النمطية على Microsoft Learn.

 {% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Exercises'" %} {% for activity in labs  %} {% if activity.url contains 'ai-foundry' %} {% continue %} {% endif %}
- [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }}) {% endfor %}
