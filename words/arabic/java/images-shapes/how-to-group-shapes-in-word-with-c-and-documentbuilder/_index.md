---
category: general
date: 2026-10-04
description: تعلم كيفية تجميع الأشكال في Word باستخدام C#. يوضح هذا الدليل كيفية إدراج
  شكل مستطيل، تجميع عدة أشكال، وإنشاء ملف Word فارغ برمجيًا.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: ar
lastmod: 2026-10-04
og_description: تجميع الأشكال في Word باستخدام C#. اتبع هذا الدليل خطوة بخطوة لإدراج
  شكل مستطيل، وتجميع عدة أشكال، وإنشاء ملف Word فارغ باستخدام DocumentBuilder.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: تجميع الأشكال في Word باستخدام C# – دليل كامل لـ DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: كيفية تجميع الأشكال في Word باستخدام C# و DocumentBuilder
url: /ar/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تجميع الأشكال في Word باستخدام C# و DocumentBuilder

إذا كنت بحاجة إلى **تجميع الأشكال في Word** من تطبيق C#، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. سترى كيفية *إدراج شكل مستطيل*، دمج عدة رسومات في مجموعة واحدة، وأخيرًا **إنشاء ملف Word فارغ** يحتوي على الكائنات المجمعة.

العمل مع الأشكال هو طلب شائع عند إنشاء التقارير أو الفواتير أو القوالب المخصصة برمجيًا. بنهاية هذا الدليل ستحصل على مقتطف كود قابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع .NET ي引用 Aspose.Words.

## ما ستتعلمه

- إنشاء مستند Word فارغ من الصفر.  
- إدراج شكل مستطيل وإهليلج باستخدام `DocumentBuilder`.  
- **تجميع عدة أشكال** في `GroupShape`.  
- استخدام **append child to group** لبناء التسلسل الهرمي.  
- حفظ الملف على القرص والتحقق من النتيجة.

لا يتطلب أي خبرة سابقة مع Aspose.Words، ولكن يجب أن يكون لديك فهم أساسي لـ C# وتطوير .NET.

## المتطلبات المسبقة

| المتطلب | السبب |
|-------------|--------|
| .NET 6.0 أو أحدث | يوفر بيئة التشغيل لكود C#. |
| Aspose.Words for .NET (أحدث نسخة) | يزود بـ `Document`, `DocumentBuilder` وفئات الشكل. |
| بيئة تطوير متكاملة مثل Visual Studio 2022 (أو VS Code) | تجعل من السهل تجميع وتشغيل العينة. |
| صلاحية كتابة إلى مجلد على جهازك | مطلوب لاستدعاء `doc.save`. |

قم بتثبيت Aspose.Words عبر NuGet:

```bash
dotnet add package Aspose.Words
```

---

## تجميع الأشكال في Word – دليل خطوة بخطوة

فيما يلي البرنامج الكامل القابل للتنفيذ. يتم شرح كل قسم بالتفصيل حتى تفهم **لماذا** كُتب الكود بهذه الطريقة، وليس فقط **ماذا** يفعل.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### لماذا كل خطوة مهمة

1. **إنشاء ملف Word فارغ** – البدء بمستند نظيف يضمن عدم تدخل أي تنسيق مخفي في موضع الشكل.  
2. **تهيئة DocumentBuilder** – `DocumentBuilder` يُجرد من معالجة العقد منخفضة المستوى، مما يتيح لك التركيز على التخطيط.  
3. **إدراج أشكال فردية** – تحتاج أولاً إلى كائنات منفصلة (`insert rectangle shape` و إهليلج) قبل أن تتمكن من تجميعها. ضبط `Left` و `Top` يضمن ظهورها جنبًا إلى جنب.  
4. **تجميع عدة أشكال** – بإنشاء `GroupShape` واستخدام **append child to group**، تحول رسمين مستقلين إلى وحدة منطقية واحدة. نقل أو تغيير حجم المجموعة سيؤثر على كلا الطفلين في آن واحد.  
5. **حفظ المستند** – الملف النهائي، `GroupedShapes.docx`، يمكن فتحه في Microsoft Word للتحقق من أن المستطيل والإهليلج مُجَمَّعَان بالفعل (اختر أحدهما، وسيتحرك كلاهما معًا).

