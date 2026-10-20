---
category: general
date: 2026-03-22
description: احفظ مستند Word كملف Markdown بسرعة باستخدام Aspose.Words. تعلّم كيفية
  تحويل Word إلى Markdown، استخراج الصور من ملف docx وتصدير الصور من Word باستخدام
  C#.
draft: false
keywords:
- save word as markdown
- convert word to markdown
- extract images from docx
- export images from word
language: ar
og_description: احفظ مستند Word كملف Markdown باستخدام Aspose.Words. يوضح هذا الدرس
  كيفية تحويل Word إلى Markdown، واستخراج الصور من ملف docx وتصدير الصور من Word.
og_title: حفظ ملف Word كـ Markdown – دليل التحويل خطوة بخطوة
tags:
- Aspose.Words
- C#
- Markdown
title: حفظ Word كـ Markdown – دليل شامل لتحويل Word إلى Markdown واستخراج الصور
url: /ar/net/programming-with-markdownsaveoptions/save-word-as-markdown-complete-guide-to-convert-word-to-mark/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ Word كـ Markdown – دليل كامل

هل احتجت يومًا إلى **save Word as markdown** لكن لم تكن متأكدًا من أين تبدأ؟ لست وحدك—المطورون يسألون باستمرار كيف **convert Word to markdown** مع الحفاظ على كل صورة مدمجة سليمة. الخبر السار هو أن Aspose.Words يجعل العملية بأكملها سهلة، ويمكنك أيضًا **extract images from docx** دون كتابة محلل مخصص. في هذا الدرس سنستعرض مثال C# جاهز للتنفيذ يقوم بذلك بالضبط ويظهر لك أيضًا كيف **export images from word** إلى مجلد منظم.

سنتناول كل ما تحتاج معرفته: تثبيت المكتبة، ربط callback لحفظ الموارد، تحميل ملف .docx، وأخيرًا كتابة ملف .md بالإضافة إلى مجموعة من ملفات الصور. في النهاية ستحصل على أمر واحد يحول أي مستند Word إلى markdown نظيف ومجموعة من أصول الصور التي يمكنك إعادة استخدامها في أي مكان.

---

## ما ستحتاجه

- **.NET 6** (أو أي بيئة تشغيل .NET حديثة) – الكود يُترجم مع .NET 5+ أيضًا.  
- **Aspose.Words for .NET** – يمكنك الحصول على نسخة تجريبية مجانية من موقع Aspose أو استخدام حزمة NuGet: `Install-Package Aspose.Words`.  
- **sample .docx** يحتوي على صورة واحدة على الأقل (حتى نتمكن من إثبات أن استخراج الصور يعمل).  
- بيئة تطوير متكاملة (IDE) أو محرر تشعر بالراحة في استخدامه (Visual Studio, Rider, VS Code…).  

لا توجد أدوات طرف ثالث أخرى مطلوبة؛ كل شيء يعمل داخل العملية.

## الخطوة 1: إنشاء معالج حفظ الموارد (Extract Images from DOCX)

عند حفظ Aspose.Words لمستند كـ markdown، يقوم ببث كل صورة مدمجة عبر callback. من خلال تنفيذ `IResourceSavingCallback` نحدد أين تُحفظ تلك الصور على القرص. المعالج أدناه ينشئ مجلد `Images`، ويعطي كل صورة اسمًا فريدًا، ويحدّث مرجع markdown وفقًا لذلك.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

