---
category: general
date: 2026-02-26
description: إنشاء مجلد لتعليم C# يوضح كيفية تحويل Word إلى markdown، واستخراج الصور
  من docx، ونسخ الدفق إلى ملف—كل ذلك في خطوة واحدة.
draft: false
keywords:
- create folder c#
- convert word to markdown
- extract images from docx
- copy stream to file
language: ar
og_description: دليل إنشاء مجلد C# يشرح لك تحويل Word إلى markdown، واستخراج الصور
  من ملف docx، ونسخ التدفق إلى ملف مع أمثلة شفرة واضحة.
og_title: إنشاء مجلد C# – تحويل Word إلى Markdown واستخراج الصور
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: إنشاء مجلد C# – تحويل Word إلى Markdown واستخراج الصور
url: /ar/net/programming-with-markdownsaveoptions/create-folder-c-convert-word-to-markdown-extract-images/
---

.

Let's translate:

Title: "# Create folder C# – Convert Word to Markdown & Extract Images" -> Arabic: "# إنشاء مجلد C# – تحويل Word إلى Markdown واستخراج الصور"

Continue.

Paragraphs.

Will translate.

Make sure not to translate code placeholders like .docx, .md etc.

Also keep bullet points.

Now produce final content with same structure.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مجلد C# – تحويل Word إلى Markdown واستخراج الصور

هل احتجت يوماً إلى **إنشاء مجلد C#** مع تحويل مستند Word إلى markdown واستخراج كل صورة منه؟ لست وحدك في هذه المشكلة. في العديد من خطوط الأتمتة تجد نفسك تتعامل مع مهام نظام الملفات، تحويل الصيغ، ومعالجة البيانات الثنائية—كل ذلك في خطوة واحدة.  

في هذا الدليل سنستعرض حلاً كاملاً قابلاً للتنفيذ يقوم بالضبط بذلك: ينشئ دليل الهدف، يحول ملف `.docx` إلى markdown، يستخرج كل صورة مدمجة، ويستخدم منطق **copy stream to file** بحيث تُحفظ الصور في المكان الذي تريد. لا سكربتات خارجية، لا خطوات يدوية. مجرد C# مكتبة Aspose.Words.

> **ما ستحصل عليه**  
> * بنية مجلد واضحة جاهزة للـ markdown والملفات المرفقة  
> * ملف markdown يربط الصور المستخرجة بشكل صحيح  
> * الكود الكامل الذي يمكنك إدراجه في أي مشروع .NET  

قبل أن نبدأ، تأكد من وجود:

* .NET 6.0 (أو أحدث) SDK مثبت – الكود يستخدم ميزات اللغة الحديثة.  
* رخصة **Aspose.Words for .NET** (الإصدار التجريبي المجاني يكفي للاختبار).  
* Visual Studio 2022 أو أي محرر تفضله.  

إذا كنت تتساءل *لماذا تريد استخراج الصور بدلاً من تضمينها*، فكر في مولّدات المواقع الثابتة: فهي تفضّل markdown مع مسارات صور نسبية، والحفاظ على الأصول في مجلد مخصص يجعل الأمور منظمة وصديقة للتخزين المؤقت.

---

## إنشاء مجلد C# وتحضير بنية المخرجات

أول شيء نحتاجه هو مكان على القرص حيث سيعيش كل شيء. هذه الخطوة هي التي يحدث فيها فعل **إنشاء مجلد C#**، وهي بسيطة بشكل مفاجئ بفضل `Directory.CreateDirectory`. الطريقة متعادلّة—لن تُطلق استثناء إذا كان المجلد موجوداً مسبقاً، مما يوفر علينا فحوصات إضافية.

```csharp
using System;
using System.IO;

// Define the base output directory (adjust as needed)
string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");

// Subfolders for markdown and images
string markdownFolder = Path.Combine(baseOutput, "markdown");
string imagesFolder   = Path.Combine(baseOutput, "MyImages");

// Ensure the folders exist
Directory.CreateDirectory(markdownFolder);
Directory.CreateDirectory(imagesFolder);

Console.WriteLine($"Created folders:\n • {markdownFolder}\n • {imagesFolder}");
```

**لماذا هذا مهم:**  
إنشاء المجلدات مسبقاً يضمن أن خطوات الحفظ اللاحقة لن تفشل بـ `DirectoryNotFoundException`. كما يمنحك تخطيطاً متوقعاً: `output/markdown` لملف الـ `.md` و `output/MyImages` لكل صورة نستخرجها.

> **نصيحة احترافية:** إذا شغّلت البرنامج مراراً، قد ترغب في تنظيف مجلد الصور أولاً (`Directory.GetFiles(imagesFolder).ToList().ForEach(File.Delete);`) لتجنب الملفات القديمة.

---

## تحويل Word إلى Markdown باستخدام Aspose.Words

الآن بعد أن شجرة الدليل جاهزة، لنحوّل مستند Word إلى markdown. تقوم Aspose.Words بالعمل الشاق—دون الحاجة للعب مع OpenXML أو محولات طرف ثالث.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source DOCX (replace with your actual path)
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
var doc = new Document(inputPath);

// Configure markdown options and attach the image callback (we’ll define it later)
var mdOptions = new MarkdownSaveOptions
{
    // The callback will redirect each extracted image to our custom folder
    ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
};

