---
title: تضمين مجموعة فرعية من الخطوط في مستند PDF
linktitle: تضمين مجموعة فرعية من الخطوط في مستند PDF
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: قلل حجم ملف PDF عن طريق تضمين مجموعات الخطوط الضرورية فقط باستخدام Aspose.Words for .NET. اتبع دليلنا خطوة بخطوة لتحسين ملفات PDF بكفاءة.
weight: 10
url: /ar/net/programming-with-pdfsaveoptions/embedded-subset-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تضمين مجموعة فرعية من الخطوط في مستند PDF

## مقدمة

هل لاحظت من قبل أن بعض ملفات PDF أكبر حجمًا من غيرها، حتى عندما تحتوي على محتوى مشابه؟ غالبًا ما يكمن السبب في الخطوط. يضمن تضمين الخطوط في ملف PDF أن يبدو بنفس الشكل على أي جهاز، ولكنه قد يؤدي أيضًا إلى تضخيم حجم الملف. لحسن الحظ، يوفر Aspose.Words for .NET ميزة مفيدة لتضمين مجموعات الخطوط الضرورية فقط، مما يحافظ على ملفات PDF الخاصة بك خفيفة الوزن وفعالة. سيرشدك هذا البرنامج التعليمي خلال العملية خطوة بخطوة.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

-  Aspose.Words for .NET: يمكنك تنزيله[هنا](https://releases.aspose.com/words/net/).
- بيئة .NET: تأكد من أن لديك بيئة تطوير .NET عاملة.
- المعرفة الأساسية بلغة C#: ستساعدك المعرفة ببرمجة C# على المتابعة.

## استيراد مساحات الأسماء

لاستخدام Aspose.Words لـ .NET، تحتاج إلى استيراد المساحات الأساسية اللازمة في مشروعك. أضف هذه المساحات في أعلى ملف C# الخاص بك:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: تحميل المستند

 أولاً، نحتاج إلى تحميل مستند Word الذي نريد تحويله إلى PDF. يتم ذلك باستخدام`Document` تم توفير الفئة بواسطة Aspose.Words.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 يقوم مقتطف التعليمات البرمجية هذا بتحميل المستند الموجود في`dataDir` . تأكد من الاستبدال`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي للمستند الخاص بك.

## الخطوة 2: تكوين خيارات حفظ PDF

 بعد ذلك، نقوم بتكوين`PdfSaveOptions` للتأكد من تضمين مجموعات الخطوط الضرورية فقط. من خلال ضبط`EmbedFullFonts` ل`false`، نطلب من Aspose.Words تضمين الحروف الرسومية المستخدمة في المستند فقط.

```csharp
// سيحتوي ملف PDF الناتج على مجموعات فرعية من الخطوط الموجودة في المستند.
// يتم تضمين الحروف الرسومية المستخدمة في المستند فقط في خطوط PDF.
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

تساعد هذه الخطوة الصغيرة ولكن الحاسمة في تقليل حجم ملف PDF بشكل كبير.

## الخطوة 3: احفظ المستند بتنسيق PDF

 وأخيرًا، نقوم بحفظ المستند بصيغة PDF باستخدام`Save` الطريقة، تطبيق الإعدادات المُكوّنة`PdfSaveOptions`.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

 سيقوم هذا الكود بإنشاء ملف PDF باسم`WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf` في الدليل المحدد، مع تضمين مجموعات الخطوط الفرعية الضرورية فقط.

## خاتمة

والآن، إليك الحل! باتباع هذه الخطوات البسيطة، يمكنك تقليل حجم ملفات PDF بكفاءة من خلال تضمين مجموعات الخطوط الضرورية فقط باستخدام Aspose.Words for .NET. وهذا لا يوفر مساحة التخزين فحسب، بل يضمن أيضًا أوقات تحميل أسرع وأداءً أفضل، وخاصةً للمستندات ذات الخطوط الواسعة.

## الأسئلة الشائعة

### لماذا يجب عليّ تضمين مجموعات فرعية من الخطوط فقط في ملف PDF؟
إن تضمين مجموعات الخطوط الضرورية فقط يمكن أن يقلل بشكل كبير من حجم ملف PDF دون المساس بمظهر المستند وقابليته للقراءة.

### هل يمكنني الرجوع إلى تضمين الخطوط الكاملة إذا لزم الأمر؟
 نعم، يمكنك ذلك. ما عليك سوى ضبط`EmbedFullFonts`الممتلكات ل`true` في`PdfSaveOptions`.

### هل يدعم Aspose.Words for .NET ميزات تحسين PDF الأخرى؟
بالتأكيد! يوفر Aspose.Words for .NET مجموعة من الخيارات لتحسين ملفات PDF، بما في ذلك ضغط الصور وإزالة الكائنات غير المستخدمة.

### ما هي أنواع الخطوط التي يمكن تضمينها باستخدام Aspose.Words لـ .NET؟
يدعم Aspose.Words for .NET تضمين مجموعة فرعية من جميع خطوط TrueType المستخدمة في المستند.

### كيف يمكنني التحقق من الخطوط المضمنة في ملف PDF الخاص بي؟
بإمكانك فتح ملف PDF في Adobe Acrobat Reader والتحقق من الخصائص ضمن علامة التبويب الخطوط لرؤية الخطوط المضمنة.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
