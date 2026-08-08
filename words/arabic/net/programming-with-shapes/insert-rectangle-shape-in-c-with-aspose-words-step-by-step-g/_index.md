---
category: general
date: 2026-08-07
description: إدراج شكل مستطيل في C# باستخدام Aspose.Words وتعلم كيفية إخفاء الشكل،
  وتعيين لون التعبئة، وإضافة شكل مستطيل إلى مستند Word بكفاءة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: ar
lastmod: 2026-08-07
og_description: إدراج شكل مستطيل في مستند Word باستخدام C#. تعلم كيفية إخفاء الشكل،
  تعيين لون التعبئة، وإضافة شكل مستطيل باستخدام Aspose.Words.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: إدراج شكل مستطيل في C# – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: إدراج شكل مستطيل في C# باستخدام Aspose.Words – دليل خطوة بخطوة
url: /ar/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج شكل مستطيل في C# باستخدام Aspose.Words – دليل خطوة بخطوة

إذا كنت بحاجة إلى **إدراج شكل مستطيل** في مستند Word من خلال C#، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. ستتعرف على كيفية تعيين لون التعبئة، إخفاء الشكل بحيث لا يظهر في التخطيط النهائي، وحفظ الملف—كل ذلك ببضع أسطر من الشيفرة فقط.

في الأقسام التالية نغطي كل ما تحتاج إلى معرفته: المتطلبات المسبقة، قائمة الشيفرة الكاملة، شرح كل خطوة، ونصائح لتغييرات شائعة مثل إظهار الشكل مرة أخرى أو استخدام لون مختلف. في النهاية ستتمكن من **إضافة شكل مستطيل** إلى أي ملف .docx برمجيًا.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* **Aspose.Words for .NET** (الإصدار 23.10 أو أحدث). يمكنك تثبيته عبر NuGet:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK أو أحدث مثبت على جهازك.
* فهم أساسي للغة C# وVisual Studio (أو أي بيئة تطوير تفضّلها).

لا توجد مكتبات إضافية مطلوبة—واجهات برمجة التطبيقات المتعلقة بالأشكال هي جزء من حزمة Aspose.Words الأساسية.

## إدراج شكل مستطيل باستخدام Aspose.Words

جوهر الحل هو برنامج قصير ومستقل يُنشئ مستندًا فارغًا، يُدرج مستطيلًا، يلوّنه، يخفّيه، ثم يحفظ الملف. أدناه الشيفرة الكاملة مع تعليقات داخلية تشرح *السبب* وراء كل سطر.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### ما تقوم به كل خطوة

