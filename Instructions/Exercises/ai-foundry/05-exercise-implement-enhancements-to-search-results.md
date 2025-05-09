---
lab:
  title: تنفيذ التحسينات على نتائج البحث
---

# تنفيذ التحسينات على نتائج البحث

لديك خدمة بحث موجودة يستخدمها تطبيق حجز العطلات. رأيت أن أهمية نتائج البحث تؤثر على عدد الحجوزات التي تحصل عليها. أضفت مؤخراً فنادق في البرتغال لذلك ترغب في تقديم اللغة البرتغالية كلغة مدعومة.

في هذا التمرين، ستضيف ملف تعريف تسجيل النقاط لتحسين صلة نتائج البحث. ثم ستستخدم خدمات الذكاء الاصطناعي في Azure لإضافة أوصاف برتغالية لجميع فنادقك.

> <b>ملاحظة</b>: لإكمال هذا التمرين، ستحتاج إلى اشتراك Microsoft Azure. إذا لم يكن لديك اشتراك بالفعل، يمكنك التسجيل للحصول على الإصدار التجريبي على [https://azure.com/free](https://azure.com/free?azure-portal=true) .

## إنشاء موارد Azure

ستنشئ خدمة بحث الذكاء الاصطناعي في Azure واستيراد عينة من بيانات الفندق.

<ol dir='rtl'>
    <li>قم بتسجيل الدخول إلى <a href="https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true">بوابة Azure</a>.</li>
    <li>حدد <b>+ Create a resource</b>.</li>
    <li>فتش عن <b>البحث</b>، ثم حدد <b>بحث الذكاء الاصطناعي في Azure</b>.</li>
    <li>حدد <b>إنشاء</b>.</li>
    <li>حدد <b>إنشاء جديد</b> ضمن مجموعة الموارد، ويمكنك تسميته <b>Learn-advanced-search</b>.</li>
    <li>في <b>اسم الخدمة</b>، أدخل <b>advanced-search-service-12345</b>. يجب أن يكون الاسم فريداً عالمياً، لذا أضف أرقاماً عشوائية إلى نهاية الاسم.</li>
    <li>حدد منطقة مدعومة بالقرب منك.</li>
    <li>استخدم القيم الافتراضية <b>لطبقة التسعير</b>.</li>
    <li>حدد "<b>Review + create</b>".</li>
    <li>حدد <b>إنشاء</b>.</li>
    <li>انتظر حتى يتم توزيع الموارد، ثم حدد <b>Go to resource</b>.</li>
</ol>


### استيراد بيانات نموذجية إلى خدمة البحث

استيراد بيانات العينة.

<ol dir='rtl'>
    <li>ثم، في جزء <b>Overview</b> حدد <b>Import data</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/import-data-new.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/import-data-new.png" alt="لقطة شاشة تعرض قائمة استيراد بيانات."></a></p>
    <li>في جزء <b>استيراد البيانات</b>، داخل <b>مصدر البيانات</b>، حدد <b>العينات</b>.</li>
    <li>حدد <b>hotels-sample</b>.</li>
    <li>في علامة التبويب <b>إضافة مهارات معرفية (اختياري)</b>، عليك توسيع <b>إرفاق خدمات الذكاء الاصطناعي</b>، ثم حدد <b>إنشاء مورد خدمات الذكاء الاصطناعي الجديد</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/add-cognitive-services-new.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/add-cognitive-services-new.png" alt="لقطة شاشة تعرض تحديد خدمات الذكاء الاصطناعي في Azure وإضافتها."></a></p>
</ol>


### إنشاء خدمة الذكاء الاصطناعي في Azure لدعم الترجمات

<ol dir='rtl'>
    <li>في علامة تبويب جديدة، سجل الدخول إلى مدخل Azure.</li>
    <li>في <b>مجموعة الموارد</b>، حدد <b>learn-advanced-search</b>.</li>
    <li>في <b>المنطقة</b>، حدد المنطقة نفسها التي اخترتها لخدمة البحث.</li>
    <li>في <b>الاسم</b>، أدخل <b>learn-cognitive-translator-12345</b> أو أي اسم تفضله. يجب أن يكون الاسم فريداً عالمياً، لذا أضف أرقاماً عشوائية إلى نهاية الاسم.</li>
    <li>في <b>طبقة التسعير</b>، حدد <b>معيار S0</b>.</li>
    <li>حدد <b>. من خلال تحديد هذا المربع، أقر بأنني قرأت وفهمت جميع الشروط أدناه</b>.</li>
    <li>حدد "<b>Review + create</b>".</li>
    <li>حدد <b>إنشاء</b>.</li>
    <li>عند إنشاء الموارد، أغلق علامة التبويب.</li>
</ol>


### إضافة إثراء الترجمة

<ol dir='rtl'>
    <li>في علامة التبويب <b>إضافة المهارات المعرفية (اختياري)،</b> حدد تحديث.</li>
    <li>حدد الخدمة الجديدة، <b>learn-cognitive-translator-12345</b>.</li>
    <li>قم بتوسيع القسم <b>Add enrichments</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/add-translation-enrichment-new.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/add-translation-enrichment-new.png" alt="لقطة شاشة تبين إضافة الترجمة البرتغالية."></a></p>
    <li>حدد <b>ترجمة النص</b>، وغير <b>اللغة الهدف</b> إلى <b>البرتغالية</b>، ثم غير <b>اسم الحقل</b> إلى <b>Description_pt</b>.</li>
    <li>حدد <b>Next: Customize target index</b>.</li>
</ol>



### تغيير الحقل لتخزين النص المترجم

<ol dir='rtl'>
    <li>في علامة التبويب <b>تخصيص الفهرس الهدف</b>، عليك التمرير إلى أسفل قائمة الحقول وتغيير <b>المحلل</b> إلى <b>البرتغالية (البرتغال) - Microsoft</b> للحقل <b>Description_pt</b>.</li>
    <li>حدد <b>التالي: إنشاء مفهرس</b>.</li>
    <li>
        <p>حدد <b>إرسال</b>.</p>
        <p>يجري إنشاء الفهرس، وسيعمل المفهرس، وسيجري استيراد 50 مستنداً تحتوي على نموذج بيانات الفندق.</p>
    </li>
    <li>في جزء <b>نظرة عامة</b>، حدد <b>الفهارس</b>، ثم حدد <b>hotels-sample-index</b>.</li>
    <li>حدد <b>بحث</b> لمشاهدة JSON لكافة المستندات في الفهرس.</li>
    <li>ابحث <b>عن Description_pt</b> (يمكنك استخدام <b>CTRL + F</b> لهذا) في النتائج ولاحظ أنها ليست ترجمة برتغالية للوصف باللغة الإنجليزية، ولكنها تبدو كما يلي بدلاً من ذلك:</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>"Description_pt": "45",</code></pre>
    </div>
</ol>


يفترض مدخل Microsoft Azure أن الحقل الأول في المستند يحتاج إلى الترجمة. لذلك فهي تستخدم حالياً مهارة الترجمة لترجمة <code>HotelId</code>.

### تحديث مجموعة المهارات لترجمة الحقل الصحيح في المستند

<ol dir='rtl'>
    <li>في أعلى الصفحة، اختر خدمة البحث، ارتباط <b>advanced-search-service-12345 | الفهارس</b>.</li>
    <li>حدد <b>مجموعات المهارات</b> ضمن إدارة البحث في الجزء الأيمن، ثم حدد <b>hotels-sample-skillset</b>.</li>
    <li>تحرير مستند JSON، وتغيير السطر 11 إلى:</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>"context": "/document/Description",</code></pre>
    </div>
    <li>يمكنك تغيير الإعداد الافتراضي من اللغة إلى الإنجليزية في السطر 12:</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>"defaultFromLanguageCode": "en",</code></pre>
    </div>
    <li>تغيير الحقل المصدر في السطر 18 إلى:</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>"source": "/document/Description"</code></pre>
    </div>
    <li>حدد <b>حفظ</b>.</li>
    <li>في أعلى الصفحة، اختر خدمة البحث، ارتباط <b>advanced-search-service-12345 | مجموعات المهارات</b>.</li>
    <li>في جزء <b>نظرة عامة</b>، حدد <b>المفهرسات</b>، ثم حدد <b>hotels-sample-indexer</b>.</li>
    <li>حدد <b>Indexer Definition (JSON)</b>.</li>
    <li>تغيير اسم الحقل المصدر في السطر 21 إلى:</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>"sourceFieldName": "/document/Description/Description_pt",</code></pre>
    </div>
    <li>حدد <b>حفظ</b>.</li>
    <li>حدد <b>إعادة تعيين</b>، ثم حدد <b>نعم</b>.</li>
    <li>حدد <b>تشغيل</b>، ثم حدد <b>نعم</b>.</li>
</ol>



### اختبار الفهرس المحدث

<ol dir='rtl'>
    <li>في أعلى الصفحة، اختر خدمة البحث، ارتباط <b>advanced-search-service-12345 | المفهرسات</b>.</li>
    <li>في جزء <b>نظرة عامة</b>، حدد <b>الفهارس</b>، ثم حدد <b>hotels-sample-index</b>.</li>
    <li>حدد <b>بحث</b> لمشاهدة JSON لكافة المستندات في الفهرس.</li>
    <li>ابحث عن <b>Description_pt</b> في النتائج ولاحظ أن هناك الآن وصفاً برتغالياً.</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>"Description_pt": "O maior resort durante todo o ano da área oferecendo mais de tudo para suas férias – pelo melhor valor!  O que você pode desfrutar enquanto estiver no resort, além das praias de areia de 1,5 km do lago? Confira nossas atividades com certeza para excitar tanto os jovens quanto os jovens hóspedes do coração. Temos tudo, incluindo ser chamado de \"Propriedade do Ano\" e um \"Top Ten Resort\" pelas principais publicações.",</code></pre>
    </div>
    <li>
        <p>الآن عليك البحث عن الفنادق التي لديها إطلالات على البحيرات. سنبدأ باستخدام بحث بسيط يرجع فقط <code>HotelName</code>و<code>Description</code> و<code>Category</code> و<code>Tags</code>. في <b>سلسلة الاستعلام</b>، أدخل هذا البحث:</p>
        <code>lake + view&$select=HotelName,Description,Category,Tags&$count=true</code>
        <p>ابحث عن النتائج وحاول العثور على الحقول التي تطابق مصطلحي البحث <code>lake</code> و<code>view</code>. لاحظ هذا الفندق وموقعه:</p>
    </li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>{
    "@search.score": 0.9433406,
    "HotelName": "Lady Of The Lake B & B",
    "Description": "Nature is Home on the beach.  Save up to 30 percent. Valid Now through the end of the year. Restrictions and blackout may apply.",
    "Category": "Luxury",
    "Tags": [
        "laundry service",
        "concierge",
        "view"
    ]
},</code></pre>
    </div>
</ol>

تطابق هذا الفندق مع بحيرة المصطلحات في حقل `HotelName` وفي المنظر في حقل `Tags`. ترغب في تعزيز تطابق الشروط في حقل `Description` على اسم الفندق. من الناحية المثالية، يجب أن يكون هذا الفندق الأخير في النتائج.

## إضافة ملف تعريف تسجيل النقاط لتحسين نتائج البحث

<ol dir='rtl'>
    <li>حدد علامة التبويب <b>ملفات تعريف تسجيل النقاط</b>.</li>
    <li>حدد <b>+ إضافة ملف تعريف تسجيل النقاط</b>.</li>
    <li>في <b>اسم ملف التعريف</b>، أدخل <b>boost-description-categories</b>.</li>
    <li>أضف الحقول والأوزان التالية ضمن <b>الأوزان</b>:</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/add-weights-new.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/05-media/add-weights-new.png" alt="لقطة شاشة للأوزان التي تجري إضافتها إلى ملف تعريف تسجيل النقاط."></a></p>
    <li>في <b>اسم الحقل</b>، حدد <b>الوصف</b>.</li>
    <li>بالنسبة <b>للوزن</b>، أدخل <b>5</b>.</li>
    <li>في <b>اسم الحقل</b>، حدد <b>الفئة</b>.</li>
    <li>بالنسبة <b>للوزن</b>، أدخل <b>3</b>.</li>
    <li>في <b>اسم الحقل</b>، حدد <b>علامات</b>.</li>
    <li>بالنسبة <b>للوزن</b>، أدخل <b>2</b>.</li>
    <li>حدد <b>حفظ</b>.</li>
    <li>حدد ⁧<b>⁩حفظ⁧</b>⁩ في الأعلى.</li>
</ol>


### اختبار الفهرس المحدث

<ol dir='rtl'>
    <li>ارجع إلى علامة تبويب <b>مستكشف البحث</b> في صفحة <b>hotels-sample-index</b>.</li>
    <li>
        <p>في <b>سلسلة الاستعلام</b>، أدخل البحث نفسه كما كان من قبل:</p>
        <code>lake + view&$select=HotelName,Description,Category,Tags&$count=true</code>
        <p>تحقق من نتائج البحث.</p>
    </li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>{
    "@search.score": 3.5707965,
    "HotelName": "Lady Of The Lake B & B",
    "Description": "Nature is Home on the beach.  Save up to 30 percent. Valid Now through the end of the year. Restrictions and blackout may apply.",
    "Category": "Luxury",
    "Tags": [
        "laundry service",
        "concierge",
        "view"
    ]
}</code></pre>
    </div>
    <p>زادت درجة البحث من <b>0.9433406</b> إلى <b>3.5707965</b>. مع ذلك، فإن جميع الفنادق الأخرى لديها درجات محسوبة أعلى. هذا الفندق هو الآن الآخر في النتائج.</p>
</ol>


## التنظيف

الآن بعد أن أكملت التمرين، احذف جميع الموارد التي لم تعد بحاجة إليها.

<ol dir='rtl'>
    <li>في مدخل Azure، حدد <b>مجموعات الموارد</b>:</li>
    <li>حدد مجموعة الموارد التي لا تحتاج إليها بعد الآن، ثم حدد <b>حذف مجموعات الموارد</b>.</li>
</ol>

