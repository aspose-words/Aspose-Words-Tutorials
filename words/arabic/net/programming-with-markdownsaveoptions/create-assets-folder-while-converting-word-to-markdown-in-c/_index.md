---
category: general
date: 2026-01-02
description: إنشاء مجلد الأصول وتحويل ملفات Word إلى Markdown باستخدام Aspose.Words.
  تعلّم كيفية استخراج الصور من ملفات docx وحفظها كملفات markdown باستخدام C#.
draft: false
keywords:
- create assets folder
- convert word to markdown
- extract images from docx
- save docx as markdown
- docx to markdown c#
language: ar
og_description: إنشاء مجلد الأصول وتحويل ملفات Word إلى Markdown باستخدام Aspose.Words.
  يوضح هذا الدرس كيفية استخراج الصور من ملف docx وحفظ ملف docx كـ markdown باستخدام
  C#.
og_title: إنشاء مجلد الأصول أثناء تحويل Word إلى Markdown – دليل C#
tags:
- Aspose.Words
- C#
- Markdown conversion
title: إنشاء مجلد الأصول أثناء تحويل Word إلى Markdown في C#
url: /ar/net/programming-with-markdownsaveoptions/create-assets-folder-while-converting-word-to-markdown-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مجلد الأصول أثناء تحويل Word إلى Markdown في C#

هل احتجت يومًا إلى **إنشاء مجلد الأصول** عندما تقوم بتحويل مستند Word إلى Markdown؟ لست وحدك. يواجه العديد من المطورين مشكلة عندما تضيع الصور والموارد المدمجة الأخرى أثناء التحويل، مما يترك روابط مكسورة في ملف `.md` الناتج.  

الأخبار السارة؟ مع Aspose.Words يمكنك **تحويل Word إلى Markdown** وتفريغ كل صورة تلقائيًا في دليل `assets` مرتب — دون الحاجة إلى نسخ يدوي. في هذا الدرس سنستعرض العملية بالكامل، من تحميل ملف `.docx` إلى استخراج الصور، حفظ الـ markdown، وبالطبع إنشاء مجلد الأصول الذي تبحث عنه.

بنهاية الدرس ستكون قادرًا على **حفظ docx كـ markdown**، وستكون كل صورة مخزنة بشكل منظم، وستفهم كيفية تعديل العملية لحالات خاصة مثل ملفات PDF الكبيرة أو أنظمة تسمية الصور المخصصة. هل أنت مستعد؟ هيا نبدأ.

---

## ما ستحتاجه

- **Aspose.Words for .NET** (v23.12 أو أحدث). المكتبة مجانية للتجربة؛ الترخيص يزيل علامة التقييم.
- **.NET 6+** (أو .NET Framework 4.7.2+ إذا كنت تفضل بيئة التشغيل الكلاسيكية).
- بيئة تطوير C# أساسية (Visual Studio، Rider، أو VS Code مع إضافة C#).
- ملف `input.docx` تجريبي يحتوي على صورة واحدة على الأقل، حتى نتمكن من رؤية خطوة **extract images from docx** عمليًا.

لا توجد حزم NuGet إضافية مطلوبة بخلاف Aspose.Words.

## الخطوة 1: إعداد مشروعك وتثبيت Aspose.Words

أولاً، أنشئ تطبيقًا سطريًا:

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

> نصيحة احترافية: إذا كنت تستخدم Visual Studio، فقط أنشئ مشروعًا جديدًا من نوع “Console App (.NET Core)” وأضف حزمة NuGet عبر واجهة مدير الحزم.

بعد تثبيت الحزمة، افتح `Program.cs`. سنبدأ بإضافة توجيهات `using` اللازمة:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;
```

هذه المساحات الاسم تعطينا الوصول إلى الفئة `Document`، و`MarkdownSaveOptions`، ومساعدي نظام الملفات الذين سنحتاجهم لخطوة **create assets folder**.

## الخطوة 2: تحميل مستند Word المصدر

تحميل ملف `.docx` بسيط كإشارة مُنشئ `Document` إلى مسار الملف. تأكد من أن الملف موجود في مكان يمكن لتطبيقك قراءته — ويفضل أن يكون بجوار الملف التنفيذي لهذا العرض.

```csharp
// Step 2: Load the source Word document
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

if (!File.Exists(inputPath))
{
    Console.WriteLine($"❌ Could not find {inputPath}. Drop a Word file there and try again.");
    return;
}

