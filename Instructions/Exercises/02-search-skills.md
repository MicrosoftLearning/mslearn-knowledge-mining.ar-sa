<div dir="rtl">

<table>
  <thead>
  <tr>
  <th>title</th>
  <th>module</th>
  </tr>
  </thead>
  <tbody>
  <tr>
  <td><div dir="auto">إنشاء مهارة مخصصة لـ Azure الذكاء الاصطناعي Search</div></td>
  <td><div dir="auto">Module 12 - Creating a Knowledge Mining Solution</div></td>
  </tr>
  </tbody>
</table>

</div>

# إنشاء مهارة مخصصة لـ Azure الذكاء الاصطناعي Search

يستخدم Azure الذكاء الاصطناعي Search مسار إثراء من مهارات الذكاء الاصطناعي لاستخراج الحقول التي تم إنشاؤها الذكاء الاصطناعي من المستندات وتضمينها في فهرس بحث. هناك مجموعة شاملة من المهارات المضمنة التي يمكنك استخدامها، ولكن إذا كان لديك متطلبات محددة لا تلبيها هذه المهارات، يمكنك إنشاء مهارة مخصصة.

في هذا التمرين، ستنشئ مهارة مخصصة في جدولة تكرار الكلمات الفردية في مستند لإنشاء قائمة بالكلمات الخمسة الأولى الأكثر استخداماً، وإضافتها إلى حل بحث عن Margie's Travel - وهي وكالة سفر وهمية.

## الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية

ستطور تطبيق البحث لديك باستخدام Visual Studio Code. تم توفير ملفات التعليمات البرمجية لتطبيقك في GitHub repo.

> <b>تلميح</b>: إذا نسخت بالفعل مستودع <b>mslearn-knowledge-mining</b>، فافتحه في Visual Studio code. وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة تطويرك.

<ol dir='rtl'>
    <li>ابدأ تشغيل Visual Studio Code.</li>
    <li>افتح لوحة (SHIFT+CTRL+P) وشغّل <b>Git: استنسخ الأمر </b> لاستنساخ مستودع <code>https://github.com/MicrosoftLearning/mslearn-knowledge-mining</code> إلى مجلد محلي (لا يُهم أي مجلد).</li>
    <li>عند استنساخ المستودع، افتح المجلد في تعليمة Visual Studio البرمجية.</li>
    <li>انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية #C في المستودع.</li>
    <blockquote><b>ملاحظة</b>: إذا جرت مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد <b>ليس الآن</b>.</blockquote>
</ol>


## إنشاء موارد Azure

> <b>ملاحظة</b>: إذا سبق أن أكملت تمرين <b>[إنشاء حل بحث الذكاء الاصطناعي في Azure](01-azure-search.md)</b>، ولا يزال لديك موارد بحث الذكاء الاصطناعي في Azure في اشتراكك، يمكنك تخطي هذا المقطع وبدء مقطع <b>إنشاء حل بحث</b>. وإلا، اتبع الخطوات أدناه لتوفير موارد Azure المطلوبة.

