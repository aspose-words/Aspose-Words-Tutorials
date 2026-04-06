---
category: general
date: 2026-04-05
description: تعلم كيفية تحويل ملفات DOCX إلى Markdown واستخراج الصور من DOCX باستخدام
  C#. دليل خطوة بخطوة مع الشيفرة الكاملة والنصائح.
draft: false
keywords:
- convert docx to markdown
- extract images from docx
- Aspose.Words markdown conversion
- C# document processing
- image extraction C#
language: ar
og_description: تحويل DOCX إلى Markdown واستخراج الصور من DOCX باستخدام Aspose.Words.
  دليل كامل بلغة C# يتضمن الشيفرة، الشرح، ونصائح أفضل الممارسات.
og_title: تحويل DOCX إلى Markdown – استخراج الصور من DOCX باستخدام C#
tags:
- Aspose.Words
- C#
- Markdown
- DOCX
- Image extraction
title: تحويل DOCX إلى Markdown – استخراج الصور من DOCX باستخدام Aspose.Words
url: /ar/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-extract-images-from-docx-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحويل DOCX إلى Markdown – استخراج الصور من DOCX باستخدام C#

هل احتجت يومًا إلى **تحويل DOCX إلى Markdown** لكنك واجهت صعوبة في اختفاء الصور في الناتج؟ لست وحدك. في العديد من المشاريع تكون نسخة الـ markdown مثالية للتحكم في الإصدارات أو مولدات المواقع الثابتة، لكن الصور تُترك خلفها، مما يحول مستندًا غنيًا إلى ملف نصي جاف.  

الأخبار السارة؟ باستخدام بضع أسطر من C# و Aspose.Words يمكنك **تحويل DOCX إلى Markdown** *و* **استخراج الصور من DOCX** تلقائيًا. هذا الدليل يشرح لك العملية بالكامل، ويوضح لماذا كل جزء مهم، ويظهر لك أيضًا كيفية الحفاظ على مجلد الصور منظمًا.

## ما ستتعلمه

- كيفية تحميل ملف DOCX يحتوي على صور.
- كيفية تعريف `IResourceSavingCallback` مخصص يحدد أين تُحفظ كل صورة.
- كيفية تكوين `MarkdownSaveOptions` بحيث تشير الـ markdown المُنشأة إلى الصور المستخرجة بشكل صحيح.
- نصائح للتعامل مع الحالات الخاصة مثل أسماء الصور المتكررة أو الصيغ غير PNG.
- عينة كود كاملة جاهزة للنسخ واللصق يمكنك تشغيلها اليوم.

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (تعمل الواجهة البرمجية على .NET Core و .NET Framework و .NET 5+).
- رخصة لـ **Aspose.Words for .NET** (الإصدار التجريبي المجاني يعمل للاختبار).
- إلمام أساسي بـ C# و Visual Studio (أو بيئة التطوير المفضلة لديك).

إذا كان لديك هذه المتطلبات، هيا نبدأ.

---

## الخطوة 1: إعداد المشروع وتثبيت Aspose.Words

أولاً، أنشئ تطبيق console جديد (أو دمجه في حل موجود).

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** استخدم أحدث نسخة من NuGet (اعتبارًا من أبريل 2026 الإصدار 24.12) للحصول على أحدث تحسينات تصدير markdown.

---

## الخطوة 2: إنشاء رد نداء لحفظ الصور في المكان الذي تريده

يتيح لك Aspose.Words اعتراض كل مورد (صور، SVGs، إلخ) يتم كتابته أثناء تصدير markdown. من خلال تنفيذ `IResourceSavingCallback` يمكنك:

