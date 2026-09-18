---
category: general
date: 2026-09-18
description: إنشاء شكل مستطيل في مستند Word باستخدام C#. تعلم كيفية إضافة أشكال متعددة،
  إضافة أشكال إلى مجموعة، وإدراج مجموعة أشكال باستخدام Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: ar
lastmod: 2026-09-18
og_description: إنشاء شكل مستطيل في ملف Word باستخدام C#. يوضح هذا الدليل كيفية إضافة
  أشكال متعددة، إضافة أشكال إلى مجموعة، وإدراج مجموعة أشكال باستخدام Aspose.Words.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: إنشاء شكل مستطيل وتجميع الأشكال في C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: إنشاء شكل مستطيل وتجميع أشكال متعددة في C#
url: /ar/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل وتجميع أشكال متعددة في C#

إذا كنت بحاجة إلى **إنشاء شكل مستطيل** في مستند Word، يوضح هذا الدليل حلاً كاملاً. سترى كيفية **إضافة أشكال متعددة**، **إضافة أشكال إلى مجموعة**، و **إدراج مجموعة أشكال** باستخدام Aspose.Words API لـ .NET.

التعامل مع الأشكال هو متطلب شائع عند إنشاء التقارير أو العقود أو المواد التسويقية برمجيًا. بنهاية هذا الدليل ستحصل على تطبيق C# console قابل للتنفيذ ينتج ملف `.docx` يحتوي على مستطيل، وإهليلج، ومجموعة تحتفظ بكل الشكلين.

المتطلبات المسبقة الوحيدة هي .NET SDK حديث (6.0 أو أحدث) ونسخة مرخصة من Aspose.Words لـ .NET. لا توجد أدوات إضافية مطلوبة.

## Prerequisites

- .NET 6.0 SDK أو أحدث  
- Aspose.Words لـ .NET (حزمة NuGet `Aspose.Words`)  
- إلمام أساسي بصياغة C#  

يمكنك تثبيت الحزمة بالأمر التالي:

```bash
dotnet add package Aspose.Words
```

## الخطوة 1: إنشاء شكل مستطيل باستخدام Aspose.Words

الخطوة الأولى هي إنشاء كائن `Shape` من النوع `Rectangle`. هذا الكائن يمثل المستطيل البصري الذي سيظهر في المستند.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**لماذا هذا مهم:** `ShapeType.Rectangle` يخبر Aspose.Words برسم مستطيل هندسي. ضبط `Width` و `Height` يحدد حجمه بالنقاط (نقطة واحدة = 1/72 بوصة). إضافة ألوان التعبئة والحد تجعل الشكل مرئيًا دون الحاجة إلى تنسيق إضافي.

## الخطوة 2: إضافة أشكال متعددة إلى المستند

بعد المستطيل، يمكنك إنشاء أي عدد من الأشكال الإضافية. في هذا المثال نضيف إهليلجًا لتوضيح كيفية عمل **إضافة أشكال متعددة**.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**لماذا هذا مهم:** كل استدعاء لـ `new Shape` ينشئ كائن رسم مستقل. من خلال إدراجها بشكل متسلسل، تقوم ببناء مجموعة من الأشكال التي يمكن لاحقًا تجميعها أو وضعها بشكل فردي.

## الخطوة 3: إضافة أشكال إلى مجموعة

تجميع الأشكال يبسط إدارة التخطيط لأن المجموعة تتصرف كعقدة واحدة. تُظهر هذه الخطوة كيفية **إضافة أشكال إلى مجموعة** باستخدام `GroupShape`.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**لماذا هذا مهم:** `GroupShape` يعمل كحاوية. عندما تحرك أو تدور أو تغير حجم المجموعة، تتبع جميع الأشكال الفرعية ذلك تلقائيًا. الصندوق المحيط (200 × 200 نقطة) يحدد مساحة الإحداثيات للأشكال الفرعية.

## الخطوة 4: إدراج مجموعة أشكال في المستند

الآن بعد أن احتوت المجموعة على المستطيل والإهليلج، تحتاج إلى **إدراج مجموعة أشكال** في الموقع المطلوب. قام الـ builder بالفعل بوضع المجموعة الفارغة، لكن يمكنك أيضًا إدراجها في مكان آخر إذا لزم الأمر.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**لماذا هذا مهم:** تعديل `Left` و `Top` ينقل المجموعة بالكامل داخل الصفحة. حفظ المستند يكتب هيكل الأشكال إلى ملف `.docx` يمكن فتحه في Microsoft Word أو LibreOffice أو أي عارض متوافق.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يجمع جميع الخطوات. انسخ الشيفرة إلى مشروع console جديد وشغّله لإنشاء `GroupShapeExample.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**الناتج المتوقع:** عند فتح `GroupShapeExample.docx` يظهر مجموعة واحدة تحتوي على مستطيل أزرق فاتح وإهليلج كورال فاتح، كلاهما موضع داخل حاوية 200 × 200 نقطة. يمكن تحديد المجموعة ككائن واحد في Word، مما يؤكد أن **إضافة أشكال إلى مجموعة** نجحت.

## الاختلافات الشائعة وحالات الحافة

| الحالة | التعديل الموصى به |
|-----------|------------------------|
| أنواع أشكال مختلفة (مثل `ShapeType.Line`) | إنشاء الشكل باستخدام `ShapeType` المطلوب وضبط هندسته وفقًا لذلك. |
| الحاجة إلى تدوير شكل | استخدم `shape.Rotation = 45;` (درجة) قبل إضافته إلى المجموعة. |
| مستندات أكبر تحتوي على مجموعات عديدة | إعادة استخدام نسخة واحدة من `DocumentBuilder`؛ تجنّب إنشاء builder جديد لكل مجموعة لتقليل استهلاك الذاكرة. |
| الحفظ كملف PDF بدلاً من DOCX | استدعِ `doc.Save("output.pdf", SaveFormat.Pdf);` بعد إدراج المجموعة. |

**نصيحة احترافية:** دائمًا قم بتعيين قيم صريحة لـ `Left` و `Top` للمجموعة عندما تحتاج إلى وضع دقيق. إذا تركتها، فإن المجموعة ترث موضع المؤشر الحالي للـ builder، مما قد يؤدي إلى نتائج تخطيط غير متوقعة.

## الخلاصة

أنت الآن تعرف كيفية **إنشاء شكل مستطيل**، **إضافة أشكال متعددة**، **إضافة أشكال إلى مجموعة**، و **إدراج مجموعة أشكال** في مستند Word باستخدام C#. يوضح المثال الكامل سير العمل الكامل من إنشاء المستند إلى حفظ الملف النهائي.

بعد ذلك، استكشف المواضيع ذات الصلة مثل **وضع الأشكال بالنسبة للنص**، **تطبيق تغليف النص**، و **تصدير الأشكال المجمعة إلى PDF**. تتيح لك هذه الإضافات بناء تخطيطات مستندات متقدمة وبرمجية باستخدام Aspose.Words.

## What Should You Learn Next?

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words لـ .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء مستند Word فارغ مع شكل مستطيل بظل – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}