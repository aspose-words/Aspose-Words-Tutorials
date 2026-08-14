---
category: general
date: 2026-08-14
description: كيفية تجميع الأشكال في مستند Word باستخدام C#. تعلم إنشاء مستند Word،
  وإدراج شكل مستطيل، وتجميع الأشكال في Word، وحفظ المستند كملف docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: ar
lastmod: 2026-08-14
og_description: كيفية تجميع الأشكال في مستند Word باستخدام C#. اتبع هذا الدرس الكامل
  لإنشاء ملف Word، وإدراج شكل مستطيل، وتجميع الأشكال في Word، وحفظ النتيجة كملف docx.
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: كيفية تجميع الأشكال في مستند Word باستخدام C# – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: كيفية تجميع الأشكال في مستند Word باستخدام C#
url: /ar/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تجميع الأشكال في مستند Word باستخدام C#

إذا كنت تحتاج إلى **كيفية تجميع الأشكال** في مستند Word، فإن هذا الدليل يوضح لك الخطوات الدقيقة باستخدام C# ومكتبة Aspose.Words. ستتعرف على كيفية إنشاء مستند Word، إدراج شكل مستطيل، تجميع الأشكال في Word، وأخيرًا **حفظ المستند كملف docx**—كل ذلك في برنامج واحد قابل للتنفيذ.

إنشاء وتعديل الأشكال هو متطلب شائع عند توليد التقارير أو العقود أو الكتيبات التسويقية برمجيًا. بنهاية هذا الدرس ستحصل على مقتطف كود قابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع .NET.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث مثبت  
- Visual Studio 2022 (أو أي بيئة تطوير تدعم .NET)  
- ترخيص Aspose.Words for .NET (أو نسخة تجريبية مجانية)  
- إلمام أساسي بصياغة C#  

لا توجد حزم NuGet إضافية مطلوبة بخلاف `Aspose.Words`.

## كيفية تجميع الأشكال في مستند Word

جوهر الحل هو عملية من خمس خطوات. يتم شرح كل خطوة بالتفصيل، ويتم توفير الكود المصدر الكامل في نهاية المقال.

### الخطوة 1: إنشاء مستند فارغ جديد

أول شيء تقوم به عندما تريد **إنشاء مستند Word** برمجيًا هو إنشاء كائن `Document`. هذا الكائن يمثل ملف .docx بالكامل في الذاكرة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**لماذا هذا مهم:** `DocumentBuilder` هو أداة مساعدة عالية المستوى تتيح لك إدراج النصوص والجداول والأشكال دون الحاجة إلى التعامل يدويًا مع شجرة العقد الأساسية.

### الخطوة 2: إدراج شكل مستطيل

للتوضيح **إدراج شكل مستطيل**، نستخدم طريقة `InsertShape`. سيعمل المستطيل كأول عضو في المجموعة.

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**لماذا هذا مهم:** يتم وضع الأشكال نسبةً إلى نقطة الإدراج. ضبط لون التعبئة يساعدك على رؤية الشكل عند فتح المستند الناتج.

### الخطوة 3: إدراج شكل إهليلجي

بعد ذلك، نقوم **بإدراج شكل إهليلجي** (تسميه الواجهة البرمجية `Ellipse`). سيكون هذا هو العضو الثاني في المجموعة.

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**لماذا هذا مهم:** بإدراج الإهليلج مباشرةً بعد المستطيل، ينتهي الأمر بوضع الشكلين في نفس الفقرة، مما يبسط عملية التجميع لاحقًا.

### الخطوة 4: تجميع المستطيل والإهليلج

الآن نجيب على السؤال الأساسي **كيفية تجميع الأشكال** في مستند Word. توفر Aspose.Words طريقة `AppendGroupShape` لإنشاء حاوية مجموعة، ثم تقوم باستدعاء `Group()` على تلك الحاوية.

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**لماذا هذا مهم:** بمجرد التجميع، أي تحويل (نقل، تغيير حجم، تدوير) يُطبق على `groupedShape` يؤثر تلقائيًا على كل من المستطيل والإهليلج. هذا أمر أساسي للحفاظ على تناسق التخطيط في المستندات المولدة.

### الخطوة 5: حفظ المستند كملف DOCX

