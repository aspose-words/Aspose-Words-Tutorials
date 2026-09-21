---
category: general
date: 2026-09-21
description: إنشاء مستند Word فارغ باستخدام Aspose.Words، ضبط حجم الشكل، ضبط موضع
  الشكل، ضبط لون الشكل، وحفظ ملف docx في خطوة واحدة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: ar
lastmod: 2026-09-21
og_description: إنشاء مستند Word فارغ، ضبط حجم الشكل، ضبط موضع الشكل، ضبط لون الشكل،
  وحفظ ملف docx باستخدام Aspose.Words في دقائق.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: إنشاء مستند Word فارغ وإضافة أشكال ملونة – دليل Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: إنشاء مستند Word فارغ وإضافة أشكال ملونة باستخدام Aspose.Words
url: /ar/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ وإضافة أشكال ملونة باستخدام Aspose.Words

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** برمجيًا، يوضح لك هذا الدليل كيفية القيام بذلك باستخدام Aspose.Words. ستتعلم كيفية **تحديد حجم الشكل**، **تحديد موضع الشكل**، **تحديد لون الشكل**، وأخيرًا **حفظ ملف docx** دون مغادرة بيئة التطوير المتكاملة الخاصة بك.

العمل مع ملفات Word في C# غالبًا ما يعني التعامل مع استدعاءات OpenXML منخفضة المستوى، لكن Aspose.Words يبسط التعقيد. بنهاية هذا الدرس ستحصل على ملف `.docx` كامل الوظيفة يحتوي على شكل مجموعة مكوّن من مستطيلين ملونين—مثالي للتقارير، الشهادات، أو القوالب المخصصة.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)
- Aspose.Words for .NET 23.9 أو أحدث (التثبيت عبر NuGet: `Install-Package Aspose.Words`)
- إلمام أساسي بـ C# و Visual Studio (أو أي محرر C#)

لا يلزم وجود ملف Word مسبقًا؛ يبدأ الدرس بـ **إنشاء مستند Word فارغ** من الصفر.

## إنشاء مستند Word فارغ باستخدام Aspose.Words

الخطوة الأولى هي إنشاء كائن `Document`. هذا الكائن يمثل ملف Word فارغ في الذاكرة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` يبدأ فارغًا، وهو بالضبط ما تحتاجه عندما **تنشئ مستند Word فارغ**. سيتم لاحقًا استخدام `builder` لإدراج مجموعة الأشكال في موقع المؤشر الحالي.

## تحديد حجم الشكل وإنشاء GroupShape

`GroupShape` يعمل كحاوية يمكنها احتواء عدة أشكال فردية. أولاً، حدد الأبعاد العامة للحاوية.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

هنا نقوم **بتحديد حجم الشكل** للمجموعة نفسها (300 × 200). تُستخدم نفس أسماء الخصائص (`Width`, `Height`) لكل شكل فرعي، مما يمنحك تحكمًا دقيقًا في كل عنصر.

## إضافة المستطيل الأول وتحديد لون الشكل

الآن أضف مستطيلًا إلى المجموعة ومنحه لون خلفية.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

خاصية `FillColor` **تحدد لون الشكل**. استخدام `System.Drawing.Color` يتيح لك اختيار أي قيمة ARGB معرفة مسبقًا أو مخصصة.

## إضافة مستطيل ثانٍ، وتحديد حجمه، موضعه، ولونه

المستطيل الثاني يوضح كيفية **تحديد موضع الشكل** بالنسبة للمجموعة وكيفية تغيير لونه.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

نظرًا لأن عرض المجموعة هو 300 نقطة، فإن المستطيلين بحجم 120 نقطة يتناسبان بشكل مريح مع فجوة 30 نقطة. عدّل `Left` و `Top` إذا كنت بحاجة إلى تخطيط مختلف.

## إدراج GroupShape في المستند

بعد تكوين المجموعة بالكامل، ضعها في موقع المؤشر الحالي.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` يكتب الشكل مباشرةً في جسم المستند، محافظًا على **موضع الشكل المحدد** الذي حددته مسبقًا.

