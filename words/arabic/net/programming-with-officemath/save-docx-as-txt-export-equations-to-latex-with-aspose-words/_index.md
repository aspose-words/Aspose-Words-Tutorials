---
category: general
date: 2026-02-12
description: احفظ ملف docx كملف txt وحوّل المعادلات إلى LaTeX دفعة واحدة. تعلّم كيفية
  تصدير الرياضيات من Word باستخدام C# و Aspose.Words.
draft: false
keywords:
- save docx as txt
- convert docx to txt
- how to export math
- convert equations to latex
- how to export equations
language: ar
og_description: احفظ ملف docx كملف txt وصدر الصيغ الرياضية إلى LaTeX باستخدام C#.
  دليل خطوة‑بخطوة لـ Aspose.Words.
og_title: حفظ ملف docx كـ txt – تصدير معادلات Word إلى LaTeX
tags:
- Aspose.Words
- C#
- Document Conversion
title: حفظ ملف docx كملف txt – تصدير المعادلات إلى LaTeX باستخدام Aspose.Words
url: /ar/net/programming-with-officemath/save-docx-as-txt-export-equations-to-latex-with-aspose-words/
---

Be careful with markdown formatting: keep headings (#) and bullet list markers.

Let's craft translation.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ docx كـ txt – تصدير معادلات Word إلى LaTeX باستخدام Aspose.Words

هل احتجت يوماً إلى **save docx as txt** لكن واجهت صعوبة عندما يحتوي مستندك على Office Math؟ لست وحدك. يعتقد معظم المطورين أن تصدير النص العادي سيزيل كل شيء ببساطة، لكن المعادلات تختفي، مما يتركك مع فوضى غير قابلة للقراءة.  

الخبر السار؟ مع Aspose.Words يمكنك **save docx as txt** *و* إخبار المكتبة بأن تعرض كل معادلة كرمز LaTeX. في هذا الدرس سنستعرض العملية بالكامل، من تحميل ملف `.docx` إلى إنتاج ملف `.txt` نظيف يحتوي على جميع معادلاتك بصيغة جاهزة للنشر العلمي.

بنهاية هذا الدرس ستعرف **how to export math** من Word، ولماذا قد ترغب في **convert equations to latex**، وكيفية **convert docx to txt** دون فقدان أي محتوى مهم.

## ما ستحتاجه

- **Aspose.Words for .NET** (الإصدار 23.8 أو أحدث). حزمة NuGet هي `Aspose.Words`.
- بيئة تطوير .NET (Visual Studio، Rider، أو VS Code مع امتداد C#).
- مستند Word تجريبي (`input.docx`) يحتوي على كائن Office Math واحد على الأقل.
- إلمام أساسي بـ C# وتطبيقات الكونسول.

لا توجد أدوات طرف ثالث إضافية مطلوبة؛ كل شيء يعمل في C# النقي.

## الخطوة 1 – تحميل المستند المصدر

الأول الذي نفعله هو قراءة ملف Word إلى كائن `Document`. هذا الكائن يمثل حزمة Word بالكامل في الذاكرة، مما يتيح لنا الوصول إلى الفقرات والجداول وعقد Office Math المخفية.

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document(@"C:\MyFiles\input.docx");
```

> **Why this matters:** تحميل المستند بهذه الطريقة يسمح لـ Aspose.Words بالحفاظ على البنية الأصلية، لذا عندما نقوم لاحقًا بتصديره إلى TXT لا يزال المكتبة تعرف مكان كل معادلة.

## الخطوة 2 – إخبار Aspose.Words بكيفية التعامل مع Office Math

افتراضيًا، `TxtSaveOptions` يكتب نصًا عاديًا فقط ويتجاهل أي رياضيات. نغيّر هذا السلوك بتعيين `OfficeMathExportMode` إلى `LaTeX`. هذا يخبر المحرك باستبدال كل كائن Office Math بتمثيله في LaTeX.

```csharp
// Step 2: Configure TXT save options to export Office Math as LaTeX
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

> **Pro tip:** إذا احتجت يومًا المعادلات بصيغة MathML بدلاً من ذلك، استبدل `OfficeMathExportMode.LaTeX` بـ `OfficeMathExportMode.MathML`. نفس الـ API يعمل لكلا الصيغتين.

## الخطوة 3 – حفظ المستند كملف نص عادي

الآن نقوم بالتحويل الفعلي. طريقة `Save` تستقبل مسار الهدف والخيارات التي قمنا بتكوينها للتو.

```csharp
// Step 3: Save the document as a plain‑text file using the configured options
doc.Save(@"C:\MyFiles\Equations.txt", txtSaveOptions);
```

عند تشغيل الكود، سيحتوي الملف `Equations.txt` على:

```
This is a sample paragraph.
Here is an inline equation: $E = mc^2$
And a displayed equation:
\[
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
\]
```

> **What you see:** كل كائن Office Math الآن محاط بفواصل LaTeX (`$…$` للخط الداخلي، `\[`…`\]` للعرض). يبقى النص المحيط كما هو تمامًا في ملف DOCX الأصلي.

## مثال كامل قابل للتنفيذ

فيما يلي تطبيق كونسول بسيط يمكنك نسخه‑ولصقه في مشروع C# جديد وتشغيله فورًا.

```csharp
using System;
using Aspose.Words;

namespace DocxToTxtWithLatex
{
    class Program
    {
        static void Main(string[] args)
        {
            // Define input and output paths
            string inputPath = @"C:\MyFiles\input.docx";
            string outputPath = @"C:\MyFiles\Equations.txt";

            // Load the Word document
            Document doc = new Document(inputPath);

            // Configure save options – export equations as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX
            };

            // Perform the conversion
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"Successfully saved TXT with LaTeX equations to: {outputPath}");
        }
    }
}
```

### النتيجة المتوقعة

افتح `Equations.txt` بأي محرر نصوص. يجب أن ترى الفقرات الأصلية، وتظهر كل معادلة كرمز LaTeX. هذا الملف الآن جاهز لتغذيته إلى مترجم LaTeX، أو معالج markdown، أو أي نظام يفهم صيغ LaTeX.

## أسئلة شائعة وحالات خاصة

### 1. *ماذا لو كان المستند لا يحتوي على معادلات؟*  
لا يزال التحويل يعمل؛ سيكتب Aspose.Words محتوى النص فقط. لا تُضاف فواصل LaTeX إضافية.

### 2. *هل يمكنني تخصيص الفواصل؟*  
نعم. `TxtSaveOptions` يتيح خصائص `InlineMathDelimiter` و `DisplayMathDelimiter`. على سبيل المثال:

```csharp
saveOptions.InlineMathDelimiter = @"\(";
saveOptions.DisplayMathDelimiter = @"\[\[";
```

### 3. *ماذا عن المستندات الكبيرة (مئات الميجابايت)؟*  
Aspose.Words يبث الملف داخليًا، لذا يبقى استهلاك الذاكرة معتدلًا. ومع ذلك، قد ترغب في زيادة إعداد `MemoryUsage` إذا صادفت `OutOfMemoryException`.

### 4. *هل يضمن إخراج LaTeX أن يتم تجميعه بنجاح؟*  
Aspose.Words يتبع خريطة التحويل من Office Math إلى LaTeX التي حددتها Microsoft. معظم البُنى الشائعة (الكسر، التكاملات، المجاميع، المصفوفات) تُجمع دون مشكلة. قد تحتاج الرموز النادرة إلى تعديل يدوي.

### 5. *هل يمكنني أيضًا التصدير إلى صيغ نصية أخرى؟*  
بالطبع. النمط نفسه يعمل مع `HtmlSaveOptions`، `MarkdownSaveOptions`، إلخ. فقط استبدل `TxtSaveOptions` بالفئة المناسبة.

## نصائح لتجربة سلسة

- **Validate the output**: شغّل `pdflatex` سريعًا على مقطع صغير للتأكد من أن LaTeX المُولد لا يفتقد حزمًا.
- **Batch processing**: غلف الكود أعلاه داخل حلقة `foreach` لتحويل عدة ملفات DOCX دفعة واحدة.
- **Logging**: استخدم `Console.WriteLine` أو مسجل مناسب لالتقاط أي تحذيرات قد تصدرها Aspose.Words حول ميزات رياضية غير مدعومة.
- **Version check**: تم تقديم تعداد `OfficeMathExportMode` في Aspose.Words 22.9. إذا كنت تستخدم نسخة أقدم، قم بالترقية عبر NuGet.

## الخلاصة

لقد أظهرنا لك كيفية **save docx as txt** مع الحفاظ على كل معادلة كرمز LaTeX. نهج الثلاث خطوات — تحميل، تكوين، حفظ — يغطي سير العمل بالكامل، والمثال الكامل يتيح لك إدراج الكود في أي مشروع .NET الآن.  

إذا كنت تبحث عن **convert docx to txt** للمعالجة اللاحقة، أو تحتاج ببساطة إلى **how to export equations** لورقة علمية، فإن هذه الطريقة موثوقة وسهلة التوسيع. بعد ذلك، قد تستكشف **how to export math** إلى لغات توصيف أخرى (MathML، ASCIIMath) أو دمج مخرجات TXT مع مولد مواقع ثابتة لإنشاء مواقع توثيق.

برمجة سعيدة، ولتكن تحويلاتك خالية من الأخطاء!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}