Document doc = new Document(inputPath);
Console.WriteLine("✅ Loaded input.docx successfully.");
```

لماذا نتحقق من `File.Exists`؟ لأن الملف المفقود هو أكثر العقبات شيوعًا عندما تحاول أول مرة **convert word to markdown**. هذا الشرط الوقائي يعطي خطأً واضحًا بدلاً من استثناء غامض.

## الخطوة 3: تكوين خيارات Markdown واستدعاء حفظ الأصول (Asset‑Saving Callback)

يتيح لنا Aspose.Words ربط عملية الحفظ عبر `IResourceSavingCallback`. هنا سنقوم بـ **create assets folder** وإعطاء كل صورة اسمًا فريدًا.

```csharp
// Step 3: Configure Markdown save options and attach a resource‑saving callback
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Use a callback to control where each resource (image, etc.) ends up
    ResourceSavingCallback = new MyResourceCallback()
};
```

فئة الاستدعاء توجد بعد بضع أسطر. تقوم بثلاثة أشياء:

1. التأكد من وجود دليل `assets`.
2. توليد اسم ملف مبني على GUID لتجنب التصادمات.
3. تحديث `args.ResourceFileName` بحيث يكتب Aspose الملف في الموقع الصحيح.

## الخطوة 4: تنفيذ استدعاء حفظ الموارد (Create Assets Folder)

إليك التنفيذ الكامل. لاحظ التعليقات المكثفة — هذا يجعل الدرس **citation‑worthy** لأن أي شخص يمكنه متابعة المنطق دون تخمين.

```csharp
// Step 4: Callback that stores each resource (e.g., images) in an assets folder
class MyResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // -----------------------------------------------------------------
        // 1️⃣ Decide where the assets folder lives.
        //    You can make this configurable, but for this demo we’ll
        //    place it next to the output markdown file.
        // -----------------------------------------------------------------
        string outputDir = Path.GetDirectoryName(args.DocumentFileName);
        string assetsFolder = Path.Combine(outputDir, "assets");

        // Ensure the folder exists – this is the core of “create assets folder”
        Directory.CreateDirectory(assetsFolder);

        // -----------------------------------------------------------------
        // 2️⃣ Generate a unique file name.
        //    Using a GUID prevents name clashes when the source doc has
        //    multiple images with the same original name.
        // -----------------------------------------------------------------
        string extension = Path.GetExtension(args.ResourceFileName);
        string uniqueName = $"{Guid.NewGuid()}{extension}";

        // -----------------------------------------------------------------
        // 3️⃣ Tell Aspose where to write the file.
        //    The markdown will reference this relative path.
        // -----------------------------------------------------------------
        args.ResourceFileName = Path.Combine(assetsFolder, uniqueName);

        // No need to set args.Cancel = true; the default saving will continue.
    }
}
```

> **لماذا GUID؟** إذا قمت بإعادة استخدام `args.ResourceFileName` فقط، قد يتم استبدال صورتين تحملان الاسم `image1.png` ببعضهما. يضمن GUID التفرد، وهو مفيد بشكل خاص عندما تقوم بـ **extract images from docx** التي تحتوي على العديد من الأسماء المتطابقة.

## الخطوة 5: حفظ المستند كـ Markdown

الآن نحن جاهزون لبدء التحويل. سيقع ملف الإخراج بجوار مجلد `assets`، وسيحتوي الـ markdown على روابط نسبية مثل `![Image](assets/123e4567-e89b-12d3-a456-426614174000.png)`.

```csharp
// Step 5: Save the document as Markdown; the callback will handle embedded resources
string outputPath = Path.Combine(Environment.CurrentDirectory, "output", "report.md");

// Ensure the output directory exists
Directory.CreateDirectory(Path.GetDirectoryName(outputPath));

doc.Save(outputPath, mdOptions);
Console.WriteLine($"✅ Markdown saved to {outputPath}");
Console.WriteLine("📁 Assets folder created at: " + Path.Combine(Path.GetDirectoryName(outputPath), "assets"));
```

تشغيل البرنامج الآن ينتج:

- `output/report.md` – نسخة الـ markdown من ملف Word الخاص بك.
- `output/assets/` – مجلد مليء بكل صورة مستخرجة.

افتح `report.md` في أي عارض markdown (معاينة VS Code، GitHub، إلخ) وسترى الصور تُعرض بشكل صحيح.

## الخطوة 6: التحقق من النتيجة — ما شكل الـ Markdown

فيما يلي مقتطف مما قد يحتويه الـ markdown المُولد بعد التحويل:

```markdown
# Sample Document

Here’s a paragraph with an image:

![Image](assets/4f3c2a1b-9e6d-4b2f-a9d3-0c9e5d6f7a12.png)

