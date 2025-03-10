---
title: التحويل بين وحدات القياس
linktitle: التحويل بين وحدات القياس
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تحويل وحدات القياس في Aspose.Words لـ .NET. اتبع دليلنا خطوة بخطوة لتعيين هوامش المستند والرؤوس والتذييلات بالبوصات والنقط.
weight: 10
url: /ar/net/programming-with-document-properties/convert-between-measurement-units/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# التحويل بين وحدات القياس

## مقدمة

مرحبًا! هل أنت مطور تعمل مع مستندات Word باستخدام Aspose.Words for .NET؟ إذا كان الأمر كذلك، فقد تجد نفسك غالبًا في حاجة إلى تعيين الهوامش أو الرؤوس أو التذييلات بوحدات قياس مختلفة. قد يكون التحويل بين وحدات مثل البوصات والنقط أمرًا صعبًا إذا لم تكن على دراية بوظائف المكتبة. في هذا البرنامج التعليمي الشامل، سنرشدك خلال عملية التحويل بين وحدات القياس باستخدام Aspose.Words for .NET. دعنا نتعمق في هذه التحويلات ونبسطها!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1.  Aspose.Words for .NET Library: إذا لم تقم بتنزيلها بالفعل، فقم بتنزيلها[هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير متكاملة أخرى متوافقة مع .NET.
3. المعرفة الأساسية بلغة C#: إن فهم أساسيات لغة C# سوف يساعدك على المتابعة بسهولة.
4.  ترخيص Aspose: اختياري ولكنه موصى به للحصول على الوظائف الكاملة. يمكنك الحصول على ترخيص مؤقت[هنا](https://purchase.aspose.com/temporary-license/).

## استيراد مساحات الأسماء

أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية. يعد هذا أمرًا بالغ الأهمية للوصول إلى الفئات والطرق التي يوفرها Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Layout;
```

دعنا نستعرض عملية تحويل وحدات القياس في Aspose.Words لـ .NET. اتبع الخطوات التفصيلية التالية لإعداد هوامش ومسافات مستندك وتخصيصها.

## الخطوة 1: إنشاء مستند جديد

أولاً، عليك إنشاء مستند جديد باستخدام Aspose.Words.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 يؤدي هذا إلى تهيئة مستند Word جديد و`DocumentBuilder` لتسهيل إنشاء المحتوى وتنسيقه.

## الخطوة 2: إعداد صفحة الوصول

 لتعيين الهوامش والرؤوس والتذييلات، تحتاج إلى الوصول إلى`PageSetup` هدف.

```csharp
PageSetup pageSetup = builder.PageSetup;
```

يتيح لك هذا الوصول إلى خصائص إعداد الصفحة المختلفة مثل الهوامش ومسافة الرأس ومسافة التذييل.

## الخطوة 3: تحويل البوصات إلى نقاط

 يستخدم Aspose.Words النقاط كوحدة قياس افتراضيًا. لتعيين الهوامش بالبوصات، ستحتاج إلى تحويل البوصات إلى نقاط باستخدام`ConvertUtil.InchToPoint` طريقة.

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

يؤدي هذا إلى حفظ مستندك مع الهوامش والمسافات المحددة بالنقاط.

## خاتمة

والآن، لقد نجحت في تحويل وتعيين الهوامش والمسافات في مستند Word باستخدام Aspose.Words for .NET. باتباع هذه الخطوات، يمكنك التعامل بسهولة مع تحويلات الوحدات المختلفة، مما يجعل عملية تخصيص المستند سهلة للغاية. استمر في تجربة الإعدادات المختلفة واستكشف الوظائف الواسعة التي يوفرها Aspose.Words. أتمنى لك برمجة ممتعة!

## الأسئلة الشائعة

### هل يمكنني تحويل وحدات أخرى مثل السنتيمترات إلى نقاط باستخدام Aspose.Words؟
 نعم، يوفر Aspose.Words طرقًا مثل`ConvertUtil.CmToPoint` لتحويل السنتيمترات إلى نقاط.

### هل هناك حاجة إلى ترخيص لاستخدام Aspose.Words لـ .NET؟
على الرغم من أنه يمكنك استخدام Aspose.Words بدون ترخيص، إلا أن بعض الميزات المتقدمة قد تكون مقيدة. يضمن الحصول على ترخيص الاستفادة الكاملة من الوظائف.

### كيف أقوم بتثبيت Aspose.Words لـ .NET؟
 يمكنك تنزيله من[موقع إلكتروني](https://releases.aspose.com/words/net/) واتبع تعليمات التثبيت.

### هل يمكنني تعيين وحدات مختلفة لأقسام مختلفة من المستند؟
 نعم، يمكنك تخصيص الهوامش والإعدادات الأخرى لأقسام مختلفة باستخدام`Section` فصل.

### ما هي الميزات الأخرى التي يقدمها Aspose.Words؟
 يدعم Aspose.Words مجموعة واسعة من الميزات بما في ذلك تحويل المستندات ودمج البريد وخيارات التنسيق الشاملة. تحقق من[التوثيق](https://reference.aspose.com/words/net/) لمزيد من التفاصيل.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
