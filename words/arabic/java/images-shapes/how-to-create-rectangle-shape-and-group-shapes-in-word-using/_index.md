---
category: general
date: 2026-11-18
description: تعلم كيفية إنشاء شكل مستطيل في مستند Word باستخدام C#. يغطي الدليل أيضًا
  ضبط حجم الشكل، وضبط موضع الشكل، وتجميع الأشكال في Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: ar
lastmod: 2026-11-18
og_description: إنشاء شكل مستطيل في ملف Word باستخدام C# وتعلم ضبط أبعاد الشكل، وضبط
  موضعه، وتجميع الأشكال في Word.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: إنشاء شكل مستطيل وتجميع الأشكال في Word باستخدام C#
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية إنشاء شكل مستطيل وتجميع الأشكال في Word باستخدام C#
url: /ar/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء شكل مستطيل وتجميع الأشكال في Word باستخدام C#

إذا كنت بحاجة إلى **إنشاء شكل مستطيل** في مستند Word، فإن هذا الدرس يوضح لك حلاً كاملاً وجاهزًا للتنفيذ. سترى كيفية ضبط حجم الشكل، وضبط موضع الشكل، وتجميع الأشكال في Word بحيث تتصرف ككائن واحد.

التعامل مع الأشكال هو متطلب شائع عند إنشاء التقارير أو الفواتير أو المخططات برمجيًا. بنهاية هذا الدليل ستكون قادرًا على إنشاء ملف `.docx` يحتوي على مستطيل، وإهليلج، وحاوية مجمعة — جميعها تم إنشاؤها باستخدام Aspose.Words for .NET.

## المتطلبات المسبقة

- .NET 6.0 SDK أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)
- حزمة NuGet لـ Aspose.Words for .NET (`Install-Package Aspose.Words`)
- محرر شفرة أو بيئة تطوير متكاملة (Visual Studio، VS Code، Rider، إلخ)

لا توجد مكتبات إضافية مطلوبة.

## كيفية إنشاء شكل مستطيل وتجميع الأشكال في Word

الخطوات الأساسية هي:

1. **إنشاء مستند فارغ** و `DocumentBuilder`.
2. **إدراج `GroupShape`** الذي سيحمل الأشكال الفردية.
3. **إنشاء شكل مستطيل**، ضبط أبعاده، وإضافته إلى المجموعة.
4. **إنشاء شكل إهليلج**، ضبط حجمه وموضعه، وإضافته إلى المجموعة.
5. **حفظ** المستند.

يتم شرح كل خطوة أدناه، ويتبع الشرح الشيفرة المصدرية الكاملة.

