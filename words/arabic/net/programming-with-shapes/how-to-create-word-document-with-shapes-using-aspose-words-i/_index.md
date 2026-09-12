---
category: general
date: 2026-09-11
description: تعلم كيفية إنشاء مستند Word، وإضافة شكل مستطيل، وتحديد أبعاد الشكل باستخدام
  Aspose.Words. دليل خطوة‑بخطوة بلغة C# لضبط حجم الشكل بدقة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: ar
lastmod: 2026-09-11
og_description: إنشاء مستند Word باستخدام Aspose.Words في C#. يوضح هذا الدليل كيفية
  إضافة شكل مستطيل، وتحديد حجم الشكل، وإدارة أبعاد الشكل برمجيًا.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: إنشاء مستند Word مع الأشكال – دليل Aspose.Words C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: كيفية إنشاء مستند Word مع أشكال باستخدام Aspose.Words في C#
url: /ar/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word يحتوي على أشكال باستخدام Aspose.Words في C#

إذا كنت بحاجة إلى **إنشاء مستند Word** يحتوي على رسومات مخصصة، يمكنك القيام بذلك بالكامل عبر الشيفرة. يشرح هذا الدليل كيفية إنشاء ملف Word، إضافة شكل مستطيل، والتحكم في كل أبعاد الشكل. في النهاية ستحصل على مقتطف قابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع .NET.

ستتعلم كيفية **إضافة شكل مستطيل**، **تحديد حجم الشكل**، و**تحديد أبعاد الشكل** داخل حاوية مجموعة. يستخدم المثال Aspose.Words 13.9، لكن المفاهيم تنطبق على الإصدارات الأحدث كذلك. لا تحتاج إلى خبرة سابقة مع Aspose drawing API—فقط معرفة أساسية بـ C#.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث مثبت  
- حزمة NuGet الخاصة بـ Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- بيئة تطوير مثل Visual Studio 2022 (أي محرر يدعم C# يعمل)  

وجود هذه الأدوات يتيح لك تشغيل الشيفرة فورًا دون إعدادات إضافية.

## الخطوة 1: تهيئة المستند والباني – أساسيات إنشاء مستند Word

العملية الأولى هي إنشاء كائن `Document` و`DocumentBuilder`. يمثل `Document` الملف نفسه، بينما يوفر `DocumentBuilder` واجهة برمجة تطبيقات سلسة لإدراج المحتوى.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**لماذا هذا مهم:**  
إنشاء المستند مسبقًا يمنحك لوحة رسم نظيفة. يبدأ مؤشر الباني في الفقرة الأولى، وهو المكان الذي سنقوم لاحقًا **بإنشاء أشكال في Word** فيه.

## الخطوة 2: بناء GroupShape لحفظ رسومات متعددة

يعمل `GroupShape` كحاوية؛ يمكنك تحريكها أو تدويرها أو تغيير حجمها ككل كوحدة واحدة. هنا نحدد عرض وارتفاع الحاوية بالنقاط (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**لماذا هذا مهم:**  
تجميع الأشكال يبسط إدارة التخطيط. إذا احتجت لاحقًا لإضافة أشكال أخرى (مثل دوائر أو مربعات نص)، فإنها ست inherit موقع وتدرج المجموعة.

## الخطوة 3: إنشاء شكل مستطيل وتكوين أبعاده

الآن نضيف المستطيل الفعلي. يتطلب مُنشئ `Shape` مرجع المستند ونوع الشكل. بعد الإنشاء نقوم صراحةً **بتحديد حجم الشكل** و**تحديد أبعاد الشكل**.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**لماذا هذا مهم:**  
تحديد العرض، الارتفاع، اليسار، والأعلى يمنحك تحكمًا دقيقًا في الشكل. هذا ضروري عندما يجب أن يتطابق المستند مع مواصفات تصميم أو نموذج مطبوع.

## الخطوة 4: تجميع المجموعة بإلحاق المستطيل

إلحاق المستطيل بـ `GroupShape` يجعله عقدة فرعية. يمكنك إضافة عدد من الأطفال حسب الحاجة قبل إدراج المجموعة في المستند.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**نصيحة:** إذا كنت تخطط لإضافة شكل ثانٍ، أنشئه بنفس الطريقة واستدعِ `group.AppendChild(secondShape)`. جميع الأطفال يشاركون نظام إحداثيات المجموعة.

## الخطوة 5: إدراج الشكل المجمّع في المستند وحفظه

بعد بناء المجموعة بالكامل، نضعها في الفقرة الحالية. خاصية `CurrentParagraph` في الباني تعطي وصولًا مباشرًا إلى شجرة العقد الأساسية.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**لماذا هذا مهم:**  
إلحاق المجموعة بفقرة يضمن ظهور الشكل ضمن تدفق النص. حفظ المستند ينهى عملية **إنشاء مستند Word**.

## الاختلافات الشائعة وحالات الحافة

| السيناريو | التعديل |
|----------|------------|
| **توجيه الصفحة مختلف** | ضع `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` قبل إنشاء المجموعة. |
| **عدة مستطيلات** | أنشئ كائنات `Shape` إضافية واستدعِ `group.AppendChild(newRect)` لكل منها. |
| **حجم ديناميكي بناءً على المحتوى** | احسب العرض/الارتفاع من أبعاد الصورة أو مقاييس النص، ثم عيّن إلى `rectangle.Width` / `rectangle.Height`. |
| **تصدير إلى PDF** | بعد `doc.Save`، استدعِ `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`. |
| **التوافق مع إصدارات Word القديمة** | احفظ باستخدام `SaveFormat.Doc` بدلاً من `Docx` لتوافق Word 97‑2003. |

هذه الاختلافات توضح كيف يمكن تعديل المنطق الأساسي ليتناسب مع متطلبات واقعية متعددة.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه، لصقه، وتشغيله. يتضمن جميع توجيهات `using`، نقطة دخول `Main`، وتعليقات تشرح كل سطر.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**الناتج المتوقع:**  
عند فتح *GroupShape.docx*، تظهر الصفحة الأولى مستطيلًا بحدود رمادية موضعه 50 pt من الهامش الأيسر/العلوي، مع إزاحة المستطيل نفسه 10 pt داخل المجموعة. الأبعاد تتطابق مع القيم المحددة في الشيفرة.

## الخلاصة

أصبحت الآن تعرف كيفية **إنشاء مستند Word**، **إضافة شكل مستطيل**، وتحديد **حجم الشكل** و**أبعاد الشكل** بدقة باستخدام Aspose.Words. نهج الشكل المجمّع يحافظ على مرونة التخطيط ويجهّزك لتوسعات مستقبلية مثل رسومات إضافية أو مربعات نص.

بعد ذلك، استكشف مواضيع ذات صلة مثل **إنشاء أشكال في Word** للدوائر، السهام، أو مسارات SVG مخصصة، وتعلم كيفية **تعيين لون تعبئة الشكل** أو **تطبيق الدوران**. جرب قياسات مختلفة لترى كيف يعرض Word النقاط مقابل السنتيمترات، ودمج الشيفرة في خطوط أنابيب توليد المستندات الأكبر.

برمجة سعيدة، ولا تتردد في تعديل هذا النمط لأي سيناريو تقارير آلية أو تعبئة نماذج تواجهه!

## ما الذي يجب أن تتعلمه لاحقًا؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [إنشاء مستند Word فارغ مع شكل مستطيل مظلل – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [دورة تعليمية حول ظل شكل Aspose.Words – إضافة ظل إلى شكل Word في C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}