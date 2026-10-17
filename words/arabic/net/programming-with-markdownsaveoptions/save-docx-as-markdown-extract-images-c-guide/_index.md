---
category: general
date: 2026-02-17
description: احفظ ملف docx كملف markdown واستخرج الصور باستخدام Aspose.Words في C#. تعلم
  كيفية تحويل Word إلى markdown واستخراج الصور من ملف DOCX.
draft: false
keywords:
- save docx as markdown
- convert word to markdown
- extract images from docx
- Aspose.Words markdown
- C# document conversion
language: ar
og_description: احفظ ملف docx كـ markdown باستخدام Aspose.Words في C#. يوضح هذا الدليل
  كيفية تحويل Word إلى markdown واستخراج الصور من ملف DOCX.
og_title: احفظ ملف docx كـ markdown واستخرج الصور – دليل C#
tags:
- C#
- Aspose.Words
- Markdown
- DOCX
- Image extraction
title: حفظ ملف docx كـ markdown واستخراج الصور – دليل C#
url: /ar/net/programming-with-markdownsaveoptions/save-docx-as-markdown-extract-images-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ docx كـ markdown واستخراج الصور – دليل C# كامل

هل احتجت يوماً إلى **حفظ ملف docx كـ markdown** مع الحفاظ على كل صورة، رسم تخطيطي، أو SVG داخل ملف Word؟ لست الوحيد الذي يواجه هذه المشكلة. في العديد من المشاريع—مولدات المواقع الثابتة، خطوط توثيق، أو أدوات تدوين بسيطة—نحتاج إلى **تحويل Word إلى markdown** مع الحفاظ على الموارد، وإلا سيظهر الملف الناتج كمدينة مهجورة.

الأخبار السارة؟ مع Aspose.Words يمكنك القيام بالأمرين في بضع سطور فقط. يوضح هذا الدليل كيفية تحميل ملف `.docx`، تكوين كائن `MarkdownSaveOptions`، كتابة `IResourceSavingCallback` مخصص يضع كل مورد خارجي في مجلد `assets`، وأخيراً التحقق من النتيجة. لا سحر، مجرد C# بسيط يمكنك إدراجه في أي تطبيق .NET Console.

> **Pro tip:** إذا كنت تهتم بالنص فقط ولا تحتاج إلى الصور، يمكنك تخطي الـ callback تماماً—ستقوم Aspose بدمج بيانات base‑64 كـ URIs بشكل افتراضي.

سترى أدناه أيضاً كيفية **استخراج الصور من docx** يدوياً، ولماذا قد ترغب في مجلد منفصل لها، وبعض النصائح الخاصة بالحالات الخاصة للحفاظ على سلاسة عملية البناء.

---

## ما ستحتاجه

- **.NET 6.0** (أو أي نسخة .NET حديثة). الإطارات القديمة تعمل، لكن الصياغة المعروضة تستخدم أحدث ميزات C#.
- حزمة NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`).
- مستند Word تجريبي (`input.docx`) يحتوي على صورة واحدة على الأقل.
- مجلد تريد حفظ الـ markdown والموارد فيه (سنسميه `YOUR_DIRECTORY`).

هذا كل شيء—لا مكتبات إضافية، ولا أدوات سطر أوامر معقدة. بضع سطور من الكود وستحصل على ملف Markdown نظيف بالإضافة إلى مجلد فرعي `assets` جاهز لمولد موقع ثابت.

## تنفيذ خطوة بخطوة

### ## حفظ docx كـ markdown – تحميل المستند المصدر

أولاً، نحتاج إلى كائن `Document` يشير إلى ملف Word الخاص بنا.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Path to the original DOCX file
        string sourcePath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        // Load the document into Aspose.Words
        Document doc = new Document(sourcePath);
```

> **Why this matters:** تحميل الملف يتحقق من أن ملف DOCX مُشكل بشكل صحيح. إذا كان الملف تالفاً، تقوم Aspose برمي استثناء واضح، مما يحفظك من الأخطاء الغامضة لاحقاً.

### ## تحويل Word إلى markdown – تكوين خيارات الحفظ مع callback

تتيح لنا فئة `MarkdownSaveOptions` التحكم في كيفية معالجة الموارد (الصور، SVGs، إلخ). من خلال تعيين `ResourceSavingCallback` مخصص، نحدد بالضبط أين يتم وضع كل ملف.

```csharp
        // Step 2: Create save options and plug in our callback
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // Our callback will write every image to the assets folder
            ResourceSavingCallback = new CustomResourceCallback()
        };
```

> **Tip:** إذا كنت تفضل تضمين data‑uri (الإعداد الافتراضي)، ببساطة احذف الـ callback. الـ callback ضروري فقط عندما *تستخرج الصور من docx* إلى دليل منفصل.

### ## استخراج الصور من docx – تنفيذ الـ callback المخصص

يتلقى الـ callback كائن `ResourceSavingArgs` لكل مورد خارجي. نستخدمه لإنشاء مجلد `assets` (إذا لم يكن موجوداً)، إعادة تسمية مسار الملف، وفتح `FileStream` للكتابة.

```csharp
        // Step 3: Save the markdown file; resources are handled by the callback
        string markdownPath = Path.Combine("YOUR_DIRECTORY", "DocWithResources.md");
        doc.Save(markdownPath, mdOptions);
    }
}

// ---------------------------------------------------------------------
// Custom callback that stores all external resources in a sub‑folder "assets"
public class CustomResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build the assets folder path (e.g., YOUR_DIRECTORY/assets)
        string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
        Directory.CreateDirectory(assetsFolder); // No‑op if it already exists

        // Preserve the original file name but prepend the assets folder
        string fileName = Path.GetFileName(args.ResourceFileName);
        args.ResourceFileName = Path.Combine(assetsFolder, fileName);

        // Open a stream that writes the resource to disk
        args.Stream = new FileStream(args.ResourceFileName, FileMode.Create);
    }
}
```

