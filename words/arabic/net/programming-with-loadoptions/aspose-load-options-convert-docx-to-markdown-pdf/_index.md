---
category: general
date: 2026-02-24
description: تعلم كيفية استخدام خيارات التحميل في Aspose لاستعادة ملفات DOCX التالفة،
  وتحويل DOCX إلى ماركداون، وتحويل Word إلى PDF مع معادلات LaTeX.
draft: false
keywords:
- aspose load options
- convert docx to markdown
- convert word to pdf
- recover corrupted docx
- export equations as latex
language: ar
og_description: إتقان خيارات التحميل في Aspose لاستعادة ملفات DOCX التالفة، وتحويل
  docx إلى markdown، وتصدير المعادلات بصيغة LaTeX أثناء إنشاء ملفات PDF/UA‑2.
og_title: خيارات تحميل Aspose – تحويل DOCX إلى ماركداون و PDF
tags:
- Aspose.Words
- C#
- Document Conversion
title: خيارات التحميل في Aspose – تحويل DOCX إلى ماركداون و PDF
url: /ar/net/programming-with-loadoptions/aspose-load-options-convert-docx-to-markdown-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Load Options – تحويل DOCX إلى Markdown و PDF

هل تساءلت يومًا كيف تسمح لك **aspose load options** بإنقاذ ملف Word تالف وتحويله إلى Markdown نظيف أو PDF متوافق؟ لست وحدك. يواجه العديد من المطورين مشكلة عندما يصل DOCX معطوبًا، أو عندما تختفي المعادلات أثناء التحويل. في هذا الدرس سنستعرض حلًا كاملًا جاهزًا للتنفيذ بلغة C# لا يقتصر فقط على *استعادة docx التالف* بل أيضًا **تحويل docx إلى markdown** و **تحويل word إلى pdf** مع **تصدير المعادلات كـ latex**.

سنغطي كل شيء من إعداد وضع الاستعادة إلى رفع الصور المستخرجة إلى حاوية سحابية، وأخيرًا إنتاج ملف PDF/UA‑2 يلتزم بمعايير الوصول. في النهاية، ستحصل على قاعدة شفرة واحدة تدير كلا التحويلين ببضع أسطر من الإعداد.

> **ما ستحصل عليه:**  
> • طريقة قوية لتحميل أي DOCX، حتى لو كان تالفًا جزئيًا.  
> • مخرجات Markdown تحتفظ بمعادلات OfficeMath كـ LaTeX.  
> • مخرجات PDF/UA‑2 مع الحفاظ على الأشكال العائمة كعلامات inline.  
> • رد نداء (callback) لإعادة رفع الصور يمكن إعادة استخدامه لتخزين سحابي.

## المتطلبات المسبقة

- **Aspose.Words for .NET** (الإصدار v23.12 أو أحدث).  
- .NET 6+ (أي SDK حديث يعمل).  
- SDK لتخزين سحابي من اختيارك (المثال يستخدم طريقة نائب).  
- إلمام أساسي بـ C# و Visual Studio أو VS Code.

إذا لم تقم بتثبيت Aspose.Words بعد، نفّذ:

```bash
dotnet add package Aspose.Words
```

## الخطوة 1: تحميل المستند باستخدام Aspose Load Options

أول شيء تحتاجه هو طريقة موثوقة لفتح DOCX قد يكون تالفًا. هنا تتألق **aspose load options**—فهي تسمح لك بإخبار المكتبة بمحاولة الاستعادة بدلاً من إلقاء استثناء.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Configure LoadOptions to recover corrupted documents.
LoadOptions loadOptions = new LoadOptions
{
    // RecoveryMode.Recover tells Aspose to salvage as much as possible.
    RecoveryMode = RecoveryMode.Recover
};

// Load the source file. Replace the path with your own.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**لماذا هذا مهم:**  
عندما يتم قص ملف Word أو يحتوي على XML غير صالح، يتوقف المحمل الافتراضي. بتمكين `RecoveryMode.Recover`، تقوم Aspose بتحليل ما يمكنها، وتتخطى الأجزاء التالفة، وتظل تقدم لك كائن `Document` قابل للاستخدام. هذا هو العمود الفقري لسيناريو *استعادة docx التالف*.

## الخطوة 2: إعداد تحويل Markdown (تصدير المعادلات كـ LaTeX)

