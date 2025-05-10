---
lab:
  title: إثراء فهرس بحث الذكاء الاصطناعي مع فئات مخصصة
---

# إثراء فهرس بحث الذكاء الاصطناعي مع فئات مخصصة

أنشئت حل بحث وتريد الآن إضافة خدمات الذكاء الاصطناعي في Azure لإثراء اللغة إلى الفهارس الخاصة بك.

في هذا التمرين، ستنشئ حل بحث الذكاء الاصطناعي في Azure وتثري الفهرس بالنتائج من مشروع تصنيف نص مخصص في Language Studio. ستقوم بإنشاء تطبيق وظائف لتوصيل نموذج البحث والتصنيف معاً.

> <b>ملاحظة</b>: لإكمال هذا التمرين، ستحتاج إلى اشتراك Microsoft Azure. إذا لم يكن لديك اشتراك بالفعل، يمكنك التسجيل للحصول على الإصدار التجريبي على [https://azure.com/free](https://azure.com/free?azure-portal=true) .

## إعداد بيئة التطوير الخاصة بك باستخدام ملحقات Python وVS Code

قم بتثبيت هذه الأدوات لإكمال هذا التمرين. لا يزال بإمكانك المتابعة مع الخطوات دون هذه الأدوات.

<ol dir='rtl'>
    <li>تثبيت <a href="https://code.visualstudio.com/">VS Code</a></li>
    <li>تثبيت <a href="https://github.com/Azure/azure-functions-core-tools">Azure Core Functions Tool</a></li>
    <li>ثبيت <a href="https://code.visualstudio.com/docs/azure/extensions">ملحقات أدوات Azure لـ VSCode</a></li>
    <li>تثبيت <a href="https://www.python.org/downloads/release/python-380/">Python 3.8</a> لنظام التشغيل الخاص بك.</li>
    <li>تثبيت <a href="https://marketplace.visualstudio.com/items?itemName=ms-python.python">ملحقات Python لـ VSCode</a></li>
</ol>


## إعداد موارد Azure الخاص بك

لتوفير وقتك، حدد قالب Azure ARM هذا لإنشاء الموارد التي ستحتاجها لاحقاً في التمرين.

### توزيع قالب ARM تم إنشاؤه مسبقاً

<ol dir='rtl'>
    <li>
        <p dir="auto"><a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FMicrosoftLearning%2Fmslearn-knowledge-mining%2Fmain%2FLabfiles%2F04-enrich-custom-classes%2Fazuredeploy.json" rel="nofollow"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/deploy-azure.svg" alt="نشر إلى Azure." style="max-width: 100%;"></a> تحديد هذا الارتباط لإنشاء موارد البداية. قد تحتاج إلى نسخ <a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FMicrosoftLearning%2Fmslearn-knowledge-mining%2Fmain%2FLabfiles%2F04-enrich-custom-classes%2Fazuredeploy.json" rel="nofollow">الارتباط المباشر</a> ولصقه في شريط البحث.</p>
        <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/deploy-azure-resources.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/deploy-azure-resources.png" alt="لقطة شاشة للخيارات المعروضة عند توزيع الموارد إلى Azure."></a></p>
    </li>
    <li>في <b>Resource group</b>، حدد <b>Create new</b>، وبادر بتسميته <b>cog-search-language-exe</b>.</li>
    <li>في <b>Region</b>، حدد <a href="https://learn.microsoft.com/azure/ai-services/language-service/concepts/regional-support">supported region</a> القريبة من منطقتك.</li>
    <li>يجب أن تكون <b>بادئة المورد</b> فريدة بشكل عام، أدخل بادئة حرف رقمية وأحرف صغيرة عشوائية، على سبيل المثال <b>acs18245</b>.</li>
    <li>في <b>Location</b>، حدد نفس المنطقة التي اخترتها أعلاه.</li>
    <li>حدد "<b>Review + create</b>".</li>
    <li>حدد <b>إنشاء</b>.</li>
    <blockquote><b>ملاحظة</b> يوجد خطأ موضح، <b>ستحتاج إلى الموافقة على شروط الخدمة أدناه لإنشاء هذا المورد بنجاح.</b>، بتحديد <b>إنشاء</b> فإنك توافق عليها.</blockquote>
    <li>حدد <b>Go to resource group</b> للاطلاع على جميع الموارد التي أنشأتها.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/azure-resources-created.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/azure-resources-created.png" alt="لقطة شاشة للموارد المنشورة."></a></p>
</ol>


ستقوم بإعداد فهرس Azure Cognitive Search، وإنشاء دالة Azure، وإنشاء مشروع Language Studio لتحديد أنواع الأفلام من ملخصاتها.

### تحميل عينة من البيانات لتدريب خدمات اللغات

يستخدم هذا التمرين 210 ملفاً نصياً يحتوي على ملخص رسم لفيلم. اسم الملفات النصية هو عنوان الفيلم. يحتوي المجلد أيضاً على ملف <b>movieLabels.json</b> الذي يعين أنواع الفيلم إلى الملف، لكل ملف يوجد إدخال JSON مثل هذا:

```json
{
    "location": "And_Justice_for_All.txt",
    "language": "en-us",
    "classifiers": [
        {
            "classifierName": "Mystery"
        },
        {
            "classifierName": "Drama"
        },
        {
            "classifierName": "Thriller"
        },
        {
            "classifierName": "Comedy"
        }
    ]
},
```
<ol dir='rtl'>
    <li>انتقل إلى <b>Labfiles/04-enrich-custom-classes</b> واستخرج مجلد <b>movies summary.zip</b> الذي يحتوي على جميع الملفات.</li>
    <blockquote><b>ملاحظة</b> يمكنك استخدام هذه الملفات لتدريب نموذج في Language Studio، كما ستقوم أيضًا بفهرسة جميع الملفات في بحث الذكاء الاصطناعي في Azure.</blockquote>
    <li>في <a href="https://portal.azure.com/">مدخل Azure</a>، حدد <b>مجموعات الموارد</b> ثم حدد مجموعة الموارد.</li>
    <li>حدد حساب التخزين الذي أنشأته، على سبيل المثال <b>acs18245str</b>.</li>
    <li>حدد <b>التكوين</b> من الجزء الأيمن، وحدد خيار <b>تمكين</b> لإعداد <i>السماح بالوصول المجهول إلى الكائن الثنائي كبير الحجم</i> ثم حدد <b>حفظ</b> في أعلى الصفحة.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/select-azure-blob-storage.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/select-azure-blob-storage.png" alt="لقطة شاشة تعرض كيفية إنشاء حاوية تخزين جديدة."></a></p>
    <li>حدد <b>حاويات</b> من اليسار، ثم حدد <b>حاويات +</b>.</li>
    <li>في جزء <b>New container</b> في <b>Name</b>، أدخل <b>language-studio-training-data</b>.</li>
    <li>في <b>مستوى الوصول المجهول</b>، اختر <b>الحاوية (وصول مجهول للقراءة للحاويات والكائنات الثنائية الكبيرة)</b> وحدد <b>إنشاء</b>.</li>
    <li>حدد الحاوية الجديدة التي قمت بإنشائها للتو، <b>language-studio-training-data</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/upload-files.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/upload-files.png" alt="لقطة شاشة لتحميل الملفات في الحاوية."></a></p>
    <li>حدد <b>Upload</b> في أعلى الجزء.</li>
    <li>في جزء <b>تحميل كائن ثنائي كبير الحجم</b> وحدد <b>استعراض للملفات</b>.</li>
    <li>انتقل إلى المكان الذي استخرجت الملفات النموذجية فيه، وحدد جميع الملفات النصية (<code>.txt</code>) وjson (<code>.json</code>).</li>
    <li>حدد <b>Upload</b> في الجزء.</li>
    <li>أغلق الجزء <b>Upload blob</b>.</li>
</ol>


### إنشاء مورد اللغة

<ol dir='rtl'>
    <li>في ارتباط العناوين في أعلى الصفحة، حدد <b>الصفحة الرئيسية</b>.</li>
    <li>حدد <b>+ إنشاء مورد</b> وابحث عن <i>خدمة اللغة</i>.</li>
    <li>حدد <b>إنشاء</b> ضمن <b>خدمة اللغة</b>.</li>
    <li>حدد الخيار الذي يتضمن <b>تصنيف النص المخصص والتعرّف على الكيانات المسماة المخصصة</b>.</li>
    <li>حدد <b>Continue to create your resource</b>.</li>
    <li>في <b>Resource group</b>، اختر <b>cog-search-language-exe</b>.</li>
    <li>في <b>Region</b>، حدد المنطقة التي استخدمتها أعلاه.</li>
    <li>في <b>Name</b>، أدخل <b>learn-language-service-for-custom-text</b>. يجب أن يكون هذا فريداً عالمياً، لذلك قد تحتاج إلى إضافة أرقام أو أحرف عشوائية في نهايتها.</li>
    <li>في مستوى <b>Pricing</b>، حدد <b>S</b>.</li>
    <li>في <b>New/Existing storage account</b>، حدد <b>Existing storage account</b>.</li>
    <li>في <b>حساب التخزين في منطقة الاشتراك والموارد المحددة حالياً</b>، حدد حساب التخزين الذي قمت بإنشائه، على سبيل المثال <b>acs18245str</b>.</li>
    <li>وافق على شروط <b>إشعار الذكاء الاصطناعي المسؤول</b>، ثم حدد <b>Review + create</b>.</li>
    <li>حدد <b>إنشاء</b>.</li>
    <li>انتظر حتى يتم توزيع الموارد، ثم حدد <b>Go to resource group</b>.</li>
    <li>حدد <b>learn-language-service-for-custom-text</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/started-language-studio.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/started-language-studio.png" alt="لقطة شاشة توضح مكان التحديد لبدء تشغيل Language Studio."></a></p>
    <li>مرر لأسفل في جزء <b>Overview</b>، وحدد <b>Get started with Language Studio</b>.</li>
    <li>سجل الدخول في language studio. إذا جرت مطالبتك باختيار مورد لغة، فحدد المورد الذي أنشأتها مسبقاً.</li>
</ol>


### إنشاء مشروع تصنيف نص مخصص في Language Studio

<ol dir='rtl'>
    <li>في الصفحة الرئيسية لـ Language Studio، حدد <b>Create new</b>، ثم حدد <b>Custom text classification</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/create-custom-text-classification-project.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/create-custom-text-classification-project.png" alt="لقطة شاشة توضح كيفية تحديد إنشاء مشروع تصنيف نص مخصص جديد."></a></p>
    <li>حدد <b>التالي</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/select-project-type.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/select-project-type.png" alt="لقطة شاشة تعرض نوع مشروع تصنيف متعدد التسميات المحدد."></a></p>
    <li>حدد <b>Multi label classification</b>، ثم حدد <b>Next</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/enter-basic-information.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/enter-basic-information.png" alt="لقطة شاشة تعرض المعلومات الأساسية لمشروع ما."></a></p>
    <li>في <b>Name</b>، أدخل <b>movie-genre-classifier</b>.</li>
    <li>في <b>Text primary language</b>، حدد <b>English (US)</b>.</li>
    <li>حدد <b>نعم، تمكين مجموعة البيانات متعددة اللغات</b>.</li>
    <li>في <b>Description</b>، أدخل <b>نموذجاً يمكنه تحديد نوع فيلم من الملخص</b>.</li>
    <li>حدد <b>التالي</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/choose-container.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/choose-container.png" alt="لقطة شاشة تظهر تحديد الحاوية مع عينة من البيانات فيها."></a></p>
    <li>في <b>Blob storage container</b>، اختر <b>language-studio-training-data</b>.</li>
    <li>حدد <b>نعم، تمت تسمية مستنداتي بالفعل ولدي ملف تسميات JSON منسق بشكل صحيح</b>.</li>
    <li>في <b>Label documents</b>، اختر <b>movieLabels</b>.</li>
    <li>حدد <b>التالي</b>.</li>
    <li>حدد <b>إنشاء مشروع</b></li>
</ol>



### تدريب نموذج الذكاء الاصطناعي لتصنيف النص المخصص الخاص بك

<ol dir='rtl'>
    <li>على اليسار، حدد <b>Training jobs</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/train-jobs.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/train-jobs.png" alt="لقطة شاشة توضح كيفية إنشاء مهمة التدريب."></a></p>
    <li>حدد <b>+ Start a training job</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/start-training-job.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/start-training-job.png" alt="لقطة شاشة تعرض المعلومات اللازمة لإنشاء مهمة تدريب."></a></p>
    <li>في <b>Train a new modal</b>، أدخل <b>movie-genre-classifier</b>.</li>
    <li>حدد <b>تدريب</b>.</li>
    <li>يجب أن يستغرق تدريب نموذج المصنف أقل من 10 دقائق. انتظر حتى تتغير الحالة إلى <b>نجح التدريب</b>.</li>
</ol>

### توزيع نموذج الذكاء الاصطناعي لتصنيف النص المخصص الخاص بك

<ol dir='rtl'>
    <li>على اليسار، حدد <b>Deploying a model</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/deploy-model.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/deploy-model.png" alt="لقطة شاشة توضح كيفية نشر نموذج."></a></p>
    <li>حدد <b>Add a deployment</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/add-deployment.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/add-deployment.png" alt="لقطة شاشة تعرض المعلومات اللازمة لنشر نموذج."></a></p>
    <li>في <b>Create a new deployment name</b>، أدخل <b>test-release</b>.</li>
    <li>في <b>Model</b>، حدد <b>movie-genre-classifier</b>.</li>
    <li>حدد <b>نشر</b>.</li>
</ol>

اترك صفحة الويب هذه مفتوحة لاحقاً في هذا التمرين.

### إنشاء فهرس كلمات بحث الذكاء الاصطناعي في Azure

أنشئ فهرس بحث يمكنك تحسينه باستخدام هذا النموذج، وستقوم بفهرسة جميع الملفات النصية التي تحتوي على ملخصات الأفلام التي قمت بتنزيلها بالفعل.

<ol dir='rtl'>
    <li>في <a href="https://portal.azure.com/">مدخل Azure</a>، حدد <b>مجموعات الموارد</b>، وحدد مجموعة الموارد الخاصة بك، ثم حدد حساب التخزين الذي أنشأته على سبيل المثال <b>acs18245str</b>.</li>
    <li>حدد <b>حاويات</b> من اليسار، ثم حدد <b>حاويات +</b>.</li>
    <li>في جزء <b>New container</b> في <b>Name</b>، أدخل <b>search-data</b>.</li>
    <li>في <b>مستوى الوصول المجهول</b>، اختر <b>الحاوية</b>.</li>
    <li>حدد <b>إنشاء</b>.</li>
    <li>حدد الحاوية الجديدة التي قمت بإنشائها للتو <b>search-data</b>.</li>
    <li>حدد <b>Upload</b> في أعلى الجزء.</li>
    <li>في جزء <b>تحميل كائن ثنائي كبير الحجم</b> وحدد <b>استعراض للملفات</b>.</li>
    <li>انتقل إلى المكان الذي قمت بتنيل ملفات العينة فيه وحدد <b>ONLY</b> الملفات النصية (<code>.txt</code>).</li>
    <li>حدد <b>Upload</b> في الجزء.</li>
    <li>أغلق الجزء <b>Upload blob</b>.</li>
</ol>


### استيراد المستندات إلى بحث الذكاء الاصطناعي في Azure

<ol dir='rtl'>
    <li>على اليمين، حدد <b>مجموعات الموارد</b>، وحدد مجموعة الموارد الخاصة بك، ثم حدد خدمة البحث لديك.</li>
    <li>حدد <b>Import data</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/connect-data.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/connect-data.png" alt="لقطة شاشة تعرض معلومات اتصال البيانات."></a></p>
    <li>في <b>Data Source</b>، حدد <b>Azure Blob Storage</b>.</li>
    <li>في <b>Data source name</b>، أدخل <b>movie-summaries</b>.</li>
    <li>حدد <b>اختيار اتصال موجود</b>، وحدد حساب التخزين الخاص بك، ثم حدد الحاوية التي أنشأتها للتو، <b>وبيانات البحث</b>.</li>
    <li>حدد <b>أضف مهارات معرفية (اختياري)</b>.</li>
    <li>يمكنك توسيع <b>قسم إرفاق خدمات الذكاء الاصطناعي</b> ثم حدد خدمة الذكاء الاصطناعي في Azure التي أنشأتها مسبقاً.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/attach-cognitive-services.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/attach-cognitive-services.png" alt="لقطة شاشة تعرض إرفاق خدمات الذكاء الاصطناعي في Azure."></a></p>
    <li>قم بتوسيع القسم <b>Add enrichments</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/add-enrichments.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/add-enrichments.png" alt="لقطة شاشة تعرض عمليات الإثراء المحدودة المحددة."></a></p>
    <li>اترك كافة الحقول بقيمها الافتراضية، ثم حدد <b>Extract people names</b>.</li>
    <li>حدد <b>Extract key phrases</b>.</li>
    <li>حدد <b>Detect language</b>.</li>
    <li>حدد <b>Next: Customize target index</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/customize-target-index.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/customize-target-index.png" alt="لقطة شاشة تعرض تخصيصات الحقول."></a></p>
    <li>اترك كافة الحقول بقيمها الافتراضية للحقل <b>metadata_storage_name</b> حدد <b>Retrievable</b> و<b>Searchable</b>.</li>
    <li>حدد <b>التالي: إنشاء مفهرس</b>.</li>
    <li>حدد <b>إرسال</b>.</li>
</ol>

سيقوم المفهرس بتشغيل وإنشاء فهرس لـ 210 ملفاً نصياً. لا تحتاج إلى الانتظار حتى يستمر في الخطوات التالية.

## إنشاء تطبيق الوظائف لإثراء فهرس البحث الخاص بك

ستقوم الآن بإنشاء تطبيق وظائف Python الذي ستستدعيه مجموعة المهارات المخصصة للبحث المعرفي. سيستخدم تطبيق الوظائف نموذج مصنف النص المخصص لإثراء فهرس البحث الخاص بك.

<ol dir='rtl'>
    <li><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining/raw/main/Labfiles/04-enrich-custom-classes/movie-genre-function.zip">تنزيل الملفات</a> يمكنك المطلوبة واستخراج المجلد الذي يحتوي على جميع الملفات.</li>
    <li>افتح تعليمة Visual Studio البرمجية وافتح مجلد <b>movie-genre-function</b> الذي نزلته للتو.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/optimize-visual-studio-code.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/optimize-visual-studio-code.png" alt="لقطة شاشة تعليمة Visual Studio برمجية تعرض مربع حوار تحسين تطبيق الوظائف."></a></p>
    <li>إذا قمت بتثبيت جميع الملحقات المطلوبة، فستتم مطالبتك بتحسين المشروع. حدد <b>نعم</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/select-python-interpreter.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/select-python-interpreter.png" alt="لقطة شاشة تعرض تحديد الإصدار 3.8 من مترجم Python."></a></p>
    <li>حدد مترجم Python الخاص بك، يجب أن يكون الإصدار 3.8.</li>
    <li>سيتم تحديث مساحة العمل، إذا تمت مطالبتك بتوصيلها بمجلد مساحة العمل، فحدد <b>Yes</b>.</li>
    <li>اضغط على <b>F5</b> لتتبع أخطاء التطبيق.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/test-function-app.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/test-function-app.png" alt="لقطة شاشة تعرض تشغيل تطبيق الوظائف."></a></p>
    <p>إذا كان التطبيق قيد التشغيل، يجب أن تشاهد عنوان URL المضيف المحلي الذي يمكنك استخدامه للاختبار المحلي.</p>
    <li>توقف عن تصحيح أخطاء التطبيق، واضغط على <b>SHIFT</b> + <b>F5</b>.</li>
</ol>


### توزيع تطبيق الوظائف المحلي إلى Azure

<ol dir='rtl'>
    <li>لفتح لوحة الأوامر في تعليمة Visual Studio البرمجية، اضغط على <b>F1</b>.</li>
    <li>في لوحة الأوامر، ابحث عن <code>Azure Functions: Create Function App in Azure...</code> واختره.</li>
    <li>قم بإدخال اسم فريد بشكل عمومي لتطبيق الوظائف الخاص بك على سبيل المثال <b>acs13245str-function-app</b>.</li>
    <li>في <b>Select a runtime stack</b>، حدد <b>Python 3.8</b>.</li>
    <li>حدد نفس الموقع الذي استخدمته سابقاً.</li>
    <li>في جزء التنقل الأيسر، حدد الملحق <b>Azure</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/deploy-function-app.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/deploy-function-app.png" alt="لقطة شاشة تعرض خيار القائمة لنشر تطبيق وظيفة إلى Azure."></a></p>
    <li>يمكنك توسيع <b>الموارد</b> وتوسيع <b>تطبيق الوظيفة</b> ضمن اشتراكك، ثم انقر بزر الماوس الأيمن على الوظيفة، على سبيل المثال <b>acs13245-function-app</b>.</li>
    <li>حدد <b>Deploy to Function App</b>. انتظر حتى يتم توزيع التطبيق.</li>
    <li>قم بتوسيع التطبيق، وانقر بزر الماوس الأيمن على <b>Application Settings</b>، ثم حدد <b>Download Remote Settings</b>.</li>
    <li>على اليسار، حدد <b>Explorer</b>، ثم حدد <b>local.settings.json</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/edit-local-settings.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/edit-local-settings.png" alt="لقطة شاشة لإعدادات تنزيل التطبيق."></a></p>
    <p>يجب أن يكون تطبيق الوظائف متصلاً بنموذج تصنيف النص المخصص. اتبع هذه الخطوات للحصول على إعدادات التكوين.</p>
    <li>في المستعرض، انتقل إلى <b>Language Studio</b>، يجب أن تكون على صفحة <b>Deploying a model</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/copy-prediction-endpoint.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/copy-prediction-endpoint.png" alt="لقطة شاشة توضِّح من أين يمكن نسخ نقطة النهاية للتنبؤ"></a></p>
    <li>تحديد النموذج الخاص بك. ثم حدد <b>الحصول على عنوان URL للتنبؤ</b>.</li>
    <li>حدد أيقونة «نسخ» بجوار <b>Prediction URL</b>.</li>
    <li>في Visual Studio Code، في أسفل <b>local.settings.json</b>، الصق عنوان URL للتنبؤ.</li>
    <li>في <b>Language Studio</b> على اليسار، حدد <b>Project settings</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/project-settings-primary-key.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/project-settings-primary-key.png" alt="لقطة شاشة توضِّح من أين يمكن نسخ المفتاح الأساسي لخدمات اللغة."></a></p>
    <li>حدد أيقون «نسخ» بجوار <b>Primary key</b>.</li>
    <li>في Visual Studio Code، في أسفل <b>local.settings.json</b>، الصق المفتاح الأساسي.</li>
    <li>قم بتحرير الإعدادات لإضافة هذه الأسطر الأربعة في الأسفل، وانسخ نقطة النهاية إلى القيمة <code>TA_ENDPOINT</code>.</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>,
"TA_ENDPOINT": " [your endpoint] ",
"TA_KEY": " [your key] ",
"DEPLOYMENT": "test-release",
"PROJECT_NAME": "movie-genre-classifier"</code></pre>
    </div>
    <li>انسخ المفتاح الأساسي إلى القيمة <code>TA_KEY</code>.</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>{
    "IsEncrypted": false,
    "Values": {
        "AzureWebJobsStorage": "DefaultEndpointsProtocol=https;AccountName=...",
        "FUNCTIONS_EXTENSION_VERSION": "~4",
        "FUNCTIONS_WORKER_RUNTIME": "python",
        "WEBSITE_CONTENTAZUREFILECONNECTIONSTRING": "DefaultEndpointsProtocol=https;AccountName=...",
        "WEBSITE_CONTENTSHARE": "acs...",
        "APPINSIGHTS_INSTRUMENTATIONKEY": "6846...",
        "TA_ENDPOINT": "https://learn-languages-service-for-custom-text.cognitiveservices.azure.com/language/analyze-text/jobs?api-version=2022-05-01",
        "TA_KEY": "7105e938ce1...",
        "DEPLOYMENT": "test-release",
        "PROJECT_NAME": "movie-genre-classifier"
    }
}</code></pre>
    </div>
    <p>يجب أن تبدو الإعدادات كما هو موضح أعلاه، مع قيم مشروعك.</p>
    <li>اضغط على <b>CTRL</b>+<b>S</b> لحفظ التغييرات الخاصة بك<b>local.settings.json</b>.</li>
    <li>في جزء التنقل الأيسر، حدد الملحق <b>Azure</b>.</li>
    <li>يمكن توسيع <b>الموارد</b>، وضمن اشتراكك، يمكن توسيع <b>تطبيق الوظائف</b>، ثم انقر بزر الماوس الأيمن على <b>إعدادات التطبيق</b>، وحدد <b>تحميل الإعدادات المحلية </b>.</li>
</ol>



### اختبار تطبيق الوظائف عن بُعد

هناك نموذج استعلام يمكنك استخدامه لاختبار أن تطبيق الوظائف ونموذج المصنف يعملان بشكل صحيح.

<ol dir='rtl'>
    <li>على اليمين، حدد <b>مستكشف</b>، ووسع المجلد <b>customtectcla</b>، ثم حدد <b>sample.dat</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/copy-sample-query.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/copy-sample-query.png" alt="لقطة شاشة تعرض نموذج استعلام JSON."></a></p>
    <li>نسخ محتويات هذا الملف.</li>
    <li>على اليسار، حدد ملحق <b>Azure</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/execute-remote-function.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/execute-remote-function.png" alt="لقطة شاشة توضح كيفية تنفيذ تطبيق وظائف عن بعد من داخل تعليمة Visual Studio البرمجية."></a></p>
    <li>ضمن <b>Function App</b>، قم بتوسيع <b>Functions</b>، وانقر بزر الماوس الأيمن على <b>customtextcla</b>، ثم حدد <b>Execute Function now</b>.</li>
    <li>في <b>Enter request body</b>، الصق عينة البيانات التي قمت بنسخها، ثم اضغط على <b>Enter</b>.</li>
    <p>سيستجيب تطبيق الوظائف بنتائج JSON.</p>
    <li>قم بتوسيع الإعلام لمشاهدة النتائج بأكملها.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/executed-function-json-response.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/executed-function-json-response.png" alt="لقطة شاشة لاستجابة JSON من تطبيق الوظائف المنفذة."></a></p>
    <p>ينبغي أن تبدو الاستجابة كما يلي:</p>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>{"values": 
    [
        {"recordId": "0", 
        "data": {"text": 
        [
            {"category": "Action", "confidenceScore": 0.99}, 
            {"category": "Comedy", "confidenceScore": 0.96}
        ]}}
    ]
}</code></pre>
    </div>
</ol>



### إضافة حقل إلى فهرس البحث الخاص بك

تحتاج إلى مكان لتخزين الإثراء الذي تم إرجاعه بواسطة تطبيق الوظائف الجديد. اتبع هذه الخطوات لإضافة حقل مركب جديد لتخزين تصنيف النص ودرجة الثقة.

<ol dir='rtl'>
    <li>في <a href="https://portal.azure.com/">مدخل Azure</a>، انتقل إلى مجموعة الموارد التي تحتوي على خدمة البحث الخاصة بك، ثم حدد خدمة البحث المعرفي التي أنشأتها، على سبيل المثال، <b>acs18245-search-service</b>.</li>
    <li>في جزء <b>Overview</b>، حدد <b>Indexes</b>.</li>
    <li>حدد <b>azurebob-index</b>.</li>
    <li>حدد <b>تحرير JSON</b>.</li>
    <li>أضف الحقول الجديدة إلى الفهرس، والصق JSON أدناه ضمن حقل المحتوى.</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>{
    "name": "textclass",
    "type": "Collection(Edm.ComplexType)",
    "analyzer": null,
    "synonymMaps": [],
    "fields": [
        {
          "name": "category",
          "type": "Edm.String",
          "facetable": true,
          "filterable": true,
          "key": false,
          "retrievable": true,
          "searchable": true,
          "sortable": false,
          "analyzer": "standard.lucene",
          "indexAnalyzer": null,
          "searchAnalyzer": null,
          "synonymMaps": [],
          "fields": []
        },
        {
          "name": "confidenceScore",
          "type": "Edm.Double",
          "facetable": true,
          "filterable": true,
          "retrievable": true,
          "sortable": false,
          "analyzer": null,
          "indexAnalyzer": null,
          "searchAnalyzer": null,
          "synonymMaps": [],
          "fields": []
        }
    ]
},</code></pre>
    </div>
    <p>يجب أن يبدو فهرسك على هذا النحو.</p>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/edit-azure-blob-index-fields.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/edit-azure-blob-index-fields.png" alt="لقطة شاشة للفهرس المحرر JSON."></a></p>
    <li>حدد <b>حفظ</b>.</li>
</ol>


### تحرير مجموعة المهارات المخصصة لاستدعاء تطبيق الوظائف الخاص بك

يحتاج فهرس البحث المعرفي إلى طريقة لملء هذه الحقول الجديدة. قم بتحرير مجموعة المهارات التي أنشأتها سابقاً لاستدعاء تطبيق الوظائف الخاص بك.

<ol dir='rtl'>
    <li>في أعلى الصفحة، حدد ارتباط خدمة البحث، على سبيل المثال <b>acs18245-search-service | فهارس</b>.</li>
    <li>في جزء <b>Overview</b>، حدد <b>Skillsets</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/select-custom-skillset.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/select-custom-skillset.png" alt="لقطة شاشة تعرض تحديد مجموعة المهارات المخصصة."></a></p>
    <li>حدد <b>azureblob-skillset</b>.</li>
    <li>أضف تعريف مجموعة المهارات المخصصة أدناه، عن طريق لصقه كمجموعة المهارات الأولى.</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>{
    "@odata.type": "#Microsoft.Skills.Custom.WebApiSkill",
    "name": "Genre Classification",
    "description": "Identify the genre of your movie from its summary",
    "context": "/document",
    "uri": "URI",
    "httpMethod": "POST",
    "timeout": "PT30S",
    "batchSize": 1,
    "degreeOfParallelism": 1,
    "inputs": [
        {
          "name": "lang",
          "source": "/document/language"
        },
        {
          "name": "text",
          "source": "/document/content"
        }
    ],
    "outputs": [
        {
          "name": "text",
          "targetName": "class"
        }
    ],
    "httpHeaders": {}
},</code></pre>
    </div>
    <p>تحتاج إلى تغيير <code>"uri": "URI"</code> للإشارة إلى تطبيق الوظائف الخاص بك.</p>
    <li>في Visual Studio Code، حدد ملحق <b>Azure</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/copy-function-url.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/copy-function-url.png" alt="لقطة شاشة توضح كيفية تحديد عنوان URL لتطبيق الوظائف."></a></p>
    <li>ضمن <b>Functions</b>، انقر بزر الماوس الأيمن على <b>customtextcla</b>، ثم حدد <b>Copy Function Url</b>.</li>
    <li>في مدخل Azure، استبدل URI بعنوان URL للوظيفة المنسوخة. </li>
    <li>حدد <b>حفظ</b>.</li>
</ol>

### تحرير تعيينات الحقول في المفهرس

لديك الآن حقول لتخزين الإثراء، ومجموعة المهارات لاستدعاء تطبيق الوظائف الخاص بك، والخطوة الأخيرة هي إخبار البحث المعرفي بمكان وضع الإثراء.

<ol dir='rtl'>
    <li>في أعلى الصفحة، حدد خدمة البحث، على سبيل المثال ارتباط <b>acs18245-search-service | مجموعات المهارات</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/select-search-indexer.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/select-search-indexer.png" alt="لقطة شاشة تعرض تحديد فهرس البحث."></a></p>
    <li>في جزء <b>Overview</b>، حدد <b>Indexers</b>.</li>
    <li>حدد <b>azureblob-indexer</b>.</li>
    <li>حدد <b>Indexer Definition (JSON)</b>.</li>
    <li>أضف تعيين حقل إخراج جديداً، عن طريق لصق تعريف الحقل هذا في أعلى قسم حقل الإخراج.</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>{
    "sourceFieldName": "/document/class",
    "targetFieldName": "textclass"
},</code></pre>
    </div>
    <p>يجب أن يبدو تعريف JSON للمفهرس الآن كما يلي:</p>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/add-output-fields-indexer.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/add-output-fields-indexer.png" alt="لقطة شاشة تعرض JSON المحرر لمهرس مع حقول إخراج مضافة."></a></p>
    <li>حدد <b>حفظ</b>.</li>
    <li>حدد <b>Reset</b>، ثم حدد <b>Yes</b>.</li>
    <li>
        <p>حدد <b>Run</b>، ثم حدد <b>Yes</b>.</p>
        <p>تقوم خدمة البحث المعرفي من Azure بتشغيل المفهرس المحدث الخاص بك. يستخدم المفهرس مجموعة المهارات المخصصة المحررة. تستدعي مجموعة المهارات تطبيق الوظائف الخاص بك مع المستند الذي تتم فهرسته. يستخدم نموذج مصنف النص المخصص النص الموجود في المستند لمحاولة تحديد نوع الفيلم. يقوم النموذج بإرجاع مستند JSON مع الأنواع ومستويات الثقة. يقوم المفهرس بتعيين نتائج JSON إلى الحقول في الفهرس باستخدام تعيين حقل الإخراج الجديد.</p>
    </li>
    <li>حدد <b>Execution history</b>.</li>
    <li>تحقق من تشغيل المفهرس بنجاح مقابل 210 مستندات.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/check-indexer-results.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/check-indexer-results.png" alt="لقطة شاشة تعرض التشغيل الناجح للفهرس."></a></p>
    <p>قد تحتاج إلى تحديد <b>Refresh</b> لتحديث حالة المفهرس.</p>
</ol>


    

## اختبار فهرس البحث الذي تم إثرائه الخاص بك

<ol dir='rtl'>
    <li>في أعلى الصفحة، حدد خدمة البحث، على سبيل المثال <b>acs18245-search-service | فهارس</b>.</li>
    <li>في جزء <b>Overview</b>، حدد <b>Indexes</b>.</li>
    <li>حدد <b>azurebob-index</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/enriched-index.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/04-media/enriched-index.png" alt="لقطة شاشة تعرض فهرس بحث جرى إثرائه."></a></p>
    <li>حدد <b>بحث</b>.</li>
    <li>استكشف نتائج البحث.</li>
</ol>


يجب أن يحتوي كل مستند في الفهرس على حقل <code>textclass</code> جديد يمكن البحث فيه. يحتوي على حقل فئة مع أنواع الأفلام. يمكن أن يكون أكثر من واحد. كما يوضح مدى ثقة نموذج تصنيف النص المخصص في النوع المحدد.

الآن بعد أن أكملت التمرين، احذف جميع الموارد التي لم تعد بحاجة إليها.

### التنظيف

<ol dir='rtl'>
    <li>في مدخل Azure، انتقل إلى الصفحة الرئيسية، وحدد <b>مجموعات الموارد</b>.</li>
    <li>حدد مجموعات الموارد التي لا تحتاج إليها، ثم حدد <b>حذف مجموعات الموارد</b>.</li>
</ol>


