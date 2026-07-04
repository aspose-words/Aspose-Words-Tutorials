---
category: general
date: 2026-06-02
description: كيفية حفظ PDF من ملف DOCX باستخدام Aspose.Words، وتصدير الأشكال كوسوم
  span مضمنة، وتحويل Word إلى PDF في بضع خطوات فقط.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- inline span tags
language: ar
og_description: كيفية حفظ PDF من مستند Word باستخدام Aspose.Words، وتصدير الأشكال
  العائمة كعلامات span مضمنة للحصول على نتيجة تحويل Word إلى PDF نظيفة.
og_title: كيفية حفظ PDF من Word – دليل تصدير الشكل المضمن
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  headline: How to Save PDF from Word with Inline Shape Export – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  name: How to Save PDF from Word with Inline Shape Export – Complete Guide
  steps:
  - name: What if my document contains **SmartArt** or **Charts**?
    text: SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag`
      flag will still wrap them in `<span>` tags, but complex graphics may lose some
      fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`)
      and then inserting it inline.
  - name: Can I **preserve hyperlinks** and **bookmarks**?
    text: Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag`
      setting. Aspose.Words retains all hyperlink and bookmark information automatically.
  - name: How do I **change PDF compression** or **embed fonts**?
    text: '`PdfSaveOptions` offers many additional properties:'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF conversion
title: كيفية حفظ PDF من Word باستخدام تصدير الشكل المضمن – دليل شامل
url: /ar/net/programming-with-pdfsaveoptions/how-to-save-pdf-from-word-with-inline-shape-export-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية حفظ PDF من Word مع تصدير الشكل المضمن – دليل كامل

هل تساءلت يومًا **كيفية حفظ PDF** من ملف Word مع الحفاظ على كل شكل عائم مُدمج بشكل أنيق داخل النص؟ لست وحدك. في العديد من تطبيقات المؤسسات نحتاج إلى *تحويل Word إلى PDF* دون الحصول على صور غير موضوعة بشكل صحيح أو كائنات رسم متشتتة. الخبر السار؟ Aspose.Words يجعل الأمر سهلًا، ويمكنك حتى إخبار المكتبة **بتصدير الأشكال كوسوم `<span>` مضمّنة** بحيث يبدو PDF تمامًا مثل ملف DOCX الأصلي.

في هذا الدرس سنستعرض العملية بالكامل — تحميل ملف DOCX، تعديل `PdfSaveOptions`، وأخيرًا حفظ PDF نظيف. في النهاية ستعرف **كيفية حفظ PDF**، **حفظ docx كـ pdf**، وحتى **كيفية تصدير الأشكال** باستخدام *وسوم span مضمّنة*.

## ما ستحتاجه

- **Aspose.Words for .NET** (أحدث إصدار، 24.x وقت الكتابة).  
- **.NET 6.0** أو أحدث – الكود يعمل أيضًا على .NET Framework 4.7.2، لكن .NET 6 هو الخيار المثالي.  
- مستند Word بسيط يحتوي على شكل عائم واحد على الأقل (صورة، مربع نص، أو رسم).  
- أي بيئة تطوير تفضلها (Visual Studio، Rider، VS Code + ملحق C#).  

هذا كل شيء — لا حزم NuGet إضافية، ولا تعقيدات COM interop. جاهز؟ لنبدأ.

## الخطوة 1: إعداد المشروع وإضافة Aspose.Words

First, create a console app (or integrate the code into your existing service).

```bash
dotnet new console -n WordToPdfDemo
cd WordToPdfDemo
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** إذا كنت تستخدم Visual Studio، يمكنك إضافة الحزمة عبر واجهة NuGet Package Manager — فقط ابحث عن *Aspose.Words*.

## الخطوة 2: تحميل المستند المصدر

Now that the library is referenced, we can load the DOCX. This is the **how to save pdf** part’s first concrete action—getting the source into memory.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

**لماذا هذا مهم:** تحميل الملف يتحقق من صحة المسار وأن Aspose يمكنه تحليل بنية Word. إذا كان الملف يحتوي على أشكال عائمة، فستكون جزءًا من شجرة العقد لكائن `Document`.

## الخطوة 3: تكوين خيارات حفظ PDF — تصدير الأشكال كوسوم مضمّنة

Here’s the heart of **how to export shapes**. By default Aspose.Words renders floating shapes as separate objects in the PDF, which can shift layout. Setting `ExportFloatingShapesAsInlineTag` to `true` tells the engine to wrap each shape in an inline `<span>` element, preserving the flow.

```csharp
        // Step 3: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            // Optional: keep the original page size
            PageMode = PdfPageMode.UseTrimBox
        };
        Console.WriteLine("PDF save options configured – shapes will be inline.");
```

**لماذا تفعيل هذه العلامة؟** تخيل عقدًا يحتوي على صندوق توقيع يطفو فوق النص. عند تحويله إلى PDF دون هذا الإعداد، قد يظهر الصندوق في صفحة مختلفة. وسوم `<span>` المضمّنة تبقي الشكل مرتبطًا بالفقرة المحيطة، مما ينتج نسخة بصرية دقيقة.

