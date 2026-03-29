---
category: general
date: 2026-03-28
description: احفظ ملف docx كـ markdown بسرعة باستخدام Aspose.Words. تعلّم كيفية تحويل Word
  إلى markdown، استخراج الصور من Word، وتصدير docx كـ markdown مع الكود الكامل.
draft: false
keywords:
- save docx as markdown
- convert word to markdown
- extract images from word
- export docx as markdown
- aspose convert docx markdown
language: ar
og_description: احفظ ملف docx كـ markdown باستخدام Aspose.Words. يوضح هذا الدليل كيفية
  تحويل Word إلى markdown، واستخراج الصور من Word، وتصدير ملف docx كـ markdown في
  بضع أسطر من الشيفرة.
og_title: حفظ ملف docx كـ markdown – دليل C# خطوة بخطوة
tags:
- Aspose.Words
- C#
- Markdown
- Document Conversion
title: حفظ ملف docx كـ markdown – دليل C# الكامل مع Aspose.Words
url: /ar/net/programming-with-markdownsaveoptions/save-docx-as-markdown-complete-c-guide-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ docx كـ markdown – دليل C# الكامل مع Aspose.Words

هل احتجت يوماً إلى **save docx as markdown** لكنك لم تكن متأكدًا أي مكتبة يمكنها القيام بذلك دون الكثير من التلاعب اليدوي؟ لست وحدك. في العديد من المشاريع نحتاج إلى تحويل تقرير Word إلى ملف Markdown خفيف، مع الحفاظ على الصور، وإبقاء التخطيط الأصلي. الخبر السار؟ باستخدام Aspose.Words يمكنك **convert word to markdown**، استخراج كل صورة من المستند، و**export docx as markdown** في عملية واحدة مرتبة.

في هذا الدرس سنستعرض مثالًا مستقلًا يوضح بالضبط كيفية **save docx as markdown** باستخدام C#. ستشاهد الكود، تفهم لماذا كل جزء مهم، وتحصل على نصائح للتعامل مع الحالات الخاصة مثل أسماء الصور المتكررة. في النهاية ستتمكن من إدراج المقتطف في أي مشروع .NET والبدء في تحويل ملفات Word إلى Markdown فورًا. لا سكربتات خارجية، لا تبعيات إضافية—فقط Aspose.Words وبعض أسطر C#.

## المتطلبات السابقة

قبل أن نبدأ، تأكد من وجود ما يلي:

* .NET 6 (أو أي نسخة حديثة من .NET) مثبتة.
* رخصة صالحة لـ Aspose.Words for .NET أو مفتاح تقييم مجاني.
* ملف `input.docx` بسيط تريد تحويله إلى Markdown.
* Visual Studio 2022 أو محرّكك المفضّل.

هذا كل شيء—لا حزم NuGet إضافية بخلاف `Aspose.Words`. إذا كنت تستخدم Aspose.Words بالفعل في حلّك، ستلاحظ نفس الكائنات والأنماط، ما يبقي منحنى التعلم مسطحًا.

## الخطوة 1 – تحميل مستند Word الذي تريد تحويله

أول شيء تقوم به هو إنشاء نسخة من `Document` تشير إلى ملف المصدر. فكر في ذلك كفتح كتاب لتتمكن من قراءة كل فصل، فقرة، وصورة.

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source DOCX file.
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

**لماذا هذا مهم:**  
`Document` هو الصنف المركزي في Aspose.Words. فهو يحلل حزمة DOCX، يبني نموذج كائنات في الذاكرة، ويمنحك الوصول إلى كل شيء—من مقاطع النص إلى المخططات المدمجة. إذا تعذر العثور على الملف، سيطرح Aspose استثناء `FileNotFoundException`، لذا تحقق من المسار أو استخدم `Path.Combine` للسلامة.

> **نصيحة احترافية:** عند التعامل مع ملفات Word الكبيرة، فكر في استخدام `LoadOptions` لتقليل استهلاك الذاكرة (مثال: `LoadOptions.LoadFormat = LoadFormat.Docx`).

## الخطوة 2 – إخبار Aspose بكيفية التعامل مع الموارد الخارجية (الصور، المخططات، إلخ)

