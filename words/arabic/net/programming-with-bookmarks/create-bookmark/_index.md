---
title: إنشاء إشارة مرجعية في مستند Word
linktitle: إنشاء إشارة مرجعية في مستند Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إنشاء إشارات مرجعية في مستندات Word باستخدام Aspose.Words for .NET من خلال هذا الدليل المفصل خطوة بخطوة. مثالي للتنقل بين المستندات وتنظيمها.
weight: 10
url: /ar/net/programming-with-bookmarks/create-bookmark/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء إشارة مرجعية في مستند Word

## مقدمة

إن إنشاء إشارات مرجعية في مستند Word قد يكون بمثابة تغيير جذري، خاصة عندما تريد التنقل عبر المستندات الكبيرة دون عناء. اليوم، سنشرح عملية إنشاء إشارات مرجعية باستخدام Aspose.Words لـ .NET. سيأخذك هذا البرنامج التعليمي خطوة بخطوة، مما يضمن فهمك لكل جزء من العملية. لذا، فلنبدأ على الفور!

## المتطلبات الأساسية

قبل أن نبدأ، يجب أن يكون لديك ما يلي:

1.  Aspose.Words for .NET Library: تنزيل وتثبيت من[هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير .NET أخرى.
3. المعرفة الأساسية بلغة C#: فهم مفاهيم برمجة C# الأساسية.

## استيراد مساحات الأسماء

للعمل مع Aspose.Words لـ .NET، تحتاج إلى استيراد المساحات الأساسية الضرورية:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: إعداد المستند وDocumentBuilder

تهيئة المستند

أولاً، نحتاج إلى إنشاء مستند جديد وتهيئة`DocumentBuilder`. هذه هي نقطة البداية لإضافة المحتوى والإشارات المرجعية إلى مستندك.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 الشرح:`Document` الهدف هو لوحتك القماشية.`DocumentBuilder` هو بمثابة قلمك، الذي يسمح لك بكتابة المحتوى وإنشاء الإشارات المرجعية في المستند.

## الخطوة 2: إنشاء الإشارة المرجعية الرئيسية

بدء وإنهاء الإشارة المرجعية الرئيسية

لإنشاء إشارة مرجعية، يجب عليك تحديد نقاط البداية والنهاية. هنا، سنقوم بإنشاء إشارة مرجعية باسم "إشارتي المرجعية".

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside a bookmark.");
```

 الشرح:`StartBookmark` تشير الطريقة إلى بداية الإشارة المرجعية، و`Writeln` يضيف النص داخل الإشارة المرجعية.

## الخطوة 3: إنشاء إشارة مرجعية متداخلة

إضافة إشارة مرجعية متداخلة داخل الإشارة المرجعية الرئيسية

يمكنك تضمين إشارات مرجعية داخل إشارات مرجعية أخرى. هنا، نضيف "إشارة مرجعية متداخلة" ضمن "إشارتي المرجعية".

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside a NestedBookmark.");
builder.EndBookmark("Nested Bookmark");
```

 الشرح: تسمح لك الإشارات المرجعية المتداخلة بتنظيم المحتوى بشكل أكثر هيكلة وتسلسلًا هرميًا.`EndBookmark` تغلق الطريقة الإشارة المرجعية الحالية.

## الخطوة 4: إضافة نص خارج الإشارة المرجعية المتداخلة

متابعة إضافة المحتوى

بعد الإشارة المرجعية المتداخلة، يمكننا الاستمرار في إضافة المزيد من المحتوى داخل الإشارة المرجعية الرئيسية.

```csharp
builder.Writeln("Text after Nested Bookmark.");
builder.EndBookmark("My Bookmark");
```

التوضيح: يضمن هذا أن الإشارة المرجعية الرئيسية تحتوي على الإشارة المرجعية المتداخلة والنص الإضافي.

## الخطوة 5: تكوين خيارات حفظ PDF

إعداد خيارات حفظ PDF للإشارات المرجعية

عند حفظ المستند بتنسيق PDF، يمكننا تكوين خيارات لتضمين الإشارات المرجعية.

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```

 الشرح:`PdfSaveOptions` تسمح لك الفئة بتحديد كيفية حفظ المستند بتنسيق PDF.`BookmarksOutlineLevels` تعرف الخاصية على التسلسل الهرمي للإشارات المرجعية في ملف PDF.

## الخطوة 6: حفظ المستند

حفظ المستند بصيغة PDF

وأخيرًا، قم بحفظ المستند بالخيارات المحددة.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```

 الشرح:`Save` تحفظ الطريقة المستند بالتنسيق والموقع المحددين. سيتضمن ملف PDF الآن الإشارات المرجعية التي أنشأناها.

## خاتمة

إن إنشاء إشارات مرجعية في مستند Word باستخدام Aspose.Words for .NET أمر بسيط ومفيد للغاية للتنقل بين المستندات وتنظيمها. سواء كنت تقوم بإنشاء تقارير أو إنشاء كتب إلكترونية أو إدارة مستندات كبيرة، فإن الإشارات المرجعية تجعل الحياة أسهل. اتبع الخطوات الموضحة في هذا البرنامج التعليمي، وستحصل على ملف PDF مُضاف إليه إشارات مرجعية في وقت قصير.

## الأسئلة الشائعة

### هل يمكنني إنشاء إشارات مرجعية متعددة على مستويات مختلفة؟

بالتأكيد! يمكنك إنشاء عدد لا حصر له من الإشارات المرجعية وتحديد مستوياتها الهرمية عند حفظ المستند بتنسيق PDF.

### كيف أقوم بتحديث نص الإشارة المرجعية؟

 يمكنك الانتقال إلى الإشارة المرجعية باستخدام`DocumentBuilder.MoveToBookmark` ومن ثم تحديث النص.

### هل من الممكن حذف الإشارة المرجعية؟

 نعم، يمكنك حذف الإشارة المرجعية باستخدام`Bookmarks.Remove` الطريقة عن طريق تحديد اسم الإشارة المرجعية.

### هل يمكنني إنشاء إشارات مرجعية بتنسيقات أخرى غير PDF؟

نعم، يدعم Aspose.Words الإشارات المرجعية في تنسيقات مختلفة، بما في ذلك DOCX، وHTML، وEPUB.

### كيف يمكنني التأكد من ظهور الإشارات المرجعية بشكل صحيح في ملف PDF؟

 تأكد من تحديد`BookmarksOutlineLevels` بشكل صحيح في`PdfSaveOptions`يضمن هذا تضمين الإشارات المرجعية في مخطط PDF.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
