---
lab:
  title: تصحيح مشكلات البحث
---

# تصحيح مشكلات البحث

لقد أنشأت حل البحث الخاص بك ولكنك لاحظت أن هناك بعض التحذيرات على المفهرس.

في هذا التمرين، ستنشئ حل بحث الذكاء الاصطناعي في Azure واستيراد بعض نماذج البيانات، ثم حل تحذير على المفهرس.

> <b>ملاحظة</b>: لإكمال هذا التمرين، ستحتاج إلى اشتراك Microsoft Azure. إذا لم يكن لديك اشتراك بالفعل، يمكنك التسجيل للحصول على الإصدار التجريبي على [https://azure.com/free](https://azure.com/free?azure-portal=true) .

## إنشاء حل البحث الخاص بك

قبل أن تتمكن من البدء في استخدام جلسة تتبع الأخطاء، تحتاج إلى إنشاء خدمة البحث بالذكاء الاصطناعي في Azure.

<ol dir='rtl'>
    <li><a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FMicrosoftLearning%2Fmslearn-knowledge-mining%2Fmain%2FLabfiles%2F08-debug-search%2Fazuredeploy.json">توزيع الموارد إلى Azure</a> - إذا كنت في جهاز ظاهري (VM) مستضاف، فانسخ هذا الارتباط والصقه في متصفح الجهاز الظاهري (VM). بخلاف ذلك، حدد هذا الرابط لتوزيع كافة الموارد التي تحتاجها في بوابة Azure.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/arm-template-deployment.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/arm-template-deployment.png" alt='لقطة شاشة لقالب توزيع arm مع الحقول التي تم إدخالها.'></a></p>
    <li>ضمن <b>مجموعة الموارد</b>، حدد مجموعة الموارد المتوفرة أو حدد <b>إنشاء جديدة</b> واكتب <b>debug-search-exercise</b>.</li>
    <li>حدد أقرب <b>منطقة</b> لك، أو استخدم الإعداد الافتراضي.</li>
    <li>بالنسبة إلى <b>بادئة الموارد</b>، أدخل <b>debugsearch</b> وأضف مجموعة عشوائية من الأرقام أو الأحرف للتأكد من أن اسم التخزين فريد.</li>
    <li>بالنسبة إلى الموقع، حدد نفس المنطقة التي استخدمتها أعلاه.</li>
    <li>في جزء التنقل السفلي، حدد <b>Review + create</b>.</li>
    <li>انتظر حتى يتم توزيع الموارد، ثم حدد <b>Go to resource group</b>.</li>
</ol>

## استيراد عينة البيانات وتكوين الموارد

باستخدام الموارد التي تم إنشاؤها، يمكنك الآن استيراد بيانات المصدر الخاص بك.

<ol dir='rtl'>
    <li>في الموارد المدرجة، انتقل إلى حساب التخزين. لتنفيذ ذلك، انتقل إلى <b>التكوين</b> في الجزء الأيسر، واضبط <b>السماح بالوصول المجهول للكائن الثنائي كبير الحجم</b> على <b>تمكين</b> ثم حدد <b>حفظ</b>.</li>
    <li>انتقل مرة أخرى إلى مجموعة الموارد الخاصة بك، وحدد خدمة البحث.</li>
    <li>
        <p>ثم، في جزء <b>Overview</b> حدد <b>Import data</b>.</p>
        <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/import-data.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/import-data.png" alt='لقطة شاشة تعرض قائمة import data المحددة.'></a></p>
    </li>
    <li>في جزء استيراد البيانات، لمصدر البيانات، حدد <b>Samples</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/import-data-selection-screen-small.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/import-data-selection-screen-small.png" alt='لقطة شاشة تعرض الحقول المكتملة.'></a></p>
    <li>في قائمة العينات، حدد <b>hotels-sample</b>.</li>
    <li>حدد <b>Next:Add cognitive skills (Optional)</b>.</li>
    <li>
        <p>قم بتوسيع القسم <b>Add enrichments</b>.</p>
        <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/add-enrichments.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/add-enrichments.png" alt='لقطة شاشة لخيارات add enrichments.'></a></p>
    </li>
    <li>حدد <b>Text Cognitive Skills</b>.</li>
    <li>حدد <b>Next:Customize target index</b>.</li>
    <li>اترك الإعدادات الافتراضية، ثم حدد <b>Next:Create an indexer</b>.</li>
    <li>حدد <b>إرسال</b>.</li>
</ol>


## استخدام جلسة تصحيح الأخطاء لحل التحذيرات على المفهرس الخاص بك

سيبدأ المفهرس الآن في استيعاب 50 مستنداً. مع ذلك، إذا تحققت من حالة المفهرس، فستجد أن هناك تحذيرات.

<p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/indexer-warnings.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/indexer-warnings.png" alt='لقطة شاشة تعرض 150 تحذيراً على أداة الفهرسة.'></a></p>

<ol dir='rtl'>
    <li>حدد <b>جلسات تتبع الأخطاء</b> في الجزء الأيمن.</li>
    <li>حدد <b>+ إضافة جلسة تتبع الأخطاء</b>.</li>
    <li>أدخل اسما لجلسة العمل، وحدد <b>hotel-sample-indexer</b> <b>لقالب المفهرس</b>.</li>
    <li>حدد حساب التخزين الخاص بك من حقل <b>حساب التخزين</b>. سيؤدي هذا تلقائيًا إلى إنشاء حاوية تخزين للاحتفاظ ببيانات تتبع الأخطاء.</li>
    <li>اترك خانة الاختيار للمصادقة باستخدام هوية مدارة غير محددة.</li>
    <li>حدد <b>حفظ</b>.</li>
    <li>
        <p>بمجرد الإنشاء، سيتم تشغيل جلسة عمل تتبع الأخطاء تلقائيًا على البيانات في خدمة البحث الخاصة بك. يجب أن يكتمل مع إعطاء أخطاء/تحذيرات.</p>
        <p>يوضح لك مخطط التبعية أنه لكل مستند هناك خطأ على ثلاث مهارات.</p>
        <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/debug-session-errors.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/debug-session-errors.png" alt='لقطة شاشة تعرض التحذيرات الثلاثة على مستند جرى إثراؤه.'></a></p>
    </li>
    <blockquote><b>ملاحظة</b>: قد ترى خطأ حول الاتصال بحساب التخزين وتكوين الهويات المُدارة. يحدث هذا إذا حاولت تتبع الأخطاء بسرعة كبيرة بعد تمكين الوصول المجهول للكائن الثنائي كبير الحجم، ويجب أن يستمر تشغيل جلسة عمل تتبع الأخطاء في العمل. يجب أن يؤدي تحديث نافذة المتصفح بعد بضع دقائق إلى إزالة التحذير.</blockquote>
    <li>في مخطط التبعية، حدد إحدى عقد المهارة التي تحتوي على خطأ.</li>
    <li>
        <p>في جزء تفاصيل المهارات، حدد <b>Errors/Warnings(1)</b>.</p>
        <p>التفاصيل هي:</p>
        <p><i>رمز لغة غير صالح "(غير معروف)". اللغات المدعومة: af ،am ،ar ،as ،az ،bg ،bn ،bs ،ca ،cs ،cy ،da ،de ،el ،en ،es ،et ،eu ،fa ،fi ،fr ،ga ،gl ،gu ،he ،hi ،hr ،hu ،hy ،id ،it ،ja ،ka ،kk ،km ،kn ،ko ،ku ،ky ،lo ،lt ،lv ،mg ،mk ،ml ،mn ،mr ،ms ،my ،ne ،nl ،no ،or ،pa ،pl ،ps ،pt-BR ،pt-PT ،ro ،ru ،sk ،sl ،so ،sq ،sr ،ss ،sv ،sw ،ta ،te ،th ،tr ،ug ،uk ،ur ،uz ،vi ،zh-Hans ،zh-Hant. للحصول على تفاصيل إضافية، راجع https://aka.ms/language-service/language-support.</i></p>
        <p>إذا نظرت إلى مخطط التبعية، فإن مهارة الكشف عن اللغة لها مخرجات للمهارات الثلاث مع أخطاء. إذا نظرت إلى إعدادات المهارة مع وجود أخطاء، فسترى إدخال المهارة الذي يسبب الخطأ هو <code>languageCode</code>.</p>
    </li>
    <li>
        <p>في مخطط التبعية، حدد <b>Language detection</b>.</p>
        <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/language-detection-skill-settings.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/language-detection-skill-settings.png" alt='لقطة شاشة تعرض إعدادات المهارات لمهارة الكشف عن اللغة.'></a></p>
        <p>بالنظر إلى إعدادات المهارة JSON، لاحظ أن الحقل المستخدم لاستدلال اللغة هو <code>HotelId</code>.</p>
        <p>سيتسبب هذا الحقل في الخطأ حيث لا يمكن للمهارة العمل على اللغة استناداً إلى معرف.</p>
    </li>
</ol>



## حل التحذير على المفهرس

<ol dir='rtl'>
    <li>حدد <b>المصدر</b> ضمن الإدخالات، وغيِّر الحقل إلى <code>/document/Description</code>.</li>
    <li>حدد <b>حفظ</b>.</li>
    <li>
        <p>حدد <b>تشغيل</b>. يجب ألا يكون لدى المفهرس أي تحذيرات بعد الآن. يمكن الآن تحديث مجموعة المهارات.</p>
        <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/debug-session-complete.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/debug-session-complete.png" alt='لقطة شاشة تعرض تشغيلًا مكتملًا بدون أخطاء.'></a></p>
    </li>
    <li>حدد <b>تثبيت التغييرات</b> لدفع التغييرات التي تم إجراؤها في جلسة العمل هذه إلى المفهرس الخاص بك.</li>
    <li>حدد <b>موافق</b>. يمكنك الآن حذف جلسة العمل الخاصة بك.</li>
    <p>الآن تحتاج إلى التأكد من إرفاق مجموعة المهارات الخاصة بك بمورد خدمات بحث الذكاء الاصطناعي في Azure وإلا فستحصل على عرض الأسعار الأساسي وسيحصل المفهرس على مهلة.</p>
</ol>


<ol dir='rtl'>
    <li>
        <p>لتنفيذ ذلك، حدد <b>مجموعات المهارات</b> في الجزء الأيمن، ثم حدد مجموعة <b>hotels-sample-skillset</b>.</p>
        <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/update-skillset.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/update-skillset.png" alt='لقطة شاشة تعرض قائمة مجموعة المهارات.'></a></p>
    </li>
    <li>
        <p>حدد <b>توصيل خدمة الذكاء الاصطناعي</b> ثم حدد مورد خدمات الذكاء الاصطناعي في القائمة.</p>
        <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/skillset-attach-service.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/skillset-attach-service.png" alt='لقطة شاشة تعرض مورد خدمات الذكاء الاصطناعي في Azure لإرفاقه بمجموعة المهارات.'></a></p>
    </li>
    <li>حدد <b>حفظ</b>.</li>
    <li>الآن عليك تشغيل المفهرس لتحديث المستندات بإثراء الذكاء الاصطناعي الثابت. لتنفيذ ذلك، حدد <b>مفهرسات</b> في الجزء الأيمن، وحدد  <b>hotels-sample-indexer</b>، ثم حدد <b>تشغيل</b>.  عند الانتهاء من التشغيل، يجب أن ترى أن التحذيرات الآن صفر.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/warnings-fixed-indexer.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/08-media/warnings-fixed-indexer.png" alt='لقطة شاشة تعرض كل ما تم حله.'></a></p>
</ol>


## التنظيف

 لقد أكملت الآن التمرين، إذا انتهيت من استكشاف خدمات بحث الذكاء الاصطناعي في Azure، فاحذف موارد Azure التي أنشأتها خلال التمرين. أسهل طريقة للقيام بذلك هي حذف مجموعة الموارد <b>acs-cognitive-search-exercise</b>.
