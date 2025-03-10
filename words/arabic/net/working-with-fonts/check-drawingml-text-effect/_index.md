---
title: التحقق من تأثير نص DrawingML
linktitle: التحقق من تأثير نص DrawingML
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية التحقق من تأثيرات نص DrawingML في مستندات Word باستخدام Aspose.Words for .NET من خلال دليلنا المفصل خطوة بخطوة. قم بتحسين مستنداتك بسهولة.
weight: 10
url: /ar/net/working-with-fonts/check-drawingml-text-effect/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# التحقق من تأثير نص DrawingML

## مقدمة

مرحبًا بكم في برنامج تعليمي مفصل آخر حول العمل مع Aspose.Words for .NET! اليوم، نتعمق في عالم تأثيرات النص الرائعة في DrawingML. سواء كنت تبحث عن تحسين مستندات Word الخاصة بك باستخدام الظلال أو الانعكاسات أو التأثيرات ثلاثية الأبعاد، فسوف يوضح لك هذا الدليل كيفية التحقق من تأثيرات النص هذه في مستنداتك باستخدام Aspose.Words for .NET. لنبدأ!

## المتطلبات الأساسية

قبل أن ننتقل إلى البرنامج التعليمي، هناك بعض المتطلبات الأساسية التي ستحتاج إلى وضعها في مكانها:

-  مكتبة Aspose.Words for .NET: تأكد من تثبيت مكتبة Aspose.Words for .NET. يمكنك تنزيلها من[صفحة إصدارات Aspose](https://releases.aspose.com/words/net/).
- بيئة التطوير: يجب أن يكون لديك بيئة تطوير تم إعدادها، مثل Visual Studio.
- المعرفة الأساسية بلغة C#: بعض الألفة مع برمجة C# سيكون مفيدًا.

## استيراد مساحات الأسماء

أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية. ستتيح لك هذه المساحات الوصول إلى الفئات والطرق المطلوبة للتعامل مع مستندات Word والتحقق من تأثيرات نص DrawingML.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## دليل خطوة بخطوة للتحقق من تأثيرات نص DrawingML

الآن، دعونا نقوم بتقسيم العملية إلى خطوات متعددة، مما يجعل من السهل متابعتها.

## الخطوة 1: تحميل المستند

الخطوة الأولى هي تحميل مستند Word الذي تريد التحقق منه بحثًا عن تأثيرات نص DrawingML. 

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "DrawingML text effects.docx");
```

يقوم مقتطف التعليمات البرمجية هذا بتحميل المستند المسمى "DrawingML text effects.docx" من الدليل المحدد.

## الخطوة 2: الوصول إلى مجموعة Runs

بعد ذلك، نحتاج إلى الوصول إلى مجموعة التشغيلات في الفقرة الأولى من المستند. التشغيلات هي أجزاء من النص بنفس التنسيق.

```csharp
RunCollection runs = doc.FirstSection.Body.FirstParagraph.Runs;
```

يسترجع هذا السطر من التعليمات البرمجية التشغيلات من الفقرة الأولى في القسم الأول من المستند.

## الخطوة 3: الحصول على الخط الخاص بالتشغيل الأول

الآن، سنحصل على خصائص الخط للتشغيل الأول في مجموعة التشغيلات. وهذا يسمح لنا بالتحقق من تأثيرات نص DrawingML المختلفة المطبقة على النص.

```csharp
Font runFont = runs[0].Font;
```

## الخطوة 4: التحقق من تأثيرات نص DrawingML

أخيرًا، يمكننا التحقق من تأثيرات نص DrawingML المختلفة مثل الظل والتأثير ثلاثي الأبعاد والانعكاس والمخطط التفصيلي والتعبئة.

```csharp
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Shadow));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Effect3D));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Reflection));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Outline));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Fill));
```

 سيتم طباعة هذه الأسطر من التعليمات البرمجية`true` أو`false` اعتمادًا على ما إذا كان يتم تطبيق كل تأثير نص DrawingML محدد على خط التشغيل.

## خاتمة

تهانينا! لقد تعلمت للتو كيفية التحقق من تأثيرات نص DrawingML في مستندات Word باستخدام Aspose.Words for .NET. تتيح لك هذه الميزة القوية اكتشاف تنسيقات النصوص المعقدة ومعالجتها برمجيًا، مما يمنحك سيطرة أكبر على مهام معالجة المستندات.


## الأسئلة الشائعة

### ما هو تأثير النص DrawingML؟
تأثيرات نص DrawingML هي خيارات تنسيق نص متقدمة في مستندات Word، بما في ذلك الظلال والتأثيرات ثلاثية الأبعاد والانعكاسات والمخططات والتعبئة.

### هل يمكنني تطبيق تأثيرات نص DrawingML باستخدام Aspose.Words لـ .NET؟
نعم، يسمح لك Aspose.Words for .NET بالتحقق من تأثيرات نص DrawingML وتطبيقها برمجيًا.

### هل أحتاج إلى ترخيص لاستخدام Aspose.Words لـ .NET؟
 نعم، يتطلب Aspose.Words for .NET ترخيصًا للحصول على الوظائف الكاملة. يمكنك الحصول على ترخيص[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) للتقييم.

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.Words لـ .NET؟
 نعم يمكنك تنزيل[نسخة تجريبية مجانية](https://releases.aspose.com/) لتجربة Aspose.Words لـ .NET قبل الشراء.

### أين يمكنني العثور على مزيد من الوثائق حول Aspose.Words لـ .NET؟
 يمكنك العثور على وثائق مفصلة على[صفحة توثيق Aspose.Words لـ .NET](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
