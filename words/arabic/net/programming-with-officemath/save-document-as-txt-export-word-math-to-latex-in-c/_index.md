---
category: general
date: 2026-04-24
description: احفظ المستند بصيغة txt وحوّل Word إلى LaTeX باستخدام Aspose.Words. تعلّم
  كيفية تصدير معادلات الرياضيات في Word إلى LaTeX بسرعة.
draft: false
keywords:
- save document as txt
- convert word to latex
- convert word equations to latex
- export word math latex
language: ar
og_description: احفظ المستند كملف txt وحوّل معادلات Word إلى LaTeX باستخدام C#. دليل
  كامل خطوة بخطوة مع الشيفرة.
og_title: حفظ المستند كملف TXT – تصدير معادلات Word إلى LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: حفظ المستند كملف TXT – تصدير معادلات Word إلى LaTeX باستخدام C#
url: /ar/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ المستند كملف TXT – تصدير معادلات Word إلى LaTeX في C#

هل احتجت يوماً إلى **حفظ المستند كملف txt** مع الحفاظ على معادلاتك المتقنة؟ لست وحدك. ميزة Word المدمجة “Save as plain text” تتخلص من Office Math، لتتركك مع نص غير قابل للقراءة. ماذا لو كان بإمكانك الاحتفاظ بهذه المعادلات، ولكن بصيغة LaTeX نظيفة؟

في هذا الدرس سنستعرض الخطوات الدقيقة **convert Word to LaTeX**‑ready text باستخدام Aspose.Words for .NET. في النهاية ستحصل على ملف `.txt` حيث تُمثَّل كل معادلة بصيغة LaTeX صحيحة، جاهزة للإدراج في ورقة أو ملف markdown. لا محولات خارجية، لا نسخ‑لصق يدوي—فقط بضع أسطر من C#.

## ما ستتعلمه

- كيفية تحميل ملف `.docx` باستخدام Aspose.Words.
- تهيئة `TxtSaveOptions` بحيث يتم تصدير Office Math كـ LaTeX.
- حفظ النتيجة في ملف نصي عادي يمكنك فتحه في أي محرر.
- معالجة الحالات الخاصة للمعادلات داخل السطر مقابل المعادلات المعروضة، ونصيحة سريعة لمعالجة دفعة من المستندات المتعددة.

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل مع .NET Framework 4.6+ أيضاً).
- حزمة NuGet الخاصة بـ Aspose.Words for .NET (`Install-Package Aspose.Words`).
- مستند Word يحتوي على معادلة واحدة على الأقل (كائن Office Math).

---

## الخطوة 1: تثبيت Aspose.Words وإعداد المشروع

أولاً، أضف المكتبة إلى مشروعك. افتح الطرفية في مجلد الحل الخاص بك وشغّل:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** إذا كنت تستخدم Visual Studio، فإن واجهة مدير الحزم NuGet تعمل بنفس الفعالية—ابحث عن “Aspose.Words” وانقر Install.

الآن أنشئ تطبيق console جديد (أو ضع الكود في تطبيق موجود). توجيهات `using` التي ستحتاجها هي:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 2: تحميل المستند المصدر

نحتاج إلى توجيه Aspose.Words إلى ملف Word الذي يحتوي على المعادلات. استبدل `YOUR_DIRECTORY/input.docx` بالمسار الفعلي على جهازك.

```csharp
// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");
```

> **Why this matters:** تحميل المستند يمنح Aspose.Words وصولاً كاملاً إلى كائنات Office Math الداخلية، والتي تكون غير مرئية لمصدّر النص البسيط.

## الخطوة 3: تهيئة TxtSaveOptions لتصدير LaTeX

السحر يحدث داخل كائن `TxtSaveOptions`. بتعيين `OfficeMathExportMode` إلى `LaTeX`، تتحول كل معادلة إلى ما يعادلها في LaTeX.

```csharp
// Configure save options to export Office Math as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Export all Office Math objects as LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: keep line breaks similar to the original layout
    PreserveTableLayout = true
};
```

> **What if you need MathML instead?** غيّر `OfficeMathExportMode` إلى `MathML`. نفس الـ API يدعم عدة صيغ إخراج.

## الخطوة 4: حفظ المستند كنص عادي

الآن نكتب الملف. الملف الناتج `Math.txt` سيحتوي على نص عادي بالإضافة إلى قطع LaTeX لكل معادلة.

```csharp
// Save the document as a .txt file with LaTeX equations
doc.Save(@"C:\MyDocs\Math.txt", txtOptions);
Console.WriteLine("Document saved as txt with LaTeX equations.");
```