/// <summary>
/// Handles image resources while saving a document as markdown.
/// </summary>
class MyMarkdownResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Ensure the Images folder exists
        string imageFolder = "Images";
        Directory.CreateDirectory(imageFolder);

        // 2️⃣ Build a unique filename (helps when the source doc has duplicate names)
        string uniqueFileName = Guid.NewGuid().ToString() + Path.GetExtension(args.FileName);
        string imagePath = Path.Combine(imageFolder, uniqueFileName);

        // 3️⃣ Write the image stream to disk
        using (FileStream fs = new FileStream(imagePath, FileMode.Create))
        {
            args.Stream.CopyTo(fs);
        }

        // 4️⃣ Tell Aspose to reference the new filename in the markdown output
        args.FileName = uniqueFileName;
        args.Stream = null; // we already saved the file, no need for Aspose to keep the stream open
    }
}
```

**لماذا هذا مهم:**  
بدون callback، سيقوم Aspose بدمج الصور كسلاسل base‑64 أو يضعها في نفس المجلد بأسمائها الأصلية، مما قد يسبب تصادمات. من خلال التحكم في موقع الحفظ، نتمكن فعليًا من **export images from word** والحفاظ على نظافة markdown.

## الخطوة 2: تحميل المستند المصدر (Convert Word to Markdown)

الآن بعد أن أصبح المعالج جاهزًا، نحتاج إلى فتح ملف .docx الذي نريد تحويله. فئة `Document` تتعامل مع أي تعقيدات في تنسيق الملف، لذا يمكنك تمرير `.docx` أو `.rtf` أو حتى PDF إذا كان لديك الترخيص المناسب.

```csharp
// Adjust the path to point at your actual .docx file
string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

// Load the Word file into Aspose.Words
Document doc = new Document(inputPath);
```

**نصيحة:** إذا كان المستند كبيرًا، فكر في استخدام `LoadOptions` لتقليل استهلاك الذاكرة، لكن بالنسبة لمعظم الملفات اليومية يكون المحمل الافتراضي مناسبًا تمامًا.

## الخطوة 3: تكوين خيارات حفظ Markdown (Save Word as Markdown)

هنا نجمع كل شيء معًا. `MarkdownSaveOptions` يتيح لنا ربط الـ callback الذي كتبناه سابقًا، ويمكننا أيضًا تعديل بعض علامات التنسيق (مثل استخدام markdown بنكهة GitHub).

```csharp
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Use the custom handler to dump images into the Images folder
    ResourceSavingCallback = new MyMarkdownResourceHandler(),

    // Optional: generate GitHub‑compatible markdown (tables, code fences, etc.)
    ExportImagesAsBase64 = false,
    ExportHeadersFooters = false,
    ExportDocumentProperties = false,
    UseGitHubFlavor = true
};
```

**ما يحدث:**  
`ExportImagesAsBase64 = false` يخبر Aspose بالإشارة إلى الصور كملفات خارجية—وهو ما نحتاجه لملف markdown نظيف. العلامات الأخرى تحافظ على تركيز الإخراج على محتوى النص الرئيسي.

## الخطوة 4: حفظ المستند كـ Markdown والتحقق من النتيجة

أخيرًا، نطلب من Aspose كتابة ملف markdown. جميع الصور ستحفظ في المجلد الفرعي `Images`، وسيحتوي markdown على روابط نسبية تشير إلى تلك الملفات.

```csharp
// Destination markdown file
string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");

// Perform the conversion
doc.Save(outputPath, mdOptions);
```

بعد انتهاء الاستدعاء، يجب أن ترى شيئين في `YOUR_DIRECTORY`:

1. **output.md** – ملف markdown حيث يتم الإشارة إلى كل صورة مثل `![](Images/123e4567‑e89b‑12d3‑a456‑426614174000.png)`.  
2. **Images/** – مجلد يحتوي على ملفات PNG/JPEG التي تم استخراجها من مستند Word الأصلي.

يمكنك فتح `output.md` في أي عارض markdown (VS Code, GitHub, Typora) وستظهر الصور تمامًا حيث كانت في الملف الأصلي.

## مثال عملي كامل (جميع الأجزاء معًا)

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في تطبيق console. فقط استبدل `YOUR_DIRECTORY` بالمسار الذي يحتوي على ملف `.docx` الخاص بك.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

// ------------------------------------------------------------
// Step 1: Resource‑saving handler (extract images from docx)
// ------------------------------------------------------------
class MyMarkdownResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        string imageFolder = "Images";
        Directory.CreateDirectory(imageFolder);

        string uniqueFileName = Guid.NewGuid().ToString() + Path.GetExtension(args.FileName);
        string imagePath = Path.Combine(imageFolder, uniqueFileName);

        using (FileStream fs = new FileStream(imagePath, FileMode.Create))
            args.Stream.CopyTo(fs);

        args.FileName = uniqueFileName;
        args.Stream = null;
    }
}

// ------------------------------------------------------------
// Main program – save word as markdown
// ------------------------------------------------------------
class Program
{
    static void Main()
    {
        // Step 2: Load the source document (convert word to markdown)
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(inputPath);

        // Step 3: Configure save options (export images from word)
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyMarkdownResourceHandler(),
            ExportImagesAsBase64 = false,
            UseGitHubFlavor = true
        };

        // Step 4: Save as markdown
        string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown file: {outputPath}");
        Console.WriteLine("Images folder: Images (inside the same directory)");
    }
}
```