<ol dir='rtl'>
    <li>في مستعرض ويب، افتح مدخل Microsoft Azure في <code>https://portal.azure.com</code>، ثم سجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure لديك.</li>
    <li>
        <p>في شريط البحث العلوي، ابحث عن <i>خدمات الذكاء الاصطناعي في Azure</i>، وحدد <b>حساب خدمة متعددة لخدمات الذكاء الاصطناعي في Azure</b>، وأنشئ مورد حساب متعدد الخدمات لخدمات الذكاء الاصطناعي في Azure بالإعدادات التالية:</p>
        <ul dir='rtl'>
            <li><b>Subscription</b>: <i>اشتراكك في Azure</i></li>
            <li><b>مجموعة الموارد</b>: <i>اختر أو أنشئ مجموعة موارد (إذا كنت تستخدم اشتراكاً مقيداً، فقد لا يكون لديك إذن لإنشاء مجموعة موارد جديدة - استخدم المجموعة المتوفرة)</i></li>
            <li><b>المنطقة</b>: <i>اختر من المناطق الجغرافية المتاحة والقريبة إليك</i></li>
            <li><b>الاسم</b>: <i>أدخل اسماً فريداً</i></li>
            <li><b>مستوى التسعير</b>: قياسي S0</li>
        </ul>
    </li>
    <li>بمجرد النشر، انتقل إلى المورد وفي <b>صفحة نظرة عامة</b>، لاحظ <b>معرّف الاشتراك</b> <b>والموقع</b>. ستحتاج إلى هذه القيم، إلى جانب اسم مجموعة الموارد في الخطوات اللاحقة. </li>
    <li>في Visual Studio Code، قم بتوسيع مجلد <b>Labfiles/02-search-skill</b> وحدد <b>setup.cmd</b>. ستستخدم دُفعة البرنامج النصي لتشغيل أوامر واجهة سطر أوامر Azure (CLI) المطلوبة لإنشاء موارد Azure التي تحتاجها.</li>
    <li>انقر بزر الماوس الأيمن فوق المجلد <b>02-search-skill</b> وحدد <b>فتح في الوحدة الطرفية المتكاملة</b>.</li>
    <li>في جزء terminal، أدخِل الأمر التالي لتأسيس اتصال مصادق إلى اشتراك Azure.</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>az login --output none</code></pre>
    </div>
    <li>عند المطالبة، قم بتحديد تسجيل الدخول إلى اشتراكك في Azure. ثم ارجع إلى Visual Studio Code وانتظر حتى تكتمل عملية تسجيل الدخول.</li>
    <li>يمكنك تشغيل الأمر التالي لسرد مواقع Azure.</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>az account list-locations -o table</code></pre>
    </div>
    <li>في المخرجات، ابحث عن قيمة <b>الاسم</b> التي تتوافق مع موقع مجموعة الموارد الخاصة بك (على سبيل المثال، بالنسبة <i>لشرق الولايات المتحدة</i>، الاسم المقابل هو <i>eastus</i>).</li>
    <li>في البرنامج النصي <b>setup.cmd</b>، عليك تعديل <b>subscription_id</b>، و<b>resource_group</b>، و<b>location</b> المتغيرين باستخدام القيم المناسبة لمعرّف الاشتراك، واسم مجموعة الموارد، واسم الموقع. ثم احفظ التغييرات.</li>
    <li>في المحطة الطرفية للمجلد <b>02-search-skill</b>، أدخل الأمر التالي لتشغيل البرنامج النصي:</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>./setup</code></pre>
    </div>
    <blockquote><b>ملاحظة</b>: إذا فشل البرنامج النصي، فتأكد من حفظه بأسماء المتغيرات الصحيحة وحاول مرة أخرى.</blockquote>
    <li>
        <p>عند اكتمال البرنامج النصي، راجع المخرجات التي يعرضها ولاحظ المعلومات التالية حول موارد Azure (ستحتاج هذه القيم لاحقًا):</p>
        <ul dir='rtl'>
            <li>Storage account name</li>
            <li>سلسلة اتصال التخزين</li>
            <li>نقطة نهاية خدمة البحث</li>
            <li>مفتاح مسؤول خدمة البحث</li>
            <li>مفتاح الاستعلام عن خدمة البحث</li>
        </ul>
    </li>
    <li>في مدخل Microsoft Azure، عليك تحديث مجموعة الموارد وتحقق من أنها تحتوي على حساب مخزن Azure ومورد خدمات الذكاء الاصطناعي في Azure ومورد بحث الذكاء الاصطناعي في Azure.</li>
</ol>


## إنشاء حل بحث

الآن بعد أن أصبح لديك موارد Azure الضرورية، يمكنك إنشاء حل بحث يتكون من المكونات التالية:

<ul dir='rtl'>
    <li><b>مصدر بيانات</b> يشير إلى المستندات في حاوية تخزين Azure لديك.</li>
    <li>تحدد <b>مجموعة مهارات</b> مسار إثراء المهارات لاستخراج الحقول التي تم إنشاؤها الذكاء الاصطناعي من المستندات.</li>
    <li><b>فهرس</b> يحدد مجموعة قابلة للبحث من سجلات المستندات.</li>
    <li>يستخرج <b>مفهرس</b> المستندات من مصدر البيانات، ويطبق مجموعة المهارات، ويملأ الفهرس.</li>
