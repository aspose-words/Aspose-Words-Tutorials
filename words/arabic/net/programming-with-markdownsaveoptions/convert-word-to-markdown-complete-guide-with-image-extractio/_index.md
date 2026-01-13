---
category: general
date: 2026-01-13
description: حوّل ملفات Word إلى markdown واستخرج الصور من ملفات docx في سير عمل سلس
  واحد. تعلّم كيفية تصدير صور Word وإنشاء markdown من ملفات docx مع أمثلة على الشيفرة.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- convert docx to markdown with images
- how to export word images
- generate markdown from docx
language: ar
og_description: حوّل ملفات Word إلى markdown بسرعة، وتعلم كيفية تصدير صور Word، وأنشئ
  markdown من ملفات docx باستخدام كود C# خطوة بخطوة.
og_title: تحويل Word إلى Markdown – دليل كامل مع استخراج الصور
tags:
- Aspose.Words
- C#
- Markdown
- Document Conversion
title: تحويل Word إلى Markdown – دليل شامل مع استخراج الصور
url: /ar/net/programming-with-markdownsaveoptions/convert-word-to-markdown-complete-guide-with-image-extractio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحويل Word إلى Markdown – دليل شامل مع استخراج الصور

هل احتجت يوماً إلى **تحويل Word إلى markdown** ولكنك كنت قلقاً من فقدان الصور؟ لست وحدك. يواجه العديد من المطورين هذه المشكلة عند ترحيل الوثائق أو المواقع الثابتة، وتؤدي الصور المفقودة إلى فوضى تامة.  

في هذا الدرس سنستعرض طريقة برمجية نظيفة **لتحويل Word إلى markdown**، **استخراج الصور من docx**، والحصول على مجلد markdown جاهز للنشر. في النهاية ستعرف بالضبط *كيفية تصدير صور Word* و*إنشاء markdown من docx* باستخدام Aspose.Words for .NET.

> **نصيحة احترافية:** نفس النهج يعمل مع مكتبات .NET أخرى تدعم استدعاءات الموارد – فقط استبدل `MarkdownSaveOptions` بالفئة المناسبة.

![مثال تحويل Word إلى Markdown](convert_word_to_markdown.png)

## ما ستحققه

- تحميل ملف `.docx` يحتوي على صور مدمجة أو عائمة.  
- حفظ المستند كملف markdown مع سحب كل صورة إلى مجلد مخصص.  
- الحصول على ملف markdown يربط الصور المستخرجة بشكل صحيح، بحيث يراها مولد الموقع الثابت أو وثائقك فوراً.  

بدون نسخ ‑ لصق يدوي، بدون روابط مكسورة، وبدون أخطاء 404 للصور الغامضة.

## المتطلبات المسبقة- .NET 6.0 أو أحدث (الكود يعمل أيضاً على .NET Framework 4.7+).  
- حزمة NuGet Aspose.Words for .NET (`Aspose.Words` الإصدار 23.12 أو أحدث).  
- فهم أساسي للغة C# وإدارة الملفات.  

إذا كان لديك هذه المتطلبات، لنبدأ.

## الخطوة 1 – تثبيت Aspose.Words

أولاً، أضف المكتبة إلى مشروعك:

```bash
dotnet add package Aspose.Words
```

هذا السطر الواحد يجلب لك كل ما تحتاجه **لتحويل docx إلى markdown مع الصور**. حاجة للبحث عن DLL إضافية.

## الخطوة 2 – تحميل مستند Word المصدر

نبدأ بإنشاء كائن `Document` يشير إلى ملف `.docx` الذي يحتوي على صورك.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Replace with the actual path to your Word file
string sourcePath = @"C:\Projects\Docs\WithImages.docx";

Document doc = new Document(sourcePath);
```

لماذا هذا مهم: فئة `Document` تمثل ملف Word بالكامل، وتمنحنا الوصول إلى النص، الأنماط، ومجموعة الموارد الحيوية حيث تعيش الصور.  

## الخطوة 3 – إعداد خيارات حفظ Markdown مع استدعاء الموارد

تتيح لنا Aspose.Words ربط عملية الحفظ عبر `IResourceSavingCallback`. هذا هو جوهر **كيفية تصدير صور Word** أثناء التحويل.

```csharp
// Define where the markdown and images will be written
string outputFolder = @"C:\Projects\Docs\Output";
string markdownPath = Path.Combine(outputFolder, "Doc.md");

// Ensure the resources sub‑folder exists
string resourcesFolder = Path.Combine(outputFolder, "Resources");
Directory.CreateDirectory(resourcesFolder);

