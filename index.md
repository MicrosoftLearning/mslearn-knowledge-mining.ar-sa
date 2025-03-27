---
title: تمارين التنقيب عن المعرفة في Azure
permalink: index.html
layout: home
---

<style>
  body {
    direction: rtl;
    text-align: right;
    font-family: Arial, sans-serif; /* Ensure Arabic fonts are supported */
  }

  h1, h2, h3, h4, h5, h6 {
    text-align: right;
  }

  p {
    text-align: right;
  }
</style>
# تمارين التنقيب عن المعرفة في Azure

تم تصميم التدريبات التالية لدعم الوحدات النمطية على Microsoft Learn.

 {% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Exercises'" %} {% for activity in labs  %} {% if activity.url contains 'ai-foundry' %} {% continue %} {% endif %}
- [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }}) {% endfor %}
