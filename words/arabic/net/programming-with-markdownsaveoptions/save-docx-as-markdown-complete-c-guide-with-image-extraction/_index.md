---
category: general
date: 2026-03-06
description: احفظ ملف docx كملف markdown واستخرج الصور من docx باستخدام Aspose.Words.
  تعلم كيفية تحويل Word إلى markdown والتعامل مع الموارد في بضع خطوات فقط.
draft: false
keywords:
- save docx as markdown
- convert word to markdown
- extract images from docx
- how to extract images
- how to convert word
language: ar
og_description: احفظ ملف docx كملف markdown باستخدام Aspose.Words. يوضح هذا الدليل
  كيفية تحويل Word إلى markdown واستخراج الصور من docx بطريقة نظيفة وقابلة لإعادة
  الاستخدام.
og_title: حفظ ملف docx كـ markdown – دليل C# خطوة بخطوة
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: حفظ ملف docx كـ markdown – دليل C# الكامل مع استخراج الصور
url: /ar/net/programming-with-markdownsaveoptions/save-docx-as-markdown-complete-c-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ docx كـ markdown – دليل C# كامل مع استخراج الصور

هل تساءلت يومًا كيف **تحفظ docx كـ markdown** دون فقدان الصور المدمجة؟ أنت لست الوحيد. يحتاج العديد من المطورين إلى سحب محتوى Word إلى المواقع الثابتة، خطوط توثيق، أو أنظمة إدارة محتوى بدون رأس (headless CMSs)، والحيل التقليدية للنسخ‑اللصق لا تُجدي نفعًا.  

الأخبار السارة؟ باستخدام بضع أسطر من C# و Aspose.Words يمكنك **تحويل word إلى markdown**، استخراج كل صورة، والحفاظ على كل شيء منظمًا في مجلد مخصص. في هذا الدرس سنستعرض العملية بالكامل، نشرح لماذا كل جزء مهم، ونزودك بعينة جاهزة للتنفيذ يمكنك وضعها في أي مشروع .NET.

> **نصيحة احترافية:** إذا كنت تستخدم Aspose.Words بالفعل لمهام مستندات أخرى، فإن هذا النهج لا يضيف تقريبًا أي عبء.

---

## ما ستحتاجه

- **.NET 6+** (أو .NET Framework 4.7.2 وما بعده) – الـ API يعمل على كليهما.
- **Aspose.Words for .NET** – يمكنك الحصول على حزمة تجريبية مجانية عبر NuGet: `Install-Package Aspose.Words`.
- ملف Word (`.docx`) يحتوي على صورة واحدة على الأقل – سنسميه `WithImages.docx`.
- دليل قابل للكتابة على القرص حيث سيعيش ملف الـ Markdown والموارد المستخرجة.

لا حاجة إلى SDKs إضافية، ولا محولات خارجية، فقط C# نقي.  

إذا كنت تسأل *كيف تستخرج الصور* من DOCX، فالجواب يكمن في واجهة `IResourceSavingCallback` – سنغوص فيها قريبًا.

## الخطوة 1: تثبيت وإشارة Aspose.Words

أولًا، أضف المكتبة إلى مشروعك. افتح وحدة تحكم مدير الحزم (Package Manager Console) وشغّل:

```powershell
Install-Package Aspose.Words
```

أو، إذا كنت تفضّل واجهة سطر الأوامر `dotnet` الأحدث:

```bash
dotnet add package Aspose.Words
```

بعد استعادة الحزمة، ستحصل على إمكانية الوصول إلى الأنواع `Document` و `MarkdownSaveOptions` و `IResourceSavingCallback` التي نحتاجها لـ **تحويل word إلى markdown**.

## الخطوة 2: إنشاء رد نداء حفظ الموارد (استخراج الصور)

