<div class="Box-sc-g0xbh4-0 eoaCFS js-snippet-clipboard-copy-unpositioned undefined" data-hpc="true"><div dir="rtl"><article class="markdown-body entry-content container-lg" itemprop="text"><markdown-accessiblity-table data-catalyst=""><table>
  <thead>
  <tr>
  <th>lab</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="auto"><table>
  <thead>
  <tr>
  <th>title</th>
  <th>module</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="auto">إنشاء حل Azure AI Search</div></td>
  <td><div dir="auto">Module 12 - Creating a Knowledge Mining Solution</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>

<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto">إنشاء حل Azure AI Search</h1><a id="user-content-إنشاء-حل-azure-ai-search" class="anchor" aria-label="Permalink: إنشاء حل Azure AI Search" href="#إنشاء-حل-azure-ai-search"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">تعتمد جميع المنظمات على المعلومات لاتخاذ القرارات والإجابة على الأسئلة والعمل بكفاءة. والمشكلة بالنسبة لمعظم المنظمات ليست نقص المعلومات، بل في التحدي المتمثل في العثور على المعلومات واستخراجها من مجموعة ضخمة من الوثائق وقواعد البيانات وغيرها من المصادر التي تخزن فيها المعلومات.</p>
<p dir="auto">على سبيل المثال، افترض أن <i>Margie's Travel</i> هي وكالة سفر متخصصة في تنظيم الرحلات إلى المدن حول العالم. بمرور الوقت، جمعت الشركة كمية كبيرة من المعلومات في وثائق مثل الكتيبات، فضلا عن تقييمات للفنادق مقدمة من قبل العملاء. هذه البيانات هي مصدر قيم لنتائج التحليلات لوكلاء السفر والعملاء أثناء تخطيطهم للرحلات، ولكن الحجم الهائل للبيانات يمكن أن يجعل من الصعب العثور على معلومات ذات صلة للإجابة على سؤال معين من العملاء.</p>
<p dir="auto">لمواجهة هذا التحدي، يمكن لـ Margie's Travel استخدام Azure AI Search لتنفيذ حل تتم فيه فهرسة المستندات وإثراءها باستخدام مهارات الذكاء الاصطناعي لتسهيل البحث عنها.</p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إنشاء موارد Azure</h2><a id="user-content-إنشاء-موارد-azure" class="anchor" aria-label="Permalink: إنشاء موارد Azure" href="#إنشاء-موارد-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الحل الذي ستقوم بإنشائه لـ Margie's Travel يتطلب الموارد التالية في اشتراك Azure الخاص بك:</p>
<ul dir="rtl">
    <li>مورد <b>بحث الذكاء الاصطناعي في Azure</b> الذي سيدير ​​الفهرسة والاستعلام.</li>
    <li>مورد <b>خدمات الذكاء الاصطناعي في Azure</b>، والذي يوفر خدمات الذكاء الاصطناعي للمهارات التي يمكن أن يستخدمها حل البحث الخاص بك لإثراء البيانات في مصدر البيانات باستخدام نتائج التحليلات التي تم إنشاؤها بالذكاء الاصطناعي.</li>
    <li><b>حساب التخزين</b> مع حاوية كائن ثنائي كبير الحجم يتم فيها تخزين المستندات التي سيتم البحث عنها.</li>
</ul>
<blockquote>
<p dir="auto"><b>مهم</b>: يجب أن تكون موارد خدمات Azure AI Search والذكاء الاصطناعي في Azure في الموقع نفسه!</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">إنشاء مورد كلام الذكاء الاصطناعي في Azure</h3><a id="user-content-إنشاء-مورد-كلام-الذكاء-الاصطناعي-في-azure" class="anchor" aria-label="Permalink: إنشاء مورد كلام الذكاء الاصطناعي في Azure" href="#إنشاء-مورد-كلام-الذكاء-الاصطناعي-في-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
    <li>في مستعرض ويب، افتح مدخل Azure في <code>https://portal.azure.com</code>، ثم سجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure لديك.</li>
    <li>
        <p dir="auto">اضغط على زر <b>＋Create a resource</b> وابحث عن <i>بحث عن</i>، وأنشئ مورد <b>Azure AI Search</b> باستخدام الإعدادات التالية:</p>
        <ul dir="rtl">
            <li><b>Subscription</b>: <i>اشتراكك في Azure</i></li>
            <li><b>مجموعة الموارد</b>: <i>أنشئ مجموعة موارد (إذا كنت تستخدم اشتراكاً مقيداً، فقد لا يكون لديك إذن لإنشاء مجموعة موارد جديدة - استخدم المجموعة المتوفرة)</i></li>
            <li><b>اسم الخدمة</b>: <i>أدخل اسماً فريداً</i></li>
            <li><b>الموقع</b>: <i>تحديد موقع- لاحظ أنه يجب أن تكون موارد خدمات Azure AI Search والذكاء الاصطناعي في Azure في الموقع نفسه</i></li>
            <li><b>مستوى التسعير</b>: أساسي</li>
        </ul>
    </li>
    <li>انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.</li>
    <li>راجع صفحة<b>نظرة عامة</b> على الجزء لمورد Azure AI Search في مدخل Microsoft Azure. هنا، يمكنك استخدام واجهة مرئية لإنشاء المكونات المختلفة لحل البحث واختبارها وإدارتها ومراقبتها؛ بما في ذلك مصادر البيانات والفهارس والمفهرسات ومجموعات المهارات.</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">إنشاء مورد خدمات الذكاء الاصطناعي في Azure</h3><a id="user-content-إنشاء-مورد-خدمات-الذكاء-الاصطناعي-في-azure" class="anchor" aria-label="Permalink: إنشاء مورد خدمات الذكاء الاصطناعي في Azure" href="#إنشاء-مورد-خدمات-الذكاء-الاصطناعي-في-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إذا لم يكن لديك بالفعل مورد في اشتراكك، فسيتعين عليك توفير مورد <b>خدمات الذكاء الاصطناعي في Azure</b>. سيستخدم حل البحث الخاص بك هذا لإثراء البيانات الموجودة في مخزن البيانات بالرؤى التي تم إنشاؤها بواسطة الذكاء الاصطناعي.</p>
