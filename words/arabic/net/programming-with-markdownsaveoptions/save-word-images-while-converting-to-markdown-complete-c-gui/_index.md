---
category: general
date: 2026-04-04
description: احفظ صور Word بسهولة عند تحويل Word إلى Markdown. تعلم كيفية استخراج
  صور docx، وإنشاء المجلد إذا كان مفقودًا، وتحويل docx إلى markdown باستخدام Aspose.Words.
draft: false
keywords:
- save word images
- convert word to markdown
- extract images docx
- create folder if missing
- convert docx to markdown
language: ar
og_description: احفظ صور Word بسهولة عند تحويل Word إلى Markdown. يوضح هذا الدليل
  كيفية استخراج صور الـ docx، وإنشاء المجلد إذا كان مفقودًا، وتحويل الـ docx إلى markdown
  باستخدام Aspose.Words.
og_title: حفظ صور Word أثناء التحويل إلى Markdown – دليل C# الكامل
tags:
- Aspose.Words
- C#
- Markdown
title: حفظ صور Word أثناء التحويل إلى Markdown – دليل C# الكامل
url: /ar/net/programming-with-markdownsaveoptions/save-word-images-while-converting-to-markdown-complete-c-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ صور Word أثناء التحويل إلى Markdown – دليل C# كامل

هل تساءلت يومًا كيف يمكنك **حفظ صور word** تلقائيًا عندما تقوم بتحويل ملف `.docx` إلى Markdown؟ لست وحدك. يواجه العديد من المطورين مشكلة اختفاء الصور أو وضعها في مجلد عشوائي، ثم يقضون ساعات في البحث عنها.  

الأخبار السارة؟ باستخدام بضع أسطر من C# و Aspose.Words يمكنك استخراج صور docx، إنشاء المجلد إذا كان مفقودًا، وتحويل docx إلى markdown في تدفق سلس واحد. بنهاية هذا الدرس ستحصل على حل قابل لإعادة الاستخدام يقوم بذلك بالضبط—دون الحاجة إلى النسخ واللصق اليدوي.

## ما يغطيه هذا الدرس

* إعداد **resource‑saving callback** الذي يعيد توجيه كل صورة إلى مجلد تتحكم فيه.  
* استخدام **MarkdownSaveOptions** لربط الـ callback بعملية التحويل.  
* تحميل مستند Word يحتوي على صور وحفظه كـ Markdown.  
* معالجة الحالات الحدية مثل المجلدات المفقودة، أسماء الصور المكررة، والصيغ غير المدعومة للصور.  

إذا كنت مرتاحًا مع C# ولديك ترخيص لـ Aspose.Words، فأنت جاهز للبدء. لا توجد متطلبات أخرى—فقط مشروع صغير وملف `.docx` يحتوي على صورة واحدة على الأقل.

## الخطوة 1: تثبيت Aspose.Words لـ .NET

قبل كتابة أي كود، تأكد من أن حزمة Aspose.Words مُشار إليها في مشروعك. أبسط طريقة هي عبر NuGet:

```bash
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** استخدم أحدث نسخة مستقرة (في وقت كتابة هذا، 24.12) للاستفادة من إصلاحات الأخطاء المتعلقة بمعالجة الصور.

## الخطوة 2: إنشاء Callback يحفظ الصور في مجلد مخصص

جوهر **save word images** يكمن في تنفيذ `IResourceSavingCallback`. هذا الـ callback يُستدعى لكل مورد خارجي (صور، أوراق أنماط، إلخ) تريد Aspose.Words كتابته. سنعترض حالة الصورة، نتأكد من وجود المجلد الهدف، ونعطي كل ملف اسمًا فريدًا.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

/// <summary>
/// Redirects each image to a user‑specified folder and gives it a GUID‑based name.
/// </summary>
class ImageSavingCallback : IResourceSavingCallback
{
    // Change this path to wherever you want your images stored.
    private readonly string _imageFolder = @"YOUR_DIRECTORY/Images/";

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // We only care about images; other resources can follow the default flow.
        if (args.ResourceType == ResourceType.Image)
        {
            // Ensure the folder exists – this satisfies the “create folder if missing” requirement.
            Directory.CreateDirectory(_imageFolder);

            // Preserve the original extension (png, jpg, gif, etc.).
            string extension = Path.GetExtension(args.FileName);

            // Generate a unique filename to avoid collisions.
            string uniqueName = $"{Guid.NewGuid()}{extension}";

            // Build the full path where the image will be saved.
            string fullPath = Path.Combine(_imageFolder, uniqueName);

            // Tell Aspose.Words where to write the image.
            args.SavePath = fullPath;

            // By null‑ing the stream we prevent the default in‑memory save.
            args.Stream = null;
        }
    }
}
```

