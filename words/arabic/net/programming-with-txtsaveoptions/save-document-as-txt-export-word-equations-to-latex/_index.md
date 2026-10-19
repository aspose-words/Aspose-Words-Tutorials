---
category: general
date: 2026-03-01
description: احفظ المستند كملف TXT مع معادلات LaTeX باستخدام Aspose.Words. تعلم كيفية
  تحويل Word إلى LaTeX وتصدير المعادلات بسهولة.
draft: false
keywords:
- save document as txt
- convert word to latex
- how to save txt
- how to export equations
- export equations to latex
language: ar
og_description: احفظ المستند كملف TXT مع معادلات LaTeX باستخدام Aspose.Words. تعلم
  كيفية تحويل Word إلى LaTeX وتصدير المعادلات بسهولة.
og_title: حفظ المستند كملف TXT – تصدير معادلات Word إلى LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
- Text Export
title: حفظ المستند كملف TXT – تصدير معادلات Word إلى LaTeX
url: /ar/net/programming-with-txtsaveoptions/save-document-as-txt-export-word-equations-to-latex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ المستند كملف TXT – تصدير معادلات Word إلى LaTeX

هل احتجت يومًا إلى **save document as txt** لكنك خفت أن تختفي معادلات Word الجميلة؟ لست وحدك. يواجه العديد من المطورين هذه المشكلة عندما يحاولون استخراج النص العادي من ملف .docx يحتوي على كائنات Office Math. الخبر السار؟ مع Aspose.Words يمكنك **save document as txt** *و* الاحتفاظ بكل معادلة بصيغة LaTeX نظيفة.

في هذا البرنامج التعليمي سنستعرض عملية تحويل ملف Word إلى ملف نص عادي يحتوي على معادلات بصيغة LaTeX. على طول الطريق سنجيب على سؤال “how to export equations”، ونظهر لك **how to save txt** برمجيًا، بل وسنغطي زاوية “convert word to latex” لأولئك الذين يحتاجون الرياضيات في ورقة علمية. لا إطالة—فقط حل كامل قابل للتنفيذ يمكنك إدراجه في أي مشروع .NET.

## ما ستحصل عليه

- دليل خطوة‑بخطوة يبدأ بتطبيق .NET console جديد وينتهي بملف `Equations.txt` مليء بـ LaTeX.  
- فهم *لماذا* `OfficeMathExportMode.LaTeX` هو الخيار الصحيح للحفاظ على الرياضيات.  
- نصائح للتعامل مع معادلات متعددة، تخطيطات معقدة، ومشكلات شائعة مثل الخطوط المفقودة.  
- عينة كود جاهزة للتنفيذ يمكنك نسخها ولصقها وتشغيلها الآن.  

> **قائمة المتطلبات المسبقة**  
> - .NET 6.0 أو أحدث (يمكنك أيضًا استخدام .NET Framework 4.8، لكن كلما كان أحدث كان أفضل).  
> - حزمة NuGet الخاصة بـ Aspose.Words for .NET (`Install-Package Aspose.Words`).  
> - مستند Word يحتوي على معادلة واحدة على الأقل (سنسميه `Sample.docx`).  

إذا كان لديك كل ذلك، فلنبدأ.

![حفظ المستند كملف txt مثال](image.png "حفظ المستند كملف txt مثال")

## الخطوة 1 – تثبيت Aspose.Words وإنشاء مشروع Console

أولاً وقبل كل شيء. افتح بيئة التطوير المفضلة لديك (Visual Studio، Rider، أو حتى VS Code) وأنشئ مشروع console جديد:

```bash
dotnet new console -n TxtExportDemo
cd TxtExportDemo
dotnet add package Aspose.Words
```

هذا السطر الواحد يجلب أحدث ملفات Aspose.Words الثنائية ويضيفها إلى ملف المشروع. في تجربتي، استخدام أحدث نسخة (حالياً 24.10) يجنبك عددًا من الأخطاء الغامضة المتعلقة بمعالجة Office Math.

## الخطوة 2 – تحميل مستند Word

الآن نحتاج إلى كائن `Document` يمثل ملف .docx الذي نريد تحويله. يضمن بيان `using` تحرير الملف بشكل نظيف.

```csharp
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Load the source Word file – make sure the path is correct.
        Document doc = new Document(@"C:\Path\To\Sample.docx");
        // The rest of the code follows…
    }
}
```

لماذا نحمل المستند بهذه الطريقة؟ `Document` يحلل حزمة OpenXML بالكامل، مكشفًا عن الصور والجداول—وبشكل حاسم—عن عقد `OfficeMath` التي تحتفظ بمعادلاتك. بدون تحميل المستند أولاً، لا شيء لتصديره.

## الخطوة 3 – تكوين خيارات حفظ TXT لتصدير المعادلات كـ LaTeX

هذا هو جوهر البرنامج التعليمي. بشكل افتراضي، حفظ الملف كنص عادي يزيل كل شيء ما عدا الأحرف الخام. ضبط `OfficeMathExportMode` إلى `LaTeX` يخبر Aspose.Words باستبدال كل عقدة `OfficeMath` بتمثيلها بصيغة LaTeX.

