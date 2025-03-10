---
title: الحفاظ على ترقيم المصدر
linktitle: الحفاظ على ترقيم المصدر
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية استيراد المستندات مع الحفاظ على التنسيق باستخدام Aspose.Words for .NET. دليل خطوة بخطوة مع أمثلة التعليمات البرمجية.
weight: 10
url: /ar/net/join-and-append-documents/keep-source-numbering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# الحفاظ على ترقيم المصدر

## مقدمة

 عند العمل مع Aspose.Words لـ .NET، يمكن التعامل بكفاءة مع استيراد المستندات من مصدر إلى آخر مع الحفاظ على التنسيق باستخدام`NodeImporter` هذا البرنامج التعليمي سوف يرشدك خلال العملية خطوة بخطوة.

## المتطلبات الأساسية

قبل البدء، تأكد من توفر ما يلي:
- تم تثبيت Visual Studio على جهازك.
-  تم تثبيت Aspose.Words لـ .NET. إذا لم يكن الأمر كذلك، فقم بتنزيله من[هنا](https://releases.aspose.com/words/net/).
- المعرفة الأساسية ببرمجة C# و.NET.

## استيراد مساحات الأسماء

أولاً، قم بتضمين المساحات الأساسية اللازمة في مشروعك:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## الخطوة 1: إعداد مشروعك

ابدأ بإنشاء مشروع C# جديد في Visual Studio وقم بتثبيت Aspose.Words عبر NuGet Package Manager.

## الخطوة 2: تهيئة المستندات
إنشاء حالات المصدر (`srcDoc`) والوجهة (`dstDoc`) وثائق.

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## الخطوة 3: تكوين خيارات الاستيراد
قم بإعداد خيارات الاستيراد للحفاظ على تنسيق المصدر، بما في ذلك الفقرات المرقمة.

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## الخطوة 4: استيراد الفقرات
قم بالتكرار عبر الفقرات في المستند المصدر واستيرادها إلى المستند الوجهة.

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## الخطوة 5: احفظ المستند
احفظ المستند المدمج في الموقع المطلوب.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## خاتمة

 في الختام، يعد استخدام Aspose.Words لـ .NET لاستيراد المستندات مع الحفاظ على التنسيق أمرًا مباشرًا مع`NodeImporter` تضمن هذه الطريقة أن مستنداتك تحافظ على مظهرها وبنيتها الأصلية بسلاسة.

## الأسئلة الشائعة

### هل يمكنني استيراد مستندات ذات أنماط تنسيق مختلفة؟
 نعم،`NodeImporter` تدعم الفئة استيراد المستندات باستخدام أنماط التنسيق المتنوعة.

### ماذا لو كانت مستنداتي تحتوي على جداول وصور معقدة؟
يتعامل Aspose.Words for .NET مع الهياكل المعقدة مثل الجداول والصور أثناء عمليات الاستيراد.

### هل Aspose.Words متوافق مع كافة إصدارات .NET؟
يدعم Aspose.Words إصدارات .NET Framework و.NET Core للتكامل السلس.

### كيف يمكنني التعامل مع الأخطاء أثناء استيراد المستند؟
استخدم كتل try-catch للتعامل مع الاستثناءات التي قد تحدث أثناء عملية الاستيراد.

### أين يمكنني العثور على مزيد من الوثائق التفصيلية حول Aspose.Words لـ .NET؟
 قم بزيارة[التوثيق](https://reference.aspose.com/words/net/) للحصول على أدلة شاملة ومراجع API.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
