---
category: general
date: 2026-03-08
description: دليل مجلد الصور المخصص لتحويل Word إلى Markdown، استخراج صور DOCX وتغيير
  تنسيق الصورة باستخدام Aspose.Words – خطوة بخطوة.
draft: false
keywords:
- custom image folder
- convert word to markdown
- change image format
- extract images docx
- convert docx to md
language: ar
og_description: دليل مجلد الصور المخصص يوضح كيفية تحويل Word إلى Markdown، استخراج
  الصور من ملف DOCX وتغيير تنسيق الصورة باستخدام Aspose.Words في C#.
og_title: مجلد صور مخصص – تحويل Word إلى Markdown باستخدام Aspose.Words
tags:
- Aspose.Words
- C#
- Markdown
title: مجلد صور مخصص – تحويل Word إلى Markdown باستخدام Aspose.Words
url: /ar/net/programming-with-markdownsaveoptions/custom-image-folder-convert-word-to-markdown-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# مجلد صور مخصص – تحويل Word إلى Markdown باستخدام Aspose.Words

هل تساءلت يومًا كيف **custom image folder** عملية تحويل Word‑to‑Markdown بحيث تنتهي الصور تمامًا في المكان الذي تريدها؟ لست وحدك. يواجه العديد من المطورين مشكلة عندما يقوم السلوك الافتراضي لـ Aspose.Words بنشر الصور في نفس المجلد مع ملف Markdown، مما يجعل تنظيف المشروع كابوسًا.  

في هذا الدرس سنستعرض حلًا كاملًا وجاهزًا للتنفيذ يـ **convert word to markdown**، **extract images docx**، وحتى **change image format** أثناء التشغيل. في النهاية ستحصل على مجلد فرعي `Resources/` نظيف، صور مُعاد تسميتها بشكل جميل، وملف markdown يشير إليها بشكل صحيح. لا سكريبتات خارجية، ولا نسخ‑لصق يدوي — فقط C# صافي و Aspose.Words.

## ما ستحتاجه

- **Aspose.Words for .NET** (أحدث نسخة حتى 2026، مثلاً 24.9).  
- بيئة تطوير .NET (Visual Studio، Rider، أو `dotnet` CLI).  
- ملف `input.docx` تجريبي يحتوي على صورة واحدة على الأقل.  
- إلمام أساسي بصياغة C# (لا شيء غريب).

إذا كان لديك هذه بالفعل، رائع—لننقض مباشرة إلى الكود. إذا لا، احصل على حزمة NuGet المجانية باستخدام `dotnet add package Aspose.Words` وأنشئ مشروع وحدة تحكم جديد.

## الخطوة 1 – تحميل مستند Word المصدر

أول شيء نقوم به هو فتح ملف `.docx` الذي نعتزم تحويله. فئة `Document` في Aspose.Words تتعامل مع كل شيء من النص إلى الموارد المضمنة.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **لماذا هذا مهم:** تحميل المستند مبكرًا يمنحنا الوصول إلى شجرة العقد الداخلية، مما يسمح لاحقًا لاستدعاء **extract images docx** برؤية كل صورة كموارد.

## الخطوة 2 – إعداد خيارات حفظ Markdown مع رد نداء حفظ الموارد

يتيح لك Aspose.Words توصيل رد نداء يُستدعى لكل مورد خارجي (صور، SVGs، إلخ). سنستخدم ذلك لتوجيه كل صورة إلى **custom image folder** وإعادة تسميتها.

```csharp
// Configure Markdown save options
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Attach our custom callback
    ResourceSavingCallback = new ImageSavingCallback()
};
```

### لماذا استخدام رد نداء؟

- **Control over location:** بشكل افتراضي، يكتب Aspose الصور بجوار ملف `.md`.  
- **Naming consistency:** يمكنك إضافة بادئة، أو طوابع زمنية، أو حتى تجزئة المحتوى.  
- **Format conversion:** يسمح لك رد النداء بالتحويل من PNG إلى JPEG أثناء التشغيل، مما يلبي متطلب **change image format**.

## الخطوة 3 – حفظ المستند كـ Markdown

الآن نخبر Aspose بإنشاء ملف markdown. رد النداء المحدد سابقًا يعمل تلقائيًا لكل صورة يصادفها.

