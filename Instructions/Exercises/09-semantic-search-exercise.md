
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
  <td><div dir="auto">إعداد مصنف دلالي</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table>
</div>

# إعداد مصنف دلالي

> <b>ملاحظة</b> لإكمال هذا النشاط المعملي، ستحتاج إلى [اشتراك Azure](https://azure.microsoft.com/free?azure-portal=true) الذي لديك فيه حق الوصول الإداري. يتطلب هذا التمرين أيضاً خدمة <b>بحث الذكاء الاصطناعي في Azure</b> ذات طبقة قابلة للفوترة.

في هذا التمرين، ستضيف مصنفاً دلالياً إلى فهرس وتستخدم مصنفاً دلالياً للاستعلام.

## تمكين مصنف دلالي

<ol dir='rtl'>
    <li>افتح مدخل Azure وسجل الدخول.</li>
    <li>حدد <b>جميع الموارد</b> وحدد خدمة البحث لديك.</li>
    <li>في جزء التنقل، حدد <b>المُصنف الدلالي</b>.</li>
    <li>في <b>التوافر</b>، في خيار <b>مجاناً</b>، حدد <b>تحديد خطة</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/semantic-search/semanticsearch.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/semantic-search/semanticsearch.png" alt='لقطة شاشة لمربع حوار المصنف الدلالي.'></a></p>
</ol>


## استيراد فهرس عينة

<ol dir='rtl'>
    <li>ارجع إلى صفحة <b>نظرة عامة</b> لخدمة البحث لديك.</li>
    <li>حدد <b>Import data</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/semantic-search/importdata.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/semantic-search/importdata.png" alt='لقطة شاشة لزر استيراد البيانات.'></a></p>
    <li>في <b>مصدر البيانات</b>، حدد <b>العينات</b>.</li>
    <li>حدد <b>hotels-sample</b> وحدد <b>التالي: أضف مهارات معرفية (اختياري)</b>.</li>
    <li>حدد <b>التخطي إلى: تخصيص الفهرس الهدف</b>.</li>
    <li>حدد <b>التالي: إنشاء مفهرس</b>.</li>
    <li>حدد <b>إرسال</b>.</li>
</ol>


## تكوين التصنيف الدلالي

بمجرد تمكين فهرس البحث وأداة التصنيف الدلالي، يمكنك تكوين الترتيب الدلالي. تحتاج إلى عميل بحث يدعم معاينة واجهات برمجة التطبيقات على طلب الاستعلام. يمكنك استخدام مستكشف البحث في بوابة Azure، أو تطبيق Postman، أو Azure SDK لـ .NET، أو Azure SDK لـ Python. في هذا التمرين، ستستخدم مستكشف البحث في مدخل Azure.

لتكوين التصنيف الدلالي، اتبع الخطوات التالية:

<ol dir='rtl'>
    <li>في شريط التنقل، في <b>إدارة البحث</b>، حدد <b>فهارس</b>.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/semantic-search/indexes.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/semantic-search/indexes.png" alt='لقطة شاشة لزر الفهارس.'></a></p>
    <li>حدد فهرسك.</li>
    <li>حدد <b>التكوينات الدلالية</b> وحدد <b>إضافة تكوين دلالي</b>.</li>
    <li>في نوع <b>الاسم</b> <b>hotels-conf</b>.</li>
    <li>في <b>حقل العنوان</b> حدد <b>HotelName</b>.</li>
    <li>ضمن <b>حقول المحتوى</b>، في <b>اسم الحقل</b>، حدد <b>وصف</b>.</li>
    <li>
        <p>كرر الخطوة السابقة للحقول التالية:</p>
        <ul>
            <li><b>الفئة</b></li>
            <li><b>العنوان/المدينة</b></li>
        </ul>
    </li>
    <li>ضمن <b>حقول الكلمات الأساسية</b>، في <b>اسم الحقل</b>، حدد <b>علامات</b>.</li>
    <li>حدد <b>حفظ</b>.</li>
    <li>في صفحة الفهرس، حدد <b>حفظ</b>.</li>
    <li>حدد <b>البحث عن المستكشف</b>.</li>
    <li>حدد <b>عرض</b> وحدد <b>طريقة عرض JSON</b>.</li>
    <li>في محرر استعلام JSON، اكتب النص التالي:</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>{
    "queryType": "semantic",
    "queryLanguage" : "en-us",
    "search": "all hotels near the water" , 
    "semanticConfiguration": "hotels-conf" , 
    "searchFields": "",
    "speller": "lexicon" , 
    "answers": "extractive|count-3",
    "count": true
}</code></pre>
</div>
    <li>حدد <b>بحث</b>.</li>
    <li>راجع نتائج الاستعلام.</li>
</ol>


## التنظيف

إذا لم تعد بحاجة إلى خدمة بحث الذكاء الاصطناعي في Azure، فيجب عليك حذف المورد من اشتراك Azure الخاص بك لتقليل التكاليف.

><b>ملاحظة</b> يضمن حذف خدمة بحث الذكاء الاصطناعي في Azure الخاصة بك عدم فرض رسوم على اشتراكك مقابل الموارد. مع ذلك، ستجري محاسبتك بمبلغ صغير مقابل تخزين البيانات طالما أن سعة التخزين موجودة في اشتراكك. إذا انتهيت من استكشاف خدمة البحث المعرفي، يمكنك حذف خدمة البحث المعرفي والموارد المرتبطة به. ومع ذلك، إذا كنت تخطط لإكمال أي معامل تجريبية أخرى في هذه السلسلة، سوف تحتاج إلى إعادة إنشائها.
> لحذف مواردك:
> 1. في <a href="https://portal.azure.com?azure-portal=true">مدخل Azure</a>، في صفحة <b>مجموعات الموارد</b>، افتح مجموعة الموارد التي حددتها عند إنشاء المورد الخاص بك.
> 1. انقر فوق <b>حذف مجموعة الموارد</b>، واكتب اسم مجموعة الموارد لتأكيد أنك ترغب في حذفها، ثم حدد <b>Delete</b>.
