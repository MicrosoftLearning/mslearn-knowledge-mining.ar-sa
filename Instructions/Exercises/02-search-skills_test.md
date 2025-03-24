---
lab:
  title: إنشاء مهارة مخصصة لـ Azure الذكاء الاصطناعي Search
  module: Module 12 - Creating a Knowledge Mining Solution
---

# إنشاء مهارة مخصصة لـ Azure الذكاء الاصطناعي Search

يستخدم Azure الذكاء الاصطناعي Search مسار إثراء من مهارات الذكاء الاصطناعي لاستخراج الحقول التي تم إنشاؤها الذكاء الاصطناعي من المستندات وتضمينها في فهرس بحث. هناك مجموعة شاملة من المهارات المضمنة التي يمكنك استخدامها، ولكن إذا كان لديك متطلبات محددة لا تلبيها هذه المهارات، يمكنك إنشاء مهارة مخصصة.

في هذا التمرين، ستنشئ مهارة مخصصة في جدولة تكرار الكلمات الفردية في مستند لإنشاء قائمة بالكلمات الخمسة الأولى الأكثر استخداماً، وإضافتها إلى حل بحث عن Margie's Travel - وهي وكالة سفر وهمية.

## الاستعداد لتطوير تطبيق في تعليمة Visual Studio البرمجية

ستطور تطبيق البحث لديك باستخدام Visual Studio Code. تم توفير ملفات التعليمات البرمجية لتطبيقك في GitHub repo.

> **تلميح**: إذا نسخت بالفعل مستودع **mslearn-knowledge-mining**، فافتحه في Visual Studio code. وإلا فاتبع هذه الخطوات لاستنساخه إلى بيئة تطويرك.

<ol>
<li>ابدأ تشغيل Visual Studio Code.</li>
<li>افتح لوحة (SHIFT+CTRL+P) وشغّل **Git: استنسخ الأمر ** لاستنساخ مستودع `https://github.com/MicrosoftLearning/mslearn-knowledge-mining` إلى مجلد محلي (لا يُهم أي مجلد).</li>
<li>عند استنساخ المستودع، افتح المجلد في تعليمة Visual Studio البرمجية.</li>
<li>انتظر حتى تثبيت ملفات إضافية لدعم مشاريع التعليمات البرمجية C# في المستودع.</li>
</ol>

    > **ملاحظة**: إذا جرت مطالبتك بإضافة الأصول المطلوبة للبناء وتصحيح الأخطاء، فحدد **ليس الآن**.

## إنشاء موارد Azure

> **ملاحظة**: إذا سبق أن أكملت تمرين **[إنشاء حل بحث الذكاء الاصطناعي في Azure](01-azure-search.md)**، ولا يزال لديك موارد بحث الذكاء الاصطناعي في Azure في اشتراكك، يمكنك تخطي هذا المقطع وبدء مقطع **إنشاء حل بحث**. وإلا، اتبع الخطوات أدناه لتوفير موارد Azure المطلوبة.

<ol>
<li>في مستعرض ويب، افتح مدخل Microsoft Azure في `https://portal.azure.com`، ثم سجل الدخول باستخدام حساب Microsoft المقترن باشتراك Azure لديك.</li>
<li>في شريط البحث العلوي، ابحث عن *خدمات الذكاء الاصطناعي في Azure*، وحدد **حساب خدمة متعددة لخدمات الذكاء الاصطناعي في Azure**، وأنشئ مورد حساب متعدد الخدمات لخدمات الذكاء الاصطناعي في Azure بالإعدادات التالية:</li>
</ol>
    - **Subscription**: *اشتراكك في Azure*
    - **مجموعة الموارد**: *اختر أو أنشئ مجموعة موارد (إذا كنت تستخدم اشتراكاً مقيداً، فقد لا يكون لديك إذن لإنشاء مجموعة موارد جديدة - استخدم المجموعة المتوفرة)*
    - **المنطقة**: *اختر من المناطق الجغرافية المتاحة والقريبة إليك*
    - **الاسم**: *أدخل اسماً فريداً*
    - **مستوى التسعير**: قياسي S0
