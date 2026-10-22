---
category: general
date: 2026-09-30
description: إنشاء مستند فارغ وإدراج شكل مستطيل، وإهليلج، وتجميع أشكال متعددة في C#
  باستخدام Aspose.Words. تعلّم كيفية إدراج الأشكال وكيفية إنشاء مجموعة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: ar
lastmod: 2026-09-30
og_description: إنشاء مستند فارغ في C# وتعلم كيفية إدراج الأشكال وتجميع عدة أشكال
  باستخدام Aspose.Words. اتبع الدليل خطوة بخطوة.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: إنشاء مستند فارغ وتجميع الأشكال في C# – دليل Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: كيفية إنشاء مستند فارغ وإضافة أشكال باستخدام Aspose.Words في C#
url: /ar/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند فارغ وإضافة أشكال باستخدام Aspose.Words في C#

إذا كنت بحاجة إلى **إنشاء مستند فارغ** وتعبئته بالرسومات، يوضح لك هذا الدليل الخطوات بالضبط. ستتعرف على كيفية **إدراج شكل مستطيل**، إضافة كائنات رسم أخرى، ثم **تجميع عدة أشكال** بحيث تتصرف كوحدة واحدة.

التعامل مع الأشكال هو مطلب شائع عند إنشاء العقود، الشهادات، أو التقارير المخصصة. في هذا البرنامج التعليمي ستتعلم سير العمل الكامل، من تهيئة المستند إلى حفظ الملف النهائي، باستخدام Aspose.Words API لـ .NET.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6.0 (أو أحدث) SDK مثبت  
* ترخيص صالح لـ Aspose.Words for .NET (الإصدار التجريبي المجاني يكفي لهذا المثال)  
* بيئة تطوير متكاملة مثل Visual Studio 2022 أو Visual Studio Code  

لا توجد حزم NuGet إضافية مطلوبة بخلاف `Aspose.Words`.

## كيفية إنشاء مستند فارغ والعمل مع الأشكال

الخطوة الأولى هي إنشاء كائن `Document`. يمثل هذا الكائن ملف Word في الذاكرة ويمنحك الوصول إلى `DocumentBuilder`، وهو الأداة الأساسية لإدراج المحتوى.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**لماذا هذا مهم:** المستند الفارغ يمنحك لوحة رسم نظيفة. يحتفظ `DocumentBuilder` بنقطة الإدراج الحالية، لذا كل شكل تضيفه يُوضع تلقائيًا في الصفحة المناسبة.

## إدراج شكل مستطيل وأشكال أخرى

بعد ذلك، نضيف مستطيلًا وإهليلجًا. كلا الاستدعائين يستخدمان نفس طريقة `InsertShape`، وهي الطريقة الموصى بها **لإدراج الأشكال** في Aspose.Words.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*طريقة `InsertShape` تضع الشكل تلقائيًا في موقع المؤشر الحالي.* إذا كنت بحاجة إلى وضع دقيق، يمكنك تعديل `Shape.Left` و `Shape.Top` بعد الإدراج.

## تجميع عدة أشكال في كائن واحد

الآن نجمع المستطيل والإهليلج في كيان منطقي واحد. التجميع مفيد عندما تريد نقل أو تغيير حجم عدة أشكال معًا.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**كيف يعمل ذلك:** `InsertGroupShape` ينشئ حاوية تتصرف كأي `Shape` أخرى. عبر استدعاء `AppendChild`، تنقل الأشكال الموجودة إلى الحاوية، التي تقوم تلقائيًا بتحديث إحداثياتها النسبية.

### نصيحة عملية

إذا احتجت لاحقًا **لإنشاء مجموعة** برمجياً لأكثر من شكلين، ما عليك سوى تكرار `AppendChild` لكل نسخة إضافية من كائن `Shape`. يمكن للمجموعة أن تحتوي على أي عدد من كائنات الرسم، بما في ذلك الصور، مربعات النص، أو حتى مجموعات أخرى.

## مثال كامل – كيفية إدراج الأشكال وحفظ المستند

فيما يلي البرنامج الكامل القابل للتنفيذ الذي يوضح كل خطوة تم مناقشتها حتى الآن. تشغيل الكود ينتج ملف `ShapesDemo.docx` يحتوي على مستطيل، إهليلج، وشكل مجمع.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**الناتج المتوقع:** فتح `ShapesDemo.docx` في Microsoft Word يظهر صفحة واحدة بها مستطيل أزرق، إهليلج أخضر، وإطار رمادي يحيط بهما يمثل المجموعة. نقل المجموعة ينقل كلا الشكلين معًا، مما يؤكد نجاح عملية **تجميع عدة أشكال**.

## أسئلة شائعة ومعالجة الحالات الخاصة

| السؤال | الجواب |
|----------|--------|
| *ماذا لو أردت الأشكال في صفحة محددة؟* | استدعِ `builder.MoveToDocumentEnd();` قبل إدراج الأشكال، أو استخدم `builder.MoveToSection(sectionIndex);` لاستهداف قسم معين. |
| *هل يمكنني إضافة نص داخل شكل مجمع؟* | نعم. أنشئ `Shape` من النوع `ShapeType.TextBox`، اضبط نصه، ثم `AppendChild` إليه داخل `GroupShape`. |
| *هل أبعاد الشكل تستخدم نقاطًا أم بكسلات؟* | Aspose.Words يستخدم **النقاط** (1 pt = 1/72 inch). هذا يضمن حجمًا ثابتًا عبر الطابعات والشاشات. |
| *كيف أغيّر دوران المجموعة؟* | اضبط `groupShape.RotationAngle = 45;` (بالدرجات). جميع الأشكال الفرعية تدور حول أصل المجموعة. |

## الخلاصة

أنت الآن تعرف كيفية **إنشاء مستند فارغ**، **إدراج شكل مستطيل**، **إدراج أشكال** مثل الإهليلجات، و**تجميع عدة أشكال** في كائن واحد باستخدام Aspose.Words for .NET. يوضح مثال الكود الكامل النهج الموصى به، وتساعدك النصائح أعلاه على تكييف الحل لسيناريوهات أكثر تعقيدًا مثل إضافة مربعات نص أو تدوير المجموعات.

هل أنت مستعد لاستكشاف المزيد؟ جرّب إضافة شكل صورة إلى المجموعة، جرب ألوان تعبئة مختلفة، أو أنشئ تقريرًا متعدد الصفحات حيث يحتوي كل صفحة على مخطط مجمع خاص بها. المبادئ نفسها تنطبق، لذا يمكنك توسيع هذا النمط لأي مشروع أتمتة مستندات.

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}