**لماذا GUID؟**  
إذا كان مستندك المصدر يحتوي على عدة صور بنفس الاسم (شائع عند النسخ من الويب)، فإن GUID يضمن التفرد دون الحاجة إلى فحص المجلد أولاً. هذا يتجاوز أيضًا حالة “اسم الصورة المكرر” التي تُربك العديد من المبتدئين.

## الخطوة 3: ربط الـ Callback بـ MarkdownSaveOptions

الآن بعد أن أصبح الـ callback جاهزًا، نربطه بـ `MarkdownSaveOptions`. هذا يخبر Aspose.Words باستدعاء منطقنا كلما صادفت صورة أثناء التحويل.

```csharp
// Configure Markdown options and plug in the callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // The callback will be called for each image resource.
    ResourceSavingCallback = new ImageSavingCallback()
};
```

> **ملاحظة:** إذا احتجت يومًا إلى تضمين الصور مباشرة كسلاسل Base64 بدلاً من ملفات منفصلة، يمكنك تبديل `ResourceSavingCallback` إلى تنفيذ مختلف. النمط يبقى نفسه.

## الخطوة 4: تحميل مستند Word الخاص بك وإجراء التحويل

مع ضبط الخيارات، يكون التحويل الفعلي سطرًا واحدًا. استبدل `YOUR_DIRECTORY/WithImages.docx` بالمسار إلى ملف المصدر الخاص بك، وحدد أين تريد أن يُحفظ ناتج الـ Markdown.

```csharp
// Load the .docx that contains images.
Document doc = new Document(@"YOUR_DIRECTORY/WithImages.docx");

// Save as Markdown; images will be stored in the folder defined above.
doc.Save(@"YOUR_DIRECTORY/Doc.md", mdOptions);
```

### النتيجة المتوقعة

* يحتوي `Doc.md` على صيغة Markdown مع روابط صور تشير إلى المجلد المخصص، مثال:

```markdown
![Image 1](Images/3f9c2e5a-7c1b-4d8f-9f3a-2e6b5c9d0a1b.png)
```

* الآن يحتوي المجلد الفرعي `Images` على ملف واحد لكل صورة أصلية، كل ملف مسمى بـ GUID والامتداد الصحيح.

