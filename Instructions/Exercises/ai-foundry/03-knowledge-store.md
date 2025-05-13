<div class="Box-sc-g0xbh4-0 eoaCFS js-snippet-clipboard-copy-unpositioned undefined" data-hpc="true"><article class="markdown-body entry-content container-lg" itemprop="text"><div dir="rtl">
<markdown-accessiblity-table data-catalyst=""><table>
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
  <td><div dir="auto">إنشاء مخزن المعلومات مع بحث الذكاء الاصطناعي في Azure</div></td>
  <td><div dir="auto">Module 12 - Creating a Knowledge Mining Solution</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table></markdown-accessiblity-table>
</div>
<div class="markdown-heading" dir="auto"><h1 tabindex="-1" class="heading-element" dir="auto">إنشاء مخزن المعلومات مع بحث الذكاء الاصطناعي في Azure</h1><a id="user-content-إنشاء-مخزن-المعلومات-مع-بحث-الذكاء-الاصطناعي-في-azure" class="anchor" aria-label="Permalink: إنشاء مخزن المعلومات مع بحث الذكاء الاصطناعي في Azure" href="#إنشاء-مخزن-المعلومات-مع-بحث-الذكاء-الاصطناعي-في-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">يستخدم بحث الذكاء الاصطناعي في Azure مسارًا إثرائيًا لمهارات الذكاء الاصطناعي لاستخراج الحقول التي جرى إنشاؤها بواسطة الذكاء الاصطناعي من المستندات وإدراجها في فهرس كلمات البحث. وفي حين يمكن اعتبار أن الفهرس هو المخرجات الأولية من عملية الفهرسة، فإن البيانات التي تم إثراؤها به والتي يحتوي عليها قد تكون مفيدة أيضًا بطرق أخرى. على سبيل المثال:</p>
<ul dir="rtl">
    <li>لأن الفهرس هو أساسًا مجموعة من عناصر JSON، فكل منها يمثل سجلاً مفهرسًا، فقد يكون من المفيد تصدير العناصر كملفات JSON للتكامل في عملية تزامن البيانات باستخدام أدوات مثل Azure Data Factory.</li>
    <li>قد تحتاج إلى تسوية سجلات الفهرس إلى مخطط ارتباطي من الجداول للتحليل وإعداد التقارير باستخدام أدوات مثل Microsoft Power BI.</li>
    <li>بعد استخراج الصور المضمنة من المستندات في أثناء عملية الفهرسة، قد تحتاج إلى حفظ هذه الصور كملفات.</li>
</ul>
<p dir="auto">في هذه الوحدة، ستنفذ مخزن معلومات لـ <i>Margie's Travel</i>، وهي وكالة سفر وهمية تستخدم المعلومات في الكتيبات وتقييمات الفنادق لمساعدة العملاء في التخطيط للرحلات.</p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية</h2><a id="user-content-الاستعداد-لتطوير-تطبيق-في-تعليمة-visual-studio-البرمجية" class="anchor" aria-label="Permalink: الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية" href="#الاستعداد-لتطوير-تطبيق-في-تعليمة-visual-studio-البرمجية"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">ستطور تطبيق البحث لديك باستخدام Visual Studio Code. تم توفير ملفات التعليمات البرمجية لتطبيقك في GitHub repo.</p>
<blockquote>
<p dir="auto"><b>تلميح</b>: إذا نسخت بالفعل مستودع <b>mslearn-knowledge-mining</b>، فافتحه في Visual Studio code. وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة تطويرك.</p>
</blockquote>
<ol dir="rtl">
    <li>ابدأ تشغيل Visual Studio Code.</li>
    <li>افتح لوحة (SHIFT+CTRL+P) وشغّل <b>Git: استنسخ الأمر </b> لاستنساخ مستودع <code>https://github.com/MicrosoftLearning/mslearn-knowledge-mining</code> إلى مجلد محلي (لا يُهم أي مجلد).</li>
    <li>عند استنساخ المستودع، افتح المجلد في تعليمة Visual Studio البرمجية.</li>
    <li>انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية #C في المستودع.</li>
    <blockquote><b>ملاحظة</b>: إذا جرت مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد <b>ليس الآن</b>.</blockquote>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إنشاء موارد Azure</h2><a id="user-content-إنشاء-موارد-azure" class="anchor" aria-label="Permalink: إنشاء موارد Azure" href="#إنشاء-موارد-azure"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<blockquote>
