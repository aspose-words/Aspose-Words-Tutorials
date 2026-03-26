---
category: general
date: 2026-03-25
description: حوّل ملفات DOCX إلى Markdown بسرعة مع استخراج الصور من Word باستخدام
  Aspose.Words. تعلّم خطوة بخطوة مع الكود الكامل.
draft: false
keywords:
- convert docx to markdown
- extract images from word
language: ar
og_description: حوّل ملفات DOCX إلى Markdown واستخرج الصور من Word باستخدام Aspose.Words.
  اتبع هذا الدرس الكامل للحصول على حل جاهز للتنفيذ.
og_title: تحويل DOCX إلى Markdown في C# – دليل خطوة بخطوة
tags:
- Aspose.Words
- C#
- Markdown
title: تحويل DOCX إلى Markdown في C# – دليل كامل
url: /ar/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحويل DOCX إلى Markdown باستخدام Aspose.Words

هل احتجت يومًا إلى **تحويل DOCX إلى markdown** لكنك لم تكن متأكدًا من كيفية الحفاظ على الصور المضمنة؟ لست وحدك—العديد من المطورين يواجهون هذه المشكلة عندما يحاولون نقل محتوى Word إلى مولد مواقع ثابت أو مستودع توثيق.  
الخبر السار هو أن Aspose.Words for .NET يمكنه القيام بالعمل الشاق نيابةً عنك، ومع رد نداء (callback) صغير يمكنك أيضًا **استخراج الصور من ملفات Word** في الوقت نفسه.

في هذا الدرس سنستعرض مثالًا واقعيًا يقوم بتحميل ملف `.docx`، حفظه كملف Markdown، وكتابة كل صورة إلى مجلد مخصص. في النهاية ستحصل على تطبيق console جاهز للتشغيل يمكنك إدراجه في أي مشروع .NET.

> **نصيحة احترافية:** إذا كنت تحتاج فقط إلى النص ولا تهتم بالصور، يمكنك تخطي `ResourceSavingCallback` تمامًا – سيظل الكود ينتج Markdown نظيفًا.

## ما ستحتاجه

- **Aspose.Words for .NET** (أحدث نسخة، مثلاً 24.12). يمكنك الحصول عليها من NuGet: `Install-Package Aspose.Words`.
- **.NET 6.0** أو أحدث (تعمل الواجهة البرمجية أيضًا على .NET Framework، لكن .NET 6 يمنحك أفضل أداء).
- مشروع console بسيط أو أي مضيف C# تفضله.
- ملف Word إدخال (`input.docx`) يحتوي على صورة واحدة على الأقل حتى نتمكن من رؤية عملية الاستخراج.

هذا كل شيء—بدون مكتبات إضافية، بدون أدوات سطر أوامر معقدة. هيا نبدأ.

![convert docx to markdown example](images/convert-docx-to-markdown.png)

*نص بديل للصورة: مثال تحويل docx إلى markdown*

## الخطوة 1 – إعداد المشروع وإضافة Aspose.Words

للحفاظ على النظافة، أنشئ تطبيق console جديد:

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

افتح `Program.cs` واحذف الكود الذي تم إنشاؤه تلقائيًا. سنلصق الحل الكامل لاحقًا، لكن الآن تأكد فقط من أن المشروع يبني بنجاح.

## الخطوة 2 – تحميل ملف DOCX المصدر

أول شيء نفعله هو إخبار Aspose.Words بقراءة ملف Word. هذه العملية **سريعة**—المكتبة تحلل بنية المستند دون فتح Word نفسه.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Path to your source document
string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

// Load the DOCX into a Document object
Document doc = new Document(inputPath);
```

لماذا نغلف المسار بـ `Path.Combine`؟ يجعل الكود قابلًا للنقل عبر Windows و macOS و Linux—شيء ستقدره عندما تنقل المشروع إلى خط أنابيب CI.

## الخطوة 3 – تكوين خيارات حفظ Markdown مع رد نداء للموارد

عند طلب حفظ Aspose.Words كـ Markdown، فإنه عادةً يضمّن الصور كسلاسل Base64. هذا مناسب للأيقونات الصغيرة، لكن للصور الكبيرة يسبب زيادة كبيرة في حجم الملف. بدلاً من ذلك، نرفق **رد نداء لحفظ الموارد** يكتب كل صورة إلى القرص ويحدّث رابط Markdown.

```csharp
// Define where the Markdown and resources will live
string outputDir = Path.Combine("YOUR_DIRECTORY", "Output");
string resourcesDir = Path.Combine(outputDir, "Resources");

// Ensure directories exist
Directory.CreateDirectory(outputDir);
Directory.CreateDirectory(resourcesDir);