الآن بعد أن أصبح المستند في الذاكرة، يمكننا تكوين كيفية حفظه كـ Markdown. هناك أمران حاسمان:

1. **OfficeMathExportMode.LaTeX** – يضمن أن تتحول أي معادلات رياضية إلى مقتطفات LaTeX، مع الحفاظ على دلالتها.  
2. **ResourceSavingCallback** – نقطة ربط تسمح لنا بتحميل الصور المستخرجة إلى حاوية سحابية بدلاً من حفظها محليًا.

```csharp
using Aspose.Words.Saving;

// Prepare Markdown save options.
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This converts OfficeMath objects to LaTeX.
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Hook to upload images to the cloud.
    ResourceSavingCallback = new CloudImageCallback()
};

// Save as Markdown.
document.Save("YOUR_DIRECTORY/result.md", markdownOptions);
```

**نصيحة احترافية:** إذا لم تكن بحاجة إلى LaTeX، غيّر `OfficeMathExportMode` إلى `Image`. لكن بالنسبة للوثائق العلمية، فإن LaTeX أكثر قابلية للنقل.

## الخطوة 3: تنفيذ رد نداء (Callback) رفع الصور السحابي

تستدعي Aspose `IResourceSavingCallback.ResourceSaving` لكل مورد خارجي (صور، مخططات، إلخ). أدناه تنفيذ بسيط يظاهر رفع الدفق إلى CDN ويعيد عنوان URL عام.

```csharp
using Aspose.Words.Saving;
using System.IO;

public class CloudImageCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Upload the image stream to your cloud storage and get a URL.
        string url = UploadToCloud(args.Stream, args.FileName);

        // Point the Markdown image reference to the CDN URL.
        args.Uri = url;

        // Prevent Aspose from writing a local copy.
        args.KeepOriginalDocumentUri = false;
    }

    private string UploadToCloud(Stream data, string name)
    {
        // Replace this stub with your actual SDK call.
        // For demo purposes we just return a placeholder.
        return $"https://cdn.example.com/{name}";
    }
}
```

**ماذا لو لم يكن لديك حاوية سحابية؟**  
يمكنك ببساطة تعيين `args.Uri = $"images/{args.FileName}"` والسماح لـ Aspose بكتابة الملفات بجوار ملف Markdown. يمنحك رد النداء (callback) السيطرة الكاملة.

## الخطوة 4: إعداد تحويل PDF (تحويل Word إلى PDF مع توافق UA‑2)

عندما يحتاج نفس المستند إلى أن يصبح PDF، خاصةً إذا كان يجب أن يلتزم بمعايير الوصول، توفر Aspose `PdfSaveOptions`. هناك إعدادان أساسيان لتحويل نظيف:

- **Compliance = PdfCompliance.PdfUa2** – ينتج ملف PDF/UA‑2، وهو المعيار ISO للـ PDFs القابلة للوصول.  
- **ExportFloatingShapesAsInlineTag = true** – يحافظ على الأشكال العائمة (مثل مربعات النص) بالترتيب الصحيح.

```csharp
using Aspose.Words.Saving;

// Prepare PDF save options.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    // Enforce PDF/UA‑2 compliance.
    Compliance = PdfCompliance.PdfUa2,

    // Preserve layout of floating shapes.
    ExportFloatingShapesAsInlineTag = true
};

// Save as PDF.
document.Save("YOUR_DIRECTORY/result.pdf", pdfOptions);
```

**لماذا هذا يعمل:**  
إعداد `Compliance` يدفع Aspose لإدراج العلامات المطلوبة، والنص البديل، وعناصر الهيكلة. علم `ExportFloatingShapesAsInlineTag` يضمن أن الأشكال التي كانت ستطفو فوق النص تُثبت كـ inline، مما يمنع مفاجآت التخطيط في PDF النهائي.

## الخطوة 5: مثال كامل من البداية إلى النهاية

بجمع كل شيء معًا، إليك البرنامج الكامل الذي يمكنك نسخه ولصقه في تطبيق Console.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Saving;

