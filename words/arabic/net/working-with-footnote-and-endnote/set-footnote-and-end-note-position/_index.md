---
title: تعيين موضع الحاشية السفلية والحاشية الختامية
linktitle: تعيين موضع الحاشية السفلية والملاحظة الختامية
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تعيين مواضع الحواشي السفلية والختامية في مستندات Word باستخدام Aspose.Words لـ .NET من خلال هذا الدليل التفصيلي خطوة بخطوة.
weight: 10
url: /ar/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين موضع الحاشية السفلية والحاشية الختامية

## مقدمة

إذا كنت تعمل مع مستندات Word وتحتاج إلى إدارة الحواشي السفلية والتعليقات الختامية بفعالية، فإن Aspose.Words for .NET هي المكتبة المناسبة لك. سيرشدك هذا البرنامج التعليمي خلال تعيين مواضع الحواشي السفلية والتعليقات الختامية في مستند Word باستخدام Aspose.Words for .NET. سنقسم كل خطوة لتسهيل اتباعها وتنفيذها.

## المتطلبات الأساسية

قبل الغوص في البرنامج التعليمي، تأكد من أن لديك ما يلي:

-  مكتبة Aspose.Words لـ .NET: يمكنك تنزيلها من[هنا](https://releases.aspose.com/words/net/).
- Visual Studio: أي إصدار حديث سيعمل بشكل جيد.
- المعرفة الأساسية بلغة C#: إن فهم الأساسيات سوف يساعدك على المتابعة بسهولة.

## استيراد مساحات الأسماء

أولاً، قم باستيراد المساحات الأساسية اللازمة في مشروع C# الخاص بك:

```csharp
using System;
using Aspose.Words;
```

## الخطوة 1: تحميل مستند Word

للبدء، تحتاج إلى تحميل مستند Word الخاص بك إلى كائن مستند Aspose.Words. سيسمح لك هذا بالتعامل مع محتويات المستند.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

في هذا الكود، استبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي يوجد به مستندك.

## الخطوة 2: تعيين موضع الحاشية السفلية

بعد ذلك، ستقوم بتعيين موضع الحواشي السفلية. يتيح لك Aspose.Words for .NET وضع الحواشي السفلية إما في أسفل الصفحة أو أسفل النص.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

 هنا، قمنا بتعيين الحواشي السفلية لتظهر أسفل النص. إذا كنت تفضلها في أسفل الصفحة، فاستخدم`FootnotePosition.BottomOfPage`.

## الخطوة 3: تعيين موضع الحاشية الختامية

وبالمثل، يمكنك تحديد موضع الحواشي الختامية. ويمكن وضع الحواشي الختامية إما في نهاية القسم أو في نهاية المستند.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

 في هذا المثال، يتم وضع الحواشي في نهاية كل قسم. لوضعها في نهاية المستند، استخدم`EndnotePosition.EndOfDocument`.

## الخطوة 4: حفظ المستند

أخيرًا، احفظ المستند لتطبيق التغييرات. تأكد من تحديد مسار الملف الصحيح واسم المستند الناتج.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

يحفظ هذا السطر المستند المعدل في الدليل المحدد.

## خاتمة

إن تحديد مواضع الحواشي السفلية والتعليقات الختامية في مستندات Word باستخدام Aspose.Words for .NET أمر بسيط بمجرد معرفة الخطوات. باتباع هذا الدليل، يمكنك تخصيص مستنداتك لتناسب احتياجاتك، مع ضمان وضع الحواشي السفلية والتعليقات الختامية بالضبط حيث تريدها.

## الأسئلة الشائعة

### هل يمكنني تعيين مواضع مختلفة للحواشي السفلية أو الختامية الفردية؟

لا، يقوم Aspose.Words لـ .NET بتعيين موضع جميع الحواشي السفلية والختامية في المستند بشكل موحد.

### هل Aspose.Words for .NET متوافق مع كافة إصدارات مستندات Word؟

نعم، يدعم Aspose.Words for .NET مجموعة واسعة من تنسيقات مستندات Word، بما في ذلك DOC، وDOCX، وRTF، والمزيد.

### هل يمكنني استخدام Aspose.Words لـ .NET مع لغات برمجة أخرى؟

تم تصميم Aspose.Words for .NET لتطبيقات .NET، ولكن يمكنك استخدامه مع أي لغة تدعم .NET مثل C#، وVB.NET، وما إلى ذلك.

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.Words لـ .NET؟

 نعم، يمكنك الحصول على نسخة تجريبية مجانية[هنا](https://releases.aspose.com/).

### أين يمكنني العثور على المزيد من الوثائق التفصيلية لـ Aspose.Words لـ .NET؟

 الوثائق التفصيلية متاحة[هنا](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
