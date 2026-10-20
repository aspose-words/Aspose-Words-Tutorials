---
category: general
date: 2026-04-10
description: احفظ المستند كملف ماركداون باستخدام Aspose.Words لـ .NET. تعلّم كيفية
  التعامل مع الموارد الخارجية باستخدام ResourceSavingCallback.
draft: false
keywords:
- save document as markdown
- MarkdownSaveOptions
- ResourceSavingCallback
- C# document conversion
- external resources handling
- Aspose.Words for .NET
language: ar
og_description: احفظ المستند كملف markdown بسرعة. يوضح هذا الدليل كيفية استخدام Aspose.Words
  لـ .NET وResourceSavingCallback لإدارة الصور وCSS.
og_title: حفظ المستند كملف ماركداون باستخدام C# – دليل كامل
tags:
- C#
- Markdown
- Aspose.Words
title: حفظ المستند كملف ماركداون باستخدام C# – دليل كامل
url: /ar/net/programming-with-markdownsaveoptions/save-document-as-markdown-with-c-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ المستند كملف Markdown – دليل برمجة كامل

هل احتجت يوماً إلى **حفظ المستند كملف markdown** لكنك لم تكن متأكدًا من كيفية إبقاء الصور، ملفات CSS، وغيرها من الأصول الخارجية في المكان الصحيح؟ لست وحدك. في العديد من المشاريع، يصدر المطورون محتوى Word أو HTML إلى Markdown ثم يواجهون روابط مكسورة لأن الموارد لم تُحفظ أو لم تُعاد كتابة عناوين URI الخاصة بها.

المفتاح هو: Aspose.Words for .NET يجعل عملية التحويل سهلة للغاية، ومع `ResourceSavingCallback` صغير يمكنك تحديد بالضبط أين تُحفظ كل صورة أو ورقة أنماط على القرص. في هذا الدرس سنستعرض مثالًا واقعيًا لا يقتصر فقط على **حفظ المستند كملف markdown** بل يوضح لك أيضًا كيفية التعامل مع الموارد الخارجية كالمحترفين.

ستحصل في النهاية على ملف Markdown مستقل، ومجلد `MarkdownResources` منظم، وفهم أعمق لـ `MarkdownSaveOptions`، `ResourceSavingCallback`، وتحويل المستندات باستخدام C# بشكل عام.

## ما ستبنيه

بنهاية هذا الدليل ستحصل على:

* تطبيق console بلغة C# يقوم بتحميل أي ملف Word (`.docx`) أو HTML.
* كود ينشئ ملف Markdown باستخدام **MarkdownSaveOptions**.
* رد نداء مخصص يكتب كل صورة، أو CSS، أو خط إلى `YOUR_DIRECTORY/MarkdownResources`.
* ملف Markdown نظيف تكون روابط صوره على الشكل `resources/<filename>` – جاهز لمولدات المواقع الثابتة أو GitHub‑flavored Markdown.

بدون سكريبتات خارجية، بدون نسخ‑لصق يدوي. مجرد كود .NET نقي.

## المتطلبات المسبقة

* **Aspose.Words for .NET** (الإصدار 23.12 أو أحدث). يمكنك الحصول عليه من NuGet: `Install-Package Aspose.Words`.
* .NET 6.0 SDK أو أحدث – الصياغة أدناه تعمل مع .NET 6+.
* مستند Word تجريبي (`Sample.docx`) يحتوي على صورة واحدة على الأقل أو نمط يستدعي ملف CSS خارجي (إذا كنت تحول HTML).

هذا كل ما تحتاجه. إذا كان لديك ذلك، فلنبدأ.

## الخطوة 1: إعداد المشروع والاستيرادات

أولاً، أنشئ مشروع console جديد واستورد المساحات الاسمية اللازمة.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

> **نصيحة للمحترفين:** احتفظ بعبارات `using` في أعلى الملف – فهذا يجعل قراءة الكود أسهل، خصوصًا عندما تقوم المساعدات الذكية بتحليلها.

## الخطوة 2: تكوين `MarkdownSaveOptions`

