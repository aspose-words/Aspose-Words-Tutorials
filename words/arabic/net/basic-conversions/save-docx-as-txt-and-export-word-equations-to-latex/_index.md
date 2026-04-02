---
category: general
date: 2026-04-02
description: احفظ ملفات docx كملفات txt وصدر معادلات Word إلى LaTeX في ثوانٍ. حوّل
  رياضيات Word إلى نص عادي باستخدام Aspose.Words – حل سريع وموثوق.
draft: false
keywords:
- save docx as txt
- export word equations latex
- save word plain text
- convert word math text
- export equations to latex
language: ar
og_description: احفظ ملفات docx كملفات txt وصدر معادلات Word إلى LaTeX فورًا. تعلّم
  حلاً كاملاً بلغة C# لتحويل رياضيات Word إلى نص عادي.
og_title: حفظ ملف docx كملف txt وتصدير معادلات Word إلى LaTeX
tags:
- Aspose.Words
- C#
- Document Conversion
title: حفظ ملف docx كملف txt وتصدير معادلات Word إلى LaTeX
url: /ar/net/basic-conversions/save-docx-as-txt-and-export-word-equations-to-latex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ docx كملف txt وتصدير معادلات Word إلى LaTeX

هل احتجت يومًا إلى **حفظ docx كملف txt** مع الحفاظ على تلك المعادلات المزعجة في Word؟ لست وحدك في هذا الإحباط. في العديد من خطوط الأتمتة، يُطلب تفريغ النص العادي للمعالجة اللاحقة، لكن يجب أن تبقى المعادلات – ويفضل أن تكون بصيغة LaTeX لتتمكن من عرضها لاحقًا.

هذا هو المشكلة التي سنحلها الآن. باستخدام Aspose.Words for .NET لن نقوم فقط **بحفظ docx كملف txt**، بل سن **نصدر معادلات Word بصيغة LaTeX**، لتحصل على ملف UTF‑8 نظيف يخلط بين النص العادي والرياضيات الجاهزة للـ LaTeX. لا أدوات خارجية، ولا نسخ يدوي.

في هذا الدليل ستتعلم كيفية:

* تحميل ملف *.docx* يحتوي على كائنات Office Math.  
* ضبط `TxtSaveOptions` بحيث يتحول كل عقدة `OfficeMath` إلى LaTeX.  
* كتابة النتيجة إلى ملف *.txt* يمكنك تمريره إلى معالجات LaTeX، فهارس البحث، أو أي سير عمل نصي عادي.  

المتطلبات قليلة: بيئة تشغيل .NET حديثة (≥ .NET 6)، حزمة Aspose.Words عبر NuGet، ومستند Word يحتوي على معادلة واحدة على الأقل. إذا كنت مرتاحًا مع C# وتملك Visual Studio أو VS Code، فأنت جاهز للانطلاق.

