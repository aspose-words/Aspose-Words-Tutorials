---
category: general
date: 2026-09-08
description: إنشاء شكل مستطيل في مستند Word باستخدام C#. تعلم كيفية ضبط حجم الشكل،
  تجميع أشكال متعددة، وإنشاء مستند Word فارغ برمجيًا.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: ar
lastmod: 2026-09-08
og_description: إنشاء شكل مستطيل في مستند Word باستخدام C#. يوضح هذا الدليل كيفية
  ضبط حجم الشكل، تجميع عدة أشكال، وإنشاء مستند Word فارغ برمجيًا.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: إنشاء شكل مستطيل وتجميع الأشكال في Word باستخدام C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: إنشاء شكل مستطيل وتجميع الأشكال في Word باستخدام C#
url: /ar/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل وتجميع الأشكال في Word باستخدام C#

إذا كنت بحاجة إلى **إنشاء شكل مستطيل** داخل ملف Word، فإن هذا الدرس يقدم لك حلاً كاملاً وجاهزًا للتنفيذ. ستتعرف على كيفية ضبط حجم الشكل، وتجميع عدة أشكال، وإنشاء مستند Word فارغ من الصفر—كل ذلك باستخدام مكتبة Aspose.Words for .NET.

التعامل مع مستندات Word برمجيًا غالبًا ما يشعر وكأنه موازنة للعديد من التفاصيل الصغيرة. في نهاية هذا الدليل ستحصل على طريقة واحدة تنتج ملف `.docx` يحتوي على مستطيل وإهليلج مُجَمَّعين معًا، جاهزين لمزيد من التحرير أو الطباعة.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

* .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.6+)
* نسخة مرخصة من **Aspose.Words for .NET** (يمكنك استخدام مفتاح تقييم مجاني)
* بيئة تطوير متكاملة (IDE) مثل Visual Studio 2022 أو Visual Studio Code
* إلمام أساسي بصياغة C#

لا توجد حزم NuGet إضافية مطلوبة بخلاف `Aspose.Words`.

## الخطوة 1: إنشاء مستند Word فارغ

الخطوة الأولى هي إنشاء مستند فارغ سيستضيف الأشكال. هذا يلبي متطلب *إنشاء مستند Word فارغ*.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

إنشاء مستند فارغ يمنحك مساحة عمل نظيفة. كائن `Document` يمثل الملف `.docx` بالكامل، و`FirstSection.Body.FirstParagraph` هو نقطة الإدراج الافتراضية للعناصر الجديدة.

## الخطوة 2: إنشاء شكل مستطيل

الآن يمكنك إضافة المستطيل. هنا يحدث عملية **إنشاء شكل مستطيل**.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

تحديد الأبعاد مباشرة يفي بكلمة المفتاح **set shape size**. جميع قيم الحجم تُعبّر عنها بالنقاط، مما يوفر تحكمًا دقيقًا في مظهر الشكل في المستند النهائي.

## الخطوة 3: إنشاء شكل إضافي (إهليلج)

حالة استخدام شائعة هي دمج عدة أشكال. هنا نضيف إهليلجًا سيشارك لاحقًا نفس الحاوية.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

كلا الشكلين لا يزالان مستقلين في هذه المرحلة. الخطوة التالية توضح كيفية **تجميع عدة أشكال** معًا.

## الخطوة 4: تجميع الأشكال في Word

تجميع الأشكال يتيح لك نقلها أو تغيير حجمها أو تنسيقها كوحدة واحدة. هذا يلبي متطلبات **group shapes in word** و **group multiple shapes**.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

خاصية `GroupShape.Bounds` تحدد نظام الإحداثيات للأشكال الفرعية. بوضع المستطيل والإهليلج داخل نفس `GroupShape`، يمكنك لاحقًا نقلهما أو تدويرهما معًا باستدعاء واحد.

## الخطوة 5: حفظ المستند

أخيرًا، احفظ المستند على القرص. سيحتوي الملف على الأشكال المجمعة التي أنشأتها للتو.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

بعد تشغيل البرنامج، افتح `GroupedShapes.docx` في Microsoft Word. يجب أن ترى مستطيلًا وإهليلجًا مُجَمَّعين معًا؛ اختيار أحد الشكلين سيختار الآخر أيضًا، مما يؤكد نجاح التجميع.

## الكود الكامل

انسخ البرنامج الكامل التالي إلى مشروع تطبيق console جديد وشغّله. لا يلزم أي كود إضافي.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### النتيجة المتوقعة

تشغيل البرنامج ينتج `GroupedShapes.docx`. فتح الملف في Word يظهر:

* **مستطيل** (100 pt × 50 pt) بحد أزرق وتعبئة رمادية فاتحة.
* **إهليلج** (80 pt × 80 pt) بحد أخضر داكن وتعبئة صفراء فاتحة.
* كلا الشكلين داخل مجموعة واحدة، لذا نقل أحدهما ينقل الآخر.

## أسئلة شائعة وحالات خاصة

| السؤال | الإجابة |
|----------|--------|
| **هل يمكنني إضافة أكثر من شكلين إلى المجموعة؟** | نعم. أنشئ كائنات `Shape` إضافية واستدعِ `group.AppendChild(yourShape)` لكل منها. |
| **ماذا لو احتجت إلى تدوير المجموعة؟** | عيّن `group.RotationAngle = 45;` (بالدرجات). جميع الأشكال الفرعية تدور معًا. |
| **هل يمكن تجميع الأشكال بعد حفظ المستند؟** | يجب تعديل بنية المستند قبل الحفظ؛ وإلا سيتعين عليك تحميل الملف، وتحديد الأشكال، وإعادة إنشاء المجموعة. |
| **هل أحتاج إلى تحرير أي كائنات؟** | Aspose.Words يدير موارده الخاصة، لكن يجب تحرير كائنات `FileStream` إذا قمت بفتح التدفقات يدويًا. |
| **هل سيعمل الكود مع تنسيق .doc (ثنائي)؟** | نعم، غير `doc.Save("output.doc")`. سلوك التجميع هو نفسه. |

## الخاتمة

أنت الآن تعرف كيفية **إنشاء شكل مستطيل**، **تحديد حجم الشكل**، و**تجميع عدة أشكال** داخل ملف Word باستخدام C#. يتيح لك هذا النهج بناء مخططات معقدة، علامات مائية، أو تقارير مبنية على القوالب برمجيًا دون الحاجة إلى تحرير يدوي.

### الخطوات التالية

* استكشف **group shapes in word** أكثر بإضافة صناديق نصية أو صور إلى نفس المجموعة.
* استخدم نمط `SetShapeSize` لحساب الأبعاد ديناميكيًا بناءً على تخطيط الصفحة.
* دمج هذه التقنية مع حقول دمج البريد لإنشاء مستندات مخصصة على نطاق واسع.

لا تتردد في تجربة أنواع مختلفة من الأشكال، الألوان، وتحويلات المجموعات. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء مستند Word فارغ مع شكل مستطيل بظل – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [إنشاء مستند Word مع مستطيل بظل – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}