<ol dir="rtl">
    <li>
        <p dir="auto">ارجع إلى الصفحة الرئيسية لبوابة Azure، ثم حدد الزر <b>＋Create a resource</b>، وابحث عن <i>خدمات الذكاء الاصطناعي في Azure</i>، وأنشئ مورد <b>حساب خدمة متعدد لخدمات الذكاء الاصطناعي في Azure</b> من خلال الإعدادات التالية:</p>
        <ul dir="rtl">
            <li><b>Subscription</b>: <i>اشتراكك في Azure</i></li>
            <li><b>مجموعة الموارد</b>: <i>مجموعة الموارد نفسها مثل مورد بحث الذكاء الاصطناعي في Azure الخاص بك</i></li>
            <li><b>المنطقة</b>: <i>الموقع نفسه كمورد بحث الذكاء الاصطناعي في Azure الخاص بك</i></li>
            <li><b>الاسم</b>: <i>أدخل اسماً فريداً</i></li>
            <li><b>مستوى التسعير</b>: قياسي S0</li>
        </ul>
    </li>
    <li>حدد مربعات الاختيار المطلوبة ثم أنشئ المورد.</li>
    <li>انتظر حتى يكتمل النشر، ثم اعرض تفاصيل النشر.</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">إنشاء حساب تخزين</h3><a id="user-content-إنشاء-حساب-تخزين" class="anchor" aria-label="Permalink: إنشاء حساب تخزين" href="#إنشاء-حساب-تخزين"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
    <li>
        <p dir="auto">ارجع إلى الصفحة الرئيسية لمدخل Microsoft Azure، ثم حدد الزر <b>＋Create a resource</b>، وابحث عن <i>storage account</i>، وأنشئ مورد <b>Storage account</b> من خلال الإعدادات التالية:</p>
        <ul dir="rtl">
            <li><b>Subscription</b>: <i>اشتراكك في Azure</i></li>
            <li><b>مجموعة الموارد</b>: *<i>مجموعة الموارد نفسها مثل موارد خدمات Azure AI Search والذكاء الاصطناعي في Azure</i></li>
            <li><b>اسم حساب التخزين</b>: <i>أدخل اسماً فريداً</i></li>
            <li><b>المنطقة</b>: <i>اختر أي منطقة متوفرة</i></li>
            <li><b>الأداء:</b> قياسي</li>
            <li><b>التكرار</b>: التخزين المتكرر محلياً (LRS)</li>
            <li>في علامة التبويب<b>خيارات متقدمة</b>، حدد المربع الموجود بجانب <i>السماح بتمكين الوصول المجهول على حاويات فردية</i></li>
        </ul>
    </li>
    <li>انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.</li>
    <li>في <b>صفحة نظرة عامة</b>، لاحظ <b>معرف الاشتراك</b> - يحدد هذا الاشتراك الذي يتم توفير حساب التخزين فيه.</li>
    <li>في صفحة <b>الوصول إلى المفاتيح</b>، لاحظ أنه تم إنشاء مفتاحين لحساب التخزين الخاص بك. ثم حدد <b>إظهار المفاتيح</b> لعرض المفاتيح.</li>
    <blockquote><b>تلميح</b>: حافظ على شفرة <b>حساب التخزين</b> مفتوحة - ستحتاج إلى معرف الاشتراك وأحد المفاتيح في الإجراء التالي.</blockquote>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية</h2><a id="user-content-الاستعداد-لتطوير-تطبيق-في-تعليمة-visual-studio-البرمجية" class="anchor" aria-label="Permalink: الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية" href="#الاستعداد-لتطوير-تطبيق-في-تعليمة-visual-studio-البرمجية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">ستطور تطبيق البحث لديك باستخدام Visual Studio Code. تم توفير ملفات التعليمات البرمجية لتطبيقك في GitHub repo.</p>
<blockquote>
<p dir="auto"><b>تلميح</b>: إذا نسخت بالفعل مستودع <b>mslearn-knowledge-mining</b>، فافتحه في Visual Studio code. وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة تطويرك.</p>
</blockquote>
<ol dir="rtl">
    <li>ابدأ تشغيل Visual Studio Code.</li>
    <li>افتح لوحة (SHIFT+CTRL+P) وشغّل <b>Git: استنسخ الأمر </b> لاستنساخ مستودع <code>https://github.com/MicrosoftLearning/mslearn-knowledge-mining</code> إلى مجلد محلي (لا يُهم أي مجلد).</li>
    <li>عند استنساخ المستودع، افتح المجلد في تعليمة Visual Studio البرمجية.</li>
    <li>انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.</li>
    <blockquote><b>ملاحظة</b>: إذا جرت مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد <b>ليس الآن</b>.</blockquote>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">تحميل المستندات إلى Azure Storage</h2><a id="user-content-تحميل-المستندات-إلى-azure-storage" class="anchor" aria-label="Permalink: تحميل المستندات إلى Azure Storage" href="#تحميل-المستندات-إلى-azure-storage"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن أصبح لديك الموارد المطلوبة، يمكنك تحميل بعض المستندات إلى حساب Azure Storage الخاص بك.</p>
<ol dir="rtl">
    <li>في Visual Studio Code، في جزء<b> Explorer</b>، قم بتوسيع مجلد<b>مجلد Labfiles\01-azure-search</b> وحدد <b>UploadDocs.cmd</b>.</li>
    <li>قم بتحرير ملف الدُفعات لاستبدال العناصر النائبة <b> YOUR_SUBSCRIPTION_ID </b>،<b>وYOUR_AZURE_STORAGE_ACCOUNT_NAME</b> و<b>YOUR_AZURE_STORAGE_KEY</b> بمعرف الاشتراك المناسب واسم حساب تخزين Azure وقيم مفتاح حساب تخزين Azure لحساب التخزين الذي قمت بإنشائه مسبقًا.</li>
    <li>احفظ التغييرات، ثم انقر بزر الماوس الأيمن فوق المجلد<b> 01-azure-search</b> وافتح محطة طرفية متكاملة.</li>
    <li>أدخل الأمر التالي لتسجيل الدخول إلى اشتراك Azure باستخدام Azure CLI.</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>az login</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="az login" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <p dir="auto">سيتم فتح علامة تبويب مستعرض ويب ومطالبتك بتسجيل الدخول إلى Azure. قم بذلك، ثم أغلق علامة تبويب المستعرض وارجع إلى Visual Studio Code.</p>
    <li>أدخل الأمر التالي لتشغيل ملف الدُفعات. سيؤدي ذلك إلى إنشاء حاوية كائن ثنائي كبير الحجم في حساب التخزين الخاص بك وتحميل المستندات في مجلد <b>البيانات</b> إليها.</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>.\UploadDocs.cmd</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value=".\UploadDocs.cmd" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">فهرسة المستندات</h2><a id="user-content-فهرسة-المستندات" class="anchor" aria-label="Permalink: فهرسة المستندات" href="#فهرسة-المستندات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن أصبح لديك المستندات في مكانها، يمكنك إنشاء حل بحث عن طريق فهرستها.</p>
