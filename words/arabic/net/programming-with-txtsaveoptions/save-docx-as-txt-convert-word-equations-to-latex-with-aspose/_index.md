---
category: general
date: 2025-12-31
description: احفظ ملف docx كملف txt باستخدام Aspose.Words – اكتشف كيفية تحويل Word إلى LaTeX،
  وتصدير الرياضيات إلى LaTeX، وتحويل معادلات docx إلى LaTeX نصّي بسيط.
draft: false
keywords:
- save docx as txt
- convert word to latex
- convert docx to latex
- convert word equations latex
- export math to latex
language: ar
og_description: احفظ ملف docx كملف txt باستخدام Aspose.Words. تعلم خطوة بخطوة كيفية
  تحويل Word إلى LaTeX، وتصدير الرياضيات إلى LaTeX، ومعالجة معادلات docx كنص عادي.
og_title: حفظ ملف docx كملف txt – دليل سريع لتحويل معادلات Word إلى LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
- Document conversion
title: حفظ ملف docx كملف txt – تحويل معادلات Word إلى LaTeX باستخدام Aspose.Words
url: /ar/net/programming-with-txtsaveoptions/save-docx-as-txt-convert-word-equations-to-latex-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ docx كـ txt – تحويل معادلات Word إلى LaTeX باستخدام Aspose.Words

هل احتجت يومًا إلى **حفظ docx كـ txt** مع الحفاظ على معادلات Office Math الصعبة؟ لست وحدك. في العديد من المشاريع—الأوراق الأكاديمية، الوثائق التقنية، أو خطوط الأنابيب الآلية—يرغب المطورون في تمثيل نصي بسيط مع الحفاظ على الرياضيات الأصلية بصيغة LaTeX.

الأمر بسيط: Aspose.Words يجعل ذلك سهلًا للغاية. في هذا الدرس ستتعرف على كيفية **تحويل Word إلى LaTeX**، **تصدير الرياضيات إلى LaTeX**، والحصول على ملف `.txt` منظم يمكنك تمريره إلى أي أداة لاحقة. لا نسخ‑لصق يدوي، لا تعبيرات regex معقدة، فقط كود C# نظيف.

سنستعرض كل ما تحتاجه: المتطلبات المسبقة، الكود الكامل، سبب أهمية كل سطر، وبعض النصائح المفيدة للحالات الخاصة. في النهاية، ستتمكن من تشغيل المثال على جهازك وتكييفه للمشاريع الأكبر.

---

## ما ستحتاجه

قبل أن نبدأ، تأكد من توفر ما يلي:

