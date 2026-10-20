---
category: general
date: 2026-05-04
description: تعلم كيفية حفظ الصور أثناء تحويل ملف DOCX إلى Markdown باستخدام Aspose.Words.
  يوضح هذا الدليل أيضًا كيفية استخراج الصور من Word وحفظ Word كـ Markdown.
draft: false
keywords:
- how to save images
- convert docx to markdown
- extract images from word
- how to convert docx
- save word as markdown
language: ar
og_description: كيفية حفظ الصور أثناء تحويل ملف DOCX إلى Markdown باستخدام Aspose.Words.
  دليل خطوة بخطوة مع كود C# كامل.
og_title: كيفية حفظ الصور – تحويل DOCX إلى ماركداون باستخدام Aspose.Words
tags:
- Aspose.Words
- C#
- Markdown conversion
title: كيفية حفظ الصور – تحويل DOCX إلى Markdown باستخدام Aspose.Words
url: /ar/net/programming-with-markdownsaveoptions/how-to-save-images-convert-docx-to-markdown-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية حفظ الصور – تحويل DOCX إلى Markdown باستخدام Aspose.Words

هل تساءلت يومًا **عن كيفية حفظ الصور** عندما تحتاج إلى تحويل ملف Word إلى Markdown؟ لست وحدك. يواجه العديد من المطورين مشكلة عندما تُسقط عملية التحويل الصور في فوضى من الروابط المكسورة، أو الأسوأ — تفقدها تمامًا. الخبر السار هو أن Aspose.Words يمنحك تحكمًا دقيقًا، بحيث يمكنك استخراج الصور من Word، وتحديد مكان حفظها، والحصول على مخرجات Markdown نظيفة.

في هذا الدرس سنستعرض مثالًا كاملاً وجاهزًا للتنفيذ بلغة C# يُظهر **كيفية حفظ الصور** في مجلد مخصص أثناء تحويل ملف `.docx` إلى `.md`. سنتطرق أيضًا إلى **convert docx to markdown**، **extract images from word**، والسؤال الأوسع **how to convert docx** بطريقة تسمح لك **save word as markdown** دون فقدان أي من الأصول.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (تعمل الواجهة البرمجية بنفس الطريقة على .NET Framework 4.7+)
- رخصة Aspose.Words سارية أو نسخة تجريبية مجانية (الإصدار المجاني يضيف علامة مائية إلى المخرجات، لكن الكود يعمل بنفس الطريقة)
- مستند Word يحتوي بالفعل على صور (مثل `DocWithImages.docx`)
- Visual Studio 2022 أو أي محرر يمكنه بناء مشاريع C#

> **نصيحة احترافية:** إذا كنت تستخدم النسخة التجريبية، لا يزال بإمكانك اختبار منطق حفظ الصور؛ فقط تذكر أن ملف PDF/MD النهائي سيحتوي على العلامة المائية التجريبية.

## نظرة عامة على الحل

على مستوى عالٍ، تبدو العملية هكذا:

1. تحميل ملف `.docx` المصدر باستخدام `Document`.
2. إنشاء كائن `MarkdownSaveOptions` وربطه بـ `IResourceSavingCallback`.
3. في الـ callback، تحديد المجلد واسم الملف لكل صورة.
4. حفظ المستند كـ Markdown؛ يقوم الـ callback بكتابة كل صورة إلى القرص.

هذا هو جوهر **كيفية حفظ الصور** أثناء التحويل. نفس النمط يعمل مع أنواع الموارد الأخرى (الخطوط، CSS، إلخ) إذا احتجت إليها.

## الخطوة 1 – تحميل ملف DOCX الذي يحتوي على صور

أولًا نحتاج إلى كائن `Document` يشير إلى ملف Word الذي تريد تحويله. لا شيء معقد هنا؛ مجرد استدعاء مباشر للمنشئ.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Adjust the path to where your .docx lives
string sourcePath = @"C:\Docs\DocWithImages.docx";

Document sourceDoc = new Document(sourcePath);
```

> **لماذا هذا مهم:** تحميل المستند هو المكان الوحيد الذي يقوم فيه Aspose بتحليل XML الخاص بـ Word، لذا أي خطوط مفقودة أو أجزاء تالفة ستؤدي إلى استثناء الآن—قبل أن نبدأ حتى في حفظ الصور.

## الخطوة 2 – إعداد MarkdownSaveOptions مع Callback لحفظ الصور

تتيح لك فئة `MarkdownSaveOptions` ربط عملية الحفظ عبر `ResourceSavingCallback`. يتلقى هذا الـ callback كائن `ResourceSavingArgs` لكل مورد خارجي (صور، CSS، إلخ) يحتاج Aspose إلى كتابته.

```csharp
// Define where the Markdown file will be written
string markdownPath = @"C:\Docs\Doc.md";

