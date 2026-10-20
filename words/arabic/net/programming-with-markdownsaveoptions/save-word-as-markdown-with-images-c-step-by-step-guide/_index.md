---
category: general
date: 2026-02-12
description: تعلم كيفية حفظ مستند Word كملف markdown وتحويل ملف docx إلى markdown
  مع استخراج الصور، باستخدام Aspose.Words في C#.
draft: false
keywords:
- save word as markdown
- convert docx to markdown
- extract images from docx
- markdown export with images
- generate unique image names
language: ar
og_description: احفظ المستند كملف ماركداون واستخرج الصور مرة واحدة. يوضح لك هذا الدليل
  كيفية تحويل docx إلى ماركداون بأسماء صور فريدة.
og_title: حفظ ملف Word كـ Markdown مع الصور – دليل C#
tags:
- Aspose.Words
- C#
- Markdown
title: حفظ ملف Word كـ Markdown مع الصور – دليل خطوة بخطوة بلغة C#
url: /ar/net/programming-with-markdownsaveoptions/save-word-as-markdown-with-images-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ مستند Word كـ markdown – مثال كامل C#

هل احتجت يوماً إلى **حفظ مستند Word كـ markdown** لكنك لم تكن متأكدًا من كيفية الحفاظ على الصور المدمجة؟ لست وحدك. في العديد من المشاريع، التحويل السريع وغير المتقن يفقد الصور، مما يتركك بملف markdown خالٍ.  

في هذا الدرس سنستعرض حلاً كاملاً يقوم بـ **convert docx to markdown**، **extract images from docx**، وحتى **generate unique image names** لكل صورة. في النهاية ستحصل على مقتطف جاهز للتنفيذ ينتج تصدير markdown نظيف مع الصور جنبًا إلى جنب في مجلد تختاره.

> **ما ستحصل عليه:** برنامج C# قابل للتنفيذ، شرح واضح لكل سطر، ونصائح عملية لتتمكن من تعديل الكود ليتناسب مع بنية المجلدات أو نظام التسمية الخاص بك.

## ما ستحتاجه

- .NET 6+ (أو .NET Framework 4.7+ – الـ API يعمل بنفس الطريقة)
- Visual Studio 2022 أو أي محرر يدعم C#
- رخصة Aspose.Words for .NET (أو نسخة تجريبية مجانية). التثبيت عبر NuGet:

```bash
dotnet add package Aspose.Words
```

لا توجد مكتبات طرف ثالث أخرى مطلوبة.

---

## الخطوة 1 – إعداد المشروع وإضافة Aspose.Words

للبدء، أنشئ تطبيق console (أو دمج الكود في مشروع موجود).

```csharp
// Program.cs – entry point
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main()
        {
            // We'll call the conversion helper later.
            MarkdownConverter.Convert(@"C:\Docs\input.docx", @"C:\Docs\output");
        }
    }
}
```

> **نصيحة احترافية:** احفظ مجلدات المصدر والإخراج منفصلة؛ هذا يمنع الكتابة فوق الملفات عن طريق الخطأ عندما تقوم بتشغيل التحويل عدة مرات.

## الخطوة 2 – تنفيذ Callback لـ **extract images from docx**

تتيح لك Aspose.Words ربط عملية الحفظ عبر `IResourceSavingCallback`. هنا نـ **generate unique image names** ونحدد مكان حفظ الملفات.

```csharp
// MyResourceCallback.cs – handles image extraction
class MyResourceCallback : IResourceSavingCallback
{
    // The folder where images will be stored.
    private readonly string _imagesFolder;

    public MyResourceCallback(string imagesFolder)
    {
        _imagesFolder = imagesFolder;
        // Ensure the folder exists.
        Directory.CreateDirectory(_imagesFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only process image resources; ignore CSS, fonts, etc.
        if (args.ResourceType != ResourceType.Image)
        {
            // Let Aspose handle non‑image resources the default way.
            return;
        }

        // Create a unique file name – e.g., img_3fa85f64‑5717‑4562‑b3fc‑2c963f66afa6.png
        string uniqueName = $"img_{Guid.NewGuid()}{args.FileExtension}";
        string fullPath = Path.Combine(_imagesFolder, uniqueName);

        // Tell Aspose where to write the image.
        args.FileName = fullPath;
        args.Stream = new FileStream(fullPath, FileMode.Create, FileAccess.Write);
    }
}
```

**لماذا نحتاج Callback؟**  
بدونها، تقوم Aspose بإسقاط الصور في نفس مجلد ملف markdown بأسماء عامة (`image001.png`). الـ Callback يمنحك التحكم الكامل—مثالي لمتطلبات **markdown export with images** وللحفاظ على تنظيم المشروع.

## الخطوة 3 – تحميل DOCX وتحضير **MarkdownSaveOptions**

الآن نحمل المستند في الذاكرة ونخبر Aspose أننا نريد ملف markdown.