> **What’s happening under the hood?** تقوم Aspose ببث كل صورة (PNG، JPEG، GIF، SVG، إلخ) إلى `args.Stream` الذي توفره. من خلال استبدال الـ stream الافتراضي بـ `FileStream` الذي يشير إلى `assets/<image-name>`، نحن فعلياً *نستخرج الصور من docx* ونحافظ على نظافة الـ markdown.

### ## التحقق من النتيجة – ما يجب أن تراه

بعد تشغيل البرنامج:

1. `YOUR_DIRECTORY/DocWithResources.md` يحتوي على نص Markdown مع روابط صور مثل `![](assets/image1.png)`.
2. `YOUR_DIRECTORY/assets/` يحتوي على كل صورة كانت في `input.docx`.

افتح ملف الـ markdown في أي محرر—إذا رأيت أماكن الصور تُظهر بشكل صحيح، فقد نجحت في **حفظ docx كـ markdown** مع استخراج جميع الموارد.

## الاختلافات الشائعة وحالات الحافة

### ### معالجة الموارد الموجودة

إذا قمت بتشغيل التحويل عدة مرات، قد تنتهي إلى استبدال الصور عن غير قصد. إجراء حماية سريع هو إلحاق طابع زمني أو GUID إلى اسم كل ملف:

```csharp
string uniqueName = $"{Path.GetFileNameWithoutExtension(fileName)}_{Guid.NewGuid()}{Path.GetExtension(fileName)}";
args.ResourceFileName = Path.Combine(assetsFolder, uniqueName);
```

### ### صور كبيرة أو ملفات PDF مدمجة كصور

تقوم Aspose.Words ببث البايتات الخام، لذا حتى مخطط بحجم 10 ميغابايت سيُحفظ كما هو. ومع ذلك، قد تواجه عارضات Markdown صعوبة مع الملفات الضخمة. فكر في تعديل حجم الصور قبل الحفظ:

```csharp
// Example using System.Drawing (requires System.Drawing.Common on .NET Core)
using (var img = System.Drawing.Image.FromStream(args.Stream))
{
    var resized = new Bitmap(img, new Size(800, 0)); // Keep aspect ratio
    resized.Save(args.ResourceFileName, img.RawFormat);
}
```

> **Caution:** مقطع تعديل الحجم اختياري ويضيف اعتماداً على `System.Drawing.Common`. استخدمه فقط إذا كان خط أنابيبك يتطلب موارد أصغر.

### ### معالجة SVG

ملفات SVG هي رسومات متجهية؛ معظم مولدات المواقع الثابتة تتعامل معها كملفات عادية. الـ callback يعمل دون تغيير، لكن تأكد من أن معالج الـ Markdown يدعم SVG داخل النص (مثل GitHub Pages).

### ### موارد غير الصور (الخطوط، كائنات OLE)

تتعامل Aspose أيضاً مع الخطوط، كائنات OLE، وغيرها من الكتل الثنائية كموارد. إذا كنت تهتم بالصور فقط، قم بالفلترة حسب الامتداد:

```csharp
if (!args.ResourceFileName.EndsWith(".png", StringComparison.OrdinalIgnoreCase) &&
    !args.ResourceFileName.EndsWith(".jpg", StringComparison.OrdinalIgnoreCase) &&
    !args.ResourceFileName.EndsWith(".svg", StringComparison.OrdinalIgnoreCase))
{
    // Skip non‑image resources
    args.Skip = true;
    return;
}
```

## مثال كامل قابل للتنفيذ (جاهز للنسخ واللصق)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1️⃣ Load the source DOCX
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2️⃣ Set up Markdown save options with a custom resource callback
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new CustomResourceCallback()
        };

        // -----------------------------------------------------------------
        // 3️⃣ Save as Markdown; the callback will store images in assets/
        // -----------------------------------------------------------------
        string markdownPath = Path.Combine("YOUR_DIRECTORY", "DocWithResources.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("🖼️  Images extracted to: assets folder");
    }
}

// ---------------------------------------------------------------------
// Custom callback – extracts every external resource into YOUR_DIRECTORY/assets
// ---------------------------------------------------------------------
public class CustomResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build assets folder (creates it if missing)
        string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
        Directory.CreateDirectory(assetsFolder);

        // Keep the original file name, but place it in assets/
        string fileName = Path.GetFileName(args.ResourceFileName);
        args.ResourceFileName = Path.Combine(assetsFolder, fileName);

        // Write the resource to disk
        args.Stream = new FileStream(args.ResourceFileName, FileMode.Create);
    }
}
```

**النتيجة المتوقعة:**  
- `DocWithResources.md` يحتوي على markdown مثل `![](assets/image1.png)`.  
- دليل `assets` يحتوي على `image1.png`، `image2.svg`، إلخ.  
- فتح الـ markdown في VS Code أو معاينة موقع ثابت يظهر الصور مدمجة داخل النص.

## الأسئلة المتكررة (FAQ)

| السؤال | الإجابة |
|----------|--------|
| *هل أحتاج إلى ترخيص لـ Aspose.Words؟* | المكتبة تعمل في

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}