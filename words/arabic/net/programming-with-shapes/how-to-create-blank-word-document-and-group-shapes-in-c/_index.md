---
category: general
date: 2026-10-07
description: إنشاء مستند Word فارغ في C# وتعلم إضافة شكل مستطيل، وإدراج شكل صورة،
  وتجميع عدة أشكال لتقارير ديناميكية.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: ar
lastmod: 2026-10-07
og_description: إنشاء مستند Word فارغ باستخدام C# و Aspose.Words. تعلم كيفية إضافة
  شكل مستطيل، وإدراج شكل صورة، وتجميع عدة أشكال لإنشاء مستندات احترافية.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: إنشاء مستند Word فارغ وتجميع الأشكال في C# – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية إنشاء مستند Word فارغ وتجميع الأشكال في C#
url: /ar/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word فارغ وتجميع الأشكال في C#

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** برمجيًا، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. سترى كيف **تضيف شكل مستطيل**، **تدرج شكل صورة**، و**تجمع عدة أشكال** بحيث تتصرف ككائن واحد عندما **تضيف صورة إلى Word** لاحقًا.

العمل مع ملفات Word من خلال الكود قد يبدو مخيفًا، لكن Aspose.Words يجعل العملية مباشرة. في نهاية هذا الدرس ستحصل على مقتطف C# قابل لإعادة الاستخدام يولد ملف Word نظيف وفارغ يحتوي على مستطيل وم logo مجمّعين. يمكنك دمج النتيجة في الفواتير، التقارير، أو أي سير عمل مستندات آلي.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+).  
* رخصة صالحة لـ Aspose.Words for .NET أو مفتاح تقييم مجاني.  
* ملف صورة (مثل `logo.png`) موجود في مجلد يمكنك الإشارة إليه من الكود.  
* Visual Studio 2022 أو أي بيئة تطوير متوافقة مع C#.

لا توجد حزم NuGet إضافية مطلوبة بخلاف `Aspose.Words`.

## كيفية إنشاء مستند Word فارغ باستخدام Aspose.Words

الخطوة الأولى دائمًا هي **إنشاء مستند Word فارغ**. هذا الكائن سيستضيف جميع الأشكال اللاحقة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` يمثل ملف `.docx` بالكامل. في هذه المرحلة يكون الملف فارغًا، مما يحقق متطلب *إنشاء مستند Word فارغ*.

## إنشاء حاوية لتجميع عدة أشكال

تجميع الأشكال يتيح لك نقلها أو تدويرها أو تغيير حجمها معًا. Aspose.Words توفر الفئة `GroupShape` لهذا الغرض.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

مستطيل `Bounds` يحدد مكان ظهور المجموعة على الصفحة. بوضع المجموعة في الفقرة الأولى تضمن أن **إنشاء مستند Word فارغ** سيحتوي فورًا على حاوية بصرية.

## كيفية إضافة شكل مستطيل داخل المجموعة

متطلب شائع هو **إضافة شكل مستطيل** كخلفية أو حد. الكود التالي ينشئ مستطيلًا ويضيفه إلى المجموعة المعرفة مسبقًا.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

نظرًا لأن المستطيل يعيش داخل `GroupShape`، سيتحرك مع أي أشكال أخرى تضيفها لاحقًا. هذا هو جوهر وظيفة **تجميع عدة أشكال**.

## كيفية إدراج شكل صورة داخل المجموعة

بعد ذلك، ستقوم **بإدراج شكل صورة** (الشعار) وتضعه بجانب المستطيل. هذا يوضح سير عمل **إضافة صورة إلى Word**.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

طريقة `SetImage` تقرأ الملف وتدمجه مباشرةً في مستند Word، مما يضمن بقاء الصورة حتى إذا تم نقل ملف المصدر. هذا يكمل خطوة **إدراج شكل صورة** ويحقق متطلب **إضافة صورة إلى Word**.

## حفظ المستند

أخيرًا، احفظ الملف على القرص. الملف المحفوظ يحتوي على المستند الفارغ، المستطيل المجمّع، والشعار المدمج.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

عند فتح `GroupShape.docx` في Microsoft Word، سترى مجموعة واحدة تشمل مستطيل رمادي فاتح والشعار موضعين جنبًا إلى جنب. اختيار أي جزء من المجموعة يتيح لك نقل أو تغيير حجم المجموعة بالكامل، مما يثبت أن الأشكال تم **تجميع عدة أشكال** فعليًا.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه، لصقه، وتشغيله. استبدل `YOUR_DIRECTORY` بمسار مطلق أو نسبي موجود على جهازك.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### النتيجة المتوقعة

* ملف باسم `GroupShape.docx` موجود في `YOUR_DIRECTORY`.  
* فتح الملف في Word يظهر مجموعة بصرية واحدة تحتوي على مستطيل رمادي على اليسار و`logo.png` على اليمين.  
* اختيار أي جزء من المجموعة البصرية يسمح لك بنقل أو تغيير حجم المجموعة بالكامل، مؤكدًا أن الأشكال تم **تجميع عدة أشكال** بشكل صحيح.

## أسئلة شائعة وتعامل مع الحالات الخاصة

| السؤال | الجواب |
|---|---|
| **هل يمكنني إضافة أكثر من شكلين إلى نفس المجموعة؟** | نعم. استدعِ `group.AppendChild(yourShape)` لكل `Shape` إضافي. يمكن للمجموعة احتواء أي عدد من كائنات الرسم. |
| **ماذا لو كان ملف الصورة مفقودًا؟** | `SetImage` سيطرح استثناء `FileNotFoundException`. احكم الاستدعاء داخل كتلة try‑catch وقدم بديلًا (مثل شكل نائب). |
| **هل أحتاج إلى تعيين `WrapType` للأشكال؟** | بشكل افتراضي تكون الأشكال مضمنة داخل النص (inline). إذا كنت تحتاج سلوكًا عائمًا، عيّن `picture.WrapType = WrapType.Inline;` أو وضع تغليف آخر قبل الإضافة إلى المجموعة. |
| **كيف يؤثر حجم المستند على حدود المجموعة؟** | مستطيل `Bounds` يُعرّف بالنقاط (1 pt ≈ 1/72 in). عدّل الحجم إذا وضعت المجموعة على تخطيط صفحة مختلف (مثل A4 مقابل Letter). |
| **هل يمكنني إعادة استخدام نفس المجموعة في مستند آخر؟** | نعم. استنسخ المجموعة باستخدام `GroupShape cloned = (GroupShape)group.Clone(true);` وأدرجها في `Document` مختلف. |

## نصائح احترافية

* **أعد استخدام `DocumentBuilder`** لإضافة نص قبل أو بعد المجموعة. فهو يحترم تلقائيًا موضع المؤشر الحالي.  
* **عيّن `Shape.StrokeColor`** إذا كنت بحاجة إلى حد مرئي حول المستطيل.  
* **استخدم ملفات PNG عالية الدقة** للشعار لتجنب التشويش عند التكبير.

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [إدراج صورة مدمجة في مستند Word باستخدام Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}