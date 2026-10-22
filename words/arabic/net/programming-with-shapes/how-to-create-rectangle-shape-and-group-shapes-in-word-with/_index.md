---
category: general
date: 2026-09-05
description: إنشاء شكل مستطيل في مستند Word باستخدام Aspose.Words، ثم تعلم كيفية إدراج
  شكل إهليلجي وتجميع الأشكال في Word للحصول على تخطيطات أكثر غنى.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: ar
lastmod: 2026-09-05
og_description: إنشاء شكل مستطيل في مستند Word باستخدام Aspose.Words، ثم تعرف على
  كيفية إدراج شكل إهليلجي وتجميع الأشكال في Word لتصاميم معقدة.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: إنشاء شكل مستطيل وتجميع الأشكال في Word – دليل Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية إنشاء شكل مستطيل وتجميع الأشكال في Word باستخدام Aspose.Words
url: /ar/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء شكل مستطيل وتجميع الأشكال في Word باستخدام Aspose.Words

إذا كنت بحاجة إلى **إنشاء شكل مستطيل** في مستند Word، يوضح لك هذا الدليل الخطوات الدقيقة باستخدام Aspose.Words for .NET. ستتعرف أيضًا على كيفية إدراج كلمة إهليلجية، تجميع الأشكال في Word، وحفظ النتيجة كملف DOCX. يعمل الحل في أي مشروع .NET 6+ ولا يتطلب تثبيت Microsoft Office على الخادم.

يغطي البرنامج التعليمي كل شيء من إعداد المشروع إلى التعامل مع مشكلات التخطيط الشائعة، بحيث يمكنك نسخ الشيفرة وتشغيلها فورًا.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6 SDK أو أحدث مثبت  
* بيئة تطوير متوافقة مع NuGet (Visual Studio، Rider، أو VS Code)  
* ترخيص Aspose.Words for .NET (أو مفتاح تقييم مؤقت)  
* معرفة أساسية بـ C# وبنية مستندات Word  

تسمح هذه العناصر بترجمة الشيفرة وتشغيل الأشكال بشكل صحيح.

## الخطوة 1: إعداد المشروع وإضافة Aspose.Words

أنشئ مشروع وحدة تحكم جديد وأضف حزمة Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

توفر الحزمة الفئات `Document`، `DocumentBuilder`، `Shape`، و `GroupShape` المستخدمة طوال هذا الدرس.

## الخطوة 2: تهيئة مستند فارغ ومُنشئ

كائن `Document` يمثل ملف Word بالكامل، بينما يتيح لك `DocumentBuilder` إدراج المحتوى برمجيًا.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

إنشاء المستند أولاً يضمن أن جميع عمليات الشكل اللاحقة لها حاوية صالحة.

## الخطوة 3: **إنشاء شكل مستطيل** وتحديد أبعاده

المستطيل هو الحاوية الأكثر شيوعًا للنص أو الصور. تحدد حجمه بالنقاط (1 pt ≈ 1/72 inch).

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

لماذا هذه الخطوة مهمة: فئة `Shape` تُغلف الهندسة، التعبئة، وخصائص الخط. ضبط `Width` و `Height` قبل الإدراج يضمن ظهور الشكل بالحجم المتوقع.

## الخطوة 4: **كيفية إدراج كلمة إهليلجية** – إضافة شكل إهليلجي

يمكن استخدام الإهليلج لأيقونات أو علامات أو عناصر زخرفية. الشيفرة تشبه إنشاء المستطيل، فقط يتغير `ShapeType`.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

توضح خصائص `FillColor` و `Line.Color` كيفية تخصيص المظهر دون الحاجة إلى صور خارجية.

## الخطوة 5: **تجميع الأشكال في Word** – دمج المستطيل والإهليلج

يسمح التجميع بنقل، تغيير حجم، أو تدوير عدة أشكال كوحدة واحدة. هذا أساسي عندما تحتاج إلى رسم مركب (مثل أيقونة معنونة).

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

عند استدعاء `AppendChild`، تُزال الأشكال الأصلية من تدفق المستند الرئيسي وتصبح أبناءً لـ `GroupShape`. يتصرف التجميع كشكل واحد، مما يبسط تعديل التخطيط لاحقًا.