### النتيجة المتوقعة

Open `GroupedShapes.docx` in Microsoft Word:

- سترى مستطيلًا وإهليلجًا موضوعة جنبًا إلى جنب.  
- اختيار أي شكل سيُبرز كلاهما، مؤكدًا أنهما ينتميان إلى نفس المجموعة.  
- يمكن سحب المجموعة، تغيير حجمها، أو تنسيقها ككائن واحد.

![مخطط للمستطيل والإهليلج المجمّعين داخل مستند Word](https://example.com/grouped-shapes.png){: .center-image alt="مخطط للمستطيل والإهليلج المجمّعين داخل مستند Word"}

*توضح لقطة الشاشة الأشكال المجمعة النهائية.*

---

## إدراج شكل مستطيل – تخصيص الحجم والنمط

إذا كنت بحاجة إلى مستطيل بلون تعبئة أو حد محدد، عدّل كائن `Shape` بعد الإدراج:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

هذه الخصائص هي جزء من فئة `Shape`، وتعمل لأي نوع من الأشكال، ليس فقط المستطيلات. تعديل النمط قبل **append child to group** يضمن أن المجموعة ترث الخصائص البصرية التي قمت بتعيينها.

---

## تجميع عدة أشكال – التعامل مع أكثر من كائنين

المثال يجمع مستطيلًا وإهليلجًا، لكن يمكنك إضافة أي عدد من الأشكال:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**نصيحة احترافية:** بعد بناء مجموعة معقدة، يمكنك قفل تخطيطها لمنع التغييرات غير المقصودة:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – الترتيب مهم

الترتيب الذي تستدعي فيه `AppendChild` يحدد ترتيب Z (أي الشكل الذي يظهر في الأعلى). في العينة، يُضاف المستطيل أولاً، ثم الإهليلج، لذا يغطى الإهليلج المستطيل إذا تقاطعا. إعادة الترتيب بسيطة كاستدعاء `RemoveChild` وإعادة الإضافة:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## إنشاء ملف Word فارغ – طريقة مساعدة قابلة لإعادة الاستخدام

إذا كان تطبيقك يحتاج بشكل متكرر إلى مستند جديد، قم بتغليف منطق الإنشاء:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

يمكنك بعد ذلك استبدال سطر `new Document()` في البرنامج الرئيسي بـ `CreateBlankWordFile()`. هذا يوضح مفهوم **create blank word file** بطريقة قابلة لإعادة الاستخدام.

---

## المشكلات الشائعة وكيفية تجنبها

| المشكلة | سبب حدوثها | الحل |
|-------|----------------|-----|
| ظهور الأشكال خارج الصفحة | القيم الافتراضية لـ `Left`/`Top` هي 0، مما يضع الشكل عند الهامش. | قم بتعيين `Left` و `Top` صراحةً بعد الإدراج. |
| فقدان تنسيق المجموعة | تغيير شكل طفل بعد إضافته إلى مجموعة قد يكسر تخطيط المجموعة. | تطبيق جميع الخصائص البصرية **قبل** استدعاء `AppendChild`. |
| الملف المحفوظ فارغ | لم يتم استخدام `DocumentBuilder` لإضافة عقدة، أو تم استدعاء `doc.Save` على كائن `Document` مختلف. | تأكد من أنك تحفظ نفس الـ `Document` الذي بنيته. |
| تحذيرات التوافق في Word | Using newer shape features not supported

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words لـ .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إدراج أشكال في مستندات Word باستخدام Aspose.Words لـ .NET](/words/english/net/working-with-shapes/insert-shape/)
- [إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}