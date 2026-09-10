---
category: general
date: 2026-02-13
description: احفظ ملف docx كملف pdf مع الحفاظ على الأشكال العائمة. تعلم كيفية تحويل Word
  إلى pdf، وتصدير الأشكال، ومعالجة الحالات الخاصة في C#.
draft: false
keywords:
- save docx as pdf
- convert word to pdf
- how to export shapes
- convert word document pdf
- how to convert docx pdf
language: ar
og_description: احفظ ملف docx كـ pdf مع الحفاظ على الأشكال العائمة. يوضح هذا الدليل
  كيفية تحويل Word إلى pdf، وتصدير الأشكال، والتعامل مع المشكلات الشائعة.
og_title: حفظ ملف docx كـ pdf باستخدام تصدير الشكل – دليل كامل
tags:
- Aspose.Words
- C#
- PDF conversion
title: حفظ ملف docx كـ pdf باستخدام تصدير الشكل – دليل كامل
url: /ar/net/programming-with-pdfsaveoptions/save-docx-as-pdf-with-shape-export-complete-guide/
---

change is the `Save` method’s format argument.

Got more questions? Drop a comment, and happy coding!

Translate.

Then closing shortcodes.

Make sure to keep all markdown formatting.

Now produce final Arabic content.

Let's write.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ docx كـ pdf – دليل شامل (C#)

هل احتجت يومًا إلى **save docx as pdf** والحفاظ على تلك المخططات العائمة بنفس الشكل تمامًا؟ أنت لست وحدك. يواجه العديد من المطورين مشكلة عندما تختفي أشكال Word أو تتشوه بعد التحويل. الخبر السار؟ ببضع أسطر من C# يمكنك إخبار المكتبة بمعاملة كل شكل كعنصر على مستوى الكتلة، والنتيجة هي نسخة PDF مطابقة.

في هذا الدليل سنستعرض العملية بالكامل: تحميل ملف `.docx`، وتكوين خيارات **convert word to pdf** بحيث يتم تصدير الأشكال بشكل صحيح، وأخيرًا كتابة ملف PDF إلى القرص. في النهاية ستعرف **how to export shapes**، وتفهم الموازين بين أوضاع التصدير المختلفة، وستحصل على عينة كود جاهزة للتنفيذ يمكنك إدراجها في أي مشروع .NET.

> **ما ستحصل عليه:** مثال كامل قابل للتنفيذ، شرح لماذا كل إعداد مهم، نصائح للحالات الخاصة، وأفكار لتوسيع الحل (مثل معالجة الصور، الخطوط المخصصة، أو ملفات PDF المحمية بكلمة مرور).

---

## Prerequisites

- .NET 6+ (أو .NET Framework 4.7+). الـ API الذي نستخدمه يعمل على كلاهما.
- Aspose.Words for .NET (نسخة تجريبية مجانية أو نسخة مرخصة). التثبيت عبر NuGet: `Install-Package Aspose.Words`.
- مستند Word (`input.docx`) يحتوي على أشكال عائمة (صناديق نصية، أشكال تلقائية، SmartArt، إلخ).
- Visual Studio 2022 أو أي بيئة تطوير تفضّلها.

لا توجد مكتبات طرف ثالث أخرى مطلوبة.

---

## Step‑by‑Step Implementation

أدناه كل خطوة ستظهر لك مقتطف كود قصير، شرح بسيط باللغة الإنجليزية، وملاحظة حول **how to export shapes** بشكل صحيح.

### ## Step 1 – Load the source document (save docx as pdf)

```csharp
// Step 1: Load the source document
// This is the starting point for any conversion – you must have a Document object.
Document doc = new Document(@"C:\MyFolder\input.docx");
```

*لماذا هذا مهم:* فئة `Document` تمثل ملف Word بالكامل في الذاكرة. إذا تخطيت هذه الخطوة، لن يكون هناك ما يُحوَّل، ولن يكون لإعدادات PDF اللاحقة ما تتعامل معه.

### ## Step 2 – Configure PDF save options (how to export shapes)

```csharp
// Step 2: Configure PDF save options to export floating shapes as block‑level tags
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
{
    // ExportFloatingShapesAsInlineTag determines how shapes are rendered in PDF.
    // Setting it to Block ensures each shape gets its own block, preserving layout.
    ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block
};
```

**Explanation**

- `PdfSaveOptions` هي “حقيبة إعدادات” تخبر Aspose.Words كيف تُترجم بنى Word إلى PDF.
- الخاصية **ExportFloatingShapesAsInlineTag** لها ثلاث قيم محتملة:
  1. **Inline** – تتحول الأشكال إلى عناصر داخلية (غالبًا ما تُضغط داخل النص المجاور).
  2. **Block** – يُوضع كل شكل في كتلة خاصة به، وهي الطريقة الأكثر أمانًا للحفاظ على المظهر الأصلي.
  3. **Auto** – تقرر المكتبة تلقائيًا (قد لا تختار دائمًا الخيار الأنسب).

اختيار **Block** هو النهج الموصى به عندما *need to export shapes* بالضبط كما تظهر في المستند الأصلي. يمنع ذلك مشكلة “اختفاء الشكل” التي يواجهها الكثيرون عند استدعاء `doc.Save("out.pdf")` ببساطة.

### ## Step 3 – Save the document as PDF (convert word to pdf)

```csharp
// Step 3: Save the document as PDF using the configured options
doc.Save(@"C:\MyFolder\FloatingShapes.pdf", pdfSaveOptions);
```

