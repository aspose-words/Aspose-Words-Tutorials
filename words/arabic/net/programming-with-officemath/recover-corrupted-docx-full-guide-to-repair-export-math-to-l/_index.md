---
category: general
date: 2025-12-23
description: تعرّف على كيفية استعادة ملفات docx التالفة، واستخدام وضع الاستعادة، وتصدير
  المعادلات إلى LaTeX، وإنشاء أسماء صور فريدة في C#. كود خطوة بخطوة مع شروحات.
draft: false
keywords:
- recover corrupted docx
- how to use recovery mode
- export equations to latex
- generate unique image names
language: ar
og_description: استعادة ملفات docx التالفة، واستخدام وضع الاستعادة، وتصدير المعادلات
  إلى LaTeX، وإنشاء أسماء صور فريدة باستخدام Aspose.Words في C#.
og_title: استعادة ملف docx التالف – دورة C# كاملة
tags:
- Aspose.Words
- C#
- Document Recovery
title: استعادة ملف docx تالف – دليل كامل للإصلاح، تصدير الرياضيات إلى LaTeX وإنشاء
  أسماء صور فريدة
url: /ar/net/programming-with-officemath/recover-corrupted-docx-full-guide-to-repair-export-math-to-l/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استعادة ملف docx التالف – دليل كامل للإصلاح، تصدير الرياضيات إلى LaTeX وإنشاء أسماء صور فريدة

هل فتحت ملف **.docx** يرفض التحميل لأنه تالف؟ لست وحدك. في العديد من المشاريع الواقعية، يمكن أن يتسبب ملف Word معطوب في إيقاف سير العمل بأكمله، لكن الخبر السار هو أنه يمكنك **استعادة ملفات docx التالفة** برمجيًا.  

في هذا البرنامج التعليمي سنستعرض الخطوات الدقيقة لـ **استعادة ملفات docx التالفة**، ونوضح **كيفية استخدام وضع الاستعادة**، ونظهر **تصدير المعادلات إلى LaTeX**، وأخيرًا **إنشاء أسماء صور فريدة** عند الحفظ إلى Markdown. في النهاية ستحصل على برنامج C# واحد قابل للتنفيذ يقوم بكل هذه المهام دون أي مشاكل.

## المتطلبات المسبقة

- .NET 6 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.6+).  
- Aspose.Words for .NET (نسخة تجريبية مجانية أو نسخة مرخصة). التثبيت عبر NuGet:

```bash
dotnet add package Aspose.Words
```

- إلمام أساسي بـ C# وإدارة ملفات الإدخال/الإخراج.  
- ملف `corrupt.docx` تالف لاختباره (يمكنك محاكاة الفساد عن طريق قطع جزء من ملف صالح).

> **نصيحة احترافية:** احتفظ بنسخة احتياطية من الملف الأصلي قبل البدء—الاستعادة تكون مدمرة فقط إذا قمت بالكتابة فوق المصدر.

## الخطوة 1 – استعادة ملف DOCX التالف باستخدام وضع الاستعادة

أول شيء نحتاج إلى القيام به هو إخبار Aspose.Words بمعاملة الملف الوارد على أنه قد يكون تالفًا. هنا يأتي دور **كيفية استخدام وضع الاستعادة**.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load a possibly corrupted document using recovery mode
        // -----------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded successfully – recovery mode applied.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
            return;
        }

        // ---------------------------------------------------------------
        // Subsequent steps go here...
        // ---------------------------------------------------------------
    }
}
```

**لماذا هذا مهم:**  
عند تفعيل `RecoveryMode.Recover`، تحاول Aspose.Words إعادة بناء شجرة المستند الداخلية، متجاوزة الأجزاء غير القابلة للقراءة مع الحفاظ على أكبر قدر ممكن من المحتوى. بدون ذلك، سيتسبب مُنشئ `Document` في رمي استثناء وستفقد أي فرصة لإنقاذ الملف.

> **ماذا لو كان الملف غير قابل للإصلاح؟**  
> ستظل المكتبة تُعيد كائن `Document`، لكن قد تكون بعض العقد مفقودة. يمكنك فحص `doc.GetChildNodes(NodeType.Any, true).Count` لمعرفة عدد العناصر التي نجت.

## الخطوة 2 – تصدير معادلات Office Math إلى LaTeX عند الحفظ كـ Markdown

تحتوي العديد من المستندات التقنية على معادلات مكتوبة باستخدام Office Math. إذا كنت بحاجة إلى تلك المعادلات بصيغة LaTeX—مثلاً للنشر على مدونة علمية—يمكنك طلب من Aspose.Words إجراء التحويل لك.

```csharp
        // -----------------------------------------------------------------
        // Step 2: Export Office Math equations to LaTeX in a Markdown file
        // -----------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        string markdownPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(markdownPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown with LaTeX equations saved to: {markdownPath}");
