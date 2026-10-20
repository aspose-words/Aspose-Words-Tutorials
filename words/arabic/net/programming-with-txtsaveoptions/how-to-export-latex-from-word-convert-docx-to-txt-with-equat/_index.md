---
category: general
date: 2026-03-21
description: تعلم كيفية تصدير LaTeX من ملف Word DOCX عن طريق تحويله إلى TXT مع الحفاظ
  على المعادلات. دليل خطوة بخطوة بلغة C# لتصدير المعادلات من Word.
draft: false
keywords:
- how to export latex
- convert docx to txt
- export equations from word
- save docx as txt
- convert word equations latex
language: ar
og_description: كيف تصدر LaTeX من Word؟ يوضح لك هذا الدرس كيفية تحويل ملف DOCX إلى
  TXT مع الحفاظ على المعادلات بصيغة LaTeX، باستخدام C#.
og_title: كيفية تصدير LaTeX من Word – دليل سريع لتحويل DOCX إلى TXT
tags:
- C#
- Aspose.Words
- LaTeX
- DOCX
- Text Export
title: كيفية تصدير LaTeX من Word – تحويل DOCX إلى TXT مع المعادلات
url: /ar/net/programming-with-txtsaveoptions/how-to-export-latex-from-word-convert-docx-to-txt-with-equat/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تصدير LaTeX من Word – تحويل DOCX إلى TXT مع المعادلات

هل تساءلت يومًا **كيف تصدر LaTeX** من مستند Word دون نسخ كل صيغة يدويًا؟ لست وحدك. يواجه معظم المطورين عائقًا عندما يحتاجون إلى استخراج المعادلات من *.docx* وإدخالها في خط أنابيب يدعم LaTeX.  

الأخبار السارة؟ ببضع أسطر من C# وإعدادات الحفظ الصحيحة، يمكنك **تحويل docx إلى txt** والحصول على كل معادلة Office Math مُصدرة كـ LaTeX نظيف. في هذا الدليل سنستعرض الخطوات الدقيقة، نشرح لماذا كل إعداد مهم، ونظهر لك النتيجة النهائية التي يمكنك التحقق منها في ثوانٍ.

## ما يغطيه هذا الدرس

سنبدأ بتحديد المتطلبات المسبقة (كل ما تحتاجه هو مكتبة Aspose.Words for .NET). ثم نتعمق في عملية من ثلاث خطوات:

1. تحميل ملف *.docx* المصدر.  
2. ضبط `TxtSaveOptions` بحيث يتم تصدير Office Math كـ LaTeX.  
3. حفظ المستند كملف نصي عادي.

بنهاية الدرس، ستعرف **كيف تصدر latex**، وستكون مرتاحًا مع **تصدير المعادلات من word**، وستحصل على مقتطف يمكن إعادة استخدامه في أي مشروع C#.  

*لماذا يهم؟* إذا كنت تُنشئ تقارير علمية، أو واجبات منزلية، أو أي محتوى يُجمع لاحقًا باستخدام LaTeX، فإن أتمتة هذا التصدير توفر ساعات من النسخ واللصق وتُزيل أخطاء التنسيق.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل مع .NET Core و .NET Framework أيضًا).  
- Aspose.Words for .NET (نسخة تجريبية مجانية أو مرخصة). التثبيت عبر NuGet:

```bash
dotnet add package Aspose.Words
```

- مستند Word (`input.docx`) يحتوي على معادلة Office Math واحدة على الأقل.

> **نصيحة احترافية:** إذا لم يكن لديك ملف DOCX جاهز، أنشئ ملف Word جديد، أدخل معادلة عبر *Insert → Equation*، واحفظه باسم `input.docx`.

## الخطوة 1: تحميل المستند المصدر الذي تريد تصديره

أولًا نحتاج إلى كائن `Document` يشير إلى الملف الذي نعتزم تحويله. فئة `Document` تمثل ملف Word بالكامل، وتمنحنا الوصول إلى الفقرات والجداول—والأهم—كائنات Office Math.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Step 1: Load the source DOCX file
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **لماذا هذا مهم:** تحميل الملف يُنشئ تمثيلًا في الذاكرة يمكن لمحرك الحفظ استعراضه. بدون هذا الكائن، لا شيء لتصديره، وستكون الإعدادات اللاحقة بلا تأثير.

## الخطوة 2: ضبط خيارات حفظ النص لتصدير Office Math كـ LaTeX

السحر يكمن في `TxtSaveOptions`. بشكل افتراضي، حفظ النص العادي يزيل كل ما ليس نصًا، بما في ذلك المعادلات. ضبط `OfficeMathExportMode` إلى `LaTeX` يخبر Aspose بترجمة كل عقدة Office Math إلى ما يعادلها في LaTeX.