عند كتابة Aspose.Words لملف Markdown تحتاج أيضًا إلى معرفة **أين** يتم تفريغ الموارد المرتبطة – عادةً الصور. من خلال تنفيذ `IResourceSavingCallback` ستحصل على تحكم كامل في اسم الملف، المجلد، وحتى معالجة التدفق.

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Handles image extraction while saving a document as Markdown.
/// Each image is placed in a dedicated folder with a unique name.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Define a folder relative to the output location.
        string resourceFolder = @"YOUR_DIRECTORY/MarkdownResources/";
        Directory.CreateDirectory(resourceFolder);

        // Build a unique file name: img_0.png, img_1.jpg, etc.
        string extension = Path.GetExtension(args.Path) ?? ".bin";
        args.Path = Path.Combine(resourceFolder, $"img_{args.Index}{extension}");

        // Let Aspose close the stream after writing.
        args.KeepResourceStreamOpen = false;
    }
}
```

**لماذا هذا مهم:** بدون رد نداء، سيقوم Aspose بتفريغ الصور في نفس مجلد ملف الـ Markdown، مما قد يؤدي إلى استبدال ملفات موجودة أو إنشاء أسماء مربكة. كما يجيب رد النداء على سؤال *كيف تستخرج الصور* من خلال توفير مخطط تسمية حتمي.

## الخطوة 3: تحميل ملف DOCX الخاص بك

الآن نقوم بتحميل المستند المصدر إلى الذاكرة. سيقوم مُنشئ `Document` بتحليل ملف `.docx` وبناء نموذج كائن يمكنك التلاعب به.

```csharp
// Adjust the path to point at your actual Word file.
string sourcePath = @"YOUR_DIRECTORY/WithImages.docx";
Document document = new Document(sourcePath);
```

إذا كان الملف يحتوي على جداول أو حواشي أو أنماط معقدة، فستُحفظ جميعها – Aspose يقوم بالعمل الشاق خلف الكواليس.

## الخطوة 4: تكوين خيارات حفظ Markdown

هنا يحدث سحر **حفظ docx كـ markdown**. نقوم بإنشاء مثال من `MarkdownSaveOptions`، نرفق رد النداء الخاص بنا، ونضبط بعض الإعدادات اختياريًا (مثل ما إذا كنا نستخدم Markdown بنكهة GitHub).

```csharp
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // Use GitHub-flavored Markdown (optional but popular).
    ExportImagesAsBase64 = false,          // We want separate image files.
    ResourceSavingCallback = new MyMarkdownResourceCallback(),
    // You can also set other options like TableFormatting, ListExportMode, etc.
};
```

**ملاحظة:** ضبط `ExportImagesAsBase64` إلى `false` يجبر Aspose على كتابة الصور كملفات خارجية، وهذا بالضبط ما نحتاجه لـ **استخراج الصور من docx**.

## الخطوة 5: حفظ المستند كـ Markdown

أخيرًا، استدعِ `Save` مع مسار الإخراج المطلوب والخيارات التي أعددناها للتو. سيُطلق رد النداء لكل مورد مدمج، مما يُنشئ بنية مجلد نظيفة.

```csharp
string outputMarkdown = @"YOUR_DIRECTORY/Doc.md";
document.Save(outputMarkdown, markdownOptions);
```

بعد تنفيذ هذا السطر ستحصل على:

- `Doc.md` – تمثيل الـ Markdown لمحتوى Word الخاص بك.
- `MarkdownResources/` – مجلد يحتوي على `img_0.png`، `img_1.jpg`، إلخ.

يمكنك فتح `Doc.md` في أي محرر، وستشير روابط الصور إلى الملفات التي تم إنشاؤها حديثًا.

## مثال كامل يعمل (جاهز للنسخ واللصق)

فيما يلي البرنامج الكامل، جاهز للترجمة. استبدل العنصر النائب `YOUR_DIRECTORY` بمسار مطلق أو نسبي يعمل على جهازك.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣  Set up paths
        string baseDir = @"C:\Temp\MarkdownDemo"; // <-- change this
        string sourceDoc = Path.Combine(baseDir, "WithImages.docx");
        string outputMd = Path.Combine(baseDir, "Doc.md");

        // 2️⃣  Load the Word document
        Document doc = new Document(sourceDoc);

        // 3️⃣  Prepare Markdown options with our custom callback
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ExportImagesAsBase64 = false,
            ResourceSavingCallback = new MyMarkdownResourceCallback()
        };

        // 4️⃣  Save as Markdown – images will be extracted automatically
        doc.Save(outputMd, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown file: {outputMd}");
        Console.WriteLine($"Images folder: {Path.Combine(baseDir, "MarkdownResources")}");
    }
}

/// <summary>
/// Custom callback that decides where each image gets saved.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        string resourceFolder = Path.Combine(
            Path.GetDirectoryName(args.Path) ?? "", "MarkdownResources");
        Directory.CreateDirectory(resourceFolder);

        string ext = Path.GetExtension(args.Path) ?? ".bin";
        args.Path = Path.Combine(resourceFolder, $"img_{args.Index}{ext}");
        args.KeepResourceStreamOpen = false;
    }
}
```