Another paragraph follows...
```

إذا فتحت ملف الـ markdown وظهرت الصورة، فقد نجحت في **save docx as markdown** بينما يحتوي مجلد الأصول على كل صورة كنت بحاجة إلى **extract images from docx**.

## أسئلة شائعة وحالات خاصة

### 1️⃣ ماذا لو كان ملف Word يحتوي على رسومات SVG أو EMF؟

يقوم Aspose.Words بتحويل معظم صيغ المتجهات إلى PNG بشكل افتراضي عند الحفظ كـ Markdown. إذا كنت تحتاج الصيغة الأصلية، يمكنك تعديل `mdOptions.ImageSavingOptions` (مثلاً، تعيين `ImageSavingOptions.ImageFormat = ImageSaveOptions.SaveFormat.Svg`). تذكر تحديث الاستدعاء للحفاظ على امتداد الملف الصحيح.

### 2️⃣ كيف يمكنني التحكم في اسم مجلد الأصول؟

ببساطة استبدل `"assets"` في `MyResourceCallback` بأي سلسلة تفضلها، أو اقرأه من ملف إعدادات:

```csharp
string assetsFolder = Path.Combine(outputDir, ConfigurationManager.AppSettings["AssetsFolderName"]);
```

### 3️⃣ مستندي يحتوي على مئات الصور عالية الدقة. هل سيستهلك ذلك الذاكرة؟

يقوم Aspose.Words ببث الموارد إلى القرص واحدة تلو الأخرى، لذا يظل استهلاك الذاكرة منخفضًا. ومع ذلك، سيطابق الحجم الكلي لمجلد الأصول حجم الصور المدمجة. فكر في ضغطها بعد التحويل إذا كان التخزين مصدر قلق.

### 4️⃣ أحتاج أن يشير الـ markdown إلى الصور عبر URL مطلق (مثلاً لمولد موقع ثابت). هل يمكنني فعل ذلك؟

نعم. داخل الاستدعاء يمكنك إضافة عنوان URL أساسي:

```csharp
string baseUrl = "https://cdn.example.com/docs/assets/";
args.ResourceFileName = baseUrl + uniqueName;
```

فقط تأكد من رفع الملفات إلى نفس الموقع الذي يشير إليه الـ URL.

### 5️⃣ هل يعمل هذا مع ملفات `.doc` (Word ثنائي)؟

بالطبع. يقوم مُنشئ `Document` بالكشف التلقائي عن الصيغة، لذا يمكنك تمرير ملف `.doc` وسيقوم نفس الخط الأنابيب بتحويله إلى Markdown، واستخراج الصور بنفس الطريقة.

## نصائح احترافية لتحويلات جاهزة للإنتاج

- **Batch Processing:** غلف منطق التحويل داخل حلقة `foreach` التي تت iterates over مجلد من ملفات `.docx`. احتفظ بمثيل واحد من `MyResourceCallback` وأعد استخدامه للسرعة.
- **Logging:** استخدم إطار تسجيل (Serilog، NLog) بدلاً من `Console.WriteLine` للتطبيقات الواقعية. سجّل أسماء الصور الأصلية لتتبعها.
- **Error Handling:** احط استدعاء `doc.Save` بكتلة try‑catch التي تلتقط استثناءات `Aspose.Words`. غالبًا ما تظهر عندما تكون ميزة غير مدعومة (مثل كائنات OLE) موجودة.
- **Unit Tests:** اكتب اختبارًا يزود ملف `.docx` معروف يحتوي على صورتين ويتأكد من أن مجلد `assets` يحتوي بالضبط على ملفين بعد التحويل. هذا يحمي من الانحدار عند ترقية Aspose.

## مثال كامل جاهز للتنفيذ (انسخه‑الصقه)

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document
            string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
            if (!File.Exists(inputPath))
            {
                Console.WriteLine($"❌ {inputPath} not found.");
                return;
            }

            Document doc = new Document(inputPath);
            Console.WriteLine("✅ Loaded input.docx");

            // 2️⃣ Configure save options with our callback
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyResourceCallback()
            };

            // 3️⃣ Prepare output location
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output", "report.md");
            Directory.CreateDirectory(Path.GetDirectoryName(outputPath));

            // 4️⃣ Save as Markdown (assets folder will be created automatically)
            doc.Save(outputPath, mdOptions);
            Console.WriteLine($"✅ Markdown saved to {outputPath}");
            Console.WriteLine("📁 Assets folder: " + Path.Combine(Path.GetDirectoryName(outputPath), "assets"));
        }
    }

    // 5️⃣ Callback that creates the assets folder and gives each image a unique name

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}