## الخطوة 6: حفظ المستند

أخيرًا، اكتب المستند إلى القرص. يمكنك اختيار أي تنسيق مدعوم (`.docx`، `.pdf`، `.html`، إلخ). في هذا الدرس نحتفظ بالتنسيق الأصلي لـ Word.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

بعد تشغيل البرنامج، افتح *GroupShape.docx* في Microsoft Word. سترى مستطيلًا وإهليلجًا مُجَمَّعين معًا، موضعين عند الإحداثيات التي حددتها.

## الاختلافات الشائعة والحالات الخاصة

| الحالة | ما الذي يجب تغييره | السبب |
|-----------|----------------|--------|
| **وحدات حجم مختلفة** | استخدم `ConvertUtil.InchToPoint(2.5)` للبوصات أو `ConvertUtil.MillimeterToPoint(30)` للمليمترات. | يبقي الشيفرة قابلة للقراءة عند العمل بوحدات غير النقاط. |
| **إضافة نص داخل المستطيل** | أنشئ عقدة `Paragraph`، اضبط خاصية `Text`، وأضفها إلى `rectangleShape` عبر `AppendChild`. | يتيح لك تسمية الشكل دون الحاجة إلى صناديق نص منفصلة. |
| **تدوير المجموعة** | اضبط `groupShape.Rotation = 45;` (درجة). | مفيد لإنشاء شارات مائلة أو علامات مائية. |
| **الحفظ كملف PDF** | استدعِ `doc.Save("GroupShape.pdf");`. | Aspose.Words يقوم تلقائيًا بتحويل الأشكال المتجهة إلى رسومات نقطية عند إخراج PDF. |
| **مجموعات متعددة** | أنشئ مثيلات إضافية من `GroupShape` وكرر خطوات الإلحاق/الإدراج. | يتيح تخطيطات صفحات معقدة تحتوي على عدة مركبات مستقلة. |

### نصيحة احترافية

دائمًا أضف الأشكال **قبل** تجميعها. إذا حاولت تجميع شكل هو بالفعل جزء من مجموعة أخرى، سيُطلق Aspose.Words استثناء `ArgumentException`. بناء المجموعة في طريقة واحدة يمنع هذا الخطأ أثناء التشغيل.

### احذر من

* **نظام الإحداثيات** – يتم قياس `Left` و `Top` من هوامش الصفحة اليسرى والعليا، وليس من حافة المستند. سوء الفهم قد يضع الأشكال خارج الصفحة.  
* **الترخيص** – بدون ترخيص صالح، سيحتوي المستند المحفوظ على علامة مائية تقول “Aspose.Words for .NET Evaluation”. ضع الترخيص مبكرًا في الشيفرة (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) لتجنب ذلك.

## الشيفرة الكاملة (قابلة للتنفيذ)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

تشغيل هذا البرنامج ينتج *GroupShape.docx* مع الأشكال المُجَمَّعة تمامًا كما هو موضح.

## الخلاصة

الآن تعرف كيف **تنشئ شكل مستطيل**، **تدرج كلمة إهليلجية**، و**تجمع الأشكال في Word** باستخدام Aspose.Words. يُظهر المثال الكامل سير العمل بالكامل—من تهيئة المستند إلى حفظ الملف النهائي—حتى تتمكن من دمج معالجة الأشكال في أي حل تقارير أو توليد مستندات تلقائي.

### ما الخطوة التالية؟

* استكشف **aspose.words create shapes** لأشكال هندسية أكثر تعقيدًا مثل `Polygon` أو `Freeform`.  
* اجمع الأشكال المُجَمَّعة مع **content controls** لبناء قوالب ديناميكية.  
* حوّل الـ DOCX إلى PDF أو HTML لترى كيف تُعرض الأشكال المتجهة عبر الصيغ المختلفة.  

لا تتردد في تجربة أحجام، ألوان، وتدويرات مختلفة. عندما تتقن تجميع الأشكال، يمكنك بناء مخططات متقدمة، شارات، وعناصر واجهة مستخدم مخصصة مباشرة داخل مستندات Word.

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}