<ol dir="rtl">
    <li>في مدخل Microsoft Azure، استعرض وصولاً إلى مورد بحث الذكاء الاصطناعي في Azure. ثم، في صفحة <b>النظرة العامة،</b> حدد <b>استيراد البيانات</b>.</li>
    <li>
        <p dir="auto">في صفحة <b>الاتصال ببياناتك</b>، في قائمة <b>مصدر البيانات</b>، حدد <b>Azure Blob Storage</b>. ثم أكمل تفاصيل مخزن البيانات بالقيم التالية:</p>
        <ul dir="rtl">
            <li><b>Data Source</b>: Azure Blob Storage</li>
            <li><b>اسم مصدر البيانات</b>: margies-data</li>
            <li><b>البيانات المراد استخراجها</b>: المحتوى وبيانات التعريف</li>
            <li><b>وضع التحليل</b>: افتراضي</li>
            <li><b>سلسلة الاتصال</b>: <i>حدد رابط<b> Choose an existing connection.</b> ثم حدد حساب التخزين الخاص بك، وأخيرًا حدد حاوية <b>margies</b> التي تم إنشاؤها بواسطة البرنامج النصي UploadDocs.cmd.</i></li>
            <li><b>مصادقة الهوية المُدارة</b>: لا شيء</li>
            <li><b>اسم الحاوية</b>: margies</li>
            <li><b>مجلد الكائنات الثنائية كبيرة الحجم</b>: <i>اترك هذا فارغاً</i></li>
            <li><b>الوصف</b>: كتيبات وتقييمات في موقع Margie's Travel على الويب.</li>
        </ul>
    </li>
    <li>تابع إلى الخطوة التالية <i>إضافة مهارات معرفية</i>.</li>
    <li>في قسم <b>إرفاق خدمات الذكاء الاصطناعي في Azure</b> حدد مورد خدمات الذكاء الاصطناعي في Azure.</li>
    <li>
        <p dir="auto">في القسم <b>إضافة إثراءات</b>:</p>
        <ul dir="rtl">
            <li>غيّر <b>اسم مجموعة المهارات</b> إلى <b>margies-skillset</b>.</li>
            <li>حدد الخيار <b>تمكين OCR ودمج كل النص في حقل merged_content</b>.</li>
            <li>تأكد من تعيين <b>حقل بيانات المصدر</b> إلى <b>merged_content</b>.</li>
            <li>اترك مستوى<b> تفاصيل الإثراء </b>كحقل <b>مصدر</b> الذي يتم تعيين محتويات المستند بالكامل التي تتم فهرستها؛ ولكن لاحظ أنه يمكنك تغيير ذلك لاستخراج المعلومات على مستويات أكثر دقة، مثل الصفحات أو الجمل.</li>
            <li>
                <p dir="auto">حدد الحقول الغنية التالية:</p>
                <markdown-accessiblity-table data-catalyst=""><table>
                    <thead>
                        <tr>
                            <th>المهارة المعرفية</th>
                            <th>المعلمة‬</th>
                            <th>اسم الحقل</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>استخراج أسماء المواقع</td>
                            <td></td>
                            <td>المواقع</td>
                        </tr>
                        <tr>
                            <td>استخراج العبارات الرئيسية</td>
                            <td></td>
                            <td>keyphrases</td>
                        </tr>
                        <tr>
                            <td>اكتشاف اللغة</td>
                            <td></td>
                            <td>اللغة</td>
                        </tr>
                        <tr>
                            <td>إنشاء علامات من الصور</td>
                            <td></td>
                            <td>imageTags</td>
                        </tr>
                        <tr>
                            <td>إنشاء تسميات توضيحية من الصور</td>
                            <td></td>
                            <td>imageCaption</td>
                        </tr>
                    </tbody>
                </table></markdown-accessiblity-table>
            </li>
        </ul>
    </li>
    <li>تحقق مرة أخرى من اختياراتك (قد يكون من الصعب تغييرها لاحقاً). ثم انتقل إلى الخطوة التالية (<i>تخصيص الفهرس الهدف</i>).</li>
    <li>غيّر <b>اسم الفهرس</b> إلى <b>margies-index</b>.</li>
    <li>تأكد من تعيين <b>المفتاح</b> على <b>metadata_storage_path</b> واترك <b>اسم المقترح فارغاً ووضع البحث </b><b>على الوضع الافتراضي</b>.</li>
    <li>
        <p dir="auto"> قم بإجراء التغييرات التالية على حقول الفهرس، مع ترك جميع الحقول الأخرى بإعداداتها الافتراضية (<b>مهم</b>: قد تحتاج إلى التمرير إلى اليمين لرؤية الجدول بالكامل):</p>
        <markdown-accessiblity-table data-catalyst=""><table>
            <thead>
                <tr>
                    <th>اسم الحقل</th>
                    <th>قابل للاسترداد</th>
                    <th>قابل للتصفية</th>
                    <th>قابل للفرز</th>
                    <th>قابلة لتشكيل الواجهة</th>
                    <th>قابل للبحث</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>metadata_storage_size</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td></td>
                    <td></td>
                </tr>
                <tr>
                    <td>metadata_storage_last_modified</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td></td>
                    <td></td>
                </tr>
                <tr>
                    <td>metadata_storage_name</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td></td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                </tr>
                <tr>
                    <td>metadata_author</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                </tr>
                <tr>
                    <td>المواقع</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td></td>
                    <td></td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                </tr>
                <tr>
                    <td>keyphrases</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td></td>
                    <td></td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                </tr>
                <tr>
                    <td>اللغة</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                    <td></td>
                    <td></td>
                    <td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔</td>
                </tr>
            </tbody>
        </table></markdown-accessiblity-table>
    </li>
    <li>تحقق جيدًا من اختياراتك، مع إيلاء اهتمام خاص للتأكد من تحديد الخيارات الصحيحة <b>Retrievable</b>،<b>وFilterable</b>،<b>وSortable</b>،<b>وFacetable</b>و <b>Searchable</b> لكل حقل (قد يكون من الصعب تغييرها لاحقًا). ثم تابع إلى الخطوة التالية (<i>إنشاء مفهرس</i>).</li>
    <li>غيّر <b>اسم المفهرس</b> إلى <b>margies-index</b>.</li>
    <li>اترك <b>الجدول</b> معيناً على <b>مرة واحدة</b>.</li>
    <li>قم بتوسيع الخيارات <b>المتقدمة</b>، وتأكد من تحديد الخيار <b>مفاتيح الترميز Base-64</b> (تجعل مفاتيح الترميز الفهرس أكثر كفاءة بشكل عام).</li>
    <li>
        <p dir="auto">حدد <b>إرسال</b> لإنشاء مصدر البيانات ومجموعة المهارات والفهرس والمفهرس. يتم تشغيل المفهرس تلقائياً ويقوم بتشغيل خط أنابيب الفهرسة، والذي:</p>
        <ol dir="auto">
            <li>يستخرج محتويات وحقول بيانات تعريف الوثيقة من مصدر البيانات</li>
            <li>يدير مجموعة مهارات المهارات المعرفية لإنشاء حقول إضافية غنية</li>
            <li>يعين الحقول المستخرجة إلى الفهرس.</li>
        </ol>
    </li>
    <li>على الجانب الأيمن، اعرض صفحة <b>المُفهرسات</b>، والتي يجب أن تظهر <b>margies-indexer</b> الذي تم إنشاؤه حديثًا. انتظر بضع دقائق، ثم انقر فوق <b>↻تحديث</b> حتى تشير <b>الحالة</b> إلى نجاح.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">البحث في الفهرس</h2><a id="user-content-البحث-في-الفهرس" class="anchor" aria-label="Permalink: البحث في الفهرس" href="#البحث-في-الفهرس"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن أصبح لديك فهرس، يمكنك البحث فيه.</p>
