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
  <td><div dir="auto">إثراء فهرس بحث باستخدام نموذج التعلم الآلي من Azure</div></td>
  </tr>
  </tbody>
</table>
</div></td>
  </tr>
  </tbody>
</table>
</div>

# إثراء فهرس بحث باستخدام نموذج التعلم الآلي من Azure

يمكنك استخدام قوة التعلم الآلي لإثراء فهرس البحث. لإجراء ذلك، ستستخدم نموذجاً مُدرباً في استوديو التعلم الآلي للذكاء الاصطناعي في Azure وتستدعيه من مجموعة مهارات مُخصَّصة للتعلم الآلي.

في هذا التمرين، ستنشئ نموذج Azure AI Machine Learning Studio، ثم عليك تدريب نقطة نهاية ونشرها واختبارها باستخدام النموذج. بعد ذلك، ستنشئ خدمة البحث المعرفي في Azure وبيانات نموذجية، وتثري فهرس باستخدام نقطة نهاية Azure AI Machine Learning studio.

> <b>ملاحظة</b>: لإكمال هذا التمرين، ستحتاج إلى اشتراك Microsoft Azure. إذا لم يكن لديك اشتراك بالفعل، يمكنك التسجيل للحصول على الإصدار التجريبي على [https://azure.com/free](https://azure.com/free?azure-portal=true) .
>

## إنشاء مساحة عمل "التعلم الآلي من Azure"

قبل أن تثري فهرس البحث خاصتك، بادر بإنشاء مساحة عمل التعلم الآلي من Azure. ستمنحك مساحة العمل إمكانية الوصول إلى Azure AI Machine Learning studio، وهو أداة رسومية يمكنك استخدامها لإنشاء نماذج الذكاء الاصطناعي ونشرها للاستخدام.

<ol dir='rtl'>
  <li>قم بتسجيل الدخول إلى <a href="https://portal.azure.com">مدخل Azure</a>.</li>
  <li>حدد <b>+ Create a resource</b>.</li>
  <li>ابحث عن التعلم الآلي، ثم حدد <b>Azure Machine Learning</b>.</li>
  <li>حدد <b>إنشاء</b>.</li>
  <li>حدد <b>إنشاء جديد</b> ضمن <b>مجموعة الموارد</b> وعليك تسميتها <b>aml-for-acs-enrichment</b>.</li>
  <li>في قسم تفاصيل مساحة العمل، بالنسبة <b>للاسم</b>، أدخل <b>aml-for-acs-workspace</b>.</li>
  <li>حدد <b>منطقة</b> مدعومة بالقرب منك.</li>
  <li>استخدم القيم الافتراضية <b>لحساب التخزين</b>، <b>ومخزن المفاتيح</b>، <b>ونتائج تحليلات التطبيقات</b>، <b>وتسجيل الحاوية</b>.</li>
  <li>حدد "<b>Review + create</b>".</li>
  <li>حدد <b>إنشاء</b>.</li>
  <li>انتظر حتى يتم توزيع مساحة عمل التعلم الآلي من Azure، ثم حدد <b>Go to resource</b>.</li>
  <li>في الجزء "Overview"، حدد <b>Launch studio</b>.</li>
</ol>


## إنشاء البنية الأساسية لبرنامج ربط العمليات التجارية الخاصة بتدريب التراجع

ستنشئ الآن نموذج انحدار وتدربه باستخدام مسار Azure AI Machine Learning Studio. ستدرب نموذجك على بيانات أسعار السيارات. سيتنبأ النموذج بمجرد تدريبه بسعر السيارة بناء على سماتها.

<ol dir='rtl'>
  <li>في الصفحة الرئيسية، حدد <b>Designer</b>.</li>
  <li>من قائمة المكونات التي تم إنشاؤها مسبقاً، حدد <b>Regression - Automobile Price Prediction (Basic)</b>.</li>
  <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/select-pre-built-components-new.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/select-pre-built-components-new.png" alt="لقطة شاشة تظهر تحديد نموذج التراجع الذي تم إنشاؤه مسبقاً."></a></p>
  <li>حدد <b>التحقق من الصحة</b>.</li>
  <li>في جزء <b>التحقق من صحة الرسم البياني</b>، حدد الخطأ <b>تحديد هدف الحساب في معالج الإرسال</b>.</li>
  <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/create-compute-instance-new.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/create-compute-instance-new.png" alt="لقطة شاشة توضح كيفية إنشاء مثيل حساب لتدريب النموذج."></a></p>
  <li>في القائمة المنسدلة <b>تحديد نوع الحوسبة</b>، اختر <b>حساب المثيل</b>. ثم حدد <b>إنشاء مثيل حساب Azure ML</b> بالأسفل.</li>
  <li>في حقل <b>اسم الحوسبة</b>، أدخل اسماً فريداً (مثل <b>حساب للتدريب</b>).</li>
  <li>حدد <b>Review + create</b>، ثم حدد <b>Create</b>.</li>
  <li>في الحقل <b>تحديد مثيل حساب Azure ML</b>، حدد المثيل الخاص بك من القائمة المنسدلة. قد تحتاج إلى الانتظار حتى ينتهي من التوفير.</li>
  <li>حدد <b>التحقق من الصحة</b> مرة أخرى، يجب أن يبدو تدفقات المبيعات جيداً.</li>
  <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/submit-pipeline.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/submit-pipeline.png" alt='لقطة شاشة تعرض البنية الأساسية لبرنامج ربط العمليات التجارية التي تبدو جيدةً، وتمييز الزر  "Submit".'></a></p>
  <li>
    <p>حدد <b>الأساسيات</b> في <b>جزء إعداد تدفقات المبيعات</b>.</p>
    <blockquote>ملاحظة: إذا قمت بإخفاء جزء <b>وظيفة إعداد البنية الأساسية لبرنامج ربط العمليات التجارية</b> من قبل، يمكنك فتحه مرة أخرى عن طريق تحديد <b>تكوين وإرسال</b></blockquote>
  </li>
  <li>حدد <b>إنشاء جديد</b> تحت اسم التجربة.</li>
  <li>في <b>New experiment name</b>، أدخِل <b>linear-regression-training</b>.</li>
  <li>حدد <b>مراجعة + إرسال</b>، ثم حدد <b>إرسال</b>.</li>
</ol>


### إنشاء نظام مجموعة استدلال لنقطة النهاية

بينما تدرب بنيتك الأساسية لبرنامج ربط العمليات التجارية نموذج التراجع الخطي، يمكنك إنشاء الموارد التي تحتاج إليها لنقطة النهاية. تحتاج نقطة النهاية هذه إلى نظام مجموعة Kubernetes لمعالجة طلبات الويب إلى نموذجك الخاص.

<ol dir='rtl'>
  <li>على اليسار، حدد <b>حساب</b>.</li>
  <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/create-inference-cluster-new.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/create-inference-cluster-new.png" alt='لقطة شاشة توضح كيفية إنشاء نظام مجموعة استدلال جديد.'></a></p>
  <li>حدد <b>مجموعات Kubernetes</b>، ثم حدد <b>+ جديد</b>.</li>
  <li>في القائمة المنسدلة، حدد <b>AksCompute</b>.</li>
  <li>في جزء <b>إنشاء AksCompute</b>، حدد <b>إنشاء مجلد جديد</b>.</li>
  <li>بالنسبة <b>للمنطقة</b>، حدد نفس المنطقة التي استخدمتها لإنشاء مواردك الأخرى.</li>
  <li>في قائمة أحجام الأجهزة الظاهرية، حدد <b>Standard_A2_v2</b>.</li>
  <li>حدد <b>التالي</b>.</li>
  <li>في <b>Compute name</b>، أدخل <b>aml-acs-endpoint</b>.</li>
  <li>حدد <b>Enable SSL configuration</b>.</li>
  <li>في <b>Leaf domain</b>، أدخِل <b>aml-for-acs</b>.</li>
  <li>حدد <b>إنشاء</b>.</li>
</ol>



### تسجيل نموذجك المُدرَّب

يجب أن تكون مهمة البنية الأساسية لبرنامج ربط العمليات التجارية خاصتك قد انتهت. ستنزل الملفين <code>score.py</code> و<code>conda_env.yaml</code>. ثم ستسجل نموذجك المُدرب.

<ol dir='rtl'>
  <li>على اليمين، حدد <b>المهام</b>.</li>
  <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/completed-pipeline-new.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/completed-pipeline-new.png" alt='لقطة شاشة تعرض وظيفة البنية الأساسية لبرنامج ربط العمليات التجارية المكتملة.'></a></p>
  <li>حدد تجربتك، ثم حدد مهمتك المكتملة في الجدول، على سبيل المثال، <b>الانحدار - التنبؤ بسعر السيارة (أساسي)</b>. إذا جرت مطالبتك بحفظ التغييرات، فحدد <b>تجاهل</b> للتغييرات.</li>
  <li>في المصمم، حدد <b>نظرة عامة</b> على الوظيفة في الجزء العلوي الأيسر، ثم حدد عقدة <b>نموذج القطار</b>.</li>
  <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/download-score-conda.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/download-score-conda.png" alt='لقطة شاشة تعرض كيفية تنزيل score.py.'></a></p>
  <li>في علامة تبويب <b>المخرجات + السجلات</b>، وسع المجلد <b>trained_model_outputs</b>.</li>
  <li>بجوار <code>score.py</code>، حدد قائمة المزيد (<b>...</b>)، ثم حدد <b>تنزيل</b>.</li>
  <li>بجوار <code>conda_env.yaml</code>، حدد قائمة المزيد (<b>...</b>)، ثم حدد <b>تنزيل</b>.</li>
  <li>حدد <b>+ نموذج التسجيل</b> في أعلى علامة التبويب.</li>
  <li>في حقل <b>مخرجات المهمة</b>، حدد المجلد <b>trained_model_outputs</b>. حدد <b>التالي</b> في أسفل الجزء.</li>
  <li>بالنسبة إلى <b>اسم</b> النموذج، أدخل <b>Carevalmodel</b>.</li>
  <li>في <b>الوصف</b>، أدخل <b>نموذج الانحدار الخطي للتنبؤ بأسعار السيارات.</b>.</li>
  <li>حدد <b>التالي</b>.</li>
  <li>حدد <b>تسجيل</b>.</li>
</ol>


### يمكنك تحرير البرنامج النصي للتسجيل للرد على بحث الذكاء الاصطناعي في Azure بشكل صحيح

نزل Azure Machine Learning Studio ملفين إلى موقع التنزيل الافتراضي لمستعرض الويب الخاص بك. تحتاج إلى تحرير ملف score.py لتغيير كيفية معالجة طلب JSON والاستجابة له. يمكنك استخدام محرر نصوص أو محرر تعليمات برمجية مثل Visual Studio Code.

<ol dir='rtl'>
  <li>في محررك، افتح ملف score.py.</li>
  <li>
    <p>استبدل جميع محتويات دالة التشغيل:</p>
  </li>
  <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>def run(data):
data = json.loads(data)
input_entry = defaultdict(list)
for row in data:
  for key, val in row.items():
    input_entry[key].append(decode_nan(val))
<br>
data_frame_directory = create_dfd_from_dict(input_entry, schema_data)
score_module = ScoreModelModule()
result, = score_module.run(
  learner=model,
  test_data=DataTable.from_dfd(data_frame_directory),
  append_or_result_only=True)
return json.dumps({"result": result.data_frame.values.tolist()})</code></pre>
  </div>
  <p>باستخدام التعليمة البرمجية Python هذا:</p>
  <div style="text-align: left; direction: ltr; margin: 0 20px;">
  <pre><code>def run(data):
  data = json.loads(data)
  input_entry = defaultdict(list)
<br>       
  for key, val in data.items():
    input_entry[key].append(decode_nan(val))
<br>    
data_frame_directory = create_dfd_from_dict(input_entry, schema_data)
score_module = ScoreModelModule()
result, = score_module.run(
  learner=model,
  test_data=DataTable.from_dfd(data_frame_directory),
  append_or_result_only=True)
output = result.data_frame.values.tolist()
<br>        
return {
  "predicted_price": output[0][-1]
}</code></pre>
  </div>
    <p>تسمح التغييرات أعلاه للوضع باستلام عنصر JSON واحد مع سمات السيارة بدلاً من صفيف من السيارات.</p>
    <p>التغيير الآخر هو إرجاع السعر المتوقع للسيارة فقط بدلاً من استجابة JSON بأكملها.</p>
  <li>احفظ التغييرات في محرر النص خاصتك.</li>
</ol>



## إنشاء بيئة مخصصة

بعد ذلك، ستنشئ بيئة مخصصة حتى تتمكن من النشر إلى نقطة نهاية في الوقت الفعلي.

<ol dir='rtl'>
  <li>حدد <b>البيئات‏‎</b> في جزء التنقل.</li>
  <li>حدد علامة التبويب <b>بيئات مخصصة</b>.</li>
  <li>حدد <b>+ إنشاء</b>.</li>
  <li>بالنسبة <b>للاسم</b>، أدخل <b>my-custom-environment</b>.</li>
  <li>في قائمة <i>البيئات المنسقة</i> ضمن <b>تحديد نوع البيئة</b>، حدد أحدث إصدار من <b>automl-gpu</b>.</li>
  <li>حدد <b>التالي</b>.</li>
  <li>على جهازك المحلي، افتح ملف <code>conda_env.yaml</code> الذي نزلته مسبقاً وانسخ محتوياته.</li>
  <li>ارجع إلى المستعرض، وحدد <b>conda_dependencies.yaml</b> في جزء تخصيص.</li>
  <li>في الجزء الموجود على اليمين، استبدل محتوياته بالتعليمات البرمجية التي نسختها سابقاً.</li>
  <li>حدد <b>التالي</b>، ثم حدد <b>التالي</b> مرة أخرى.</li>
  <li>حدد <b>إنشاء</b> لإنشاء بيئتك المخصصة.</li>
</ol>



## توزيع النموذج باستخدام التعليمات البرمجية المُحدَّثة لتسجيل النقاط <!--Option for web service deployment is greyed out. Can't go further after trying several different things.-->

يجب أن يكون نظام مجموعة الاستدلال خاصتك جاهزاً للاستخدام الآن. لقد حررت أيضاً التعليمات البرمجية الخاصة بتسجيل النقاط لمعالجة الطلبات من مجموعة المهارات المخصصة لـ Azure Cognitive Search. لننشئ نقطة نهاية للنموذج ونختبرها.

<ol dir='rtl'>
  <li>على اليسار، حدد <b>Models</b>.</li>
  <li>حدد النموذج الذي سجلته، <b>carevalmodel</b>.</li>
  <li>حدد <b>نشر</b>، ثم حدد <b>نقطة نهاية الوقت الفعلي</b>.</li>
  <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/04-select-endpoint.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/04-select-endpoint.png" alt='لقطة شاشة لجزء تحديد نقطة النهاية.'></a></p>
  <li>بالنسبة إلى <b>اسم نقطة النهاية</b>، أدخل اسمًا فريدًا، على سبيل المثال <b>car-evaluation-endpoint-1440637584</b>.</li>
  <li>بالنسبة إلى <b>نوع الحوسبة</b>، حدد <b>المدارة</b>.</li>
  <li>بالنسبة إلى <b>نوع المصادقة</b>، حدد <b>يعتمد على المفتاح</b>.</li>
  <li>حدد <b>التالي</b>، ثم حدد <b>التالي</b>.</li>
  <li>حدد <b>التالي</b> مرة أخرى.</li>
  <li>في الحقل <b>تحديد برنامج نصي للتسجيل للاستدلال</b>، استعرض وصولاً إلى الملف المحدث <code>score.py</code> لديك وحدده.</li>
  <li>في القائمة المنسدلة <b>تحديد نوع البيئة</b>، حدد <b>البيئات المخصصة</b>.</li>
  <li>حدد خانة الاختيار على البيئة المخصصة من القائمة.</li>
  <li>حدد <b>التالي</b>.</li>
  <li>بالنسبة للجهاز الظاهري، حدد <b>Standard_D2as_v4</b>.</li>
  <li>تعيين <b>عدد المثيلات</b> إلى <b>1</b>.</li>
  <li>حدد <b>التالي</b>، ثم حدد <b>التالي</b> مرة أخرى.</li>
  <li>حدد <b>إنشاء</b>.</li>
  <p>انتظر حتى توزيع النموذج، فقد يستغرق الأمر ما يصل إلى 10 دقائق. يمكنك التحقق من الحالة في قسم <b>الإشعارات</b> أو نقاط النهاية في Azure Machine Learning Studio.</p>
</ol>

### اختبار نقطة نهاية النموذج المُدرَّب خاصتك

<ol dir='rtl'>
  <li>على اليمين، حدد <b>نقاط النهاية</b>.</li>
  <li>حدد <b>car-evaluation-endpoint</b>.</li>
  <li>حدد <b>اختبار</b>، في <b>إدخال البيانات لاختبار نقطة النهاية</b>، الصق هذا المثال JSON.</li>
  <div style="text-align: left; direction: ltr; margin: 0 20px;">
  <pre><code>{
  "symboling": 2,
  "make": "mitsubishi",
  "fuel-type": "gas",
  "aspiration": "std",
  "num-of-doors": "two",
  "body-style": "hatchback",
  "drive-wheels": "fwd",
  "engine-location": "front",
  "wheel-base": 93.7,
  "length": 157.3,
  "width": 64.4,
  "height": 50.8,
  "curb-weight": 1944,
  "engine-type": "ohc",
  "num-of-cylinders": "four",
  "engine-size": 92,
  "fuel-system": "2bbl",
  "bore": 2.97,
  "stroke": 3.23,
  "compression-ratio": 9.4,
  "horsepower": 68.0,
  "peak-rpm": 5500.0,
  "city-mpg": 31,
  "highway-mpg": 38,
  "price": 0.0
}</code></pre>
  </div>
  <li>حدد <b>اختبار</b>، وينبغي أن تشاهد استجابة:</li>
  <div style="text-align: left; direction: ltr; margin: 0 20px;">
  <pre><code>{
  "predicted_price": 5852.823214312815
}</code></pre>
  </div>
  <li>حدد <b>Consume</b>.</li>
  <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/copy-rest-endpoint.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/copy-rest-endpoint.png" alt='لقطة شاشة توضح كيفية نسخ نقطة نهاية REST والمفتاح الأساسي.'></a></p>
  <li>انسخ <b>REST endpoint</b>.</li>
  <li>انسخ <b>Primary key</b>.</li>
</ol>


### دمج نموذج Azure Machine Learning مع بحث الذكاء الاصطناعي في Azure

بعد ذلك، يمكنك إنشاء خدمة بحث معرفي جديدة وإثراء الفهرس باستخدام مجموعة مهارات مخصصة.

### إنشاء ملف اختبار

<ol dir='rtl'>
  <li>في <a href="https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true">مدخل Azure</a>، حدد "Resource groups".</li>
  <li>حدد <b>aml-for-acs-enrichment</b>.</li>
  <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/navigate-storage-account.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/navigate-storage-account.png" alt='لقطة شاشة تعرض كيفية إنشاء حساب تخزين في مدخل Azure.'></a></p>
  <li>حدد حساب التخزين، على سبيل المثال <b>amlforacsworks1440637584</b>.</li>
  <li>حدد <b>تكوين</b> ضمن <b>الإعدادات</b>. ثم عليك تعيين <b>السماح بالوصول المجهول للكائن الثنائي كبير الحجم</b> إلى <b>مُمكّن</b>.</li>
  <li>حدد <b>حفظ</b>.</li>
  <li>ضمن <b>Data storage</b>، حدد <b>Containers</b>.</li>
  <li>أنشئ حاوية جديدة لتخزين بيانات الفهرس، وحدد <b>+ Container</b>.</li>
  <li>في الجزء <b>New container</b> في <b>Name</b>، أدخِل <b>docs-to-search</b>.</li>
  <li>في <b>مستوى الوصول المجهول</b>، حدد <b>الحاوية (وصول مجهول للقراءة للحاويات والوحدات الثنائية الكبيرة)</b>.</li>
  <li>حدد <b>إنشاء</b>.</li>
  <li>حدد حاوية <b>docs-to-search</b> التي أنشأتها.</li>
  <li>
    <p>في محرر النص، أنشئ مستند JSON:</p>
  </li>
  <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>{
  "symboling": 0,
  "make": "toyota",
  "fueltype": "gas",
  "aspiration": "std",
  "numdoors": "four",
  "bodystyle": "wagon",
  "drivewheels": "fwd",
  "enginelocation": "front",
  "wheelbase": 95.7,
  "length": 169.7,
  "width": 63.6,
  "height": 59.1,
  "curbweight": 2280,
  "enginetype": "ohc",
  "numcylinders": "four",
  "enginesize": 92,
  "fuelsystem": "2bbl",
  "bore": 3.05,
  "stroke": 3.03,
  "compressionratio": 9.0,
  "horsepower": 62.0,
  "peakrpm": 4800.0,
  "citympg": 31,
  "highwaympg": 37,
  "price": 0
}</code></pre>
  </div>
    <p>احفظ المستند إلى جهازك كملحق <code>test-car.json</code>.</p>
  <li>في المدخل، حدد <b>Upload</b>.</li>
  <li>في جزء <b>تحميل كائن ثنائي كبير الحجم</b>، حدد <b>مستعرضات الملفات</b>، وانتقل إلى المكان الذي حفظت فيه مستند JSON، ثم حدده.</li>
  <li>حدد <b>تحميل</b>.</li>
</ol>



### إنشاء مورد كلام الذكاء الاصطناعي في Azure

<ol dir='rtl'>
  <li>في مدخل Azure، في الصفحة الرئيسية، حدد <b>+ إنشاء مورد</b>.</li>
  <li>ابحث عن <b>بحث الذكاء الاصطناعي في Azure</b> ثم حدد <b>بحث الذكاء الاصطناعي في Azure</b>.</li>
  <li>حدد <b>إنشاء</b>.</li>
  <li>في <b>Resource Group</b>، حدد <b>aml-for-acs-enrichment</b>.</li>
  <li>في اسم الخدمة، أدخل اسماً فريداً، على سبيل المثال <b>acs-enriched-1440637584</b>.</li>
  <li>بالنسبة إلى <b>الموقع</b>، حدد المنطقة نفسها التي استخدمتها سابقاً.</li>
  <li>حدد <b>Review + create</b>، ثم حدد <b>Create</b>.</li>
  <li>انتظر حتى يتم توزيع الموارد، ثم حدد <b>Go to resource</b>.</li>
  <li>حدد <b>Import data</b>.</li>
  <li>في جزء <b>الاتصال ببياناتك</b>، بالنسبة لحقل <b>مصدر البيانات</b>، حدد <b>Azure Blob Storage</b>.</li>
  <li>في <b>اسم مصدر البيانات</b>، حدد <b>import-docs</b>.</li>
  <li>في <b>Parsing mode</b>، حدد <b>JSON</b>.</li>
  <li>في <b>Connection string</b>: حدد <b>Choose an existing connection</b>.</li>
  <li>حدد حساب التخزين الذي حملت إليه، على سبيل المثال، <b>amlforacsworks1440637584</b>.</li>
  <li>في الجزء <b>Containers</b>، حدد <b>docs-to-search</b>. </li>
  <li>حدد <b>تحديد</b>.</li>
  <li>حدد <b>Next: Add cognitive skills (Optional)</b>.</li>
</ol>


### إضافة مهارات معرفية

<ol dir='rtl'>
  <li>بادر بتوسيع <b>Add enrichments</b>، ثم حدد <b>Extract people names</b>.</li>
  <li>حدد <b>Next: Customize target index</b>.</li>
  <li>حدد <b>+ إضافة حقل</b>، وفي <b>اسم الحقل</b>، أدخل <b>predicted_price</b> في أسفل القائمة.</li>
  <li>في <b>النوع</b>، حدد <b>Edm.Double</b> للإدخال الجديد.</li>
  <li>حدد <b>Retrievable</b> لجميع الحقول.</li>
  <li>حدد <b>قابل للبحث</b> <b>للإعداد</b>.</li>
  <li>حدد <b>التالي: إنشاء مفهرس</b>.</li>
  <li>حدد <b>إرسال</b>.</li>
</ol>


## إضافة AML Skill إلى مجموعة المهارات

ستحل الآن محل إثراء أسماء الأشخاص مجموعة المهارات المُخصصة من Azure Machine Learning.

<ol dir='rtl'>
  <li>في جزء النظرة العامة، حدد <b>مجموعات المهارات</b> ضمن <b>إدارة البحث</b>.</li>
  <li>ضمن <b>Name</b>، حدد <b>azureblob-skillset</b>.</li>
  <li>
    <p>استخدم JSON هذا بدلاً من تعريف المهارات لـ <code>EntityRecognitionSkill</code>، تذكر استبدال نقطة النهاية وقيم المفتاح الأساسي المنسوخين لديك:</p>
  </li>
  <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>"@odata.type": "#Microsoft.Skills.Custom.AmlSkill",
"name": "AMLenricher",
"description": "AML studio enrichment example",
"context": "/document",
"uri": "PASTE YOUR AML ENDPOINT HERE",
"key": "PASTE YOUR PRIMARY KEY HERE",
"resourceId": null,
"region": null,
"timeout": "PT30S",
"degreeOfParallelism": 1,
"inputs": [
    "name": "symboling",
  {
    "source": "/document/symboling"
  },
  {
    "name": "make",
    "source": "/document/make"
  },
  {
    "name": "fuel-type",
    "source": "/document/fueltype"
  },
  {
    "name": "aspiration",
    "source": "/document/aspiration"
  },
  {
    "name": "num-of-doors",
    "source": "/document/numdoors"
  },
  {
    "name": "body-style",
    "source": "/document/bodystyle"
  },
  {
    "name": "drive-wheels",
    "source": "/document/drivewheels"
  },
  {
    "name": "engine-location",
    "source": "/document/enginelocation"
  },
  {
    "name": "wheel-base",
    "source": "/document/wheelbase"
  },
  {
    "name": "length",
    "source": "/document/length"
  },
  {
    "name": "width",
    "source": "/document/width"
  },
  {
    "name": "height",
    "source": "/document/height"
  },
  {
    "name": "curb-weight",
    "source": "/document/curbweight"
  },
  {
    "name": "engine-type",
    "source": "/document/enginetype"
  },
  {
    "name": "num-of-cylinders",
    "source": "/document/numcylinders"
  },
  {
    "name": "engine-size",
    "source": "/document/enginesize"
  },
  {
    "name": "fuel-system",
    "source": "/document/fuelsystem"
  },
  {
    "name": "bore",
    "source": "/document/bore"
  },
  {
    "name": "stroke",
    "source": "/document/stroke"
  },
  {
    "name": "compression-ratio",
    "source": "/document/compressionratio"
  },
  {
    "name": "horsepower",
    "source": "/document/horsepower"
  },
  {
    "name": "peak-rpm",
    "source": "/document/peakrpm"
  },
  {
    "name": "city-mpg",
    "source": "/document/citympg"
  },
  {
    "name": "highway-mpg",
    "source": "/document/highwaympg"
  },
  {
    "name": "price",
    "source": "/document/price"
  }
],
"outputs": [
  {
    "name": "predicted_price",
    "targetName": "predicted_price"
  }
]</code></pre>
  </div>
  <li>حدد <b>حفظ</b>.</li>
</ol>


### تحديث تعيينات حقل الإخراج

<ol dir='rtl'>
  <li>ارجع إلى جزء <b>نظرة عامة</b> في خدمة البحث الخاصة بك، وحدد <b>المفهرسون</b>، ثم حدد <b>azureblob-indexer</b>.</li>
  <li>
    <p>حدد علامة التبويب <b>تعريف الفهرس (JSON)</b>، ثم يمكنك تغيير قيمة <b>outputFieldMappings</b> إلى:</p>
  </li>
  <div style="text-align: left; direction: ltr; margin: 0 20px;">
    <pre><code>"outputFieldMappings": [
  {
    "sourceFieldName": "/document/predicted_price",
    "targetFieldName": "predicted_price"
  }
]</code></pre>
  </div>
  <li>حدد <b>حفظ</b>.</li>
  <li>حدد <b>Reset</b>، ثم حدد <b>Yes</b>.</li>
  <li>حدد <b>Run</b>، ثم حدد <b>Yes</b>.</li>
</ol>

## اختبر إثراء الفهرس

ستضيف مجموعة المهارات المُحدَّثة الآن قيمة متوقعة إلى مستند سيارة الاختبار في فهرسك الخاص. لإجراء ذلك، اتبع الخطوات الآتية.

<ol dir='rtl'>
  <li>في جزء <b>النظرة العامة</b> في خدمة البحث الخاصة بك، حدد <b>مستكشف البحث</b> في الجزء العلوي من الجزء.</li>
  <li>حدد <b>بحث</b>.</li>
  <li>مرِّر إلى أسفل النتائج.</li>
  <p dir="rtl"><a href="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/test-results-search-explorer.png"><img src="https://github.com/MicrosoftLearning/mslearn-knowledge-mining.ar-sa/blob/main/Instructions/media/06-media/test-results-search-explorer.png" alt='لقطة شاشة تعرض حقل سعر السيارة المتوقع الذي تمت إضافته إلى نتائج البحث.'></a></p>
  <p>يجب أن ترى الحقل المملوء <code>predicted_price</code>.</p>
</ol>


## التنظيف

الآن بعد أن أكملت التمرين، احذف جميع الموارد التي لم تعد بحاجة إليها. احذف موارد Azure:

<ol dir='rtl'>
  <li>في <b>مدخل Azure</b>، حدد "Resource groups".</li>
  <li>حدد مجموعة الموارد التي لا تحتاج إليها، ثم حدد <b>حذف مجموعات الموارد</b>.</li>
</ol>

