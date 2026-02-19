---
category: general
date: 2026-02-18
description: كيفية تصدير LaTeX من ملف DOCX باستخدام Aspose.Words C#. يوضح هذا الدليل
  كيفية تحويل DOCX إلى TXT، حفظ المستند كملف TXT، وتصدير LaTeX بسرعة.
draft: false
keywords:
- how to export latex
- convert docx to txt
- save document as txt
- how to save txt
- save word as txt
language: ar
og_description: كيفية تصدير LaTeX من ملف DOCX باستخدام C#. تعلم تحويل DOCX إلى TXT،
  حفظ المستند كملف TXT، والحصول على مخرجات LaTeX باستخدام Aspose.Words.
og_title: كيفية تصدير LaTeX من DOCX – دليل C#
tags:
- Aspose.Words
- C#
- LaTeX export
title: كيفية تصدير LaTeX من DOCX – تحويل DOCX إلى TXT باستخدام C#
url: /ar/net/programming-with-txtsaveoptions/how-to-export-latex-from-docx-convert-docx-to-txt-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تصدير LaTeX من DOCX – تحويل DOCX إلى TXT في C#

هل تساءلت يومًا **كيف تصدر LaTeX** من مستند Word دون نسخ كل معادلة يدويًا؟ لست وحدك. في العديد من المشاريع العلمية، يحتوي ملف .docx الأصلي على عشرات معادلات Office Math التي تحتاج إلى تحويلها إلى LaTeX للأوراق البحثية أو العروض التقديمية أو المواقع الثابتة. الخبر السار؟ باستخدام Aspose.Words for .NET يمكنك **تحويل docx إلى txt** وجعل كل معادلة تتحول تلقائيًا إلى ترميز LaTeX.

في هذا الدرس سنستعرض الخطوات الدقيقة **لحفظ المستند كملف txt**، وتكوين المُصدِّر لإخراج LaTeX، والحصول على ملف `.txt` نظيف يمكنك إرساله مباشرة إلى خط أنابيب LaTeX الخاص بك. لا أدوات خارجية، لا معالجة يدوية معقدة—فقط بضع أسطر من C#.

> **ما ستحصل عليه:** برنامج كامل قابل للتنفيذ يقوم بتحميل `input.docx`، ويصدّر جميع المعادلات كـ LaTeX، ويكتبها في `Math.txt`. بنهاية الدرس ستعرف أيضًا كيفية تعديل الخيارات لسيناريوهات مختلفة، مثل الحفاظ على فواصل الأسطر أو معالجة الملفات الكبيرة.

## المتطلبات المسبقة

- **Aspose.Words for .NET** (الإصدار 23.10 أو أحدث). يمكنك الحصول عليه من NuGet: `Install-Package Aspose.Words`.
- بيئة تشغيل .NET 6+ (الكود يعمل على .NET Core، .NET Framework، و .NET 5/6).
- مستند Word (`input.docx`) يحتوي على كائنات Office Math.
- إلمام أساسي بـ C# و Visual Studio أو أي بيئة تطوير تفضّلها.

إذا كان لديك كل ذلك، رائع—هيا نبدأ.

## الخطوة 1: تحميل المستند المصدر

أول شيء نحتاجه هو كائن `Document` يمثل ملف .docx الموجود على القرص.

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document(@"C:\MyProjects\ExportLatexDemo\input.docx");
```

**لماذا هذا مهم:** Aspose.Words يُجسّد بنية ملف Word بالكامل (فقرات، جداول، معادلات) في كائن واحد. بتحميله مرة واحدة نتجنب عمليات I/O المتكررة ونعطي المكتبة فرصة لتحليل كائنات Office Math بشكل صحيح.

> **نصيحة احترافية:** استخدم مسارًا مطلقًا أثناء التطوير لتجنب مفاجآت “الملف غير موجود”، ثم انتقل إلى مسار نسبي أو إعداد تكوين للإنتاج.

## الخطوة 2: تكوين خيارات حفظ TXT لتصدير LaTeX

بشكل افتراضي، حفظ المستند كنص عادي يزيل كل ما ليس أحرفًا بسيطة. نحتاج أن نخبر الحافظ **بحفظ المستند كـ txt** مع تحويل المعادلات إلى LaTeX.

```csharp
// Step 2: Create TXT save options and set Office Math export mode to LaTeX
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    // This flag makes every OfficeMath object become LaTeX code.
    OfficeMathExportMode = TxtSaveOptions.OfficeMathExportMode.LaTeX,

    // Optional: keep line breaks as they appear in Word.
    PreserveLineBreaks = true
};
```

**لماذا هذا مهم:** `OfficeMathExportMode` يتحكم في طريقة عرض المعادلات. القيمة `LaTeX` تخبر Aspose.Words بترجمة كل عقدة `OfficeMath` إلى صيغ LaTeX المقابلة (`\frac{a}{b}`, `\int`، إلخ). بدون ذلك ستحصل على عنصر نائب بسيط مثل `[Equation]`.

## الخطوة 3: حفظ المستند كملف نصي عادي

الآن نكتب ملف الإخراج. طريقة `Save` تحترم الخيارات التي ضبطناها للتو.

```csharp
// Step 3: Save the document as a plain‑text file using the configured options
doc.Save(@"C:\MyProjects\ExportLatexDemo\Math.txt", txtSaveOptions);
```

عند انتهاء البرنامج، افتح `Math.txt` وسترى شيئًا مثل:

```
Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \,dx = 1
\]
```

هذا هو **كيفية حفظ txt** التي كنت تبحث عنها—كل كتلة Office Math أصبحت الآن LaTeX صحيحًا.

## مثال كامل يعمل

فيما يلي البرنامج الكامل، جاهز للنسخ واللصق في تطبيق Console.

```csharp
using System;
using Aspose.Words;