<ol>
<li>بمجرد النشر، انتقل إلى المورد وفي **صفحة نظرة عامة**، لاحظ **معرّف الاشتراك** **والموقع**. ستحتاج إلى هذه القيم، إلى جانب اسم مجموعة الموارد في الخطوات اللاحقة. </li>
<li>في Visual Studio Code، قم بتوسيع مجلد **Labfiles/02-search-skill** وحدد **setup.cmd**. ستستخدم دُفعة البرنامج النصي لتشغيل أوامر واجهة سطر أوامر Azure (CLI) المطلوبة لإنشاء موارد Azure التي تحتاجها.</li>
<li>انقر بزر الماوس الأيمن فوق المجلد **02-search-skill** وحدد **فتح في الوحدة الطرفية المتكاملة**.</li>
<li>في جزء terminal، أدخِل الأمر التالي لتأسيس اتصال مصادق إلى اشتراك Azure.</li>
</ol>

    ```powershell
    az login --output none
    ```

<ol>
<li>عند المطالبة، قم بتحديد تسجيل الدخول إلى اشتراكك في Azure. ثم ارجع إلى Visual Studio Code وانتظر حتى تكتمل عملية تسجيل الدخول.</li>
<li>يمكنك تشغيل الأمر التالي لسرد مواقع Azure.</li>
</ol>

    ```powershell
    az account list-locations -o table
    ```

<ol>
<li>في المخرجات، ابحث عن قيمة **الاسم** التي تتوافق مع موقع مجموعة الموارد الخاصة بك (على سبيل المثال، بالنسبة *لشرق الولايات المتحدة*، الاسم المقابل هو *eastus*).</li>
<li>في البرنامج النصي **setup.cmd**، عليك تعديل **subscription_id**، و**resource_group**، و**location** المتغيرين باستخدام القيم المناسبة لمعرّف الاشتراك، واسم مجموعة الموارد، واسم الموقع. ثم احفظ التغييرات.</li>
<li>في المحطة الطرفية للمجلد **02-search-skill**، أدخل الأمر التالي لتشغيل البرنامج النصي:</li>
</ol>

    ```powershell
    ./setup
    ```

    > **ملاحظة**: إذا فشل البرنامج النصي، فتأكد من حفظه بأسماء المتغيرات الصحيحة وحاول مرة أخرى.

<ol>
<li>عند اكتمال البرنامج النصي، راجع المخرجات التي يعرضها ولاحظ المعلومات التالية حول موارد Azure (ستحتاج هذه القيم لاحقًا):</li>
</ol>
    - Storage account name
    - سلسلة اتصال التخزين
    - نقطة نهاية خدمة البحث
    - مفتاح مسؤول خدمة البحث
    - مفتاح الاستعلام عن خدمة البحث

<ol>
<li>في مدخل Microsoft Azure، عليك تحديث مجموعة الموارد وتحقق من أنها تحتوي على حساب مخزن Azure ومورد خدمات الذكاء الاصطناعي في Azure ومورد بحث الذكاء الاصطناعي في Azure.</li>
</ol>

## إنشاء حل بحث

الآن بعد أن أصبح لديك موارد Azure الضرورية، يمكنك إنشاء حل بحث يتكون من المكونات التالية:

- **مصدر بيانات** يشير إلى المستندات في حاوية تخزين Azure لديك.
- تحدد **مجموعة مهارات** مسار إثراء المهارات لاستخراج الحقول التي تم إنشاؤها الذكاء الاصطناعي من المستندات.
- **فهرس** يحدد مجموعة قابلة للبحث من سجلات المستندات.
- يستخرج **مفهرس** المستندات من مصدر البيانات، ويطبق مجموعة المهارات، ويملأ الفهرس.

في هذا التمرين، ستستخدم واجهة Azure الذكاء الاصطناعي Search REST لإنشاء هذه المكونات عن طريق إرسال طلبات JSON.