</ul>

في هذا التمرين، ستستخدم واجهة Azure الذكاء الاصطناعي Search REST لإنشاء هذه المكونات عن طريق إرسال طلبات JSON.

<ol dir='rtl'>
    <li>في Visual Studio Code، في المجلد <b>02-search-skill</b>، قم بتوسيع مجلد <b>create-search</b> وحدد <b>data_source.json</b>. يحتوي هذا الملف على تعريف JSON لمصدر بيانات يسمى <b>margies-custom-data</b>.</li>
    <li>استبدل العنصر النائب <b>YOUR_CONNECTION_STRING</b> سلسلة الاتصال لحساب تخزين Azure الخاص بك، والذي يجب أن يشبه ما يلي:</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>DefaultEndpointsProtocol=https;AccountName=ai102str123;AccountKey=12345abcdefg...==;EndpointSuffix=core.windows.net</code></pre>
    </div>
    <p><i>يمكنك العثور على سلسلة الاتصال في صفحة <b>مفاتيح الوصول</b> لحساب التخزين الخاص بك في مدخل Microsoft Azure.</i></p>
    <li>احفظ ملف JSON المُحدَّث وأغلقه.</li>
    <li>في مجلد <b>create-search</b>، افتح <b>skillset.json</b>. يحتوي هذا الملف على تعريف JSON لمصدر بيانات يسمى <b>margies-custom-skillset</b>.</li>
    <li>
        <p>في الجزء العلوي من تعريف مجموعة المهارات، في <b>عنصر cognitiveServices</b>، استبدل <b>العنصر النائب YOUR_AI_SERVICES_KEY</b> بأي من مفاتيح موارد Azure الذكاء الاصطناعي Services.</p>
        <p><i>يمكنك العثور على المفاتيح في صفحة <b>المفاتيح ونقطة النهاية</b> لمورد Azure الذكاء الاصطناعي Services في مدخل Microsoft Azure.</i></p>
    </li>
    <li>احفظ وأغلق ملف JSON المحدث.</li>
    <li>في <b>مجلد create-search</b>، افتح <b>index.json</b>. يحتوي هذا الملف على تعريف JSON لفهرس يسمى <b>margies-custom-index</b>.</li>
    <li>راجع JSON للفهرس، ثم أغلق الملف دون إجراء أي تغييرات.</li>
    <li>في مجلد <b>create-search</b>، افتح <b>indexer.json</b>. يحتوي هذا الملف على تعريف JSON لمفهرس يسمى <b>margies-custom-indexer</b>.</li>
    <li>راجع JSON للفهرس، ثم أغلق الملف دون إجراء أي تغييرات.</li>
    <li>في مجلد <b>create-search</b>، افتح <b>create-search.cmd</b>. يستخدم هذا البرنامج النصي الدفعي الأداة المساعدة cURL لإرسال تعريفات JSON إلى واجهة REST لمورد بحث الذكاء الاصطناعي في Azure.</li>
    <li>
        <p>استبدل العناصر النائبة والمتغيرة <b>YOUR_SEARCH_URL</b> <b>وYOUR_ADMIN_KEY</b> بعنوان <b>Url</b> وأحد <b>مفاتيح المسؤول</b> لمورد بحث الذكاء الاصطناعي في Azure.</p>
        <p><i>يمكنك العثور على هذه القيم في صفحات <b>النظرة العامة</b> <b>والمفاتيح</b> لمورد بحث الذكاء الاصطناعي في Azure في مدخل Microsoft Azure.</i></p>
    </li>
    <li>احفظ ملف الدفعة المُحدَّث.</li>
    <li>انقر بزر الماوس الأيمن فوق المجلد <b>create-search</b> وحدد <b>فتح في الوحدة الطرفية المتكاملة</b>.</li>
    <li>في الجزء الطرفي لمجلد <b>create-search</b>، أدخل الأمر التالي وشغَّل دُفعة البرنامج النصي.</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>./create-search</code></pre>
    </div>
    <li>
        <p>عند اكتمال البرنامج النصي، في مدخل Azure، على صفحة مورد بحث الذكاء الاصطناعي في Azure، حدد صفحة <b>المفهرسات</b> وانتظر حتى تكتمل عملية الفهرسة.</p>
        <p><i>يمكنك تحديد <b>تحديث</b> لتتبع تقدم عملية الفهرسة. قد يستغرق الأمر دقيقة أو نحو ذلك حتى يكتمل.</i></p>
    </li>