```csharp
// MarkdownConverter.cs – core conversion logic
static class MarkdownConverter
{
    public static void Convert(string docxPath, string outputRoot)
    {
        // 1️⃣ Load the source document.
        Document doc = new Document(docxPath);

        // 2️⃣ Define where images will live.
        string imagesFolder = Path.Combine(outputRoot, "Images");

        // 3️⃣ Wire up the callback that extracts images.
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyResourceCallback(imagesFolder)
        };

        // 4️⃣ Ensure the output folder exists.
        Directory.CreateDirectory(outputRoot);

        // 5️⃣ Build the markdown file name.
        string markdownPath = Path.Combine(outputRoot, "output.md");

        // 6️⃣ Save – this triggers the callback for every image.
        doc.Save(markdownPath, mdOptions);
    }
}
```

**نقاط رئيسية**

- `ResourceSavingCallback` هو الجسر الذي يتيح لنا **extract images from docx**.
- بوضع الصور في `outputRoot\Images`، سيشير ملف markdown إليها بمسارات نسبية مثل `Images/img_…png`. هذا يحقق هدف **markdown export with images**.
- استدعاء `Guid.NewGuid()` يضمن أن كل صورة تحصل على **unique image name**، مما يمنع التعارض عندما تظهر الصورة نفسها عدة مرات.

## الخطوة 4 – تشغيل المحول والتحقق من النتيجة

قم بترجمة وتشغيل تطبيق console:

```bash
dotnet run
```

بعد التنفيذ يجب أن ترى بنية مجلد مشابهة لـ:

```
C:\Docs\output\
│   output.md
└───Images\
        img_a1b2c3d4-e5f6-7890-abcd-ef1234567890.png
        img_fedcba98-7654-3210-zyxw-vutsrqponmlk.jpg
```

افتح `output.md` في أي عارض markdown (VS Code، GitHub، إلخ). ستجد أسطرًا مثل:

```markdown
![Image](Images/img_a1b2c3d4-e5f6-7890-abcd-ef1234567890.png)
```

هذا هو نتيجة **save word as markdown** التي كنا نبحث عنها—كل صورة مرتبطة بشكل صحيح ومخزنة باسم مميز.

## الخطوة 5 – تنوعات شائعة وحالات حافة

### التعامل مع صيغ صور مختلفة

تقوم Aspose تلقائيًا بتعيين `args.FileExtension` بناءً على نوع الصورة الأصلي (png، jpg، gif، إلخ). إذا أردت جميع الصور بصيغة PNG، يمكنك تجاوز الامتداد:

```csharp
args.FileName = Path.Combine(_imagesFolder,
    $"img_{Guid.NewGuid()}.png");
args.Stream = new FileStream(args.FileName, FileMode.Create, FileAccess.Write);
```

### تحويل عدة ملفات DOCX دفعيًا

غلف استدعاء `Convert` داخل حلقة:

```csharp
foreach (var file in Directory.GetFiles(@"C:\Docs\Batch", "*.docx"))
{
    string folder = Path.Combine(@"C:\Docs\BatchOutput", Path.GetFileNameWithoutExtension(file));
    MarkdownConverter.Convert(file, folder);
}
```

### عندما لا يحتوي المستند على صور

الـ callback ببساطة لا يُستدعى، وستحصل على ملف markdown لا يحتوي على روابط صور. لا يُطرح أي خطأ—مناسب لسيناريوهات **convert docx to markdown** التي يكون المصدر نصيًا فقط.

## الخطوة 6 – نصائح عملية ومخاطر محتملة

- **الأداء:** إذا كنت تعالج ملفات ضخمة (مئات الـ MB)، فكر في إعادة استخدام كائن `Document` واحد وكتابة الصور إلى تدفق مؤقت أولًا، ثم نقلها إلى المجلد النهائي.  
- **الترخيص:** الرخصة التجريبية تُضيف علامة مائية إلى الناتج. تأكد من تطبيق ملف الترخيص الصحيح (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).  
- **طول المسارات:** مسارات Windows التي تتجاوز 260 حرفًا قد تُسبب استثناء `PathTooLongException`. حافظ على `outputRoot` قصيرًا أو فعّل دعم المسارات الطويلة.  
- **الكتابة فوق الملفات:** نظام التسمية القائم على GUID يمنع الكتابة فوق الملفات، لكن إذا شغلت المحول مرارًا على نفس المصدر، سيتراكم عدد كبير من الصور. نظّف مجلد `Images` بين كل تشغيل إذا لم تكن بحاجة إلى السجل.

---

## الخاتمة

غطّينا كل ما تحتاجه لـ **save word as markdown** مع الحفاظ على جميع الصور، **convert docx to markdown**، و**generate unique image names** لتصدير منظم. المثال الكامل القابل للتنفيذ موجود في المقاطع البرمجية أعلاه، لذا يمكنك نسخه، تعديل مسارات المجلدات، وتشغيله اليوم.

بعد ذلك، قد تستكشف **markdown export with images** لصيغ أخرى (HTML، PDF) أو تدمج المحول في API ASP.NET Core يقدم markdown عند الطلب. نمط الـ callback نفسه يعمل لاستخراج الخطوط، ملفات الأنماط، أو حتى أجزاء XML مخصصة—فقط تحقق من `args.ResourceType` وتعامل وفقًا لذلك.

برمجة سعيدة، ولتكن ملفات markdown الخاصة بك دائمًا غنية بالصور!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}