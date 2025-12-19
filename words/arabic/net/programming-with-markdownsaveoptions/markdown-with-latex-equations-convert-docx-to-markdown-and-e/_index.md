---
category: general
date: 2025-12-19
description: دليل ماركداون مع معادلات لايتكس – تعلم كيفية تحويل ملف docx إلى ماركداون،
  وتصدير المعادلات إلى لايتكس، وحفظ الصور في مجلد بأسماء فريدة باستخدام Aspose.Words
  في C#.
draft: false
keywords:
- markdown with latex equations
- convert docx to markdown
- save images to folder
- export equations to latex
- generate unique image names
language: ar
og_description: يظهر دليل الماركداون مع معادلات لايتكس كيفية تحويل ملف docx إلى ماركداون،
  وتصدير المعادلات إلى لايتكس، وإنشاء أسماء صور فريدة للصور المحفوظة.
og_title: ماركداون مع معادلات لايتكس – دليل التحويل الكامل لـ C#
tags:
- Aspose.Words
- C#
- Markdown
- LaTeX
title: 'ماركداون مع معادلات لاتكس: تحويل DOCX إلى ماركداون وتصدير الصور'
url: /ar/net/programming-with-markdownsaveoptions/markdown-with-latex-equations-convert-docx-to-markdown-and-e/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown مع معادلات latex: تحويل DOCX إلى Markdown وتصدير الصور

هل احتجت يومًا إلى **markdown مع معادلات latex** لكن لم تكن متأكدًا من كيفية استخراجها من ملف Word؟ لست وحدك—العديد من المطورين يواجهون هذه المشكلة عند نقل الوثائق من Office إلى مولدات المواقع الثابتة.  

في هذا الدرس سنستعرض حلًا كاملاً من البداية إلى النهاية **يحول docx إلى markdown**، **يصدر المعادلات إلى latex**، و**يحفظ الصور في مجلد** مع منطق **إنشاء أسماء صور فريدة**، كل ذلك باستخدام Aspose.Words for .NET.  

بنهاية الدرس ستحصل على برنامج C# جاهز للتنفيذ ينتج ملفات Markdown نظيفة، رياضيات جاهزة للـ LaTeX، ودليل صور منظم—دون الحاجة إلى النسخ واللصق يدويًا.

## ما ستحتاجه

- .NET 6 (أو أي بيئة تشغيل .NET حديثة)  
- Aspose.Words for .NET 23.10 أو أحدث (حزمة NuGet `Aspose.Words`)  
- عينة `input.docx` تحتوي على نص عادي، كائنات Office Math، وبعض الصور  
- بيئة تطوير تحبها (Visual Studio، Rider، أو VS Code)  

هذا كل شيء. لا مكتبات إضافية، ولا أدوات سطر أوامر معقدة—فقط C# نقي.

## الخطوة 1: تحميل المستند بأمان (وضع الاسترداد)

عند التعامل مع ملفات قد تم تحريرها من قبل عدة أشخاص، يكون الفساد خطرًا حقيقيًا. يتيح لك Aspose.Words تمكين *RecoveryMode* بحيث يحاول المحمل إصلاح الأجزاء المكسورة بدلاً من إلقاء استثناء.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // Load the document with recovery mode – this handles possible corruption.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);
```

**لماذا هذا مهم:**  
إذا كان الملف المصدر يحتوي على عقد XML غريبة أو تدفق صورة مكسور، سيظل وضع الاسترداد يمنحك كائن `Document` قابل للاستخدام. تخطي هذه الخطوة قد يسبب تعطلًا حادًا، خاصةً في خطوط أنابيب CI حيث لا تتحكم في كل عملية رفع.

> **نصيحة احترافية:** عند معالجة دفعات، غلف عملية التحميل داخل `try/catch` وسجّل أي `DocumentCorruptedException` للمراجعة لاحقًا.

## الخطوة 2: تحويل DOCX إلى Markdown مع معادلات LaTeX

الآن يأتي جوهر الدرس: نريد **markdown مع معادلات latex**. يتيح لك `MarkdownSaveOptions` في Aspose.Words تحديد `OfficeMathExportMode.LaTeX`، والذي يحول كل كائن Office Math إلى سلسلة LaTeX محاطة بـ `$…$` أو `$$…$$`.

```csharp
        // Export Office Math equations to LaTeX while saving as Markdown.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);
```

الملف الناتج `output_math.md` سيظهر شيئًا مثل:

```markdown
Here is an inline equation $E = mc^2$ inside a sentence.

And a displayed equation:

$$
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
$$
```

**لماذا قد ترغب في ذلك:**  
معظم مولدات المواقع الثابتة (Hugo, Jekyll, MkDocs) تفهم بالفعل محددات LaTeX عندما تقوم بتمكين إضافة MathJax أو KaTeX. من خلال التصدير مباشرة إلى LaTeX تتجنب خطوة ما بعد المعالجة التي قد تتطلب حيل regex.

### حالات الحافة

- **معادلات معقدة:** الهياكل المتداخلة بعمق لا تزال تُعرض بشكل صحيح، لكن قد تحتاج إلى زيادة حد الذاكرة لـ `MathRenderer` إذا واجهت `OutOfMemoryException`.  
- **محتوى مختلط:** إذا كان الفقرة تمزج بين نص عادي ومعادلة، يقوم Aspose.Words تلقائيًا بتقسيمهما، مع الحفاظ على الـ markdown المحيط.

## الخطوة 3: حفظ الصور في مجلد بأسماء فريدة

إذا كان مستند Word يحتوي على صور، ربما تريدها كملفات صورة منفصلة يمكن للـ markdown الإشارة إليها. يتيح لك `ResourceSavingCallback` على `MarkdownSaveOptions` التحكم الكامل في كيفية كتابة كل صورة.

```csharp
        // Customize image handling during Markdown export.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                // Generate a unique file name for each image.
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);

                // Ensure the Images folder exists.
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);

                // Save the image to the file system.
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);
```

**كيف يبدو الـ markdown الآن:**  

```markdown
![Image description](Images/img_3f9c2a1e-7b5d-4c8f-9d6e-2b5c7a9e1f0a.png)
```

**لماذا إنشاء أسماء فريدة؟**  
إذا ظهرت الصورة نفسها عدة مرات، فإن استخدام الاسم الأصلي سيتسبب في استبدال الملفات. تضمن الأسماء المستندة إلى GUID أن كل ملف فريد، وهو مفيد خاصةً عند تشغيل التحويل في وظائف متوازية.

### نصائح وملاحظات

- **الأداء:** إنشاء GUID لكل صورة يضيف عبءً ضئيلًا، لكن إذا عالجت آلاف الصور يمكنك التحول إلى تجزئة حتمية (مثل SHA‑256 لبايتات الصورة).  
- **تنسيق الملف:** `resource.Save` يحفظ الصورة بالتنسيق الأصلي. إذا كنت بحاجة إلى جميع PNGs، استبدل `resource.Save(imageFile);` بـ `resource.Save(imageFile, ImageSaveOptions.CreateSaveOptions(SaveFormat.Png));`.

## الخطوة 4: تصدير PDF مع أشكال داخلية (اختياري)

أحيانًا لا يزال هناك حاجة إلى نسخة PDF من نفس المستند، ربما للمراجعة القانونية. يضمن تعيين `ExportFloatingShapesAsInlineTag` إبقاء الكائنات العائمة (مثل مربعات النص) في PDF كعلامات داخلية، مما يحافظ على دقة التخطيط.

```csharp
        // Save the document as PDF, exporting floating shapes as inline tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

يمكنك تخطي هذه الخطوة إذا لم يكن إخراج PDF جزءًا من سير عملك—لن يحدث أي عطل إذا حذفتها.

## مثال كامل يعمل (جميع الخطوات مجتمعة)

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في تطبيق console. تذكر استبدال `YOUR_DIRECTORY` بمسار فعلي مطلق أو نسبي.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // 1️⃣ Load with recovery mode.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);

        // 2️⃣ Export markdown with LaTeX equations.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);

        // 3️⃣ Save images to a folder, using unique GUID names.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);

        // 4️⃣ (Optional) Export PDF with inline shape tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

تشغيل هذا البرنامج ينتج ثلاثة ملفات:

| الملف | الغرض |
|------|---------|
| `output_math.md` | Markdown يحتوي على معادلات جاهزة للـ LaTeX |
| `output_images.md` | Markdown مع روابط صور تشير إلى PNGs بأسماء فريدة |
| `output_shapes.pdf` | نسخة PDF تحافظ على الأشكال العائمة كعلامات داخلية (اختياري) |

## الخلاصة

أنت الآن تمتلك خط أنابيب **markdown مع معادلات latex** يقوم **بتحويل docx إلى markdown**، **بتصدير المعادلات إلى latex**، و**بحفظ الصور في مجلد** مع **إنشاء أسماء صور فريدة** لكل صورة. النهج مكتمل ذاتيًا، يعمل مع أي مشروع .NET حديث، ويتطلب فقط حزمة NuGet الخاصة بـ Aspose.Words.

ما الخطوة التالية؟ جرّب إدخال الـ markdown المُولد في مولد موقع ثابت مثل Hugo، فعّل MathJax، وشاهد وثائقك تتحول من تنسيق Office مغلق إلى موقع ويب جميل وجاهز. هل تحتاج جداول؟ يدعم Aspose.Words أيضًا `MarkdownSaveOptions.ExportTableAsHtml`، بحيث يمكنك الحفاظ على التخطيطات المعقدة.

If

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}