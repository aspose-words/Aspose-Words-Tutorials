---
title: التحكم في محتوى مربع النص الغني
linktitle: التحكم في محتوى مربع النص الغني
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إضافة عنصر تحكم محتوى مربع النص الغني وتخصيصه في مستند Word باستخدام Aspose.Words for .NET باستخدام هذا الدليل المفصل خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-sdt/rich-text-box-content-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# التحكم في محتوى مربع النص الغني

## مقدمة

في عالم معالجة المستندات، يمكن أن تعمل القدرة على إضافة عناصر تفاعلية إلى مستندات Word على تحسين وظائفها بشكل كبير. ومن بين هذه العناصر التفاعلية عنصر التحكم في محتوى مربع النص الغني. باستخدام Aspose.Words for .NET، يمكنك بسهولة إدراج مربع نص غني وتخصيصه في مستنداتك. سيرشدك هذا الدليل خلال العملية خطوة بخطوة، مما يضمن فهمك لكيفية تنفيذ هذه الميزة بشكل فعال.

## المتطلبات الأساسية

قبل الغوص في البرنامج التعليمي، تأكد من أن لديك ما يلي:

1.  Aspose.Words for .NET: تأكد من تثبيت Aspose.Words for .NET. إذا لم تقم بذلك بعد، يمكنك تنزيله من[هنا](https://releases.aspose.com/words/net/).

2. Visual Studio: بيئة تطوير مثل Visual Studio سوف تساعدك على كتابة وتنفيذ التعليمات البرمجية.

3. المعرفة الأساسية بلغة C#: ستكون المعرفة بلغة C# وبرمجة .NET مفيدة لأننا سنكتب التعليمات البرمجية بهذه اللغة.

4. .NET Framework: تأكد من أن مشروعك يستهدف إصدارًا متوافقًا من .NET Framework.

## استيراد مساحات الأسماء

للبدء، تحتاج إلى تضمين مساحات الأسماء الضرورية في مشروع C# الخاص بك. يتيح لك هذا استخدام الفئات والطرق التي يوفرها Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Drawing;
```

الآن، دعنا نوضح عملية إضافة عنصر التحكم في محتوى مربع النص الغني إلى مستند Word الخاص بك.

## الخطوة 1: تحديد المسار إلى دليل المستندات الخاص بك

أولاً، حدد المسار الذي تريد حفظ المستند فيه. هذا هو المكان الذي سيتم فيه تخزين الملف الناتج.

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 يستبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي تريد حفظ مستندك فيه.

## الخطوة 2: إنشاء مستند جديد

 إنشاء جديد`Document` الكائن الذي سيكون بمثابة الأساس لمستند Word الخاص بك.

```csharp
Document doc = new Document();
```

سيؤدي هذا إلى تهيئة مستند Word فارغ حيث ستضيف المحتوى الخاص بك.

## الخطوة 3: إنشاء علامة مستند منظمة للنص الغني

 لإضافة مربع نص غني، تحتاج إلى إنشاء`StructuredDocumentTag` (SDT) من النوع`RichText`.

```csharp
StructuredDocumentTag sdtRichText = new StructuredDocumentTag(doc, SdtType.RichText, MarkupLevel.Block);
```

 هنا،`SdtType.RichText` يحدد أن SDT سيكون عبارة عن مربع نص غني، و`MarkupLevel.Block` يحدد سلوكه في المستند.

## الخطوة 4: إضافة المحتوى إلى مربع النص الغني

 إنشاء`Paragraph` و أ`Run` كائن لاحتواء المحتوى الذي تريد عرضه في مربع النص الغني. قم بتخصيص النص والتنسيق حسب الحاجة.

```csharp
Paragraph para = new Paragraph(doc);
Run run = new Run(doc);
run.Text = "Hello World";
run.Font.Color = Color.Green;
para.Runs.Add(run);
sdtRichText.ChildNodes.Add(para);
```

في هذا المثال، نضيف فقرة تحتوي على النص "Hello World" بخط باللون الأخضر إلى مربع النص الغني.

## الخطوة 5: إضافة مربع النص الغني إلى المستند

 أضف`StructuredDocumentTag` إلى نص الوثيقة.

```csharp
doc.FirstSection.Body.AppendChild(sdtRichText);
```

تضمن هذه الخطوة تضمين مربع النص الغني في محتوى المستند.

## الخطوة 6: حفظ المستند

وأخيرًا، قم بحفظ المستند في الدليل المحدد.

```csharp
doc.Save(dataDir + "WorkingWithSdt.RichTextBoxContentControl.docx");
```

سيؤدي هذا إلى إنشاء مستند Word جديد باستخدام عنصر التحكم في محتوى مربع النص الغني.

## خاتمة

إن إضافة عنصر تحكم في محتوى مربع نص غني باستخدام Aspose.Words for .NET هي عملية بسيطة تعمل على تعزيز التفاعل في مستندات Word الخاصة بك. باتباع الخطوات الموضحة في هذا الدليل، يمكنك بسهولة دمج مربع نص غني في مستنداتك وتخصيصه ليناسب احتياجاتك.

## الأسئلة الشائعة

### ما هي علامة المستند المنظم (SDT)؟
علامة المستند المنظم (SDT) عبارة عن نوع من عناصر التحكم في المحتوى في مستندات Word المستخدمة لإضافة عناصر تفاعلية مثل مربعات النص والقوائم المنسدلة.

### هل يمكنني تخصيص مظهر مربع النص الغني؟
 نعم، يمكنك تخصيص المظهر عن طريق تعديل خصائص`Run`الكائن، مثل لون الخط وحجمه ونمطه.

### ما هي الأنواع الأخرى من SDTs التي يمكنني استخدامها مع Aspose.Words؟
بالإضافة إلى النص الغني، يدعم Aspose.Words أنواع SDT الأخرى مثل النص العادي، ومحدد التاريخ، والقائمة المنسدلة.

### كيف يمكنني إضافة مربعات نص غنية متعددة إلى مستند؟
 يمكنك إنشاء العديد من`StructuredDocumentTag` الحالات وإضافتها بشكل تسلسلي إلى نص المستند.

### هل يمكنني استخدام Aspose.Words لتعديل المستندات الموجودة؟
نعم، يسمح لك Aspose.Words بفتح مستندات Word الموجودة وتعديلها وحفظها، بما في ذلك إضافة SDTs أو تحديثها.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
