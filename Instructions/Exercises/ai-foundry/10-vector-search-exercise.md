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
  <td><div dir="auto">استخدام واجهة برمجة تطبيقات REST لتشغيل استعلامات بحث متجه</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table>
</div>

# استخدام واجهة برمجة تطبيقات REST لتشغيل استعلامات بحث متجه

في هذا التمرين، ستقوم بإعداد مشروعك وإنشاء فهرس وتحميل مستنداتك وتشغيل الاستعلامات.

ستحتاج إلى الآتي للنجاح في هذا التمرين:

<ul dir='rtl'>
    <li><a href="https://www.postman.com/downloads/">تطبيق Postman</a></li>
    <li>اشتراك Azure</li>
    <li>خدمة البحث من الذكاء الاصطناعي في Azure</li>
    <li>مجموعة عينات Postman موجودة في هذا المستودع - <i>Vector-Search-Quickstart.postman_collection v1.0 json</i>.</li>
</ul>

> <b>ملاحظة</b> ستجد معلومات إضافية حول تطبيق Postman <a href="https://learn.microsoft.com/en-us/azure/search/search-get-started-rest">هنا</a>، عند الحاجة.

## إعداد مشروعك

قم أولاً بإعداد مشروعك بتنفيذ الخطوات التالية:

<ol dir='rtl'>
    <li>لاحظ <b>عنوان URL</b> و<b>المفتاح</b> من خدمة البحث من الذكاء الاصطناعي في Azure.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/vector-search/search%20keys.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/vector-search/search%20keys.png" alt='رسم توضيحي لموقع اسم الخدمة والمفاتيح.'></a></p>
    <li>قم بتنزيل <a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining/blob/main/Labfiles/10-vector-search/Vector%20Search.postman_collection%20v1.0.json">مجموعة عينات Postman</a>.</li>
    <li>افتح Postman واستورد المجموعة عن طريق تحديد زر <b>استيراد</b> واسحب مجلد المجموعة وضعه في المربع.</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/vector-search/import.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/vector-search/import.png" alt='صورة مربع حوار استيراد'></a></p>
    <li>حدد زر <b>نسخ</b> لإنشاء نسخة للمجموعة وأضف اسماً فريداً.</li>
    <li>انقر بزر الماوس الأيمن فوق اسم مجموعتك وحدد <b>تحرير</b>.</li>
    <li>حدد علامة تبويب <b>المتغيرات</b> وأدخل القيم التالية باستخدام خدمة البحث وأسماء الفهارس من خدمة البحث من الذكاء الاصطناعي في Azure لديك:</li>
    <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/vector-search/variables.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/vector-search/variables.png" alt='مخطط يعرض مثال على إعدادات المتغيرات'></a></p>
    <li>احفظ التغييرات التي أضفتها بتحديد زر <b>حفظ</b>.</li>
    <p>أنت جاهز لإرسال طلباتك إلى خدمة البحث من الذكاء الاصطناعي في Azure.</p>
</ol>


## إنشاء فهرس

تالياً، قم بإنشاء الفهرس الخاص بك في Postman:

<ol dir='rtl'>
    <li>حدد <b>PUT Create/Update Index</b> من القائمة الجانبية.</li>
    <li>قم بتحديث عنوان URL باستخدام <b>search-service-name</b> و<b>index-name</b> و<b>api-version</b> الذين لاحظتهم سابقاً.</li>
    <li>حدد علامة تبويب <b>النص الأساسي</b> لرؤية الاستجابة.</li>
    <li> قم بتعيين <b>index-name</b> على قيمة اسم الفهرس الخاص بك من عنوان URL لديك وحدد <b>إرسال</b>.</li>
</ol>

من المفترض أن ترى رمز حالة للنوع <b>200</b> الذي يشير إلى طلب ناجح.

## تحميل المستندات

هناك 108 مستندات مضمنة في طلب "تحميل المستندات"، ويحتوي كل مستند على مجموعة كاملة من التضمينات لحقلي <b>titleVector</b> و<b>contentVector</b>.

<ol dir='rtl'>
    <li>حدد <b>POST Upload Docs</b> من الشريط الجانبي.</li>
    <li>قم بتحديث عنوان URL بـ <b>search-service-name</b> و<b>index-name</b> و<b>api-version</b> كما سبق.</li>
    <li>حدد علامة تبويب <b>النص الأساسي</b> لرؤية الاستجابة وحدد <b>إرسال</b>.</li>
    <p>من المفترض أن ترى رمز حالة للنوع <b>200</b> لإظهار نجاح طلبك.</p>
</ol>

## تشغيل الاستعلامات

<ol dir='rtl'>
    <li>
        <p>جرّب الآن تشغيل الاستعلامات التالية على القائمة الجانبية. للقيام بذلك، احرص على تحديث عنوان URL في كل مرة كما سبق وإرسال طلب بتحديد <b>إرسال</b>:</p>
        <ul dir='rtl'>
            <li>بحث متجه واحد</li>
            <li>بحث متجه واحد مع عامل تصفية</li>
            <li>بحث مختلط بسيط</li>
            <li>بحث مختلط بسيط مع عامل تصفية</li>
            <li>بحث عبر الحقول</li>
            <li>بحث متعدد الاستعلامات</li>
        </ul>
    </li>
    <li>حدد علامة تبويب <b>النص الأساسي</b> لرؤية الاستجابة وعرض النتائج.</li>
    <p>من المفترض أن ترى رمز حالة للنوع <b>200</b> لإظهار طلب ناجح.</p>
</ol>

### التنظيف

الآن بعد أن أكملت التمرين، احذف جميع الموارد التي لم تعد بحاجة إليها. ابدأ بالتعليمة البرمجية المستنسخة إلى جهازك. ثم احذف موارد Azure.
