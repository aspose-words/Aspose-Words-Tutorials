---
category: general
date: 2026-08-04
description: احفظ ملف docx برمجيًا مع إضافة شكل مستطيل وتجميع الأشكال في Word. تعلم
  كيفية ضبط أبعاد الشكل وإنشاء مربع نص برمجيًا.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: ar
lastmod: 2026-08-04
og_description: حفظ ملف docx باستخدام C# عن طريق إضافة شكل مستطيل، تجميع الأشكال في Word،
  ضبط أبعاد الشكل، وإنشاء مربع نص برمجيًا.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: حفظ ملف docx مع أشكال مجمعة في Word – دليل خطوة‑بخطوة بلغة C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: حفظ ملف docx مع الأشكال المجمعة في Word باستخدام C#
url: /ar/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ ملف docx مع أشكال مجمعة في Word باستخدام C#

إذا كنت بحاجة إلى **حفظ ملف docx** يحتوي على عدة أشكال مرتبة معًا، يوضح لك هذا الدليل كيفية القيام بذلك باستخدام C#. ستتعلم كيفية **إضافة شكل مستطيل**، تجميع أشكال متعددة في مستند Word، **تحديد أبعاد الشكل**، و**إنشاء مربع نص برمجيًا**. يعمل الحل مع أحدث نسخة من Aspose.Words for .NET ويعمل على .NET 6 أو أحدث.

يتبع البرنامج التعليمي كل خطوة، من إعداد المشروع إلى استدعاء `doc.Save` النهائي. في النهاية ستحصل على مقطع شفرة قابل لإعادة الاستخدام يمكنك لصقه في أي مشروع Console أو ASP.NET. لا تحتاج إلى أي سكريبتات خارجية أو تعديل يدوي لملف DOCX.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من توفر ما يلي:

* .NET 6 SDK (أو أحدث) مثبت.
* ترخيص صالح لـ **Aspose.Words for .NET** (الإصدار التجريبي المجاني يكفي للاختبار).
* Visual Studio 2022، VS Code، أو أي بيئة تطوير متكاملة يمكنها بناء مشاريع .NET.

تستخدم الشفرة مساحة الاسم Aspose.Words فقط، لذا لا توجد حزم NuGet إضافية مطلوبة.

## حفظ ملف docx مع أشكال مجمعة في Word

جوهر الحل هو إنشاء `GroupShape` يحتوي على مستطيل ومربع نص، ثم إدراج المجموعة في المستند واستدعاء `doc.Save`. الأقسام التالية تقسم العملية إلى أجزاء يمكن إدارتها.

### 1. إنشاء مستند جديد وBuilder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*لماذا هذه الخطوة مهمة* – كائن `Document` الجديد يمثل ملف *.docx* فارغ. يوفر `DocumentBuilder` طرقًا عالية المستوى مثل `InsertNode`، والتي سنستخدمها لوضع شكل المجموعة.

### 2. إضافة شكل مستطيل إلى مجموعة

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*لماذا هذه الخطوة مهمة* – عملية **إضافة شكل مستطيل** توضح كيفية تعريف عنصر بصري بحجم وموقع محددين بدقة. يعيش المستطيل داخل `group`، لذا تحريك المجموعة لاحقًا يحرك المستطيل تلقائيًا.

### 3. تجميع الأشكال في مستند Word

فئة `GroupShape` تجمع عدة كائنات رسمية. التجميع مفيد عندما تريد التعامل مع عدة كائنات كوحدة واحدة (مثل التحريك، الدوران، أو النسخ معًا).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*لماذا نجمع* – يقلل التجميع من تعقيد التخطيط. بدلاً من تحديد موضع كل شكل على حدة في الصفحة، يمكنك تعديل `Left` و`Top` و`Width` و`Height` للمجموعة مرة واحدة.

### 4. تحديد أبعاد الشكل لتخطيط دقيق