**الناتج المتوقع:**  
تشغيل البرنامج يطبع رسالة نجاح وينشئ ملف الـ Markdown بالإضافة إلى مجلد `MarkdownResources` المملوء بالصور المستخرجة. افتح `Doc.md` – ستلاحظ صيغة صورة Markdown القياسية مثل `![](MarkdownResources/img_0.png)`.

## الأسئلة المتكررة

### كيف يمكنني **تحويل word إلى markdown** دون فقدان التنسيق؟

يحتفظ Aspose.Words بمعظم التنسيقات (العناوين، الغامق، القوائم، الجداول). إذا كنت تحتاج إلى تحويل أكثر دقة، عدل `MarkdownSaveOptions` – على سبيل المثال، اضبط `ExportHeadersAsHtml = false` للحفاظ على عناوين نصية بسيطة، أو عدل `TableFormatting` للجداول بصيغة markdown.

### ماذا لو كان مستندي يحتوي على **عدة صور بنفس الاسم**؟

يستخدم رد النداء قيمة `args.Index`، وهي فريدة لكل مورد، مما يضمن عدم حدوث تصادمات. يمكنك أيضًا دمج اسم الملف الأصلي (`args.Path`) في الاسم الجديد إذا كنت تفضّل مخططًا أكثر قابلية للقراءة.

### هل يمكنني **استخراج الصور** إلى موقع مختلف لكل مستند؟

بالتأكيد. داخل `ResourceSaving`، لديك وصول كامل إلى كائن `args`، لذا يمكنك حساب مجلد بناءً على اسم ملف المصدر، التاريخ، أو أي منطق مخصص.

### هل يعمل هذا مع ملفات **.doc** (ثنائية)؟

نعم. يدعم Aspose.Words كلًا من `.doc` و `.docx`. يعمل نفس الكود؛ فقط وجه `sourceDoc` إلى الملف المناسب.

### كيف أتعامل مع **مستندات كبيرة** بكفاءة؟

اضبط `args.KeepResourceStreamOpen = false` (كما هو موضح) حتى يغلق المكتبة تدفق كل صورة بعد الكتابة. كما يمكنك التفكير في تدفق ملف المصدر إذا كانت الذاكرة مصدر قلق: `Document doc = new Document(new FileStream(sourceDoc, FileMode.Open, FileAccess.Read));`

## الحالات الحدية وأفضل الممارسات

- **الموارد غير الصور** (مثل كائنات OLE المدمجة) ستُفعّل رد النداء أيضًا. إذا كنت تريد الصور فقط، تحقق من `args.ResourceType == ResourceType.Image` قبل الحفظ.
- **أسماء ملفات Unicode**: استخدم `Path.GetInvalidFileNameChars()` لتطهير أي منطق تسمية مخصص.
- **نصيحة أداء:** أعد استخدام مثال واحد من `MarkdownSaveOptions` إذا كنت تحول العديد من الملفات دفعة واحدة – يمكن مشاركة كائن رد النداء.
- **توافق الإصدارات:** يستهدف الكود Aspose.Words 24.10 وما بعده. قد تحتوي الإصدارات السابقة على مساحات أسماء مختلفة قليلاً.

## الخلاصة

أصبح لديك الآن حل قوي وشامل من البداية إلى النهاية لـ **حفظ docx كـ markdown**، **تحويل word إلى markdown**، و **استخراج الصور من docx** باستخدام C#. من خلال الاستفادة من `IResourceSavingCallback` تتحكم تمامًا في مكان وضع كل صورة، مما يجعل الناتج جاهزًا لمولدات المواقع الثابتة، خطوط التوثيق، أو أي سير عمل يستهلك Markdown عادي.

هل أنت مستعد للخطوة التالية؟ جرّب تحويل مجموعة من ملفات DOCX في حلقة، أو جرب علامة `ExportImagesAsBase64` لتضمين الصور مباشرةً في الـ Markdown – كلاهما على بعد بضع أسطر فقط.  

إذا وجدت هذا الدليل مفيدًا، لا تتردد في مشاركته، وضع نجمة على المستودع حيث تحتفظ بمقتطفاتك، أو اترك تعليقًا بتعديلاتك الخاصة. ترميز سعيد!

![مخطط تدفق يوضح عملية حفظ docx كـ markdown](https://example.com/placeholder.png "مخطط عمل حفظ docx كـ markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}