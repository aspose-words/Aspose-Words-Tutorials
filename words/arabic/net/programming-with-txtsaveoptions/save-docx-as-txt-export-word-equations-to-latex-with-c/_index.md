---
category: general
date: 2026-04-05
description: احفظ ملف docx كملف txt باستخدام Aspose.Words – تحويل سريع من Word إلى txt وتعلّم
  كيفية تصدير المعادلات الرياضية كـ LaTeX. كود C# بسيط، لا حاجة لأدوات إضافية.
draft: false
keywords:
- save docx as txt
- convert word to txt
- how to export math
- how to save txt
- convert word equations latex
language: ar
og_description: احفظ ملف docx كملف txt في C# وتعرّف على كيفية تصدير الرياضيات إلى LaTeX.
  اتبع هذا الدليل خطوة بخطوة لتحويل Word إلى txt مع الحفاظ على المعادلات.
og_title: حفظ ملف docx كملف txt – تصدير معادلات Word إلى LaTeX
tags:
- Aspose.Words
- C#
- Document Conversion
title: حفظ ملف docx كملف txt – تصدير معادلات Word إلى LaTeX باستخدام C#
url: /ar/net/programming-with-txtsaveoptions/save-docx-as-txt-export-word-equations-to-latex-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ docx كملف txt – تصدير معادلات Word إلى LaTeX باستخدام C#

هل احتجت يوماً إلى **save docx as txt** لكنك كنت قلقاً من أن تختفي معادلاتك أو تتحول إلى رموز غير قابلة للقراءة؟ لست وحدك. يواجه العديد من المطورين هذه المشكلة عندما يحاولون **convert word to txt** للمعالجة اللاحقة، خاصةً عندما يحتوي ملف المصدر على كائنات Office Math.

الخبر السار؟ ببضع أسطر من C# والخيارات المناسبة، يمكنك ليس فقط **convert Word to txt** بل أيضاً الحفاظ على كل معادلة كترميز LaTeX نظيف. في هذا الدرس سنستعرض العملية بالكامل، نشرح لماذا كل إعداد مهم، ونظهر لك كيفية التحقق من النتيجة.

سنغطي:

* تثبيت مكتبة Aspose.Words for .NET  
* تحميل ملف `.docx` يحتوي على معادلات رياضية  
* تكوين `TxtSaveOptions` بحيث يصبح **how to export math** سلسلة صديقة لـ LaTeX  
* حفظ الملف والتحقق من الناتج  

في النهاية، ستحصل على مقتطف قابل لإعادة الاستخدام يتيح لك **save docx as txt** مع الحفاظ على كل صيغة كـ LaTeX—مثالي لسلاسل الأنابيب العلمية، مولدات المواقع الثابتة، أو أي سير عمل يحتاج إلى رياضيات نصية عادية.

---

## المتطلبات المسبقة

قبل أن نغوص في التفاصيل، تأكد من أن لديك:

* .NET 6.0 أو أحدث (الكود يعمل أيضاً مع .NET Framework 4.6+ )  
* Visual Studio 2022 (أو أي بيئة تطوير تفضلها)  
* حزمة **Aspose.Words for .NET** عبر NuGet – ثبّتها باستخدام  

```bash
dotnet add package Aspose.Words
```

لا توجد محولات إضافية أو أدوات خارجية مطلوبة؛ Aspose.Words يتولى كل العمل ثقيلًا داخليًا.

---

## الخطوة 1: تثبيت وإضافة مرجع Aspose.Words

أولاً، أضف المكتبة إلى مشروعك. إذا كنت تستخدم سطر الأوامر، شغّل الأمر أعلاه. في Visual Studio يمكنك أيضاً النقر بزر الماوس الأيمن على **Dependencies → Manage NuGet Packages** والبحث عن *Aspose.Words*.

```csharp
// Add the namespace at the top of your file
using Aspose.Words;
using Aspose.Words.Saving;
```

> **Pro tip:** استخدم أحدث نسخة مستقرة (حتى أبريل 2026 الإصدار هو 24.10). الإصدارات الأحدث تجلب إصلاحات للأخطاء المتعلقة بمعالجة OfficeMath، مما يجنبك فقدان الرموز غير المتوقّع.

---

## الخطوة 2: تحميل المستند المصدر

الآن نقوم بتحميل ملف `.docx` الذي يحتوي على المعادلات التي تريد الاحتفاظ بها. فئة `Document` تمثل ملف Word بالكامل، وتمنحك الوصول إلى النصوص، الصور، وكائنات Office Math.

```csharp
// Step 2: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – make sure the document actually loaded
if (doc == null || doc.PageCount == 0)
{
    throw new InvalidOperationException("The document could not be loaded or is empty.");
}
```

لماذا نحمل الملف أولاً؟ Aspose.Words يحلل الملف إلى نموذج كائنات، مما يسمح لنا بفحص أو تعديل المحتوى قبل أن نقرر طريقة التصدير. هنا تبدأ قرارات **how to export math** في إظهار أهميتها.

