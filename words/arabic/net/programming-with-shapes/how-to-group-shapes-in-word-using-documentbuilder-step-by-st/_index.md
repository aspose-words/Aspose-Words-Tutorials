---
category: general
date: 2026-09-08
description: تعرّف على كيفية تجميع الأشكال في Word باستخدام DocumentBuilder، وإنشاء
  مستند Word فارغ، وإدراج شكل مستطيل ببضع أسطر فقط من كود C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: ar
lastmod: 2026-09-08
og_description: تجميع الأشكال في Word باستخدام DocumentBuilder. يوضح هذا الدرس كيفية
  إنشاء مستند Word فارغ، وإدراج شكل مستطيل، وتجميع الأشكال في GroupShape.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: تجميع الأشكال في Word باستخدام DocumentBuilder – مثال كامل بلغة C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية تجميع الأشكال في Word باستخدام DocumentBuilder – دليل خطوة بخطوة
url: /ar/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تجميع الأشكال في Word باستخدام DocumentBuilder – دليل خطوة بخطوة

إذا كنت بحاجة إلى **تجميع الأشكال في Word** برمجياً، يوضح هذا الدرس حلاً كاملاً بلغة C#. ستتعرف على كيفية **إنشاء مستند Word فارغ**، واستخدام **DocumentBuilder**، و**إدراج شكل مستطيل** قبل تجميعه مع شكل بيضاوي. النتيجة هي `GroupShape` واحد يمكنك تحريكه، تغيير حجمه، أو تنسيقه ككائن واحد.

يغطي هذا الدليل كل ما تحتاجه لإنشاء مستند Word يحتوي على رسومات مجمعة باستخدام مكتبة Aspose.Words for .NET. بنهاية المقال ستحصل على مشروع قابل للتنفيذ ينتج ملف `GroupedShapes.docx` يحتوي على مستطيل وبيضاوي مدمجين في شكل واحد.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضاً مع .NET Framework 4.7.2+)
- حزمة NuGet الخاصة بـ Aspose.Words for .NET (`Aspose.Words`) – الإصدار 23.12 أو أحدث
- بيئة تطوير C# مثل Visual Studio 2022 أو Visual Studio Code
- إلمام أساسي بصياغة C# والبرمجة الكائنية

> **نصيحة احترافية:** قم بتثبيت حزمة NuGet من سطر الأوامر للحفاظ على مشروعك منظمًا:  
> `dotnet add package Aspose.Words --version 23.12.0`

## الخطوة 1: إنشاء مستند Word فارغ

العملية الأولى هي إنشاء كائن `Document`، الذي يمثل ملف Word فارغ، وإنشاء `DocumentBuilder` يتيح لك إضافة المحتوى.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**لماذا هذا مهم:** يوفر `Document` حاوية الملف، بينما يقدم `DocumentBuilder` واجهة برمجة تطبيقات سلسة لإدراج النصوص، الصور، والأشكال. بدون `DocumentBuilder` سيتعين عليك تعديل شجرة العقد في المستند يدويًا، وهو أمر عرضة للأخطاء.

## الخطوة 2: إدراج شكل مستطيل

المستطيل هو عنصر بناء شائع للمخططات. استخدم `InsertShape` مع `ShapeType.Rectangle` وحدد العرض والارتفاع بالنقاط (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**لماذا هذا مهم:** يحدد `Left` و `Top` موضع المستطيل بدقة على الصفحة، وهو أمر أساسي عندما تقوم لاحقًا بتجميعه مع أشكال أخرى. طريقة `InsertShape` تضيف الشكل تلقائيًا إلى الفقرة الحالية.

## الخطوة 3: إدراج شكل بيضاوي

بعد ذلك، أضف بيضاويًا سيقع بجانب المستطيل.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**لماذا هذا مهم:** يوضح استخدام `ShapeType` مختلف كيف يمكن لنفس واجهة `DocumentBuilder` إنشاء رسومات متنوعة. وضع البيضاوي بحيث يتقاطع مع المستطيل يجعل تأثير التجميع واضحًا.

## الخطوة 4: تجميع الشكلين

يعمل `GroupShape` كحاوية. من خلال إلحاق المستطيل والبيضاوي كعناصر فرعية، يتصرفان ككائن واحد.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**لماذا هذا مهم:** تحدد خاصية `Bounds` موقع المجموعة على الصفحة. من خلال إلحاق الأشكال الفرعية، تحتفظ بتنسيقها الفردي مع تمكين التحولات الجماعية (نقل، دوران، تغيير حجم).

## الخطوة 5: حفظ المستند

أخيرًا، اكتب المستند إلى القرص. يمكنك تغيير المسار إلى أي مجلد تفضله.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

عند فتح `GroupedShapes.docx` في Microsoft Word، سترى مستطيلًا وبيضاويًا مجمّعين معًا. تحديد المجموعة سيُظهر كلا الشكلين، مما يسمح لك بسحبهما أو تغيير حجمهما كوحدة واحدة.

### النتيجة المتوقعة

- ملف Word باسم **GroupedShapes.docx**
- الصفحة الأولى تحتوي على **مستطيل** (100 pt × 50 pt) في الموضع (50, 50)
- **بيضاوي** (80 pt × 80 pt) في الموضع (200, 70)
- كلا الشكلين جزء من **GroupShape** بحدود 300 pt × 200 pt

## الاختلافات الشائعة وحالات الحافة

| السيناريو | التعديل |
|----------|----------|
| **حجم صفحة مختلف** | عيّن `document.Sections[0].PageSetup.PageWidth` و `PageHeight` قبل إدراج الأشكال. |
| **أكثر من شكلين** | أنشئ كائنات `Shape` إضافية واستدعِ `groupShape.AppendChild(newShape)` لكل منها. |
| **تطبيق لون تعبئة** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **دوران المجموعة** | `groupShape.Rotation = 45;` (درجة) |
| **تصدير إلى PDF** | بعد حفظ DOCX، استدعِ `document.Save("GroupedShapes.pdf");` |

## الكود الكامل (جاهز للتنفيذ)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

انسخ الكود إلى مشروع وحدة تحكم جديد، استعد حزمة NuGet الخاصة بـ Aspose.Words، وشغّله. سيؤكد الطرفية موقع الملف، وعند فتحه ستظهر الرسومات المجمعة.

## الخلاصة

أصبحت الآن تعرف **كيفية تجميع الأشكال في Word** باستخدام Aspose.Words `DocumentBuilder`. استعرض الدرس إنشاء **مستند Word فارغ**، **إدراج شكل مستطيل**، إضافة بيضاوي، وتوحيدهما في `GroupShape`. مع هذه الأساسيات يمكنك بناء مخططات أكثر تعقيدًا، مخططات تدفق، أو رسومات مخصصة مباشرة من C#.

### ما الخطوة التالية؟

- استكشف **كيفية استخدام DocumentBuilder** للجداول، رؤوس وتذييلات الصفحات.
- دمج تقنيات **إدراج شكل مستطيل في Word** مع مربعات النص لإنشاء مخططات مشروحة.
- استخدم **إنشاء مستند Word فارغ** كقالب لتوليد تقارير آلية.

لا تتردد في تجربة الألوان، التدرجات، وإضافة أشكال أخرى. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شاملة مع شروح خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}