<ol dir="rtl">
    <li>في أعلى صفحة <b>نظرة عامة</b>، لمورد Azure AI Search خاصتك، حدد <b>مستكشف البحث</b>.</li>
    <li>في مستكشف البحث، في مربع <b>سلسلة الاستعلام</b>، أدخل `*` (علامة نجمية واحدة)، ثم حدد <b>بحث</b>.</li>
    <p dir="auto">يسترد هذا الاستعلام جميع المستندات في الفهرس بتنسيق JSON. افحص النتائج ولاحظ الحقول الخاصة بكل مستند، والتي تحتوي على محتوى المستند وبيانات التعريف والبيانات التي تم إثراؤها المستخلصة من المهارات المعرفية التي حددتها.</p>
    <li>ي قائمة <b>العرض</b>، حدد <b>طريقة عرض JSON</b> ولاحظ ظهور طلب JSON للبحث، مثل هذا:</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>{
    "search": "*"
}</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="{
    &quot;search&quot;: &quot;*&quot;
}" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <li>قم بتعديل طلب JSON ليتضمن معلمة <b>العد</b> كما هو موضح هنا:</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>{
    "search": "*",
    "count": true
}</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="{
    &quot;search&quot;: &quot;*&quot;,
    &quot;count&quot;: true
}" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <li>أرسل البحث المعدل. هذه المرة، تتضمن النتائج حقلًا<b>@odata.count</b> في أعلى النتائج يشير إلى عدد المستندات التي تم إرجاعها بواسطة البحث.</li>
    <li>جرّب الاستعلام التالي:</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>{
    "search": "*",
    "count": true,
    "select": "metadata_storage_name,metadata_author,locations"
}</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="{
    &quot;search&quot;: &quot;*&quot;,
    &quot;count&quot;: true,
    &quot;select&quot;: &quot;metadata_storage_name,metadata_author,locations&quot;
}" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <p dir="auto">تتضمن النتائج هذه المرة فقط اسم الملف والكاتب وأي مواقع مذكورة في محتوى المستند. يوجد اسم الملف والكاتب في حقلي <b>metadata_storage_name</b> و <b>metadata_author</b>، اللذين تم استخلاصهما من مستند المصدر. تم إنشاء حقل<b>المواقع</b> بواسطة مهارة معرفية.</p>
    <li>الآن جرب سلسلة الاستعلام التالية:</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>{
    "search": "New York",
    "count": true,
    "select": "metadata_storage_name,keyphrases"
}</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="{
    &quot;search&quot;: &quot;New York&quot;,
    &quot;count&quot;: true,
    &quot;select&quot;: &quot;metadata_storage_name,keyphrases&quot;
}" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <p dir="auto">يبحث هذا البحث عن المستندات التي تشير إلى "نيويورك" في أي من الحقول القابلة للبحث، ويعيد اسم الملف والعبارات الرئيسية في المستند.</p>
    <li>دعنا نجرب استعلام آخر:</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>{
    "search": "New York",
    "count": true,
    "select": "metadata_storage_name",
    "filter": "metadata_author eq 'Reviewer'"
}</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="{
    &quot;search&quot;: &quot;New York&quot;,
    &quot;count&quot;: true,
    &quot;select&quot;: &quot;metadata_storage_name&quot;,
    &quot;filter&quot;: &quot;metadata_author eq 'Reviewer'&quot;
}" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <p dir="auto">يقوم هذا الاستعلام بإرجاع اسم الملف لأي مستندات قام <i>المراجع</i>بتأليفها والتي تشير إلى "نيويورك".</p>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">استكشاف وتعديل تعريفات مكونات البحث</h2><a id="user-content-استكشاف-وتعديل-تعريفات-مكونات-البحث" class="anchor" aria-label="Permalink: استكشاف وتعديل تعريفات مكونات البحث" href="#استكشاف-وتعديل-تعريفات-مكونات-البحث"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">تستند مكونات حل البحث إلى تعريفات JSON، والتي يمكنك عرضها وتعديلها في مدخل Microsoft Azure.</p>
<p dir="auto">بينما يمكنك استخدام المدخل لإنشاء حلول البحث وتعديلها، غالبًا ما يكون من المستحسن تعريف كائنات البحث في JSON واستخدام REST لخدمة الذكاء الاصطناعي في Azure لإنشائها وتعديلها.</p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">الحصول على نقطة النهاية والمفتاح لمورد Azure AI Search resource خاصتك</h3><a id="user-content-الحصول-على-نقطة-النهاية-والمفتاح-لمورد-azure-ai-search-resource-خاصتك" class="anchor" aria-label="Permalink: الحصول على نقطة النهاية والمفتاح لمورد Azure AI Search resource خاصتك" href="#الحصول-على-نقطة-النهاية-والمفتاح-لمورد-azure-ai-search-resource-خاصتك"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
    <li>في مدخل Microsoft Azure، ارجع إلى صفحة<b> نظرة عامة</b> لمورد Azure AI Search خاصتك، وفي القسم العلوي من الصفحة، ابحث عن <b>عنوان URL</b> للمورد لديك (الذي يشبه <b><a href="https://resource_name.search.windows.net" rel="nofollow">https://resource_name.search.windows.net</a></b>) وانسخه إلى الحافظة.</li>
    <li>في Visual Studio Code، في جزء Explorer، قم بتوسيع المجلد <b> 01-azure-search</b> ومجلده الفرعي <b> modify-search</b>، وحدد <b>modify-search.cmd</b> لفتحه. ستستخدم ملف البرنامج النصي هذا لتشغيل أوامر <i> cURL</i> التي ترسل JSON إلى واجهة REST لخدمة الذكاء الاصطناعي في Azure.</li>
    <li>في <b>modify-search.cmd</b>، استبدل العنصر النائب<b> YOUR_SEARCH_URL</b> بعنوان URL الذي نسخته إلى الحافظة.</li>
    <li>في بوابة Azure، في قسم <b>الإعدادات</b>، اعرض صفحة <b>المفاتيح</b> لمورد Azure AI Search الخاص بك، وانسخ <b>مفتاح المسؤول الأساسي</b> إلى الحافظة.</li>
    <li>في Visual Studio Code، استبدل العنصر النائب <b> YOUR_ADMIN_KEY</b>بالمفتاح الذي نسخته إلى الحافظة.</li>
    <li>احفظ التغييرات على <b>modify-search.cmd</b> (ولكن لا تقم بتشغيلها بعد!)</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">مراجعة مجموعة المهارات وتعديلها</h3><a id="user-content-مراجعة-مجموعة-المهارات-وتعديلها" class="anchor" aria-label="Permalink: مراجعة مجموعة المهارات وتعديلها" href="#مراجعة-مجموعة-المهارات-وتعديلها"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
    <li>في Visual studio Code، في مجلد<b> modify-search</b>، افتح <b>skillset.json</b>. يظهر هذا تعريف JSON لمجموعة <b>margies-skillset</b>.</li>
    <li>في أعلى تعريف مجموعة المهارات، لاحظ كائن <b> cognitiveServices</b>، والذي يستخدم لتوصيل مورد خدمات الذكاء الاصطناعي في Azure بمجموعة المهارات.</li>
    <li>في بوابة Azure، افتح مورد Azure AI Services (ليس مورد Azure AI Search الخاص بك!) وفي قسم <b>إدارة الموارد</b>، اعرض صفحة <b>المفاتيح ونقاط النهاية</b> الخاصة به. ثم انسخ <b>المفتاح 1</b>إلى الحافظة.</li>
    <li>في Visual Studio Code، في <b>skillset.json</b>، استبدل العنصر النائب<b> YOUR_COGNITIVE_SERVICES_KEY</b> بمفتاح خدمات الذكاء الاصطناعي في Azure الذي نسخته إلى الحافظة.</li>
    <li>قم بالتمرير عبر ملف JSON، مع ملاحظة أنه يتضمن تعريفات للمهارات التي أنشأتها باستخدام واجهة مستخدم Azure AI Search في مدخل Microsoft Azure. في أسفل قائمة المهارات، تمت إضافة مهارة إضافية باستخدام التعريف التالي:</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>{
    "@odata.type": "#Microsoft.Skills.Text.V3.SentimentSkill",
    "defaultLanguageCode": "en",
    "name": "get-sentiment",
    "description": "New skill to evaluate sentiment",
    "context": "/document",
    "inputs": [
        {
            "name": "text",
            "source": "/document/merged_content"
        },
        {
            "name": "languageCode",
            "source": "/document/language"
        }
    ],
    "outputs": [
        {
            "name": "sentiment",
            "targetName": "sentimentLabel"
        }
    ]
}</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="{
    &quot;@odata.type&quot;: &quot;#Microsoft.Skills.Text.V3.SentimentSkill&quot;,
    &quot;defaultLanguageCode&quot;: &quot;en&quot;,
    &quot;name&quot;: &quot;get-sentiment&quot;,
    &quot;description&quot;: &quot;New skill to evaluate sentiment&quot;,
    &quot;context&quot;: &quot;/document&quot;,
    &quot;inputs&quot;: [
        {
            &quot;name&quot;: &quot;text&quot;,
            &quot;source&quot;: &quot;/document/merged_content&quot;
        },
        {
            &quot;name&quot;: &quot;languageCode&quot;,
            &quot;source&quot;: &quot;/document/language&quot;
        }
    ],
    &quot;outputs&quot;: [
        {
            &quot;name&quot;: &quot;sentiment&quot;,
            &quot;targetName&quot;: &quot;sentimentLabel&quot;
        }
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
    </div>
    <p dir="auto">تسمى المهارة الجديدة<b> get-sentiment</b>، ولكل <b>مستوى مستند</b> في مستند، ستقوم بتقييم النص الموجود في الحقل<b> merged_content</b> للمستند الذي تتم فهرسته (والذي يتضمن المحتوى المصدر بالإضافة إلى أي نص مستخلص من الصور في المحتوى). ويستخدم اللغة<b> المستخلصة </b>للمستند (مع القيمة اللغة الإنجليزية بشكل افتراضي)، ويقيّم تسمية لتوجه المحتوى. يمكن أن تكون قيم تسمية التوجه "إيجابية" أو "سلبية" أو "محايدة" أو "مختلطة". ثم يتم إخراج هذه التسمية كحقل جديد يسمى <b>sentimentLabel</b>.</p>
    <li>احفظ التغييرات التي أجريتها على<b>skillset.json</b>.</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">مراجعة الفهرس وتعديله</h3><a id="user-content-مراجعة-الفهرس-وتعديله" class="anchor" aria-label="Permalink: مراجعة الفهرس وتعديله" href="#مراجعة-الفهرس-وتعديله"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
    <li>في Visual studio Code، في مجلد<b> modify-search</b>، افتح <b>index.json</b>. يظهر هذا تعريف JSON لـ <b>margies-index</b>.</li>
    <li>قم بالتمرير عبر الفهرس وشاهد تعريفات الحقول. تستند بعض الحقول إلى بيانات التعريف والمحتوى في المستند المصدر، وتستند الحقول الأخرى على نتائج المهارات في مجموعة المهارات.</li>
    <li>في نهاية قائمة الحقول التي قمت بتعريفها في مدخل Microsoft Azure، لاحظ أنه تمت إضافة حقلين إضافيين:</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>{
    "name": "sentiment",
    "type": "Edm.String",
    "facetable": false,
    "filterable": true,
    "retrievable": true,
    "sortable": true
},
{
    "name": "url",
    "type": "Edm.String",
    "facetable": false,
    "filterable": true,
    "retrievable": true,
    "searchable": false,
    "sortable": false
}</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="{
    &quot;name&quot;: &quot;sentiment&quot;,
    &quot;type&quot;: &quot;Edm.String&quot;,
    &quot;facetable&quot;: false,
    &quot;filterable&quot;: true,
    &quot;retrievable&quot;: true,
    &quot;sortable&quot;: true
},
{
    &quot;name&quot;: &quot;url&quot;,
    &quot;type&quot;: &quot;Edm.String&quot;,
    &quot;facetable&quot;: false,
    &quot;filterable&quot;: true,
    &quot;retrievable&quot;: true,
    &quot;searchable&quot;: false,
    &quot;sortable&quot;: false
}" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <li>سيتم استخدام حقل<b>التوجه</b> لإضافة الإخراج من مهارة<b> get-sentiment</b> التي تمت إضافتها إلى مجموعة المهارات. سيتم استخدام حقل<b>url</b> لإضافة عنوان URL لكل مستند مفهرس إلى الفهرس، استنادًا إلى القيمة<b> metadata_storage_path</b> المستخلصة من مصدر البيانات. لاحظ أن الفهرس يتضمن بالفعل حقل <b> metadata_storage_path</b>، ولكنه يستخدم كمفتاح فهرس والمرمز باستخدام Base-64، ما يجعله فعالاً كمفتاح ولكنه يتطلب من تطبيقات العميل فك ترميزه إذا كانوا يريدون استخدام قيمة URL الفعلية كحقل. تؤدي إضافة حقل ثان للقيمة غير المشفرة إلى حل هذه المشكلة.</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">مراجعة المفهرس وتعديله</h3><a id="user-content-مراجعة-المفهرس-وتعديله" class="anchor" aria-label="Permalink: مراجعة المفهرس وتعديله" href="#مراجعة-المفهرس-وتعديله"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
    <li>في Visual studio Code، في مجلد<b> modify-search</b>، افتح <b>indexer.json</b>. يعرض هذا تعريف JSON لمفهرس <b>margies-indexer</b>، الذي يعين الحقول المستخلصة من محتوى المستند وبيانات التعريف (في قسم<b> fieldMappings</b>)، والقيم المستخلصة بواسطة المهارات في مجموعة المهارات (في قسم<b> outputFieldMappings</b>)، إلى الحقول في الفهرس.</li>
    <li>في قائمة <b> fieldMappings</b>، لاحظ تعيين قيمة<b> metadata_storage_path</b> إلى حقل المفتاح المشفر باستخدام base-64. تم إنشاء هذا عند تعيين <b>metadata_storage_path</b> كمفتاح وتحديد خيار لترميز المفتاح في مدخل Microsoft Azure. بالإضافة إلى ذلك، يقوم التعيين الجديد بتعيين نفس القيمة بشكل صريح إلى حقل عنوان <b>url</b>، ولكن بدون ترميز Base-64:</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>{
    "sourceFieldName" : "metadata_storage_path",
    "targetFieldName" : "url"
} </code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="{
    &quot;sourceFieldName&quot; : &quot;metadata_storage_path&quot;,
    &quot;targetFieldName&quot; : &quot;url&quot;
} " tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <p dir="auto">يتم تعيين كافة حقول بيانات التعريف والمحتوى الأخرى في المستند المصدر ضمنيًا إلى حقول بنفس الاسم في الفهرس.</p>
    <li>راجع قسم<b> ouputFieldMappings</b>، الذي يعين المخرجات من المهارات في مجموعة المهارات إلى حقول الفهرس. يعكس معظم ذلك الخيارات التي قمت بها في واجهة المستخدم، ولكن تمت إضافة التعيين التالي لتعيين قيمة <b> sentimentLabel</b> المستخلصة من مهارة التوجه الخاصة بك إلى حقل<b> التوجه </b>الذي أضفته إلى الفهرس:</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>{
    "sourceFieldName": "/document/sentimentLabel",
    "targetFieldName": "sentiment"
} </code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="{
    &quot;sourceFieldName&quot;: &quot;/document/sentimentLabel&quot;,
    &quot;targetFieldName&quot;: &quot;sentiment&quot;
} " tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">استخدام واجهة برمجة تطبيقات REST لتحديث حل البحث</h3><a id="user-content-استخدام-واجهة-برمجة-تطبيقات-rest-لتحديث-حل-البحث" class="anchor" aria-label="Permalink: استخدام واجهة برمجة تطبيقات REST لتحديث حل البحث" href="#استخدام-واجهة-برمجة-تطبيقات-rest-لتحديث-حل-البحث"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
    <li>انقر بزر الماوس الأيمن فوق مجلد <b>modify-search</b> وافتح محطة طرفية متكاملة.</li>
    <li>في جزء الوحدة الطرفية لمجلد <b>modify-search</b>، أدخل الأمر التالي لتشغيل البرنامج النصي<b> modify-search.cmd</b>، الذي يرسل تعريفات JSON إلى واجهة REST ويبدأ الفهرسة.</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>./modify-search</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="./modify-search" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <li>عند انتهاء البرنامج النصي، ارجع إلى صفحة <b>نظرة عامة</b> لمورد Azure AI Search في مدخل Microsoft Azure واعرض صفحة<b>المفهرسات</b>. حدد <b>تحديث</b> بشكل دوري لتتبع تقدم عملية الفهرسة. قد يستغرق الأمر دقيقة أو نحو ذلك حتى يكتمل.</li>
    <p dir="auto"><i>قد تكون هناك بعض التحذيرات لبعض المستندات الكبيرة جدًا لتقييم التوجه. غالبًا ما يتم إجراء تحليل التوجه على مستوى الصفحة أو الجملة بدلاً من المستند بالكامل؛ ولكن في سيناريو هذه الحالة، فإن معظم المستندات - خاصة تقييمات الفندق، تكون قصيرة بما يكفي لتقييم درجات التوجه المفيدة على مستوى المستند.</i></p>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">الاستعلام عن الفهرس المعدل</h3><a id="user-content-الاستعلام-عن-الفهرس-المعدل" class="anchor" aria-label="Permalink: الاستعلام عن الفهرس المعدل" href="#الاستعلام-عن-الفهرس-المعدل"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
    <li>في أعلى الجزء لمورد Azure الذكاء الاصطناعي Search، حدد <b>مستكشف البحث</b>.</li>
    <li>في مستكشف البحث، في <b>مربع </b>سلسلة الاستعلام، أرسل استعلام JSON التالي:</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>{
    "search": "London",
    "select": "url,sentiment,keyphrases",
    "filter": "metadata_author eq 'Reviewer' and sentiment eq 'positive'"
}</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="{
    &quot;search&quot;: &quot;London&quot;,
    &quot;select&quot;: &quot;url,sentiment,keyphrases&quot;,
    &quot;filter&quot;: &quot;metadata_author eq 'Reviewer' and sentiment eq 'positive'&quot;
}" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <p dir="auto">يسترد هذا الاستعلام عنوان <b>URL</b> <b>والمشاعر</b> <b>وعبارات</b> المفاتيح لجميع المستندات التي تشير إلى <i>لندن</i> التي ألفها <i>المراجع</i> التي تحمل وصفا إيجابيا <b>للتوجه</b> (بمعنى آخر، المراجعات الإيجابية التي تذكر لندن)</p>
    <li><b>أغلق صفحة مستكشف البحث</b> للعودة إلى صفحة<b>نظرة عامة</b>.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إنشاء تطبيق بحث للعميل</h2><a id="user-content-إنشاء-تطبيق-بحث-للعميل" class="anchor" aria-label="Permalink: إنشاء تطبيق بحث للعميل" href="#إنشاء-تطبيق-بحث-للعميل"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن أصبح لديك فهرس مفيد، يمكنك استخدامه من تطبيق عميل. يمكنك القيام بذلك عن طريق استخدام واجهة REST، وإرسال الطلبات وتلقي الاستجابات بتنسيق JSON عبر HTTP؛ أو يمكنك استخدام مجموعة أدوات تطوير البرامج (SDK) للغة البرمجة المفضلة لديك. سنستخدم SDK، في هذا التمرين.</p>
