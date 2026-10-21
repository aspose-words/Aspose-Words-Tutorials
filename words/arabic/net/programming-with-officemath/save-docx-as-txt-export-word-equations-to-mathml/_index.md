---
category: general
date: 2026-06-24
description: احفظ ملف docx كملف txt وحوّل رياضيات Word بسهولة إلى LaTeX أو صدّر معادلات Word
  بصيغة MathML للمعالجة اللاحقة. دليل خطوة‑بخطوة.
draft: false
keywords:
- save docx as txt
- convert word math to latex
- export word equations mathml
- extract equations from word
language: ar
og_description: احفظ ملف docx كملف txt وصدر معادلات Word بصيغة MathML (أو LaTeX) مع
  مثال كامل للكود. تعلم كيفية استخراج المعادلات من Word.
og_title: حفظ ملف docx كملف txt – تصدير معادلات Word إلى MathML
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: save docx as txt and easily convert word math to LaTeX or export word
    equations MathML for downstream processing. Step‑by‑step guide.
  headline: save docx as txt – Export Word Equations to MathML
  type: TechArticle
- description: save docx as txt and easily convert word math to LaTeX or export word
    equations MathML for downstream processing. Step‑by‑step guide.
  name: save docx as txt – Export Word Equations to MathML
  steps:
  - name: – Load the source document
    text: First we need to bring the `.docx` into memory. The `Document` class does
      all the heavy lifting.
  - name: – Choose how to export the equations
    text: Aspose.Words lets you decide whether you want **MathML** (ideal for web
      rendering) or **LaTeX** (perfect for scientific pipelines). This is controlled
      via the `OfficeMathExportMode` property of `TxtSaveOptions`.
  - name: – Save the document as plain‑text
    text: Now we write the file. The `Save` method respects the options we just set,
      so every equation is replaced by its chosen markup.
  - name: – Verify the output (optional but recommended)
    text: It’s good practice to read the file back and confirm that the markup appears
      where you expect it.
  - name: Multiple equations on the same line
    text: 'Word sometimes stores several `OfficeMath` objects in a single paragraph.
      Aspose.Words will serialize each one sequentially, preserving whitespace. If
      you need a custom separator, you can post‑process the text:'
  - name: Documents without any equations
    text: '`TxtSaveOptions` still works—your output will be a faithful plain‑text
      copy of the original document. No special handling required, but you might want
      to log a warning:'
  - name: Large files and memory usage
    text: 'For massive Word files, consider using the **LoadOptions** constructor
      that streams the document instead of loading it entirely into memory:'
  type: HowTo
tags:
- Aspose.Words
- .NET
- document-conversion
title: حفظ ملف docx كملف txt – تصدير معادلات Word إلى MathML
url: /ar/net/programming-with-officemath/save-docx-as-txt-export-word-equations-to-mathml/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ docx كـ txt – تصدير معادلات Word إلى MathML

هل تساءلت يوماً كيف **تحفظ docx كـ txt** مع الحفاظ على تلك المعادلات المزعجة؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحتاجون لاستخراج الرياضيات من ملف Word وإرسالها إلى معالج لاحق لا يتعامل إلا مع النص العادي.

الخبر السار: يمكنك القيام بذلك ببضع أسطر من C# دون الحاجة لكتابة محلل خاص بك. في هذا الدرس سنستعرض تحويل ملف `.docx` إلى ملف `.txt`، وتصدير المعادلات إما كـ **MathML** أو **LaTeX** — بالضبط ما تحتاجه **لاستخراج المعادلات من Word** والحفاظ على قابليتها للاستخدام.

بنهاية هذا الدليل ستكون قادرًا على:

* تحميل أي مستند Word باستخدام Aspose.Words.
* اختيار وضع تصدير المعادلة (`MathML` أو `LaTeX`).
* حفظ النتيجة كنص عادي، مع الحفاظ على كل صيغة.
* التحقق من المخرجات ومعالجة الحالات الشائعة.

بدون إطالة، مجرد حل كامل وقابل للتنفيذ يمكنك نسخه ولصقه في مشروعك.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من وجود:

* **.NET 6.0** (أو أحدث) مثبت – الشيفرة تعمل على Windows أو Linux أو macOS.
* حزمة **Aspose.Words for .NET** عبر NuGet. ثبّتها باستخدام:

```bash
dotnet add package Aspose.Words
```

* مستند Word (`.docx`) يحتوي على معادلة واحدة على الأقل. إذا لم يكن لديك واحد، أنشئ ملفًا سريعًا في Microsoft Word وأدرج معادلة عبر **Insert → Equation**.

