---
category: general
date: 2026-08-10
description: إنشاء مستند Word برمجيًا باستخدام Aspose.Words، وتعلم كيفية تجميع عدة
  أشكال في Word، وإضافة مستطيل إلى Word، وإنشاء مجموعة أشكال في C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: ar
lastmod: 2026-08-10
og_description: إنشاء مستند Word برمجيًا باستخدام Aspose.Words. يوضح هذا الدليل كيفية
  تجميع أشكال متعددة في Word، وإضافة مستطيل إلى Word، وتضمين عنصر تحكم محتوى نصي عادي،
  كل ذلك باستخدام C#.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: إنشاء مستند Word برمجيًا – تجميع الأشكال في C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: إنشاء مستند Word برمجيًا وتجميع الأشكال في C#
url: /ar/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word برمجياً وتجميع الأشكال في C#

إذا كنت بحاجة إلى **create word document programmatically**، يوضح لك هذا الدليل كيفية بناء ملف DOCX باستخدام Aspose.Words و **group multiple shapes word** معًا. سنغطي أيضًا **add rectangle to word** و **how to create group shape** التي تحتوي على كل من المستطيل والبيضة، بالإضافة إلى StructuredDocumentTag نصي بسيط لإدخال المستخدم.

سوف تحصل في النهاية على ملف Word جاهز للاستخدام يحتوي على شكل مجموعة من المستطيل والبيضة وعنصر تحكم محتوى يمكن للمستخدم كتابة اسمه فيه. لا يلزم أي تعديل يدوي في Word بعد تشغيل الكود.

## ما ستحتاجه

- .NET 6.0 أو أحدث (العينة تستهدف .NET 6، لكن أي نسخة حديثة من .NET تعمل).
- رخصة Aspose.Words for .NET (الإصدار التجريبي المجاني يعمل للاختبار).
- Visual Studio 2022 أو أي بيئة تطوير C# تفضلها.
- إلمام أساسي بصياغة C#.

## إنشاء مستند Word برمجياً – سير العمل العام

تتكون العملية من ثلاث مراحل منطقية:

1. **Initialize** مستند `Document` و `DocumentBuilder` – الأساس لأي ملف Word تقوم بإنشائه.
2. **Build a group shape** التي تحتوي على مستطيل وبيضة – توضح **group multiple shapes word** و **how to create group shape**.
3. **Insert a StructuredDocumentTag (SDT)** – عنصر تحكم محتوى نصي بسيط يتيح للمستخدمين النهائيين ملء البيانات، موضحًا **add rectangle to word** كجزء من تخطيط المستند العام.

فيما يلي الكود الكامل القابل للتنفيذ يليه شرح خطوة بخطوة.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### الخطوة 1 – تهيئة المستند والباني
كائن `Document` يمثل ملف DOCX بالكامل، بينما يوفر `DocumentBuilder` واجهة برمجة تطبيقات مريحة لإضافة المحتوى. تهيئتهما هي المتطلب الأول كلما قمت بـ **create word document programmatically**.

> **نصيحة احترافية:** إذا كنت تخطط لإعادة استخدام نفس المستند عبر عمليات متعددة، احتفظ بنسخة واحدة من `DocumentBuilder` لتجنب إنشاء كائنات غير ضرورية.

### الخطوة 2 – إنشاء حاوية مجموعة الأشكال
`Shape` مع `ShapeType.Group` يعمل كقماش يمكنه احتواء أشكال أخرى. ضبط `Width` و `Height` يحدد الصندوق المحيط للمجموعة. هذا هو جوهر **how to create group shape** في Aspose.Words.

> **حالة حدية:** إذا كان عرض المجموعة أصغر من العرض المجموع لأطفالها، سيتم قطع الأطفال. احرص دائمًا على جعل المجموعة كبيرة بما يكفي لاحتواء كل شكل طفل.