<p dir="auto"><b>ملاحظة</b>: إذا سبق أن أكملت تمرين <b><a href="/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/OLPRODLOC/Instructions/Exercises/ai-foundry/01-azure-search.md">إنشاء حل بحث الذكاء الاصطناعي في Azure</a></b>، ولا يزال لديك موارد بحث الذكاء الاصطناعي في Azure في اشتراكك، يمكنك تخطي هذا المقطع وبدء مقطع <b>إنشاء حل بحث</b>. وإلا، اتبع الخطوات أدناه لتوفير موارد Azure المطلوبة.</p>
</blockquote>
<ol dir="rtl">
    <li>في مستعرض ويب، افتح مدخل Microsoft Azure في <code>https://portal.azure.com</code>، ثم سجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure لديك.</li>
    <li>يمكنك عرض <b>مجموعات الموارد</b> في اشتراكك.</li>
    <li>إذا كنت تستخدم اشتراكًا مقيدًا توفرت فيه مجموعة موارد لك، فحدد مجموعة الموارد لعرض خصائصها. وإلا، فعليك إنشاء مجموعة موارد جديدة باسم من اختيارك، وانتقل إليها عند إنشائها.</li>
    <li>في صفحة <b>النظرة العامة</b> لمجموعة الموارد الخاصة بك، لاحظ <b>معرف الاشتراك</b> و<b>الموقع</b>. ستحتاج إلى هذه القيم، إلى جانب اسم مجموعة الموارد في الخطوات اللاحقة.</li>
    <li>في تعليمة Visual Studio البرمجية، عليك توسيع المجلد <b>Labfiles/03-knowledge-store</b> وحدد <b>setup.cmd</b>. ستستخدم دُفعة البرنامج النصي لتشغيل أوامر واجهة سطر أوامر Azure (CLI) المطلوبة لإنشاء موارد Azure التي تحتاجها.</li>
    <li>انقر بزر الماوس الأيمن فوق المجلد <b>03-knowledge-store</b> وحدد <b>فتح في الوحدة الطرفية المتكاملة</b>.</li>
    <li>ي جزء terminal، أدخِل الأمر التالي لتأسيس اتصال مصادق إلى اشتراك Azure.</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>az login --output none</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="az login --output none" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <li>عند المطالبة، قم بتسجيل الدخول إلى اشتراكك في Azure. ثم ارجع إلى Visual Studio Code وانتظر حتى تكتمل عملية تسجيل الدخول.</li>
    <li>يمكنك تشغيل الأمر التالي لسرد مواقع Azure.</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>az account list-locations -o table</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="az account list-locations -o table" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <li>في المخرجات، ابحث عن قيمة <b>الاسم</b> التي تتوافق مع موقع مجموعة الموارد الخاصة بك (على سبيل المثال، بالنسبة <i>لشرق الولايات المتحدة</i>، الاسم المقابل هو <i>eastus</i>).</li>
    <li>في البرنامج النصي <b>setup.cmd</b>، عليك تعديل <b>subscription_id</b>، و<b>resource_group</b>، و<b>location</b> المتغيرين باستخدام القيم المناسبة لمعرّف الاشتراك، واسم مجموعة الموارد، واسم الموقع. ثم احفظ التغييرات.</li>
    <li>في الوحدة الطرفية للمجلد <b>03-knowledge-store</b>، أدخل الأمر التالي لتشغيل البرنامج النصي:</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>./setup</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="./setup" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <blockquote><b>ملاحظة</b>: الوحدة النمطية Search CLI قيد المعاينة، وقد تتعطل في <i>- قيد التشغيل ..</i> العملية. إذا حدث ذلك لأكثر من دقيقتين، فاضغط على CTRL+C لإلغاء العملية طويلة الأمد، ثم حدد <b>N</b> عند سؤالك عما إذا كنت تريد إنهاء البرنامج النصي. ومن ثمَّ، يجب أن يكتمل بنجاح.</blockquote>
    <blockquote></blockquote>
    <blockquote>إذا فشل البرنامج النصي، فتأكد من حفظه بأسماء المتغيرات الصحيحة وحاول مرة أخرى.</blockquote>
    <li>
        <p dir="auto">عند اكتمال البرنامج النصي، راجع المخرجات التي يعرضها ولاحظ المعلومات التالية حول موارد Azure (ستحتاج هذه القيم لاحقًا):</p>
        <ul dir="rtl">
            <li>Storage account name</li>
            <li>سلسلة اتصال التخزين</li>
            <li>حساب خدمات الذكاء الاصطناعي في Azure</li>
            <li>مفتاح خدمات الذكاء الاصطناعي في Azure</li>
            <li>نقطة نهاية خدمة البحث</li>
            <li>مفتاح مسؤول خدمة البحث</li>
            <li>مفتاح الاستعلام عن خدمة البحث</li>
        </ul>
    </li>
    <li>في مدخل Microsoft Azure، عليك تحديث مجموعة الموارد وتحقق من أنها تحتوي على حساب مخزن Azure ومورد خدمات الذكاء الاصطناعي في Azure ومورد بحث الذكاء الاصطناعي في Azure.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">إنشاء حل بحث</h2><a id="user-content-إنشاء-حل-بحث" class="anchor" aria-label="Permalink: إنشاء حل بحث" href="#إنشاء-حل-بحث"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن أصبح لديك موارد Azure الضرورية، يمكنك إنشاء حل بحث يتكون من المكونات التالية:</p>
