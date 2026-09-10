---
category: general
date: 2026-02-10
description: تعلم كيفية تضمين الصور أثناء تحويل DOCX إلى Markdown، بالإضافة إلى نصائح
  للمعادلات وإخراج عالي الدقة.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- export word to markdown
- how to convert equations
- save word as markdown
language: ar
og_description: كيفية تضمين الصور عند تحويل ملف DOCX إلى Markdown، مع صور عالية الدقة
  وتصدير معادلات LaTeX.
og_title: كيفية تضمين الصور في ماركداون من DOCX – دليل كامل
tags:
- Aspose.Words
- C#
- Document conversion
title: كيفية تضمين الصور في ماركداون من DOCX
url: /ar/net/programming-with-markdownsaveoptions/how-to-embed-images-in-markdown-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تضمين الصور في Markdown من DOCX

هل تساءلت يومًا **كيف يتم تضمين الصور** أثناء تحويل ملف Word إلى مستند Markdown نظيف؟ لست وحدك—المطورون يواجهون دائمًا مشكلة فقدان الصور أو ظهورها غير واضحة بعد التحويل. الخبر السار؟ ببضع أسطر من C# يمكنك الحفاظ على كل صورة بوضوح، وتصدير الرياضيات كـ LaTeX، والحصول على ملف `.md` جاهز للنشر.

في هذا الدرس سنتطرق أيضًا إلى **convert docx to markdown**، **export word to markdown**، وحتى **how to convert equations** حتى تتمكن من **save word as markdown** دون التضحية بالجودة. في النهاية ستحصل على مثال مكتمل، قابل للتنفيذ، يمكنك لصقه مباشرة في مشروعك.

---

## ما ستحتاجه

