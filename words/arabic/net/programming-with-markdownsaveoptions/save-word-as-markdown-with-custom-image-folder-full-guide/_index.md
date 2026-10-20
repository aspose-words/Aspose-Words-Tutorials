---
category: general
date: 2026-04-07
description: احفظ مستند Word كملف Markdown واستخرج الصور من ملف docx باستخدام رد نداء.
  تعلّم كيفية استخدام رد النداء لتخزين مجلد صور الـ Markdown بكفاءة.
draft: false
keywords:
- save word as markdown
- extract images from docx
- how to use callback
- markdown images folder
language: ar
og_description: احفظ مستند Word كـ Markdown واستخرج الصور من ملف docx باستخدام رد
  النداء. يوضح هذا الدليل كيفية استخدام رد النداء لإنشاء مجلد صور Markdown.
og_title: حفظ ملف Word كـ Markdown – دليل خطوة بخطوة كامل
tags:
- Aspose.Words
- C#
- Markdown
- Image Extraction
title: حفظ ملف وورد كماركداون مع مجلد صور مخصص – دليل كامل
url: /ar/net/programming-with-markdownsaveoptions/save-word-as-markdown-with-custom-image-folder-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ Word كـ Markdown – دليل خطوة‑بخطوة كامل

هل احتجت يومًا إلى **حفظ Word كـ Markdown** لكنك لم تكن متأكدًا مما يجب فعله بالصور المدمجة؟ أنت لست وحدك. في العديد من المشاريع يبدو ناتج الـ markdown رائعًا—*حتى* تدرك أن روابط الصور مكسورة لأن الملفات لم تغادر حزمة Word أبداً.  

الخبر السار هو أن Aspose.Words يوفّر لك طريقة نظيفة لـ **استخراج الصور من docx** ووضعها تمامًا حيث تريد، باستخدام **callback** يتيح لك التحكم في مجلد صور الـ markdown. في هذا الدرس سنستعرض العملية بالكامل، من تحميل ملف `.docx` إلى الحصول على مجلد منظم يحتوي على PNGs (أو أي صيغة لديك) وملف markdown يشير إليها.

بحلول نهاية هذا الدليل ستتمكن من:

* تحويل أي مستند Word إلى Markdown بسطر واحد من الكود.  
* تفريغ كل صورة تلقائيًا في مجلد فرعي مخصص `images`.  
* تخصيص أسماء الملفات بحيث لا تتصادم أبدًا، حتى عندما يحتوي المصدر على عشرات الصور.  

بدون سكريبتات خارجية، بدون نسخ ولصق يدوي—فقط C# نقي و Aspose.Words.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من أن لديك:

* **Aspose.Words for .NET** (أحدث نسخة مستقرة؛ عند كتابة هذا الدليل هي 24.9).  
* بيئة تطوير .NET (Visual Studio، Rider، أو `dotnet` CLI).  
* مستند Word (`.docx`) يحتوي على صورة واحدة على الأقل—سميه `DocWithImages.docx`.  

إذا لم تستخدم Aspose.Words من قبل، لا تقلق. المكتبة مُدارة بالكامل، لا تتطلب أي تفاعل COM، وتعمل على .NET 6+ وكذلك .NET Framework 4.8.

## الخطوة 1 – إعداد المشروع وتثبيت الحزمة

أولاً، أنشئ تطبيق console جديد (أو أضف الكود إلى مشروع موجود).

```bash
dotnet new console -n WordToMarkdownDemo
cd WordToMarkdownDemo
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** إذا كنت تستهدف .NET 6، فإن `Program.cs` الافتراضي يستخدم بالفعل عبارات المستوى العلوي، مما يجعل العينة مختصرة.

## الخطوة 2 – إنشاء Callback للتحكم في حفظ الصور

Aspose.Words يستدعي `IResourceSavingCallback.ResourceSaving` لكل مورد خارجي يحتاج إلى كتابته (صور، CSS، إلخ). من خلال تنفيذ هذه الواجهة نحصل على صلاحية كاملة للتحكم في **كيفية بناء مجلد صور الـ markdown**.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Handles the saving of resources (e.g., images) when a document is converted to Markdown.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    // Folder where we want to dump the images.
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        // Ensure the folder exists before the first write.
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique filename: img_<guid>.<originalExtension>
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";

        // Full path where the image will be saved.
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        // Copy the incoming stream to our file.
        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        // Tell Aspose we’ve handled the write; skip its default behavior.
        args.Cancel = true;
    }
}
```

### لماذا نستخدم callback؟

* **تحكم دقيق** – أنت تقرر بنية المجلد ومخطط التسمية.  
* **الأداء** – تكتب الدفق مرة واحدة، متجنبًا كتابة المكتبة المزدوجة.  
* **المرونة** – يمكنك إضافة تسجيل، تحسين الصور، أو حتى رفعها إلى التخزين السحابي في هذه المرحلة.

## الخطوة 3 – تحميل مستند Word

الآن بعد أن أصبح الـ callback جاهزًا، نحتاج فقط لتوجيه Aspose.Words إلى ملف المصدر.

```csharp
// Path to the source .docx (adjust as needed).
string sourcePath = Path.Combine("YOUR_DIRECTORY", "DocWithImages.docx");

// Load the document into memory.
Document doc = new Document(sourcePath);
```