<ul dir="rtl">
    <li><b>مصدر بيانات</b> يشير إلى المستندات في حاوية تخزين Azure لديك.</li>
    <li>تحدد <b>مجموعة مهارات</b> مسار إثراء المهارات لاستخراج الحقول التي جرى إنشاؤها الذكاء الاصطناعي من المستندات. تحدد مجموعة المهارات أيضًا <i>التوقعات</i> التي سيجري إنشاؤها في <i>مخزن المعلومات</i> الخاص بك.</li>
    <li><b>فهرس</b> يحدد مجموعة قابلة للبحث من سجلات المستندات.</li>
    <li>يستخرج <b>مفهرس</b> المستندات من مصدر البيانات، ويطبق مجموعة المهارات، ويملأ الفهرس. كما تستمر عملية الفهرسة في التوقعات المحددة في مجموعة المهارات في مخزن المعلومات.</li>
</ul>
<p dir="auto">في هذا التمرين، ستستخدم واجهة بحث الذكاء الاصطناعي في Azure REST لإنشاء هذه المكونات عن طريق إرسال طلبات JSON.</p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">إعداد JSON لعمليات REST</h3><a id="user-content-إعداد-json-لعمليات-rest" class="anchor" aria-label="Permalink: إعداد JSON لعمليات REST" href="#إعداد-json-لعمليات-rest"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">ستستخدم واجهة REST لإرسال تعريفات JSON لمكونات بحث الذكاء الاصطناعي في Azure لديك.</p>
<ol dir="rtl">
    <li>في تعليمة Visual Studio البرمجية في مجلد <b>03-knowledge-store</b>، عليك توسيع مجلد <b>create-search</b> وحدد <b>data_source.json</b>. يحتوي هذا الملف على تعريف JSON لمصدر بيانات يسمى <b>margies-knowledge-data</b>.</li>
    <li>استبدل العنصر النائب <b>YOUR_CONNECTION_STRING</b> بسلسلة الاتصال لحساب تخزين Azure الخاص بك، والذي يجب أن يشبه ما يلي:</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>DefaultEndpointsProtocol=https;AccountName=ai102str123;AccountKey=12345abcdefg...==;EndpointSuffix=core.windows.net</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="DefaultEndpointsProtocol=https;AccountName=ai102str123;AccountKey=12345abcdefg...==;EndpointSuffix=core.windows.net" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
    </div>
    <p dir="auto"><i>يمكنك العثور على سلسلة الاتصال في صفحة <b>مفاتيح الوصول</b> لحساب التخزين الخاص بك في مدخل Microsoft Azure.</i></p>
    <li>احفظ ملف JSON المُحدَّث وأغلقه.</li>
    <li>في مجلد <b>create-search</b>، افتح <b>skillset.json</b>. يحتوي هذا الملف على تعريف JSON لمصدر بيانات يسمى <b>margies-knowledge-skillset</b>.</li>
    <li>في الجزء العلوي من تعريف مجموعة المهارات، في عنصر <b>cognitiveServices</b>، استبدل العنصر النائب <b>YOUR_COGNITIVE_SERVICES_KEY</b> بأي من المفاتيح الخاصة بموارد خدمات الذكاء الاصطناعي في Azure الخاصة بك.</li>
    <p dir="auto"><i>يمكنك العثور على المفاتيح في صفحة <b>المفاتيح ونقطة النهاية</b> لمورد خدمات الذكاء الاصطناعي في Azure في مدخل Microsoft Azure.</i></p>
    <li>في نهاية مجموعة المهارات الموجودة في مجموعة المهارات الخاصة بك، ابحث عن مهارة <b>Microsoft.Skills.Util.ShaperSkill</b> المسماة <b>Define-projection</b>. تحدد هذه المهارة بنية JSON للبيانات الغنية التي ستُستخدم لتوقعات استمرار التدفق في مخزن المعلومات لكل مستند تجري معالجته بواسطة المفهرس.</li>
    <li>
        <p dir="auto">في الجزء السفلي من ملف مجموعة المهارات، لاحظ أن مجموعة المهارات تتضمن أيضًا تعريف <b>knowledgeStore</b>، والذي يتضمن سلسلة اتصال لحساب تخزين Azure حيث سيجري إنشاء مخزن المعلومات، ومجموعة من <b>الاحتمالات</b>. هذه المهارات تتضمن ثلاث <i>مجموعات احتمال</i>:</p>
        <ul dir="rtl">
            <li>مجموعة تحتوي على احتمال <i>عنصر</i> استنادًا إلى مخرج <b>knowledge_projection</b> من مهارة أداة التشكيل في مجموعة المهارات.</li>
            <li>مجموعة تحتوي على احتمال <i>ملف</i> استنادًا إلى مجموعة <b>normalized_images</b> من بيانات الصور المستخرجة من المستندات.</li>
            <li>
                <p dir="auto">مجموعة تحتوي على احتمالات <i>الجدول</i> التالي:</p>
                <ul dir="rtl">
                    <li><b>KeyPhrases</b>: تحتوي على عمود مفتاح جرى إنشاؤه تلقائيًا وعمود <b>keyPhrase</b> معيَّن إلى مجموعة مخرجات <b>knowledge_projection/key_phrases/</b> من مهارة أداة التشكيل.</li>
                    <li><b>المواقع</b>: تحتوي على عمود مفتاح جرى إنشاؤه تلقائيًا وعمود <b>الموقع</b> المعيَّن إلى مجموعة مخرجات <b>knowledge_projection/key_phrases/</b> من مهارة أداة التشكيل.</li>
                    <li><b>ImageTags</b>: تحتوي على عمود مفتاح جرى إنشاؤه تلقائيًا وعمود <b>علامة</b> معيَّن إلى مخرج مجموعة <b>knowledge_projection/image_tags/</b> من مهارة أداة التشكيل.</li>
                    <li><b>المستندات</b>: يحتوي على عمود مفتاح جرى إنشاؤه تلقائيًا وجميع قيم مخرجات <b>knowledge_projection</b> من مهارة أداة التشكيل التي لم يجري تعيينها بالفعل إلى جدول.</li>
                </ul>
            </li>
        </ul>
    </li>
    <li>استبدل العنصر النائب <b>YOUR_CONNECTION_STRING</b> لقيمة <b>storageConnectionString</b> بسلسلة الاتصال لحساب التخزين الخاص بك.</li>
    <li>احفظ ملف JSON المُحدَّث وأغلقه.</li>
    <li>في مجلد <b>create-search</b>، افتح <b>index.json</b>. يحتوي هذا الملف على تعريف JSON لفهرس يسمى <b>margies-knowledge-index</b>.</li>
    <li>راجع JSON للفهرس، ثم أغلق الملف دون إجراء أي تغييرات.</li>
    <li>في مجلد <b>create-search</b>، افتح <b>indexer.json</b>. يحتوي هذا الملف على تعريف JSON لمفهرس يسمى <b>margies-knowledge-indexer</b>.</li>
    <li>راجع JSON للفهرس، ثم أغلق الملف دون إجراء أي تغييرات.</li>
