---
category: general
date: 2026-01-08
description: تعلم كيفية تصدير LaTeX من ملف DOCX باستخدام Aspose.Words – تحويل docx
  إلى markdown، حفظ Word كـ markdown، وحفظ docx كملف txt في دقائق.
draft: false
keywords:
- how to export latex
- convert docx to markdown
- save word as markdown
- save docx as markdown
- save docx as txt
language: ar
og_description: دليل خطوة بخطوة حول كيفية تصدير LaTeX من مستندات Word، وتحويل docx
  إلى markdown، وحفظ docx كملف txt باستخدام Aspose.Words.
og_title: 'كيفية تصدير LaTeX: تحويل DOCX إلى Markdown و TXT'
tags:
- Aspose.Words
- C#
- Document Conversion
title: 'كيفية تصدير LaTeX: تحويل DOCX إلى Markdown و TXT'
url: /ar/net/programming-with-markdownsaveoptions/how-to-export-latex-convert-docx-to-markdown-txt/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تصدير LaTeX من مستندات Word  

هل احتجت يومًا إلى **كيفية تصدير LaTeX** من ملف Word لكن لم تكن متأكدًا أي واجهة برمجة تطبيقات (API) تستخدم؟ لست وحدك—المطورون يسألون باستمرار، “هل يمكنني الحفاظ على معادلاتي عندما أحول ملف .docx إلى شيء أخف مثل markdown؟”  

الإجابة المختصرة هي **نعم**. باستخدام Aspose.Words يمكنك تحويل docx إلى markdown، حفظ Word كـ markdown، وحتى حفظ docx كـ txt مع الحفاظ على معادلات Office Math الأصلية كـ LaTeX. في هذا الدرس سنستعرض العملية بالكامل، نشرح لماذا كل إعداد مهم، ونزودك بعينة كود جاهزة للتنفيذ.

## ما ستحتاجه  

- .NET 6+ (أو .NET Framework 4.7.2+).  
- مرجع إلى حزمة **Aspose.Words** عبر NuGet (`Install-Package Aspose.Words`).  
- مستند Word (`input.docx`) يحتوي على معادلة واحدة على الأقل (OfficeMath).  

هذا كل شيء. لا محولات إضافية، ولا سكريبتات ما بعد المعالجة المعقدة.

![كيفية تصدير LaTeX من Word](/images/export-latex-word.png)

*نص بديل للصورة: how to export latex from a Word document using Aspose.Words*

## الخطوة 1: كيفية تصدير LaTeX – إعداد المشروع  

أولاً، أنشئ تطبيق console جديد (أو دمج الكود في أي مشروع C# موجود). أضف توجيهات `using` المطلوبة حتى يعرف المترجم أين توجد الفئات:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

لماذا مساحة الاسم `Aspose.Words.Saving`؟ لأنها تحتوي على الفئات `MarkdownSaveOptions` و `TxtSaveOptions` التي تسمح لك بتحديد كيفية تصيير كائنات OfficeMath. بدون هذه الخيارات ستحصل على عناصر نائبة عامة بدلاً من LaTeX الحقيقي.

## الخطوة 2: تحميل ملف DOCX المصدر  

```csharp
// Step 2: Load the source document containing equations
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

إذا لم يُعثر على الملف، ستطرح Aspose استثناء `FileNotFoundException`. نصيحة سريعة: احتفظ بملف الإدخال بجوار الملف التنفيذي أثناء التطوير، أو استخدم مسارًا مطلقًا للسكريبتات الإنتاجية.

## الخطوة 3: تحويل DOCX إلى Markdown – تصدير LaTeX  

Markdown هو تنسيق خفيف شائع، لكنه بشكل افتراضي يتجاهل OfficeMath. للحفاظ على المعادلات، قم بتكوين `MarkdownSaveOptions`:

```csharp
// Step 3: Configure Markdown save options to export OfficeMath as LaTeX
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This tells Aspose to render each equation as a LaTeX block
    OfficeMathExportMode = OfficeMathExportMode.LaTeX   // alternatives: MathML, Text
};
```

**لماذا LaTeX؟** LaTeX هو المعيار الفعلي للوثائق العلمية؛ معظم عارضات markdown (GitHub، MkDocs، Jekyll) تفهم كتل `$…$` أو `$$…$$`. إذا كنت تفضّل MathML للعرض على الويب، فقط استبدل قيمة الـ enum.

الآن احفظ ملف markdown:

```csharp
// Step 4: Save the document as a Markdown file with LaTeX equations
document.Save("YOUR_DIRECTORY/output.md", markdownOptions);
```

سيحتوي الملف `output.md` الناتج على شيء مشابه لـ:

```markdown
Here is an equation:

$$
\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
$$
```

## الخطوة 4: حفظ DOCX كـ TXT – الحفاظ على LaTeX داخل النص  

أحيانًا تحتاج فقط إلى نص عادي—ربما لفهرسة سريعة. نفس الخاصية `OfficeMathExportMode` تعمل مع `TxtSaveOptions`:

```csharp
// Step 5: Configure plain‑text (TXT) save options to export OfficeMath as LaTeX
TxtSaveOptions textOptions = new TxtSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};

