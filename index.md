<div class="Box-sc-g0xbh4-0 eoaCFS js-snippet-clipboard-copy-unpositioned undefined" data-hpc="true"><article class="markdown-body entry-content container-lg" itemprop="text"><div dir="rtl"><markdown-accessiblity-table data-catalyst=""><table>
  <thead>
  <tr>
  <th>title</th>
  <th>permalink</th>
  <th>layout</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="rtl">تمارين التنقيب عن المعرفة في Azure</div></td>
  <td><div dir="rtl">index.html</div></td>
  <td><div dir="rtl">home</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<div class="markdown-heading" dir="rtl"><h1 tabindex="-1" class="heading-element" dir="rtl">تمارين التنقيب عن المعرفة في Azure</h1><a id="user-content-تمارين-التنقيب-عن-المعرفة-في-azure" class="anchor" aria-label="Permalink: تمارين التنقيب عن المعرفة في Azure" href="#تمارين-التنقيب-عن-المعرفة-في-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="rtl">تم تصميم التدريبات التالية لدعم الوحدات النمطية على Microsoft Learn.</p>
<p dir="rtl">{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Exercises'" %} {% for activity in labs  %} {% if activity.url contains 'ai-foundry' %} {% continue %} {% endif %}</p>
<ul dir="rtl">
<li>[{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }}) {% endfor %}</li>
</ul>
</article></div>