### الخطوة 3 – إضافة مستطيل إلى Word
يتم إنشاء مستطيل باستخدام `ShapeType.Rectangle`. تحدد خصائص `Left` و `Top` موقعه بالنسبة لأصل المجموعة. تُظهر هذه الخطوة **add rectangle to word** وتوضح كيف يمكنك التحكم في الموضع الدقيق.

> **خطأ شائع:** نسيان ضبط `Left`/`Top` يؤدي إلى ظهور المستطيل عند أصل المجموعة الافتراضي (0,0)، مما قد يتداخل مع أشكال أخرى.

### الخطوة 4 – إضافة بيضة (دائرة) إلى المجموعة
يتم إضافة بيضة بنفس طريقة المستطيل، ولكن باستخدام `ShapeType.Ellipse`. القيمة `Left = 210` تحركها إلى يمين المستطيل، مكونة زوجًا من الأشكال المميزة بصريًا داخل نفس المجموعة.

> **لماذا نستخدم مجموعة؟** التجميع يتيح لك نقل أو تدوير أو تغيير حجم كلا الشكلين معًا بعملية واحدة لاحقًا، مع الحفاظ على تخطيطهما النسبي.

### الخطوة 5 – إدراج مجموعة الأشكال المكتملة في المستند
`builder.InsertNode(groupShape)` يضع المجموعة بالكامل في موقع المؤشر الحالي. لأن المجموعة تحتوي بالفعل على أطفالها، لا تحتاج إلى استدعاءات إدراج إضافية للمستطيل أو البيضة.

### الخطوة 6 – إنشاء StructuredDocumentTag نصي بسيط (SDT)
StructuredDocumentTag هو عنصر تحكم محتوى يمكن للمستخدمين النهائيين ملؤه عند فتح المستند في Word. ضبط `Title = "CustomerName"` يمنح التحكم معرفًا ذا معنى، وهو مفيد لاستخراج البيانات لاحقًا.

> **لماذا SDT نصي بسيط؟** يقتصر الإدخال على نص عادي، مما يمنع التنسيق غير المقصود الذي قد يعيق المعالجة اللاحقة.

### الخطوة 7 – حفظ المستند
`doc.Save("GroupAndSDT.docx")` يكتب الملف إلى القرص. يحتوي ملف DOCX الناتج على الأشكال المجمعة وSDT. عند فتح الملف في Microsoft Word سيظهر مستطيل بجانب دائرة، كلاهما قابل للتحديد ككائن واحد، يليه عنصر نائب “Enter name here …”.

#### النتيجة المتوقعة
- ملف باسم **GroupAndSDT.docx** في مجلد التنفيذ.
- في Word: مجموعة أشكال (مستطيل + بيضة) يمكنك نقلها كوحدة واحدة.
- مباشرة أسفل المجموعة، عنصر تحكم محتوى مظلل بالرمادي يطلب من المستخدم كتابة اسم.

## تنويعات إضافية وأفضل الممارسات

### استخدام أنواع أشكال مختلفة
يمكنك استبدال `ShapeType.Rectangle` أو `ShapeType.Ellipse` بأي `ShapeType` آخر (مثلًا `ShapeType.Polygon`، `ShapeType.Line`). يظل منطق التجميع كما هو.

### ضبط لون التعبئة والحدود
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
إضافة تعبئة وخط يحسن التمييز البصري، خاصة عندما يتم مشاركة المستند مع أصحاب المصلحة غير التقنيين.

### تدوير المجموعة بأكملها
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
تدوير المجموعة أكثر كفاءة من تدوير كل عنصر على حدة.

### التصدير إلى PDF
إذا كنت بحاجة إلى نسخة PDF، فقط استدعِ:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
ستظهر جميع الأشكال المجمعة وSDT (المعروض كحقل نص) في ملف PDF.

## الأخطاء الشائعة وكيفية تجنبها

| العَرَض | السبب | الحل |
|---------|-------|------|

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشروعاتك.

- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [إنشاء مستند Word فارغ مع شكل مستطيل مظلل – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}