- **.NET 6.0 أو أحدث** (المثال يستخدم .NET 6، لكن أي نسخة حديثة تعمل)
- **Aspose.Words for .NET** – يمكنك الحصول على حزمة تجريبية مجانية عبر NuGet (`Install-Package Aspose.Words`)  
- مستند Word (`input.docx`) يحتوي على معادلة Office Math واحدة على الأقل  
- بيئة تطوير مفضلة (Visual Studio، Rider، أو VS Code مع امتداد C#)

هذا كل شيء—لا مكتبات إضافية، لا COM interop، ولا ملفات إعداد مخفية.

---

## الخطوة 1: تثبيت Aspose.Words وإعداد المشروع

أولًا، أضف حزمة Aspose.Words إلى مشروعك. افتح الطرفية في مجلد الحل وشغّل:

```bash
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** إذا كنت تستخدم Visual Studio، يمكنك أيضًا إضافة الحزمة عبر واجهة NuGet Package Manager. المكتبة مُدارة بالكامل، لذا لن تحتاج إلى أي DLLs أصلية.

---

## الخطوة 2: تحميل مستند Word الذي يحتوي على معادلات رياضية

الآن سنحمّل ملف `.docx`. هذه الخطوة هي بداية عملية **حفظ docx كـ txt**، لأننا نحتاج إلى كائن `Document` يمكن لـ Aspose.Words التعامل معه.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Path to the source Word file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; Aspose.Words parses all parts, including Office Math
Document document = new Document(inputPath);
```

**لماذا هذا مهم:** Aspose.Words يقرأ حزمة OOXML بالكامل، لذا أي كائنات معادلات مدمجة تُمثَّل كعُقد `OfficeMath` داخل نموذج كائن `Document`. إذا تخطيت هذه الخطوة أو استخدمت تدفق ملف عادي، قد تُفقد معلومات الرياضيات.

---

## الخطوة 3: تكوين خيارات حفظ النص لتصدير الرياضيات كـ LaTeX

السحر يحدث عندما نخبر Aspose.Words كيف يتعامل مع `OfficeMath`. فئة `TxtSaveOptions` تحتوي على خاصية `OfficeMathExportMode` التي تقبل `OfficeMathExportMode.LaTeX`. هذا يخبر المكتبة بتحويل كل معادلة إلى سلسلة LaTeX بدلاً من النص العادي الافتراضي.

```csharp
// Create save options for plain‑text output
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Export Office Math nodes as LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
    
    // Optional: preserve line breaks from the original document
    PreserveTableLayout = true,
    
    // Optional: set encoding to UTF‑8 (default is UTF‑8, but explicit is clearer)
    Encoding = Encoding.UTF8
};
```

**لماذا هذا مهم:** بدون ضبط `OfficeMathExportMode`، سيستبدل Aspose.Words كل معادلة ببديل مثل “[Equation]”. باختيار `LaTeX`، ستحصل على العلامة الدقيقة التي تكتبها يدويًا، جاهزة لأي معالج LaTeX.

---

## الخطوة 4: حفظ المستند كملف نصي عادي

أخيرًا، نكتب المحتوى المحوَّل إلى ملف `.txt`. سيحتوي الملف على نص عادي متداخل مع مقتطفات LaTeX لكل معادلة.

```csharp
// Destination path for the output text file
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.txt");

// Save the document using the configured options
document.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved as txt at: {outputPath}");
```

تشغيل البرنامج ينتج `output.txt` يبدو تقريبًا هكذا (با افتراض أن المستند الأصلي يحتوي على معادلة تربيعية بسيطة):

```
Here is a quadratic formula:
\[
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\]

And here's a summation:
\[
\sum_{n=1}^{\infty} \frac{1}{n^2} = \frac{\pi^2}{6}
\]
```

**لماذا هذا مهم:** الملف الناتج هو نص UTF‑8 نقي، لذا يمكنك تمريره إلى أنظمة التحكم في الإصدارات، أدوات المقارنة، أو أي معالج يدعم LaTeX دون الحاجة إلى تحويل إضافي.

---

## الخطوة 5: التحقق من الناتج ومعالجة الحالات الخاصة

### تحقق سريع

افتح `output.txt` في أي محرر نصوص. يجب أن ترى فقرات عادية مختلطة مع كتل LaTeX محاطة بـ `\[` … `\]` (رياضيات عرض) أو `$…$` (رياضيات داخلية). إذا لاحظت بدائل `[Equation]`، فتأكد من ضبط `OfficeMathExportMode` بشكل صحيح.

### المشكلات الشائعة وكيفية تجنبها

| المشكلة | السبب | الحل |
|-------|-------|-----|
| تظهر المعادلات كـ `[Equation]` | ترك `OfficeMathExportMode` على الوضع الافتراضي (`PlainText`) | ضبط `OfficeMathExportMode = OfficeMathExportMode.LaTeX` |
| تشوه الأحرف غير ASCII | حفظ الملف بترميز غير UTF‑8 | تعيين صراحةً `txtOptions.Encoding = Encoding.UTF8` |
| التخطيط يبدو مضغوطًا | ترك `PreserveTableLayout` على `false` وتقلص الجداول | تمكين `PreserveTableLayout = true` |
| المستندات الكبيرة تستغرق وقتًا | الحفظ باستخدام الضغط الافتراضي قد يكون أبطأ | استخدام `txtOptions.Compression = CompressionLevel.Fastest` (اختياري) |

---

## مكافأة: تحويل Word إلى LaTeX مباشرة (بدون خطوة txt وسيطة)

إذا كان هدفك هو **تحويل docx إلى latex** دون خطوة النص العادي، يمكنك ببساطة تغيير صيغة الحفظ:

```csharp
// Save as a .tex file (LaTeX source)
document.Save("output.tex", SaveFormat.LaTeX);
```

هذا ينتج مستند LaTeX كامل، يتضمن المقدمة، `\begin{document}`، وجميع المعادلات مُصدَّرة كـ LaTeX. مفيد عندما تحتاج إلى مصدر LaTeX كامل بدلاً من مقتطفات فقط.

---

## الأسئلة المتكررة

**س: هل يعمل هذا مع ملفات .doc (صيغة Word القديمة)؟**  
ج: نعم. يمكن لـ Aspose.Words تحميل ملفات `.doc` بنفس الطريقة؛ لا يزال `OfficeMathExportMode` يُطبق.

**س: ماذا لو أردت رياضيات داخلية (`$…$`) بدلاً من عرضية؟**  
ج: استخدم `OfficeMathExportMode = OfficeMathExportMode.LaTeXInline` (متاح في الإصدارات الأحدث) للحصول على `$…$` للمعادلات داخل النص.

**س: هل يمكنني معالجة مجموعة من المستندات دفعة واحدة؟**  
ج: بالتأكيد. ضع منطق التحميل/الحفظ داخل حلقة `foreach` على مجلد يحتوي على ملفات `.docx`. تذكر تحرير كل كائن `Document` أو إعادة استخدام كائن واحد إذا كانت الذاكرة تشكل قلقًا.

**س: هل النسخة التجريبية كافية للإنتاج؟**  
ج: النسخة التجريبية تعمل بالكامل لكنها تضيف تعليقًا صغيرًا كعلامة مائية في الملفات المولدة. للإنتاج، اشترِ ترخيصًا؛ سيظل استخدام الـ API هو نفسه.

---

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑لصقه في تطبيق Console جديد (`dotnet new console`) وتشغيله فورًا.

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Load the Word document that contains math
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document doc = new Document(inputPath);

        // -------------------------------------------------
        // 2️⃣ Configure TxtSaveOptions to export OfficeMath as LaTeX
        // -------------------------------------------------
        TxtSaveOptions options = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            PreserveTableLayout = true,
            Encoding = Encoding.UTF8
        };

        // -------------------------------------------------
        // 3️⃣ Save the document as plain‑text (txt)
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.txt");
        doc.Save(outputPath, options);

        Console.WriteLine($"✅ save docx as txt completed. Output at: {outputPath}");
    }
}
```

**الناتج المتوقع:** فتح `output.txt` يُظهر فقرات عادية بالإضافة إلى كتل LaTeX مثل `\[\int_0^1 x^2 dx = \frac{1}{3}\]`. يطبع الطرفية رسالة نجاح مع إيموجي علامة ✓ لإضفاء طابع ودود.

---

## الخلاصة

أصبح لديك الآن طريقة واضحة من البداية إلى النهاية **لحفظ docx كـ txt** مع **تحويل Word إلى LaTeX** لكل معادلة داخل المستند. باستخدام `OfficeMathExportMode` في Aspose.Words، تتجنب استخراج الرياضيات يدويًا وتحصل على LaTeX نظيف يعمل مع أي أداة لاحقة.

باختصار:

- حمّل ملف `.docx` باستخدام Aspose.Words  
- اضبط `TxtSaveOptions.OfficeMathExportMode = LaTeX`  
- احفظ كـ `.txt` (أو مباشرةً كـ `.tex` للحصول على ملف LaTeX كامل)  

جرّب الوضع الداخلي، عالج مجموعة ملفات، أو دمج الكود في خط أنابيب CI ي抽ّ المعادلات تلقائيًا لتوليد الوثائق. الاحتمالات لا حصر لها.

هل لديك أسئلة إضافية حول **تحويل docx إلى latex**، **تصدير الرياضيات إلى latex**، أو التعامل مع تخطيطات معادلات معقدة؟ اترك تعليقًا أدناه، ونتمنى لك برمجة سعيدة!

---

![مخطط يوضح تدفق العملية من مستند Word → معالجة Aspose.Words → تصدير LaTeX → حفظ docx كـ txt](https://example.com/placeholder-image.png "مخطط سير عمل حفظ docx كـ txt")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}