- **Aspose.Words for .NET** (الإصدار 23.9 أو أحدث). إنها مكتبة تجارية، لكن يمكنك الحصول على نسخة تجريبية مجانية لمدة 30 يومًا من موقع Aspose.  
- بيئة تطوير .NET (Visual Studio، Rider، أو VS Code مع امتداد C#).  
- مستند Word إدخالي (`input.docx`) يحتوي على صورة واحدة على الأقل وبعض المعادلات.  

هذا كل ما تحتاجه—لا حزم NuGet إضافية، ولا محولات خارجية. المكتبة تتولى كل الأعمال الثقيلة.

---

## تحويل خطوة بخطوة

فيما يلي نقسم العملية إلى خطوات صغيرة. كل عنوان يحتوي على كلمة مفتاحية لتلبية محركات البحث ومساعدي الذكاء الاصطناعي.

### ## كيفية تضمين الصور أثناء تحويل DOCX إلى Markdown

أول شيء عليك فعله هو إخبار Aspose.Words بمكان الملف المصدر.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Step 1: Load the source document
Document doc = new Document(@"C:\Docs\input.docx");
```

*لماذا هذا مهم*: تحميل المستند يُنشئ تمثيلًا في الذاكرة لكل فقرة، صورة، ومعادلة. إذا تخطيت هذه الخطوة، لن يكون هناك شيء للتحويل، وبالتالي لا صور لتضمينها.

> **نصيحة احترافية**: استخدم مسارًا مطلقًا أثناء الاختبار، ثم انتقل إلى مسار نسبي (مثال: `Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "input.docx")`) للإنتاج.

### ## Convert docx to markdown with high‑resolution images

الآن نقوم بتهيئة `MarkdownSaveOptions`. هنا تتحكم في DPI الصورة ووضع تصدير الرياضيات.

```csharp
// Step 2: Configure Markdown save options
MarkdownSaveOptions mdSave = new MarkdownSaveOptions
{
    // 300 DPI gives you print‑ready quality while still keeping file size reasonable
    ImageResolution = 300,

    // Export equations as LaTeX so they render nicely on GitHub, GitLab, or static site generators
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Uncomment the line below if you prefer Base64‑embedded images (makes the .md file self‑contained)
    // ExportImagesAsBase64 = true,
};
```

*لماذا هذا مهم*: `ImageResolution` يحدد كيف تُحفظ الصور النقطية. الإعداد الافتراضي (96 DPI) غالبًا ما يبدو ضبابيًا على شاشات Retina. ضبطه إلى **300 DPI** يحافظ على التفاصيل دون زيادة حجم الملف بشكل كبير. `OfficeMathExportMode.LaTeX` يضمن تحويل أي معادلة Word إلى كود LaTeX نظيف، وهو ما تفهمه معظم عارضات Markdown.

### ## Export word to markdown and verify the output

أخيرًا، اكتب ملف Markdown إلى القرص.

```csharp
// Step 3: Save the document as Markdown
string outputPath = @"C:\Docs\HighRes.md";
doc.Save(outputPath, mdSave);
Console.WriteLine($"✅ Document saved to {outputPath}");
```

*لماذا هذا مهم*: طريقة `Save` تُطبق كل الخيارات التي حددناها مسبقًا. بعد هذه العملية ستجد ملف `.md` حيث كل وسم صورة يبدو هكذا:

```markdown
![Image 1](HighRes.md_files/Image_0.png)
```

إذا فعلت `ExportImagesAsBase64`، سيحتوي الوسم بدلاً من ذلك على سلسلة طويلة من الشكل `data:image/png;base64,…`، مما يجعل ملف Markdown قابلًا للنقل.

---

## كيفية تحويل المعادلات دون فقدان الدقة

المعادلات غالبًا ما تكون الجزء الأصعب في سير عمل تحويل Word إلى Markdown. تقدم Aspose.Words وضعين للتصدير:

| الوضع | النتيجة | متى تستخدم |
|------|--------|-------------|
| **LaTeX** (`OfficeMathExportMode.LaTeX`) | صيغة LaTeX صافية (`\frac{a}{b}`) | عندما تعرض Markdown على منصات تدعم MathJax أو KaTeX. |
| **Image** (`OfficeMathExportMode.Image`) | صورة PNG مدمجة كأي صورة أخرى | عندما لا يدعم العارض المستهدف الرياضيات (مثال: README عادي على GitHub). |

إذا كنت بحاجة إلى **كلاهما**—LaTeX للمشاهدين الحديثين *و* صورة احتياطية للأدوات القديمة—يمكنك تشغيل التحويل مرتين، كل مرة باستخدام `OfficeMathExportMode` مختلف، ثم دمج النتائج يدويًا. قد يتطلب ذلك جهدًا إضافيًا، لكنه يضمن أقصى توافق.

---

## Save word as markdown – معالجة الحالات الخاصة

### صور كبيرة

عندما يتجاوز حجم الصورة 5 MB، قد ينتج `ImageResolution` الافتراضي صورة PNG ضخمة. للحفاظ على حجم الملف، يمكنك تقليل الدقة بشكل انتقائي:

```csharp
if (new FileInfo(@"C:\Docs\input.docx").Length > 10_000_000) // >10 MB DOCX
{
    mdSave.ImageResolution = 150; // half the DPI for huge docs
}
```

### خطوط مفقودة

إذا كان ملف Word يستخدم خطًا مخصصًا غير مثبت على الخادم، قد تبدو الصورة النقطية غير صحيحة. الحل الأكثر أمانًا هو **تضمين الخط** في DOCX قبل التحويل (File → Options → Save → Embed fonts) أو تثبيت الخط مسبقًا على الجهاز الذي يشغل الكود.

### Base64 مقابل الملفات الخارجية

تضمين الصور كـ Base64 يجعل ملف Markdown وحدة واحدة قابلة للمشاركة—مفيد للبريد الإلكتروني أو العروض السريعة. ومع ذلك، قد يزداد حجم الملف (صورة PNG بحجم 200 KB تصبح ~270 KB في Base64). إذا كنت تخطط لإيداع Markdown في مستودع Git، يُفضَّل استخدام ملفات صور خارجية للحصول على اختلافات (diffs) أنظف.

---

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه في تطبيق Console. يتضمن جميع الفحوص الاختيارية التي نوقشت أعلاه.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // ---- Configuration -------------------------------------------------
        string inputPath  = @"C:\Docs\input.docx";
        string outputPath = @"C:\Docs\HighRes.md";

        // Verify the source file exists
        if (!File.Exists(inputPath))
        {
            Console.Error.WriteLine($"❌ Input file not found: {inputPath}");
            return;
        }

        // Load the Word document
        Document doc = new Document(inputPath);

        // Set up save options
        MarkdownSaveOptions mdSave = new MarkdownSaveOptions
        {
            ImageResolution = 300,
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            // ExportImagesAsBase64 = true, // uncomment for a single‑file .md
        };

        // Adjust DPI for very large source files
        if (new FileInfo(inputPath).Length > 10_000_000) // >10 MB
        {
            mdSave.ImageResolution = 150;
            Console.WriteLine("🔧 Large DOCX detected – reducing image DPI to 150.");
        }

        // Perform the conversion
        doc.Save(outputPath, mdSave);
        Console.WriteLine($"✅ Markdown saved to: {outputPath}");

        // Quick verification: list generated images
        string imageFolder = Path.Combine(Path.GetDirectoryName(outputPath) ?? "", Path.GetFileNameWithoutExtension(outputPath) + "_files");
        if (Directory.Exists(imageFolder))
        {
            Console.WriteLine("🖼️ Images generated:");
            foreach (var img in Directory.GetFiles(imageFolder))
                Console.WriteLine($"   - {Path.GetFileName(img)}");
        }
    }
}
```

**النتيجة المتوقعة**: بعد تشغيل البرنامج، ستجد `HighRes.md` بجانب مجلد `HighRes_files` يحتوي على كل صورة بصيغة PNG (أو سلسلة Base64 واحدة إذا فعلت هذا الخيار). جميع المعادلات تظهر ككتل LaTeX مثل:

```markdown
$$
\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
$$
```

افتح ملف `.md` في VS Code، أو معاينة GitHub، أو أي عارض Markdown يدعم MathJax وسترى نسخة مطابقة للأصل من مستند Word.

---

## الخلاصة

لقد استعرضنا **كيفية تضمين الصور** عندما **تحول docx إلى markdown**، مع تغطية جميع إعدادات DPI وتصدير معادلات LaTeX. البرنامج الصغير أعلاه يتيح لك **export word to markdown** بخطوة واحدة، مع تحكم كامل في جودة الصور وتنسيق المعادلات.  

إذا كنت مستعدًا للخطوة التالية، فكر في:

- **Saving Word as Markdown** مع CSS مخصص للتنسيق.  
- أتمتة العملية لمجموعة ملفات باستخدام `Directory.GetFiles`.  
- إضافة وسيط سطر أوامر لتبديل تضمين Base64 في الوقت الفعلي.  

جرّبه، عدّل الخيارات، ودع مستندات Markdown تبدو مصقولة كما هي ملفات Word الأصلية. لديك أسئلة أو حالة خاصة؟ اترك تعليقًا—برمجة سعيدة!  

![مثال على كيفية تضمين الصور](placeholder-image.png)   <!-- alt text includes primary keyword -->

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}