```csharp
// Save the document as Markdown; images are handled by the callback
doc.Save("YOUR_DIRECTORY/output.md", mdOptions);
```

في هذه المرحلة يجب أن ترى `output.md` ومجلدًا جديدًا يُدعى `Resources` (أو أي اسم اخترته) يحتوي على ملفات صور مُعاد تسميتها.

## الخطوة 4 – تنفيذ رد نداء حفظ الصورة

فيما يلي التنفيذ الكامل لـ `ImageSavingCallback`. يقوم بإنشاء مجلد الوجهة، وإعادة تسمية كل صورة، واختيارياً تغيير تنسيقها.

```csharp
/// <summary>
/// Handles saving of external resources (images) during Markdown export.
/// </summary>
public class ImageSavingCallback : IResourceSavingCallback
{
    /// <summary>
    /// Invoked for each resource (image, SVG, etc.) Aspose.Words wants to write.
    /// </summary>
    /// <param name="args">Information about the resource being saved.</param>
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Define the custom folder – this is our "custom image folder"
        string folder = "YOUR_DIRECTORY/Resources/";
        Directory.CreateDirectory(folder); // ensures the folder exists

        // 2️⃣ Build a clean, predictable file name
        //   Example: img_12345.png → img_input_12345.png
        string safeBaseName = Path.GetFileNameWithoutExtension(args.ResourceFileName);
        string newName = $"img_{safeBaseName}{Path.GetExtension(args.ResourceFileName)}";

        // 3️⃣ Update the path that Markdown will reference
        args.ResourceFileName = Path.Combine(folder, newName);

        // 4️⃣ OPTIONAL: Change the image format (covers "change image format")
        // Uncomment the line below to force JPEG output for all images.
        // args.ResourceFileFormat = SaveFormat.Jpeg;

        // 5️⃣ Log for debugging – helpful when troubleshooting edge cases
        Console.WriteLine($"Saving image as: {args.ResourceFileName}");
    }
}
```

#### نصائح احترافية وحالات حافة

- **Missing folder:** `Directory.CreateDirectory` عملية لا تتسبب في خطأ إذا كان المجلد موجودًا بالفعل.  
- **Name collisions:** إذا شاركت صورتان نفس الاسم الأصلي، تضيف حيلة `safeBaseName` بادئة فريدة (`img_`). لمزيد من الأمان، أضف GUID: `Guid.NewGuid().ToString("N")`.  
- **Changing format:** عندما تُزيل التعليق عن `args.ResourceFileFormat = SaveFormat.Jpeg;`، يقوم Aspose تلقائيًا بتحويل بيانات الصورة، مما يحقق متطلب **change image format**.  
- **Performance:** بالنسبة للمستندات الكبيرة جدًا، فكر في بث الإخراج بدلاً من تحميل كل شيء في الذاكرة — يوفر Aspose `LoadOptions` لهذا الغرض.

## الخطوة 5 – التحقق من النتيجة

بعد انتهاء البرنامج، افتح `output.md`. يجب أن ترى روابط صور Markdown التي تشير إلى الموقع الجديد، على سبيل المثال:

```markdown
![Sample Image](Resources/img_SampleImage.png)
```

إذا فعلت تحويل JPEG، سينتهي الرابط بـ `.jpeg`. افتح مجلد `Resources` وتأكد من وجود الصور، وإعادة تسميتها بشكل صحيح، وإمكانية عرضها.

## الأسئلة المتكررة (FAQs)

### هل يمكنني استخدام هذا النهج لـ **convert docx to md** بدون Aspose؟

نعم، لكنك ستفقد معالجة الموارد المدمجة. مكتبات مثل **DocX** أو **Open XML SDK** يمكنها استخراج الصور، لكن سيتعين عليك كتابة مولد markdown الخاص بك — عمل أكثر كثيرًا وعرضة للأخطاء.

### ماذا لو كان ملف Word يحتوي على رسومات SVG؟

يعمل رد النداء مع أي مورد خارجي، بما في ذلك SVG. خاصية `ResourceSavingArgs.ResourceFileFormat` ستُظهر الصيغة الأصلية، بحيث يمكنك اتخاذ قرار بالحفاظ على SVG أو تحويله إلى صورة نقطية.