// Create the options object and attach the callback
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This is the heart of how to save images
    ResourceSavingCallback = new ImageSavingCallback()
};
```

### تنفيذ الـ Callback

فيما يلي التنفيذ الكامل لـ `ImageSavingCallback`. يقوم بإنشاء مجلد فرعي `Images` بجوار ملف Markdown، ويعطي كل صورة اسمًا تسلسليًا (`img_0.png`, `img_1.jpg`, …)، ويمكنك أيضًا توجيه تدفق الصورة إلى مكان آخر (مثل دلو سحابي).

```csharp
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only handle images; other resources (like CSS) are ignored here
        if (args.ResourceType != ResourceType.Image)
            return;

        // Build a folder called "Images" right next to the markdown file
        string markdownDir = Path.GetDirectoryName(args.DestinationFileName);
        string imagesFolder = Path.Combine(markdownDir, "Images");
        Directory.CreateDirectory(imagesFolder);

        // Compose a safe file name: img_<index>.<original extension>
        string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
        args.FileName = Path.Combine(imagesFolder, newFileName);

        // If you wanted to push the image to a remote store, you could replace args.Stream here.
        // For now we just let Aspose write to the local file system.
    }
}
```

> **كيف يساعدك هذا:** من خلال تخصيص `args.FileName` تتحكم تمامًا في **كيفية حفظ الصور**—سواء في مجلد مسطح، أو هيكل هرمي مبني على التاريخ، أو حتى قاعدة بيانات BLOB. الـ callback يُنفّذ لكل صورة، لذا لن تحتاج إلى معالجة لاحقة لملف Markdown.

## الخطوة 3 – حفظ المستند كـ Markdown

الآن بعد أن أصبحت الخيارات والـ callback جاهزين، التحويل الفعلي هو سطر واحد فقط.

```csharp
// Save the document; the callback will fire for each image automatically
sourceDoc.Save(markdownPath, markdownOptions);
```

عند انتهاء السطر، ستحصل على:

- `Doc.md` – تمثيل Markdown لمحتوى Word الخاص بك.
- `Images\img_0.png`, `Images\img_1.jpg`, … – كل صورة مستخرجة من ملف DOCX الأصلي.

## مثال كامل وجاهز للتنفيذ

نجمع كل شيء معًا في تطبيق console مستقل يمكنك نسخه ولصقه في مشروع C# جديد.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // 1️⃣ Load the source DOCX that contains images
            // -----------------------------------------------------------------
            string sourcePath = @"C:\Docs\DocWithImages.docx";
            Document sourceDoc = new Document(sourcePath);

            // -----------------------------------------------------------------
            // 2️⃣ Prepare Markdown options with a custom image‑saving callback
            // -----------------------------------------------------------------
            string markdownPath = @"C:\Docs\Doc.md";
            MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // -----------------------------------------------------------------
            // 3️⃣ Perform the conversion – this is where we actually learn
            //     how to save images while converting docx to markdown
            // -----------------------------------------------------------------
            sourceDoc.Save(markdownPath, markdownOptions);

            Console.WriteLine("Conversion complete!");
            Console.WriteLine($"Markdown file: {markdownPath}");
            Console.WriteLine("Images folder: " + Path.Combine(Path.GetDirectoryName(markdownPath), "Images"));
        }
    }

    // -----------------------------------------------------------------
    // 4️⃣ Callback that decides where each image ends up
    // -----------------------------------------------------------------
    class ImageSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType != ResourceType.Image)
                return;

            string markdownDir = Path.GetDirectoryName(args.DestinationFileName);
            string imagesFolder = Path.Combine(markdownDir, "Images");
            Directory.CreateDirectory(imagesFolder);

            string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
            args.FileName = Path.Combine(imagesFolder, newFileName);

            // Optional: redirect the image stream elsewhere (e.g., cloud storage)
            // args.Stream = new MemoryStream(); // your custom stream here
        }
    }
}
```

### النتيجة المتوقعة

