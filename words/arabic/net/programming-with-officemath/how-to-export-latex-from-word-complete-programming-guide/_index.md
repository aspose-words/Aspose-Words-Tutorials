---
category: general
date: 2026-06-17
description: كيفية تصدير LaTeX من Word باستخدام Aspose.Words. تعلم تحويل معادلات Word
  إلى LaTeX، حفظ المستند كنص عادي، وتصدير المعادلات إلى ملف txt.
draft: false
keywords:
- how to export latex
- convert word equations latex
- save document plain text
- save equations txt file
language: ar
og_description: كيفية تصدير LaTeX من Word باستخدام Aspose.Words. يوضح لك هذا الدليل
  كيفية تحويل معادلات Word إلى LaTeX، حفظ المستند كنص عادي، وإنشاء ملف txt للمعادلات.
og_title: كيفية تصدير LaTeX من Word – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: How to export LaTeX from Word using Aspose.Words. Learn to convert
    Word equations LaTeX, save document plain text, and export equations txt file.
  headline: How to Export LaTeX from Word – Complete Programming Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- LaTeX
title: كيفية تصدير LaTeX من Word – دليل البرمجة الكامل
url: /ar/net/programming-with-officemath/how-to-export-latex-from-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تصدير LaTeX من Word – دليل برمجة شامل

هل تساءلت يومًا **كيف تصدر LaTeX** من ملف Microsoft Word دون نسخ كل معادلة يدويًا؟ لست وحدك. في العديد من خطوط الأنابيب العلمية أو الأكاديمية تحتاج إلى المعادلات بصيغة LaTeX، وتخزين المستند بالكامل كنص عادي، وربما وضع النتيجة في ملف `.txt` للمعالجة لاحقًا.  

في هذا الدرس سنستعرض **حلًا كاملاً وقابلًا للتنفيذ** يوضح لك كيفية **تحويل معادلات Word إلى LaTeX**، ثم **حفظ المستند كنص عادي** وأخيرًا **حفظ المعادلات في ملف txt** باستخدام Aspose.Words for .NET. في النهاية ستحصل على تطبيق وحدة تحكم C# واحد يقوم بالمهمة في ثلاث خطوات واضحة—بدون الحاجة لتعديل يدوي.

## المتطلبات المسبقة — ما ستحتاجه قبل البدء

| المتطلب | لماذا هو مهم |
|-------------|----------------|
| .NET 6.0 SDK (أو أحدث) | يوفّر بيئة تشغيل كود C#. |
| Visual Studio 2022 (أو VS Code) | يجعل التحرير وتصحيح الأخطاء أسهل. |
| Aspose.Words for .NET (حزمة NuGet `Aspose.Words`) | المكتبة التي تفهم OfficeMath ويمكنها تصديرها كـ LaTeX. |
| مستند Word (`.docx`) يحتوي على معادلات | المصدر الذي سنقوم بتحويله. |

إذا لم تقم بتثبيت Aspose.Words بعد، نفّذ:

```bash
dotnet add package Aspose.Words
```

هذا السطر الواحد يجلب لك كل ما تحتاجه، بما في ذلك تعداد `OfficeMathExportMode` الذي سنستخدمه لاحقًا.

## الخطوة 1: تحميل مستند Word وتحضير خيارات الحفظ

أول ما نقوم به هو تحميل ملف `.docx` إلى كائن `Aspose.Words.Document`. ثم نضبط `TxtSaveOptions` بحيث يتم تصدير أي **OfficeMath** (الاسم الداخلي لمعادلات Word) كـ LaTeX.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source Word file that contains equations.
        Document doc = new Document(@"YOUR_DIRECTORY/SourceWithEquations.docx");

        // Configure text save options to export OfficeMath as LaTeX.
        TxtSaveOptions txtOpts = new TxtSaveOptions
        {
            // This flag tells Aspose.Words to turn each equation into its LaTeX representation.
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
```

**لماذا هذا مهم:** بشكل افتراضي، تقوم Aspose.Words بكتابة المعادلة كحروف Unicode عادية، مما ينتج عنه نص غير مفهوم في بيئات النص العادي. ضبط `OfficeMathExportMode` إلى `LaTeX` يمنحك سلاسل LaTeX نظيفة جاهزة للنسخ واللصق.

## الخطوة 2: حفظ المستند كنص عادي

بعد أن أصبحت الخيارات جاهزة، نستدعي ببساطة `Document.Save`. الطريقة تحترم `TxtSaveOptions` التي مررناها، لذا يحتوي الملف الناتج على كل من النص العادي والمعادلات بصيغة LaTeX.

```csharp
        // Save the document as a plain‑text file with the specified options.
        doc.Save(@"YOUR_DIRECTORY/Equations.txt", txtOpts);

        Console.WriteLine("✅ Document saved as plain text with LaTeX equations.");
    }
}
```

**ما ستحصل عليه:** ملف اسمه `Equations.txt` يبدو شيئًا مثل هذا:

```
Here is a simple paragraph.

\[
E = mc^2
\]

Another paragraph with an inline equation \(a^2 + b^2 = c^2\).

