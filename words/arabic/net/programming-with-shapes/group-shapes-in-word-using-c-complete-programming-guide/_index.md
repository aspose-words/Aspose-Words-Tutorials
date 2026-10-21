---
category: general
date: 2026-10-13
description: تجميع الأشكال في Word باستخدام C# – تعلم كيفية تجميع الأشكال وإضافة أشكال
  إلى المجموعة باستخدام Aspose.Words في بضع خطوات سهلة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- add shapes to group
language: ar
lastmod: 2026-10-13
og_description: تجميع الأشكال في Word باستخدام C# و Aspose.Words. اتبع هذا الدليل
  لتعلم كيفية تجميع الأشكال وإضافة الأشكال إلى مجموعة في مستند Word.
og_image_alt: Screenshot of a Word document showing two shapes combined into a single
  grouped shape
og_title: تجميع الأشكال في Word باستخدام C# – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  headline: Group shapes in Word using C# – complete programming guide
  type: TechArticle
- description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  name: Group shapes in Word using C# – complete programming guide
  steps:
  - name: Load the Word document
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Retrieve the shapes you want to group
    text: '```csharp // Get the first shape (index 0) and second shape (index 1) from
      the whole document. Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0,
      true); Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true); ```'
  - name: Create a new `GroupShape` container
    text: '```csharp GroupShape groupShape = new GroupShape(doc); ```'
  - name: Add the individual shapes to the group
    text: '```csharp groupShape.AppendChild(firstShape); groupShape.AppendChild(secondShape);
      ```'
  - name: Insert the group shape into the document body
    text: '```csharp // Insert the group as the last child of the first paragraph.
      Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph; firstParagraph.AppendChild(groupShape);
      ```'
  - name: Save the modified document
    text: '```csharp string outputPath = @"YOUR_DIRECTORY\output.docx"; doc.Save(outputPath);
      ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: تجميع الأشكال في Word باستخدام C# – دليل برمجي كامل
url: /ar/net/programming-with-shapes/group-shapes-in-word-using-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تجميع الأشكال في Word باستخدام C# – دليل برمجة كامل

إذا كنت بحاجة إلى **تجميع الأشكال في Word** برمجيًا، يوضح لك هذا الدليل الطريقة بالضبط. بحلول نهاية الجملتين الأوليين ستعرف الكود المطلوب، السبب وراء كل خطوة، وكيفية **إضافة الأشكال إلى المجموعة** دون مفاجآت.

سنغطي كل شيء بدءًا من تحميل ملف `.docx` وحتى حفظ المستند المحدث. يفترض الدليل أن لديك معرفة أساسية بـ C# وإشارة إلى مكتبة Aspose.Words for .NET. لا تحتاج إلى أي وثائق خارجية—فقط انسخ، الصق، وشغِّل.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)
- حزمة NuGet الخاصة بـ Aspose.Words for .NET (`Install-Package Aspose.Words`)
- مستند Word (`input.docx`) يحتوي مسبقًا على شكلين على الأقل (مثل الصور أو AutoShapes)

> **نصيحة محترف:** إذا كنت تختبر، أنشئ ملف Word بسيط يحتوي على مستطيلين عبر واجهة Word. احفظه باسم `input.docx` في مجلد تتحكم فيه.

## تجميع الأشكال في Word – دليل خطوة بخطوة

فيما يلي نقسم العملية إلى خمس خطوات منطقية. كل خطوة تتضمن كود C# الدقيق، شرحًا *لـ لماذا* السطر مطلوب، وملاحظة قصيرة حول الأخطاء الشائعة.

### الخطوة 1: تحميل مستند Word

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
```

**لماذا:** `Document` هو نقطة الدخول لأي تعديل على Word. توفير المسار الكامل للملف يحمل المستند في الذاكرة، مما يسمح لنا باستعلام شجرة العقد وتعديلها.

**ملاحظة:** تمرير مسار نسبي قد يفشل عندما يختلف دليل العمل. استخدم مسارًا مطلقًا أو `Path.Combine` مع `AppContext.BaseDirectory`.

### الخطوة 2: استرجاع الأشكال التي تريد تجميعها

```csharp
// Get the first shape (index 0) and second shape (index 1) from the whole document.
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);
```

**لماذا:** `GetChild` يتجول في شجرة المستند ويعيد العقدة *n‑th* من النوع المطلوب. ضبط `isDeep` إلى `true` يبحث في المستند بأكمله، وليس فقط في القسم الحالي.

**حالة حدية:** إذا كان المستند يحتوي على أقل من شكلين، فإن `firstShape` أو `secondShape` سيكون `null` وسيتم إلقاء استثناء عند محاولة التحويل. احمِ الكود من ذلك:

```csharp
if (firstShape == null || secondShape == null)
    throw new InvalidOperationException("The document must contain at least two shapes to group.");
