---
category: general
date: 2026-09-27
description: إنشاء مستند Word برمجياً باستخدام مجموعة أشكال عبر Aspose.Words في C#.
  اتبع هذا الدليل خطوة بخطوة لإنشاء الملف وتعلم نصائح مفيدة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: ar
lastmod: 2026-09-27
og_description: إنشاء مستند Word برمجياً باستخدام مجموعة أشكال عبر Aspose.Words. يشرح
  هذا الدرس الكود الكامل بلغة C#، يوضح كل خطوة، ويعرض النتيجة النهائية.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: إنشاء مستند Word برمجيًا مع مجموعة أشكال – دليل C#
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: إنشاء مستند Word برمجياً مع مجموعة أشكال
url: /ar/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word برمجيًا مع شكل مجموعة

إذا كنت بحاجة إلى **إنشاء مستند Word برمجيًا** يحتوي على رسم مجموعة، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك باستخدام Aspose.Words for .NET. سواء كنت تبني مولد عقود، أو أداة إنشاء تقارير، أو أداة تعبئة نماذج، ستتعلم الكود الكامل بلغة C#، ولماذا كل استدعاء API مهم، وكيفية التعامل مع الحالات الحدية الشائعة.

إنشاء شكل مجموعة في Word قد يبدو صعبًا لأن نموذج كائنات Word يعامل أشكال المجموعة كحاويات لكائنات رسم أخرى. لا يجيب هذا الدليل فقط على **كيفية إنشاء مستندات Word بشكل مجموعة**، بل يوضح أيضًا كيفية تضمين StructuredDocumentTag (SDT) نص عادي داخل المجموعة بحيث يمكن للشكل احتواء محتوى قابل للتحرير.

## ما ستحققه

- تهيئة مستند Word فارغ جديد باستخدام `Document` و `DocumentBuilder`.
- إدراج `GroupShape` في موضع المؤشر الحالي.
- إضافة `StructuredDocumentTag` نص عادي (SDT) إلى شكل المجموعة.
- حفظ الملف كملف `.docx` يمكن فتحه في Microsoft Word.
- فهم الخصائص الرئيسية لـ `GroupShape` و `StructuredDocumentTag` للتوسعات المستقبلية.

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+).
- حزمة NuGet لـ Aspose.Words for .NET (`Install-Package Aspose.Words`).
- بيئة تطوير C# مثل Visual Studio 2022 أو VS Code مع امتداد C#.

---

## إنشاء مستند Word برمجيًا – إعداد المشروع

1. **إنشاء مشروع وحدة تحكم جديد**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **فتح المشروع في بيئة التطوير الخاصة بك** واستبدال محتوى `Program.cs` بالكود المعروض في الأقسام التالية.

> **نصيحة احترافية:** حافظ على نظافة مجلد المشروع؛ تقوم Aspose.Words بكتابة ملف الإخراج إلى دليل العمل ما لم تقم بتوفير مسار مطلق.

## الخطوة 1: تهيئة المستند والباني

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**لماذا هذا مهم:**  
`Document` يمثل ملف Word بالكامل، بينما `DocumentBuilder` يتيح لك وضع العناصر الجديدة دون الحاجة إلى التنقل يدويًا في شجرة العقد. ضبط أبعاد الصفحة مبكرًا يضمن أن شكل المجموعة لا يتجاوز حدود الصفحة.

## الخطوة 2: إدراج GroupShape في موقع المؤشر الحالي

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**شرح:**  
`GroupShape` هو كائن رسم يمكنه احتواء أشكال أخرى أو صور أو مربعات نص. من خلال ضبط `Width` و `Height` و `Left` و `Top`، تتحكم في موضعه الدقيق على الصفحة. طريقة `InsertNode` تضع الشكل في تدفق المستند الرئيسي، وتعمل ككائن عائم.

## الخطوة 3: إضافة StructuredDocumentTag (SDT) نص عادي داخل المجموعة

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**لماذا نستخدم SDT؟**  
StructuredDocumentTags هي عناصر تحكم المحتوى الأصلية في Word. تسمح للمستخدمين بتحرير النص مباشرةً في المستند المحفوظ، ويمكن الوصول إليها برمجيًا لاحقًا لاستخراج البيانات. وضع SDT داخل شكل مجموعة يتيح لك دمج التجميع البصري مع محتوى قابل للتحرير.

## الخطوة 4: حفظ المستند

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**النتيجة:**  
فتح `GroupShapeDemo.docx` في Microsoft Word يظهر مستطيلًا عائمًا (شكل المجموعة) يحتوي على عنصر نائب نصي يقرأ “Enter text here”. يمكن للمستخدمين النقر داخل الشكل والكتابة مباشرة.

### لقطة شاشة للنتيجة المتوقعة (تصورية)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

الصندوق الخارجي هو `GroupShape`؛ المنطقة الرمادية الداخلية هي `StructuredDocumentTag`.

## كيفية إنشاء شكل مجموعة في Word – اعتبارات إضافية

### إضافة المزيد من الأشكال الفرعية

يمكنك إثراء المجموعة بإضافة كائنات رسم إضافية، مثل الصور أو مربعات النص:

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### التحكم في نمط الالتفاف

إذا كنت بحاجة إلى أن يبقى شكل المجموعة خلف النص أو أن يكون له التفاف محكم، قم بتعيين خاصية `WrapType`:

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### حالة حدية: شكل مجموعة فارغ

`GroupShape` بدون أطفال يُظهر كعنصر نائب غير مرئي. تأكد دائمًا من إضافة طفل واحد على الأقل (مثل SDT أو صورة)؛ وإلا قد يتجاهل Word المجموعة أثناء الحفظ.

### ملاحظة حول التوافق

Aspose.Words 23.10+ يدعم بالكامل `GroupShape` و `StructuredDocumentTag`. إذا كنت تستهدف إصدارات أقدم، قد تتصرف طريقة `AppendChild` بشكل مختلف، وقد تحتاج إلى استدعاء `UpdatePageLayout` بعد الحفظ.

## مثال كامل قابل للتنفيذ

انسخ المقتطف الكامل أدناه إلى `Program.cs` وشغّل المشروع. يتضمن الكود جميع الخطوات السابقة في برنامج واحد مكتمل.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.PageSetup.PageWidth = 595;
        builder.PageSetup.PageHeight = 842;

        // 2️⃣ Create and insert a GroupShape.
        GroupShape groupShape = new GroupShape(doc)
        {
            Width = 300,
            Height = 150,
            Left = 100,
            Top = 100
        };
        builder.InsertNode(groupShape);

        // 3️⃣ Add a plain‑text StructuredDocumentTag (SDT) inside the group.
        StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
        {
            Title = "GroupShapeText",
            PlaceholderName = "Enter text here"
        };
        groupShape.AppendChild(sdtTag);

        // 4️⃣ Optional: add a picture to demonstrate multiple children.
        // Uncomment and adjust the path if you want to test this.
        /*
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            ImageData = ImageData.FromFile("logo.png"),
            Width = 100,
            Height = 50,
            Left


## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [إنشاء مستند Word فارغ باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}