---
category: general
date: 2026-03-28
description: تعلم كيفية تصدير مستند Word إلى markdown، وإضافة ظل للشكل، وحفظ PDF/UA
  باستخدام Aspose.Words في C# – دليل خطوة بخطوة.
draft: false
keywords:
- export word to markdown
- add shape shadow
- save pdf ua
- Aspose.Words markdown
- C# document conversion
language: ar
og_description: تصدير مستند Word إلى markdown، إضافة ظل للشكل، وحفظ PDF/UA باستخدام
  Aspose.Words في C#. دليل كامل مع الشيفرة والنصائح.
og_title: تصدير Word إلى Markdown – إضافة ظل الشكل وحفظ PDF/UA
tags:
- Aspose.Words
- C#
- Markdown
- PDF/UA
title: تصدير Word إلى Markdown مع ظلال الأشكال و PDF/UA
url: /ar/net/programming-with-markdownsaveoptions/export-word-to-markdown-with-shape-shadows-and-pdf-ua/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تصدير Word إلى Markdown مع ظلال الأشكال و PDF/UA

هل احتجت يومًا إلى **تصدير Word إلى markdown** مع الحفاظ على ظلال الأشكال الفاخرة وفي نفس الوقت الالتزام بمعايير PDF/UA؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحاولون الحفاظ على الدقة البصرية أثناء تحويل الصيغ، خاصةً عندما تكون إمكانية الوصول (PDF/UA) أمرًا ضروريًا.

في هذا الدليل سنستعرض مثالًا كاملاً وقابلًا للتنفيذ يوضح لك كيفية **تصدير Word إلى markdown**، **إضافة ظل للشكل** في رسم، وأخيرًا **حفظ PDF/UA** مع إجبار الأشكال العائمة أن تكون مضمنة داخل النص. سنستخدم Aspose.Words for .NET، المكتبة الرائدة للتحويل القوي للمستندات. لا سكريبتات خارجية، لا محولات يدوية — مجرد كود C# نظيف يمكنك وضعه في تطبيق console اليوم.

> **نصيحة احترافية:** إذا لم تقم بتثبيت Aspose.Words بعد، احصل على أحدث حزمة NuGet (`Install-Package Aspose.Words`) — فهي تعمل مع .NET 6+، .NET Framework 4.8، وحتى .NET Core.

## ما ستحتاجه

- **Visual Studio 2022** (أو أي بيئة تطوير تدعم .NET 6+)
- **Aspose.Words for .NET** (إصدار NuGet 23.8 أو أحدث)
- ملف `input.docx` تجريبي يحتوي على شكل واحد على الأقل (مثلًا مستطيل)
- معرفة أساسية بـ C# — سنبقي الصياغة بسيطة

مع هذه المتطلبات الأساسية، لنبدأ.

![مخطط يوضح تدفق تصدير Word إلى markdown](export_word_to_markdown_diagram.png){alt="مثال تصدير Word إلى markdown"}

## الخطوة 1: تحميل مستند Word في وضع الاسترداد  

قبل أن نتمكن من تعديل أي شيء، نحتاج المستند في الذاكرة. التحميل باستخدام **RecoveryMode.Recover** يلتقط أي تحذيرات استبدال الخطوط، وهو مفيد عندما يستخدم المصدر خطوطًا غير مثبتة لديك.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Saving;

// 1️⃣ Load the document while collecting warnings
var loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover,
    WarningCallback = new WarningInfoCollection()
};

Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*لماذا RecoveryMode؟*  
إذا كان الملف الأصلي يشير إلى خطوط مفقودة، سيقوم Aspose باستبدالها وإصدار تحذير. من خلال التقاط هذه التحذيرات يمكننا تسجيلها لاحقًا — مفيد للتصحيح ولتقارير الامتثال.

## الخطوة 2: إضافة ظل للشكل  

الآن بعد تحميل المستند، لنُحسّن مظهر أحد الأشكال. سنستخرج أول عقدة `Shape` ونفعّل ظلًا خفيفًا.

```csharp
// 2️⃣ Find the first shape and enable its shadow
Shape shape = (Shape)doc.GetChildNodes(NodeType.Shape, true)[0];
shape.ShadowFormat.Visible = true;
shape.ShadowFormat.BlurRadius = 4;   // soft edges
shape.ShadowFormat.Distance = 2;    // how far the shadow is from the shape
shape.ShadowFormat.Angle = 30;      // direction of the light source
```

*لماذا تعديل الظل؟*  
الظل يضيف عمقًا، مما يجعل الشكل يبرز في كل من Word والصورة المصدرة إلى markdown (إذا قمت بتحويل الشكل إلى صورة لاحقًا). كما أنه طريقة سريعة لاختبار بقاء الخصائص البصرية خلال مسار التحويل.

## الخطوة 3: تصدير المستند إلى Markdown (مع معادلات LaTeX)  

يمكن لـ Aspose.Words تحويل ملف Word إلى markdown نظيف. هنا نخبره أيضًا بتصدير أي معادلات OfficeMath كـ LaTeX، وهو المعيار الفعلي للوثائق العلمية.

```csharp
// 3️⃣ Configure markdown export options
var markdownOptions = new MarkdownSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
    // Store all extracted images in a dedicated folder
    ResourceSavingCallback = (s, e) =>
    {
        string assetsFolder = "YOUR_DIRECTORY/assets";
        Directory.CreateDirectory(assetsFolder);
        e.FileName = Path.Combine(assetsFolder, e.FileName);
    }
};

// Save as markdown
doc.Save("YOUR_DIRECTORY/output.md", markdownOptions);
```