---

## الخطوة 3: تكوين TxtSaveOptions لتصدير LaTeX

جوهر الحل هو فئة `TxtSaveOptions`. بشكل افتراضي، حفظ الملف كـ TXT يزيل كل Office Math تمامًا. ضبط `OfficeMathExportMode` إلى `LaTeX` يخبر المكتبة بترجمة كل معادلة إلى تمثيل LaTeX الخاص بها.

```csharp
// Step 3: Create TxtSaveOptions and set the OfficeMath export mode to LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This makes every OfficeMath object become LaTeX code in the output file
    OfficeMathExportMode = TxtSaveOptions.OfficeMathExportMode.LaTeX,

    // Optional: preserve line breaks as they appear in Word
    PreserveTableLayout = true,

    // Optional: ensure UTF‑8 encoding so special symbols survive
    Encoding = System.Text.Encoding.UTF8
};
```

**Why LaTeX?** LaTeX هو اللغة المشتركة للنشر العلمي. بتصدير الرياضيات بهذه الطريقة، تحتفظ بدلالة المعادلة بدلاً من صورة مسطحة أو سلسلة مشوشة. إذا قمت لاحقًا بتمرير ملف TXT إلى معالج Markdown يدعم MathJax، ستظهر المعادلات بشكل مثالي.

---

## الخطوة 4: حفظ المستند كنص عادي

مع تكوين الخيارات، الخطوة الأخيرة هي سطر واحد يكتب الملف إلى القرص.

```csharp
// Step 4: Save the document as plain‑text using the configured options
doc.Save("YOUR_DIRECTORY/MathSample.txt", txtOptions);
```

هذا كل شيء—ملف `.docx` الخاص بك أصبح الآن ملف `.txt` حيث تظهر كل معادلة كقطة LaTeX، جاهزة للاستخدام في المراحل اللاحقة.

---

## التحقق من النتيجة (كيفية حفظ txt بشكل صحيح)

افتح `MathSample.txt` في أي محرر نصوص. يجب أن ترى شيئًا مشابهًا لـ:

```
This is a sample paragraph.

Here is an equation in LaTeX:
\[
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
\]

Another line of regular text.
```

إذا لاحظت وجود أحرف خاصة بـ Word (مثل `?` أو رموز مفقودة)، تأكد من:

* أنك تستخدم نسخة حديثة من Aspose.Words (الإصدارات القديمة كانت تحتوي على أخطاء في OfficeMath).  
* أن المستند المصدر يحتوي فعليًا على كائنات **OfficeMath**—not كائنات محرر المعادلات Legacy. بالنسبة الأخيرة، قد تحتاج إلى تحويلها يدويًا أو استخدام طريقة `ConvertMathToOfficeMath` قبل الحفظ.

---

## الاختلافات الشائعة وحالات الحافة

| الحالة | ما الذي يجب فعله |
|-----------|------------|
| **Legacy Equation Editor** objects | استدعِ `doc.ConvertMathToOfficeMath()` قبل الخطوة 3. |
| **You need plain Unicode math, not LaTeX** | عيّن `OfficeMathExportMode = TxtSaveOptions.OfficeMathExportMode.Unicode`. |
| **Large documents (100 + MB)** | قم ببث عملية الحفظ باستخدام `doc.Save(Stream, txtOptions)` لتجنب استهلاك الذاكرة العالي. |
| **You want to keep the original file name** | استخدم `Path.GetFileNameWithoutExtension(inputPath) + ".txt"` عند إنشاء مسار الإخراج. |

هذه التعديلات تجيب على سؤال “**how to export math**” لمختلف سلاسل الأنابيب، وتضمن أن يكون حلك قويًا بغض النظر عن المصدر.

---

## مثال كامل يعمل (جميع الخطوات في مكان واحد)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Install Aspose.Words via NuGet before running this code.

        // 2️⃣ Load the .docx containing equations
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // Optional: Convert legacy equations to OfficeMath (covers edge cases)
        doc.ConvertMathToOfficeMath();

        // 3️⃣ Set up TXT save options – LaTeX export for math
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = TxtSaveOptions.OfficeMathExportMode.LaTeX,
            PreserveTableLayout = true,
            Encoding = System.Text.Encoding.UTF8
        };

        // 4️⃣ Define output path and save
        string outputPath = Path.Combine(
            Path.GetDirectoryName(inputPath),
            Path.GetFileNameWithoutExtension(inputPath) + ".txt");

        doc.Save(outputPath, txtOptions);

        Console.WriteLine($"✅ Successfully saved '{outputPath}'.");
    }
}
```

شغّل البرنامج، افتح ملف `.txt` المُولد، وسترى معادلات LaTeX مدمجة في المكان الذي كانت فيه. هذه هي أبسط طريقة لـ **convert

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}