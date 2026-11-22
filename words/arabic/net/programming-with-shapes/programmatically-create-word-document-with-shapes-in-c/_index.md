---
category: general
date: 2026-11-22
description: إنشاء مستند Word برمجياً باستخدام C# وإدراج شكل مستطيل، وإدراج أشكال
  متعددة، وكتابة الأشكال إلى Word باستخدام Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: ar
lastmod: 2026-11-22
og_description: إنشاء مستند Word برمجياً باستخدام C# عن طريق إدراج شكل مستطيل، وإدراج
  أشكال متعددة، وكتابة الأشكال إلى Word باستخدام Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: إنشاء مستند Word مع أشكال برمجيًا باستخدام C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: إنشاء مستند Word مع أشكال برمجيًا باستخدام C#
url: /ar/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word برمجيًا مع الأشكال باستخدام C#

إذا كنت بحاجة إلى **إنشاء مستند Word برمجيًا** يحتوي على رسومات مخصصة، يوضح لك هذا الدليل كيفية القيام بذلك باستخدام Aspose.Words for .NET. ستتعلم كيفية إدراج شكل مستطيل، إضافة أشكال إضافية، تجميعها، وأخيرًا كتابة الأشكال إلى Word—كل ذلك في بضع أسطر من C#.

إنشاء ملف Word يحتوي على رسومات لم يعد يتطلب تحريرًا يدويًا أو سكريبتات ماكرو. بنهاية هذا الدرس ستحصل على طريقة قابلة لإعادة الاستخدام تنتج ملف `.docx` يحتوي على مستطيل وإهليلج مجمّعين معًا، جاهزين للمعالجة اللاحقة أو للتقارير.

## ما ستحتاجه

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.6+)
- Aspose.Words for .NET (حزمة NuGet `Aspose.Words`)
- بيئة تطوير مثل Visual Studio 2022 (أي محرر يمكنه تجميع C# يكفي)

> **نصيحة احترافية:** قم بتثبيت الحزمة باستخدام أمر سطر الأوامر `dotnet add package Aspose.Words` قبل البدء في كتابة الكود.

## إنشاء مستند Word برمجيًا – نظرة عامة

يتكون التدفق العام من ثلاث مراحل منطقية:

1. **تهيئة** كائن `Document` جديد و`DocumentBuilder`.  
2. **إدراج عدة أشكال** (مستطيل وإهليلج) ووضعها داخل `GroupShape`.  
3. **كتابة الأشكال إلى Word** عن طريق حفظ `Document` كملف `.docx`.

كل مرحلة موضحة في خطوة مخصصة أدناه، بحيث يمكنك نسخ‑لصق الكود مباشرةً إلى مشروعك.

![Programmatically create Word document with grouped shapes](grouped-shapes.png){: .align-center alt="إنشاء مستند Word برمجيًا مع أشكال مجمّعة"}

## الخطوة 1: تهيئة المستند والباني

فئة `Document` تمثل ملف Word بالكامل، بينما يوفر `DocumentBuilder` واجهة برمجة تطبيقات سلسة لإضافة المحتوى.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*لماذا هذا مهم:* إنشاء الـ `Document` أولًا يمنحك لوحة رسم نظيفة. يتتبع `DocumentBuilder` نقطة الإدراج الحالية، وهو أمر أساسي عندما تقوم لاحقًا بإرفاق الأشكال بهيكل الفقرات.

## الخطوة 2: إدراج حاوية مجموعة الأشكال

يتيح لك `GroupShape` التعامل مع عدة أشكال فردية كوحدة واحدة. هذا مفيد عندما تريد نقلها أو تغيير حجمها معًا.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*شرح:* `InsertGroupShape` يدرج حاوية فارغة ويجعلها تلقائيًا الشكل الحالي. جميع عمليات إدراج الأشكال التالية ستُضاف إلى هذه الحاوية حتى تقوم بإغلاق المجموعة.

## إدراج شكل مستطيل

الآن نضيف أول رسم—المستطيل. هذا يفي بمتطلب **إدراج شكل مستطيل**.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

المستطيل يرث سياق تنسيق المجموعة، لذا يظهر داخل `GroupShape`. يمكنك أيضًا ضبط لون الخط، التعبئة، أو النص لاحقًا إذا لزم الأمر.

## إدراج عدة أشكال

لإظهار قدرة **إدراج عدة أشكال**، نضيف إهليلجًا مباشرةً بعد المستطيل. يمكنك الاستمرار في إضافة أي عدد من الأشكال (مثل المثلثات أو النجوم) قبل إغلاق المجموعة.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

في هذه المرحلة تحتوي المجموعة على شكلين مميزين: مستطيل وإهليلج. لأنهما يشتركان في نفس الأصل، يمكنك تحريكهما كوحدة واحدة.

## الخطوة 3: إرفاق مجموعة الأشكال بهيكل الفقرات

تخزن مستندات Word المحتوى في شجرة فقرات. لجعل المجموعة مرئية في الملف النهائي، يجب إرفاقها بالفقرة الحالية.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*لماذا هذه الخطوة ضرورية:* بدون إلحاق المجموعة بفقرة، تبقى الأشكال في الذاكرة فقط وتُحذف عند حفظ المستند.

## الخطوة 4: حفظ المستند – كتابة الأشكال إلى Word

أخيرًا، نقوم بحفظ الـ `Document` الموجود في الذاكرة إلى القرص. هذا يحقق هدف **كتابة الأشكال إلى Word**.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

عند فتح `GroupShape.docx` في Microsoft Word، ستظهر لك مستطيل وإهليلج مجمّعين معًا، تمامًا كما أدرج الكود.

### النتيجة المتوقعة

- ملف باسم **GroupShape.docx** موجود في مجلد الإخراج الخاص بالمشروع.
- داخل ملف Word: فقرة واحدة تحتوي على مستطيل مجمّع (100 pt × 50 pt) وإهليلج (80 pt × 40 pt). اختيار أي من الشكلين يختار المجموعة بأكملها.

## معالجة الحالات الشائعة

| الحالة | التوصية |
|-----------|----------------|
| **دقة DPI أو حجم الصفحة مختلف** | اضبط `builder.PageSetup.PaperSize` صراحةً قبل إدراج الأشكال لتجنب التحجيم غير المتوقع. |
| **الحاجة إلى تموضع الأشكال بدقة** | استخدم `builder.MoveTo` لتحريك نقطة الإدراج، ثم عيّن خصائص `groupShape.Left` و `groupShape.Top` (القيم بوحدات النقاط). |


## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة‑بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Word Document – Insert Rectangle Shape & Shadow in C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Create word document programmatically and group shapes in C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Programmatically create a Word document with a group shape](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}