<blockquote>
<p dir="auto"><b>ملاحظة</b>: يمكنك اختيار استخدام SDK إما لـ <b>C#</b> أو <b>Python</b>. في الخطوات الواردة أدناه، نفذ الإجراءات المناسبة للغتك المفضلة.</p>
</blockquote>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">الحصول على نقطة النهاية والمفاتيح لمورد البحث خاصتك</h3><a id="user-content-الحصول-على-نقطة-النهاية-والمفاتيح-لمورد-البحث-خاصتك" class="anchor" aria-label="Permalink: الحصول على نقطة النهاية والمفاتيح لمورد البحث خاصتك" href="#الحصول-على-نقطة-النهاية-والمفاتيح-لمورد-البحث-خاصتك"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
    <li>في مدخل Microsoft Azure، في صفحة <b>نظرة عامة</b> لمورد Azure AI Search، لاحظ قيمة<b> Url</b>، والتي يجب أن تكون مشابهة لـ <b>https://<i>your_resource_name</i>.search.windows.net</b>. هذه هي نقطة النهاية لمورد البحث لديك.</li>
    <li>في صفحة <b>المفاتيح</b>، لاحظ أن هناك مفتاحين <b>للمسؤول</b> ومفتاح استعلام**** واحد. <i>يتم استخدام مفتاح المسؤول</i> لإنشاء موارد البحث وإدارتها؛ ويتم استخدام مفتاح<i>الاستعلام</i> بواسطة تطبيقات العميل التي تحتاج فقط إلى إجراء استعلامات البحث.</li>
    <p dir="auto"><i>ستحتاج إلى نقطة النهاية ومفتاح الاستعلام لتطبيق العميل الخاص بك.</i></p>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">الاستعداد لاستخدام Azure AI Search SDK</h3><a id="user-content-الاستعداد-لاستخدام-azure-ai-search-sdk" class="anchor" aria-label="Permalink: الاستعداد لاستخدام Azure AI Search SDK" href="#الاستعداد-لاستخدام-azure-ai-search-sdk"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
    <li>في Visual Studio Code، في جزء <b>Explorer</b>، استعرض للوصول إلى المجلد <b>01-azure-search</b> وقم بتوسيع المجلد <b>CSharp</b> أو <b>Python</b> حسب تفضيل اللغة لديك.</li>
    <li>انقر بزر الماوس الأيمن فوق مجلد <b>margies-travel</b> وافتح محطة طرفية متكاملة. ثم عليك تثبيت حزمة Azure AI Search SDK عن طريق تشغيل الأمر المناسب لتفضيل اللغة لديك:</li>
    <b>#C</b>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet add package Azure.Search.Documents --version 11.6.0</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet add package Azure.Search.Documents --version 11.6.0" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <b>Python</b>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>pip install azure-search-documents==11.5.1</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="pip install azure-search-documents==11.5.1" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <li>
        <p dir="auto">اعرض محتويات مجلد <b>margies-travel</b>، ولاحظ أنه يحتوي على ملف لإعدادات التكوين:</p>
        <ul dir="rtl">
            <li><b>C#</b>: appsettings.json</li>
            <li><b>Python</b>: .env</li>
        </ul>
    </li>
    <p dir="auto">افتح ملف التكوين وقم بتحديث قيم التكوين التي يحتوي عليها لتعكس <b>نقطة النهاية</b> و<b>مفتاح الاستعلام</b> لمورد Azure AI Search. احفظ تغييراتك.</p>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">استكشاف التعليمات البرمجية للبحث في فهرس</h3><a id="user-content-استكشاف-التعليمات-البرمجية-للبحث-في-فهرس" class="anchor" aria-label="Permalink: استكشاف التعليمات البرمجية للبحث في فهرس" href="#استكشاف-التعليمات-البرمجية-للبحث-في-فهرس"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">يحتوي مجلد<b> margies-travel</b> على ملفات تعليمات برمجية لتطبيق ويب (تطبيق ويب Microsoft C# <i>ASP.NET Razor</i> أو تطبيق Python <i>Flask</i>)، والذي يتضمن وظائف البحث.</p>