هذا كل ما تحتاجه. لا مكتبات إضافية، لا COM interop، ولا أي تحليل يدوي.

## حفظ docx كـ txt باستخدام Aspose.Words

تكمن جوهر الحل في ثلاث خطوات بسيطة: التحميل، الإعداد، والحفظ. لنستعرض كل خطوة.

### الخطوة 1 – تحميل المستند المصدر

أولًا نحتاج إلى جلب ملف `.docx` إلى الذاكرة. تقوم فئة `Document` بكل العمل الشاق.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file from disk
Document doc = new Document(@"C:\Temp\input.docx");
```

*لماذا هذا مهم*: تقوم `Document` بتحليل حزمة OpenXML، وتبني نموذجًا كائنيًا، وتمنحنا وصولًا مباشرًا إلى كل عنصر — بما في ذلك كائنات `OfficeMath` التي تمثل المعادلات.

### الخطوة 2 – اختيار طريقة تصدير المعادلات

تتيح لك Aspose.Words تحديد ما إذا كنت تريد **MathML** (مثالي للعرض على الويب) أو **LaTeX** (مثالي لسلاسل المعالجة العلمية). يتم التحكم في ذلك عبر الخاصية `OfficeMathExportMode` في `TxtSaveOptions`.

```csharp
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Switch between MathML and LaTeX by changing the enum value
    OfficeMathExportMode = OfficeMathExportMode.MathML   // or OfficeMathExportMode.LaTeX
};
```

*نصيحة محترف*: إذا كنت ستغذي النص إلى محرك يدعم LaTeX (مثل Pandoc أو دفتر Jupyter)، اضبط الوضع على `LaTeX`. بالنسبة للعارضات القائمة على الويب التي تفهم MathML، ابقَ على `MathML`.

### الخطوة 3 – حفظ المستند كنص عادي

الآن نكتب الملف. تحترم طريقة `Save` الخيارات التي ضبطناها، لذا تُستبدل كل معادلة بالترميز المختار.

```csharp
// Save as a .txt file; equations are now MathML or LaTeX strings
doc.Save(@"C:\Temp\Equations.txt", txtOptions);
```

هذه هي العملية بأكملها. عند فتح `Equations.txt` سترى شيئًا مثل:

```
This is a sample paragraph.

<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mrow>
    <mi>x</mi>
    <mo>=</mo>
    <mfrac>
      <mn>‑b</mn>
      <mi>a</mi>
    </mfrac>
  </mrow>
</math>

Another paragraph with no equations.
```

إذا اخترت `LaTeX`، سيظهر المقتطف هكذا:

```
This is a sample paragraph.

\[
x = \frac{-b}{a}
\]

Another paragraph with no equations.
```

### الخطوة 4 – التحقق من المخرجات (اختياري لكن موصى به)

من الممارسات الجيدة قراءة الملف مرة أخرى والتأكد من ظهور الترميز في الموضع المتوقع.

```csharp
string txtContent = File.ReadAllText(@"C:\Temp\Equations.txt");

// Simple sanity check: look for a MathML tag or a LaTeX delimiter
bool containsMathML = txtContent.Contains("<math");
bool containsLaTeX = txtContent.Contains("\\[") && txtContent.Contains("\\]");