كلا من المجموعة والأشكال الفرعية تحتاج إلى أبعاد صريحة؛ وإلا سيطبق Word أحجامًا افتراضية قد لا تتطابق مع التصميم الخاص بك.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*لماذا نحدد الأبعاد* – القياس الدقيق يضمن أن المستطيل ومربع النص لا يتداخلان بشكل غير مقصود، وأن عملية **حفظ ملف docx** النهائية تتطابق مع التخطيط المقصود.

### 5. إنشاء مربع نص برمجيًا داخل المجموعة

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*لماذا هذه الخطوة مهمة* – يوضح قسم **إنشاء مربع نص برمجيًا** كيفية تضمين نص غني داخل شكل. باستخدام `Paragraph` و`Run` تحصل على تحكم كامل في التنسيق لاحقًا.

### 6. إدراج شكل المجموعة و**حفظ ملف docx**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*لماذا هذه الخطوة النهائية مهمة* – استدعاء `InsertNode` يضع الأشكال المجمعة بالضبط حيث يوجد مؤشر الـ builder. طريقة `doc.Save` تنفذ عملية **حفظ ملف docx**، وتكتب مستند Word كامل المميزات إلى القرص.

> **النتيجة:** عند فتح *GroupShape.docx* في Microsoft Word يظهر مستطيل على اليسار ومربع نص على اليمين، كلاهما مقفل معًا داخل مجموعة واحدة. يمكنك تحريك المجموعة كوحدة، تغيير حجمها، أو تطبيق تنسيقات إضافية.

## مثال كامل قابل للتنفيذ

انسخ الشفرة أدناه إلى مشروع Console جديد (`dotnet new console`) وشغّل `dotnet run`. سيقوم البرنامج بإنشاء `GroupShape.docx` في مجلد الإخراج الخاص بالمشروع.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### المخرجات المتوقعة

* يظهر ملف باسم **GroupShape.docx** في دليل الإخراج.
* عند فتح الملف يظهر شكل مستطيل على اليسار ومربع نص يحتوي على النص “Grouped text” على اليمين، كلاهما مقفل معًا.
* اختيار أي من الشكلين يحرك المجموعة بالكامل، مما يؤكد أن وظيفة **group shapes word** تعمل كما هو متوقع.

## الاختلافات الشائعة وحالات الحافة

| الحالة | التوصية |
|-----------|----------------|
| الحاجة إلى أكثر من شكلين | أضف كائنات `Shape` إضافية إلى `group` قبل استدعاء `builder.InsertNode`. |
| رغبة ظهور المجموعة في صفحة محددة | حرّك مؤشر الـ builder باستخدام `builder.MoveToDocumentEnd()` أو `builder.MoveToPage(pageNumber)`. |
| الحاجة إلى وحدات مختلفة (مثل السنتيمترات) | استخدم `ConvertUtil.InchToPoint(1.0)` لتحويل الإنش إلى نقاط، الوحدة التي يتوقعها Word. |
| رغبة جعل مربع النص يلتف حول النص | عيّن `textBox.TextBoxWrap = TextBoxWrapType.Square` بعد إنشاء مربع النص. |
| العمل مع إصدارات أقدم من .NET Framework | نفس الـ API يعمل مع .NET Framework 4.7+، لكن تأكد من الإشارة إلى نسخة Aspose.Words الصحيحة. |

**نصيحة محترف:** دائمًا عيّن `Width` و`Height` للمجموعة *بعد* إضافة جميع الأشكال الفرعية. يضمن ذلك أن تغطي المجموعة محتوياتها بالكامل، مما يمنع القص عند فتح المستند في Word.

## الخلاصة

أنت الآن تعرف كيف **تحفظ ملف docx** مع **إضافة شكل مستطيل**، **تجميع الأشكال في Word**، **تحديد أبعاد الشكل**، و**إنشاء مربع نص برمجيًا** باستخدام Aspose.Words for .NET. يوضح المثال الكامل نمطًا نظيفًا وقابلًا لإعادة الاستخدام يمكنك تعديله لتصاميم أكثر تعقيدًا، مثل المخططات والصور.

## ماذا يجب أن تتعلم بعد ذلك؟

تغطي الدروس التالية مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}