تشغيل البرنامج ينتج ملفًا يشبه ما يلي:

```
This is a simple paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \, dx = 1
\]
```

لاحظ كيف تستخدم المعادلة داخل السطر `$…$` بينما تُحاط المعادلة المعروضة بـ `\[` و `\]`. هذا هو الاتفاق القياسي في LaTeX، وتقوم Aspose.Words بذلك تلقائيًا.

## الخطوة 5: التحقق من النتيجة (اختياري)

إذا أردت التأكد من صحة LaTeX، يمكنك تمرير `.txt` إلى مترجم LaTeX مثل `pdflatex` أو إلى عارض إلكتروني مثل Overleaf. يجب أن يُترجم النص دون أخطاء، وتظهر المعادلات كما كانت في Word.

```bash
pdflatex Math.txt
```

إذا ظهرت رسالة “Undefined control sequence”، تأكد من تضمين حزم LaTeX التي تحتاجها (مثل `amsmath`) في المقدمة عندما تدمج النص في مستند LaTeX أكبر.

## معالجة الاختلافات الشائعة

### تحويل ملفات متعددة في مجلد

```csharp
string[] files = Directory.GetFiles(@"C:\MyDocs\", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtOptions);
}
Console.WriteLine("Batch conversion complete.");
```

### التعامل مع المعادلات داخل السطر مقابل المعادلات المعروضة

تكتشف Aspose.Words نوع المعادلة تلقائيًا بناءً على تخطيطها في Word. إذا احتجت إلى فرض نمط معين، يمكنك معالجة الناتج بعد ذلك:

```csharp
string txt = File.ReadAllText(@"C:\MyDocs\Math.txt");
txt = txt.Replace("$", "\\(").Replace("$", "\\)"); // forces inline math delimiters
File.WriteAllText(@"C:\MyDocs\Math_fixed.txt", txt);
```

### التصدير إلى صيغ أخرى

إذا لم يكن LaTeX هو هدفك، ما عليك سوى تغيير وضع التصدير:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML; // for MathML
```

أو استخدم `HtmlSaveOptions` إذا كنت تفضّل تضمين MathML داخل HTML.

---

## مثال كامل يعمل

فيما يلي البرنامج الكامل الجاهز للتنفيذ. انسخه إلى `Program.cs` في مشروع console .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexTxt
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"C:\MyDocs\input.docx");

            // 2️⃣ Set up save options to export Office Math as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                PreserveTableLayout = true
            };

            // 3️⃣ Save as plain‑text with LaTeX equations
            string outputPath = @"C:\MyDocs\Math.txt";
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"✅ Saved document as txt at: {outputPath}");
            Console.WriteLine("Open the file to see LaTeX‑formatted equations.");
        }
    }
}
```

شغّل البرنامج (`dotnet run`)، افتح `Math.txt`، وسترى محتوى Word مع معادلات LaTeX محفوظة.

---

## الأسئلة المتكررة

**س: هل يعمل هذا مع ملفات .doc القديمة؟**  
ج: نعم—يمكن لـ Aspose.Words فتح ملفات `.doc` القديمة، لكن المعادلات المعقدة قد تُخزن كصور. في هذه الحالة يعود المُصدّر إلى تعليق نائب.

**س: ماذا لو احتوت المعادلة على رموز مخصصة؟**  
ج: يقوم Aspose.Words بتحويل معظم رموز Office Math إلى أوامر LaTeX القياسية. بالنسبة للرموز المخصصة تمامًا قد تحتاج إلى تعديل LaTeX المُولد يدويًا.

**س: هل الإخراج مشفر بـ UTF‑8؟**  
ج: بشكل افتراضي، يكتب `TxtSaveOptions` بصيغة UTF‑8، وهو آمن لمعظم اللغات والرموز.

## الخلاصة

أنت الآن تعرف كيف **save document as txt** مع الحفاظ على كل معادلة بصيغة LaTeX نظيفة. يتيح لك هذا النهج **convert Word to LaTeX** دون أدوات طرف ثالث، ويعمل على نطاق من ملف واحد إلى مجلدات كاملة. بعد ذلك، قد تستكشف **convert word equations to LaTeX** للمعالجة الدفعة، أو تغوص في **export word math latex** للأنابيب HTML أو Markdown.

لا تتردد في التجربة—بدّل `OfficeMathExportMode` إلى MathML، عدّل معالجة فواصل الأسطر، أو دمج هذا المقتطف في سير عمل توليد مستندات أكبر. Happy coding, and may your equations always render perfectly!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}