<ol>
<li>في Visual Studio Code، في المجلد **02-search-skill**، قم بتوسيع مجلد **create-search** وحدد **data_source.json**. يحتوي هذا الملف على تعريف JSON لمصدر بيانات يسمى **margies-custom-data**.</li>
<li>استبدل العنصر النائب **YOUR_CONNECTION_STRING** سلسلة الاتصال لحساب تخزين Azure الخاص بك، والذي يجب أن يشبه ما يلي:</li>
</ol>

    ```
    DefaultEndpointsProtocol=https;AccountName=ai102str123;AccountKey=12345abcdefg...==;EndpointSuffix=core.windows.net
    ```

    *يمكنك العثور على سلسلة الاتصال في صفحة **مفاتيح الوصول** لحساب التخزين الخاص بك في مدخل Microsoft Azure.*

<ol>
<li>احفظ ملف JSON المُحدَّث وأغلقه.</li>
<li>في مجلد **create-search**، افتح **skillset.json**. يحتوي هذا الملف على تعريف JSON لمصدر بيانات يسمى **margies-custom-skillset**.</li>
<li>في الجزء العلوي من تعريف مجموعة المهارات، في **عنصر cognitiveServices**، استبدل **العنصر النائب YOUR_AI_SERVICES_KEY** بأي من مفاتيح موارد Azure الذكاء الاصطناعي Services.</li>
</ol>

    *يمكنك العثور على المفاتيح في صفحة **المفاتيح ونقطة النهاية** لمورد Azure الذكاء الاصطناعي Services في مدخل Microsoft Azure.*

<ol>
<li>احفظ وأغلق ملف JSON المحدث.</li>
<li>في **مجلد create-search**، افتح **index.json**. يحتوي هذا الملف على تعريف JSON لفهرس يسمى **margies-custom-index**.</li>
<li>راجع JSON للفهرس، ثم أغلق الملف دون إجراء أي تغييرات.</li>
<li>في مجلد **create-search**، افتح **indexer.json**. يحتوي هذا الملف على تعريف JSON لمفهرس يسمى **margies-custom-indexer**.</li>
<li>راجع JSON للفهرس، ثم أغلق الملف دون إجراء أي تغييرات.</li>
<li>في مجلد **create-search**، افتح **create-search.cmd**. يستخدم هذا البرنامج النصي الدفعي الأداة المساعدة cURL لإرسال تعريفات JSON إلى واجهة REST لمورد بحث الذكاء الاصطناعي في Azure.</li>
<li>استبدل العناصر النائبة والمتغيرة **YOUR_SEARCH_URL** **وYOUR_ADMIN_KEY** بعنوان **Url** وأحد **مفاتيح المسؤول** لمورد بحث الذكاء الاصطناعي في Azure.</li>
</ol>

    *يمكنك العثور على هذه القيم في صفحات **النظرة العامة** **والمفاتيح** لمورد بحث الذكاء الاصطناعي في Azure في مدخل Microsoft Azure.*

<ol>
<li>احفظ ملف الدفعة المُحدَّث.</li>
<li>انقر بزر الماوس الأيمن فوق المجلد **create-search** وحدد **فتح في الوحدة الطرفية المتكاملة**.</li>
<li>في الجزء الطرفي لمجلد **create-search**، أدخل الأمر التالي وشغَّل دُفعة البرنامج النصي.</li>
</ol>

    ```powershell
    ./create-search
    ```

<ol>
<li>عند اكتمال البرنامج النصي، في مدخل Azure، على صفحة مورد بحث الذكاء الاصطناعي في Azure، حدد صفحة **المفهرسات** وانتظر حتى تكتمل عملية الفهرسة.</li>
</ol>

    *يمكنك تحديد **تحديث** لتتبع تقدم عملية الفهرسة. قد يستغرق الأمر دقيقة أو نحو ذلك حتى يكتمل.*

## البحث في الفهرس

الآن بعد أن أصبح لديك فهرس، يمكنك البحث فيه.