// Step 6: Save the document as a plain‑text file with LaTeX equations
document.Save("YOUR_DIRECTORY/output.txt", textOptions);
```

سيحتوي `output.txt` على تمثيل LaTeX مدمج مع النص المحيط، مما يجعله قابلًا للبحث مع الحفاظ على الدقة الرياضية.

## الاختلافات الشائعة وحالات الحافة  

| السيناريو | الإعداد الموصى به | السبب |
|----------|--------------------|-------|
| تحتاج MathML لصفحة ويب | `OfficeMathExportMode.MathML` | MathML يُفهم أصلاً من قبل المتصفحات التي تدعم MathML. |
| تريد فقط نص المعادلة، بدون تنسيق | `OfficeMathExportMode.Text` | يزيل رموز LaTeX، ويترك أحرف رياضية Unicode عادية. |
| مستندك يحتوي على صور تريدها أيضًا في markdown | `markdownOptions.ImagesFolder = "images"` و `markdownOptions.ExportImagesAsBase64 = false` | يحافظ على الصور كملفات منفصلة، وهو ما تتوقعه العديد من مولدات المواقع الثابتة. |
| المستندات الكبيرة تسبب ضغطًا على الذاكرة | استخدم `Document.LoadOptions` مع `LoadFormat.Docx` وعالج الصفحات تدريجيًا | يمنع تحميل الملف بالكامل في الذاكرة دفعة واحدة. |

**نصيحة احترافية:** اختبر دائمًا الـ markdown المُولد في العارض المستهدف (GitHub، معاينة VS Code، إلخ) لأن بعض المنصات تدعم فقط `$…$` للرياضيات داخل السطر و `$$…$$` للرياضيات المنفصلة.

## مثال كامل يعمل  

فيما يلي البرنامج الكامل جاهز للنسخ‑واللصق الذي يدمج كل خطوة تم مناقشتها:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

namespace ExportLatexDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Adjust these paths to match your environment
            string inputPath = "YOUR_DIRECTORY/input.docx";
            string markdownPath = "YOUR_DIRECTORY/output.md";
            string txtPath = "YOUR_DIRECTORY/output.txt";

            // Load the source document
            Document doc = new Document(inputPath);

            // ---------- Export to Markdown ----------
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                // Optional: keep images as separate files
                ExportImagesAsBase64 = false,
                ImagesFolder = "images"
            };
            doc.Save(markdownPath, mdOptions);
            Console.WriteLine($"Markdown with LaTeX saved to: {markdownPath}");

            // ---------- Export to Plain Text ----------
            TxtSaveOptions txtOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX
            };
            doc.Save(txtPath, txtOptions);
            Console.WriteLine($"Plain‑text with LaTeX saved to: {txtPath}");
        }
    }
}
```

شغّل البرنامج (`dotnet run`)، وستحصل على ملفين يحافظان على كل معادلة كـ LaTeX—بالضبط ما تحتاجه عندما تريد **كيفية تصدير LaTeX** من Word.

## الأسئلة المتكررة  

**س: هل يعمل هذا مع ملفات .doc (الصيغة الثنائية القديمة)؟**  
ج: نعم. يمكن لـ Aspose.Words تحميل ملفات `.doc` بنفس الطريقة؛ فقط استخدم `new Document("file.doc")`. منطق تصدير LaTeX يبقى هو نفسه.

**س: ماذا لو احتوت المعادلة على رموز غير مدعومة؟**  
ج: سيعود Aspose إلى أقرب تمثيل Unicode. بالنسبة للرموز الغريبة جدًا قد تحتاج إلى معالجة ما بعد التصدير لسلسلة LaTeX.

**س: هل يمكنني معالجة مجموعة من ملفات DOCX دفعة واحدة؟**  
ج: بالتأكيد. غلف منطق `Main` داخل حلقة `foreach (var file in Directory.GetFiles(folder, "*.docx"))` وعدّل أسماء المخرجات وفقًا لذلك.

## الخلاصة  

أنت الآن تعرف **كيفية تصدير LaTeX** من مستندات Word باستخدام Aspose.Words، وكيفية **تحويل docx إلى markdown**، وكيفية **حفظ Word كـ markdown**، وكيفية **حفظ docx كـ txt** مع الحفاظ على كل معادلة. الفكرة الأساسية هي خاصية `OfficeMathExportMode`—حددها إلى `LaTeX` وستقوم المكتبة بالعمل الشاق نيابةً عنك.

ما الخطوة التالية؟ جرّب تبديل وضع التصدير إلى MathML، جرب خيارات معالجة الصور، أو دمج هذه المنطق في خط أنابيب CI يولد الوثائق تلقائيًا من ملفات `.docx` المصدرية. الاحتمالات لا حصر لها، والكود الذي كتبته الآن هو أساس قوي.

برمجة سعيدة، ولتظهر معادلاتك دائمًا بشكل مثالي!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}