</ol>


## البحث في الفهرس

الآن بعد أن أصبح لديك فهرس، يمكنك البحث فيه.

<ol dir='rtl'>
    <li>في أعلى الجزء لمورد Azure الذكاء الاصطناعي Search، حدد <b>مستكشف البحث</b>.</li>
    <li>في مستكشف البحث، في <b>مربع استعلام</b> الاستعلام، أدخل سلسلة الاستعلام التالية، ثم حدد <b>بحث</b>.</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>search=London&$select=url,sentiment,keyphrases&$filter=metadata_author eq 'Reviewer' and sentiment eq 'positive'</code></pre>
    </div>
    <p>يسترد هذا الاستعلام عنوان <b>URL</b> <b>والمشاعر</b> <b>وعبارات</b> المفاتيح لجميع المستندات التي تشير إلى <i>لندن</i> التي ألفها <i>المراجع</i> التي تحمل وصفا إيجابيا <b>للتوجه</b> (بمعنى آخر، المراجعات الإيجابية التي تذكر لندن)</p>
</ol>



## إنشاء دالة Azure لمهارة مخصصة

يتضمن حل البحث عددا من المهارات الذكاء الاصطناعي المضمنة التي تثري الفهرس بمعلومات من المستندات، مثل درجات التوجه وقوائم العبارات الرئيسية التي شوهدت في المهمة السابقة.

يمكنك تحسين الفهرس بشكل أكبر من خلال إنشاء مهارات مخصصة. على سبيل المثال، قد يكون من المفيد تحديد الكلمات التي يتم استخدامها بشكل متكرر في كل مستند، ولكن لا توجد مهارة مضمنة توفر هذه الوظيفة.

لتنفيذ وظيفة عدد الكلمات كمهارة مخصصة، ستقوم بإنشاء دالة Azure باللغة المفضلة لديك.

