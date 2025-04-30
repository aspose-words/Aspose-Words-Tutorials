---
"description": "قلّل حجم ملف PDF بتضمين مجموعات الخطوط الضرورية فقط باستخدام Aspose.Words لـ .NET. اتبع دليلنا خطوة بخطوة لتحسين ملفات PDF بكفاءة."
"linktitle": "تضمين مجموعة فرعية من الخطوط في مستند PDF"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تضمين مجموعة فرعية من الخطوط في مستند PDF"
"url": "/ar/net/programming-with-pdfsaveoptions/embedded-subset-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تضمين مجموعة فرعية من الخطوط في مستند PDF

## مقدمة

هل لاحظتَ يومًا أن بعض ملفات PDF أكبر حجمًا من غيرها، حتى مع تشابه محتواها؟ غالبًا ما يكمن السبب في الخطوط. يضمن تضمين الخطوط في ملف PDF مظهرًا متطابقًا على أي جهاز، ولكنه قد يؤدي أيضًا إلى زيادة حجم الملف. لحسن الحظ، يوفر Aspose.Words for .NET ميزةً عمليةً لتضمين مجموعات الخطوط الضرورية فقط، مما يحافظ على ملفات PDF الخاصة بك بسيطةً وفعالة. سيرشدك هذا الدليل خلال العملية خطوة بخطوة.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

- Aspose.Words for .NET: يمكنك تنزيله [هنا](https://releases.aspose.com/words/net/).
- بيئة .NET: تأكد من أن لديك بيئة تطوير .NET عاملة.
- المعرفة الأساسية بلغة C#: ستساعدك المعرفة ببرمجة C# على المتابعة.

## استيراد مساحات الأسماء

لاستخدام Aspose.Words لـ .NET، عليك استيراد مساحات الأسماء اللازمة في مشروعك. أضف هذه في أعلى ملف C#:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: تحميل المستند

أولاً، علينا تحميل مستند Word الذي نريد تحويله إلى PDF. يتم ذلك باستخدام `Document` تم توفير الفئة بواسطة Aspose.Words.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

يقوم مقتطف التعليمات البرمجية هذا بتحميل المستند الموجود في `dataDir`. تأكد من استبدال `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي للمستند الخاص بك.

## الخطوة 2: تكوين خيارات حفظ PDF

بعد ذلك، نقوم بتكوين `PdfSaveOptions` لضمان تضمين مجموعات الخطوط الفرعية الضرورية فقط. عن طريق ضبط `EmbedFullFonts` ل `false`، نطلب من Aspose.Words تضمين الحروف الرسومية المستخدمة في المستند فقط.

```csharp
// سيحتوي ملف PDF الناتج على مجموعات فرعية من الخطوط الموجودة في المستند.
// يتم تضمين الحروف الرسومية المستخدمة في المستند فقط في خطوط PDF.
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

تساعد هذه الخطوة الصغيرة ولكن الحاسمة في تقليل حجم ملف PDF بشكل كبير.

## الخطوة 3: حفظ المستند بتنسيق PDF

وأخيرًا، نقوم بحفظ المستند بصيغة PDF باستخدام `Save` الطريقة، تطبيق التكوين `PdfSaveOptions`.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

سيقوم هذا الكود بإنشاء ملف PDF باسم `WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf` في الدليل المحدد، مع تضمين مجموعات الخطوط الضرورية فقط.

## خاتمة

وهذا كل ما في الأمر! باتباع هذه الخطوات البسيطة، يمكنك تقليل حجم ملفات PDF بكفاءة عن طريق تضمين مجموعات الخطوط الضرورية فقط باستخدام Aspose.Words لـ .NET. هذا لا يوفر مساحة تخزين فحسب، بل يضمن أيضًا أوقات تحميل أسرع وأداءً أفضل، خاصةً للمستندات ذات الخطوط الكثيفة.

## الأسئلة الشائعة

### لماذا يجب عليّ تضمين مجموعات فرعية من الخطوط فقط في ملف PDF؟
إن تضمين مجموعات الخطوط الضرورية فقط قد يؤدي إلى تقليل حجم ملف PDF بشكل كبير دون المساس بمظهر المستند وقابليته للقراءة.

### هل يمكنني الرجوع إلى تضمين الخطوط الكاملة إذا لزم الأمر؟
نعم، يمكنك ذلك. ما عليك سوى ضبط `EmbedFullFonts` الممتلكات إلى `true` في `PdfSaveOptions`.

### هل يدعم Aspose.Words for .NET ميزات تحسين PDF الأخرى؟
بالتأكيد! يوفر Aspose.Words for .NET مجموعة واسعة من الخيارات لتحسين ملفات PDF، بما في ذلك ضغط الصور وإزالة العناصر غير المستخدمة.

### ما هي أنواع الخطوط التي يمكن تضمينها باستخدام Aspose.Words لـ .NET؟
يدعم Aspose.Words for .NET تضمين مجموعة فرعية من جميع خطوط TrueType المستخدمة في المستند.

### كيف يمكنني التحقق من الخطوط المضمنة في ملف PDF الخاص بي؟
يمكنك فتح ملف PDF في Adobe Acrobat Reader والتحقق من الخصائص ضمن علامة التبويب الخطوط لرؤية الخطوط المضمنة.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}