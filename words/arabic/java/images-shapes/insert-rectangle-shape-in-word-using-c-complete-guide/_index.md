---
category: general
date: 2026-08-04
description: إدراج شكل مستطيل في مستند Word باستخدام C#. تعلّم كيفية تجميع الأشكال
  في Word، حفظ المستند بصيغة docx، واستخدام DocumentBuilder لتصاميم متقدمة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: ar
lastmod: 2026-08-04
og_description: إدراج شكل مستطيل في ملف Word باستخدام C# ثم تجميع الأشكال لتصاميم
  متقدمة. يغطي هذا الدرس أيضًا حفظ المستند كملف docx واستخدام DocumentBuilder بكفاءة.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: إدراج شكل مستطيل في Word – دليل خطوة بخطوة بلغة C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: إدراج شكل مستطيل في Word باستخدام C# – دليل كامل
url: /ar/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج شكل مستطيل في Word باستخدام C# – دليل كامل

إذا كنت بحاجة إلى **إدراج شكل مستطيل** في مستند Word باستخدام C#، فإن هذا الدرس يوضح لك بالضبط كيفية القيام بذلك. ستتعلم أيضًا **كيفية تجميع الأشكال** في Word، **حفظ المستند كملف docx**، و**كيفية استخدام Builder** لكتابة كود نظيف وسهل الصيانة.

العمل مع الأشكال هو طلب شائع عند إنشاء تقارير، شهادات، أو تخطيطات مخصصة برمجيًا. بنهاية هذا الدليل ستحصل على مثال كامل قابل للتنفيذ ينشئ مستطيلًا، يضيف إهليلجًا، يجمعهما، ويحفظ النتيجة كملف DOCX.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من توفر ما يلي:

* .NET 6.0 أو أحدث مثبت  
* Visual Studio 2022 (أو أي بيئة تطوير تدعم C#)  
* مكتبة **Aspose.Words for .NET** (متاحة عبر NuGet)  

يمكنك إضافة المكتبة بالأمر التالي:

```bash
dotnet add package Aspose.Words
```

## إدراج شكل مستطيل باستخدام DocumentBuilder

الخطوة الأولى هي إنشاء كائن `Document` جديد و`DocumentBuilder`. يوفر الـ builder واجهة API سلسة لإدراج المحتوى، بما في ذلك الأشكال.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

كائن `DocumentBuilder` هو العنصر الأساسي الذي ستستخدمه **لإدراج شكل مستطيل** وعناصر أخرى. يتتبع موقع المؤشر الحالي داخل المستند، لذا أي إدراج يحدث بالضبط حيث تحتاجه.

## كيفية إدراج شكل مستطيل

مع جاهزية الـ builder، استدعِ `InsertShape`. تحدد `ShapeType` والعرض والارتفاع بالنقاط (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*لماذا هذا مهم*: ضبط `FillColor` و`StrokeColor` يجعل المستطيل مميزًا بصريًا، مما يساعد عندما تقوم لاحقًا بتجميعه مع أشكال أخرى.

## كيفية تجميع الأشكال في Word

تجميع الأشكال يتيح لك نقلها، تدويرها، أو تنسيقها ككيان واحد. بعد إدراج المستطيل، أضف شكلًا آخر (إهليلج في هذا المثال) ثم أنشئ `GroupShape`.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

استدعاء `InsertGroupShape` ينشئ عنصرًا نائبًا يمكنه احتواء أي عدد من الأشكال الفرعية. عبر إلحاق المستطيل والإهليلج، تقوم فعليًا **بتجميع الأشكال في Word**. يتصرف التجميع كشكل واحد—يمكنك إعادة وضعه، إضافة حد، أو تغيير حجمه دون التأثير على تخطيط كل عنصر فرعي.

### نصيحة احترافية

بعد التجميع، يمكنك تغيير موضع المجموعة بالنسبة للصفحة:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## حفظ المستند كملف docx

بعد ترتيب الأشكال، تحتاج إلى حفظ الملف. طريقة `Document.Save` تحدد الصيغة تلقائيًا بناءً على امتداد الملف. لـ **حفظ المستند كملف docx**، مرّر مسارًا ينتهي بـ `.docx`.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

تشغيل البرنامج ينشئ `output.docx`. افتح الملف في Microsoft Word، وسترى مستطيلًا أزرق فاتحًا وإهليلجًا مرجانيًا فاتحًا مجمّعين معًا. يمكنك النقر على المجموعة وتحريكها ككائن واحد.

## كيفية استخدام DocumentBuilder بفعالية

`DocumentBuilder` ليس مجرد أداة لإدراج الأشكال؛ فهو يتعامل أيضًا مع النصوص، الجداول، رؤوس وتذييلات الصفحات. عندما تجمع إنشاء الأشكال مع النص، تذكر إعادة ضبط المؤشر إذا كنت بحاجة لإدراج محتوى في مكان آخر:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

الحفاظ على حالة الـ builder صريحة يجنب الكتابة فوق البيانات بطريق الخطأ ويجعل الكود أسهل صيانة.

## الحالات الخاصة والاختلافات

| الحالة | النهج الموصى به |
|-----------|----------------------|
| **أكثر من شكلين** | أدخل كل شكل، ثم استدعِ `AppendChild` لكل شكل قبل الحفظ. |
| **مجموعات متداخلة** | أنشئ مجموعة، أضف الأشكال، ثم أدخل تلك المجموعة في `GroupShape` آخر. |
| **وحدات قياس مختلفة** | استخدم `builder.ConvertPixelsToPoints` إذا كانت الأبعاد بوحدات البكسل. |
| **التوافق مع إصدارات Word القديمة** | احفظ كـ `.doc` بتغيير الامتداد؛ لا تزال معظم ميزات الأشكال تعمل. |

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في مشروع وحدة تحكم جديد. لا تحتاج إلى أي مقتطفات إضافية.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**النتيجة المتوقعة**: فتح `output.docx` يُظهر مستطيلًا أزرق فاتحًا وإهليلجًا مرجانيًا فاتحًا مجمّعين معًا، موضعهما 150 pt من الهامش الأيسر و100 pt من الأعلى. التسمية تظهر أسفل المجموعة.

## الخلاصة

أنت الآن تعرف **كيفية إدراج شكل مستطيل** في ملف Word باستخدام C#، **كيفية تجميع الأشكال في Word**، و**كيفية حفظ المستند كملف docx** باستخدام Aspose.Words `DocumentBuilder`. من خلال إتقان هذه الخطوات يمكنك بناء تخطيطات معقدة—شهادات، تقارير، أو نماذج مخصصة—كليًا عبر الكود.

بعد ذلك، استكشف المواضيع ذات الصلة مثل **إضافة صناديق نصية**، **العمل مع الجداول**، أو **التصدير إلى PDF**. كل منها يبني على أساسيات `DocumentBuilder` التي مارستها للتو.

هل أنت مستعد لأتمتة مستندات Word الخاصة بك؟ جرّب توسيع المثال بمزيد من الأشكال، تطبيق التدرجات، أو تكرار البيانات لإنشاء تقرير كامل في تشغيل واحد. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إدراج أشكال في مستندات Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}