<div class="Box-sc-g0xbh4-0 eoaCFS js-snippet-clipboard-copy-unpositioned undefined" data-hpc="true"><article class="markdown-body entry-content container-lg" itemprop="text"><div dir="rtl"><markdown-accessiblity-table data-catalyst=""><table>
  <thead>
  <tr>
  <th>lab</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="rtl"><table>
  <thead>
  <tr>
  <th>title</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="rtl">تنفيذ التحسينات على نتائج البحث</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<div class="markdown-heading" dir="rtl"><h1 tabindex="-1" class="heading-element" dir="rtl">تنفيذ التحسينات على نتائج البحث</h1><a id="user-content-تنفيذ-التحسينات-على-نتائج-البحث" class="anchor" aria-label="Permalink: تنفيذ التحسينات على نتائج البحث" href="#تنفيذ-التحسينات-على-نتائج-البحث"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="rtl">لديك خدمة بحث موجودة يستخدمها تطبيق حجز العطلات. رأيت أن أهمية نتائج البحث تؤثر على عدد الحجوزات التي تحصل عليها. أضفت مؤخراً فنادق في البرتغال لذلك ترغب في تقديم اللغة البرتغالية كلغة مدعومة.</p>
<p dir="rtl">في هذا التمرين، ستضيف ملف تعريف تسجيل النقاط لتحسين صلة نتائج البحث. ثم ستستخدم خدمات الذكاء الاصطناعي في Azure لإضافة أوصاف برتغالية لجميع فنادقك.</p>
<blockquote>
<p dir="rtl"><strong>ملاحظة</strong>: لإكمال هذا التمرين، ستحتاج إلى اشتراك Microsoft Azure. إذا لم يكن لديك اشتراك بالفعل، يمكنك التسجيل للحصول على الإصدار التجريبي على <a href="https://azure.com/free?azure-portal=true" rel="nofollow">https://azure.com/free</a> .</p>
</blockquote>
<div class="markdown-heading" dir="rtl"><h2 tabindex="-1" class="heading-element" dir="rtl">إنشاء موارد Azure</h2><a id="user-content-إنشاء-موارد-azure" class="anchor" aria-label="Permalink: إنشاء موارد Azure" href="#إنشاء-موارد-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="rtl">ستنشئ خدمة بحث الذكاء الاصطناعي في Azure واستيراد عينة من بيانات الفندق.</p>
<ol dir="rtl">
<li>قم بتسجيل الدخول إلى <a href="https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true" rel="nofollow">بوابة Azure</a>.</li>
<li>حدد <strong>+ Create a resource</strong>.</li>
<li>فتش عن <strong>البحث</strong>، ثم حدد <strong>بحث الذكاء الاصطناعي في Azure</strong>.</li>
<li>حدد <strong>إنشاء</strong>.</li>
<li>حدد <strong>إنشاء جديد</strong> ضمن مجموعة الموارد، ويمكنك تسميته <strong>Learn-advanced-search</strong>.</li>
<li>في <strong>اسم الخدمة</strong>، أدخل <strong>advanced-search-service-12345</strong>. يجب أن يكون الاسم فريداً عالمياً، لذا أضف أرقاماً عشوائية إلى نهاية الاسم.</li>
<li>حدد منطقة مدعومة بالقرب منك.</li>
<li>استخدم القيم الافتراضية <strong>لطبقة التسعير</strong>.</li>
<li>حدد "<strong>Review + create</strong>".</li>
<li>حدد <strong>إنشاء</strong>.</li>
<li>انتظر حتى يتم توزيع الموارد، ثم حدد <strong>Go to resource</strong>.</li>
</ol>
<div class="markdown-heading" dir="rtl"><h3 tabindex="-1" class="heading-element" dir="rtl">استيراد بيانات نموذجية إلى خدمة البحث</h3><a id="user-content-استيراد-بيانات-نموذجية-إلى-خدمة-البحث" class="anchor" aria-label="Permalink: استيراد بيانات نموذجية إلى خدمة البحث" href="#استيراد-بيانات-نموذجية-إلى-خدمة-البحث"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="rtl">استيراد بيانات العينة.</p>
<ol dir="rtl">
<li>
<p dir="rtl">ثم، في جزء <strong>Overview</strong> حدد <strong>Import data</strong>.</p>
<p dir="rtl"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/import-data-new.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/import-data-new.png" alt="لقطة شاشة تعرض قائمة استيراد بيانات." style="max-width: 100%;"></a></p>
</li>
<li>
<p dir="rtl">في جزء <strong>استيراد البيانات</strong>، داخل <strong>مصدر البيانات</strong>، حدد <strong>العينات</strong>.</p>
</li>
<li>
<p dir="rtl">حدد <strong>hotels-sample</strong>.</p>
</li>
<li>
<p dir="rtl">في علامة التبويب <strong>إضافة مهارات معرفية (اختياري)</strong>، عليك توسيع <strong>إرفاق خدمات الذكاء الاصطناعي</strong>، ثم حدد <strong>إنشاء مورد خدمات الذكاء الاصطناعي الجديد</strong>.</p>
<p dir="rtl"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/add-cognitive-services-new.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/add-cognitive-services-new.png" alt="لقطة شاشة تعرض تحديد خدمات الذكاء الاصطناعي في Azure وإضافتها." style="max-width: 100%;"></a></p>
</li>
</ol>
<div class="markdown-heading" dir="rtl"><h3 tabindex="-1" class="heading-element" dir="rtl">إنشاء خدمة الذكاء الاصطناعي في Azure لدعم الترجمات</h3><a id="user-content-إنشاء-خدمة-الذكاء-الاصطناعي-في-azure-لدعم-الترجمات" class="anchor" aria-label="Permalink: إنشاء خدمة الذكاء الاصطناعي في Azure لدعم الترجمات" href="#إنشاء-خدمة-الذكاء-الاصطناعي-في-azure-لدعم-الترجمات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>في علامة تبويب جديدة، سجل الدخول إلى مدخل Azure.</li>
<li>في <strong>مجموعة الموارد</strong>، حدد <strong>learn-advanced-search</strong>.</li>
<li>في <strong>المنطقة</strong>، حدد المنطقة نفسها التي اخترتها لخدمة البحث.</li>
<li>في <strong>الاسم</strong>، أدخل <strong>learn-cognitive-translator-12345</strong> أو أي اسم تفضله. يجب أن يكون الاسم فريداً عالمياً، لذا أضف أرقاماً عشوائية إلى نهاية الاسم.</li>
<li>في <strong>طبقة التسعير</strong>، حدد <strong>معيار S0</strong>.</li>
<li>حدد <strong>. من خلال تحديد هذا المربع، أقر بأنني قرأت وفهمت جميع الشروط أدناه</strong>.</li>
<li>حدد "<strong>Review + create</strong>".</li>
<li>حدد <strong>إنشاء</strong>.</li>
<li>عند إنشاء الموارد، أغلق علامة التبويب.</li>
</ol>
<div class="markdown-heading" dir="rtl"><h3 tabindex="-1" class="heading-element" dir="rtl">إضافة إثراء الترجمة</h3><a id="user-content-إضافة-إثراء-الترجمة" class="anchor" aria-label="Permalink: إضافة إثراء الترجمة" href="#إضافة-إثراء-الترجمة"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>في علامة التبويب <strong>إضافة المهارات المعرفية (اختياري)،</strong> حدد تحديث.</li>
<li>حدد الخدمة الجديدة، <strong>learn-cognitive-translator-12345</strong>.</li>
<li>قم بتوسيع القسم <strong>Add enrichments</strong>.
<a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/add-translation-enrichment-new.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/add-translation-enrichment-new.png" alt="لقطة شاشة تبين إضافة الترجمة البرتغالية." style="max-width: 100%;"></a></li>
<li>حدد <strong>ترجمة النص</strong>، وغير <strong>اللغة الهدف</strong> إلى <strong>البرتغالية</strong>، ثم غير <strong>اسم الحقل</strong> إلى <strong>Description_pt</strong>.</li>
<li>حدد <strong>Next: Customize target index</strong>.</li>
</ol>
<div class="markdown-heading" dir="rtl"><h3 tabindex="-1" class="heading-element" dir="rtl">تغيير الحقل لتخزين النص المترجم</h3><a id="user-content-تغيير-الحقل-لتخزين-النص-المترجم" class="anchor" aria-label="Permalink: تغيير الحقل لتخزين النص المترجم" href="#تغيير-الحقل-لتخزين-النص-المترجم"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="rtl">في علامة التبويب <strong>تخصيص الفهرس الهدف</strong>، عليك التمرير إلى أسفل قائمة الحقول وتغيير <strong>المحلل</strong> إلى <strong>البرتغالية (البرتغال) - Microsoft</strong> للحقل <strong>Description_pt</strong>.</p>
</li>
<li>
<p dir="rtl">حدد <strong>التالي: إنشاء مفهرس</strong>.</p>
</li>
<li>
<p dir="rtl">حدد <strong>إرسال</strong>.</p>
<p dir="rtl">يجري إنشاء الفهرس، وسيعمل المفهرس، وسيجري استيراد 50 مستنداً تحتوي على نموذج بيانات الفندق.</p>
</li>
<li>
<p dir="rtl">في جزء <strong>نظرة عامة</strong>، حدد <strong>الفهارس</strong>، ثم حدد <strong>hotels-sample-index</strong>.</p>
</li>
<li>
<p dir="rtl">حدد <strong>بحث</strong> لمشاهدة JSON لكافة المستندات في الفهرس.</p>
</li>
<li>
<p dir="rtl">ابحث <strong>عن Description_pt</strong> (يمكنك استخدام <strong>CTRL + F</strong> لهذا) في النتائج ولاحظ أنها ليست ترجمة برتغالية للوصف باللغة الإنجليزية، ولكنها تبدو كما يلي بدلاً من ذلك:</p>
<div class="highlight highlight-source-json notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-ent">"Description_pt"</span>: <span class="pl-s"><span class="pl-pds">"</span>45<span class="pl-pds">"</span></span>,</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="&quot;Description_pt&quot;: &quot;45&quot;," tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
</ol>
<p dir="rtl">يفترض مدخل Microsoft Azure أن الحقل الأول في المستند يحتاج إلى الترجمة. لذلك فهي تستخدم حالياً مهارة الترجمة لترجمة <code>HotelId</code>.</p>
<div class="markdown-heading" dir="rtl"><h3 tabindex="-1" class="heading-element" dir="rtl">تحديث مجموعة المهارات لترجمة الحقل الصحيح في المستند</h3><a id="user-content-تحديث-مجموعة-المهارات-لترجمة-الحقل-الصحيح-في-المستند" class="anchor" aria-label="Permalink: تحديث مجموعة المهارات لترجمة الحقل الصحيح في المستند" href="#تحديث-مجموعة-المهارات-لترجمة-الحقل-الصحيح-في-المستند"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="rtl">في أعلى الصفحة، اختر خدمة البحث، ارتباط <strong>advanced-search-service-12345 | الفهارس</strong>.</p>
</li>
<li>
<p dir="rtl">حدد <strong>مجموعات المهارات</strong> ضمن إدارة البحث في الجزء الأيمن، ثم حدد <strong>hotels-sample-skillset</strong>.</p>
</li>
<li>
<p dir="rtl">عدّل مستند JSON، غيّر السطر 9 إلى:</p>
<div class="highlight highlight-source-json notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-ent">"context"</span>: <span class="pl-s"><span class="pl-pds">"</span>/document/Description<span class="pl-pds">"</span></span>,</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="&quot;context&quot;: &quot;/document/Description&quot;," tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="rtl">غيّر اللغة الافتراضية من اللغة إلى اللغة الإنجليزية على السطر 11:</p>
<div class="highlight highlight-source-json notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-ent">"defaultFromLanguageCode"</span>: <span class="pl-s"><span class="pl-pds">"</span>en<span class="pl-pds">"</span></span>,</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="&quot;defaultFromLanguageCode&quot;: &quot;en&quot;," tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="rtl">غيّر حقل المصدر على السطر 15 إلى:</p>
<div class="highlight highlight-source-json notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-ent">"source"</span>: <span class="pl-s"><span class="pl-pds">"</span>/document/Description<span class="pl-pds">"</span></span>,</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="&quot;source&quot;: &quot;/document/Description&quot;," tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="rtl">حدد <strong>حفظ</strong>.</p>
</li>
<li>
<p dir="rtl">في أعلى الصفحة، اختر خدمة البحث، ارتباط <strong>advanced-search-service-12345 | مجموعات المهارات</strong>.</p>
</li>
<li>
<p dir="rtl">في جزء <strong>نظرة عامة</strong>، حدد <strong>المفهرسات</strong>، ثم حدد <strong>hotels-sample-indexer</strong>.</p>
</li>
<li>
<p dir="rtl">حدد <strong>تحرير JSON</strong>.</p>
</li>
<li>
<p dir="rtl">غيّر اسم حقل المصدر على السطر 20 إلى:</p>
<div class="highlight highlight-source-json notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-ent">"sourceFieldName"</span>: <span class="pl-s"><span class="pl-pds">"</span>/document/Description/Description_pt<span class="pl-pds">"</span></span>,</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="&quot;sourceFieldName&quot;: &quot;/document/Description/Description_pt&quot;," tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="rtl">حدد <strong>حفظ</strong>.</p>
</li>
<li>
<p dir="rtl">حدد <strong>إعادة تعيين</strong>، ثم حدد <strong>نعم</strong>.</p>
</li>
<li>
<p dir="rtl">حدد <strong>تشغيل</strong>، ثم حدد <strong>نعم</strong>.</p>
</li>
</ol>
<div class="markdown-heading" dir="rtl"><h3 tabindex="-1" class="heading-element" dir="rtl">اختبار الفهرس المحدث</h3><a id="user-content-اختبار-الفهرس-المحدث" class="anchor" aria-label="Permalink: اختبار الفهرس المحدث" href="#اختبار-الفهرس-المحدث"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="rtl">في أعلى الصفحة، اختر خدمة البحث، ارتباط <strong>advanced-search-service-12345 | المفهرسات</strong>.</p>
</li>
<li>
<p dir="rtl">في جزء <strong>نظرة عامة</strong>، حدد <strong>الفهارس</strong>، ثم حدد <strong>hotels-sample-index</strong>.</p>
</li>
<li>
<p dir="rtl">حدد <strong>بحث</strong> لمشاهدة JSON لكافة المستندات في الفهرس.</p>
</li>
<li>
<p dir="rtl">ابحث عن <strong>Description_pt</strong> في النتائج ولاحظ أن هناك الآن وصفاً برتغالياً.</p>
<div class="highlight highlight-source-json notranslate position-relative overflow-auto" dir="rtl"><pre><span class="pl-ent">"Description_pt"</span>: <span class="pl-s"><span class="pl-pds">"</span>O maior resort durante todo o ano da área oferecendo mais de tudo para suas férias – pelo melhor valor!  O que você pode desfrutar enquanto estiver no resort, além das praias de areia de 1,5 km do lago? Confira nossas atividades com certeza para excitar tanto os jovens quanto os jovens hóspedes do coração. Temos tudo, incluindo ser chamado de <span class="pl-cce">\"</span>Propriedade do Ano<span class="pl-cce">\"</span> e um <span class="pl-cce">\"</span>Top Ten Resort<span class="pl-cce">\"</span> pelas principais publicações.<span class="pl-pds">"</span></span>,</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="&quot;Description_pt&quot;: &quot;O maior resort durante todo o ano da área oferecendo mais de tudo para suas férias – pelo melhor valor!  O que você pode desfrutar enquanto estiver no resort, além das praias de areia de 1,5 km do lago? Confira nossas atividades com certeza para excitar tanto os jovens quanto os jovens hóspedes do coração. Temos tudo, incluindo ser chamado de \&quot;Propriedade do Ano\&quot; e um \&quot;Top Ten Resort\&quot; pelas principais publicações.&quot;," tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
<li>
<p dir="rtl">الآن عليك البحث عن الفنادق التي لديها إطلالات على البحيرات. سنبدأ باستخدام بحث بسيط يرجع فقط <code>HotelName</code>و<code>Description</code> و<code>Category</code> و<code>Tags</code>. في <strong>سلسلة الاستعلام</strong>، أدخل هذا البحث:</p>
<p dir="rtl"><code>lake + view&amp;$select=HotelName,Description,Category,Tags&amp;$count=true</code></p>
<p dir="rtl">ابحث عن النتائج وحاول العثور على الحقول التي تطابق مصطلحي البحث <code>lake</code> و<code>view</code>. لاحظ هذا الفندق وموقعه:</p>
<div class="highlight highlight-source-json notranslate position-relative overflow-auto" dir="rtl"><pre>{
  <span class="pl-ent">"@search.score"</span>: <span class="pl-c1">0.9433406</span>,
  <span class="pl-ent">"HotelName"</span>: <span class="pl-s"><span class="pl-pds">"</span>Lady Of The Lake B &amp; B<span class="pl-pds">"</span></span>,
  <span class="pl-ent">"Description"</span>: <span class="pl-s"><span class="pl-pds">"</span>Nature is Home on the beach.  Save up to 30 percent. Valid Now through the end of the year. Restrictions and blackout may apply.<span class="pl-pds">"</span></span>,
  <span class="pl-ent">"Category"</span>: <span class="pl-s"><span class="pl-pds">"</span>Luxury<span class="pl-pds">"</span></span>,
  <span class="pl-ent">"Tags"</span>: [
    <span class="pl-s"><span class="pl-pds">"</span>laundry service<span class="pl-pds">"</span></span>,
    <span class="pl-s"><span class="pl-pds">"</span>concierge<span class="pl-pds">"</span></span>,
    <span class="pl-s"><span class="pl-pds">"</span>view<span class="pl-pds">"</span></span>
  ]
},</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="{
  &quot;@search.score&quot;: 0.9433406,
  &quot;HotelName&quot;: &quot;Lady Of The Lake B &amp; B&quot;,
  &quot;Description&quot;: &quot;Nature is Home on the beach.  Save up to 30 percent. Valid Now through the end of the year. Restrictions and blackout may apply.&quot;,
  &quot;Category&quot;: &quot;Luxury&quot;,
  &quot;Tags&quot;: [
    &quot;laundry service&quot;,
    &quot;concierge&quot;,
    &quot;view&quot;
  ]
}," tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</li>
</ol>
<p dir="rtl">تطابق هذا الفندق مع بحيرة المصطلحات في حقل <code>HotelName</code> وفي المنظر في حقل <code>Tags</code>. ترغب في تعزيز تطابق الشروط في حقل <code>Description</code> على اسم الفندق. من الناحية المثالية، يجب أن يكون هذا الفندق الأخير في النتائج.</p>
<div class="markdown-heading" dir="rtl"><h2 tabindex="-1" class="heading-element" dir="rtl">إضافة ملف تعريف تسجيل النقاط لتحسين نتائج البحث</h2><a id="user-content-إضافة-ملف-تعريف-تسجيل-النقاط-لتحسين-نتائج-البحث" class="anchor" aria-label="Permalink: إضافة ملف تعريف تسجيل النقاط لتحسين نتائج البحث" href="#إضافة-ملف-تعريف-تسجيل-النقاط-لتحسين-نتائج-البحث"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="rtl">حدد علامة التبويب <strong>ملفات تعريف تسجيل النقاط</strong>.</p>
</li>
<li>
<p dir="rtl">حدد <strong>+ إضافة ملف تعريف تسجيل النقاط</strong>.</p>
</li>
<li>
<p dir="rtl">في <strong>اسم ملف التعريف</strong>، أدخل <strong>boost-description-categories</strong>.</p>
</li>
<li>
<p dir="rtl">أضف الحقول والأوزان التالية ضمن <strong>الأوزان</strong>:</p>
<p dir="rtl"><a target="_blank" rel="noopener noreferrer" href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/add-weights-new.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/add-weights-new.png" alt="لقطة شاشة للأوزان التي تجري إضافتها إلى ملف تعريف تسجيل النقاط." style="max-width: 100%;"></a></p>
</li>
<li>
<p dir="rtl">في <strong>اسم الحقل</strong>، حدد <strong>الوصف</strong>.</p>
</li>
<li>
<p dir="rtl">بالنسبة <strong>للوزن</strong>، أدخل <strong>5</strong>.</p>
</li>
<li>
<p dir="rtl">في <strong>اسم الحقل</strong>، حدد <strong>الفئة</strong>.</p>
</li>
<li>
<p dir="rtl">بالنسبة <strong>للوزن</strong>، أدخل <strong>3</strong>.</p>
</li>
<li>
<p dir="rtl">في <strong>اسم الحقل</strong>، حدد <strong>علامات</strong>.</p>
</li>
<li>
<p dir="rtl">بالنسبة <strong>للوزن</strong>، أدخل <strong>2</strong>.</p>
</li>
<li>
<p dir="rtl">حدد <strong>حفظ</strong>.</p>
</li>
<li>
<p dir="rtl">حدد ⁧<strong>⁩حفظ⁧</strong>⁩ في الأعلى.</p>
</li>
</ol>
<div class="markdown-heading" dir="rtl"><h3 tabindex="-1" class="heading-element" dir="rtl">اختبار الفهرس المحدث</h3><a id="user-content-اختبار-الفهرس-المحدث-1" class="anchor" aria-label="Permalink: اختبار الفهرس المحدث" href="#اختبار-الفهرس-المحدث-1"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
<li>
<p dir="rtl">ارجع إلى علامة تبويب <strong>مستكشف البحث</strong> في صفحة <strong>hotels-sample-index</strong>.</p>
</li>
<li>
<p dir="rtl">في <strong>سلسلة الاستعلام</strong>، أدخل البحث نفسه كما كان من قبل:</p>
<p dir="rtl"><code>lake + view&amp;$select=HotelName,Description,Category,Tags&amp;$count=true</code></p>
<p dir="rtl">تحقق من نتائج البحث.</p>
<div class="highlight highlight-source-json notranslate position-relative overflow-auto" dir="rtl"><pre>{
  <span class="pl-ent">"@search.score"</span>: <span class="pl-c1">3.5707965</span>,
  <span class="pl-ent">"HotelName"</span>: <span class="pl-s"><span class="pl-pds">"</span>Lady Of The Lake B &amp; B<span class="pl-pds">"</span></span>,
  <span class="pl-ent">"Description"</span>: <span class="pl-s"><span class="pl-pds">"</span>Nature is Home on the beach.  Save up to 30 percent. Valid Now through the end of the year. Restrictions and blackout may apply.<span class="pl-pds">"</span></span>,
  <span class="pl-ent">"Category"</span>: <span class="pl-s"><span class="pl-pds">"</span>Luxury<span class="pl-pds">"</span></span>,
  <span class="pl-ent">"Tags"</span>: [
    <span class="pl-s"><span class="pl-pds">"</span>laundry service<span class="pl-pds">"</span></span>,
    <span class="pl-s"><span class="pl-pds">"</span>concierge<span class="pl-pds">"</span></span>,
    <span class="pl-s"><span class="pl-pds">"</span>view<span class="pl-pds">"</span></span>
  ]
}</pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="{
  &quot;@search.score&quot;: 3.5707965,
  &quot;HotelName&quot;: &quot;Lady Of The Lake B &amp; B&quot;,
  &quot;Description&quot;: &quot;Nature is Home on the beach.  Save up to 30 percent. Valid Now through the end of the year. Restrictions and blackout may apply.&quot;,
  &quot;Category&quot;: &quot;Luxury&quot;,
  &quot;Tags&quot;: [
    &quot;laundry service&quot;,
    &quot;concierge&quot;,
    &quot;view&quot;
  ]
}" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="rtl">زادت درجة البحث من <strong>0.9433406</strong> إلى <strong>3.5707965</strong>. مع ذلك، فإن جميع الفنادق الأخرى لديها درجات محسوبة أعلى. هذا الفندق هو الآن الآخر في النتائج.</p>
</li>
</ol>
<div class="markdown-heading" dir="rtl"><h2 tabindex="-1" class="heading-element" dir="rtl">التنظيف</h2><a id="user-content-التنظيف" class="anchor" aria-label="Permalink: التنظيف" href="#التنظيف"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="rtl">الآن بعد أن أكملت التمرين، احذف جميع الموارد التي لم تعد بحاجة إليها.</p>
<ol dir="rtl">
<li>في مدخل Azure، حدد <strong>مجموعات الموارد</strong>:</li>
<li>حدد مجموعة الموارد التي لا تحتاج إليها بعد الآن، ثم حدد <strong>حذف مجموعات الموارد</strong>.</li>
</ol>
</article></div>