> <b>ملاحظة</b>: في هذا التمرين، ستقوم بإنشاء دالة Node.JS بسيطة باستخدام إمكانات تحرير التعليمات البرمجية في مدخل Azure. في حل الإنتاج، عادة ما تستخدم بيئة تطوير مثل Visual Studio Code لإنشاء تطبيق دالة بلغتك المفضلة (على سبيل المثال #C أو Python أو Node.JS أو Java) ونشره على Azure كجزء من عملية DevOps.

<ol dir='rtl'>
    <li>
        <p>في مدخل Microsoft Azure، في <b>الصفحة الرئيسية</b>، أنشئ مورد <b>Function App</b> جديدا بالإعدادات التالية:</p>
        <ul>
            <li><b>خطة الاستضافة</b>: الاستهلاك</li>
            <li><b>اشتراك</b>: <i>اشتراكك</i></li>
            <li><b>مجموعة الموارد</b>: <i>مجموعة الموارد نفسها مثل مورد بحث الذكاء الاصطناعي في Azure الخاص بك</i></li>
            <li><b>اسم Function App</b>: <i>اسم فريد</i></li>
            <li><b>مكدس وقت التشغيل</b>: Node.js</li>
            <li><b>الإصدار</b>: 18 LTS</li>
            <li><b>المنطقة</b>: <i>الموقع نفسه كمورد بحث الذكاء الاصطناعي في Azure الخاص بك</i></li>
            <li><b>نظام التشغيل</b>: Windows</li>
        </ul>
    </li>
    <li>انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.</li>
    <li>
        <p>في صفحة <b>نظرة عامة</b>، حدد <b>إنشاء دالة</b> في أسفل الصفحة لإنشاء دالة جديدة بالإعدادات التالية:</p>
        <ul dir='rtl'>
            <li>
                <p><b>اختر قالبًا</b></p>
                <ul dir='rtl'>
                    <li><b>القالب</b>: مشغل HTTP  </li>
                </ul>
            </li>
            <li>
                <p><b>تفاصيل القالب</b>:</p>
                <ul dir='rtl'>
                    <li><b>اسم الدالة</b>: عدد الكلمات</li>
                    <li><b>مستوى التخويل</b> الدالة</li>
                </ul>
            </li>
        </ul>
        <blockquote><b>ملاحظة</b>: إذا تلقيت خطأ إنشاء دالة، فيرجى تحديث الصفحة ويجب إنشاء المورد كما هو متوقع.</blockquote>
    </li>
    <li>انتظر حتى يتم إنشاء دالة <i>عدد الكلمات</i>. ثم في صفحتها، حدد علامة التبويب <b>Code + Test</b> .</li>
    <li>استبدل رمز الوظيفة الافتراضية بالكود التالي:</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>module.exports = async function (context, req) {
    context.log('JavaScript HTTP trigger function processed a request.');
<br>
    if (req.body && req.body.values) {
<br>
        vals = req.body.values;
<br>
        // Array of stop words to be ignored
        var stopwords = ['', 'i', 'me', 'my', 'myself', 'we', 'our', 'ours', 'ourselves', 'you',
            "youre", "youve", "youll", "youd", 'your', 'yours', 'yourself',
            'yourselves', 'he', 'him', 'his', 'himself', 'she', "shes", 'her',
            'hers', 'herself', 'it', "its", 'itself', 'they', 'them',
            'their', 'theirs', 'themselves', 'what', 'which', 'who', 'whom',
            'this', 'that', "thatll", 'these', 'those', 'am', 'is', 'are', 'was',
            'were', 'be', 'been', 'being', 'have', 'has', 'had', 'having', 'do',
            'does', 'did', 'doing', 'a', 'an', 'the', 'and', 'but', 'if', 'or',
            'because', 'as', 'until', 'while', 'of', 'at', 'by', 'for', 'with',
            'about', 'against', 'between', 'into', 'through', 'during', 'before',
            'after', 'above', 'below', 'to', 'from', 'up', 'down', 'in', 'out',
            'on', 'off', 'over', 'under', 'again', 'further', 'then', 'once', 'here',
            'there', 'when', 'where', 'why', 'how', 'all', 'any', 'both', 'each',
            'few', 'more', 'most', 'other', 'some', 'such', 'no', 'nor', 'not',
            'only', 'own', 'same', 'so', 'than', 'too', 'very', 'can', 'will',
            'just', "dont", 'should', "shouldve", 'now', "arent", "couldnt",
            "didnt", "doesnt", "hadnt", "hasnt", "havent", "isnt", "mightnt", "mustnt",
            "neednt", "shant", "shouldnt", "wasnt", "werent", "wont", "wouldnt"
        ];
<br>
        res = { "values": [] };
<br>
        for (rec in vals) {
            // Get the record ID and text for this input
            resVal = { recordId: vals[rec].recordId, data: {} };
            txt = vals[rec].data.text;
<br>
            // remove punctuation and numerals
            txt = txt.replace(/[^ A-Za-z_]/g, "").toLowerCase();

            // Get an array of words
            words = txt.split(" ");

            // count instances of non-stopwords
            wordCounts = {};
            for (var i = 0; i < words.length; ++i) {
                word = words[i];
                if (stopwords.includes(word) == false) {
                    if (wordCounts[word]) {
                        wordCounts[word]++;
                    }
                    else {
                        wordCounts[word] = 1;
                    }
                }
            }
<br>
            // Convert wordcounts to an array
            var topWords = [];
            for (var word in wordCounts) {
                topWords.push([word, wordCounts[word]]);
            }

            // Sort in descending order of count
            topWords.sort(function (a, b) {
                return b[1] - a[1];
            });
<br>
            // Get the first ten words from the first array dimension
            resVal.data.text = topWords.slice(0, 9)
                .map(function (value, index) { return value[0]; });

            res.values[rec] = resVal;
        };
<br>
        context.res = {
            body: JSON.stringify(res),
            headers: {
                'Content-Type': 'application/json'
            }
        };
    }
    else {
        context.res = {
            status: 400,
            body: { "errors": [{ "message": "Invalid input" }] },
            headers: {
                'Content-Type': 'application/json'
            }
        };
    }
};
</code></pre>
    </div>
    <li>احفظ الوظيفة ثم افتح جزء <b>Test/Run</b>.</li>
    <li>في جزء <b>Test/Run</b> استبدل <b>النص الأساسي</b> الموجود بـ JSON التالية، والذي يعكس المخطط المتوقع من خلال مهارة Azure الذكاء الاصطناعي Search حيث يتم إرسال السجلات التي تحتوي على بيانات لمستند واحد أو أكثر للمعالجة: </li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>{
    "values": [
        {
            "recordId": "a1",
            "data":
            {
            "text":  "Tiger, tiger burning bright in the darkness of the night.",
            "language": "en"
            }
        },
            {
                "recordId": "a2",
                "data":
                {
                "text":  "The rain in spain stays mainly in the plains! That's where you'll find the rain!",
                "language": "en"
            }
        }
    ]
}</code></pre>
    </div>
    <li>انقر فوق <b>تشغيل</b> واعرض محتوى استجابة HTTP الذي يتم إرجاعه بواسطة الوظيفة الخاصة بك. وهذا يعكس المخطط المتوقع بواسطة Azure الذكاء الاصطناعي Search عند استخدام مهارة، حيث يتم إرجاع استجابة لكل مستند. في هذه الحالة، تتكون الاستجابة من 10 مصطلحات في كل وثيقة بترتيب تنازلي لمدى تكرار ظهورها:</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>{
    "values": [
        {
            "recordId": "a1",
            "data": {
                "text": [
                "tiger",
                "burning",
                "bright",
                "darkness",
                "night"
                ]
            }
        },
        {
            "recordId": "a2",
            "data": {
                "text": [
                    "rain",
                    "spain",
                    "stays",
                    "mainly",
                    "plains",
                    "thats",
                    "youll",
                    "find"
                ]
            }
        }
    ]
}</code></pre>
    </div>
    <li>أغلق جزء <b>Test/Run</b> وفي جزء الوظيفة <b>عدد الكلمات</b> انقر فوق <b>الحصول على عنوان URL الوظيفة</b>. ثم انسخ عنوان موقع الويب للمفتاح الافتراضي إلى الحافظة. ستحتاج إلى هذا في الإجراء التالي.</li>
</ol>


## إضافة المهارة المخصصة إلى حل البحث

الآن تحتاج إلى تضمين وظيفتك كمهارة مخصصة في مجموعة مهارات حل البحث، وتعيين النتائج التي تنتجها إلى حقل في الفهرس. 

<ol dir='rtl'>
    <li>في Visual Studio Code، في المجلد <b>02-search-skill/update-search</b>، افتح ملف <b>update-skillset.json</b> . حيث يتضمن تعريف JSON مجموعة المهارات.</li>
    <li>قم بمراجعة تعريف مجموعة المهارات. تتضمن المهارات نفسها كما كان من قبل، فضلًا عن مهارة <b>WebApiSkill</b> جديدة تسمى <b>get-top-words</b>.</li>
    <li>قم بتحرير تعريف المهارة <b>get-top-words</b> لتعيين قيمة <b>uri</b> إلى عنوان URL الخاص بوظيفة Azure لديك (التي قمت بنسخها إلى الحافظة في الإجراء السابق)، واستبدال <b>*YOUR-FUNCTION-APP-URL</b>.</li>
    <li>في الجزء العلوي من تعريف مجموعة المهارات، في <b>عنصر cognitiveServices</b>، استبدل <b>العنصر النائب YOUR_AI_SERVICES_KEY</b> بأي من مفاتيح موارد Azure الذكاء الاصطناعي Services.</li>
    <p><i>يمكنك العثور على المفاتيح في صفحة <b>المفاتيح ونقطة النهاية</b> لمورد Azure الذكاء الاصطناعي Services في مدخل Microsoft Azure.</i></p>
    <li>احفظ وأغلق ملف JSON المحدث.</li>
    <li>في مجلد <b>update-search</b>، افتح <b>update-index.json</b>. يحتوي هذا الملف على تعريف JSON للفهرس <b>margies-custom-index</b>، مع حقل إضافي يسمى <b>top_words</b> في أسفل تعريف الفهرس.</li>
    <li>راجع JSON للفهرس، ثم أغلق الملف دون إجراء أي تغييرات.</li>
    <li>في مجلد <b>update-search</b>، افتح <b>update-index.json</b>. يحتوي هذا الملف على تعريف JSON للمفهرس <b>margies-custom-indexer</b>، مع تعيين إضافي لحقل <b>top_words</b> .</li>
    <li>راجع JSON للفهرس، ثم أغلق الملف دون إجراء أي تغييرات.</li>
    <li>في مجلد <b>update-search</b>، افتح <b>update-search.cmd</b>. يستخدم هذا البرنامج النصي الدفعي الأداة المساعدة cURL لإرسال تعريفات JSON إلى واجهة REST لمورد Azure الذكاء الاصطناعي Search.</li>
    <li>
        <p>استبدل العناصر النائبة <b>YOUR_SEARCH_URL والمتغيرة <b>YOUR_ADMIN_KEY</b> بعنوان <b>URL</b> وأحد <b>مفاتيح</b> المسؤول لمورد Azure الذكاء الاصطناعي Search.</b></p>
        <p><i>يمكنك العثور على هذه القيم في صفحات <b>النظرة العامة</b> <b>والمفاتيح</b> لمورد بحث الذكاء الاصطناعي في Azure في مدخل Microsoft Azure.</i></p>
    </li>
    <li>احفظ ملف الدفعة المحدث.</li>
    <li>انقر بزر الماوس الأيمن فوق المجلد <b>update-search</b> وحدد <b>فتح في الوحدة الطرفية المتكاملة</b>.</li>
    <li>في الجزء الطرفي لمجلد <b>update-search</b>، أدخل الأمر التالي، قم بتشغيل البرنامج النصي الدفعي.</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>./update-search</code></pre>
    </div>
    <li>
        <p>عند اكتمال البرنامج النصي، في مدخل Microsoft Azure، على صفحة مورد Azure الذكاء الاصطناعي Search، حدد <b>صفحة المفهرسات</b> وانتظر حتى تكتمل عملية الفهرسة.</p>
        <p><i>يمكنك تحديد <b>تحديث</b> لتتبع تقدم عملية الفهرسة. قد يستغرق الأمر دقيقة أو نحو ذلك حتى يكتمل.</i></p>
    </li>
</ol>



## البحث في الفهرس

الآن بعد أن أصبح لديك فهرس، يمكنك البحث فيه.


<ol dir='rtl'>
    <li>في أعلى الجزء لمورد Azure الذكاء الاصطناعي Search، حدد <b>مستكشف البحث</b>.</li>
    <li>في مستكشف البحث، قم بتغيير طريقة العرض إلى <b>طريقة عرض JSON</b>، ثم أرسل استعلام البحث التالي:</li>
    <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>{
    "search": "Las Vegas",
    "select": "url,top_words"
}</code></pre>
    </div>
    <p>يسترد هذا الاستعلام حقلي <b>url</b> و<b>top_words</b> لجميع المستندات التي تشير إلى <i>Las Vegas</i>.</p>
</ol>



## التنظيف

الآن بعد أن أكملت التمرين، احذف جميع الموارد التي لم تعد بحاجة إليها. احذف موارد Azure:

<ol dir='rtl'>
    <li>في <b>مدخل Azure</b>، حدد "Resource groups".</li>
    <li>حدد مجموعة الموارد التي لا تحتاج إليها، ثم حدد <b>حذف مجموعات الموارد</b>.</li>
</ol>


## مزيد من المعلومات


للتعرّف على المزيد حول إنشاء مهارات مخصصة ل Azure الذكاء الاصطناعي Search، راجع <a href="https://docs.microsoft.com/azure/search/cognitive-search-custom-skill-interface">وثائق</a> Azure الذكاء الاصطناعي Search.