الخطوة الأخيرة هي **حفظ المستند كملف docx**. يمكنك اختيار أي مسار تفضله؛ المثال يستخدم عنصر نائب `"YOUR_DIRECTORY"` يجب استبداله بمجلد حقيقي.

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**لماذا هذا مهم:** حفظ الملف كـ DOCX يحافظ على بيانات التجميع، لذا عند فتح الملف في Microsoft Word سترى المستطيل والإهليلج يعملان ككائن واحد.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يجمع جميع الخطوات الخمس. انسخه في مشروع وحدة تحكم جديد، استعد حزمة NuGet الخاصة بـ Aspose.Words، ثم شغّله.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### النتيجة المتوقعة

عند فتح `groupedShapes.docx` في Microsoft Word، ستلاحظ مستطيل أزرق فاتح وإهليلج وردي فاتح مرتبطين معًا. النقر على أي من الشكلين يحدد كليهما، مما يتيح لك تحريكهما أو تغيير حجمهما كوحدة واحدة.

## الأسئلة الشائعة والحالات الخاصة

| Question | Answer |
|----------|--------|
| **هل يمكنني تجميع أكثر من شكلين؟** | نعم. مرّر أي عدد من كائنات `Shape` إلى `AppendGroupShape`. الطريقة تقبل مصفوفة، لذا يمكنك بناء مجموعة ديناميكيًا. |
| **ماذا لو احتجت أن تكون المجموعة مرتبطة بخلية جدول؟** | أدخل الأشكال داخل فقرة الخلية، ثم استدعِ `AppendGroupShape` على تلك الفقرة. المجموعة ترث تثبيت الخلية. |
| **هل يؤثر التجميع على XML الأساسي؟** | تكتب Aspose.Words عنصر `<w:grpSp>` الذي يحتوي على الأشكال الفرعية. يتعرف Word على ذلك كمجموعة، محافظًا على التموقع النسبي. |
| **كيف يمكنني فك التجميع لاحقًا؟** | استدعِ `groupedShape.Ungroup()`؛ تُعيد الطريقة الأشكال الفردية بحيث يمكنك تعديلها بشكل منفصل. |
| **هل هناك تأثير على الأداء عند تجميع عدد كبير من الأشكال؟** | التجميع نفسه غير مكلف، لكن عرض مجموعات كبيرة جدًا (مئات الأشكال) قد يزيد من حجم الملف. فكر في تسطيح الصور إذا أصبح الحجم مشكلة. |

## نصائح احترافية

- **حدد المواقع الصريحة** (`Left`, `Top`) إذا كنت بحاجة إلى محاذاة دقيقة قبل التجميع.  
- **استخدم `Shape.WrapType = WrapType.Inline`** عندما تريد أن تتصرف المجموعة كعنصر فقرة بدلاً من كائن عائم.  
- **طبق نمط خط** على المجموعة (`groupedShape.LineFormat`) لإعطاء المجموعة بأكملها حدًا.  
- **أعد استخدام المجموعة**: بعد استدعاء `Group()`، يمكنك استنساخ `groupedShape` وإدراج النسخة المستنسخة في مكان آخر في المستند.

## الخطوات التالية

الآن بعد أن عرفت **كيفية تجميع الأشكال** في مستند Word، يمكنك استكشاف المواضيع ذات الصلة مثل:

- **إدراج شكل مستطيل** مع نص مخصص أو صور داخل الشكل.  
- **إنشاء مخططات معقدة** عن طريق تجميع المجموعات داخل بعضها (تجميع مجموعة).  
- **تصدير المستند كملف PDF** مع الحفاظ على تجميع الأشكال (`doc.Save("output.pdf", SaveFormat.Pdf)`).  

كل من هذه يبني على الأساسيات نفسها التي تم تغطيتها هنا، لذا أنت في موقع جيد لتوسيع مجموعة أدوات أتمتة Word الخاصة بك.

## الخلاصة

هذا الدرس أوضح **كيفية تجميع الأشكال** في مستند Word باستخدام C#. تعلمت **إنشاء مستند Word**، **إدراج شكل مستطيل**، **تجميع الأشكال في Word**، وأخيرًا **حفظ المستند كملف docx**. مع المثال الكامل القابل للتنفيذ والنصائح العملية المقدمة، يمكنك دمج تجميع الأشكال في أي سير عمل لتوليد المستندات. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إدراج أشكال في مستندات Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}