<div dir="rtl">
<table>
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
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="auto">إضافة إلى فهرس باستخدام واجهة برمجة تطبيقات الدفع</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table>
</div>

# إضافة إلى فهرس باستخدام واجهة برمجة تطبيقات الدفع

تريد استكشاف كيفية إنشاء فهرس بحث الذكاء الاصطناعي في Azure وتحميل المستندات إلى هذا الفهرس باستخدام التعليمات البرمجية #C.

في هذا التمرين، ستستنسخ حل #C موجود وتشغله للعمل على الحجم الأمثل للدُفعة لتحميل المستندات. ثم ستستخدم حجم الدُفعة هذا وتحميل المستندات بفعاليةٍ باستخدام نهج مؤشر ترابط.

> <b>ملاحظة</b>: لإكمال هذا التمرين، ستحتاج إلى اشتراك Microsoft Azure. إذا لم يكن لديك اشتراك بالفعل، يمكنك التسجيل للحصول على الإصدار التجريبي على [https://azure.com/free](https://azure.com/free?azure-portal=true) .

## إعداد موارد Azure الخاص بك

لتوفير وقتك، حدد قالب Azure Resource Manager هذا لإنشاء الموارد التي ستحتاج إليها لاحقاً في التمرين:

<ol dir='rtl'>
    <li><a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FMicrosoftLearning%2Fmslearn-knowledge-mining%2Fmain%2FLabfiles%2F07-exercise-add-to-index-use-push-api%20lab-files%2Fazuredeploy.json">توزيع الموارد إلى Azure</a> - حدد هذا الارتباط لإنشاء موارد الذكاء الاصطناعي في Azure.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/07-media/deploy-azure-resources.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/07-media/deploy-azure-resources.png" alt='لقطة شاشة للخيارات المعروضة عند توزيع الموارد إلى Azure.'></a></p>
    <li>في <b>Resource group</b>، حدد <b>Create new</b>، وبادر بتسميته <b>cog-search-language-exe</b>.</li>
    <li>في <b>Region</b>، حدد <a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/azure/ai-services/language-service/custom-text-classification/service-limits#regional-availability">supported region</a> القريبة من منطقتك.</li>
    <li>يجب أن تكون <b>بادئة المورد</b> فريدة بشكل عام، أدخل بادئة حرف رقمية وأحرف صغيرة عشوائية، على سبيل المثال، <b>acs118245</b>.</li>
    <li>في <b>Location</b>، حدد نفس المنطقة التي اخترتها أعلاه.</li>
    <li>حدد "<b>Review + create</b>".</li>
    <li>حدد <b>إنشاء</b>.</li>
    <li>عند انتهاء النشر، حدد <b>الانتقال إلى مجموعة الموارد</b> لرؤية كافة الموارد التي أنشأتها.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/07-media/azure-resources-created.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/07-media/azure-resources-created.png" alt='لقطة شاشة تعرض جميع موارد Azure الموزعة.'></a></p>
</ol>


## نسخ معلومات واجهة برمجة تطبيقات REST الخاصة بخدمة بحث الذكاء الاصطناعي في Azure

<ol dir='rtl'>
    <li>في قائمة الموارد، حدد خدمة البحث التي أنشأتها. في المثال أعلاه <b>acs118245-search-service</b>.</li>
    <li>انسخ اسم خدمة البحث في ملف نصي.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/07-media/search-api-keys-exercise-version.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/07-media/search-api-keys-exercise-version.png" alt='لقطة شاشة للقسم "keys " لخدمة بحث.'></a></p>
    <li>على اليسار، حدد <b>Keys</b>، ثم انسخ <b>مفتاح المسؤول الأساسي</b> في نفس الملف النصي.</li>
</ol>


## نسخ المستودع إلى Cloud Shell

ستقوم بتطوير التعليمات البرمجية الخاصة بك باستخدام Cloud Shell من بوابة Azure. تم توفير ملفات التعليمات البرمجية لتطبيقك في GitHub repo.

> <b>تلميح</b>: إذا كنت قد استنسخت بالفعل مستودع <b>mslearn-knowledge-mining</b> مؤخرًا، فيمكنك تخطي هذه المهمة. وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة تطويرك.

<ol dir='rtl'>
    <li>
        <p>في بوابة Azure، استخدم الزر <b>[\>_]</b> على يمين شريط البحث أعلى الصفحة لإنشاء Cloud Shell جديد في بوابة Azure، وتحديد بيئة <b><i>PowerShell</i></b>. يوفّر Cloud Shell واجهة سطر أوامر في جزء أسفل بوابة Azure.</p>
        <blockquote><b>ملاحظة</b>: إذا كنت قد أنشأت مسبقًا Cloud Shell يستخدم بيئة <i>معالج Bash</i>، فبدّل إلى <b><i>PowerShell</i></b>.</blockquote>
    </li>
    <li>
        <p>في شريط أدوات Cloud Shell، في قائمة <b>الإعدادات</b>، حدد <b>الانتقال إلى الإصدار الكلاسيكي</b> (هذا مطلوب لاستخدام محرر التعليمات البرمجية).</p>
        <blockquote><b>تلميح</b>: عند لصق الأوامر في CloudShell، قد يشغل الإخراج مساحة كبيرة من ذاكرة التخزين المؤقت للشاشة. يمكنك مسح الشاشة عن طريق إدخال الأمر <code>cls</code> لتسهيل التركيز على كل مهمة.</blockquote>
    </li>
    <li>
        <p>في جزء PowerShell، أدخل الأوامر التالية لاستنساخ مستودع GitHub لهذا التمرين:</p>
    </li>
        <div style="text-align: left; direction: ltr; margin: 0 20px;">
        <pre><code>rm -r mslearn-knowledge-mining -f
git clone https://github.com/microsoftlearning/mslearn-knowledge-mining mslearn-knowledge-mining</code></pre>
        </div>
    <li>
        <p>بعد استنساخ مخزن بيانات خاصة، انتقل إلى المجلد الذي يحتوي على ملفات التعليمات البرمجية لتطبيق الدردشة:  </p>
    </li>
        <div style="text-align: left; direction: ltr; margin: 0 20px;">
        <pre><code>cd mslearn-knowledge-mining/Labfiles/07-exercise-add-to-index-use-push-api/OptimizeDataIndexing</code></pre>
        </div>
</ol>



## إعداد التطبيق الخاص بك

<ol dir='rtl'>
    <li>باستخدام الأمر <code>ls</code>، يمكنك عرض محتويات المجلد <b>OptimizeDataIndexing</b>. لاحظ أنه يحتوي على ملف <code>appsettings.json</code> لإعدادات التكوين.</li>
    <li>
        <p>أدخل الأمر التالي لتحرير ملف التكوين الذي تم توفيره:</p>
    </li>
        <div style="text-align: left; direction: ltr; margin: 0 20px;">
        <pre><code>code appsettings.json</code></pre>
        </div>
        <p>يتم فتح الملف في محرر التعليمات البرمجية.</p>
        <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/07-media/update-app-settings.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/07-media/update-app-settings.png" alt='لقطة شاشة تعرض محتويات ملف appsettings.json.'></a></p>
    <li>
        <p>الصق اسم خدمة البحث ومفتاح المسؤول الأساسي لديك.</p>
    </li>
        <div style="text-align: left; direction: ltr; margin: 0 20px;">
        <pre><code>{
    "SearchServiceUri": "https://acs118245-search-service.search.windows.net",
    "SearchServiceAdminApiKey": "YOUR_SEARCH_SERVICE_KEY",
    "SearchIndexName": "optimize-indexing"
}</code></pre>
        </div>  
        <p>يجب أن يبدو ملف الإعدادات مشابهاً لما هو موضح أعلاه.</p>
    <li>بعد استبدال العناصر النائبة، استخدم الأمر <b>CTRL+S</b> لحفظ التغييرات ثم استخدم الأمر <b>CTRL+Q</b> لإغلاق محرر التعليمات البرمجية مع إبقاء سطر أوامر Cloud Shell مفتوحWا.</li>
    <li>
        <p>في الوحدة الطرفية، أدخل <code>dotnet run</code> واضغط على <b>Enter</b>.</p>
        <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/07-media/debug-application.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/07-media/debug-application.png" alt='لقطة شاشة تعرض التطبيق قيد التشغيل في VS Code مع استثناء.'></a></p>
        <p>يوضح الناتج أنه في هذه الحالة، يكون حجم الدفعة الأفضل أداءً هو 900 مستند بأعلى معدل نقل (ميغابايت/ثانية).</p>
        <blockquote><b>ملاحظة</b>: قد تختلف قيم معدل النقل لديك عما هو موضح في لقطة الشاشة. ومع ذلك، يجب أن يظل حجم الدفعة الأفضل أداءً هو نفسه. </blockquote>
    </li>
</ol>


## تحرير التعليمات البرمجية لتنفيذ مؤشر الترابط واستراتيجية التراجع وإعادة المحاولة

هناك تعليمة برمجية تم تعطيلها بالتحويل إلى تعليق وهي جاهزة لتغيير التطبيق لاستخدام مؤشرات الترابط لتحميل المستندات إلى فهرس البحث.

<ol dir='rtl'>
    <li>
        <p>أدخل الأمر التالي لفتح ملف التعليمات البرمجية لتطبيق العميل:</p>
    </li>
        <div style="text-align: left; direction: ltr; margin: 0 20px;">
        <pre><code>code Program.cs</code></pre>
        </div>
    <li>
        <p>علق على السطرين 38 و 39 هكذا:</p>
    </li>
        <div style="text-align: left; direction: ltr; margin: 0 20px;">
        <pre><code>//Console.WriteLine("{0}", "Finding optimal batch size...\n");
//await TestBatchSizesAsync(searchClient, numTries: 3);</code></pre>
</      </div>
    <li>
        <p>أسطر إلغاء التعليق من 41 إلى 49.</p>
    </li>
        <div style="text-align: left; direction: ltr; margin: 0 20px;">
        <pre><code>long numDocuments = 100000;
DataGenerator dg = new DataGenerator();
List<Hotel> hotels = dg.GetHotels(numDocuments, "large");
<br>
Console.WriteLine("{0}", "Uploading using exponential backoff...\n");
await ExponentialBackoff.IndexDataAsync(searchClient, hotels, 1000, 8);
<br>
Console.WriteLine("{0}", "Validating all data was indexed...\n");
await ValidateIndexAsync(indexClient, indexName, numDocuments);</code></pre>
        </div>
        <p>التعليمات البرمجية التي تتحكم في حجم الدُفعة وعدد مؤشرات الترابط هي <code>await ExponentialBackoff.IndexDataAsync(searchClient, hotels, 1000, 8)</code>. حجم الدُفعة هو 1000 ومؤشرات الترابط ثمانية.</p>
        <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/07-media/thread-code-ready.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/07-media/thread-code-ready.png" alt='لقطة شاشة تعرض جميع التعليمات البرمجية التي تم تحريرها.'></a></p>
        <p>ينبغي أن تبدو تعليماتك البرمجية كما هو موضح أعلاه.</p>
    <li>احفظ تغييراتك.</li>
    <li>حدد المحطة الطرفية، ثم اضغط على أي مفتاح لإنهاء عملية التشغيل إذا لم تكن قد نفذت ذلك بالفعل.</li>
    <li>
        <p>شغّل <code>dotnet run</code> في المحطة.</p>
        <p>سيبدأ التطبيق ثمانية مؤشرات ترابط، ثم مع انتهاء كل مؤشر ترابط من كتابة رسالة جديدة إلى وحدة التحكم:</p>
    </li>
        <div style="text-align: left; direction: ltr; margin: 0 20px;">
        <pre><code>Finished a thread, kicking off another...
Sending a batch of 1000 docs starting with doc 57000...</code></pre>
        </div>
        <p>بعد تحميل 100,000 مستند، يكتب التطبيق ملخصاً (قد يستغرق هذا بعض الوقت ليكتمل):</p>
        <div style="text-align: left; direction: ltr; margin: 0 20px;">
        <pre><code>Ended at: 9/1/2023 3:25:36 PM
<br>
Upload time total: 00:01:18:0220862
Upload time per batch: 780.2209 ms
Upload time per document: 0.7802 ms
<br>
Validating all data was indexed...
<br>
Waiting for service statistics to update...
<br>
Document Count is 100000
<br>
Waiting for service statistics to update...
<br>
Index Statistics: Document Count is 100000
Index Statistics: Storage Size is 71453102</code></pre>
    </div>
    <p>استكشف التعليمات البرمجية في الإجراء <code>TestBatchSizesAsync</code> لمعرفة كيفية اختبار التعليمات البرمجية لأداء حجم الدُفعة.</p>
    <p>استكشف التعليمات البرمجية في الإجراء <code>IndexDataAsync</code> لمعرفة كيفية إدارة التعليمات البرمجية لمؤشرات الترابط.</p>
    <p>استكشف التعليمات البرمجية في <code>ExponentialBackoffAsync</code> لمعرفة كيفية تنفيذ التعليمات البرمجية لاستراتيجية إعادة محاولة التراجع المطرد.</p>
    <p>يمكنك البحث والتحقق من إضافة المستندات إلى الفهرس في مدخل Azure.</p>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/07-media/check-search-service-index.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/07-media/check-search-service-index.png" alt='لقطة شاشة تعرض فهرس البحث مع 100000 مستند.'></a></p>
</ol>


## التنظيف

الآن بعد أن أكملت التمرين، احذف جميع الموارد التي لم تعد بحاجة إليها. ابدأ بالتعليمة البرمجية المستنسخة إلى جهازك. ثم احذف موارد Azure.

<ol dir='rtl'>
    <li>في <b>مدخل Azure</b>، حدد "Resource groups".</li>
    <li>حدد مجموعة الموارد التي أنشأتها لهذا التمرين.</li>
    <li>حدد <b>Delete resource group</b>. </li>
    <li>أكد الحذف ثم حدد <b>حذف</b>.</li>
    <li>حدد الموارد التي لا تحتاج إليها، ثم حدد <b>Delete</b>.</li>
</ol>