### هل يعمل هذا على .NET 6/7/8؟

بالتأكيد. يستهدف Aspose.Words .NET Standard 2.0+، لذا أي بيئة تشغيل .NET حديثة متوافقة.

### كيف أتعامل مع صور *كبيرة جدًا* تحتاج إلى تغيير الحجم؟

يمكنك إدخال معالجة الصور داخل رد النداء باستخدام `System.Drawing` أو `ImageSharp`. بعد حفظ الصورة إلى تدفق مؤقت، قم بتغيير حجمها، ثم اكتب البيانات المعدلة مرة أخرى إلى `args.Stream`.

## مثال كامل يعمل

إليك البرنامج الكامل في ملف واحد. انسخه‑الصقه، عدل المسارات، وشغّله.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 1: Load the source Word document
            // -----------------------------------------------------------------
            string inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // -----------------------------------------------------------------
            // Step 2: Configure Markdown save options with a custom callback
            // -----------------------------------------------------------------
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // -----------------------------------------------------------------
            // Step 3: Save as Markdown – images are routed to the custom folder
            // -----------------------------------------------------------------
            string outputPath = "YOUR_DIRECTORY/output.md";
            doc.Save(outputPath, mdOptions);

            Console.WriteLine("Conversion complete!");
            Console.WriteLine($"Markdown file: {outputPath}");
        }
    }

    // -----------------------------------------------------------------
    // Step 4 – Callback that stores each image in a custom folder
    // -----------------------------------------------------------------
    public class ImageSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            // Define the folder where images will be placed (our custom image folder)
            string folder = "YOUR_DIRECTORY/Resources/";
            Directory.CreateDirectory(folder);

            // Build a new, predictable name for the image
            string safeBase = Path.GetFileNameWithoutExtension(args.ResourceFileName);
            string newName = $"img_{safeBase}{Path.GetExtension(args.ResourceFileName)}";

            // Update the path used in the generated Markdown
            args.ResourceFileName = Path.Combine(folder, newName);

            // OPTIONAL: Force JPEG output – uncomment to enable
            // args.ResourceFileFormat = SaveFormat.Jpeg;

            // Debug output
            Console.WriteLine($"Saving image as: {args.ResourceFileName}");
        }
    }
}
```

### النتيجة المتوقعة

تشغيل البرنامج يطبع شيئًا مثل:

```
Saving image as: YOUR_DIRECTORY/Resources/img_SampleImage.png
Conversion complete!
Markdown file: YOUR_DIRECTORY/output.md
```

افتح `output.md` وسترى:

```markdown
# Sample Document

Here is an image:

![Sample Image](Resources/img_SampleImage.png)
```

ملف الصورة يعيش بشكل منظم داخل `Resources/`، مما يحقق متطلب **custom image folder**.

## الخلاصة

لقد بنينا للتو خط أنابيب قوي يـ **convert word to markdown**، **extract images docx**، و **change image format** مع الحفاظ على كل صورة داخل **custom image folder** يمكنك التحكم فيه. الحل هو:

1. تحميل ملف `.docx` باستخدام Aspose.Words.  
2. إرفاق `ResourceSavingCallback` الذي ينشئ مجلدًا، يُعيد تسمية الملفات، ويحوّل الصيغ اختياريًا.  
3. حفظ كـ Markdown — يقوم رد النداء بالمعالجة الثقيلة تلقائيًا.

لا تتردد في التجربة: استبدل `SaveFormat.Jpeg` بـ `SaveFormat.Png`، أضف طابعًا زمنيًا إلى اسم الملف، أو دمج مكتبات ضغط الصور للحصول على أصول أصغر. النمط يتوسع لمعالجة دفعات، خطوط CI، أو حتى خدمات ويب تقبل ملفات Word مرفوعة وتعيد Markdown جاهز للنشر.

---

*هل أنت مستعد للتحدي التالي؟* جرّب ربط هذا التحويل مع مولد موقع ثابت مثل Hugo أو MkDocs لأتمتة سير عمل الوثائق. أو استكشف مُصدِّري **HTML** و **PDF** في Aspose.Words للنشر متعدد الصيغ. برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}