*ما ستراه:* بعد تنفيذ هذا السطر، سيظهر `FloatingShapes.pdf` في `C:\MyFolder`. افتحه، ويجب أن ترى كل صندوق نص، وتعليق، وSmartArt في الموضع نفسه كما هو في ملف `.docx` الأصلي.

---

## Full Working Example

أدناه **البرنامج الكامل** الذي يمكنك تجميعه وتشغيله كتطبيق Console. يتضمن جميع بيانات `using` الضرورية وتعليقات للتوضيح.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the DOCX file you want to convert.
        // Replace the path with your own file location.
        Document doc = new Document(@"C:\MyFolder\input.docx");

        // 2️⃣ Set up PDF options – this is where we tell Aspose.Words
        //    how to handle floating shapes.
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            // ExportFloatingShapesAsInlineTag = Block makes each shape a separate block.
            ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block,

            // Optional: preserve the original page size.
            PageMode = PdfPageMode.UseOutlines,

            // Optional: embed fonts to avoid missing‑glyph issues.
            EmbedFullFonts = true
        };

        // 3️⃣ Write the PDF to disk.
        string outPath = @"C:\MyFolder\FloatingShapes.pdf";
        doc.Save(outPath, pdfOptions);

        Console.WriteLine($"Successfully saved DOCX as PDF: {outPath}");
    }
}
```

**Expected output**

```
Successfully saved DOCX as PDF: C:\MyFolder\FloatingShapes.pdf
```

افتح ملف PDF الناتج وتأكد من أن جميع الأشكال تحتفظ بمواقعها الأصلية. إذا ما زال أي شكل يبدو غير صحيح، تحقق مرة أخرى من أنه فعلاً *floating* shape (وليس صورة داخلية) في Word.

---

## Frequently Asked Questions & Edge Cases

| Question | Answer |
|----------|--------|
| **Can I export shapes as inline instead of block?** | نعم – اضبط `ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Inline`. قد يكون ذلك مفيدًا لتخطيطات بسيطة، لكن توقع تدفق نص أقرب وتداخل محتمل. |
| **What if my document contains images inside shapes?** | نفس الخيار يعمل؛ Aspose.Words يرسم الشكل مع صورته. للحصول على أعلى دقة، فعّل أيضًا `PdfSaveOptions.JpegQuality` إذا كنت تحتاج إلى ضغط صور أفضل. |
| **Does this work with password‑protected DOCX files?** | حمّل المستند باستخدام كائن `LoadOptions` يزود كلمة المرور، ثم تابع كالمعتاد. |
| **Can I convert multiple DOCX files in a batch?** | ضع منطق الخطوات الثلاث داخل حلقة `foreach` على قائمة الملفات. تذكر إعادة استخدام `PdfSaveOptions` لتحسين الأداء. |
| **Is the PDF compatible with older readers (Acrobat 7)?** | بشكل افتراضي تُنشئ Aspose.Words ملفات PDF 1.7. اضبط `pdfOptions.Compliance = PdfCompliance.PdfA1b` للحصول على ملفات PDF من الدرجة الأرشيفية تعمل على القارئات القديمة. |

---

## Pro Tips & Common Pitfalls

- **Pro tip:** إذا لاحظت انزياحات رأسية طفيفة بعد التحويل، جرّب ضبط `pdfOptions.UsePdfDocumentStructure = true`. هذا يجبر محرك PDF على احترام هيكل تخطيط Word.
- **Watch out for:** المستندات التي تمزج بين الأشكال العائمة والجداول المرسَّخة. في بعض الحالات، قد يدفع تصدير الكتلة الجدول إلى صفحة جديدة؛ يمكنك التخفيف من ذلك بتعديل `pdfOptions.PageSetup` قبل الحفظ.
- **Performance note:** إعادة استخدام كائن `PdfSaveOptions` واحد للعديد من الملفات يقلل من ضغط الـ GC ويسرّع التحويلات الدفعية.

---

## Visual Reference

أدناه لقطة شاشة تخطيطية (عنصر نائب) تُظهر قبل/بعد مستند يحتوي على صندوق نص عائم.

![save docx as pdf example with floating shapes](image-placeholder.png "save docx as pdf example with floating shapes")

*توضح الصورة كيف يبقى الشكل في الموضع نفسه تمامًا كما كان في ملف Word الأصلي بعد التحويل.*

---

## Wrap‑Up

غطّينا **how to save docx as pdf** مع الحفاظ على كل شكل عائم كما هو، واستعرضنا إعدادات **convert word to pdf** المهمة، وأجبنا على أكثر الأسئلة شيوعًا حول “**how to export shapes**”. عينة الكود الكاملة جاهزة للإدراج في أي مشروع C#، والتعديلات الاختيارية تمنحك مرونة للتعامل مع سيناريوهات العالم الحقيقي مثل المعالجة الدفعية أو توافق PDF/A.

### Next Steps

- جرّب **convert word document pdf** بمستويات امتثال مختلفة (`PdfCompliance.PdfA2b`, `PdfCompliance.PdfUa`) لتلبية المتطلبات التنظيمية.
- جرب **how to convert docx pdf** للملفات المحمية بكلمة مرور—أضف `LoadOptions` مع كلمة مرور و`PdfSaveOptions` مع `EncryptionDetails`.
- استكشف صيغ إخراج أخرى (مثل XPS، HTML) باستخدام نفس كائن `Document`؛ التغيير الوحيد هو وسيط صيغة الدالة `Save`.

هل لديك أسئلة إضافية؟ اترك تعليقًا، وتمنياتنا لك ببرمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}