```

**كيف يعمل:**  
`OfficeMathExportMode.LaTeX` يُخبر الحافظ باستبدال كل عقدة `OfficeMath` بتمثيل LaTeX الخاص بها محاطًا بـ `$…$` (مضمن) أو `$$…$$` (عرض). يمكن للملف Markdown الناتج أن يُغذى مباشرةً إلى مولدات المواقع الثابتة مثل Hugo أو Jekyll.

> **حالة خاصة:** إذا كان المستند الأصلي يحتوي على كائنات معادلات معقدة (مثل المصفوفات)، قد ينتج عن تحويل LaTeX مخرجات متعددة الأسطر. راجع ملف `.md` المُولد للتأكد من توافقه مع توقعات التنسيق لديك.

## الخطوة 3 – حفظ المستند كـ PDF مع التحكم في وسوم الأشكال العائمة

أحيانًا تحتاج إلى نسخة PDF من نفس المستند، لكنك تهتم أيضًا بكيفية وسم الأشكال العائمة (الصور، مربعات النص) لتسهيل الوصول. علمة `ExportFloatingShapesAsInlineTag` تمنحك هذا التحكم.

```csharp
        // -----------------------------------------------------------------
        // Step 3: Save as PDF with custom floating‑shape tagging
        // -----------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true // true → <Figure>, false → <Div>
        };

        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved with inline tags to: {pdfPath}");
