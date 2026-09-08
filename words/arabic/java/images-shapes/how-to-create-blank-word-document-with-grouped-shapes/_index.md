---
category: general
date: 2026-09-08
description: تعلم كيفية إنشاء مستند Word فارغ، وإدراج شكل مستطيل، وتجميع أشكال متعددة
  باستخدام C#. اتبع هذا الدليل خطوة بخطوة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: ar
lastmod: 2026-09-08
og_description: إنشاء مستند Word فارغ، وإدراج شكل مستطيل وتجميع عدة أشكال في C#. يشرح
  هذا الدليل العملية بالكامل.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: إنشاء مستند Word فارغ مع أشكال مجمعة في C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: كيفية إنشاء مستند Word فارغ مع أشكال مجمعة
url: /ar/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word فارغ مع أشكال مجمعة

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** يحتوي على رسومات مخصصة، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. ستتعلم **إدراج شكل مستطيل**، **تجميع أشكال متعددة**، و**إضافة أشكال إلى المجموعة** باستخدام Aspose.Words for .NET.

المستند الفارغ يمنحك لوحة رسم نظيفة، وتسمح لك تجميع الأشكال بتحريكها أو تغيير حجمها أو تدويرها كوحدة واحدة. يغطي هذا البرنامج التعليمي كل خطوة—من تهيئة المستند إلى حفظ الملف النهائي—حتى تتمكن من نسخ الشيفرة إلى مشروعك الخاص ورؤية النتائج فورًا.

## ما ستحتاجه

* .NET 6.0 أو أحدث (الشيفرة تعمل أيضًا مع .NET Framework 4.6+)
* رخصة صالحة لـ Aspose.Words for .NET (التقييم المجاني يعمل للاختبار)
* بيئة تطوير متكاملة مثل Visual Studio 2022 أو Visual Studio Code
* إلمام أساسي بصياغة C#

## كيفية إنشاء مستند Word فارغ

الخطوة الأولى هي إنشاء كائن `Document`. هذا الكائن يمثل ملف `.docx` فارغ يمكنك تحريره باستخدام `DocumentBuilder`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

منشئ `Document` ينشئ **مستند Word فارغ** في الذاكرة. يوفر `DocumentBuilder` واجهة برمجة تطبيقات سلسة لإدراج النصوص والصور والكائنات الرسومية.

## إدراج شكل مستطيل في المستند

بعد ذلك، أضف شكل مستطيل. سيكون المستطيل هو الطفل الأول للمجموعة التي سننشئها لاحقًا.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

استدعاء `InsertShape` مع `ShapeType.Rectangle` **يدرج شكل مستطيل** في موضع المؤشر الحالي. العرض والارتفاع يُعبَّران بالنقاط (1 pt ≈ 1/72 in).

## تجميع أشكال متعددة معًا

`GroupShape` يعمل كحاوية. جميع الأشكال الفرعية داخل المجموعة تتحرك وتتحول معًا. أولاً، أنشئ المجموعة، ثم أضف المستطيل الذي أنشأناه للتو.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

طريقة `InsertGroupShape` تضع مجموعة فارغة عند مؤشر الـ builder. من خلال إلحاق المستطيل، نحن **نجمع أشكالًا متعددة**—يصبح المستطيل جزءًا من مجموعة العقد الداخلية للمجموعة.

## إضافة أشكال إلى المجموعة وحفظ الملف

الآن أضف شكلًا ثانيًا—بيضاويًا—لتوضيح كيفية مشاركة كائنات متعددة لنفس الحاوية. بعد ذلك، احفظ المستند.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

استدعاء `InsertShape` **يضيف أشكالًا إلى المجموعة** عندما تلحق الـ `Shape` المرجعة إلى الـ `GroupShape`. حفظ الـ `Document` يكتب ملف `.docx` يمكنك فتحه في Microsoft Word أو LibreOffice أو أي عارض متوافق.

### النتيجة المتوقعة

عند فتح *GroupShapeDemo.docx*، سترى صفحة فارغة تحتوي على كائن مجمع يضم مستطيلًا أزرق فاتحًا وبيضاويًا ورديًا. اختيار المجموعة يتيح لك تحريك الشكلين معًا، مما يؤكد أن **تجميع أشكال متعددة** قد عمل كما هو مقصود.

## لماذا تستخدم GroupShape؟

* **تحويلات ذرية** – تعديل الحجم، أو الدوران، أو تحريك المجموعة يؤثر على جميع الأطفال بشكل موحد.
* **تنظيم منطقي** – يحافظ على الرسومات المرتبطة معًا، مما يجعل بنية المستند أسهل في الصيانة.
* **الأداء** – عرض حاوية واحدة غالبًا ما يكون أسرع من معالجة العديد من الأشكال المستقلة.

إذا كنت بحاجة لتعديل أحد الأطفال لاحقًا، يمكنك استرجاعه من `group.ChildNodes` باستخدام الفهرس أو باستخدام خاصية `Name` الخاصة به.

## الاختلافات الشائعة وحالات الحافة

| السيناريو                                 | كيفية تعديل الشيفرة                                                            |
|------------------------------------------|----------------------------------------------------------------------------------|
| **أنواع أشكال مختلفة**                | استبدل `ShapeType.Rectangle` أو `ShapeType.Ellipse` بأي `ShapeType` آخر |
| **إضافة نص داخل شكل**           | استخدم `Shape.TextPath.Text = "Hello"` بعد إدراج الشكل                    |
| **تحديد زاوية الدوران**             | `group.Rotation = 45;` (درجة)                                                 |
| **حفظ كملف PDF بدلاً من DOCX**        | `doc.Save("GroupShapeDemo.pdf");`                                                |
| **تطبيق حد على المجموعة**       | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`               |

## نصائح احترافية

* **قم بتسمية الأشكال** – `rectangle.Name = "MyRect";` يجعل من السهل العثور عليها لاحقًا.
* **استخدم التموضع النسبي** – اضبط `group.RelativeHorizontalPosition` إلى `RelativeHorizontalPosition.Page` إذا كنت تريد أن تبقى المجموعة مثبتة على هوامش الصفحة.
* **تحرير الموارد** – ضع الـ `Document` داخل كتلة `using` عند العمل في تطبيقات أكبر لتحرير الذاكرة غير المُدارة بسرعة.

## الشيفرة المصدرية الكاملة للنسخ السريع

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

انسخ الشيفرة إلى مشروع وحدة تحكم جديد، استعد حزمة NuGet `Aspose.Words`، ثم شغّل. يظهر ملف الإخراج في مجلد المشروع `bin/Debug/net6.0` (أو ما يعادله).

## الخطوات التالية

الآن بعد أن أصبحت قادرًا على **إنشاء مستند Word فارغ**، **إدراج شكل مستطيل**، و**تجميع أشكال متعددة**، قد ترغب في استكشاف:

* إضافة **صناديق نصية** داخل مجموعة لإنشاء مخططات معنونة.
* تصدير الرسم المجمّع إلى صورة باستخدام `doc.Save("image.png", SaveFormat.Png)`.
* دمج المجموعات مع الجداول لإنشاء تقارير ذات تنسيق غني.

جرّب خصائص أشكال مختلفة، هياكل المجموعات، وصيغ التصدير للاستفادة الكاملة من قدرات الرسم في Aspose.Words.

--- 

*تذكّر*: تجميع الأشكال طريقة قوية للحفاظ على تنظيم مستندات Word وكودك قابل للصيانة. برمجة سعيدة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [إدراج أشكال في مستندات Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}