### الخطوة 1: تهيئة المستند والباني

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` يمثل ملف Word بالكامل، بينما `DocumentBuilder` يوفر واجهة برمجة تطبيقات سلسة لإدراج المحتوى. تهيئتهما إلزامية قبل أن تتمكن من إضافة أي أشكال.

### الخطوة 2: إدراج مجموعة أشكال

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

`GroupShape` يعمل كحاوية؛ جميع الأشكال الفرعية تتحرك معًا. هذه هي الطريقة الموصى بها **لتجميع الأشكال في Word** عندما تحتاج إلى تحويلات جماعية (مثل التحريك، أو الدوران، أو الحذف).

### الخطوة 3: إنشاء المستطيل وضبط حجمه

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

هنا نقوم **بإنشاء شكل مستطيل** و **ضبط حجم الشكل** عن طريق تعيين `Width` و `Height`. في Aspose.Words، يتم التعبير عن الأحجام بالنقاط (1 pt ≈ 1/72 in). ضبط الأبعاد صراحة يضمن ظهور المستطيل بالضبط كما هو مقصود.

### الخطوة 4: إنشاء الإهليلج، ضبط الأبعاد، وتحديد موضعه

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

إن **ضبط أبعاد الشكل** للإهليلج متطابقة للعرض والارتفاع، مما ينتج دائرة مثالية. الخاصية `Left` توضح **ضبط موضع الشكل**: يبدأ الإهليلج 120 pt إلى يمين أصل المجموعة، لذا لا يتداخل مع المستطيل.

### الخطوة 5: حفظ المستند

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

الحفظ يكتب ملف Word إلى القرص. يمكنك فتح `GroupShape.docx` في Microsoft Word للتحقق من أن المستطيل والإهليلج تم تجميعهما وتحديد موضعهما بشكل صحيح.

## ضبط أبعاد الشكل وحجمه – نظرة أعمق

- **النقاط مقابل البوصات**: 72 pt = 1 in. إذا كنت تفضل البوصات، اضرب في 72 (مثال، `2.5 * 72` لـ 2.5 in).
- **التحجيم التلقائي**: إذا تركت `Width` أو `Height`، يستخدم الشكل حجمه الافتراضي. اضبط **حجم الشكل** صراحة لتجنب مفاجآت التخطيط.
- **نسبة الأبعاد**: بالنسبة للأشكال مثل `Ellipse`، الحفاظ على تساوي `Width` و `Height` يحافظ على مظهر دائري.

## تحديد موضع الشكل في Word

تتحكم خصائص `Left` و `Top` في إزاحة الشكل داخل حاويته (المجموعة أو الصفحة). القيم الموجبة تحرك الشكل إلى اليمين/الأسفل؛ القيم السالبة تنقله إلى اليسار/الأعلى. عند التجميع، تكون المواقع نسبية لأصل المجموعة، مما يبسط حسابات التخطيط.

## تجميع الأشكال في Word باستخدام Aspose.Words

التجميع ضروري عندما تريد أن تتصرف عدة أشكال كوحدة واحدة. كائن `GroupShape`:

- يدعم `AppendChild` لإضافة أي `Shape` (مستطيل، إهليلج، صورة، إلخ).
- يسمح لك بتحريك أو تدوير أو حذف المجموعة بأكملها باستدعاء واحد.
- يحافظ على مواقع الأشكال الفرعية نسبياً إلى المجموعة، مما يجعل المخططات المعقدة أسهل في الإدارة.

**نصيحة احترافية:** بعد إضافة جميع الأشكال الفرعية، يمكنك تعديل `Width` و `Height` و `Left` و `Top` للمجموعة لإعادة وضع المجموعة بأكملها في خطوة واحدة.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه، لصقه، وتشغيله. يتضمن جميع توجيهات `using`، ودالة `Main`، وتعليقات تشرح كل سطر.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**الناتج المتوقع:** بعد تشغيل البرنامج، يظهر `GroupShape.docx` في مجلد التنفيذ. فتحه في Word يظهر مستطيل (100 pt × 50 pt) على اليسار وإهليلج (80 pt × 80 pt) موضعه 120 pt إلى اليمين، كلاهما داخل كائن مجمع واحد.

![مستند Word مع مستطيل وإهليلج مجمّعين](grouped_shapes.png){: .center alt="لقطة شاشة لمستند Word يظهر مستطيلًا وإهليلجًا مجمّعين تم إنشاؤهما باستخدام C#" }

*الصورة أعلاه توضح النتيجة النهائية؛ يمكن اختيار المستطيل والإهليلج ككائن واحد.*

## أسئلة شائعة وحالات حافة

| السؤال | الإجابة |
|----------|--------|
| **هل يمكنني إضافة أكثر من شكلين؟** | نعم. استدعِ `group.AppendChild(yourShape)` لكل شكل إضافي. |
| **ماذا لو احتجت إلى تدوير المجموعة؟** | استخدم `group.RotationAngle = 45;` (درجة) بعد إضافة جميع العناصر الفرعية. |
| **كيف يمكنني تغيير لون خلفية المجموعة؟** | عيّن `group.FillColor = System.Drawing.Color.LightGray;`. |
| **هل سيعمل هذا مع ملفات .doc؟** | Aspose.Words يدعم `.doc` و `.docx`. الكود نفسه يعمل؛ فقط غير امتداد الملف في `Save`. |
| **هل هناك تأثير على الذاكرة عند تجميع عدد كبير من الأشكال؟** | التجميع نفسه يضيف حملاً بسيطًا على الذاكرة. القلق الرئيسي هو عدد الأشكال الإجمالي؛ حافظ على عدد معقول للوثائق الكبيرة. |

## الخلاصة

في هذا الدرس تعلمت كيفية **إنشاء شكل مستطيل** في ملف Word باستخدام C#، وكيفية **ضبط حجم الشكل**، **ضبط أبعاد الشكل**، **ضبط موضع الشكل**، وأخيرًا كيفية **تجميع الأشكال في Word** باستخدام Aspose.Words. المثال الكامل يوضح نهجًا نظيفًا وقابلًا للصيانة يمكنك توسيعه إلى مخططات أكثر تعقيدًا، أو رسوم بيانية، أو رسومات مخصصة.

التالي قد تستكشفه:

- إضافة نص داخل الأشكال (`Shape.TextPath.Text = "Hello"`).
- إدراج صور في `GroupShape`.
- تصدير الأشكال المجمعة إلى PDF باستخدام `doc.Save("output.pdf")`.

لا تتردد في تجربة أحجام مختلفة، مواضع، وأنواع أشكال إضافية لتلبية احتياجات مشروعك. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء شكل مستطيل وتجميع الأشكال في Word باستخدام Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}