```

### الخطوة 3: إنشاء حاوية `GroupShape` جديدة

```csharp
GroupShape groupShape = new GroupShape(doc);
```

**لماذا:** `GroupShape` يعمل كعقدة أب يمكنها احتواء عدة كائنات `Shape`. هو يرث من `Shape`، لذا يمكن إدراجه في أي مكان يُسمح فيه بإدراج شكل عادي (مثل داخل فقرة).

### الخطوة 4: إضافة الأشكال الفردية إلى المجموعة

```csharp
groupShape.AppendChild(firstShape);
groupShape.AppendChild(secondShape);
```

**لماذا:** `AppendChild` ينقل الأشكال من مواقعها الأصلية إلى المجموعة الجديدة. بعد هذا الاستدعاء، لا توجد الأشكال الأصلية كعقد مستقلة؛ تصبح جزءًا من `groupShape`.

**نصيحة:** التجميع يضبط تلقائيًا المواقع النسبية للأشكال الفرعية. إذا كنت تحتاج إلى تخطيط محدد، عيّن خاصية `GroupShape.Bounds` *قبل* إضافة الأطفال.

```csharp
// Example: set the group to start at (100, 100) points and be 300x200 points large.
groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);
```

### الخطوة 5: إدراج مجموعة الأشكال في جسم المستند

```csharp
// Insert the group as the last child of the first paragraph.
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
firstParagraph.AppendChild(groupShape);
```

**لماذا:** يجب وضع `GroupShape` داخل فقرة (أو خلية جدول) لتظهر. بإلحاقها بالفقرة الأولى نضمن وضعًا مرئيًا دون إزعاج التخطيط الحالي.

### الخطوة 6: حفظ المستند المعدل

```csharp
string outputPath = @"YOUR_DIRECTORY\output.docx";
doc.Save(outputPath);
```

**لماذا:** `Save` يكتب التغييرات الموجودة في الذاكرة إلى ملف `.docx`. يمكنك أيضًا الحفظ إلى تدفق أو إلى PDF بتغيير النسخة المتعددة المعاملات.

**التحقق من النتيجة:** افتح `output.docx` في Microsoft Word. يجب أن ترى الشكلين الأصليين الآن مدمجين في كائن مجموعة واحد. اختيار المجموعة سيظهر مقابض التجميع القياسية في Word.

## كيفية تجميع الأشكال برمجيًا – رؤى أعمق

- **ملكية العقدة:** عند استدعاء `AppendChild`، يتغير مرجع `ParentNode` للشكل تلقائيًا. هذا يمنع وجود عقد "يتيمة" قد تفسد المستند.
- **الحفاظ على التنسيق:** التجميع **لا** يفقد أي تنسيق للشكل (لون التعبئة، نمط الخط، إلخ). جميع الأشكال الفرعية تحتفظ بخصائصها الأصلية.
- **المجموعات المتداخلة:** يمكن لـ `GroupShape` احتواء كائنات `GroupShape` أخرى، مما يتيح هياكل متعددة المستويات. تعامل مع المجموعة الداخلية كأي شكل آخر.

## إضافة أشكال إلى المجموعة وإدارتها لاحقًا

إذا كنت بحاجة إلى إضافة المزيد من الأشكال بعد إنشاء المجموعة الأولية، يمكنك إعادة استخدام نفس كائن `GroupShape`:

```csharp
// Assume we have a third shape somewhere in the document.
Shape thirdShape = (Shape)doc.GetChild(NodeType.Shape, 2, true);
groupShape.AppendChild(thirdShape);
```

عند الحاجة لاحقًا إلى فك التجميع، قم بالتكرار على `groupShape.GetChildNodes(NodeType.Shape, true)` وأعد إدراج كل طفل في المكان الذي تريده.

```csharp
foreach (Shape child in groupShape.GetChildNodes(NodeType.Shape, true))
{
    // Example: move each child back to the original paragraph.
    firstParagraph.AppendChild(child);
}
firstParagraph.RemoveChild(groupShape); // Remove the empty group container.
```

**لماذا هذا مهم:** بعض سير العمل يتطلب تجميعًا مؤقتًا (مثل محاذاة عدة كائنات) يليه فك التجميع لإجراء تعديلات فردية إضافية.

## مثال كامل قابل للتنفيذ

فيما يلي برنامج مستقل يمكنك تجميعه وتشغيله كما هو. استبدل `YOUR_DIRECTORY` بمسار مجلد فعلي على جهازك.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the document.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2. Retrieve the first two shapes.
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);

        if (firstShape == null || secondShape == null)
        {
            Console.WriteLine("Document must contain at least two shapes.");
            return;
        }

        // 3. Create a GroupShape container.
        GroupShape groupShape = new GroupShape(doc);

        // Optional: define the group’s bounding box.
        groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);

        // 4. Add the shapes to the group.
        groupShape.AppendChild(firstShape);
        groupShape.AppendChild(secondShape);

        // 5. Insert the group into the first paragraph.
        Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(groupShape);

        // 6. Save the result.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Grouped shapes saved to {outputPath}");
    }
}
```

**الناتج المتوقع:** عند فتح `output.docx`، سيظهر الشكلان الأصليان ككائن مجموعة واحد. اختيار المجموعة يُظهر مقابض التجميع المألوفة في Word، مما يتيح لك نقل، تغيير حجم، أو تدوير المجموعة بأكملها معًا.

## الخاتمة

أنت الآن تعرف كيف **تجميع الأشكال في Word** باستخدام C# و Aspose.Words، ورأيت الخطوات الدقيقة **لإضافة الأشكال إلى المجموعة** ثم تعديلها أو فك تجميعها لاحقًا. هذه التقنية مثالية لأتمتة تخطيطات التقارير، إنشاء مخططات مركبة، أو إعداد قوالب Word تتطلب تموضعًا دقيقًا لعدة كائنات.

بعد ذلك، استكشف مواضيع ذات صلة مثل **كيفية تجميع الأشكال** بأنواع تثبيت مختلفة، تطبيق **تنسيق متقدم** على الكائنات المجمعة، أو تصدير النتيجة المجمعة إلى PDF. جرّب تجميع المجموعات المتداخلة لبناء رسومات معقدة برمجيًا.

برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك الخاصة.

- [إدراج أشكال في مستندات Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إضافة تأثير الظل إلى أشكال Word – دليل C# كامل](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}