<ol>
<li>في أعلى الجزء لمورد Azure الذكاء الاصطناعي Search، حدد **مستكشف البحث**.</li>
<li>في مستكشف البحث، في **مربع استعلام** الاستعلام، أدخل سلسلة الاستعلام التالية، ثم حدد **بحث**.</li>
</ol>

    ```
    search=London&$select=url,sentiment,keyphrases&$filter=metadata_author eq 'Reviewer' and sentiment eq 'positive'
    ```

    يسترد هذا الاستعلام عنوان **URL** **والمشاعر** **وعبارات** المفاتيح لجميع المستندات التي تشير إلى *لندن* التي ألفها *المراجع* التي تحمل وصفا إيجابيا **للتوجه** (بمعنى آخر، المراجعات الإيجابية التي تذكر لندن)

## إنشاء دالة Azure لمهارة مخصصة

يتضمن حل البحث عددا من المهارات الذكاء الاصطناعي المضمنة التي تثري الفهرس بمعلومات من المستندات، مثل درجات التوجه وقوائم العبارات الرئيسية التي شوهدت في المهمة السابقة.

يمكنك تحسين الفهرس بشكل أكبر من خلال إنشاء مهارات مخصصة. على سبيل المثال، قد يكون من المفيد تحديد الكلمات التي يتم استخدامها بشكل متكرر في كل مستند، ولكن لا توجد مهارة مضمنة توفر هذه الوظيفة.

لتنفيذ وظيفة عدد الكلمات كمهارة مخصصة، ستقوم بإنشاء دالة Azure باللغة المفضلة لديك.