// Create Markdown options and plug in the callback
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver(resourcesDir)
};
```

لاحظ أننا نمرر `resourcesDir` إلى مُنشئ رد النداء—هذا يبقي منطق المسار خارج رد النداء نفسه ويجعل الفئة قابلة لإعادة الاستخدام.

## الخطوة 4 – تنفيذ رد نداء حفظ الموارد

رد النداء ينفّذ `IResourceSavingCallback`. لكل صورة يرغب Aspose.Words في كتابتها، يمرّر لنا كائن `ResourceSavingArgs`. نقرر **أين** نخزن الملف، نعطيه اسمًا فريدًا، ثم نخبر المحرك بتخطي سلوكه الافتراضي في الحفظ.

```csharp
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique, deterministic file name
        string ext = Path.GetExtension(args.FileName);          // e.g., ".png"
        string fileName = $"img_{args.Index}{ext}";            // img_0.png, img_1.jpg, …

        // Full path on disk
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Write the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown URI so it points to the saved image
        args.Uri = $"Resources/{fileName}";

        // Tell Aspose.Words we handled the saving
        args.Cancel = true;
    }
}
```

**لماذا هذا مهم:** بتعيين `args.Uri` نتحكم تمامًا في كيفية الإشارة إلى الصورة في ملف `.md` الناتج. المسار النسبي `Resources/img_0.png` يعمل سواء فتحت الـ Markdown في VS Code أو GitHub أو مولد مواقع ثابت.

## الخطوة 5 – حفظ المستند كـ Markdown

الآن الجزء الأخير: نطلب من Aspose.Words كتابة ملف Markdown. رد النداء الذي ربطناه سيُنفّذ تلقائيًا لكل صورة.

```csharp
// Destination Markdown file
string markdownPath = Path.Combine(outputDir, "output.md");

// Perform the conversion
doc.Save(markdownPath, mdOptions);
```

عند انتهاء السطر، ستحصل على:

- `output.md` – تمثيل Markdown نظيف لمحتوى Word الأصلي.
- مجلد `Resources/` – يحتوي على كل صورة تم استخراجها من الـ DOCX.

## مثال كامل يعمل

فيما يلي البرنامج **الكامل، جاهز للنسخ واللصق**. استبدل `YOUR_DIRECTORY` بالمسار المطلق أو النسبي الذي يحتوي على `input.docx`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // ------------------------------------------------------------
        // 1️⃣  Define paths
        // ------------------------------------------------------------
        string baseDir = Path.Combine(Environment.CurrentDirectory, "DemoFiles");
        string inputPath = Path.Combine(baseDir, "input.docx");
        string outputDir = Path.Combine(baseDir, "Output");
        string resourcesDir = Path.Combine(outputDir, "Resources");

        // Create folders if they don't exist
        Directory.CreateDirectory(outputDir);
        Directory.CreateDirectory(resourcesDir);

        // ------------------------------------------------------------
        // 2️⃣  Load the DOCX
        // ------------------------------------------------------------
        Document doc = new Document(inputPath);

        // ------------------------------------------------------------
        // 3️⃣  Prepare Markdown options with a resource callback
        // ------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyResourceSaver(resourcesDir)
        };

        // ------------------------------------------------------------
        // 4️⃣  Save as Markdown
        // ------------------------------------------------------------
        string markdownPath = Path.Combine(outputDir, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown file: {markdownPath}");
        Console.WriteLine($"Images folder: {resourcesDir}");
    }
}

// -----------------------------------------------------------------
// Callback that writes each image to the Resources folder
// -----------------------------------------------------------------
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Create a deterministic file name like img_0.png
        string extension = Path.GetExtension(args.FileName);
        string fileName = $"img_{args.Index}{extension}";
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Persist the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown link to point to the saved image
        args.Uri = $"Resources/{fileName}";

        // Cancel default saving because we already wrote the file
        args.Cancel = true;
    }
}
```

### النتيجة المتوقعة

افتح `Output/output.md` في أي عارض Markdown وسترى شيئًا مشابهًا لـ:

```markdown
# My Sample Document

Here is a paragraph that came from Word.

![Image 1](Resources/img_0.png)

Another paragraph with **bold** text.
```

سيتضمن مجلد `Resources` ملفات `img_0.png`، `img_1.jpg`، إلخ، مطابقة للصور التي كانت مضمّنة أصلاً في `input.docx`.

## الأسئلة المتكررة (FAQ)

**هل يعمل هذا مع ملفات .doc؟**  
نعم. يمكن لـ Aspose.Words تحميل `.doc` و `.docx` و `.rtf` والعديد من الصيغ الأخرى. فقط غيّر امتداد الملف في `inputPath`.

**ماذا لو احتجت إلى عناوين URL مطلقة للصور؟**  
استبدل `args.Uri = $"Resources/{fileName}";` بشيء مثل `args.Uri = $"https://mycdn.com/docs/{fileName}";`. سيتضمن الـ Markdown الآن الإشارة إلى الموقع البعيد.

**هل يمكنني التحكم في جودة أو صيغة الصورة؟**  
رد النداء يتلقى تدفق الصورة الأصلي. إذا أردت تحويل PNG إلى JPEG، يمكنك تحميل التدفق إلى `System.Drawing.Image`، إعادة الترميز، ثم كتابة البايتات الجديدة قبل تعيين `args.Uri`.

**هل `ResourceSavingCallback` آمن للاستخدام في بيئات متعددة الخيوط؟**  
Aspose.Words يستدعي رد النداء بشكل متسلسل لكل مورد، لذا

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}