</ol>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">إرسال طلبات REST</h3><a id="user-content-إرسال-طلبات-rest" class="anchor" aria-label="Permalink: إرسال طلبات REST" href="#إرسال-طلبات-rest"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن أعددت كائنات JSON التي تحدد مكونات حل البحث، يمكنك إرسال مستندات JSON إلى واجهة REST لإنشائها.</p>
<ol dir="rtl">
    <li>في مجلد <b>create-search</b>، افتح <b>create-search.cmd</b>. يستخدم هذا البرنامج النصي الدفعي الأداة المساعدة cURL لإرسال تعريفات JSON إلى واجهة REST لمورد بحث الذكاء الاصطناعي في Azure.</li>
    <li>استبدل العناصر النائبة والمتغيرة <b>YOUR_SEARCH_URL</b> <b>وYOUR_ADMIN_KEY</b> بعنوان <b>Url</b> وأحد <b>مفاتيح المسؤول</b> لمورد بحث الذكاء الاصطناعي في Azure.</li>
    <p dir="auto"><i>يمكنك العثور على هذه القيم في صفحات <b>النظرة العامة</b> <b>والمفاتيح</b> لمورد بحث الذكاء الاصطناعي في Azure في مدخل Microsoft Azure.</i></p>
    <li>احفظ ملف الدفعة المُحدَّث.</li>
    <li>انقر بزر الماوس الأيمن فوق المجلد <b>create-search</b> وحدد <b>فتح في الوحدة الطرفية المتكاملة</b>.</li>
    <li>في الجزء الطرفي لمجلد <b>create-search</b>، أدخل الأمر التالي وشغَّل دُفعة البرنامج النصي.</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>./create-search</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="./create-search" tabindex="0" role="button">
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
        <p dir="auto">عند اكتمال البرنامج النصي، في مدخل Azure، على صفحة مورد بحث الذكاء الاصطناعي في Azure، حدد صفحة <b>المفهرسات</b> وانتظر حتى تكتمل عملية الفهرسة.</p>
        <p dir="auto"><i>يمكنك تحديد <b>تحديث</b> لتتبُّع تقدُّم عملية الفهرسة. قد يستغرق الأمر دقيقة أو نحو ذلك حتى يكتمل.</i></p>
        <blockquote><b>تلميح</b>: إذا فشل البرنامج النصي، فتحقق من العناصر النائبة التي أضفتها في ملفي <b>data_source.json</b> و<b>skillset.json</b> بالإضافة إلى ملف <b>create-search.cmd</b>. بعد تصحيح أي أخطاء، قد تحتاج إلى استخدام واجهة مستخدم مدخل Azure لحذف أي مكونات جرى إنشاؤها في مورد البحث قبل إعادة تشغيل البرنامج النصي.</blockquote>
    </li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">عرض مخزن المعلومات</h2><a id="user-content-عرض-مخزن-المعلومات" class="anchor" aria-label="Permalink: عرض مخزن المعلومات" href="#عرض-مخزن-المعلومات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">بعد تشغيل مفهرس يستخدم مجموعة مهارات لإنشاء مخزن معلومات، يتم الحفاظ على استمرار البيانات التي تم إثراؤها والمستخرجة بواسطة عملية الفهرسة في إسقاطات مخزن المعلومات.</p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">عرض إسقاطات العنصر</h3><a id="user-content-عرض-إسقاطات-العنصر" class="anchor" aria-label="Permalink: عرض إسقاطات العنصر" href="#عرض-إسقاطات-العنصر"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">تتكون احتمالات <i>العنصر</i> المحددة في مجموعة المهارات الخاصة بـ Margie Travel من ملف JSON لكل وثيقة مفهرسة. يتم تخزين هذه الملفات في حاوية blob في حساب Azure Storage المحدد في تعريف مجموعة المهارات.</p>