<ol dir="rtl">
    <li>
        <p dir="auto">افتح ملف التعليمات البرمجية التالي في تطبيق الويب، اعتمادًا على اختيارك للغة البرمجة:</p>
        <ul dir="rtl">
            <li><b>C#</b>:Pages/Index.cshtml.cs</li>
            <li><b>Python</b>: app.py</li>
        </ul>
    </li>
    <li>بالقرب من أعلى ملف التعليمات البرمجية، ابحث عن التعليق <b>استيراد مساحات أسماء البحث</b>، ولاحظ مساحات الأسماء التي تم استيرادها للعمل مع Azure AI Search SDK:</li>
    <li>في الدالة <b>search_query</b>، ابحث عن التعليق <b>إنشاء عميل بحث</b>، ولاحظ أن التعليمات البرمجية تنشئ كائن <b>SearchClient</b> باستخدام نقطة النهاية ومفتاح الاستعلام لمورد Azure AI Search لديك:</li>
    <li>
        <p dir="auto">في الدالة <b>search_query</b>، ابحث عن التعليق <b>إرسال استعلام بحث</b>، وراجع التعليمات البرمجية لإرسال بحث عن النص المحدد باستخدام الخيارات التالية:</p>
        <ul dir="rtl">
            <li>تم العثور على <i>وضع بحث</i> يتطلب <b>كل</b>الكلمات الفردية في نص البحث.</li>
            <li>يتم تضمين العدد الإجمالي للمستندات التي تم العثور عليها عن طريق البحث في النتائج.</li>
            <li>تتم تصفية النتائج لتضمين فقط المستندات التي تطابق تعبير عامل التصفية المقدّم.</li>
            <li>يتم فرز النتائج في ترتيب الفرز المحدد.</li>
            <li>يتم إرجاع كل قيمة منفصلة لحقل <b> metadata_author</b> <i>كواجهة</i> والتي يمكن استخدامها لعرض قيم محددة مسبقًا للتصفية.</li>
            <li>يتم تضمين ما يصل إلى ثلاثة مستخلصات من حقول <b> merged_content</b> و <b>imageCaption</b> مع كون مصطلحات البحث المضمنة في النتائج.</li>
            <li>تتضمن النتائج الحقول المحددة فقط.</li>
        </ul>
    </li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">استكشاف التعليمات البرمجية لعرض نتائج البحث</h3><a id="user-content-استكشاف-التعليمات-البرمجية-لعرض-نتائج-البحث" class="anchor" aria-label="Permalink: استكشاف التعليمات البرمجية لعرض نتائج البحث" href="#استكشاف-التعليمات-البرمجية-لعرض-نتائج-البحث"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">يتضمن تطبيق الويب بالفعل تعليمة برمجية لمعالجة نتائج البحث وعرضها.</p>