> **ملاحظة**: في هذا التمرين، ستقوم بإنشاء دالة Node.JS بسيطة باستخدام إمكانات تحرير التعليمات البرمجية في مدخل Azure. في حل الإنتاج، عادة ما تستخدم بيئة تطوير مثل Visual Studio Code لإنشاء تطبيق دالة بلغتك المفضلة (على سبيل المثال C# أو Python أو Node.JS أو Java) ونشره على Azure كجزء من عملية DevOps.

<ol>
<li>في مدخل Microsoft Azure، في **الصفحة الرئيسية**، أنشئ مورد **Function App** جديدا بالإعدادات التالية:</li>
</ol>
    - **خطة الاستضافة**: الاستهلاك
    - **اشتراك**: *اشتراكك*
    - **مجموعة الموارد**: *مجموعة الموارد نفسها مثل مورد بحث الذكاء الاصطناعي في Azure الخاص بك*
    - **اسم Function App**: *اسم فريد*
    - **مكدس وقت التشغيل**: Node.js
    - **الإصدار**: 18 LTS
    - **المنطقة**: *الموقع نفسه كمورد بحث الذكاء الاصطناعي في Azure الخاص بك*
    - **نظام التشغيل**: Windows

<ol>
<li>انتظر حتى يكتمل النشر، ثم انتقل إلى المورد المنشور.</li>
<li>في صفحة **نظرة عامة**، حدد **إنشاء دالة** في أسفل الصفحة لإنشاء دالة جديدة بالإعدادات التالية:</li>
</ol>
    - **اختر قالبًا**
        - **القالب**: مشغل HTTP    
    - **تفاصيل القالب**:
        - **اسم الدالة**: عدد الكلمات
        - **مستوى التخويل** الدالة

    > **ملاحظة**: إذا تلقيت خطأ إنشاء دالة، فيرجى تحديث الصفحة ويجب إنشاء المورد كما هو متوقع.

<ol>
<li>انتظر حتى يتم إنشاء دالة *عدد الكلمات*. ثم في صفحتها، حدد علامة التبويب **Code + Test** .</li>
<li>استبدل رمز الوظيفة الافتراضية بالكود التالي:</li>
</ol>

```javascript
module.exports = async function (context, req) {
    context.log('JavaScript HTTP trigger function processed a request.');

    if (req.body && req.body.values) {

        vals = req.body.values;

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
        "neednt", "shant", "shouldnt", "wasnt", "werent", "wont", "wouldnt"];

        res = {"values":[]};

        for (rec in vals)
        {
            // Get the record ID and text for this input
            resVal = {recordId:vals[rec].recordId, data:{}};
            txt = vals[rec].data.text;

            // remove punctuation and numerals
            txt = txt.replace(/[^ A-Za-z_]/g,"").toLowerCase();

            // Get an array of words
            words = txt.split(" ")

            // count instances of non-stopwords
            wordCounts = {}
            for(var i = 0; i < words.length; ++i) {
                word = words[i];
                if (stopwords.includes(word) == false )
                {
                    if (wordCounts[word])
                    {
                        wordCounts[word] ++;
                    }
                    else
                    {
                        wordCounts[word] = 1;
                    }
                }
            }

            // Convert wordcounts to an array
            var topWords = [];
            for (var word in wordCounts) {
                topWords.push([word, wordCounts[word]]);
            }

            // Sort in descending order of count
            topWords.sort(function(a, b) {
                return b[1] - a[1];
            });

            // Get the first ten words from the first array dimension
            resVal.data.text = topWords.slice(0,9)
              .map(function(value,index) { return value[0]; });

            res.values[rec] = resVal;
        };

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
            body: {"errors":[{"message": "Invalid input"}]},
            headers: {
            'Content-Type': 'application/json'
        }

        };
    }
};
```

<ol>
<li>احفظ الوظيفة ثم افتح جزء **Test/Run**.</li>
<li>في جزء **Test/Run** استبدل **النص الأساسي** الموجود بـ JSON التالية، والذي يعكس المخطط المتوقع من خلال مهارة Azure الذكاء الاصطناعي Search حيث يتم إرسال السجلات التي تحتوي على بيانات لمستند واحد أو أكثر للمعالجة:</li>
</ol>

    ```json
    {
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
    }
    ```

<ol>
<li>انقر فوق **تشغيل** واعرض محتوى استجابة HTTP الذي يتم إرجاعه بواسطة الوظيفة الخاصة بك. وهذا يعكس المخطط المتوقع بواسطة Azure الذكاء الاصطناعي Search عند استخدام مهارة، حيث يتم إرجاع استجابة لكل مستند. في هذه الحالة، تتكون الاستجابة من 10 مصطلحات في كل وثيقة بترتيب تنازلي لمدى تكرار ظهورها:</li>
</ol>

    ```json
    {
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
    }
    ```

<ol>
<li>أغلق جزء **Test/Run** وفي جزء الوظيفة **عدد الكلمات** انقر فوق **الحصول على عنوان URL الوظيفة**. ثم انسخ عنوان موقع الويب للمفتاح الافتراضي إلى الحافظة. ستحتاج إلى هذا في الإجراء التالي.</li>
</ol>

## إضافة المهارة المخصصة إلى حل البحث

الآن تحتاج إلى تضمين وظيفتك كمهارة مخصصة في مجموعة مهارات حل البحث، وتعيين النتائج التي تنتجها إلى حقل في الفهرس. 

<ol>
<li>في Visual Studio Code، في المجلد **02-search-skill/update-search**، افتح ملف **update-skillset.json** . حيث يتضمن تعريف JSON مجموعة المهارات.</li>
<li>قم بمراجعة تعريف مجموعة المهارات. تتضمن المهارات نفسها كما كان من قبل، فضلًا عن مهارة **WebApiSkill** جديدة تسمى **get-top-words**.</li>
<li>قم بتحرير تعريف المهارة **get-top-words** لتعيين قيمة **uri** إلى عنوان URL الخاص بوظيفة Azure لديك (التي قمت بنسخها إلى الحافظة في الإجراء السابق)، واستبدال ***YOUR-FUNCTION-APP-URL**.</li>
<li>في الجزء العلوي من تعريف مجموعة المهارات، في **عنصر cognitiveServices**، استبدل **العنصر النائب YOUR_AI_SERVICES_KEY** بأي من مفاتيح موارد Azure الذكاء الاصطناعي Services.</li>
</ol>

    *يمكنك العثور على المفاتيح في صفحة **المفاتيح ونقطة النهاية** لمورد Azure الذكاء الاصطناعي Services في مدخل Microsoft Azure.*

<ol>
<li>احفظ وأغلق ملف JSON المحدث.</li>
<li>في مجلد **update-search**، افتح **update-index.json**. يحتوي هذا الملف على تعريف JSON للفهرس **margies-custom-index**، مع حقل إضافي يسمى **top_words** في أسفل تعريف الفهرس.</li>
<li>راجع JSON للفهرس، ثم أغلق الملف دون إجراء أي تغييرات.</li>
<li>في مجلد **update-search**، افتح **update-index.json**. يحتوي هذا الملف على تعريف JSON للمفهرس **margies-custom-indexer**، مع تعيين إضافي لحقل **top_words** .</li>
<li>راجع JSON للفهرس، ثم أغلق الملف دون إجراء أي تغييرات.</li>
<li>في مجلد **update-search**، افتح **update-search.cmd**. يستخدم هذا البرنامج النصي الدفعي الأداة المساعدة cURL لإرسال تعريفات JSON إلى واجهة REST لمورد Azure الذكاء الاصطناعي Search.</li>
<li>استبدل العناصر النائبة **YOUR_SEARCH_URL والمتغيرة **YOUR_ADMIN_KEY** بعنوان **URL** وأحد **مفاتيح** المسؤول لمورد Azure الذكاء الاصطناعي Search.**</li>
</ol>

    *يمكنك العثور على هذه القيم في صفحات **النظرة العامة** **والمفاتيح** لمورد بحث الذكاء الاصطناعي في Azure في مدخل Microsoft Azure.*

<ol>
<li>احفظ ملف الدفعة المحدث.</li>
<li>انقر بزر الماوس الأيمن فوق المجلد **update-search** وحدد **فتح في الوحدة الطرفية المتكاملة**.</li>
<li>في الجزء الطرفي لمجلد **update-search**، أدخل الأمر التالي، قم بتشغيل البرنامج النصي الدفعي.</li>
</ol>

    ```powershell
    ./update-search
    ```

<ol>
<li>عند اكتمال البرنامج النصي، في مدخل Microsoft Azure، على صفحة مورد Azure الذكاء الاصطناعي Search، حدد **صفحة المفهرسات** وانتظر حتى تكتمل عملية الفهرسة.</li>
</ol>

    *يمكنك تحديد **تحديث** لتتبع تقدم عملية الفهرسة. قد يستغرق الأمر دقيقة أو نحو ذلك حتى يكتمل.*

## البحث في الفهرس

الآن بعد أن أصبح لديك فهرس، يمكنك البحث فيه.

<ol>
<li>في أعلى الجزء لمورد Azure الذكاء الاصطناعي Search، حدد **مستكشف البحث**.</li>
<li>في مستكشف البحث، قم بتغيير طريقة العرض إلى **طريقة عرض JSON**، ثم أرسل استعلام البحث التالي:</li>
</ol>

    ```json
    {
      "search": "Las Vegas",
      "select": "url,top_words"
    }
    ```

    يسترد هذا الاستعلام حقلي **url** و**top_words** لجميع المستندات التي تشير إلى *Las Vegas*.

## التنظيف

الآن بعد أن أكملت التمرين، احذف جميع الموارد التي لم تعد بحاجة إليها. احذف موارد Azure:

<ol>
<li>في **مدخل Azure**، حدد "Resource groups".</li>
<li>حدد مجموعة الموارد التي لا تحتاج إليها، ثم حدد **حذف مجموعات الموارد**.</li>
</ol>

## مزيد من المعلومات

للتعرّف على المزيد حول إنشاء مهارات مخصصة ل Azure الذكاء الاصطناعي Search، راجع [وثائق](https://docs.microsoft.com/azure/search/cognitive-search-custom-skill-interface) Azure الذكاء الاصطناعي Search.
