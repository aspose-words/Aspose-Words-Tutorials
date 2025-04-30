---
"description": "قم بترقية معالجة المستندات لديك باستخدام Aspose.Words for .NET وGoogle AI لإنشاء ملخصات موجزة بسهولة."
"linktitle": "العمل مع نموذج الذكاء الاصطناعي من Google"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "العمل مع نموذج الذكاء الاصطناعي من Google"
"url": "/ar/net/ai-powered-document-processing/working-with-google-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# العمل مع نموذج الذكاء الاصطناعي من Google

## مقدمة

في هذه المقالة، سنستكشف كيفية تلخيص المستندات باستخدام Aspose.Words ونماذج الذكاء الاصطناعي من جوجل خطوة بخطوة. سواءً كنت ترغب في تلخيص تقرير طويل أو استخلاص رؤى من مصادر متعددة، فلدينا ما يناسبك.

## المتطلبات الأساسية

قبل الخوض في الجزء العملي، لنتأكد من جاهزيتك للنجاح. إليك ما ستحتاجه:

1. المعرفة الأساسية بلغة C# و.NET: ستساعدك المعرفة بمفاهيم البرمجة على فهم الأمثلة بشكل أفضل.
   
2. مكتبة Aspose.Words لـ .NET: تتيح لك هذه المكتبة القوية إنشاء مستندات Word ومعالجتها بسلاسة. يمكنك [قم بتحميله هنا](https://releases.aspose.com/words/net/).

3. مفتاح واجهة برمجة التطبيقات لنموذج الذكاء الاصطناعي من جوجل: لاستخدام نماذج الذكاء الاصطناعي، تحتاج إلى مفتاح واجهة برمجة تطبيقات للمصادقة. خزّنه بأمان في متغيرات بيئتك.

4. بيئة التطوير: تأكد من إعداد بيئة عمل .NET (Visual Studio أو أي IDE آخر).

5. مستند نموذجي: ستحتاج إلى مستندات Word نموذجية (على سبيل المثال، "Big document.docx"، "Document.docx") لاختبار التلخيص.

الآن بعد أن قمنا بتغطية الأساسيات، دعنا نتعمق في الكود!

## استيراد الحزم

للعمل مع Aspose.Words ودمج نماذج Google AI، عليك استيراد مساحات الأسماء اللازمة. إليك كيفية القيام بذلك:

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

الآن بعد أن قمت باستيراد الحزم اللازمة، دعنا نقوم بتقسيم عملية تلخيص المستندات خطوة بخطوة.

## الخطوة 1: إعداد دليل المستندات الخاص بك

قبل معالجة المستندات، يجب تحديد مكان حفظها. هذه الخطوة ضرورية لضمان وصول Aspose.Words إليها.

```csharp
// دليل المستندات الخاص بك
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// دليل القطع الأثرية الخاص بك
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

يستبدل `"YOUR_DOCUMENT_DIRECTORY"` و `"YOUR_ARTIFACTS_DIRECTORY"` مع المسارات الفعلية لتخزين مستنداتك على نظامك. سيُستخدم هذا كأساس لقراءة المستندات وحفظها.

## الخطوة 2: تحميل المستندات

بعد ذلك، علينا تحميل المستندات التي نريد تلخيصها. في هذه الحالة، ستحمل مستندين حددناهما سابقًا.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

ال `Document` تتيح لك فئة Aspose.Words تحميل ملفات Word إلى الذاكرة. تأكد من تطابق أسماء الملفات مع المستندات الموجودة في مجلدك، وإلا ستواجه أخطاء "لم يتم العثور على الملف".

## الخطوة 3: استرداد مفتاح API

لاستخدام نموذج الذكاء الاصطناعي، ستحتاج إلى استرداد مفتاح API الخاص بك. يُعد هذا بمثابة تصريح دخولك إلى خدمات Google AI.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

يقوم هذا السطر من التعليمات البرمجية بجلب مفتاح واجهة برمجة التطبيقات (API) المُخزّن في متغيرات بيئتك. يُنصح بإخفاء المعلومات الحساسة، مثل مفاتيح واجهة برمجة التطبيقات، عن التعليمات البرمجية لأسباب أمنية.

## الخطوة 4: إنشاء مثيل لنموذج الذكاء الاصطناعي

الآن، حان وقت إنشاء نسخة من نموذج الذكاء الاصطناعي. هنا يمكنك اختيار النموذج الذي تريد استخدامه، وفي هذا المثال، اخترنا نموذج GPT-4 Mini.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

يُهيئ هذا السطر نموذج الذكاء الاصطناعي الذي ستستخدمه لتلخيص المستندات. تأكد من استشارة [الوثائق](https://reference.aspose.com/words/net/) للحصول على تفاصيل حول النماذج المختلفة وقدراتها.

## الخطوة 5: تلخيص مستند واحد

لنركز على تلخيص الوثيقة الأولى. يمكننا اختيار ملخص قصير هنا.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

في هذه الخطوة نستخدم `Summarize` طريقة من نموذج الذكاء الاصطناعي للحصول على ملخص للمستند الأول. طول الملخص مُحدد على أنه قصير، ولكن يُمكنك تخصيصه حسب احتياجاتك. أخيرًا، يُحفظ المستند المُلخص في مجلد القطع الأثرية.

## الخطوة 6: تلخيص مستندات متعددة

هل تريد تلخيص عدة مستندات دفعةً واحدة؟ يُسهّل Aspose.Words هذه العملية أيضًا!

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

هنا، نحن ندعو `Summarize` هذه المرة، سنستخدم الطريقة مرة أخرى، ولكن مع مجموعة من المستندات. سيمنحك هذا ملخصًا طويلًا يُلخص جوهر كلا الملفين. وكما في السابق، تُحفظ النتيجة في مجلد القطع الأثرية المحدد.

## خاتمة

ها قد انتهيت! لقد نجحت في إعداد بيئة لتلخيص المستندات باستخدام Aspose.Words لـ .NET ونماذج الذكاء الاصطناعي من Google. من تحميل المستندات إلى إنشاء ملخصات موجزة، توفر هذه الخطوات نهجًا مبسطًا لإدارة كميات كبيرة من النصوص بفعالية.

## الأسئلة الشائعة

### ما هو Aspose.Words؟
Aspose.Words هي مكتبة قوية لإنشاء وتعديل وتحويل مستندات Word باستخدام .NET.

### كيف أحصل على مفتاح API لـ Google AI؟
يمكنك عادةً الحصول على مفتاح API عن طريق الاشتراك في Google Cloud وتمكين خدمات API الضرورية.

### هل يمكنني تلخيص عدة مستندات في وقت واحد؟
نعم! كما هو موضح، يمكنك تمرير مجموعة من المستندات إلى طريقة التلخيص.

### ما هي أنواع الملخصات التي يمكنني إنشاؤها؟
يمكنك الاختيار بين الملخصات القصيرة والمتوسطة والطويلة بناءً على احتياجاتك.

### أين يمكنني العثور على المزيد من الموارد Aspose.Words؟
تحقق من [التوثيق](https://reference.aspose.com/words/net/) لمزيد من الأمثلة والتوجيهات.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}