namespace AsposeDocxConversion
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load with recovery.
            LoadOptions loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // 2️⃣ Convert to Markdown (export equations as LaTeX, upload images).
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                ResourceSavingCallback = new CloudImageCallback()
            };
            doc.Save("YOUR_DIRECTORY/result.md", mdOptions);
            Console.WriteLine("✅ Markdown saved.");

            // 3️⃣ Convert to PDF/UA‑2 (preserve floating shapes).
            PdfSaveOptions pdfOptions = new PdfSaveOptions
            {
                Compliance = PdfCompliance.PdfUa2,
                ExportFloatingShapesAsInlineTag = true
            };
            doc.Save("YOUR_DIRECTORY/result.pdf", pdfOptions);
            Console.WriteLine("✅ PDF/UA‑2 saved.");
        }
    }

    // Callback for uploading images.
    public class CloudImageCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string url = UploadToCloud(args.Stream, args.FileName);
            args.Uri = url;
            args.KeepOriginalDocumentUri = false;
        }

        private string UploadToCloud(Stream data, string name)
        {
            // Insert real SDK code here.
            return $"https://cdn.example.com/{name}";
        }
    }
}
```

**الناتج المتوقع:**  
تشغيل البرنامج ينشئ ملفين في `YOUR_DIRECTORY`:

- `result.md` – مستند Markdown حيث تظهر كل معادلة كـ `$$\LaTeX$$` وروابط الصور تشير إلى `https://cdn.example.com/...`.  
- `result.pdf` – ملف PDF/UA‑2 متوافق يمكن فتحه في Adobe Reader مع اجتياز فاحص الوصول.

يمكنك فتح ملف Markdown في أي محرر أو تمريره إلى مولد مواقع ثابت، ويمكن توزيع ملف PDF على المستخدمين الذين يحتاجون إلى تنسيق قابل للوصول.

## الأسئلة المتكررة والحالات الخاصة

| السؤال | الجواب |
|----------|--------|
| **ماذا لو كان DOCX غير قابل للقراءة تمامًا؟** | حتى مع `RecoveryMode.Recover`، قد يرمي ملف تالف بالكامل استثناء `FileCorruptedException`. غلف استدعاء التحميل بـ `try/catch` واستخدم صفحة خطأ صديقة للمستخدم كبديل. |
| **هل يمكنني تغيير تنسيق الصورة أثناء الرفع؟** | نعم. داخل `UploadToCloud` يمكنك استخدام مكتبة معالجة صور (مثل ImageSharp) لتغيير الحجم أو التحويل إلى WebP قبل الإرسال إلى CDN. |
| **هل أحتاج إلى ترخيص لـ Aspose.Words؟** | النسخة التجريبية المجانية تعمل حتى 20 صفحة. للإنتاج، الترخيص التجاري يزيل علامة التقييم المائية ويفتح جميع الميزات. |
| **ماذا لو أردت الاحتفاظ بالمعادلات كصور بدلاً من LaTeX؟** | غيّر `OfficeMathExportMode` إلى `Image` في `MarkdownSaveOptions`. سيستقبل رد النداء (callback) تدفقات PNG يمكنك رفعها. |
| **كيف أضيف بيانات تعريف مخصصة إلى PDF؟** | استخدم `pdfOptions.CustomProperties.Add("Author", "Your Name")` قبل استدعاء `Save`. |

## 🎯 الخلاصة

لقد أوضحنا للتو كيف تمكّنك **aspose load options** من **استعادة docx التالف**، **تحويل docx إلى markdown**، و **تحويل word إلى pdf** مع **تصدير المعادلات كـ latex**. النهج معيّن: يمكنك استبدال رد نداء رفع الصور، تغيير مستوى التوافق، أو حتى إضافة خطوة DOCX‑to‑HTML باستخدام خيارات مماثلة.

الخطوات التالية التي قد تستكشفها:

- دمج هذه السلسلة في API ASP .NET Core بحيث يمكن للمستخدمين رفع الملفات والحصول على كل من Markdown و PDF فورًا.  
- استبدال عنوان CDN الوهمي بـ Azure Blob Storage أو استدعاءات SDK لـ Amazon S3.  
- إضافة خطوة ما بعد المعالجة التي تشغل أداة فحص Markdown لضمان مخرجات نظيفة.

لا تتردد في التجربة—ربما تضيف تصدير جدول إلى CSV أو تذييل PDF مخصص. API الخاص بـ Aspose.Words مرن بما يكفي لمعظم سيناريوهات أتمتة المستندات.

**برمجة سعيدة!** إذا واجهت أي مشكلة، اترك تعليقًا أدناه أو تواصل مع منتديات مجتمع Aspose.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}