![Save docx as txt with LaTeX equations](https://example.com/image.png "Save docx as txt with LaTeX equations")

## ما ستحتاجه

| العنصر | السبب |
|------|--------|
| **Aspose.Words for .NET** (NuGet) | يوفر الفئات `Document` و `TxtSaveOptions` التي تدعم Office Math. |
| **.NET 6+** | ميزات لغة حديثة وأداء أفضل. |
| **ملف .docx** يحتوي على معادلات (مثل `input.docx`) | المصدر الذي سنحوّله. |
| **أي بيئة تطوير** (Visual Studio, Rider, VS Code) | لكتابة وتشغيل مقتطف C#. |

الآن لنشمر عن سواعدنا ونجعل الكود يعمل.

## الخطوة 1 – تحميل المستند المصدر (تحضير **حفظ docx كملف txt**)

قبل أن نتمكن من **حفظ docx كملف txt**، يجب جلب ملف Word إلى الذاكرة. فئة `Document` تمثل بنية الملف بالكامل، بما في ذلك الفقرات والجداول، وبشكل حاسم – كائنات `OfficeMath`.

```csharp
using Aspose.Words;

// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");

// Quick sanity check – print how many equations we found
int equationCount = doc.GetChildNodes(NodeType.OfficeMath, true).Count;
Console.WriteLine($"Found {equationCount} equation(s) in the document.");
```

*لماذا هذا مهم:* من خلال فحص `NodeType.OfficeMath` نتأكد أن المستند يحتوي فعليًا على رياضيات. إذا كان العدد صفرًا، فإن خطوة **تصدير المعادلات إلى LaTeX** لاحقًا لن تكتب شيئًا، مما قد يكون خطأ صامتًا في خط أنابيب أكبر.

## الخطوة 2 – ضبط خيارات حفظ TXT لـ **تصدير معادلات Word بصيغة LaTeX**

السحر يحدث في `TxtSaveOptions`. ضبط `OfficeMathExportMode` إلى `LaTeX` يخبر Aspose.Words أن يستبدل كل عقدة `OfficeMath` بتمثيل LaTeX بدلاً من النص العادي الافتراضي.

```csharp
// Configure TXT save options – this is where we enable LaTeX export
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    // Export each OfficeMath object as LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
    
    // Optional: preserve original line breaks for better readability
    PreserveTableLayout = true,
    
    // Optional: set encoding explicitly (UTF‑8 works everywhere)
    Encoding = System.Text.Encoding.UTF8
};
```

*لماذا هذا مهم:* بدون `OfficeMathExportMode = LaTeX`، سيعود Aspose.Words إلى تقريب نصي عادي للمعادلة، وهو غالبًا غير قابل للقراءة. إخراج LaTeX يكون مضغوطًا ومفهومًا عالميًا من قبل الأدوات العلمية.

## الخطوة 3 – حفظ المستند كنص عادي (الختام **حفظ docx كملف txt**)

الآن نُجري أخيرًا **حفظ docx كملف txt**—لكن مع تضمين المعادلات الغنية بـ LaTeX.

```csharp
// Define the output path
string outputPath = @"C:\MyDocs\Math.txt";

// Perform the conversion
doc.Save(outputPath, txtSaveOptions);

Console.WriteLine($"Conversion complete! Text file saved at: {outputPath}");
```

### النتيجة المتوقعة

افتح `Math.txt` بأي محرر وسترى شيء مشابه لـ:

```
This is a sample paragraph.

Here is an inline equation: $E = mc^{2}$

Another block equation:
\[
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
\]

Regular text continues here.
```

النص المحيط هو UTF‑8 نقي، بينما كل معادلة تظهر كـ LaTeX محاطة بـ `$…$` (مضمنة) أو `\[…\]` (عرض). هذا يحقق متطلبات **تحويل نص رياضيات Word** ويجعل الملف جاهزًا للعرض عبر LaTeX أو فهرسة محركات البحث.

## الخطوة 4 – الحالات الخاصة والنصائح العملية (تحسين **تصدير المعادلات إلى LaTeX**)

### 4.1 معالجة المستندات بدون معادلات
إذا كان `equationCount` يساوي صفرًا، قد ترغب في تخطي التحويل أو إصدار تحذير:

```csharp
if (equationCount == 0)
{
    Console.WriteLine("Warning: No equations found. The output will be plain text only.");
}
```

### 4.2 المستندات الكبيرة واستهلاك الذاكرة
لملفات متعددة الميغابايت، فكر في تحميل المستند باستخدام `LoadOptions` التي تتيح البث:

```csharp
LoadOptions loadOptions = new LoadOptions { LoadFormat = LoadFormat.Docx };
Document largeDoc = new Document(@"C:\MyDocs\bigfile.docx", loadOptions);
```

البث يقلل من الضغط على الذاكرة، وهو مفيد عندما تقوم بـ **حفظ نص Word** للوظائف الدفعية.

### 4.3 تخصيص فواصل المعادلات
إذا كان المحلل اللاحق يتوقع `$$…$$` بدلًا من `\[…\]`، يمكنك معالجة النص بعد الإنشاء:

```csharp
string txt = File.ReadAllText(outputPath);
txt = txt.Replace(@"\[", "$$").Replace(@"\]", "$$");
File.WriteAllText(outputPath, txt);
```

### 4.4 التوافق مع إصدارات Aspose.Words القديمة
ظهر تعداد `OfficeMathExportMode` في الإصدار 22.9. إذا كنت عالقًا على إصدار أقدم، سيتعين عليك الترقية أو الرجوع إلى استخراج MathML وتحويله يدويًا—وهو مسار أكثر تعقيدًا.

## الخطوة 5 – التحقق من النتيجة (اختبار سير عمل **حفظ نص Word**)

اختبار سريع هو تمرير ملف `.txt` المُنتج إلى محرك LaTeX (مثل `pdflatex`) داخل مستند بسيط:

```latex
\documentclass{article}
\usepackage{amsmath}
\begin{document}
\input{C:/MyDocs/Math.txt}
\end{document}
```

إذا نجح التجميع وعُرضت المعادلات بشكل صحيح، فقد أتممت عملية **تصدير معادلات Word بصيغة LaTeX** بنجاح.

## الخلاصة

استعرضنا حلًا كاملًا ومستقلاً يتيح لك **حفظ docx كملف txt** مع **تصدير معادلات Word إلى LaTeX**. الخطوات الأساسية—تحميل المستند، ضبط `TxtSaveOptions`، وكتابة الملف—تتطلب بضع أسطر من الشيفرة فقط، لكنها تفتح بابًا قويًا لتحويل المستندات لأي مطور .NET.

هل انتهيت من الأساسيات؟ يمكنك الآن:

* **حفظ نص Word** لفهرسة البحث النصي الكامل.  
* **تحويل نص رياضيات Word** إلى صيغ أخرى (MathML، Unicode).  
* أتمتة التحويلات الدفعية عبر مجلد من المستندات.  

لا تتردد في تجربة الإعدادات الاختيارية أعلاه، وشاركنا تعليقًا إذا واجهت أي صعوبة. برمجة سعيدة!  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}