1. اختيار مجلد يقع بجوار ملف markdown الخاص بك.
2. إنشاء اسم ملف فريد (حتى لا تقوم بالكتابة فوق صورة موجودة).
3. تحديد الصيغة (هنا نجبر على PNG للاتساق).

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Saves each image extracted from the DOCX into a dedicated folder
/// with a GUID‑based filename. The markdown file will reference the
/// new filename via <c>args.ResourceFileName</c>.
/// </summary>
class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageResourceSaver(string targetFolder)
    {
        _targetFolder = targetFolder;
        // Ensure the folder exists before we start writing files.
        Directory.CreateDirectory(_targetFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Generate a unique name to avoid collisions.
        string newFileName = $"img_{Guid.NewGuid():N}.png";

        // Full physical path where the image will be written.
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // Tell the markdown exporter what name to use in the .md file.
        args.ResourceFileName = newFileName;

        // Provide a stream that writes to the desired location.
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}
```

### لماذا اسم مبني على GUID؟

إذا كان ملف DOCX المصدر يحتوي على صورتين بنفس الاسم الأصلي، فإن النسخ‑اللصق البسيط سيستبدل إحداهما. استخدام `Guid.NewGuid()` يضمن التفرد، وهو مفيد جدًا عندما تقوم بتشغيل التحويل عدة مرات في خط أنابيب آلي.

---

## الخطوة 3: تحميل DOCX وربط خيارات Markdown

الآن نقوم بتحميل المستند إلى الذاكرة وربط رد النداء الذي أنشأناه للتو.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------------
        // 1️⃣  Define paths – adjust these to match your environment.
        // --------------------------------------------------------------------
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMarkdown = @"C:\Docs\DocWithImages.md";
        string imagesFolder = @"C:\Docs\MarkdownResources";

        // --------------------------------------------------------------------
        // 2️⃣  Load the Word document.
        // --------------------------------------------------------------------
        Document doc = new Document(sourceDocx);

        // --------------------------------------------------------------------
        // 3️⃣  Configure MarkdownSaveOptions with our custom saver.
        // --------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This tells Aspose.Words to call ImageResourceSaver for each image.
            ResourceSavingCallback = new ImageResourceSaver(imagesFolder)
        };

        // --------------------------------------------------------------------
        // 4️⃣  Perform the conversion.
        // --------------------------------------------------------------------
        doc.Save(outputMarkdown, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputMarkdown}");
        Console.WriteLine($"Images saved to:   {imagesFolder}");
    }
}
```

### ما يفعله الكود خطوة بخطوة

| الخطوة | الغرض |
|------|---------|
| **تحديد المسارات** | يحافظ على مرونة مشروعك؛ يمكنك الإشارة إلى أي مجلد دون الحاجة لإعادة التجميع. |
| **تحميل الـ DOCX** | `Document` يحلل ملف Word، مما يجعل جميع العناصر (فقرات، جداول، صور) متاحة. |
| **تكوين `MarkdownSaveOptions`** | `ResourceSavingCallback` هو النقطة التي تستخرج الصور. بدونه، سيقوم Aspose.Words إما بدمج الصور كسلاسل base64 أو حذفها تمامًا، حسب الإعدادات. |
| **حفظ** | `doc.Save` يكتب ملف markdown ويُطلق رد النداء لكل صورة. |

---

## الخطوة 4: التحقق من الناتج – ماذا يجب أن ترى؟

بعد تشغيل البرنامج، افتح `DocWithImages.md`. ستلاحظ روابط صور markdown التي تبدو هكذا:

```markdown
![img_1a2b3c4d5e6f7g8h9i0j.png](MarkdownResources/img_1a2b3c4d5e6f7g8h9i0j.png)
```

وفي `C:\Docs\MarkdownResources` ستجد مجموعة من ملفات PNG بأسماء GUID. افتح أيًا منها – يجب أن تكون مطابقة للصور التي كانت مدمجة في الـ DOCX الأصلي.

إذا فتحت ملف markdown في عارض يحترم المسارات النسبية (مثل معاينة VS Code، GitHub، أو مولد موقع ثابت)، ستظهر الصور كما ظهرت في Word.

### الأخطاء الشائعة وكيفية تجنبها

| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| الصور تظهر كروابط مكسورة | `ResourceFileName` لم يتم تعيينه، لذا يشير الـ markdown إلى ملف غير موجود. | تأكد من `args.ResourceFileName = newFileName;` داخل رد النداء. |
| ملفات PNG ضخمة | الصور الأصلية كانت JPEG أو BMP؛ تحويلها إلى PNG قد يزيد الحجم. | اكتشف الصيغة الأصلية عبر `args.ResourceContentType` وحافظ عليها: `args.ResourceFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";` |
| الصور المتكررة لا تزال تظهر | استخدمت اسم ملف ثابت بدلاً من GUID. | ارجع إلى منطق GUID أو أضف عدادًا لكل نوع صورة. |
| التحويل يطرح استثناء `FileNotFoundException` | مسار DOCX المصدر غير صحيح أو المجلد يفتقر إلى صلاحية القراءة. | تحقق من المسار ومنح الصلاحيات المناسبة لنظام الملفات. |

---

## الخطوة 5: تعديلات متقدمة (اختياري)

### 5.1 الحفاظ على صيغ الصور الأصلية

إذا كنت تريد أن تحتفظ الصور الناتجة بامتداداتها الأصلية، عدل رد النداء:

```csharp
public void ResourceSaving(ResourceSavingArgs args)
{
    string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
    // Default to .png if Aspose couldn't determine an extension.
    if (string.IsNullOrEmpty(ext)) ext = ".png";

    string newFileName = $"img_{Guid.NewGuid():N}{ext}";
    string fullPath = Path.Combine(_targetFolder, newFileName);
    args.ResourceFileName = newFileName;
    args.Stream = new FileStream(fullPath, FileMode.Create);
}
```

### 5.2 تضمين الصور كـ Base64 (عندما *لا تريد* ملفات منفصلة)

أحيانًا يكون markdown بملف واحد مفضلاً (مثلاً للإرسال عبر البريد الإلكتروني). غيّر الخيار:

```csharp
mdOptions.ImagesFolder = string.Empty; // disables external folder
mdOptions.ExportImagesAsBase64 = true;
```

لكن تذكر: **استخراج الصور من DOCX** هو الهدف الأساسي لمعظم سير عمل المواقع الثابتة، لذا فإن نهج المجلد عادةً ما يكون الخيار الأفضل.

---

## مثال كامل يعمل (جاهز للنسخ واللصق)

فيما يلي البرنامج الكامل في ملف واحد. فقط استبدل المسارات بمساراتك الخاصة وشغّله.

```csharp
// ---------------------------------------------------------------
// Convert DOCX to Markdown – Extract Images from DOCX
// ---------------------------------------------------------------
// NuGet: Aspose.Words (>= 24.12)
// ---------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageResourceSaver(string targetFolder) => Directory.CreateDirectory(_targetFolder = targetFolder);

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
        if (string.IsNullOrEmpty(ext)) ext = ".png";
        string newFileName = $"img_{Guid.NewGuid():N}{ext}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        args.ResourceFileName = newFileName;
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}

class Program
{
    static void Main()
    {
        // 👉 Adjust these paths:
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMd  = @"C:\Docs\DocWithImages.md";
        string imgFolder = @"C:\Docs\MarkdownResources";

        // Load the DOCX.
        Document doc = new Document(sourceDocx);

        // Set up markdown options with our image saver.
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageResourceSaver(imgFolder)
        };

        // Perform conversion.
        doc.Save(outputMd, mdOptions);

        Console.WriteLine("✅ DOCX successfully converted to Markdown.");
        Console.WriteLine($"📄 Markdown: {outputMd}");
        Console.WriteLine($"🖼️ Images folder: {imgFolder}");
    }
}
```

شغّله باستخدام `dotnet run`. عندما يطبع الطرفية السطر ✅، افتح ملف markdown ويجب أن ترى الصور معروضة بشكل صحيح.

---

## الخلاصة

أصبح لديك الآن **حل كامل وجاهز للإنتاج لتحويل DOCX إلى Markdown واستخراج الصور من DOCX** باستخدام Aspose.Words في C#. الكلمة المفتاحية الأساسية تظهر طوال الدليل، مما يعزز الصلة لمحركات البحث ومساعدي الذكاء الاصطناعي.  

في خطوة واحدة يقوم الكود بـ:

1. تحميل مستند Word.
2. اعتراض كل صورة عبر `IResourceSavingCallback`.
3. حفظ كل صورة في مجلد متوقع باسم فريد.
4. توليد markdown يشير إلى تلك الصور.

من هنا يمكنك:

- Plug

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}