```

**لماذا نقلب هذا العلم؟**  
- `true` → تتحول الأشكال العائمة إلى وسوم `<Figure>`، والتي يتعامل معها العديد من قارئات الشاشة كصور متميزة مع تسميات توضيحية.  
- `false` → تُغلف الأشكال بوسوم عامة `<Div>`، قد يتم تجاهلها من قبل تقنيات المساعدة. اختر بناءً على متطلبات الوصول لديك.

## الخطوة 4 – تصدير إلى Markdown مع معالجة مخصصة للصور (إنشاء أسماء صور فريدة)

عند حفظ مستند Word إلى Markdown، تُكتب جميع الصور المدمجة إلى القرص. بشكل افتراضي، تُعطى هذه الصور اسم الملف الأصلي، مما قد يسبب تصادمًا إذا عالجت العديد من المستندات في نفس المجلد. دعنا نتدخل في عملية الحفظ و**ننشئ أسماء صور فريدة** تلقائيًا.

```csharp
        // -----------------------------------------------------------------
        // Step 4: Export to Markdown with custom image naming
        // -----------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                // Create a sub‑folder for markdown images if it doesn't exist
                string imageFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imageFolder);

                // Build a GUID‑based filename preserving the original extension
                string uniqueName = Guid.NewGuid().ToString() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imageFolder, uniqueName);
            }
        };

        string markdownPath2 = @"YOUR_DIRECTORY\out2.md";
        doc.Save(markdownPath2, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with uniquely named images saved to: {markdownPath2}");
```

**ما الذي يحدث خلف الكواليس؟**  
`ResourceSavingCallback` يُستدعى لكل مورد خارجي (صور، SVGs، إلخ) أثناء عملية الحفظ. بإرجاع مسار كامل، تحدد مكان حفظ الملف وما هو اسمه. يضمن الـ GUID **إنشاء أسماء صور فريدة** دون أي تدبير يدوي.

> **نصيحة:** إذا كنت تحتاج إلى نظام تسمية حتمي (مثلاً بناءً على نص alt للصورة)، استبدل `Guid.NewGuid()` بعملية تجزئة (`hash`) لاسم `resourceInfo.Name`.

## مثال عملي كامل

بدمج كل ما سبق، إليك البرنامج الكامل الذي يمكنك نسخه ولصقه في تطبيق Console:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------------------
        // Load the possibly corrupted document (Recovery Mode)
        // -------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded with recovery mode.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Unable to load document: {ex.Message}");
            return;
        }

        // -------------------------------------------------------------
        // Export equations to LaTeX in Markdown
        // -------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        string mdMathPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(mdMathPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown (LaTeX) saved: {mdMathPath}");

        // -------------------------------------------------------------
        // Save as PDF with inline floating‑shape tags
        // -------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved: {pdfPath}");

        // -------------------------------------------------------------
        // Export Markdown with unique image names
        // -------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                string imgFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imgFolder);
                string uniqueFile = Guid.NewGuid() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imgFolder, uniqueFile);
            }
        };
        string mdImgPath = @"YOUR_DIRECTORY\out2.md";
        doc.Save(mdImgPath, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with unique images saved: {mdImgPath}");
    }
}
```

### النتيجة المتوقعة

تشغيل البرنامج يجب أن ينتج رسائل في وحدة التحكم مشابهة لـ:

```
✅ Document loaded with recovery mode.
✅ Markdown (LaTeX) saved: YOUR_DIRECTORY\out.md
✅ PDF saved: YOUR_DIRECTORY\out.pdf
✅ Markdown with unique images saved: YOUR_DIRECTORY\out2.md
```

ستجد ثلاثة ملفات:

| الملف | الغرض |
|------|--------|
| `out.md` | ملف Markdown حيث تظهر كل معادلة Office Math بصيغة LaTeX (`$…$` أو `$$…$$`). |
| `out.pdf` | نسخة PDF مع وسم الأشكال العائمة كـ `<Figure>` لتحسين إمكانية الوصول. |
| `out2.md` + `md_images\*` | ملف Markdown بالإضافة إلى مجلد يحتوي على صور مسماة بأسماء فريدة (معتمدة على GUID). |

## الأسئلة المتكررة وحالات الحافة

| السؤال | الجواب |
|----------|--------|
| **ماذا لو كان الملف التالف لا يحتوي على محتوى قابل للاسترداد؟** | ستظل Aspose.Words تُعيد كائن `Document`، لكنه قد يكون فارغًا. تحقق من `doc.GetChildNodes(NodeType.Paragraph, true).Count` قبل المتابعة. |
| **هل يمكنني تغيير الفاصل الخاص بـ LaTeX؟** | نعم—عيّن `markdownMathOptions.MathDelimiter = "$$"` لإجبار الفواصل على نمط العرض. |
| **هل يجب تحرير كائن `Document`؟** | فئة `Document` تُطبق `IDisposable`. ضعها داخل كتلة `using` إذا كنت تعالج العديد من الملفات لتحرير الموارد الأصلية بسرعة. |
| **كيف أحافظ على أسماء الصور الأصلية؟** | إرجع `Path.Combine(imageFolder, resourceInfo.Name)` داخل الـ callback. فقط تذكر خطر تصادم الأسماء. |
| **هل نهج الـ GUID آمن للمستودعات التي تُدار بالتحكم بالإصدارات؟** | الـ GUID ثابت عبر عمليات التشغيل، لكنه غير قابل للقراءة البشرية. إذا كنت تحتاج إلى أسماء قابلة لإعادة الإنتاج، قم بتجزئة الاسم الأصلي مع إضافة ملح (salt) على مستوى المشروع. |

## الخلاصة

لقد أظهرنا لك كيفية **استعادة ملفات docx التالفة**، ووضحنا **كيفية استخدام  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}