Console.WriteLine($"MathML detected: {containsMathML}");
Console.WriteLine($"LaTeX detected: {containsLaTeX}");
```

إذا طبع الطرفية `true` للصيغة التي اخترتها، فقد نجحت في **convert word math to latex** (أو MathML). وإلا، راجع قيمة `OfficeMathExportMode`.

## معالجة الحالات الشائعة

### عدة معادلات في نفس السطر

أحيانًا يخزن Word عدة كائنات `OfficeMath` في فقرة واحدة. سيقوم Aspose.Words بتسلسل كل واحدة منها، مع الحفاظ على الفراغات. إذا أردت فاصلًا مخصصًا، يمكنك معالجة النص بعد ذلك:

```csharp
string processed = Regex.Replace(txtContent, @"(?<=\])\s+(?=\[)", "\n---\n");
File.WriteAllText(@"C:\Temp\ProcessedEquations.txt", processed);
```

### مستندات بدون أي معادلات

ما زالت `TxtSaveOptions` تعمل — سيصبح الناتج نسخة نصية مطابقة للمستند الأصلي. لا تحتاج إلى معالجة خاصة، لكن قد ترغب في تسجيل تحذير:

```csharp
if (!txtContent.Contains("<math") && !txtContent.Contains("\\["))
{
    Console.WriteLine("Warning: No equations were found in the source document.");
}
```

### ملفات كبيرة واستهلاك الذاكرة

للملفات الضخمة، فكر في استخدام مُنشئ **LoadOptions** الذي يبث المستند بدلاً من تحميله بالكامل في الذاكرة:

```csharp
LoadOptions loadOpts = new LoadOptions { LoadFormat = LoadFormat.Docx };
Document largeDoc = new Document(@"C:\Temp\bigfile.docx", loadOpts);
largeDoc.Save(@"C:\Temp\bigfile.txt", txtOptions);
```

هذا النهج يحافظ على خفة عملية **extract equations from word**.

## مثال كامل قابل للتنفيذ

بدمج كل ما سبق، إليك برنامج واحد يمكنك تجميعه وتشغيله:

```csharp
using System;
using System.IO;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document
        string inputPath = @"C:\Temp\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Configure TXT save options – change to LaTeX if you prefer
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.MathML // or OfficeMathExportMode.LaTeX
        };

        // 3️⃣ Save as plain‑text with equations exported
        string outputPath = @"C:\Temp\Equations.txt";
        doc.Save(outputPath, txtOptions);
        Console.WriteLine($"Document saved to {outputPath}");

        // 4️⃣ Verify the result (optional)
        string txtContent = File.ReadAllText(outputPath);
        bool hasMathML = txtContent.Contains("<math");
        bool hasLaTeX = txtContent.Contains("\\[") && txtContent.Contains("\\]");

        Console.WriteLine($"MathML present: {hasMathML}");
        Console.WriteLine($"LaTeX present: {hasLaTeX}");

        // 5️⃣ Simple post‑processing example (add a visual separator)
        string processed = Regex.Replace(txtContent, @"(?<=\])\s+(?=\[)", "\n---\n");
        File.WriteAllText(@"C:\Temp\ProcessedEquations.txt", processed);
        Console.WriteLine("Post‑processed file created.");
    }
}
```

**الناتج المتوقع** (عند استخدام `OfficeMathExportMode.MathML`):

```
Document saved to C:\Temp\Equations.txt
MathML present: True
LaTeX present: False
Post‑processed file created.
```

افتح `Equations.txt` لرؤية وسوم MathML الخام؛ وافتح `ProcessedEquations.txt` لرؤية الفاصل المخصص بين أي كتل LaTeX متجاورة.

## الأسئلة المتكررة

* **هل يمكنني تصدير كل من MathML *و* LaTeX في نفس الوقت؟**  
  ليس مباشرة — تسمح لك Aspose.Words باختيار وضع واحد لكل عملية حفظ. الحل هو تشغيل الحفظ مرتين بخيارات مختلفة ثم دمج النتائج يدويًا.

* **ماذا عن المعادلات داخل الجداول؟**  
  تُعامل تمامًا كأي كائن `OfficeMath` آخر. سيظهر الترميز داخل النص المحيط بخلية الجدول.

* **هل المكتبة مجانية؟**  
  تقدم Aspose.Words نسخة تجريبية مجانية مع جميع الوظائف. للاستخدام الإنتاجي تحتاج إلى ترخيص، لكن واجهة البرمجة تبقى نفسها.

## الخلاصة

أظهرنا لك كيفية **حفظ docx كـ txt** مع الحفاظ على كل صيغة، مما يمنحك القدرة على **convert word math to latex** أو **export word equations MathML** لأي سير عمل لاحق. النهج خفيف، يعتمد فقط على Aspose.Words، ويعمل على جميع منصات .NET الرئيسية.

ما الخطوة التالية؟ جرّب إدخال MathML الناتج في صفحة HTML باستخدام MathJax، أو مرّر LaTeX إلى مولّد مواقع ثابت يدعم الرياضيات. يمكنك أيضًا أتمتة معالجة مجموعة من ملفات Word عبر حلقة `foreach`.

هل لديك سيناريوهات أخرى — مثل استخراج المعادلات فقط وتجاهل النص المحيط؟ لا تتردد في تجربة `Document.GetChildNodes(NodeType.Office`


## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شاملة مع شرح خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [How to Export LaTeX from Word: Convert DOCX to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/how-to-export-latex-from-word-convert-docx-to-markdown-with/)
- [Convert docx to markdown – Export Math Equations to LaTeX with Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [Save docx as markdown – Complete C# Guide with LaTeX Equations](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-complete-c-guide-with-latex-equations/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}