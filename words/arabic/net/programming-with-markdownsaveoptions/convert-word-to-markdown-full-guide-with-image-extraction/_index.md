---
category: general
date: 2026-03-14
description: تحويل Word إلى Markdown بسرعة مع استخراج الصور من ملف docx باستخدام Aspose.Words.
  مثال خطوة‑بخطوة بلغة C# للمطورين.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- Aspose.Words C#
- markdown conversion tutorial
- docx image handling
language: ar
og_description: حوّل ملفات Word إلى Markdown واستخرج الصور من ملفات docx باستخدام
  Aspose.Words. اتبع هذا الدليل التفصيلي للحصول على تحويل خالٍ من المتاعب.
og_title: تحويل Word إلى Markdown – دليل C# الكامل
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: تحويل Word إلى Markdown – دليل كامل مع استخراج الصور
url: /ar/net/programming-with-markdownsaveoptions/convert-word-to-markdown-full-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحويل Word إلى Markdown – دليل C# كامل

هل احتجت يوماً إلى **تحويل Word إلى Markdown** لكنك لم تكن متأكدًا من كيفية الحفاظ على الصور المدمجة؟ لست وحدك. يواجه العديد من المطورين عقبة حيث ينتقل النص بنجاح، لكن الصور تختفي. الخبر السار؟ باستخدام بضع أسطر من C# ومكتبة Aspose.Words القوية، يمكنك **تحويل Word إلى Markdown** *و* **استخراج الصور من docx** في عملية واحدة سلسة.

في هذا الدرس سنستعرض كل ما تحتاجه: من تثبيت حزمة NuGet، تحميل ملف `.docx`، تكوين حفظ الـ markdown، إلى ربط رد نداء يضع كل صورة في مجلد مخصص ويعيد كتابة روابط الصور. في النهاية ستحصل على ملف Markdown جاهز للاستخدام ومجلد `resources` منظم يحتوي على كل صورة من مستند Word الأصلي.

## ما ستتعلمه

- كيفية إعداد Aspose.Words لـ .NET في مشروع C#.
- الكود الدقيق المطلوب **لتحويل Word إلى Markdown** مع الحفاظ على الصور.
- لماذا `ResourceSavingCallback` ضروري لـ **استخراج الصور من docx**.
- المشكلات الشائعة (مثل فواصل المسارات، أسماء الملفات المتكررة) وكيفية تجنبها.
- خطوات تحقق سريعة للتأكد من أن Markdown المُنتج يُظهر بشكل صحيح.

### المتطلبات المسبقة