```csharp
// Step 2: Set up save options for LaTeX export
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    // This flag ensures every equation becomes LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

> **ما الذي يحدث خلف الكواليس؟** يقوم Aspose بتحليل XML الخاص بـ Office Math، ويربط المشغلات بأوامر LaTeX، ثم يكتب النتيجة في تدفق النص. تعداد `OfficeMathExportMode` يقدم أيضًا `Unicode` و `MathML`—اختر ما يناسب سلسلة أدواتك اللاحقة.

## الخطوة 3: حفظ المستند كملف نصي عادي باستخدام الخيارات المكوَّنة

الآن نكتب المحتوى المُحوَّل إلى القرص. امتداد الملف `.txt` يشير إلى تنسيق نص عادي، لكن بفضل الخيارات التي ضبطناها، سيحتوي الملف على مزيج من النص العادي ومقاطع LaTeX حيثما وجدت المعادلات.

```csharp
// Step 3: Export the document to a TXT file with LaTeX equations
doc.Save(@"YOUR_DIRECTORY\Equations.txt", txtSaveOptions);
```

### النتيجة المتوقعة

افتح `Equations.txt` في أي محرر. يجب أن ترى شيئًا مشابهًا لـ:

```
This is a sample paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
\]
```

إذا ظهر LaTeX تمامًا كما هو أعلاه، فقد نجحت في **حفظ docx كـ txt** مع الحفاظ على الرياضيات.

## الاختلافات الشائعة وحالات الحافة

### تحويل ملفات متعددة دفعة واحدة

إذا كنت بحاجة لمعالجة مجلد من ملفات DOCX، غلف الخطوات الثلاث داخل حلقة `foreach`:

```csharp
string[] files = Directory.GetFiles(@"YOUR_DIRECTORY", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtSaveOptions);
}
```

### التعامل مع محتوى غير المعادلات

تتيح لك `TxtSaveOptions` أيضًا التحكم في فواصل الأسطر، الترميز، وما إذا كنت تريد الحفاظ على النص المخفي. على سبيل المثال، لفرض UTF‑8:

```csharp
txtSaveOptions.Encoding = Encoding.UTF8;
```

### التصدير إلى صيغ نصية أخرى

إذا كنت تفضل Markdown بدلاً من TXT الخام، ما عليك سوى تغيير الامتداد وتعديل الخيارات حسب الحاجة:

```csharp
doc.Save(@"YOUR_DIRECTORY\Equations.md", txtSaveOptions);
```

تبقى كتل LaTeX سليمة، ويمكن لمعالجات Markdown مثل Pandoc أن تُظهرها لاحقًا.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه في تطبيق Console. يتضمن جميع تعليمات `using` اللازمة، ومعالجة الأخطاء، وتعليقات توضح كل سطر.

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexExport
{
    class Program
    {
        static void Main(string[] args)
        {
            // Adjust these paths to match your environment
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\Equations.txt";

            try
            {
                // 1️⃣ Load the Word document
                Document doc = new Document(inputPath);

                // 2️⃣ Prepare save options – this is where we tell Aspose to export equations as LaTeX
                TxtSaveOptions saveOptions = new TxtSaveOptions
                {
                    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                    Encoding = Encoding.UTF8          // Ensure Unicode characters survive
                };

                // 3️⃣ Perform the export
                doc.Save(outputPath, saveOptions);

                Console.WriteLine($"✅ Success! LaTeX‑rich text file created at: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Oops – something went wrong: {ex.Message}");
            }
        }
    }
}
```

شغّل البرنامج، افتح `Equations.txt` الناتج، وسترى كل معادلة مُصدرة كـ LaTeX—جاهزة لتُغذى إلى مترجم LaTeX أو سير عمل نشر علمي.

## الأسئلة المتكررة

**هل يعمل هذا مع إصدارات أقدم من Aspose.Words؟**  
نعم. خاصية `OfficeMathExportMode` موجودة منذ الإصدار 19.8. إذا كنت تستخدم نسخة أقدم، قم بالترقية إلى ذلك الإصدار على الأقل.

**ماذا لو كان ملف DOCX يحتوي على صور؟**  
تصدير النص العادي يتخلص من الصور بطبيعة الحال. إذا كنت بحاجة إلى كل من الصور وLaTeX، فكر في التصدير إلى HTML (`HtmlSaveOptions`) ثم معالجة HTML لاستخراج كتل LaTeX.

**هل يمكنني التصدير مباشرة إلى ملف `.tex`؟**  
لا توفر Aspose كاتبًا أصليًا لملف `.tex`، لكن يمكنك إعادة تسمية ملف `.txt` إلى `.tex` بعد التصدير—كود LaTeX يبقى هو نفسه. فقط تأكد من إضافة بنية المستند المحيطة (المقدمة، `\begin{document}`) يدويًا.

## الخلاصة

أنت الآن تعرف **كيف تصدر latex** من ملف Word عبر **تحويل docx إلى txt** مع الحفاظ على كل معادلة. المقتطف الثلاثي الخطوات في C#—التحميل، الضبط، الحفظ—يغطي جوهر **تصدير المعادلات من word**، ويمكن تعديل النمط نفسه للمعالجة الدفعة أو صيغ إخراج بديلة.  

هل أنت مستعد للتحدي التالي؟ جرّب **حفظ docx كـ txt** للمستندات متعددة اللغات، أو استكشف تحويل كتل LaTeX إلى ملفات PDF باستخدام أداة مثل `pdflatex`. السماء هي الحد عندما تجمع Aspose.Words مع سير عمل LaTeX قوي.

---

![مخطط يوضح التدفق: DOCX → Aspose.Words → TXT مع معادلات LaTeX](https://example.com/flow-diagram.png "مخطط تدفق كيفية تصدير latex")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}