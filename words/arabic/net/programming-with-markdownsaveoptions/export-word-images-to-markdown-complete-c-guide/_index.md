---
category: general
date: 2025-12-31
description: تصدير صور Word إلى Markdown بسرعة. تعلم كيفية تحويل Word إلى Markdown،
  استخراج الصور من ملفات docx، وتعيين DPI للصور في دليل واحد.
draft: false
keywords:
- export word images
- convert word to markdown
- extract images from docx
- how to convert docx to markdown
- how to set image dpi
language: ar
og_description: تصدير صور Word إلى Markdown باستخدام Aspose.Words. يوضح هذا الدليل
  كيفية تحويل docx إلى markdown، واستخراج الصور، وتعيين DPI للصور.
og_title: تصدير صور Word إلى Markdown – دليل C# خطوة بخطوة
tags:
- Aspose.Words
- C#
- Markdown
- Document Conversion
title: تصدير صور Word إلى Markdown – دليل C# الكامل
url: /ar/net/programming-with-markdownsaveoptions/export-word-images-to-markdown-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تصدير صور Word إلى Markdown – دليل C# الكامل

هل احتجت يومًا إلى **export word images** إلى Markdown لكنك لم تكن متأكدًا من أين تبدأ؟ لست وحدك—فالعديد من المطورين يواجهون هذه العقبة عندما يحاولون نقل الوثائق من سير عمل Word المؤسسي إلى مولد مواقع ثابتة. في هذا الدرس سنستعرض حلاً واحدًا مكتملًا **converts a DOCX file to Markdown**، يستخرج كل صورة مدمجة بدقة 300 DPI، وحتى يحول معادلات Office Math إلى LaTeX.

لماذا هذا مهم؟ الصور عالية الدقة تحافظ على وضوح المخططات على الويب، بينما تُظهر معادلات LaTeX بشكل جميل في معظم عارضات Markdown. في النهاية ستحصل على ملف `.md` جاهز للنشر ومجلد يحتوي على صور PNG بحجم مثالي، جميعها مُولدة من كود C#.

## ما ستتعلمه

* كيفية **convert word to markdown** باستخدام Aspose.Words.
* الخطوات الدقيقة لـ **extract images from docx** مع التحكم في DPI.
* طرق للإجابة على “**how to set image dpi**” في الكود.
* نصائح للتعامل مع المستندات الكبيرة، الصور المفقودة، ومجلدات الإخراج المخصصة.
* مثال كامل قابل للتنفيذ يمكنك وضعه في أي مشروع .NET.

### المتطلبات المسبقة

* .NET 6.0 أو أحدث (الكود يعمل أيضًا على .NET Framework 4.7+).
* رخصة Aspose.Words for .NET سارية (يمكنك البدء بالتقييم المجاني).
* إلمام أساسي بـ C# وسطر الأوامر.
* ملف DOCX يحتوي على صورة واحدة على الأقل أو معادلة—ملف العينة `input.docx` يكفي.

> **نصيحة احترافية:** إذا كنت تستخدم خط أنابيب CI/CD، احتفظ بملف الترخيص خارج التحكم في المصدر وحمّله من متغيّر بيئي.

---

## الخطوة 1 – تثبيت Aspose.Words وإعداد المشروع

أولًا، تحتاج إلى المكتبة التي تقوم بالعمل الشاق.

```bash
dotnet new console -n WordToMarkdown
cd WordToMarkdown
dotnet add package Aspose.Words
```

هذا ينشئ تطبيق console بسيط باسم **WordToMarkdown** ويجلب أحدث حزمة Aspose.Words من NuGet.  

> **لماذا Aspose.Words؟** يدعم استخراج الصور بدون فقدان، وتغيير DPI، وتصدير LaTeX الأصلي لـ Office Math—وهي ميزات تفتقر إليها معظم المكتبات المجانية.

---

## الخطوة 2 – تحميل المستند المصدر

الآن نقوم بقراءة ملف `.docx` الذي يحتوي على الصور التي تريد تصديرها.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Replace with the actual path on your machine
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document – this also parses all embedded resources
Document sourceDocument = new Document(inputPath);
```

إذا لم يُعثر على الملف، تقوم Aspose بإلقاء استثناء `FileNotFoundException`. التقاطه مبكرًا يوفر رسالة خطأ أوضح للمستخدم النهائي.

```csharp
if (!File.Exists(inputPath))
{
    Console.Error.WriteLine($"❌ Cannot locate '{inputPath}'. Ensure the file exists.");
    return;
}
```

---

## الخطوة 3 – تكوين خيارات حفظ Markdown (بما في ذلك DPI)

هنا نجيب على **how to set image dpi**. بشكل افتراضي تقوم Aspose بتصدير الصور بدقة 96 DPI، مما يجعلها ضبابية على شاشات Retina. ضبط `ImageResolution` إلى **300** يمنحك صورًا بجودة الطباعة.

```csharp
// Configure the export settings
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // Export each image at 300 DPI – ideal for most web and print scenarios
    ImageResolution = 300,

    // Turn Office Math equations into LaTeX so they render nicely in Markdown
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: store images in a sub‑folder called "images"
    ImagesFolder = "images"
};
```

> **لماذا LaTeX؟** معظم عارضات Markdown (GitHub، GitLab، MkDocs) تفهم صيغة `$…$`، مما يمنحك معادلات واضحة وقابلة للتكبير دون إضافات إضافية.

---

## الخطوة 4 – حفظ المستند كـ Markdown

مع إعداد الخيارات، يمكننا أخيرًا **export word images** وبقية المحتوى.

```csharp
// Destination markdown file
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.md");

// Perform the conversion
sourceDocument.Save(outputPath, markdownOptions);