```

لاحظ محددات LaTeX (`\[` … `\]` للمعادلات العرضية، `\(` … `\)` للمعادلات داخل السطر). هذا هو بالضبط ما أنتجه خطوة **convert word equations latex**.

## الخطوة 3: (اختياري) استخراج المعادلات فقط إلى ملف .txt منفصل

أحيانًا يهمك فقط المعادلات نفسها. يمكنك معالجة النص المولد لاحقًا، أو يمكنك السماح لـ Aspose.Words بإعطائك سلاسل LaTeX الخام مباشرة عبر واجهة `NodeCollection`. إليك طريقة سريعة لكتابة **المعادلات فقط** في ملف ثانٍ:

```csharp
        // Collect all LaTeX equations from the document.
        var latexEquations = new System.Text.StringBuilder();

        foreach (Node node in doc.GetChildNodes(NodeType.OfficeMath, true))
        {
            // Convert each OfficeMath node to LaTeX.
            string latex = node.ToString(SaveFormat.LaTeX);
            latexEquations.AppendLine(latex);
        }

        // Save the equations to a dedicated txt file.
        System.IO.File.WriteAllText(@"YOUR_DIRECTORY/OnlyEquations.txt", latexEquations.ToString());

        Console.WriteLine("✅ Extracted equations saved to OnlyEquations.txt");
```

**لماذا قد تقوم بذلك:** إذا كنت تُغذّي المعادلات إلى مترجم LaTeX منفصل، أو مولد موقع ثابت، أو خط أنابيب تعلم آلي، فإن قائمة نظيفة من سلاسل LaTeX تكون غالبًا أكثر ملاءمة من مستند مختلط.

## المشكلات الشائعة & نصائح احترافية

| المشكلة | كيفية تجنّبها |
|---------|-----------------|
| **حزمة NuGet مفقودة** – ستحصل على استثناء `FileNotFoundException` وقت التشغيل. | نفّذ `dotnet add package Aspose.Words` قبل البناء. |
| **مسار ملف غير صحيح** – يرمى التطبيق استثناء `FileNotFoundException`. | استخدم مسارات مطلقة أو `Path.Combine(Environment.CurrentDirectory, "file.docx")`. |
| **المعادلات تظهر كـ Unicode** – نسيت ضبط `OfficeMathExportMode`. | راجع كتلة `TxtSaveOptions`؛ الخاصية يجب أن تكون `LaTeX`. |
| **المستندات الكبيرة تستهلك الذاكرة** – تحميل كل المحتوى مرة واحدة قد يكون ثقيلًا. | استخدم `LoadOptions` مع `LoadFormat.Docx` وفكّر في التدفق إذا وصلت للحدود. |

## التحقق من النتيجة

بعد تشغيل البرنامج، افتح `Equations.txt` في أي محرر نصوص. يجب أن ترى فقرات عادية متداخلة مع مقتطفات LaTeX محاطة بـ `\[` … `\]` أو `\(` … `\)`. إذا فتحت `OnlyEquations.txt`، ستحصل على قائمة نظيفة:

```
\[
E = mc^2
\]
\[
a^2 + b^2 = c^2
\]
```

إذا كان شكل LaTeX غير صحيح، تأكد أن ملف Word الأصلي يستخدم محرر **Equation** المدمج (OfficeMath) وليس صورًا مُدرَجة. لا يمكن لـ Aspose.Words ترجمة سوى كائنات OfficeMath الحقيقية.

## الشيفرة الكاملة (جاهزة للنسخ‑اللصق)

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Saving;

class ExportLatexDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains equations.
        Document doc = new Document(@"YOUR_DIRECTORY/SourceWithEquations.docx");

        // 2️⃣ Configure TxtSaveOptions so OfficeMath becomes LaTeX.
        TxtSaveOptions txtOpts = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 3️⃣ Save the whole document as plain text (includes LaTeX equations).
        doc.Save(@"YOUR_DIRECTORY/Equations.txt", txtOpts);
        Console.WriteLine("✅ Document saved as plain text with LaTeX equations.");

        // 4️⃣ (Optional) Extract only the LaTeX equations.
        StringBuilder latexEquations = new StringBuilder();

        foreach (Node node in doc.GetChildNodes(NodeType.OfficeMath, true))
        {
            string latex = node.ToString(SaveFormat.LaTeX);
            latexEquations.AppendLine(latex);
        }

        System.IO.File.WriteAllText(@"YOUR_DIRECTORY/OnlyEquations.txt", latexEquations.ToString());
        Console.WriteLine("✅ Extracted equations saved to OnlyEquations.txt");
    }
}
```

قم بالترجمة والتشغيل باستخدام:

```bash
dotnet run
```

يجب أن ترى رسالتين ✅ تؤكدان نجاح عملية التصدير.

## الخلاصة

لقد أظهرنا للتو **كيفية تصدير LaTeX** من مستند Word، **تحويل معادلات Word إلى LaTeX**، **حفظ المستند كنص عادي**، وحتى **حفظ المعادلات في ملف txt** للمعالجة اللاحقة. الفكرة الأساسية هي أن Aspose.Words يجعل كامل الخط الأنابيب سهلًا—فقط اضبط `OfficeMathExportMode` إلى `LaTeX` ودع المكتبة تتولى الجزء الثقيل.

ما الخطوة التالية؟ جرّب إمداد ملفات `.txt` المولدة إلى مولد موقع ثابت يبني مدونة مبنية على Markdown، أو مرّر سلاسل LaTeX إلى مترجم PDF مثل `pdflatex` لتوليد تقارير دفعة واحدة. يمكنك أيضًا تجربة إعدادات أخرى في `TxtSaveOptions` (مثل `Encoding` أو `PreserveTableLayout`) لضبط مخرجات النص العادي بدقة.

هل لديك أسئلة حول حالات خاصة، مثل التعامل مع معادلات متداخلة أو ماكرو مخصص؟ اترك تعليقًا أدناه، وتمنياتنا لك ببرمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة‑بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [How to Export LaTeX from Word: Convert DOCX to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/how-to-export-latex-from-word-convert-docx-to-markdown-with/)
- [Save Document as Txt – Export Word Math to LaTeX in C#](/words/english/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/)
- [How to Export LaTeX from Word – Step‑by‑Step Guide](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}