*ما ستراه:*  
- ملف `output.md` يحتوي على صsyntax markdown قياسي.  
- جميع الصور المضمنة (بما فيها الشكل الذي أضفنا له الظل) تُحفظ تحت مجلد `assets/`.  
- أي معادلات تظهر ككتل LaTeX داخل `$…$`، جاهزة للعرض عبر MathJax أو KaTeX.

## الخطوة 4: حفظ نفس المستند كـ PDF/UA  

PDF/UA (PDF/Universal Accessibility) يضمن أن ملف PDF يطابق المعيار ISO 14289‑1. سنجبر أيضًا الأشكال العائمة على أن تُحفظ كعلامات مضمنة داخل النص، مما يبسط وسم إمكانية الوصول.

```csharp
// 4️⃣ Set up PDF/UA compliance and inline floating shapes
var pdfOptions = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfUAX2,
    ExportFloatingShapesAsInlineTag = true
};

// Save the PDF/UA file
doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*لماذا PDF/UA؟*  
إذا كان جمهورك يشمل مستخدمي قارئات الشاشة أو تحتاج إلى تلبية معايير الوصول القانونية، فإن PDF/UA هو الخيار المناسب. علم `ExportFloatingShapesAsInlineTag` يمنع الكائنات العائمة من كسر ترتيب القراءة المنطقي.

## الخطوة 5: مراجعة تحذيرات استبدال الخطوط  

بعد خطوات التحويل، من الممارسات الجيدة إظهار أي تحذيرات متعلقة بالخطوط التي تم التقاطها في **الخطوة 1**.

```csharp
// 5️⃣ List font‑substitution warnings (if any)
var warnings = (WarningInfoCollection)loadOptions.WarningCallback;
foreach (var warning in warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"⚠️ {warning.Description}");
}
```

إذا رأيت رسائل مثل *“Font 'Calibri' was substituted with 'Arial'”* فأنت الآن تعرف بالضبط أي خطوط كانت مفقودة ويمكنك اتخاذ قرار بشأن تضمين بديل أو شحن الخط المفقود مع تطبيقك.

## مثال كامل يعمل  

بجمع كل ما سبق، إليك البرنامج الكامل الذي يمكنك نسخه ولصقه في مشروع console جديد:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load with recovery mode and capture warnings
        var loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Recover,
            WarningCallback = new WarningInfoCollection()
        };
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Add a shadow to the first shape
        Shape shape = (Shape)doc.GetChildNodes(NodeType.Shape, true)[0];
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.BlurRadius = 4;
        shape.ShadowFormat.Distance = 2;
        shape.ShadowFormat.Angle = 30;

        // Export to Markdown with LaTeX math and custom assets folder
        var markdownOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            ResourceSavingCallback = (s, e) =>
            {
                string assetsFolder = "YOUR_DIRECTORY/assets";
                Directory.CreateDirectory(assetsFolder);
                e.FileName = Path.Combine(assetsFolder, e.FileName);
            }
        };
        doc.Save("YOUR_DIRECTORY/output.md", markdownOptions);

        // Save as PDF/UA, forcing floating shapes inline
        var pdfOptions = new PdfSaveOptions
        {
            Compliance = PdfCompliance.PdfUAX2,
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // Print any font‑substitution warnings
        var warnings = (WarningInfoCollection)loadOptions.WarningCallback;
        foreach (var warning in warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ {warning.Description}");
        }
    }
}
```

### النتيجة المتوقعة  

- `output.md` يحتوي على markdown نظيف، معادلات مشفرة بـ LaTeX، وروابط صور مثل `![Shape](assets/shape0.png)`.  
- `output.pdf` هو ملف PDF/UA متوافق ينجح في فحص إمكانية الوصول في Adobe Acrobat.  
- مخرجات الـ console تسرد أي تحذيرات استبدال خطوط، مما يساعدك على تتبع الخطوط المفقودة.

## أسئلة شائعة وحالات خاصة  

**ماذا لو كان المستند يحتوي على عدة أشكال؟**  
استخدم حلقة `doc.GetChildNodes(NodeType.Shape, true)` وطبق إعدادات الظل على كل عنصر.  

**هل يمكنني تغيير لون الظل؟**  
نعم — عيّن `shape.ShadowFormat.Color = Color.Gray;` قبل الحفظ.  

**هل يجب تعديل مسار مجلد الأصول لتوزيع الويب؟**  
بالطبع. استخدم مسارًا نسبيًا أو اضبط عنوان URL لـ CDN في `ResourceSavingCallback` لتقديم الصور بكفاءة.  

**هل سيفقد تصدير markdown أي ميزات خاصة بـ Word؟**  
ميزات مثل التغييرات المتتبعة، التعليقات، أو SmartArt المعقد لا تُمثَّل في markdown. إذا كنت تحتاج إليها، احتفظ بنسخة PDF/UA كاحتياطي.

## الخلاصة  

لقد تعلمت الآن كيفية **تصدير Word إلى markdown**، **إضافة ظل للشكل**، و**حفظ PDF/UA** باستخدام Aspose.Words في C#. يوضح مثال الكود الكامل سير عمل جاهز للإنتاج يتعامل مع تحذيرات الخطوط، إدارة الموارد، والامتثال لإمكانية الوصول — كل ذلك في سكريبت واحد سهل القراءة.

الخطوات التالية؟ جرّب تعديل معلمات الظل، استكشف `MarkdownSaveOptions` المختلفة (مثل `ExportImagesAsBase64`)، أو دمج هذه السلسلة في API ASP.NET Core يحول ملفات Word التي يرفعها المستخدمون في الوقت الفعلي. وإذا كنت مهتمًا بصيغ إخراج أخرى، تفقد خيارات **HTML**، **EPUB**، أو **TIFF** في Aspose — كل منها يتبع نمطًا مشابهًا.

برمجة سعيدة، ولتظهر مستنداتك دائمًا كما تصورتها!  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}