شغّل البرنامج (`dotnet run`)، وستحصل على **saved Word as markdown** مع **exporting images from word** إلى مجلد منظم.

## النتيجة المتوقعة

| الملف | الوصف |
|------|-------------|
| `output.md` | نص Markdown مع مراجع صور مثل `![](Images/abcd1234.png)`. |
| `Images/` | ملف واحد لكل صورة تم استخراجها من ملف `.docx` الأصلي. أسماء الملفات تعتمد على GUID لتجنب التعارضات. |

افتح `output.md` في عارض markdown وسترى التخطيط الأصلي، العناوين، القوائم النقطية، وجميع الصور معروضة في أماكنها الصحيحة.

## أسئلة شائعة وحالات خاصة

- **ماذا لو كان المستند يحتوي على صور SVG أو WMF؟**  
  Aspose.Words يقوم تلقائيًا بتحويل تلك الصيغ إلى PNG عندما يكون `ExportImagesAsBase64 = false`. لا حاجة إلى كود إضافي.

- **هل يمكنني تغيير اسم مجلد الصور؟**  
  بالتأكيد—فقط عدل المتغير `imageFolder` داخل `MyMarkdownResourceHandler`. تذكر أن تبقي مسار المجلد نسبياً لملف markdown حتى تظل الروابط صالحة.

- **هل أحتاج إلى رخصة تجارية؟**  
  النسخة التجريبية المجانية تعمل للتقييم، لكنها تضيف علامة مائية إلى الناتج. للاستخدام الإنتاجي ستحتاج إلى رخصة مناسبة؛ استخدام الـ API يبقى كما هو.

- **ماذا عن الجداول أو الحواشي؟**  
  `MarkdownSaveOptions` يتعامل بالفعل مع الجداول (markdown بنكهة GitHub). الحواشي يتم تجاهلها افتراضيًا؛ اضبط `ExportHeadersFooters = true` إذا كنت تحتاجها.

- **هل تسبب المستندات الكبيرة ضغطًا على الذاكرة؟**  
  استخدم `LoadOptions` مع `LoadFormat.Docx` و `LoadOptions.MemoryOptimization = true`. عملية التحويل نفسها تظل صديقة للبث بفضل الـ callback.

## الخلاصة

أصبح لديك الآن وصفة شاملة من البداية إلى النهاية لـ **save Word as markdown**، **convert Word to markdown**، و **extract images from docx**—كل ذلك في بضع أسطر من C#. المفتاح هو `IResourceSavingCallback` المخصص الذي يتيح لك **export images from word** بالضبط حيث تريدها. من هنا يمكنك دمج الروتين في خط بناء، خدمة ويب، أو أداة سطح مكتب تقوم بتحويل تقارير Word جماعيًا إلى markdown صديق للمطورين.

ما التالي؟ جرّب تعديل `MarkdownSaveOptions` لتوليد روابط نصية عادية، أو دمج ذلك مع مولد موقع ثابت لنشر الوثائق

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}