// Save the markdown file into the previously created folder
string markdownPath = Path.Combine(markdownFolder, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Word document converted to markdown at: {markdownPath}");
```

**ما الذي يحدث خلف الكواليس؟**  
`MarkdownSaveOptions` تخبر Aspose بإصدار صيغة markdown. بشكل افتراضي، المكتبة ستضع الصور في نفس مجلد ملف الـ markdown بأسماء مُولدة تلقائياً. من خلال توفير `ResourceSavingCallback`، نُعترض هذا السلوك ونقوم بـ **copy stream to file** في الموقع الذي نحدده.

---

## استخراج الصور من DOCX وحفظها

فئة الـ callback تُنفّذ `IResourceSavingCallback`. داخلها نستقبل كائن `ResourceSavingArgs` يحتوي على تدفق الصورة الأصلي واسم الملف المقترح. نكتب ذلك التدفق إلى القرص، نعيد تسمية الملف إذا أردنا، ونخبر Aspose أننا عالجناه.

```csharp
using Aspose.Words.Saving;
using System.IO;

/// <summary>
/// Handles image extraction during markdown conversion.
/// </summary>
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageSavingCallback(string targetFolder)
    {
        _targetFolder = targetFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Ensure the target folder exists (defensive, though we created it earlier)
        Directory.CreateDirectory(_targetFolder);

        // Build a new, friendly file name – you can customize the pattern
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // **Copy stream to file** – the core of the image extraction
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Tell Aspose to use our new path in the markdown reference
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true; // Prevent default saving logic
    }
}
```

### ما سيظهر في ملف الـ markdown

بعد التحويل، سيحتوي `output.md` المُولد على أسطر مثل:

```markdown
![Image 1](MyImages/img_picture1.png)
```

لأننا غيرنا `args.ResourceFileName` إلى مسار نسبي، يشير الـ markdown مباشرة إلى المجلد الذي أنشأناه. هذا بالضبط ما تتوقعه مولّدات المواقع الثابتة.

**معالجة الحالات الخاصة:**  
*إذا كان المستند يحتوي على أسماء صور مكررة*، فإن البادئة `img_` مضافة إلى الاسم الأصلي عادةً ما تُجنب التصادمات، لكن يمكنك أيضاً إضافة GUID (`Guid.NewGuid()`) لضمان التفرد الكامل.

---

## Copy stream to file – معالجة بيانات الصورة

قد تتساءل لماذا لا نستخدم `File.WriteAllBytes` مباشرة. الجواب يكمن في **مرونة الـ stream**. `args.Stream` قد يكون MemoryStream، NetworkStream، أو أي تنفيذ آخر. باستخدام `CopyTo`، نبقى محايدين ونترك .NET يتولى ضبط حجم البوفر بكفاءة.

إليك طريقة مساعدة مختصرة إذا احتجت لنسخ أي Stream عام إلى مكان آخر:

```csharp
/// <summary>
/// Copies any readable stream to a file on disk.
/// </summary>
public static void CopyStreamToFile(Stream source, string destinationPath)
{
    using (var file = new FileStream(destinationPath, FileMode.Create, FileAccess.Write))
    {
        source.CopyTo(file);
    }
}
```

يمكنك استبدال النسخ المضمن في `ImageSavingCallback` باستدعاء `CopyStreamToFile` إذا فضلت نهج المسؤولية الواحدة.

---

## مثال كامل قابل للتنفيذ

جمع كل الأجزاء معاً يمنحك برنامجاً مستقلاً يمكنك تشغيله من سطر الأوامر:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the folder structure
        string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");
        string markdownFolder = Path.Combine(baseOutput, "markdown");
        string imagesFolder   = Path.Combine(baseOutput, "MyImages");
        Directory.CreateDirectory(markdownFolder);
        Directory.CreateDirectory(imagesFolder);

        // 2️⃣ Load the DOCX
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(inputPath);

        // 3️⃣ Set up markdown options with our image callback
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
        };

        // 4️⃣ Save as markdown
        string markdownPath = Path.Combine(markdownFolder, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown: {markdownPath}");
        Console.WriteLine($"Images folder: {imagesFolder}");
    }
}

// ---------- ImageSavingCallback (same as earlier) ----------
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageSavingCallback(string targetFolder) => _targetFolder = targetFolder;

    public void ResourceSaving(ResourceSavingArgs args)
    {
        Directory.CreateDirectory(_targetFolder);
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true;
    }
}
```

**النتيجة المتوقعة**

* `output/markdown/output.md` – ملف markdown يحتوي على مراجع صور مثل `![Alt text](MyImages/img_picture1.png)`.  
* `output/MyImages/` – ملف PNG/JPEG لكل صورة كانت موجودة أصلاً داخل `input.docx`.  

افتح الـ markdown في أي عارض (VS Code، GitHub، أو مولّد موقع ثابت) وسترى الصور مُدرجة تماماً كما كانت في ملف Word الأصلي.

---

## الأسئلة المتكررة & استكشاف الأخطاء وإصلاحها

| السؤال | الجواب |
|----------|--------|
| **ماذا لو كان المجلد الهدف يحتوي بالفعل على ملفات؟** | `Directory.CreateDirectory` لا يكتب فوق الملفات. إذا كنت تحتاج تشغيل نظيف، احذف |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}