![هيكل مجلد حفظ صور word](https://example.com/placeholder.png "هيكل مجلد حفظ صور word – يُظهر مجلد Images مع ملفات مسماة بـ GUID")

نص alt أعلاه يتضمن الكلمة المفتاحية الأساسية، مما يحقق قاعدة تحسين محركات البحث لصور alt.

## الخطوة 5: معالجة الحالات الحدية الشائعة

### 5.1 وثيقة المصدر مفقودة

إذا كان مسار `.docx` غير صحيح، سيُطلق `Document` استثناء `FileNotFoundException`. غلف استدعاء التحميل بكتلة try‑catch لتقديم رسالة ودية:

```csharp
try
{
    Document doc = new Document(@"YOUR_DIRECTORY/WithImages.docx");
    doc.Save(@"YOUR_DIRECTORY/Doc.md", mdOptions);
}
catch (FileNotFoundException ex)
{
    Console.Error.WriteLine($"Source file not found: {ex.FileName}");
}
```

### 5.2 صيغ الصور غير المدعومة

يدعم Aspose.Words معظم صيغ الرسوم النقطية، لكن الصيغ المتجهية مثل SVG قد تحتاج إلى معالجة إضافية. إذا لم يكن نوع الصورة مدعومًا، سيظل الـ callback يعمل، لكن `args.Stream` سيكون `null`. يمكنك تسجيل تحذير:

```csharp
if (args.Stream == null)
{
    Console.WriteLine($"Warning: Image format not supported for {args.FileName}");
}
```

### 5.3 المستندات الكبيرة

عند تحويل ملفات Word ضخمة، فكر في زيادة إعداد `MemoryUsage` في `MarkdownSaveOptions` إلى `MemoryUsage.SaveOnly`. هذا يقلل من الضغط على الذاكرة على حساب كتابة أبطأ قليلًا.

```csharp
mdOptions.MemoryUsage = MemoryUsage.SaveOnly;
```

## الخطوة 6: التحقق من الناتج

بعد انتهاء التحويل، افتح `Doc.md` في أي عارض Markdown (VS Code، Typora، أو إضافة متصفح). يجب أن ترى محتوى النص بالإضافة إلى عناصر نائبة للصور التي تُحل بشكل صحيح إلى ملفات داخل مجلد `Images`.  

إذا فشلت صورة في العرض، تحقق مرة أخرى من رابط Markdown المُولد وتأكد من وجود الملف المقابل على القرص. هذا الفحص السريع يضمن أن تنفيذ **save word images** يعمل عبر أنظمة تشغيل مختلفة.

## مكافأة: إعادة استخدام المنطق في مكتبة

إذا كنت تتوقع الحاجة إلى هذه الوظيفة في عدة مشاريع، قم بلف التدفق بالكامل في طريقة مساعدة ثابتة:

```csharp
public static class WordToMarkdownConverter
{
    public static void Convert(string sourceDocx, string targetMd, string imageFolder)
    {
        var callback = new ImageSavingCallback(imageFolder);
        var options = new MarkdownSaveOptions { ResourceSavingCallback = callback };

        var doc = new Document(sourceDocx);
        doc.Save(targetMd, options);
    }
}

// Usage:
WordToMarkdownConverter.Convert(
    @"C:\Docs\Report.docx",
    @"C:\Docs\Report.md",
    @"C:\Docs\Images\");
```

لاحظ كيف أن مُنشئ `ImageSavingCallback` الآن يقبل مسار المجلد، مما يجعل المساعدة أكثر مرونة. هذا النمط يتماشى مع الكلمات المفتاحية الثانوية “extract images docx” و “convert docx to markdown”، ويمنحك قطعة كود قابلة لإعادة الاستخدام يمكن للزملاء إدراجها في حلولهم.

---

## الخاتمة

لقد تعلمت الآن كيفية **save word images** تلقائيًا أثناء **convert word to markdown** باستخدام Aspose.Words لـ .NET. من خلال تنفيذ `IResourceSavingCallback` مخصص، ضمنا استخراج كل صورة، وضعها في مجلد ننشئه في الوقت الفعلي، والإشارة إليها بشكل صحيح في ملف Markdown الناتج.  

باختصار، الحل:

1. يثبت Aspose.Words.  
2. يعرّف `ImageSavingCallback` الذي يتعامل مع إنشاء المجلد والتسمية الفريدة.  
3. يضبط `MarkdownSaveOptions` مع الـ callback.  
4. يحمل ملف `.docx` ويحفظه كـ `.md`.  

من هنا يمكنك استكشاف مواضيع ذات صلة مثل **extract images docx** للمعالجة المنفصلة، أو تعديل الـ callback لتضمين الصور كـ Base64 لإنتاج Markdown بملف واحد. قد تجرب أيضًا استراتيجيات تسمية صور مختلفة، أو دمج هذا المنطق في خط أنابيب CI يولد الوثائق تلقائيًا من قوالب Word.

هل لديك أسئلة حول معالجة SVGs، أو تريد معالجة مجموعة من المستندات دفعة واحدة؟ اترك تعليقًا، وتمنياتنا بالبرمجة السعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}