> **ماذا لو لم يُعثر على الملف؟**  
> سيُطلق `Document` استثناءً من نوع `FileNotFoundException`. غلف عملية التحميل بـ `try/catch` إذا كنت تتوقع مسارات ديناميكية.

## الخطوة 4 – ربط MarkdownSaveOptions

فئة `MarkdownSaveOptions` تتيح لنا توصيل الـ callback الذي أنشأناه للتو. كما نحدد المجلد الذي ستعيش فيه الصور بالنسبة لملف الـ markdown.

```csharp
// Define where we want the images folder to sit.
string markdownFolder = Path.Combine("YOUR_DIRECTORY", "markdown-output");
string imagesSubFolder = Path.Combine(markdownFolder, "images");

// Ensure the markdown output directory exists.
Directory.CreateDirectory(markdownFolder);

// Create the save options and attach the callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // This callback will be invoked for every image.
    ResourceSavingCallback = new MyMarkdownResourceCallback(imagesSubFolder),

    // Optional: keep image references relative to the markdown file.
    ImagesFolder = "images"
};
```

خاصية `ImagesFolder` تخبر Aspose بإنشاء روابط markdown مثل `![Alt text](images/img_123.png)`. لأننا أيضًا قمنا بتعيين `ResourceFileName` داخل الـ callback، فإن الملف الفعلي يُوضع تمامًا هناك.

## الخطوة 5 – حفظ كـ Markdown والتحقق من النتيجة

أخيرًا، نكتب ملف الـ markdown. الـ callback سيكون قد ملأ بالفعل المجلد الفرعي `images`.

```csharp
// Destination markdown file.
string markdownPath = Path.Combine(markdownFolder, "Doc.md");

// Save the document.
doc.Save(markdownPath, mdOptions);

// Quick sanity check – list the generated files.
Console.WriteLine("Markdown saved to: " + markdownPath);
Console.WriteLine("Extracted images:");
foreach (var img in Directory.GetFiles(imagesSubFolder))
{
    Console.WriteLine("  • " + Path.GetFileName(img));
}
```

### النتيجة المتوقعة

تشغيل البرنامج يجب أن يطبع شيئًا مشابهًا لـ:

```
Markdown saved to: C:\Project\markdown-output\Doc.md
Extracted images:
  • img_5c2a1f8b-3e7b-4d9a-9c1f-2b6e5f9d9a3c.png
  • img_a7d4c9e2-1f55-4c2b-8f6a-9e1b2c3d4e5f.jpg
```

افتح `Doc.md` في أي عارض markdown؛ سترى روابط الصور التي تشير بشكل صحيح إلى مجلد `images`.

---

## الأسئلة المتكررة (FAQ)

### كيف **استخراج الصور من docx** دون التحويل إلى markdown؟

يمكنك إعادة استخدام نفس `MyMarkdownResourceCallback` ولكن تمريره إلى `doc.Save("images.zip", SaveFormat.Zip)`. سيظل الـ callback يُستدعى لكل صورة، مما يتيح لك وضعها في أي مكان تريده.

### ماذا لو احتجت **صيغ صور مختلفة**؟

`args.FileName` يحتوي بالفعل على الامتداد الأصلي (`.png`, `.jpg`, إلخ). إذا كان عليك تحويل جميع الصور إلى صيغة واحدة، أضف خطوة التحويل داخل `ResourceSaving` قبل كتابة الدفق.

### هل يمكنني **تخصيص مجلد صور الـ markdown** لكل مستند؟

بالطبع. الـ callback يستقبل مسار المجلد عبر المُنشئ الخاص به، لذا يمكنك إنشاء callback جديد بمجلد مختلف لكل مستند في عملية دفعة.

### هل يعمل هذا مع **مستندات كبيرة** (مئات الصور)؟

نعم. الـ callback يبث الصورة مباشرة إلى القرص، مما يحافظ على انخفاض استهلاك الذاكرة. فقط تأكد من أن القرص الهدف يحتوي على مساحة كافية وأنك لا تتجاوز حدود مقابض الملفات في نظام التشغيل.

## مثال كامل يعمل

فيما يلي البرنامج الكامل جاهز للنسخ واللصق. استبدل `YOUR_DIRECTORY` بمسار مطلق أو نسبي يناسب بيئتك.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        args.Cancel = true;
    }
}

class Program
{
    static void Main()
    {
        // Adjust these paths.
        string baseDir = Path.Combine(Environment.CurrentDirectory, "demo");
        string sourceDoc = Path.Combine(baseDir, "DocWithImages.docx");
        string markdownDir = Path.Combine(baseDir, "markdown-output");
        string imagesDir = Path.Combine(markdownDir, "images");
        string markdownFile = Path.Combine(markdownDir, "Doc.md");

        // Load the document.
        Document doc;
        try
        {
            doc = new Document(sourceDoc);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // Configure save options with our callback.
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyMarkdownResourceCallback(imagesDir),
            ImagesFolder = "images"
        };

        // Ensure output folder exists.
        Directory.CreateDirectory(markdownDir);

        // Save as markdown.
        doc.Save(markdownFile, mdOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownFile}");
        Console.WriteLine("🖼️ Extracted images:");
        foreach (var file in Directory.GetFiles(imagesDir))
            Console.WriteLine($"   - {Path.GetFileName(file)}");
    }
}
```

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}