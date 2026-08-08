---
category: general
date: 2026-08-07
description: كيفية تجميع الأشكال في Word باستخدام Aspose.Words وإضافة الأشكال إلى
  مستند Word باستخدام C#. اتبع هذا الدليل خطوة بخطوة للحصول على كود نظيف وقابل لإعادة
  الاستخدام.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: ar
lastmod: 2026-08-07
og_description: كيفية تجميع الأشكال في Word باستخدام Aspose.Words لـ .NET. يوضح هذا
  البرنامج التعليمي كيفية إضافة الأشكال إلى مستند Word، تجميعها، وحفظ الملف باستخدام
  كود C# واضح.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: كيفية تجميع الأشكال في Word – دليل C# سريع
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: كيفية تجميع الأشكال في Word وإضافة الأشكال إلى مستند Word
url: /ar/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تجميع الأشكال في Word وإضافة أشكال إلى مستند Word

إذا كنت بحاجة إلى **how to group shapes in Word**، فإن هذا الدليل يشرح لك العملية بالكامل باستخدام Aspose.Words for .NET. ستتعلم أيضًا **add shapes to Word document** ببضع أسطر من كود C#، بحيث يكون الناتج جاهزًا لأي سيناريو تقارير أو قوالب.

يغطي الدرس كل ما تحتاجه: حزم NuGet المطلوبة، ملف مصدر كامل، وتفسير لماذا كل خطوة مهمة. في النهاية يمكنك إنشاء ملف DOCX يحتوي على مستطيل وإهليلج مدمجين في شكل مجموعة واحد.

## المتطلبات المسبقة

* .NET 6.0 SDK أو أحدث مثبت  
* Visual Studio 2022 (أو أي بيئة تطوير تدعم .NET)  
* حزمة NuGet الخاصة بـ Aspose.Words for .NET (`Aspose.Words`) – النسخة التجريبية المجانية تعمل للاختبار، لكن الترخيص يزيل علامات التقييم  

هذه العناصر هي الاعتمادات الخارجية الوحيدة لـ **add shapes to Word document**.

## كيفية تجميع الأشكال في Word

جوهر الحل هو إنشاء أشكال فردية، وضعها على الصفحة، ثم تغليفها داخل `GroupShape`. الخطوات التالية تعكس الترتيب المنطقي للكود.

### الخطوة 1: إنشاء مستند ومُنشئ

`Document` تمثل الملف DOCX بالكامل. `DocumentBuilder` توفر واجهة برمجة تطبيقات مريحة لتحرير المستند.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*لماذا هذا مهم*: الـ `Document` هو الحاوية لجميع عناصر Word. الـ `DocumentBuilder` يتتبع موقع المؤشر الحالي، وهو مطلوب عندما تقوم لاحقًا بإدراج الشكل المجمع.

### الخطوة 2: إضافة شكل المستطيل

يتم إنشاء مستطيل عن طريق تحديد `ShapeType.Rectangle`. يتم ضبط العرض والارتفاع والموقع بالنقاط (1 pt ≈ 1/72 in).

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*لماذا هذا مهم*: ضبط `StrokeColor` يجعل الشكل مرئيًا عند فتح المستند. يمكنك أيضًا ملء الشكل بـ `FillColor` إذا كان هناك حاجة إلى داخلية صلبة.

### الخطوة 3: إضافة شكل الإهليلج

يستخدم الإهليلج `ShapeType.Ellipse`. حجمه وموقعه مستقلان عن المستطيل، مما يتيح لك التحكم في التخطيط النهائي للمجموعة.

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*لماذا هذا مهم*: بوضع الإهليلج عند `Left = 120`، لا يتداخل مع المستطيل، مما يجعل المجموعة مميزة بصريًا.

### الخطوة 4: تجميع الشكلين

`GroupShape` يعمل كحاوية تعالج أطفاله ككائن واحد. هذه هي العملية الأساسية لـ **how to group shapes in Word**.

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*لماذا هذا مهم*: التجميع يتيح لك تحريك أو تغيير حجم أو تدوير الشكلين معًا. أي تحويل يُطبق على `groupShape` ينتقل إلى أطفاله.

### الخطوة 5: إدراج الشكل المجمع في المستند

`DocumentBuilder.InsertNode` يضع الـ `GroupShape` في موقع المؤشر الحالي. نظرًا لأننا لم نحرك الـ builder، يظهر المجموعة في بداية الصفحة الأولى.

```csharp
builder.InsertNode(groupShape);
```

*لماذا هذا مهم*: إدراج العقدة مباشرةً يتجنب الحاجة إلى فقرة منفصلة أو خلية جدول. تصبح المجموعة جزءًا من تدفق المستند.

### الخطوة 6: حفظ المستند

أخيرًا، اكتب ملف DOCX إلى القرص. استخدم مسارًا كاملاً يمكن لتطبيقك الكتابة إليه.

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*لماذا هذا مهم*: `doc.Save` يُنهي جميع التغييرات. يمكن فتح الملف الناتج في Microsoft Word أو LibreOffice أو أي عارض يدعم DOCX.

## ملف المصدر الكامل

انسخ الكود أدناه إلى مشروع وحدة تحكم جديد (`dotnet new console`) وشغّله. البرنامج ينشئ ملفًا باسم `GroupShape.docx` يحتوي على مستطيل وإهليلج مجمّعين.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### النتيجة المتوقعة

افتح `GroupShape.docx`. سترى كائنًا بصريًا واحدًا يحتوي على مستطيل أزرق على اليسار وإهليلج أخضر على اليمين. تحديد الكائن في Word يبرز الشكلين معًا—دليل على أن **how to group shapes in Word** نجح.

## أسئلة شائعة وحالات خاصة

* **هل يمكنني إضافة أكثر من شكلين؟**  
  نعم. استدعِ `groupShape.AppendChild` لكل `Shape` إضافية قبل إدراج المجموعة.

* **ماذا لو احتجت لتدوير المجموعة؟**  
  اضبط `groupShape.RotationAngle = 45;` (الزاوية بالدرجات) بعد بناء المجموعة.

* **هل أحتاج لاستدعاء `doc.UpdatePageLayout()`؟**  
  ليس لهذا السيناريو. يتم تحديث التخطيط تلقائيًا عند حفظ المستند.

* **كيف يؤثر الترخيص على الكود؟**  
  باستخدام ترخيص Aspose.Words صالح (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) لا يحتوي المستند المُنشأ على علامة مائية للتقييم.

## الخلاصة

أنت الآن تعرف **how to group shapes in Word** و **add shapes to Word document** باستخدام Aspose.Words for .NET. غطى الدرس إنشاء مستند، تعريف أشكال فردية، تجميعها، إدراج المجموعة، وحفظ الملف.  

من هنا يمكنك التجربة مع:

* إضافة صناديق نصية أو صور إلى المجموعة  
* تغيير ألوان التعبئة، أنماط الخطوط، أو تأثيرات الظل  
* تجميع الأشكال داخل الجداول أو رؤوس الصفحات  

هذه الإضافات تتيح لك بناء قوالب Word متقدمة برمجيًا مع الحفاظ على نظافة الكود وصيانته. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}