| المتطلب | السبب |
|-------------|--------|
| .NET 6.0 أو أحدث (أو .NET Framework 4.7+) | تدعم Aspose.Words كلاهما؛ إصدارات الوقت الأحدث توفر أداءً أفضل. |
| Visual Studio 2022 (أو أي بيئة تطوير C#) | يجعل عملية تصحيح الأخطاء وإدارة الحزم أسهل. |
| اتصال إنترنت لاستعادة حزم NuGet | تُجلب المكتبة من المصدر الرسمي. |
| ملف `input.docx` تجريبي يحتوي على نص **وصور** | لرؤية استخراج الصور عمليًا. |

لا تحتاج إلى أدوات طرف ثالث إضافية — Aspose.Words يتولى كل شيء في الخلفية.

---

## الخطوة 1: تثبيت Aspose.Words عبر NuGet

أولاً، أضف حزمة Aspose.Words إلى مشروعك. افتح **Package Manager Console** وشغّل:

```powershell
Install-Package Aspose.Words
```

بدلاً من ذلك، استخدم الواجهة الرسومية: انقر بزر الماوس الأيمن على المشروع → *Manage NuGet Packages* → ابحث عن “Aspose.Words” → اضغط **Install**. سيجلب ذلك ملفات DLL الأساسية ومساحة الاسم `Saving` التي سنحتاجها لاحقًا.

> **نصيحة احترافية:** قم بتثبيت الإصدار (مثال، `22.12.0`) لتجنب التغييرات المفاجئة التي قد تكسر الكود عندما يتم تحديث المكتبة تلقائيًا.

---

## الخطوة 2: تحميل مستند Word المصدر

الآن بعد أن أصبحت المكتبة جاهزة، يمكننا تحميل ملف `.docx`. استخدم مسارًا مطلقًا أو نسبيًا يشير إلى المستند المصدر.

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file. Replace the placeholder with your actual path.
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **لماذا هذا مهم:** `Document` يحلل حزمة Word بالكامل، مما يمنحنا الوصول إلى الفقرات والجداول وأجزاء الصور المخفية التي سنستخرجها لاحقًا.

---

## الخطوة 3: إنشاء خيارات حفظ Markdown

تأتي Aspose.Words مع فئة `MarkdownSaveOptions` التي تسمح لنا بتعديل سلوك التحويل. على الأقل نقوم بإنشائها؛ لاحقًا سنرفق رد نداء.

```csharp
// Instantiate the options object.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
```

يمكنك تعديل الخصائص مثل `ExportImagesAsBase64` (ضبطه على `false` لأننا نريد ملفات صور منفصلة) أو `ExportHeadersFooters` إذا كنت تحتاج تلك الأقسام في Markdown.

---

## الخطوة 4: تكوين ResourceSavingCallback – استخراج الصور من DOCX

هذا هو جوهر الدرس. `ResourceSavingCallback` يتم استدعاؤه لكل **مورد** (صور، خطوط، إلخ) يرغب الحافظ في كتابته. من خلال توفير معالجنا الخاص نقرر أين تُحفظ الصورة وكيف يشير ملف Markdown إليها.

```csharp
mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
    (sender, args) =>
    {
        // 1️⃣ Define the folder where we’ll dump extracted pictures.
        string imageFolder = @"YOUR_DIRECTORY\resources\";

        // 2️⃣ Ensure the folder exists – create it on the fly.
        Directory.CreateDirectory(imageFolder);

        // 3️⃣ Preserve the original filename (e.g., Image1.png).
        string imageFileName = Path.GetFileName(args.FileName);
        string targetPath   = Path.Combine(imageFolder, imageFileName);

        // 4️⃣ Write the image stream to disk.
        using (FileStream fs = new FileStream(targetPath, FileMode.Create))
        {
            args.Stream.CopyTo(fs);
        }

        // 5️⃣ Tell the Markdown generator to use a relative path.
        //    This is the step that **extract images from docx** correctly.
        args.ResourceFileName = $"resources/{imageFileName}";
    });
```

### ما يفعله هذا

1. **ينشئ** مجلد فرعي `resources` إذا لم يكن موجودًا بالفعل.  
2. **ينسخ** كل تدفق صورة وارد إلى ذلك المجلد، مع الحفاظ على اسم الملف الأصلي لتجنب الالتباس.  
3. **يحدّث** رابط Markdown (`![alt](resources/Image1.png)`) بحيث يمكن للقراء رؤية الصورة عند عرض الملف.

> **حالة خاصة:** إذا شاركت صورتان نفس الاسم، فإن الصورة اللاحقة ستحل محل السابقة. لتجنب ذلك، يمكنك إضافة GUID مسبقًا أو استخدام `Path.GetUniqueFileName` (مساعد مخصص) قبل الحفظ.

---

## الخطوة 5: حفظ المستند كـ Markdown

مع ربط رد النداء، الخطوة الأخيرة هي سطر واحد يكتب ملف Markdown.

```csharp
// Choose the output path for the Markdown file.
string markdownPath = @"YOUR_DIRECTORY\output.md";

doc.Save(markdownPath, mdOptions);
```

بعد انتهاء هذا الاستدعاء، ستحصل على:

- `output.md` يحتوي على نص Markdown وروابط الصور مثل `![Image1](resources/Image1.png)`.  
- مجلد `resources` مليء بكل صورة تم استخراجها من ملف `.docx` الأصلي.

---

## الخطوة 6: التحقق من النتيجة

افتح `output.md` في أي عارض Markdown (VS Code، GitHub، Typora). يجب أن ترى عناوين المستند الأصلي، القوائم، و**الصور معروضة بشكل صحيح**. إذا كانت صورة مفقودة:

1. تحقق من أن مجلد `resources` يحتوي على الملف.  
2. تأكد من أن المسار النسبي في Markdown (`resources/<filename>`) يطابق اسم المجلد تمامًا (حسّاس لحالة الأحرف على Linux).  
3. تأكد من أن ملف الصورة غير تالف – افتحه مباشرةً في عارض صور.

---

## مثال كامل يعمل

فيما يلي البرنامج الكامل الجاهز للتنفيذ. استبدل العنصر النائب `YOUR_DIRECTORY` بمسار المجلد الفعلي الخاص بك.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class WordToMarkdown
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Load the source Word document.
        // -------------------------------------------------
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // -------------------------------------------------
        // 2️⃣ Prepare Markdown save options.
        // -------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // Export images as separate files, not Base64.
            ExportImagesAsBase64 = false
        };

        // -------------------------------------------------
        // 3️⃣ Set up the callback to **extract images from docx**.
        // -------------------------------------------------
        mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
            (sender, args) =>
            {
                string imageFolder = @"YOUR_DIRECTORY\resources\";
                Directory.CreateDirectory(imageFolder);

                string imageFileName = Path.GetFileName(args.FileName);
                string targetPath = Path.Combine(imageFolder, imageFileName);

                using (FileStream fs = new FileStream(targetPath, FileMode.Create))
                {
                    args.Stream.CopyTo(fs);
                }

                // Update the reference used inside the Markdown file.
                args.ResourceFileName = $"resources/{imageFileName}";
            });

        // -------------------------------------------------
        // 4️⃣ Save as Markdown.
        // -------------------------------------------------
        string outputPath = @"YOUR_DIRECTORY\output.md";
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Check output.md and the resources folder.");
    }
}
```

**الناتج المتوقع:** افتح `output.md` وسترى شيئًا مشابهًا لـ:

```markdown
# Sample Title