// Set up the markdown options and attach our callback
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new ImageSavingCallback(resourcesFolder)
};
```

لاحظ أننا نمرر `resourcesFolder` إلى مُنشئ الاستدعاء – هذا يبقي المنطق منظمًا ويجعل مسار المجلد قابلًا لإعادة الاستخدام.

## الخطوة 4 – تنفيذ استدعاء حفظ الصورة

إليك الفئة التي تقرر **أين وكيف يتم حفظ كل صورة**. تعطي كل صورة اسم ملف فريد لتجنب التصادمات.

```csharp
class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _folder;

    public ImageSavingCallback(string folder)
    {
        _folder = folder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique file name like img_7f9c3a2b-1e4d.png
        string uniqueName = $"img_{Guid.NewGuid()}{args.Extension}";
        string fullPath = Path.Combine(_folder, uniqueName);

        // Tell Aspose to write the image to this path
        args.FileName = fullPath;
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}
```

**لماذا نستخدم GUID؟** لأن مستندات Word غالبًا ما تحتوي على صور متعددة تحمل نفس الاسم الأصلي. بإنشاء GUID نضمن أن كل ملف مميز، وهو أمر أساسي عند **استخراج الصور من docx** لعملية markdown.

## الخطوة 5 – حفظ المستند كـ Markdown

الآن نُجري التحويل أخيرًا. الاستدعاء يعمل تلقائيًا لكل مورد خارجي (أي كل صورة).

```csharp
// Perform the conversion
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
Console.WriteLine($"🖼️ Images extracted to: {resourcesFolder}");
```

عند انتهاء عملية الحفظ، ستجد:

- `Doc.md` – ملف markdown يحتوي على روابط صور مثل `![Image](Resources/img_...png)`.  
- `Resources/` – مجلد مليء بملفات PNG/JPEG التي كانت داخل مستند Word الأصلي.

هذا هو كامل خط أنابيب **تحويل Word إلى markdown** في بضع عشرات السطر فقط.

## التحقق من النتيجة

افتح `Doc.md` في أي عارض markdown (VS Code، GitHub، MkDocs). يجب أن ترى النص تمامًا كما هو في ملف Word الأصلي، وتظهر كل صورة بشكل صحيح. إذا ظهرت صورة مكسورة، تحقق من أن المسار النسبي في markdown يطابق اسم المجلد الفعلي – الاستدعاء يستخدم بالفعل `Resources/`، لذا احتفظ بهذا المجلد بجوار ملف markdown.

## أسئلة شائعة وحالات خاصة

### “ماذا لو كان ملف Word يحتوي على صور SVG أو EMF؟”

يقوم Aspose.Words تلقائيًا بتحويل الصيغ غير المدعومة إلى PNG أثناء الاستدعاء. ستحصل على صورة صالحة، رغم أن امتداد الملف سيكون `.png`. إذا كنت بحاجة إلى الصيغة الأصلية، يمكنك فحص `args.Extension` وتعديل منطق التحويل.

### “هل يمكنني التحكم في جودة الصورة؟”

نعم. داخل `ResourceSaving` يمكنك تحميل التيار إلى `System.Drawing.Image`، تعديل الحجم أو إعادة الترميز، ثم كتابة التيار المعدل مرة أخرى. هذا مفيد عندما تريد **إنشاء markdown من docx** لموقع ويب يتطلب أصولًا أصغر حجمًا.

### “ماذا عن الخطوط المدمجة أو الموارد الأخرى؟”

يتم استدعاء `ResourceSavingCallback` لأي مورد خارجي، ليس فقط الصور. إذا كنت تحتاج أيضًا لاستخراج صوت أو فيديو أو كائنات OLE، عالجها في نفس الاستدعاء – `args.Extension` سيخبرك بالنوع.

### “هل صيغة markdown متوافقة مع GitHub؟”

يتبع Aspose.Words مواصفة CommonMark، التي يستخدمها GitHub. لذا العناوين والجداول والكتل البرمجية تُعرض كما هو متوقع.

## مثال كامل جاهز للتنفيذ (انسخه‑ألصقه)

فيما يلي البرنامج الكامل الذي يمكنك وضعه في تطبيق Console وتشغيله فورًا.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main()
        {
            // Paths – adjust to your environment
            string sourcePath = @"C:\Projects\Docs\WithImages.docx";
            string outputFolder = @"C:\Projects\Docs\Output";
            string markdownPath = Path.Combine(outputFolder, "Doc.md");
            string resourcesFolder = Path.Combine(outputFolder, "Resources");

            // Ensure output directories exist
            Directory.CreateDirectory(outputFolder);
            Directory.CreateDirectory(resourcesFolder);

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Configure markdown options with our callback
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback(resourcesFolder)
            };

            // Save as markdown – images are extracted automatically
            doc.Save(markdownPath, mdOptions);

            Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
            Console.WriteLine($"🖼️ Images extracted to: {resourcesFolder}");
        }
    }

    // Callback that writes each image to the Resources folder
    class ImageSavingCallback : IResourceSavingCallback
    {
        private readonly string _folder;

        public ImageSavingCallback(string folder) => _folder = folder;

        public void ResourceSaving(ResourceSavingArgs args)
        {
            string uniqueName = $"img_{Guid.NewGuid()}{args.Extension}";
            string fullPath = Path.Combine(_folder, uniqueName);
            args.FileName = fullPath;
            args.Stream = new FileStream(fullPath, FileMode.Create);
        }
    }
}
```

شغّل البرنامج، افتح `Output\Doc.md`، وسترى ملف markdown منسق تمامًا مع جميع الصور محفوظة. 🎉

## الخلاصة

غطينا كل ما تحتاجه **لتحويل word إلى markdown**، **استخراج الصور من docx**، و**إنشاء markdown من docx** دون فقدان أي بكسل. الفكرة الأساسية؟ الاستفادة من `ResourceSavingCallback` في Aspose.Words لمنحك تحكمًا دقيقًا في طريقة حفظ كل صورة، مما يجعل عملية التحويل موثوقة وقابلة للتكرار.

### ما التالي؟

- **تحويل دفعي:** كرر العملية على مجلد من ملفات `.docx` وانتج موقع markdown خلال دقائق.  
- **تحسين الصور:** دمج مكتبة مثل `ImageSharp` لتغيير حجم الصور أو ضغطها أثناء التحويل.  
- **تنسيق markdown مخصص:** عدل `MarkdownSaveOptions` (مثل `ExportHeadersAsHtml`) لتتناسب مع توقعات مولد الموقع الثابت الخاص بك.  

لا تتردد في التجربة، وإذا واجهت أي صعوبات، اترك تعليقًا أدناه. برمجة سعيدة، واستمتع بالجسر السلس بين Word و markdown!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}