## حفظ ملف docx

الخطوة الأخيرة هي حفظ المستند على القرص. هذا يوضح عملية **حفظ ملف docx**.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

بعد تشغيل البرنامج، افتح `GroupShape.docx` في Microsoft Word. يجب أن ترى صفحة فارغة تحتوي على شكل مجموعة يضم مستطيلين ملونين موضعين جنبًا إلى جنب.

### النتيجة المتوقعة

- ملف `.docx` بصفحة واحدة.
- الصفحة تحتوي على مجموعة أشكال تقع على بعد 100 نقطة من الهوامش اليسرى والعليا.
- داخل المجموعة، مستطيل أزرق فاتح على اليسار، ومستطيل مرجاني فاتح على اليمين، كل منهما بحجم 120 × 80 نقطة.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه في تطبيق وحدة تحكم. لا تحتاج إلى ملفات إضافية.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

تشغيل هذا البرنامج ينشئ المستند الدقيق الموضح سابقًا، محققًا جميع الأهداف الأربعة: **إنشاء مستند Word فارغ**، **تحديد حجم الشكل**، **تحديد موضع الشكل**، **تحديد لون الشكل**، و**حفظ ملف docx**.

## الاختلافات الشائعة وحالات الحافة

| السيناريو | ما الذي يجب تغييره | لماذا يهم |
|----------|-------------------|-----------|
| **أنواع أشكال مختلفة** | استبدل `ShapeType.Rectangle` بـ `ShapeType.Ellipse`، `ShapeType.Triangle`، إلخ. | يسمح لك بإنشاء رسومات أكثر تعقيدًا دون الحاجة إلى صور خارجية. |
| **أبعاد ديناميكية** | احسب `Width` و `Height` من مدخلات المستخدم أو ملفات الإعداد. | يجعل الحل قابلًا لإعادة الاستخدام عبر قوالب مستندات متعددة. |
| **الحفظ كملف PDF** | استدعِ `document.Save("output.pdf", SaveFormat.Pdf);` | إذا كان المستلمون يحتاجون إلى تنسيق غير قابل للتحرير، فإن PDF خيار آمن. |
| **إضافة نص داخل الشكل** | أنشئ شكل `TextBox` واضبط `TextBox.Text`. | مفيد لإنشاء شارات أو توضيحات معنونة. |
| **مجموعات متعددة في صفحة واحدة** | كرر الخطوات 2‑5 باستخدام قيم `Left`/`Top` مختلفة. | يمكنك من بناء لوحات معلومات أو تخطيطات متعددة الأقسام. |

### نصيحة احترافية

عندما تحتاج إلى محاذاة الأشكال بدقة، استخدم الخاصية `ShapeBase.WrapType = WrapType.Inline` قبل إدراج المجموعة. هذا يجبر المجموعة على التصرف كفقرة، مما يمنع تدفق النص غير المتوقع حولها.

## الخلاصة

أنت الآن تعرف كيفية **إنشاء مستند Word فارغ** باستخدام Aspose.Words، **تحديد حجم الشكل**، **تحديد موضع الشكل**، **تحديد لون الشكل**، و**حفظ ملف docx**. المثال الكامل يوضح نمطًا نظيفًا وقابلًا لإعادة الاستخدام لإضافة رسومات مجموعة إلى أي مشروع أتمتة Word.

من هنا يمكنك استكشاف:
- إضافة المزيد من الأشكال أو الصور إلى نفس `GroupShape` (تغييرات **تحديد حجم الشكل**، **تحديد لون الشكل**).
- استخدام `ShapeBase.Rotation` لتدوير المستطيلات لتأثيرات زخرفية.
- تصدير نفس المستند كملف PDF أو HTML لتوسيع نطاق التوزيع (بديل **حفظ ملف docx**).

لا تتردد في تجربة ألوان وأحجام ومنطق تخطيط مختلف لتلبية احتياجاتك الخاصة بالتقارير أو القوالب. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words لـ .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [دروس ظل الشكل في Aspose.Words – إضافة ظل إلى شكل Word في C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}