Here is some introductory text.

![Image1](resources/Image1.png)

More paragraphs…

![Diagram](resources/Diagram.jpg)
```

جميع الصور تظهر جنبًا إلى جنب مع النص، تمامًا كما كان في ملف Word الأصلي.

---

## أسئلة شائعة ومشكلات محتملة

**س: هل يمكنني تغيير تنسيق الصورة أثناء الاستخراج؟**  
**ج:** نعم. داخل رد النداء يمكنك إعادة ترميز التدفق (مثلاً إلى PNG) قبل كتابته. استخدم `System.Drawing` أو `ImageSharp` لمعالجة `args.Stream`.

**س: ماذا لو كان مستند Word يحتوي على صور SVG أو EMF؟**  
**ج:** تقوم Aspose.Words بتحويل معظم صيغ المتجهات إلى PNG نقطي بشكل افتراضي. إذا كنت تحتاج المتجه الأصلي، اضبط `mdOptions.ExportImageResolution` وتعامل مع التدفق وفقًا لذلك.

**س: هل يعمل هذا على .NET Core على Linux؟**  
**ج:** بالتأكيد. فقط تأكد من أن مسار `resources` يستخدم الشرطات المائلة للأمام (`/`) أو `Path.Combine` كما هو موضح. تذكر أن أنظمة ملفات Linux حساسة لحالة الأحرف، لذا حافظ على تناسق أسماء المجلدات.

**س: كيف يمكنني إخفاء الحواشي أو التعليقات؟**  
**ج:** عدل خصائص `mdOptions.ExportFootnotes` أو `mdOptions.ExportComments` قبل الحفظ.

---

## الخاتمة

لقد غطينا للتو **حلًا كاملاً من البداية إلى النهاية لتحويل Word إلى Markdown** مع استخراج **الصور من docx** بشكل موثوق. من خلال الاستفادة من `MarkdownSaveOptions` في Aspose.Words و`ResourceSavingCallback`، ستحصل على تحكم دقيق في كل من تحويل النص ومعالجة الصور. الكود مستقل بذاته، يعمل على أي منصة .NET، ويمكن دمجه في خطوط الأنابيب الحالية بأقل جهد.

هل أنت مستعد للخطوة التالية؟ فكر في أتمتة التحويلات الجماعية، دمج هذه المنطق في API بـ ASP.NET، أو توسيع رد النداء لإنشاء صور مصغرة لكل صورة مستخرجة. السماء هي الحد عندما تكون لديك عملية التحويل الأساسية.

![مثال تحويل Word إلى Markdown](convert-word-to-markdown.png "مثال تحويل Word إلى Markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}