```csharp
// Step 3: Configure TXT save options to export Office Math as LaTeX
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    // This converts every equation into LaTeX syntax.
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

**لماذا LaTeX؟** LaTeX هو اللغة المشتركة للنشر العلمي. عندما تُدخل الملف `.txt` الناتج لاحقًا إلى محرر LaTeX أو معالج markdown يدعم `$…$`، تُظهر المعادلات بشكل مثالي. إذا كنت تفضل MathML أو Unicode عادي، يدعم Aspose.Words تلك الأنماط أيضًا—فقط غيّر قيمة الـ enum.

## الخطوة 4 – حفظ المستند كملف نص عادي

مع ضبط الخيارات، يصبح استدعاء الحفظ سطرًا واحدًا. يمكن أن يكون اسم الملف أي شيء تريده؛ سنبقيه `Equations.txt` لتوضيح الأمور.

```csharp
// Step 4: Save the document as a plain‑text file with the configured options
doc.Save(@"C:\Path\To\Equations.txt", txtSaveOptions);
```

تشغيل البرنامج الآن ينتج ملف `Equations.txt` يشبه ما يلي:

```
This is a sample paragraph.

The quadratic formula is given by:
\[
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\]

Another equation:
\[
E = mc^2
\]
```

لاحظ محددات `\[` … `\]`—هذه هي علامات “display math” في LaTeX التي يتعرف عليها العديد من المحررات تلقائيًا.

## الخطوة 5 – التحقق من النتيجة (وماذا تفعل إذا بدت غريبة)

افتح الملف المُولد في أي محرر نصوص. إذا رأيت سلاسل LaTeX الخام، فقد نجحت. إذا ظهرت المعادلات كحروف مشوشة، تحقق من أمرين:

1. **OfficeMathExportMode** – تأكد من ضبطه على `LaTeX`.  
2. **إصدار المستند** – ملفات .doc القديمة قد تخزن المعادلات بصيغة مملوكة؛ حوّلها إلى .docx أولًا.

فحص سريع هو لصق المحتوى في مُعرض LaTeX على الإنترنت (مثل Overleaf). إذا ظهرت المعادلات، فأنت في الطريق الصحيح.

## الخطوة 6 – حالات خاصة ونصائح متقدمة

### عدة معادلات في فقرة واحدة

عندما تتواجد عدة كائنات `OfficeMath` جنبًا إلى جنب، يضيف Aspose.Words مسافة بين كل كتلة LaTeX. إذا كنت تحتاج إلى تحكم أدق (مثلاً معادلات داخلية مفصولة بفواصل)، عالج ملف txt بعد الإنشاء:

```csharp
string txt = File.ReadAllText(@"C:\Path\To\Equations.txt");
txt = txt.Replace(@"\] \[", @"\]\,\[" ); // adds a thin space between display blocks
File.WriteAllText(@"C:\Path\To\Equations.txt", txt);
```

### الحفاظ على تنسيق غير رياضي

النص العادي لا يمكنه احتواء أنماط **bold** أو *italic*، لكن يمكنك طلب من Aspose.Words إضافة علامات markdown:

```csharp
txtSaveOptions.AdditionalExportOptions = TxtExportOptions.Markdown;
```

الآن يظهر النص العريض كـ `**bold**`، والمائل كـ `_italic_`. هذا مفيد إذا كنت ستمرر الملف لاحقًا إلى مولد مواقع ثابتة.

### التصدير إلى صيغ رياضية أخرى

إذا كانت أداتك اللاحقة تفضّل MathML، ما عليك سوى التبديل:

```csharp
txtSaveOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
```

بقية سير العمل تبقى كما هي—مما يوضح مدى سهولة **convert word to latex** *أو* أي صيغة أخرى بتغيير سطر واحد فقط.

## الأسئلة المتكررة

**س: هل يعمل هذا على .NET Core؟**  
ج: بالتأكيد. Aspose.Words متعدد المنصات، لذا يعمل نفس الكود على Windows، Linux، أو macOS.

**س: ماذا عن ملفات Word المحمية بكلمة مرور؟**  
ج: حمّلها باستخدام `LoadOptions` التي تتضمن كلمة المرور، ثم تابع كالمعتاد.

```csharp
LoadOptions loadOpts = new LoadOptions { Password = "mySecret" };
Document protectedDoc = new Document(@"C:\Path\Protected.docx", loadOpts);
```

**س: هل يمكنني تصدير المعادلات فقط، متجاوزًا النص العادي؟**  
ج: نعم. يمكنك التجول عبر `doc.GetChildNodes(NodeType.OfficeMath, true)` وكتابة LaTeX لكل عقدة إلى الملف يدويًا. هذه طريقة أنيقة لـ **export equations to latex** عندما لا تحتاج إلى النص المحيط.

## ملخص – حفظ المستند كـ TXT مع معادلات LaTeX في خطوة واحدة

بدأنا بسؤال بسيط: *كيف أحفظ ملف Word كـ txt مع الحفاظ على الرياضيات؟* عبر تثبيت Aspose.Words، تحميل المستند، تكوين `TxtSaveOptions` مع `OfficeMathExportMode.LaTeX`، ثم استدعاء `doc.Save`، لديك الآن خط أنابيب موثوق يتيح لك **save document as txt** و**export equations to latex**.

من هنا يمكنك:

- **Convert Word to LaTeX** لمخطوطة كاملة.  
- استخدام ملف txt المُولد كمدخل لمولد مواقع ثابتة يدعم LaTeX.  
- توسيع السكريبت لمعالجة مجموعة من ملفات Word دفعة واحدة.  

جرّبه، العب مع وضع التصدير، ودع ملفات LaTeX النصية تقوم بالعمل الشاق لورقتك البحثية أو مشروع الوثائق القادم.

*برمجة سعيدة، ولتظهر معادلاتك دائمًا بشكل جميل!*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}