قلب عملية التحويل يكمن في `MarkdownSaveOptions`. هذا الكائن يحدد لـ Aspose.Words كيفية كتابة ملف Markdown، وبشكل حاسم يوفر لنا نقطة ربط **للتعامل مع الموارد الخارجية**.

```csharp
// Step 2: Create and configure MarkdownSaveOptions
var markdownOptions = new MarkdownSaveOptions
{
    // This callback fires for every image, CSS file, or other external resource.
    ResourceSavingCallback = (sender, args) =>
    {
        // Extract just the file name (e.g., "logo.png")
        string fileName = Path.GetFileName(args.ResourceFileName);

        // Build the target path inside a folder called "MarkdownResources"
        string targetPath = Path.Combine("YOUR_DIRECTORY", "MarkdownResources", fileName);

        // Ensure the directory exists
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath)!);

        // Write the raw bytes to disk
        File.WriteAllBytes(targetPath, args.ResourceData);

        // Rewrite the URI that will appear in the generated Markdown
        args.ResourceFileName = $"resources/{fileName}";
        args.Handled = true; // Tell Aspose.Words we took care of it
    },

    // Optional: you can fine‑tune how headings are rendered, but the defaults work fine.
    ExportImagesAsBase64 = false // Keep images as separate files, not inline Base64 strings
};
```

**لماذا هذا مهم:** بدون رد النداء، سيقوم Aspose.Words إما بدمج الصور كـ Base64 (مما يجعل ملف Markdown ضخمًا) أو سيتجاهلها تمامًا. من خلال معالجة الموارد بأنفسنا نحافظ على خفة الملف وإمكانية نقله بالكامل.

## الخطوة 3: تحميل المستند المصدر

سواء كنت تبدأ من `.docx`، `.html` أو حتى `.rtf`، خطوة التحميل هي نفسها.

```csharp
// Step 3: Load the source document
string sourcePath = Path.Combine("YOUR_DIRECTORY", "Sample.docx"); // change extension if needed
Document doc = new Document(sourcePath);
```

إذا كنت تحول HTML يحتوي بالفعل على مراجع إلى CSS خارجي، فإن رد النداء نفسه سيلتقط تلك أوراق الأنماط أيضًا. هذه هي روعة **تحويل المستندات بـ C#** – حيث يُجرد المحرك الفروقات بين صيغ الملفات.

## الخطوة 4: حفظ المستند كملف Markdown

الآن نكتب ملف Markdown، مع تمرير الخيارات التي أعددناها مسبقًا.

```csharp
// Step 4: Save the document as Markdown
string markdownPath = Path.Combine("YOUR_DIRECTORY", "Doc.md");
doc.Save(markdownPath, markdownOptions);
```

بعد تنفيذ هذا السطر، ستحصل على:

* `Doc.md` – محتوى Markdown.
* `YOUR_DIRECTORY/MarkdownResources/` – مجلد يحتوي على كل صورة، أو CSS، أو خط كان المستند الأصلي يشير إليه.
* داخل `Doc.md`، روابط الصور تكون على الشكل `![Alt text](resources/logo.png)`.

## الخطوة 5: التحقق من النتيجة (اختياري لكن موصى به)

فحص سريع يوفر عليك ساعات من التصحيح لاحقًا.

```csharp
Console.WriteLine("✅ Markdown export complete!");
Console.WriteLine($"Markdown file: {markdownPath}");
Console.WriteLine($"Resources folder: {Path.Combine("YOUR_DIRECTORY", "MarkdownResources")}");
```

افتح `Doc.md` في VS Code أو أي عارض Markdown. يجب أن تظهر جميع الصور، ويجب أن يحتفظ النص بالعناوين، والقوائم، والجداول كما كانت في المصدر.

## مثال كامل يعمل

