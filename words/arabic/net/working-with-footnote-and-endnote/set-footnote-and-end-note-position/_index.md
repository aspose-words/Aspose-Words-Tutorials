---
"description": "تعرف على كيفية تعيين مواضع الحواشي السفلية والختامية في مستندات Word باستخدام Aspose.Words for .NET باستخدام هذا الدليل المفصل خطوة بخطوة."
"linktitle": "تعيين موضع الحاشية السفلية والملاحظة الختامية"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تعيين موضع الحاشية السفلية والحاشية الختامية"
"url": "/ar/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تعيين موضع الحاشية السفلية والحاشية الختامية

## مقدمة

إذا كنت تعمل على مستندات Word وتحتاج إلى إدارة الحواشي السفلية والختامية بفعالية، فإن Aspose.Words for .NET هي مكتبتك المثالية. سيرشدك هذا البرنامج التعليمي إلى كيفية ضبط مواضع الحواشي السفلية والختامية في مستند Word باستخدام Aspose.Words for .NET. سنشرح كل خطوة بالتفصيل لتسهيل اتباعها وتطبيقها.

## المتطلبات الأساسية

قبل الغوص في البرنامج التعليمي، تأكد من أن لديك ما يلي:

- مكتبة Aspose.Words لـ .NET: يمكنك تنزيلها من [هنا](https://releases.aspose.com/words/net/).
- Visual Studio: أي إصدار حديث سيعمل بشكل جيد.
- المعرفة الأساسية بلغة C#: فهم الأساسيات سوف يساعدك على المتابعة بسهولة.

## استيراد مساحات الأسماء

أولاً، قم باستيراد المساحات الأساسية اللازمة في مشروع C# الخاص بك:

```csharp
using System;
using Aspose.Words;
```

## الخطوة 1: تحميل مستند Word

للبدء، عليك تحميل مستند Word الخاص بك إلى كائن Aspose.Words. سيسمح لك هذا بالتحكم في محتوياته.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

في هذا الكود، استبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي يوجد به مستندك.

## الخطوة 2: تعيين موضع الحاشية السفلية

بعد ذلك، يمكنك تحديد موضع الحواشي السفلية. يتيح لك Aspose.Words لـ .NET وضع الحواشي السفلية إما في أسفل الصفحة أو أسفل النص.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

هنا، قمنا بضبط الحواشي السفلية لتظهر أسفل النص. إذا كنت تفضلها أسفل الصفحة، فاستخدم `FootnotePosition.BottomOfPage`.

## الخطوة 3: تعيين موضع الحاشية الختامية

وبالمثل، يمكنك تحديد موضع الحواشي الختامية. يمكن وضعها إما في نهاية القسم أو في نهاية المستند.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

في هذا المثال، تُوضع الحواشي الختامية في نهاية كل قسم. لوضعها في نهاية المستند، استخدم `EndnotePosition.EndOfDocument`.

## الخطوة 4: حفظ المستند

أخيرًا، احفظ المستند لتطبيق التغييرات. تأكد من تحديد مسار الملف واسمه الصحيحين للمستند الناتج.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

يحفظ هذا السطر المستند المعدل في الدليل المحدد.

## خاتمة

ضبط مواضع الحواشي السفلية والختامية في مستندات Word باستخدام Aspose.Words for .NET سهلٌ للغاية بمجرد معرفة الخطوات. باتباع هذا الدليل، يمكنك تخصيص مستنداتك لتناسب احتياجاتك، مع ضمان وضع الحواشي السفلية والختامية في المكان المطلوب تمامًا.

## الأسئلة الشائعة

### هل يمكنني تحديد مواضع مختلفة للحواشي السفلية أو النهائية الفردية؟

لا، يقوم Aspose.Words for .NET بتعيين موضع جميع الحواشي السفلية والختامية في المستند بشكل موحد.

### هل Aspose.Words for .NET متوافق مع كافة إصدارات مستندات Word؟

نعم، يدعم Aspose.Words for .NET مجموعة واسعة من تنسيقات مستندات Word، بما في ذلك DOC، وDOCX، وRTF، والمزيد.

### هل يمكنني استخدام Aspose.Words لـ .NET مع لغات برمجة أخرى؟

تم تصميم Aspose.Words for .NET لتطبيقات .NET، ولكن يمكنك استخدامه مع أي لغة تدعم .NET مثل C#، VB.NET، وما إلى ذلك.

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.Words لـ .NET؟

نعم، يمكنك الحصول على نسخة تجريبية مجانية [هنا](https://releases.aspose.com/).

### أين يمكنني العثور على المزيد من الوثائق التفصيلية لـ Aspose.Words لـ .NET؟

الوثائق التفصيلية متاحة [هنا](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}