## الخطوة 4: حفظ المستند كـ PDF

Finally, we call `doc.Save` with the options we just built. This is the moment you actually **save docx as pdf**.

```csharp
        // Step 4: Save the document as a PDF using the configured options
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved successfully to: {outputPath}");
    }
}
```

Run the program (`dotnet run`) and check the `output.pdf`. You should see your floating shapes rendered inline, just as they appeared in Word.

## الخطوة 5: التحقق من النتيجة — قائمة مراجعة سريعة

1. **كل النص موجود** — لا فقرات مفقودة.  
2. **الأشكال العائمة تظهر في مكانها الصحيح** — أصبحت الآن جزءًا من تدفق النص.  
3. **حجم PDF معقول** — تصدير كوسوم مضمّنة عادةً يقلل من حجم الملف مقارنةً بتدفقات الصور المنفصلة.  

إذا ظهر أي شيء غير صحيح، تحقق مرة أخرى من أن ملف DOCX المصدر يستخدم فعلاً أشكالًا *عائمة* (انقر بزر الماوس الأيمن → Layout → “In line with text” مقابل “Square/Behind text”). تحويل الشكل إلى “In line” قبل التحويل يعمل أيضًا، لكن خيار الوسم المضمّن يمنحك التحكم دون تعديل الملف الأصلي.

## الحالات الخاصة والأسئلة الشائعة

### ماذا لو كان المستند يحتوي على **SmartArt** أو **Charts**؟

SmartArt والرسوم البيانية يُعاملان ككائنات رسم. ستظل علامة `ExportFloatingShapesAsInlineTag` تغلفها بوسوم `<span>`، لكن الرسومات المعقدة قد تفقد بعض الدقة. في تلك الحالات، فكر في تصدير الرسم البياني كصورة أولاً (`Chart.ToImage()`) ثم إدراجه مضمّنًا.

### هل يمكنني **الحفاظ على الروابط التشعبية** و**الإشارات المرجعية**؟

بالطبع. لا تتأثر هذه العناصر بإعداد `ExportFloatingShapesAsInlineTag`. تحتفظ Aspose.Words بجميع معلومات الروابط التشعبية والإشارات المرجعية تلقائيًا.

### كيف يمكنني **تغيير ضغط PDF** أو **تضمين الخطوط**؟

`PdfSaveOptions` توفر العديد من الخصائص الإضافية:

```csharp
pdfOpts.JpegQuality = 90;               // Adjust image compression
pdfOpts.FontEmbeddingMode = FontEmbeddingMode.EmbedAll; // Embed all used fonts
```

لا تتردد في تعديل هذه الإعدادات وفقًا لمتطلباتك اللاحقة (مثل الامتثال لـ PDF/A).

## مثال كامل جاهز للنسخ واللصق

Below is the complete program you can copy into `Program.cs`. Replace `YOUR_DIRECTORY` with an actual folder path.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source DOCX (contains floating shapes)
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded.");

        // Configure PDF save options – export shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            PageMode = PdfPageMode.UseTrimBox,
            // Optional tweaks
            JpegQuality = 90,
            FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };
        Console.WriteLine("PDF options set – shapes will be inline.");

        // Save as PDF
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

**الناتج المتوقع في وحدة التحكم:**

```
Document loaded.
PDF options set – shapes will be inline.
PDF saved to C:\MyDocs\output.pdf
```

Open `output.pdf`—you’ll see the original layout, with every floating shape snugly placed inside the text flow.

## الخلاصة

We’ve covered **how to save PDF** from a Word document while ensuring that floating shapes become inline `<span>` tags. By loading the DOCX, configuring `PdfSaveOptions`, and invoking `doc.Save`, you can reliably **save docx as pdf** and **convert word to pdf** without layout surprises.  

الخطوات التالية؟ جرّب دمج هذا النهج مع الامتثال لـ **PDF/A** للأرشفة، أو معالجة مجموعة من ملفات DOCX دفعيًا باستخدام حلقة `foreach` بسيطة. يمكنك أيضًا استكشاف **التصيير المخصص** (مثل إضافة العلامات المائية) من خلال الاستفادة من API `DocumentVisitor` في Aspose.Words.

هل لديك المزيد من الأسئلة حول معالجة الأشكال، تضمين الخطوط، أو تحسين الأداء؟ اترك تعليقًا أدناه، وتمنياتنا لك بالبرمجة السعيدة!

## ماذا يجب أن تتعلمه بعد ذلك؟

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [كيفية حفظ المستند كـ pdf باستخدام Aspose.Words للـ Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [تحويل Word إلى PDF باستخدام Aspose.Words للـ Java](/words/english/java/document-converting/exporting-documents-to-pdf/)
- [aspose word to pdf – تحويل DOCX إلى PDF في Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}