بعد تشغيل البرنامج:

- افتح `C:\Docs\Doc.md` في أي محرر نصوص. ستظهر روابط صور Markdown مثل `![](Images/img_0.png)`.
- سيحتوي مجلد `Images` على كل صورة مستخرجة، مسماة تسلسليًا.
- سيُعرض ملف Markdown بشكل صحيح في أي عارض يدعم الصور المحلية (معاينة VS Code، GitHub، إلخ).

## الأسئلة المتكررة (FAQs)

### هل يعمل هذا مع صيغ صور أخرى (SVG, TIFF)؟

نعم. `Path.GetExtension(args.FileName)` يحافظ على الامتداد الأصلي، لذا تُحفظ SVG، TIFF، BMP، وحتى EMF دون تغيير. الملاحظة الوحيدة هي أن بعض عارضات Markdown قد لا تعرض SVG داخل النص؛ في هذه الحالة يمكنك تحويل SVG إلى PNG مسبقًا.

### ماذا لو أردت تضمين الصور كـ Base64 بدلاً من ملفات منفصلة؟

داخل `ResourceSaving` يمكنك استبدال كتابة الملف الفعلية بـ `MemoryStream` ثم تعديل رابط Markdown يدويًا. لا يوفر Aspose مفتاحًا مباشرًا لـ “embed as Base64”، لكن الـ callback يمنحك التحكم الكامل في `args.Stream`.

### كيف يختلف هذا عن طريقة `ExportImages` المدمجة؟

`ExportImages` تستخرج جميع الصور إلى مجلد **بدون** توليد Markdown. ربطنا بين العمليتين عبر الـ callback يضمن أن أسماء ملفات الصور تتطابق مع الإشارات داخل ملف `.md`. هذا التوافق هو المفتاح لـ **كيفية حفظ الصور** بشكل صحيح أثناء التحويل.

### هل يمكنني تحويل عدة ملفات DOCX دفعة واحدة؟

بالتأكيد. غلف المنطق الأساسي داخل حلقة `foreach (var file in Directory.GetFiles(..., "*.docx"))`، عدّل مسارات الإخراج، وأعد استخدام نفس `ImageSavingCallback`. فقط تذكّر إنشاء كائن `MarkdownSaveOptions` جديد لكل مستند، لأن `args.DestinationFileName` يتغيّر في كل تكرار.

## الحالات الخاصة وأفضل الممارسات

| الحالة | ما يجب الانتباه إليه | الإصلاح الموصى به |
|-----------|----------------------|-----------------|
| **DOCX كبير (مئات الـ MB)** | ضغط على الذاكرة أثناء التحميل | استخدم `LoadOptions` مع `LoadFormat.Docx` واضبط `LoadOptions.LoadFormat = LoadFormat.Docx` للتحميل التدفقي للأجزاء |
| **تعارض أسماء الصور** | إذا كان المصدر يحتوي بالفعل على `img_0.png` في المجلد الهدف، قد يتم الكتابة فوقه | أضف GUID: `newFileName = $"img_{args.Index}_{Guid.NewGuid():N}{Path.GetExtension(args.FileName)}"` |
| **مجلد الإخراج للقراءة فقط** | عملية الحفظ تُطلق `UnauthorizedAccessException` | تأكد من تشغيل العملية بأذونات مناسبة أو اختر مسارًا قابلًا للكتابة |
| **موارد غير صور (CSS, خطوط)** | الـ callback يستقبلها أيضًا | احمِ الكود بـ `if (args.ResourceType != ResourceType.Image) return;` (مُظهر مسبقًا) |
| **أسماء ملفات Unicode** | بعض أنظمة الملفات قد تُسيء معالجة الأحرف | استخدم `Path.GetInvalidFileNameChars()` لتنقية `args.FileName` قبل تعيينه |

## مواضيع ذات صلة قد ترغب في استكشافها لاحقًا

- **convert docx to markdown** مع أنماط عناوين مخصصة (استخدم `MarkdownSaveOptions.ExportImagesAsBase64` للصور المضمنة)
- **extract images from word** باستخدام `Document.GetChildNodes(NodeType.Shape, true)` وغيرها من الأساليب المتقدمة
- **how to convert docx** إلى صيغ أخرى مثل HTML أو PDF مع الحفاظ على الموارد المضمنة
- **save word as markdown** مع تحسينات للروابط الداخلية وتنسيق القوائم

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}