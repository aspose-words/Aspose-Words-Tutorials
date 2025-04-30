---
"description": "تعرّف على كيفية تحويل وحدات القياس في Aspose.Words لـ .NET. اتبع دليلنا خطوة بخطوة لضبط هوامش المستند، ورؤوس الصفحات، وتذييلاتها بالبوصات والنقاط."
"linktitle": "التحويل بين وحدات القياس"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "التحويل بين وحدات القياس"
"url": "/ar/net/programming-with-document-properties/convert-between-measurement-units/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# التحويل بين وحدات القياس

## مقدمة

أهلاً! هل أنت مطور تعمل على مستندات Word باستخدام Aspose.Words لـ .NET؟ إذا كان الأمر كذلك، فقد تحتاج غالبًا إلى ضبط الهوامش أو الرؤوس أو التذييلات بوحدات قياس مختلفة. قد يكون التحويل بين وحدات القياس، مثل البوصات والنقاط، صعبًا إذا لم تكن على دراية بوظائف المكتبة. في هذا البرنامج التعليمي الشامل، سنرشدك خلال عملية التحويل بين وحدات القياس باستخدام Aspose.Words لـ .NET. لنبدأ بتبسيط هذه التحويلات!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1. Aspose.Words لمكتبة .NET: إذا لم تقم بتنزيلها بالفعل، فقم بتنزيلها [هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير متكاملة أخرى متوافقة مع .NET.
3. المعرفة الأساسية بلغة C#: إن فهم أساسيات لغة C# سوف يساعدك على المتابعة بسهولة.
4. ترخيص Aspose: اختياري، ولكنه مُوصى به للاستخدام الكامل. يمكنك الحصول على ترخيص مؤقت. [هنا](https://purchase.aspose.com/temporary-license/).

## استيراد مساحات الأسماء

أولاً، عليك استيراد مساحات الأسماء اللازمة. هذا ضروري للوصول إلى الفئات والأساليب التي يوفرها Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Layout;
```

لنشرح عملية تحويل وحدات القياس في Aspose.Words لـ .NET. اتبع هذه الخطوات المفصلة لإعداد هوامش ومسافات مستندك وتخصيصها.

## الخطوة 1: إنشاء مستند جديد

أولاً، عليك إنشاء مستند جديد باستخدام Aspose.Words.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

يؤدي هذا إلى تهيئة مستند Word جديد و `DocumentBuilder` لتسهيل إنشاء المحتوى وتنسيقه.

## الخطوة 2: إعداد صفحة الوصول

لتعيين الهوامش والرؤوس والتذييلات، تحتاج إلى الوصول إلى `PageSetup` هدف.

```csharp
PageSetup pageSetup = builder.PageSetup;
```

يتيح لك هذا الوصول إلى خصائص إعداد الصفحة المختلفة مثل الهوامش ومسافة الرأس ومسافة التذييل.

## الخطوة 3: تحويل البوصات إلى نقاط

يستخدم Aspose.Words النقاط كوحدة قياس افتراضية. لتعيين الهوامش بالبوصات، ستحتاج إلى تحويل البوصات إلى نقاط باستخدام `ConvertUtil.InchToPoint` طريقة.

```csharp
pageSetup.TopMargin = ConvertUtil.InchToPoint(1.0);
pageSetup.BottomMargin = ConvertUtil.InchToPoint(1.0);
pageSetup.LeftMargin = ConvertUtil.InchToPoint(1.5);
pageSetup.RightMargin = ConvertUtil.InchToPoint(1.5);
pageSetup.HeaderDistance = ConvertUtil.InchToPoint(0.2);
pageSetup.FooterDistance = ConvertUtil.InchToPoint(0.2);
```

فيما يلي تفصيل لما يفعله كل سطر:
- تعيين الهوامش العلوية والسفلية إلى 1 بوصة (تحويلها إلى نقاط).
- تعيين الهوامش اليمنى واليسرى إلى 1.5 بوصة (تحويلها إلى نقاط).
- تعيين مسافة الرأس والتذييل إلى 0.2 بوصة (تحويلها إلى نقاط).

## الخطوة 4: حفظ المستند

وأخيرًا، احفظ مستندك للتأكد من تطبيق كافة التغييرات.

```csharp
doc.Save("ConvertedDocument.docx");
```

يؤدي هذا إلى حفظ مستندك بالهوامش والمسافات المحددة بالنقاط.

## خاتمة

ها قد انتهيت! لقد نجحت في تحويل وضبط الهوامش والمسافات في مستند Word باستخدام Aspose.Words لـ .NET. باتباع هذه الخطوات، يمكنك بسهولة التعامل مع تحويلات الوحدات المختلفة، مما يجعل عملية تخصيص مستندك في غاية السهولة. استمر في تجربة الإعدادات المختلفة واستكشف الوظائف الواسعة التي يقدمها Aspose.Words. برمجة ممتعة!

## الأسئلة الشائعة

### هل يمكنني تحويل وحدات أخرى مثل السنتيمترات إلى نقاط باستخدام Aspose.Words؟
نعم، يوفر Aspose.Words طرقًا مثل `ConvertUtil.CmToPoint` لتحويل السنتيمترات إلى نقاط.

### هل هناك حاجة إلى ترخيص لاستخدام Aspose.Words لـ .NET؟
مع أنه يمكنك استخدام Aspose.Words بدون ترخيص، إلا أن بعض الميزات المتقدمة قد تكون محدودة. الحصول على ترخيص يضمن لك كامل وظائف البرنامج.

### كيف أقوم بتثبيت Aspose.Words لـ .NET؟
يمكنك تنزيله من [موقع إلكتروني](https://releases.aspose.com/words/net/) واتبع تعليمات التثبيت.

### هل يمكنني تعيين وحدات مختلفة لأقسام مختلفة من المستند؟
نعم، يمكنك تخصيص الهوامش والإعدادات الأخرى للأقسام المختلفة باستخدام `Section` فصل.

### ما هي الميزات الأخرى التي يقدمها Aspose.Words؟
يدعم Aspose.Words مجموعة واسعة من الميزات، بما في ذلك تحويل المستندات، ودمج البريد، وخيارات التنسيق الشاملة. تحقق من [التوثيق](https://reference.aspose.com/words/net/) لمزيد من التفاصيل.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}