Console.WriteLine($"✅ Conversion complete! Markdown saved to '{outputPath}'.");
Console.WriteLine($"🖼️ Extracted images are in the '{markdownOptions.ImagesFolder}' folder.");
```

تشغيل البرنامج ينتج عنصرين:

1. `output.md` – تمثيل Markdown الكامل لملف Word الأصلي.
2. `images/` – مجلد يحتوي على كل صورة من DOCX، الآن بصيغة PNG بدقة 300 DPI (أو الصيغة الأصلية إذا كانت بالفعل عالية الدقة).

---

## الخطوة 5 – التحقق من النتيجة (اختياري لكن موصى به)

فحص سريع يضمن لك تجنب المفاجآت غير السارة لاحقًا.

```csharp
// Verify that at least one image was extracted
int imageCount = Directory.GetFiles(markdownOptions.ImagesFolder).Length;
if (imageCount == 0)
{
    Console.WriteLine("⚠️ No images were found. Did the source DOCX contain pictures?");
}
else
{
    Console.WriteLine($"🔎 Found {imageCount} image(s) at 300 DPI.");
}
```

افتح `output.md` في محرّكك المفضّل. يجب أن ترى وسوم صور Markdown مثل:

```markdown
![Figure 1](images/Image_0.png)
```

إذا أدرجت معادلات، ستظهر ككتل LaTeX:

```markdown
$$
\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
$$
```

---

## حالات الحافة والأسئلة الشائعة

### ماذا لو كان الـ DOCX يحتوي على صور كبيرة جدًا؟

يقوم Aspose تلقائيًا بتقليل حجم الصور التي تتجاوز DPI المطلوب، ولكن يمكنك التحكم في الحد الأقصى للعرض/الارتفاع باستخدام خاصية `ImageSize` في `MarkdownSaveOptions`. مثال:

```csharp
markdownOptions.ImageSize = new Size(1200, 0); // 1200px wide, preserve aspect ratio
```

### كيف أتعامل مع DOCX لا يحتوي على صور؟

ما زالت عملية التحويل تعمل؛ ستحصل ببساطة على ملف Markdown بدون أي وسوم `![...]`. خطوة التحقق أعلاه ستحذّرك، وهو مفيد لخطوط CI.

### هل يمكنني تغيير صيغة الصورة؟

نعم. اضبط `markdownOptions.ImageExportFormat` إلى `ImageExportFormat.Jpeg` أو `Png` أو `Bmp`. PNG هو الافتراضي لأنه يحافظ على الجودة بدون فقد.

### هل الترخيص مطلوب لتغيير DPI؟

رخصة التقييم المجانية تشمل تغيير DPI، لكنها تضيف علامة مائية صغيرة على الصفحة الأولى. للاستخدام الإنتاجي، اشترِ رخصة لإزالة العلامة المائية وإطلاق الأداء الكامل.

### كيف أشغل هذا على Linux/macOS؟

نفس تطبيق .NET console يعمل عبر الأنظمة. فقط قم بتثبيت .NET SDK لنظامك وشغّل `dotnet run`. تأكد من توفر تبعيات Aspose.Words الأصلية؛ حزمة NuGet تضم كل ما تحتاجه.

---

## مثال كامل يعمل (جاهز للنسخ واللصق)

فيما يلي ملف `Program.cs` الكامل الذي يمكنك وضعه في مشروع console جديد. لا يوجد أي جزء مفقود.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣  Load the source DOCX
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        if (!File.Exists(inputPath))
        {
            Console.Error.WriteLine($"❌ Cannot locate '{inputPath}'.");
            return;
        }

        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // 2️⃣  Configure Markdown export options
        // -------------------------------------------------
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
        {
            ImageResolution = 300,                     // How to set image DPI
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            ImagesFolder = "images",                   // Extracted images go here
            ImageExportFormat = ImageExportFormat.Png   // Keep lossless quality
        };

        // -------------------------------------------------
        // 3️⃣  Save as Markdown
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.md");
        sourceDocument.Save(outputPath, markdownOptions);
        Console.WriteLine($"✅ Markdown saved to '{outputPath}'.");
        Console.WriteLine($"🖼️ Images saved to folder '{markdownOptions.ImagesFolder}'.");

        // -------------------------------------------------
        // 4️⃣  Quick verification (optional)
        // -------------------------------------------------
        if (Directory.Exists(markdownOptions.ImagesFolder))
        {
            int imageCount = Directory.GetFiles(markdownOptions.ImagesFolder).Length;
            Console.WriteLine(imageCount > 0
                ? $"🔎 Found {imageCount} image(s) at 300 DPI."
                : "⚠️ No images were extracted.");
        }
    }
}
```

احفظه كـ `Program.cs`، شغّل `dotnet run`، وشاهد السحر يحدث.

---

## الخاتمة

لقد أظهرنا لك الآن كيفية **export word images** إلى Markdown، **convert word to markdown**، و **extract images from docx** مع التحكم الدقيق في DPI. الخطوات الأساسية—تثبيت Aspose.Words، تحميل المستند، تعديل `MarkdownSaveOptions`، والحفظ—بساطة كافية لسكريبت سريع ولكنها قوية بما يكفي لخطوط الإنتاج.

من هنا قد:

* توجيه الـ Markdown المُولد إلى مولد مواقع ثابتة مثل Hugo أو MkDocs.
* إضافة خطوة ما بعد المعالجة لإعادة تسمية الصور بأسماء أكثر معنى.
* دمج هذا الكود في Azure Function لتحويل المستندات عند الطلب.

لا تتردد في تجربة قيم DPI مختلفة، صيغ صور مختلفة، أو حتى CSS مخصص للـ Markdown المُولد. إذا واجهت أي مشكلة، اترك تعليقًا أدناه—تحويل سعيد!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}