<ol dir="rtl">
    <li>
        <p dir="auto">افتح ملف التعليمات البرمجية التالي في تطبيق الويب، اعتمادًا على اختيارك للغة البرمجة:</p>
        <ul dir="rtl">
            <li><b>C#</b>:Pages/Index.cshtml</li>
            <li><b>Python</b>: templates/search.html</li>
        </ul>
    </li>
    <li>
        <p dir="auto">افحص التعليمات البرمجية التي تعرض الصفحة التي يتم عرض نتائج البحث عليها. لاحظ ما يلي:</p>
        <ul dir="rtl">
            <li>تبدأ الصفحة بنموذج بحث يمكن للمستخدم استخدامه لإرسال بحث جديد (في إصدار Python للتطبيق، يتم تعريف هذا النموذج في قالب<b> base.html</b>)، والذي تتم الإشارة إليه في بداية الصفحة.</li>
            <li>
                <p dir="auto">ثم يتم عرض نموذج ثان، مما يمكن المستخدم من تحسين نتائج البحث. التعليمات البرمجية لهذا النموذج:</p>
                <ul dir="rtl">
                    <li>استرداد عدد المستندات وعرضها من نتائج البحث.</li>
                    <li>استرداد قيم الواجهة لحقل <b>metadata_author</b> وعرضها كقائمة خيار للتصفية.</li>
                    <li>إنشاء قائمة منسدلة لخيارات الفرز للنتائج.</li>
                </ul>
            </li>
            <li>
                <p dir="auto">ثم تتكرر التعليمات البرمجية من خلال نتائج البحث، مع عرض كل نتيجة على النحو التالي:</p>
                <ul dir="rtl">
                    <li><b>عرض حقل metadata_storage_name</b> (اسم الملف) كارتباط إلى العنوان في حقل<b> url</b>.</li>
                    <li>عرض<i>النقاط البارزة</i> لمصطلحات البحث الموجودة في حقلي<b> merged_content</b> و <b>imageCaption</b> للمساعدة في إظهار مصطلحات البحث في السياق.</li>
                    <li>عرض حقول <b>metadata_author</b>و<b>metadata_storage_size</b>و<b>metadata_storage_last_modified</b> و <b>اللغة</b>.</li>
                    <li>عرض تسمية<b>التوجه</b> للمستند. يمكن أن تكون إيجابية أو سلبية أو محايدة أو مختلطة.</li>
                    <li>عرض أول خمس <b>عبارات أساسية</b> (إن وجدت).</li>
                    <li>عرض أول خمسة <b>مواقع</b> (إن وجدت).</li>
                    <li>عرض أول خمس <b> علامات الصورة</b>(إن وجدت).</li>
                </ul>
            </li>
        </ul>
    </li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">شغّل تطبيق الويب</h3><a id="user-content-شغّل-تطبيق-الويب" class="anchor" aria-label="Permalink: شغّل تطبيق الويب" href="#شغّل-تطبيق-الويب"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<ol dir="rtl">
    <li>أعد الوحدة الطرفية المتكاملة للمجلد <b>margies-travel</b>، وأدخل الأمر التالي لتشغيل البرنامج:</li>
    <b>#C</b>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>dotnet run</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="dotnet run" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <b>Python</b>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>flask run</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="flask run" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <li>في الرسالة التي يتم عرضها عند بدء تشغيل التطبيق بنجاح، اتبع الارتباط إلى تطبيق الويب قيد التشغيل (<i>http://localhost:5000/</i> أو <i><a href="http://127.0.0.1:5000/" rel="nofollow">http://127.0.0.1:5000/</a></i>) لفتح موقع Margies Travel في مستعرض ويب.</li>
    <li>على موقع Margie's Travel على الويب، أدخل <b>فندق لندن</b> في مربع البحث وانقر فوق <b>Search</b>.</li>
    <li>راجع نتائج البحث. وهي تشمل اسم الملف (مع ارتباط تشعبي إلى عنوان URL للملف) ومستخرج من محتوى الملف مع التأكيد على مصطلحات البحث (<i>لندن</i> و<i>فندق</i>) والسمات الأخرى للملف من حقول الفهرس.</li>
    <li>
        <p dir="auto">لاحظ أن صفحة النتائج تتضمن بعض عناصر واجهة المستخدم التي تمكنك من تحسين النتائج. يتضمن هذا ما يلي:</p>
        <ul dir="rtl">
            <li>يستند<i>عامل تصفية</i> إلى قيمة واجهة لحقل <b>metadata_author</b>. يوضح هذا كيفية استخدامك حقول <i>قابلة لتشكيل الواجهة</i> لإرجاع قائمة من <i>الواجهات</i> - الحقول مع مجموعة صغيرة من القيم المنفصلة التي يمكن عرضها كقيم تصفية محتملة في واجهة المستخدم.</li>
            <li>القدرة على <i>ترتيب </i>النتائج استنادًا إلى حقل محدد واتجاه الفرز (تصاعدي أو تنازلي). يستند الترتيب الافتراضي إلى <i>الصلة</i>، والتي يتم حسابها كقيمة <b>search.score()</b> استنادًا إلى <i>ملف تعريف التسجيل</i>الذي يقيّم تكرار وأهمية مصطلحات البحث في حقول الفهرس.</li>
        </ul>
    </li>
    <li>حدد عامل تصفية <b>المراجع</b> وخيار الفرز <b>الإيجابية إلى السلبية</b>، ثم حدد <b>تحسين النتائج</b>.</li>
    <li>لاحظ أن النتائج تتم تصفيتها لتضمين التقييمات فقط، ويتم فرزها استنادًا إلى تسمية التوجه.</li>
    <li>في <b>مربع البحث</b>، أدخل بحثًا جديدًا عن <b>فندق هادئ في نيويورك</b> وراجع النتائج.</li>
    <li>
        <p dir="auto">جرب مصطلحات البحث التالية:</p>
        <ul dir="rtl">
            <li><b>برج لندن</b> (لاحظ أن هذا المصطلح يعرف على <i>أنه عبارة رئيسية</i> في بعض الوثائق).</li>
            <li><b>ناطحة السحاب</b> (لاحظ أن هذه الكلمة لا تظهر في المحتوى الفعلي لأي مستندات، ولكنها موجودة في <i>التسميات التوضيحية للصور</i> و<i>علامات الصور</i>التي تم إنشاؤها للصور في بعض المستندات).</li>
            <li><b>صحراء موهافي</b> (لاحظ أن هذا المصطلح محدد كـ <i>موقع</i> في بعض المستندات).</li>
        </ul>
    </li>
    <li>أغلق علامة تبويب المتصفح التي تحتوي على موقع ويب Margie's Travel وقم بالعودة إلى Visual Studio Code. ثم في وحدة Python الطرفية لمجلد <b>margies-travel</b> (حيث يتم تشغيل dotnet أو تطبيق flask)، أدخل Ctrl+C لوقف التطبيق.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">التنظيف</h2><a id="user-content-التنظيف" class="anchor" aria-label="Permalink: التنظيف" href="#التنظيف"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن أكملت التمرين، احذف جميع الموارد التي لم تعد بحاجة إليها. احذف موارد Azure:</p>
<ol dir="rtl">
    <li>في <b>مدخل Azure</b>، حدد "Resource groups".</li>
    <li>حدد مجموعة الموارد التي لا تحتاج إليها، ثم حدد <b>حذف مجموعات الموارد</b>.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">مزيد من المعلومات</h2><a id="user-content-مزيد-من-المعلومات" class="anchor" aria-label="Permalink: مزيد من المعلومات" href="#مزيد-من-المعلومات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">للتعرّف على المزيد حول Azure AI Search، راجع <a href="https://docs.microsoft.com/azure/search/search-what-is-azure-search" rel="nofollow">وثائق Azure AI Search</a></p>
</article></div>