بدمج كل ما سبق، إليك برنامجًا بسيطًا لكنه كامل يمكنك لصقه في `Program.cs` وتشغيله.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Define where everything lives
        const string baseDir = @"C:\Temp\MarkdownExport";
        const string sourceFile = Path.Combine(baseDir, "Sample.docx");
        const string markdownFile = Path.Combine(baseDir, "Doc.md");

        // 2️⃣ Configure MarkdownSaveOptions with a ResourceSavingCallback
        var markdownOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (sender, args) =>
            {
                string fileName = Path.GetFileName(args.ResourceFileName);
                string targetPath = Path.Combine(baseDir, "MarkdownResources", fileName);
                Directory.CreateDirectory(Path.GetDirectoryName(targetPath)!);
                File.WriteAllBytes(targetPath, args.ResourceData);
                args.ResourceFileName = $"resources/{fileName}";
                args.Handled = true;
            },
            ExportImagesAsBase64 = false
        };

        // 3️⃣ Load the source document (Word, HTML, etc.)
        Document doc = new Document(sourceFile);

        // 4️⃣ Save as Markdown
        doc.Save(markdownFile, markdownOptions);

        // 5️⃣ Tell the user we’re done
        Console.WriteLine("✅ Save document as markdown completed successfully.");
        Console.WriteLine($"📄 Markdown file: {markdownFile}");
        Console.WriteLine($"📁 Resources folder: {Path.Combine(baseDir, "MarkdownResources")}");
    }
}
```

### النتيجة المتوقعة

تشغيل البرنامج سيطبع شيئًا مشابهًا لـ:

```
✅ Save document as markdown completed successfully.
📄 Markdown file: C:\Temp\MarkdownExport\Doc.md
📁 Resources folder: C:\Temp\MarkdownExport\MarkdownResources
```

فتح `Doc.md` سيظهر Markdown نظيف مع روابط صور مثل:

```markdown
![My Photo](resources/photo1.png)
```

جميع الصور المشار إليها موجودة في مجلد `MarkdownResources`، جاهزة للرفع إلى مستودع أو لخدمة موقع ثابت.

## أسئلة شائعة وحالات خاصة

### ماذا لو كان لدي **عدة** صور بنفس اسم الملف؟

`ResourceSavingCallback` يستقبل اسم الملف الأصلي، لكن يمكنك بسهولة إضافة GUID أو عداد لتجنب التصادم:

```csharp
string uniqueName = $"{Guid.NewGuid()}_{fileName}";
```

### هل يمكنني تصدير ملفات **CSS** بنفس الطريقة؟

بالطبع. رد النداء يُستدعى لأي مورد خارجي، بما في ذلك `.css`. فقط تأكد من أن عارض Markdown الخاص بك يعرف كيفية تضمين تلك الأنماط (مثلاً عبر رابط front‑matter أو وسم HTML `<link>`).

### ماذا عن المستندات **الكبيرة**؟

يُعالج رد النداء الموارد واحدةً تلو الأخرى، لذا يبقى استهلاك الذاكرة منخفضًا. إذا كنت تتعامل مع ملفات بحجم الجيجابايت، ففكّر في بث المستند المصدر من ملف أو موقع شبكة.

### هل يعمل هذا على **Linux/macOS**؟

نعم. Aspose.Words for .NET متعدد المنصات، والكود يستخدم فقط واجهات `System.IO` التي لا تعتمد على نظام التشغيل. فقط عدّل فواصل المسارات إذا رغبت في استخدام `Path.Combine` في كل مكان (كما هو موضح).

## الخلاصة

لقد استعرضنا معًا كيفية **حفظ المستند كملف markdown** باستخدام Aspose.Words for .NET، مستفيدين من `MarkdownSaveOptions` و`ResourceSavingCallback` المخصص لتجميع كل صورة، أو ملف CSS، أو خط خارجي بطريقة منظمة. النهج موثوق، يعمل عبر المنصات، ويمنحك سيطرة كاملة على بنية المجلد الناتج.

إذا كنت مستعدًا للخطوة التالية، جرّب ما يلي:

* تحويل عدة مستندات دفعة واحدة (حلقة عبر مجلد).
* تخصيص مخرجات Markdown – مثلاً باستخدام `ExportImagesAsBase64 = true` لحل ملف واحد.
* إضافة بيانات front‑matter للمنصات الثابتة مثل Hugo أو Jekyll.

برمجة سعيدة، ولتظل ملفات Markdown دائمًا مرتبة! 

![مخطط يوضح تدفق التحويل من المستند المصدر إلى Markdown مع مجلد الموارد – حفظ المستند كملف Markdown](https://example.com/placeholder-diagram.png "مخطط تدفق حفظ المستند كملف Markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}