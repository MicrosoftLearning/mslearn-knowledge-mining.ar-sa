---
lab:
  title: إضافة إلى فهرس باستخدام واجهة برمجة تطبيقات الدفع
---

# إضافة إلى فهرس باستخدام واجهة برمجة تطبيقات الدفع

تريد استكشاف كيفية إنشاء فهرس بحث الذكاء الاصطناعي في Azure وتحميل المستندات إلى هذا الفهرس باستخدام التعليمات البرمجية C#.

في هذا التمرين، ستستنسخ حل C# موجود وتشغله للعمل على الحجم الأمثل للدُفعة لتحميل المستندات. ثم ستستخدم حجم الدُفعة هذا وتحميل المستندات بفعاليةٍ باستخدام نهج مؤشر ترابط.

> **ملاحظة**: لإكمال هذا التمرين، ستحتاج إلى اشتراك Microsoft Azure. إذا لم يكن لديك اشتراك بالفعل، يمكنك التسجيل للحصول على الإصدار التجريبي على [https://azure.com/free](https://azure.com/free?azure-portal=true) .

## إعداد موارد Azure الخاص بك

لتوفير وقتك، حدد قالب Azure Resource Manager هذا لإنشاء الموارد التي ستحتاج إليها لاحقاً في التمرين:

1. [توزيع الموارد إلى Azure](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FMicrosoftLearning%2Fmslearn-knowledge-mining%2Fmain%2FLabfiles%2F07-exercise-add-to-index-use-push-api%2Fazuredeploy.json) - حدد هذا الارتباط لإنشاء موارد الذكاء الاصطناعي في Azure.
    ![لقطة شاشة للخيارات المعروضة عند توزيع الموارد إلى Azure.](../media/07-media/deploy-azure-resources.png)
1. في **Resource group**، حدد **Create new**، وبادر بتسميته **cog-search-language-exe**.
1. في **Region**، حدد [supported region](/azure/ai-services/language-service/custom-text-classification/service-limits#regional-availability) القريبة من منطقتك.
1. يجب أن تكون **بادئة المورد** فريدة بشكل عام، أدخل بادئة حرف رقمية وأحرف صغيرة عشوائية، على سبيل المثال، **acs118245**.
1. في **Location**، حدد نفس المنطقة التي اخترتها أعلاه.
1. حدد "**Review + create**".
1. حدد **إنشاء**.
1. عند انتهاء النشر، حدد **الانتقال إلى مجموعة الموارد** لرؤية كافة الموارد التي أنشأتها.

    ![لقطة شاشة تعرض جميع موارد Azure الموزعة.](../media/07-media/azure-resources-created.png)

## نسخ معلومات واجهة برمجة تطبيقات REST الخاصة بخدمة بحث الذكاء الاصطناعي في Azure

1. في قائمة الموارد، حدد خدمة البحث التي أنشأتها. في المثال أعلاه **acs118245-search-service**.
1. انسخ اسم خدمة البحث في ملف نصي.

    ![لقطة شاشة للقسم "keys " لخدمة بحث.](../media/07-media/search-api-keys-exercise-version.png)
1. على اليسار، حدد **Keys**، ثم انسخ **مفتاح المسؤول الأساسي** في نفس الملف النصي.

## نسخ المستودع إلى Cloud Shell

ستقوم بتطوير التعليمات البرمجية الخاصة بك باستخدام Cloud Shell من بوابة Azure. تم توفير ملفات التعليمات البرمجية لتطبيقك في GitHub repo.

> **تلميح**: إذا كنت قد استنسخت بالفعل مستودع **mslearn-knowledge-mining** مؤخرًا، فيمكنك تخطي هذه المهمة. وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة تطويرك.

1. في بوابة Azure، استخدم الزر **[\>_]** على يمين شريط البحث أعلى الصفحة لإنشاء Cloud Shell جديد في بوابة Azure، وتحديد بيئة ***PowerShell***. يوفّر Cloud Shell واجهة سطر أوامر في جزء أسفل بوابة Azure.

    > **ملاحظة**: إذا كنت قد أنشأت مسبقًا Cloud Shell يستخدم بيئة *معالج Bash*، فبدّل إلى ***PowerShell***.

1. في شريط أدوات Cloud Shell، في قائمة **الإعدادات**، حدد **الانتقال إلى الإصدار الكلاسيكي** (هذا مطلوب لاستخدام محرر التعليمات البرمجية).

    > **تلميح**: عند لصق الأوامر في CloudShell، قد يشغل الإخراج مساحة كبيرة من ذاكرة التخزين المؤقت للشاشة. يمكنك مسح الشاشة عن طريق إدخال الأمر `cls` لتسهيل التركيز على كل مهمة.

1. في جزء PowerShell، أدخل الأوامر التالية لاستنساخ مستودع GitHub لهذا التمرين:

    ```
    rm -r mslearn-knowledge-mining -f
    git clone https://github.com/microsoftlearning/mslearn-knowledge-mining mslearn-knowledge-mining
    ```

1. بعد استنساخ مخزن بيانات خاصة، انتقل إلى المجلد الذي يحتوي على ملفات التعليمات البرمجية لتطبيق الدردشة:  

    ```
   cd mslearn-knowledge-mining/Labfiles/07-exercise-add-to-index-use-push-api/OptimizeDataIndexing
    ```

## إعداد التطبيق الخاص بك

1. باستخدام الأمر `ls`، يمكنك عرض محتويات المجلد **OptimizeDataIndexing**. لاحظ أنه يحتوي على ملف `appsettings.json` لإعدادات التكوين.

1. أدخل الأمر التالي لتحرير ملف التكوين الذي تم توفيره:

    ```
   code appsettings.json
    ```

    يتم فتح الملف في محرر التعليمات البرمجية.

    ![لقطة شاشة تعرض محتويات ملف appsettings.json.](../media/07-media/update-app-settings.png)

1. الصق اسم خدمة البحث ومفتاح المسؤول الأساسي لديك.

    ```json
    {
      "SearchServiceUri": "https://acs118245-search-service.search.windows.net",
      "SearchServiceAdminApiKey": "YOUR_SEARCH_SERVICE_KEY",
      "SearchIndexName": "optimize-indexing"
    }
    ```

    يجب أن يبدو ملف الإعدادات مشابهاً لما هو موضح أعلاه.
   
1. بعد استبدال العناصر النائبة، استخدم الأمر **CTRL+S** لحفظ التغييرات ثم استخدم الأمر **CTRL+Q** لإغلاق محرر التعليمات البرمجية مع إبقاء سطر أوامر Cloud Shell مفتوحWا.
1. في الوحدة الطرفية، أدخل `dotnet run` واضغط على **Enter**.

    ![لقطة شاشة تعرض التطبيق قيد التشغيل في VS Code مع استثناء.](../media/07-media/debug-application.png)

    يوضح الناتج أنه في هذه الحالة، يكون حجم الدفعة الأفضل أداءً هو 900 مستند بأعلى معدل نقل (ميغابايت/ثانية).
   
    >**ملاحظة**: قد تختلف قيم معدل النقل لديك عما هو موضح في لقطة الشاشة. ومع ذلك، يجب أن يظل حجم الدفعة الأفضل أداءً هو نفسه. 

## تحرير التعليمات البرمجية لتنفيذ مؤشر الترابط واستراتيجية التراجع وإعادة المحاولة

هناك تعليمة برمجية تم تعطيلها بالتحويل إلى تعليق وهي جاهزة لتغيير التطبيق لاستخدام مؤشرات الترابط لتحميل المستندات إلى فهرس البحث.

1. أدخل الأمر التالي لفتح ملف التعليمات البرمجية لتطبيق العميل:

    ```
   code Program.cs
    ```

1. علق على السطرين 38 و 39 هكذا:

    ```csharp
    //Console.WriteLine("{0}", "Finding optimal batch size...\n");
    //await TestBatchSizesAsync(searchClient, numTries: 3);
    ```

1. أسطر إلغاء التعليق من 41 إلى 49.

    ```csharp
    long numDocuments = 100000;
    DataGenerator dg = new DataGenerator();
    List<Hotel> hotels = dg.GetHotels(numDocuments, "large");

    Console.WriteLine("{0}", "Uploading using exponential backoff...\n");
    await ExponentialBackoff.IndexDataAsync(searchClient, hotels, 1000, 8);

    Console.WriteLine("{0}", "Validating all data was indexed...\n");
    await ValidateIndexAsync(indexClient, indexName, numDocuments);
    ```

    التعليمات البرمجية التي تتحكم في حجم الدُفعة وعدد مؤشرات الترابط هي `await ExponentialBackoff.IndexDataAsync(searchClient, hotels, 1000, 8)`. حجم الدُفعة هو 1000 ومؤشرات الترابط ثمانية.

    ![لقطة شاشة تعرض جميع التعليمات البرمجية التي تم تحريرها.](../media/07-media/thread-code-ready.png)

    ينبغي أن تبدو تعليماتك البرمجية كما هو موضح أعلاه.

1. احفظ تغييراتك.
1. حدد المحطة الطرفية، ثم اضغط على أي مفتاح لإنهاء عملية التشغيل إذا لم تكن قد نفذت ذلك بالفعل.
1. شغّل `dotnet run` في المحطة.

    سيبدأ التطبيق ثمانية مؤشرات ترابط، ثم مع انتهاء كل مؤشر ترابط من كتابة رسالة جديدة إلى وحدة التحكم:

    ```powershell
    Finished a thread, kicking off another...
    Sending a batch of 1000 docs starting with doc 57000...
    ```

    بعد تحميل 100,000 مستند، يكتب التطبيق ملخصاً (قد يستغرق هذا بعض الوقت ليكتمل):

    ```powershell
    Ended at: 9/1/2023 3:25:36 PM
    
    Upload time total: 00:01:18:0220862
    Upload time per batch: 780.2209 ms
    Upload time per document: 0.7802 ms
    
    Validating all data was indexed...
    
    Waiting for service statistics to update...
    
    Document Count is 100000
    
    Waiting for service statistics to update...
    
    Index Statistics: Document Count is 100000
    Index Statistics: Storage Size is 71453102
    
    ``````

استكشف التعليمات البرمجية في الإجراء `TestBatchSizesAsync` لمعرفة كيفية اختبار التعليمات البرمجية لأداء حجم الدُفعة.

استكشف التعليمات البرمجية في الإجراء `IndexDataAsync` لمعرفة كيفية إدارة التعليمات البرمجية لمؤشرات الترابط.

استكشف التعليمات البرمجية في `ExponentialBackoffAsync` لمعرفة كيفية تنفيذ التعليمات البرمجية لاستراتيجية إعادة محاولة التراجع المطرد.

يمكنك البحث والتحقق من إضافة المستندات إلى الفهرس في مدخل Azure.

![لقطة شاشة تعرض فهرس البحث مع 100000 مستند.](../media/07-media/check-search-service-index.png)

## التنظيف

الآن بعد أن أكملت التمرين، احذف جميع الموارد التي لم تعد بحاجة إليها. ابدأ بالتعليمة البرمجية المستنسخة إلى جهازك. ثم احذف موارد Azure.

1. في **مدخل Azure**، حدد "Resource groups".
1. حدد مجموعة الموارد التي أنشأتها لهذا التمرين.
1. حدد **Delete resource group**. 
1. أكد الحذف ثم حدد **حذف**.
1. حدد الموارد التي لا تحتاج إليها، ثم حدد **Delete**.