| الخطوة | السبب |
|--------|--------|
| **Create a new document** | يوفر لوحة رسم نظيفة؛ يمكنك أيضًا تحميل ملف .docx موجود بتمرير مسار الملف إلى `new Document(path)`. |
| **Initialize DocumentBuilder** | `DocumentBuilder` هو المساعد عالي المستوى الذي يتيح لك إدراج النصوص، الجداول، والأشكال دون التعامل مع شجرة العقد منخفضة المستوى. |
| **Insert rectangle shape** | تُعيد طريقة `InsertShape` كائن `Shape` يمكنك تخصيصه أكثر (الحجم، الموضع، الحدود، إلخ). |
| **Set fill color** | تتحكم خاصية `FillColor` في لون الداخل؛ يمكنك استخدام أي قيمة `Color` (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)`, إلخ). |
| **Hide the shape** | `Hidden = true` يخبر Word بتجاهل الشكل أثناء التخطيط مع بقائه في XML الخاص بالمستند. هذه هي الطريقة القياسية لتخزين الكائنات غير المرئية. |
| **Save the document** | يحفظ التغييرات إلى ملف .docx. سيحتوي الملف المحفوظ على شكل المستطيل المخفي. |

## كيفية تعيين لون التعبئة لشكل

تغيير لون التعبئة بسيط مثل تعيين `System.Drawing.Color` إلى خاصية `FillColor`. إذا كنت تحتاج إلى درجة مخصصة، استخدم `Color.FromArgb`:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*لماذا هذا مهم*: يُخزن لون التعبئة في XML الخاص بالشكل (`<w:fill>`). عندما يكون الشكل مخفيًا، يظل اللون موجودًا، وهو ما يمكن أن يكون مفيدًا لمعالجة لاحقة (مثل استخراج بيانات التعريف بناءً على رموز الألوان).

## كيفية إخفاء الشكل في المستند النهائي

العلم `Hidden` هو خاصية منطقية في فئة `Shape`. ضبطها على `true` يضمن أن يتجاهل محرك تخطيط Word الشكل.

```csharp
rectangleShape.Hidden = true;
```

**أخطاء شائعة**

* **Hidden vs. Visible** – إذا احتجت لاحقًا إلى إظهار الشكل، ما عليك سوى ضبط `Hidden = false`.
* **Compatibility** – قد تتعامل إصدارات Word القديمة (قبل 2007) مع كائنات الرسم المخفية بشكل مختلف. تحافظ Aspose.Words على التوافق بتخزين العلامة في العنصر المناسب من OOXML.

## كيفية إدراج شكل برمجيًا

بينما يستخدم المثال مستطيلًا، تعمل نفس طريقة `InsertShape` مع العديد من الأشكال الأخرى (إهليلج، مثلث، خط، إلخ). الوسيط الأول هو قيمة من تعداد `ShapeType`:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**نصيحة**: إذا كنت بحاجة إلى وضع الشكل في موقع محدد على الصفحة، استخدم `builder.MoveTo` لتعيين نقطة الإدراج قبل استدعاء `InsertShape`.

## إضافة شكل مستطيل إلى مستند موجود

غالبًا ما تقوم بتعزيز قالب بدلاً من البدء من الصفر. استبدل الخطوة 1 بـ:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

جميع الخطوات اللاحقة تبقى كما هي، وسيُضاف المستطيل حيثما يكون مؤشر الـ builder موضعًا (عادةً في نهاية المستند افتراضيًا).

## معالجة الحالات الخاصة والتغييرات

### 1. إظهار الشكل مرة أخرى

إذا احتاج جزء لاحق من سير العمل إلى كشف المستطيل المخفي، يمكنك تبديل العلامة:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. إضافة حد (stroke)

يمكن للشكل المخفي أن يمتلك حدًا مرئيًا عندما تقرر إظهاره. اضبط خاصيتي `LineColor` و `LineWidth`:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. تموضع المستطيل بشكل مطلق

لتحكم دقيق في التخطيط، غيّر `WrapType` الخاص بالشكل إلى `WrapType.Inline` (الافتراضي) أو `WrapType.TopBottom` واضبط خاصيتي `Left`/`Top`:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. استخدام وحدة قياس مختلفة

تعمل Aspose.Words بالنقاط (1 pt = 1/72 inch). إذا كنت تفضّل السنتيمترات، قم بالتحويل أولًا:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج *الكامل* الذي يمكنك نسخه، لصقه، وتشغيله. يتضمن جميع توجيهات `using` الضرورية ويستخدم مسارات مطلقة يجب تعديلها وفق بيئتك.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**النتيجة المتوقعة**: يفتح الملف `HiddenRectangleShape.docx` في Microsoft Word دون أي شكل مرئي، لكن المستطيل المخفي موجود في XML الخاص بالمستند. يمكنك التحقق من وجوده بفتح ملف .docx كأرشيف zip وفحص `word/document.xml` للبحث عن عنصر `<w:shape>` يحتوي على السمتين `w:fill="yellow"` و `w:hidden="true"`.

## الخلاصة

أنت الآن تعرف كيفية **إدراج شكل مستطيل** في مستند Word باستخدام C# وAspose.Words، وكيفية **تعيين لون التعبئة**، وكيفية **إخفاء الشكل** بحيث يبقى غير مرئي في التخطيط النهائي. نفس النمط يعمل مع أنواع أشكال أخرى، ألوان مخصصة، وقوالب موجودة. جرّب إضافة حدود، تموضع مطلق، ووحدات قياس مختلفة لتخصيص الشكل وفق متطلباتك الدقيقة.

### الخطوات التالية

* استكشف **كيفية إدراج شكل** داخل الجداول أو رؤوس/تذييلات الصفحات لإنشاء علامات مائية.
* اجمع **إضافة شكل مستطيل** مع عناصر التحكم بالمحتوى لإنشاء نواقل ديناميكية.
* راجع API **تعديل الأشكال** في Aspose.Words للميزات المتقدمة مثل الدوران، تعبئة التدرج، واستيراد SVG.

لا تتردد في تعديل الشيفرة لتناسب مشروعك، وأخبرنا في التعليقات أي تحدٍ متعلق بالأشكال حلتَه بعد ذلك!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}