عند التصدير إلى Markdown، تُحفظ كل صورة كملف منفصل. بشكل افتراضي يكتب Aspose هذه الصور بجوار ملف `.md`، لكننا عادةً نرغب في مجلد `assets` منظم. `MarkdownSaveOptions.ResourceSavingCallback` يمنحنا التحكم الكامل.

```csharp
// Configure Markdown save options.
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This callback runs for each external resource (image, chart, etc.).
    ResourceSavingCallback = (sender, args) =>
    {
        // Determine the assets folder path and ensure it exists.
        string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
        Directory.CreateDirectory(assetsFolder);

        // Build a unique filename to avoid collisions.
        string uniqueName = Path.GetFileNameWithoutExtension(args.FileName) +
                            "_" + Guid.NewGuid().ToString("N") +
                            Path.GetExtension(args.FileName);

        // Save the resource inside the assets folder.
        args.FileName = Path.Combine(assetsFolder, uniqueName);
    }
};
```

**لماذا هذا مهم:**  
بدون رد نداء (callback)، سيُسقط Aspose الصور مباشرةً بجانب `output.md`، مما يملأ جذر المشروع. يتيح لك الرد النّادي أيضًا **extract images from word** وإعادة تسميتها بأمان—مثالي لأنابيب CI التي تُجري تحويلات متعددة بالتوازي. يضمن الـ GUID أن كل صورة تحصل على اسم فريد، مما يمنع الكتابة فوق ملفات عندما تشترك صورتان في نفس اسم الملف الأصلي.

> **احذر:** إذا كنت تخطط لاستضافة Markdown على موقع ثابت، تأكد من أن مسار `assets` يتطابق مع مخطط URL النسبي للموقع (مثال: `./assets/`).

## الخطوة 3 – حفظ المستند كـ Markdown

الآن تم إنجاز الجزء الأكبر. سطر واحد يحفظ كل شيء: النص، العناوين، الجداول، والموارد الخارجية التي وجهتها إلى مجلد `assets`.

```csharp
// Save the document as Markdown using the configured options.
string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");
doc.Save(outputPath, markdownOptions);
```

**ما ستراه:**  
* `output.md` – ملف Markdown بصياغة قياسية (`#` للعناوين، `![alt](assets/…)` للصور).  
* `YOUR_DIRECTORY/assets/` – مجلد يحتوي على كل صورة، مخطط، أو SVG كان موجودًا في DOCX الأصلي.

إذا فتحت `output.md` في عارض Markdown، يجب أن ترى نفس البنية البصرية كما في ملف Word الأصلي، باستثناء الميزات الخاصة بـ Word مثل التغييرات المتعقّبة. ستُعرض الصور تلقائيًا من مجلد `assets`.

## الخطوة 4 – التحقق من التحويل (اختياري لكن مُستحب)

من الجيد دائمًا التأكد من أن كل شيء وصل إلى المكان المتوقع. يمكن أن يكون اختبار بسيط كقراءة ملف Markdown المُولد والتأكد من أن كل مرجع صورة يشير إلى ملف موجود.

```csharp
// Simple verification script.
string markdownContent = File.ReadAllText(outputPath);
foreach (Match match in Regex.Matches(markdownContent, @"!\[.*?\]\((.*?)\)"))
{
    string imagePath = Path.GetFullPath(Path.Combine("YOUR_DIRECTORY", match.Groups[1].Value));
    Console.WriteLine(File.Exists(imagePath)
        ? $"✅ Image found: {imagePath}"
        : $"❌ Missing image: {imagePath}");
}
```

**لماذا تُجري هذا؟**  
عند معالجة عشرات ملفات DOCX دفعةً واحدة، قد تتسبب صورة مفقودة في تعطل موقع توثيقي أو مدونة ثابتة. هذه الحلقة الصغيرة تعطيك تغذية راجعة فورية ويمكن دمجها في اختبارات آلية.

## الخطوة 5 – تنويعات شائعة وتعامل مع الحالات الطرفية

### أ) الحفاظ على أسماء الصور الأصلية

إذا كنت تفضّل الأسماء الأصلية بدلاً من GUIDs، فقط احذف منطق `uniqueName` واستخدم `args.FileName` مباشرة. تذكّر فقط معالجة التصادمات المحتملة بنفسك.

### ب) تحويل جزء فقط من المستند

يتيح لك Aspose استنساخ أقسام أو صفحات قبل الحفظ. مثال على تصدير أول ثلاثة أقسام فقط:

```csharp
Document part = doc.ExtractPages(0, 3);
part.Save("partial.md", markdownOptions);
```

### ج) ضبط جودة الصورة

يمكنك اعتراض `ImageSavingCallback` (شقيق `ResourceSavingCallback`) لتقليل حجم PNG الكبيرة أو تغيير الصيغة إلى JPEG، مما يقلل حجم حزمة Markdown.

```csharp
markdownOptions.ImageSavingCallback = (s, e) =>
{
    // Example: convert all PNGs to JPEG with 80% quality.
    if (e.ImageFormat == ImageSaveOptions.SaveFormat.Png)
    {
        e.ImageFormat = ImageSaveOptions.SaveFormat.Jpeg;
        e.JpegQuality = 80;
    }
};
```

### د) استخدام مجلد إخراج مختلف

ما عليك سوى تغيير المتغيّر `assetsFolder` إلى أي مسار تريده—ربما دلو CDN أو دليل مؤقت. نمط الرد النّادي نفسه يعمل في أي مكان.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في تطبيق Console. يتضمن جميع الخطوات، معالجة الأخطاء، والتحقق الاختياري.

```csharp
using System;
using System.IO;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1️⃣ Load the source DOCX.
        // -----------------------------------------------------------------
        string baseDir = @"YOUR_DIRECTORY";               // ← change this
        string inputPath = Path.Combine(baseDir, "input.docx");
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // 2️⃣ Configure Markdown options and resource callback.
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (sender, args) =>
            {
                string assetsFolder = Path.Combine(baseDir, "assets");
                Directory.CreateDirectory(assetsFolder);

                // Ensure unique filenames.
                string uniqueName = Path.GetFileNameWithoutExtension(args.FileName) +
                                    "_" + Guid.NewGuid().ToString("N") +
                                    Path.GetExtension(args.FileName);
                args.FileName = Path.Combine(assetsFolder, uniqueName);
            }
        };

        // -----------------------------------------------------------------
        // 3️⃣ Save as Markdown.
        // -----------------------------------------------------------------
        string outputMd = Path.Combine(baseDir, "output.md");
        doc.Save(outputMd, mdOptions);
        Console.WriteLine($"✅ Markdown saved to: {outputMd}");

        // -----------------------------------------------------------------
        // 4️⃣ Verify that every referenced image exists.
        // -----------------------------------------------------------------
        VerifyImages(outputMd, baseDir);
    }

    static void VerifyImages(string markdownPath, string rootDir)
    {
        string content = File.ReadAllText(markdownPath);
        var matches = Regex.Matches(content, @"!\[.*?\]\((.*?)\)");
        foreach (Match m in matches)
        {
            string relPath = m.Groups[1].Value;
            string fullPath = Path.GetFullPath(Path.Combine(rootDir, relPath));
            Console.WriteLine(File.Exists(fullPath)
                ? $"✅ Image found: {fullPath}"
                : $"❌ Missing image: {fullPath}");
        }
    }
}
```

**النتيجة المتوقعة:**  
تشغيل البرنامج يُنشئ `output.md` ومجلد `assets` مملوء بملفات صور مثل `image_0a1b2c3d4e5f6g7h8i9j.png`. فتح `output.md` في معاينة Markdown في VS Code يُظهر العناوين، القوائم النقطية، والصور تمامًا كما ظهرت في مستند Word الأصلي.

---

![Diagram showing the flow from input.docx to output.md and assets folder – save docx as markdown example](assets/flow-diagram.png "مثال حفظ docx كـ markdown")

*نص بديل للصورة:* **save docx as markdown** – تمثيل بصري لسلسلة التحويل.

## الخلاصة

الآن لديك نمط مُختبر للمعركة **save docx as markdown** باستخدام Aspose.Words، مع رد نادى يُـ **extract images from word** ويخزنها في دليل `assets` نظيف. سواء كنت تبني مولّد توثيق، أنابيب موقع ثابت، أو فقط تحتاج إلى أرشفة تقارير بصيغة Markdown خفيفة، فإن هذا النهج يتوسع بسهولة.

تذكّر، يمكنك **convert word to markdown** لمجلدات كاملة، تعديل الرد النّادي لإعادة تسمية الملفات كما تشاء، أو حتى استبدال

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}