<ol dir="rtl">
    <li>في مدخل Microsoft Azure، اعرض حساب تخزين Azure الذي أنشأته مسبقًا.</li>
    <li>حدد علامة التبويب <b>مستعرض التخزين</b> (في الجزء الموجود على اليسار) لعرض حساب التخزين في واجهة مستكشف التخزين في مدخل Microsoft Azure.</li>
    <li>عليك توسيع <b>حاويات كائن ثنائي كبير الحجم</b> لعرض الحاويات في حساب التخزين. بالإضافة إلى حاوية <b>margies</b> حيث يجري تخزين البيانات المصدر، يجب أن يكون هناك حاويتين جديدتين: <b>margies-images</b> و <b>margies-knowledge</b>. تم إنشاؤها بواسطة عملية الفهرسة.</li>
    <li>اختر حاوية <b>margies-knowledge</b>. يجب أن تحتوي على مجلد لكل مستند مفهرس.</li>
    <li>افتح أي من المجلدات، ثم افتح ملف <b>knowledge-projection.json</b> الذي يحتوي عليه. يحتوي كل ملف JSON على تمثيل للمستند المفهرس، بما في ذلك البيانات التي تم إثراؤها والمستخرجة من مجموعة المهارات كما هو موضح هنا.</li>
    <div dir="auto">
    <div class="snippet-clipboard-content notranslate position-relative overflow-auto"><pre class="notranslate"><code>{
"file_id":"abcd1234....",
"file_name":"Margies Travel Company Info.pdf",
"url":"https://store....blob.core.windows.net/margies/...pdf",
"language":"en",
"sentiment":0.83164644241333008,
"key_phrases":[
    "Margie’s Travel",
    "Margie's Travel",
    "best travel experts",
    "world-leading travel agency",
    "international reach"
],
"locations":[
    "Dubai",
    "Las Vegas",
    "London",
    "New York",
    "San Francisco"
],
"image_tags":[
    "outdoor",
    "tree",
    "plant",
    "palm"
    ]
}</code></pre><div class="zeroclipboard-container">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn btn-invisible js-clipboard-copy m-2 p-0 d-flex flex-justify-center flex-items-center" data-copy-feedback="Copied!" data-tooltip-direction="w" value="{
&quot;file_id&quot;:&quot;abcd1234....&quot;,
&quot;file_name&quot;:&quot;Margies Travel Company Info.pdf&quot;,
&quot;url&quot;:&quot;https://store....blob.core.windows.net/margies/...pdf&quot;,
&quot;language&quot;:&quot;en&quot;,
&quot;sentiment&quot;:0.83164644241333008,
&quot;key_phrases&quot;:[
    &quot;Margie’s Travel&quot;,
    &quot;Margie's Travel&quot;,
    &quot;best travel experts&quot;,
    &quot;world-leading travel agency&quot;,
    &quot;international reach&quot;
],
&quot;locations&quot;:[
    &quot;Dubai&quot;,
    &quot;Las Vegas&quot;,
    &quot;London&quot;,
    &quot;New York&quot;,
    &quot;San Francisco&quot;
],
&quot;image_tags&quot;:[
    &quot;outdoor&quot;,
    &quot;tree&quot;,
    &quot;plant&quot;,
    &quot;palm&quot;
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
</ol>
<p dir="auto">القدرة على إنشاء احتمالات <i>عنصر</i> مثل هذا تمكنك من توليد عناصر البيانات التي يجري إثراؤها والتي يمكن دمجها في حل تحليل البيانات الخاص بالمؤسسة -- على سبيل المثال عن طريق استيعاب الملفات JSON في مجرى Azure Data Factory لمزيد من المعالجة أو التحميل في مستودع البيانات.</p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">عرض إسقاطات الملف</h3><a id="user-content-عرض-إسقاطات-الملف" class="anchor" aria-label="Permalink: عرض إسقاطات الملف" href="#عرض-إسقاطات-الملف"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">إن احتمالات <i>الملفات</i> المعرفة في مجموعة المهارات تنشئ ملفات JPEG لكل صورة جرى استخراجها من المستندات خلال عملية الفهرسة.</p>
<ol dir="rtl">
    <li>في واجهة <i>مستعرض التخزين</i> في مدخل Microsoft Azure، حدد حاوية كائن ثنائي كبير الحجم <b>margies-images</b>. تحتوي هذه الحاوية على مجلد لكل مستند يحتوي على صور.</li>
    <li>افتح أي من المجلدات واعرض محتوياته - يحتوي كل مجلد على ملف .jpg * واحد على الأقل.</li>
    <li>افتح أيًا من ملفات الصور للتحقق من أنها تحتوي على صور مستخرجة من المستندات.</li>
</ol>
<p dir="auto">القدرة على إنشاء احتمالات <i>ملف</i> مثل هذا تجعل الفهرسة طريقة فعالة لاستخراج الصور المضمنة من حجم كبير من المستندات.</p>
<div class="markdown-heading" dir="auto"><h3 tabindex="-1" class="heading-element" dir="auto">عرض إسقاطات الجدول</h3><a id="user-content-عرض-إسقاطات-الجدول" class="anchor" aria-label="Permalink: عرض إسقاطات الجدول" href="#عرض-إسقاطات-الجدول"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">تشكل احتمالات <i>الجدول</i> المحددة في مجموعة المهارات مخططًا ارتباطيًا للبيانات الثرية.</p>
<ol dir="rtl">
    <li>في واجهة <i>مستعرض التخزين</i> في مدخل Microsoft Azure، عليك توسيع <b>الجداول</b>.</li>
    <li>
        <p dir="auto">حدد جدول <b>المستندات</b> لعرض الأعمدة الخاصة به. تتضمن الأعمدة بعض أعمدة جدول تخزين Azure القياسية - لإخفاء هذه الأعمدة، عليك تعديل <b>خيارات العمود</b> لتحديد الأعمدة التالية فقط:</p>
        <ul dir="rtl">
            <li><b>document_id</b> (عمود المفتاح الذي يجري إنشاؤه تلقائيًا بواسطة عملية الفهرسة)</li>
            <li><b>file_id</b> (عنوان URL للملف المشفر)</li>
            <li><b>file_name</b> (اسم الملف المستخرج من بيانات تعريف المستند)</li>
            <li><b>اللغة</b> (اللغة التي تجري كتابة المستند بها)</li>
            <li><b>التوجه</b> درجة التوجه المحسوبة للمستند.</li>
            <li><b>URL</b> عنوان URL لكائن ثنائي كبير الحجم للمستند في تخزين Azure.</li>
        </ul>
    </li>
    <li>
        <p dir="auto">اعرض الجداول الأخرى التي تم إنشاؤها بواسطة عملية الفهرسة:</p>
        <ul dir="rtl">
            <li><b>ImageTags</b> (تحتوي على صف لكل علامة صورة فردية مع <b>document_id</b> للمستند الذي تظهر فيه العلامة).</li>
            <li><b>KeyPhrases</b> (تحتوي على صف لكل عبارة مفتاح فردية مع <b>document_id</b> للمستند الذي تظهر فيه العبارة).</li>
            <li><b>Locations</b> (تحتوي على صف لكل موقع على حدة مع <b>document_id</b> للمستند الذي يظهر فيه الموقع).</li>
        </ul>
    </li>
</ol>
<p dir="auto">تمكنك القدرة على إنشاء إسقاطات الجدول من إنشاء حلول تحليلية وتقارير للاستعلام عن المخطط الارتباطي على سبيل المثال، استخدام Microsoft Power BI. يمكن استخدام أعمدة المفاتيح التي تم توليدها تلقائيًا للانضمام إلى الجداول في الاستعلامات - على سبيل المثال لإرجاع كافة المواقع المذكورة في مستند معين.</p>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">التنظيف</h2><a id="user-content-التنظيف" class="anchor" aria-label="Permalink: التنظيف" href="#التنظيف"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">الآن بعد أن أكملت التمرين، احذف جميع الموارد التي لم تعد بحاجة إليها. احذف موارد Azure:</p>
<ol dir="rtl">
    <li>في <b>مدخل Azure</b>، حدد "Resource groups".</li>
    <li>حدد مجموعة الموارد التي لا تحتاج إليها، ثم حدد <b>حذف مجموعات الموارد</b>.</li>
</ol>
<div class="markdown-heading" dir="auto"><h2 tabindex="-1" class="heading-element" dir="auto">مزيد من المعلومات</h2><a id="user-content-مزيد-من-المعلومات" class="anchor" aria-label="Permalink: مزيد من المعلومات" href="#مزيد-من-المعلومات"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path d="m7.775 3.275 1.25-1.25a3.5 3.5 0 1 1 4.95 4.95l-2.5 2.5a3.5 3.5 0 0 1-4.95 0 .751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018 1.998 1.998 0 0 0 2.83 0l2.5-2.5a2.002 2.002 0 0 0-2.83-2.83l-1.25 1.25a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042Zm-4.69 9.64a1.998 1.998 0 0 0 2.83 0l1.25-1.25a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042l-1.25 1.25a3.5 3.5 0 1 1-4.95-4.95l2.5-2.5a3.5 3.5 0 0 1 4.95 0 .751.751 0 0 1-.018 1.042.751.751 0 0 1-1.042.018 1.998 1.998 0 0 0-2.83 0l-2.5 2.5a1.998 1.998 0 0 0 0 2.83Z"></path></svg></a></div>
<p dir="auto">لمعرفة المزيد عن إنشاء مخازن المعرفة باستخدام بحث الذكاء الاصطناعي في Azure، راجع <a href="https://docs.microsoft.com/azure/search/knowledge-store-concept-intro" rel="nofollow">وثائق بحث الذكاء الاصطناعي في Azure</a>.</p>
</article></div>
