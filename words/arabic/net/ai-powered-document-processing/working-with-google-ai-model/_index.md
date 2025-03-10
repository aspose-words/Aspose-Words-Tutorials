---
title: العمل مع نموذج الذكاء الاصطناعي من Google
linktitle: العمل مع نموذج الذكاء الاصطناعي من Google
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: قم بترقية معالجة المستندات لديك باستخدام Aspose.Words for .NET وGoogle AI لإنشاء ملخصات موجزة دون عناء.
weight: 10
url: /ar/net/ai-powered-document-processing/working-with-google-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# العمل مع نموذج الذكاء الاصطناعي من Google

## مقدمة

في هذه المقالة، سنستكشف كيفية تلخيص المستندات باستخدام Aspose.Words ونماذج الذكاء الاصطناعي من Google خطوة بخطوة. سواء كنت تريد تلخيص تقرير طويل أو استخراج رؤى من مصادر متعددة، فلدينا ما يناسبك.

## المتطلبات الأساسية

قبل الخوض في الجزء العملي، دعنا نتأكد من أنك مستعد للنجاح. إليك ما ستحتاج إليه:

1. المعرفة الأساسية بلغة C# و.NET: ستساعدك المعرفة بمفاهيم البرمجة على فهم الأمثلة بشكل أفضل.
   
2.  مكتبة Aspose.Words لـ .NET: تتيح لك هذه المكتبة القوية إنشاء مستندات Word ومعالجتها بسلاسة. يمكنك[تحميله هنا](https://releases.aspose.com/words/net/).

3. مفتاح API لنموذج الذكاء الاصطناعي من Google: للاستفادة من نماذج الذكاء الاصطناعي، تحتاج إلى مفتاح API للمصادقة. قم بتخزينه بأمان في متغيرات البيئة الخاصة بك.

4. بيئة التطوير: تأكد من إعداد بيئة عمل .NET (Visual Studio أو أي IDE آخر).

5. مستند نموذجي: ستحتاج إلى مستندات Word نموذجية (على سبيل المثال، "Big document.docx"، "Document.docx") لاختبار التلخيص.

الآن بعد أن قمنا بتغطية الأساسيات، دعنا نتعمق في الكود!

## استيراد الحزم

للعمل مع Aspose.Words ودمج نماذج Google AI، تحتاج إلى استيراد المساحات الأساسية اللازمة. إليك كيفية القيام بذلك:

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

الآن بعد أن قمت باستيراد الحزم اللازمة، دعنا نقوم بتقسيم عملية تلخيص المستندات خطوة بخطوة.

## الخطوة 1: إعداد دليل المستندات الخاص بك

قبل أن نتمكن من معالجة المستندات، نحتاج إلى تحديد مكان وجود ملفاتنا. هذه الخطوة ضرورية لضمان قدرة Aspose.Words على الوصول إلى المستندات.

```csharp
// دليل المستندات الخاص بك
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// دليل ArtifactsDir الخاص بك
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

 يستبدل`"YOUR_DOCUMENT_DIRECTORY"` و`"YOUR_ARTIFACTS_DIRECTORY"` مع المسارات الفعلية على نظامك حيث يتم تخزين مستنداتك. سيعمل هذا بمثابة الأساس لقراءة المستندات وحفظها.

## الخطوة 2: تحميل المستندات

بعد ذلك، نحتاج إلى تحميل المستندات التي نريد تلخيصها. في هذه الحالة، ستقوم بتحميل مستندين حددناهما سابقًا.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

 ال`Document` تتيح لك الفئة من Aspose.Words تحميل ملفات Word إلى الذاكرة. تأكد من أن أسماء الملفات تتطابق مع المستندات الفعلية الموجودة في الدليل، وإلا فستواجه أخطاء عدم العثور على الملف!

## الخطوة 3: استرداد مفتاح API

للاستفادة من نموذج الذكاء الاصطناعي، ستحتاج إلى استرداد مفتاح API الخاص بك. يعمل هذا المفتاح بمثابة تصريح دخول إلى خدمات الذكاء الاصطناعي من Google.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

يقوم هذا السطر من التعليمات البرمجية بجلب مفتاح واجهة برمجة التطبيقات الذي قمت بتخزينه في متغيرات البيئة الخاصة بك. من الجيد أن تحرص على عدم إدراج معلومات حساسة مثل مفاتيح واجهة برمجة التطبيقات في التعليمات البرمجية الخاصة بك لأسباب أمنية.

## الخطوة 4: إنشاء مثيل لنموذج الذكاء الاصطناعي

الآن، حان الوقت لإنشاء مثيل لنموذج الذكاء الاصطناعي. هنا يمكنك اختيار النموذج الذي تريد استخدامه — في هذا المثال، اخترنا نموذج GPT-4 Mini.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

 يقوم هذا السطر بإعداد نموذج الذكاء الاصطناعي الذي ستستخدمه لتلخيص المستندات. تأكد من استشارة[التوثيق](https://reference.aspose.com/words/net/) للحصول على تفاصيل حول النماذج المختلفة وقدراتها.

## الخطوة 5: تلخيص مستند واحد

دعونا نركز على تلخيص الوثيقة الأولى. يمكننا اختيار الحصول على ملخص قصير هنا.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

 في هذه الخطوة، نستخدم`Summarize`الطريقة من نموذج الذكاء الاصطناعي للحصول على ملخص للوثيقة الأولى. يتم ضبط طول الملخص على قصير، ولكن يمكنك تخصيص ذلك وفقًا لاحتياجاتك. أخيرًا، يتم حفظ المستند الملخص في دليل القطع الأثرية لديك.

## الخطوة 6: تلخيص مستندات متعددة

هل تريد تلخيص عدة مستندات في وقت واحد؟ Aspose.Words يجعل هذا الأمر سهلاً أيضًا!

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

 هنا، نحن ندعو`Summarize` هذه الطريقة مرة أخرى، ولكن هذه المرة باستخدام مجموعة من المستندات. سيمنحك هذا ملخصًا طويلًا يلخص جوهر الملفين. تمامًا كما حدث من قبل، يتم حفظ النتيجة في دليل القطع الأثرية المحدد.

## خاتمة

والآن، لقد نجحت في إعداد بيئة لتلخيص المستندات باستخدام Aspose.Words for .NET ونماذج الذكاء الاصطناعي من Google. بدءًا من تحميل المستندات إلى إنشاء ملخصات موجزة، توفر هذه الخطوات نهجًا مبسطًا لإدارة كميات كبيرة من النصوص بشكل فعال.

## الأسئلة الشائعة

### ما هو Aspose.Words؟
Aspose.Words هي مكتبة قوية لإنشاء وتعديل وتحويل مستندات Word باستخدام .NET.

### كيف أحصل على مفتاح API لـ Google AI؟
يمكنك عادةً الحصول على مفتاح API عن طريق الاشتراك في Google Cloud وتمكين خدمات API الضرورية.

### هل يمكنني تلخيص عدة مستندات مرة واحدة؟
نعم! كما هو موضح، يمكنك تمرير مجموعة من المستندات إلى طريقة التلخيص.

### ما هي أنواع الملخصات التي يمكنني إنشاؤها؟
يمكنك الاختيار بين ملخصات قصيرة ومتوسطة وطويلة بناءً على احتياجاتك.

### أين يمكنني العثور على المزيد من الموارد Aspose.Words؟
 تحقق من[التوثيق](https://reference.aspose.com/words/net/) لمزيد من الأمثلة والتوجيهات.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