namespace ExportLatexDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Verify input arguments
            if (args.Length < 2)
            {
                Console.WriteLine("Usage: ExportLatexDemo <input.docx> <output.txt>");
                return;
            }

            string inputPath = args[0];
            string outputPath = args[1];

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Configure save options for LaTeX export
            TxtSaveOptions options = new TxtSaveOptions
            {
                OfficeMathExportMode = TxtSaveOptions.OfficeMathExportMode.LaTeX,
                PreserveLineBreaks = true,
                // Optional: set encoding if you need UTF‑8 (default is UTF‑8)
                Encoding = System.Text.Encoding.UTF8
            };

            // 3️⃣ Save as plain‑text (this is where we **convert docx to txt**)
            doc.Save(outputPath, options);

            Console.WriteLine($"✅ Successfully exported LaTeX to \"{outputPath}\"");
        }
    }
}
```

### كيفية تشغيله

```bash
dotnet run --project ExportLatexDemo.csproj "C:\Docs\input.docx" "C:\Docs\Math.txt"
```

ستظهر رسالة في وحدة التحكم تؤكد عملية التصدير، ويمكنك فتح `Math.txt` بأي محرر نصوص.

## الحالات الخاصة والأسئلة الشائعة

### 1. ماذا لو كان المستند يحتوي على صور إلى جانب المعادلات؟

فئة `TxtSaveOptions` تتعامل فقط مع المحتوى النصي. تُهمل الصور لأن النص العادي لا يمكنه تمثيلها. إذا كنت بحاجة إلى مخرجات مختلطة (مثل Markdown مع صور base64 مدمجة)، عليك استخدام `SaveFormat.Markdown` ومعالجة تحويل الصور بشكل منفصل.

### 2. معادلاتي تحتوي على رموز مخصصة لا تُظهر في LaTeX. لماذا؟

Aspose.Words يطابق معظم رموز Office Math مع ما يعادلها في LaTeX، لكن بعض الرموز Unicode النادرة تُستبدل بالحرف الحرفي. في هذه الحالات النادرة يمكنك معالجة النتيجة لاحقًا باستبدال بسيط، مثلًا:

```csharp
string txt = File.ReadAllText(outputPath);
txt = txt.Replace("ℵ", @"\aleph");
File.WriteAllText(outputPath, txt);
```

### 3. المستندات الكبيرة (مئات الـ MB) تتسبب في حدوث OutOfMemoryException. أي نصائح؟

- استخدم `LoadOptions` مع `LoadFormat.Docx` واضبط `MemoryOptimization` إلى `MemoryOptimization.MemorySaving`.
- عالج المستند على دفعات: قسّمه إلى أقسام، صدّر كل قسم، ثم اجمع النتائج.

```csharp
LoadOptions loadOptions = new LoadOptions { MemoryOptimization = MemoryOptimization.MemorySaving };
Document largeDoc = new Document(inputPath, loadOptions);
```

### 4. هل يمكنني تصدير LaTeX بدون delimiters `$` المحيطة؟

نعم. اضبط `OfficeMathExportMode` إلى `TxtSaveOptions.OfficeMathExportMode.LaTeX` (كما هو موضح) ثم احذف delimiters يدويًا إذا رغبت في الحصول على أوامر صافية. تعبير regex بسيط يقوم بالمهمة:

```csharp
txt = Regex.Replace(txt, @"\$(.*?)\$", "$1"); // removes inline $…$
```

## نصائح عملية (E‑E‑A‑T)

- **الإصدار مهم:** تم تقديم مُصدّر LaTeX في Aspose.Words 22.5. إذا كنت تستخدم إصدارًا أقدم، خاصية `OfficeMathExportMode` لن تكون موجودة.
- **الاختبار:** دائمًا تحقق من صحة LaTeX المُولد باستخدام مُجمع (`pdflatex`, `xelatex`) قبل إدخاله في خط أنابيب أكبر.
- **الأداء:** عندما تحتاج فقط إلى المعادلات، فكر في استخدام `Document.GetChildNodes(NodeType.OfficeMath, true)` لاستخراجها مباشرةً، متجاوزًا تحويل النص الكامل.

## الخلاصة

أنت الآن تعرف **كيفية تصدير LaTeX** من ملف DOCX باستخدام C#. من خلال تكوين `TxtSaveOptions` يمكنك **تحويل docx إلى txt**، **حفظ المستند كـ txt**، والحصول على ترميز LaTeX نظيف لكل معادلة. الكود الكامل أعلاه يتعامل مع تحليل الوسائط، الترميز، وبعض الحيل المفيدة للحالات الخاصة، بحيث يمكنك دمجه في أي سكريبت أتمتة.

هل أنت مستعد للخطوة التالية؟ جرّب ربط هذا المُصدّر مع مولّد موقع ثابت لبناء وثائق تلقائيًا، أو استخدم الناتج في خط CI يُنشئ ملفات PDF عند كل تعديل. وإذا كنت مهتمًا بصيغ تصدير أخرى—مثل تحويل DOCX إلى Markdown مع الحفاظ على LaTeX—اطلع على خيار `SaveFormat.Markdown` في Aspose.Words.

برمجة سعيدة، ولتظهر معادلاتك دائمًا بشكل مثالي! 

![مخطط يوضح تدفق العملية من DOCX → Aspose.Words → تصدير LaTeX TXT](https://example.com/images/how-to-export-latex-flow.png "مخطط تدفق تصدير LaTeX")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}