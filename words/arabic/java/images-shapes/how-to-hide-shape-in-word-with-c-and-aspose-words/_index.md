---
category: general
date: 2026-09-11
description: تعلم كيفية إخفاء الشكل في Word باستخدام C#. يوضح هذا الدليل أيضًا كيفية
  إدراج شكل مستطيل وإدراج الشكل في مستند Word باستخدام Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: ar
lastmod: 2026-09-11
og_description: كيفية إخفاء الشكل في Word باستخدام C# و Aspose.Words. اتبع الدليل
  خطوة بخطوة لإدراج شكل مستطيل وإدارة الأشكال في مستند Word.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: كيفية إخفاء الشكل في Word – دليل C# الكامل
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية إخفاء الشكل في Word باستخدام C# و Aspose.Words
url: /ar/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إخفاء الشكل في Word باستخدام C# و Aspose.Words

إذا كنت بحاجة إلى إخفاء الشكل في Word مع الحفاظ على وجوده في بنية المستند، فإن هذا الدرس يوضح لك بالضبط كيفية القيام بذلك. باستخدام Aspose.Words for .NET يمكنك إدراج شكل مستطيل، إخفاؤه، وما زال يحتفظ بموقعه للمعالجة لاحقًا.

غالبًا ما تتطلب أتمتة Word تحكمًا دقيقًا في الأشكال — سواء كنت تُنشئ قوالب، تُعد تقارير، أو تبني خدمة تحرير مستندات. بنهاية هذا الدليل ستكون قادرًا على:

* إدراج شكل مستطيل في مستند Word (`insert rectangle shape`).
* إخفاء أي شكل دون حذفه (`how to hide shape in word`).
* حفظ النتيجة والتحقق من أن الشكل المخفي لا يظهر في العرض النهائي (`insert shape into word document`).

يعمل المثال مع Aspose.Words 24.10 أو أحدث ويستهدف .NET 6.0+، لكن المفاهيم تنطبق على الإصدارات السابقة أيضًا.

## المتطلبات المسبقة

* **Aspose.Words for .NET** ≥ 24.10. يمكنك الحصول على ترخيص مؤقت مجاني من موقع Aspose.
* **.NET SDK** 6.0 أو أحدث مثبت على جهازك.
* بيئة تطوير مثل Visual Studio 2022، VS Code، أو Rider.
* إلمام أساسي بـ C# ومفهوم Word Open XML (اختياري لكن مفيد).

## كيفية إخفاء الشكل في Word باستخدام Aspose.Words

فيما يلي برنامج كامل قابل للتنفيذ يوضح سير العمل بالكامل — من إنشاء مستند إلى إدراج شكل مستطيل وأخيرًا إخفائه.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### شرح كل خطوة

1. **إنشاء مستند جديد** – `Document` تمثل ملف Word في الذاكرة. `DocumentBuilder` توفر API سلس لإدراج المحتوى.
2. **إدراج شكل مستطيل** – `InsertShape` تنشئ كائن رسم من النوع `Rectangle`. الأبعاد تُعبّر بالنقاط (1 pt ≈ 1/72 in). هذا يفي بمتطلب `insert rectangle shape`.
3. **إخفاء الشكل** – ضبط `Shape.Hidden = true` يعلّم الشكل كمخفي في ترميز Word (`<w:hidden/>`). يبقى الشكل جزءًا من شجرة المستند، لذا يمكنك لاحقًا إلغاء إخفائه أو الإشارة إليه برمجيًا. هذا هو جوهر `how to hide shape in word`.
4. **حفظ الملف** – يُكتب المستند إلى `output.docx`. عند فتحه في Microsoft Word، لن يكون المستطيل مرئيًا، لكنه لا يزال موجودًا في XML ويمكن فحصه باستخدام عارض ZIP أو Open XML SDK.

### النتيجة المتوقعة

افتح `output.docx` في Microsoft Word:

* المستند يظهر فارغًا — لا شكل مرئي.
* إذا فحصت XML الأساسي (`word/document.xml`) ستجد عنصر `<w:pict>` مع سمة `<w:hidden/>`، مما يؤكد أن الشكل موجود لكنه مخفي.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

يمكن جعل الشكل المخفي مرئيًا مرة أخرى عن طريق ضبط `Hidden = false` وإعادة حفظ المستند.

## إدراج شكل مستطيل في مستند Word

بينما الهدف الأساسي هو إخفاء الشكل، تبدأ العديد من السيناريوهات بإدراج شكل أولاً. طريقة `InsertShape` تدعم العديد من قيم `ShapeType`، بما في ذلك `Rectangle`، `Ellipse`، `Line`، والصور المخصصة.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**لماذا نستخدم مستطيلًا؟**  
المستطيل يوفر حاوية نظيفة ومحاذاة محورية يمكنها احتواء نص، صور، أو أشكال متداخلة أخرى. يُستخدم غالبًا كعنصر نائب للمحتوى الديناميكي مثل الجداول أو المخططات. بإدراج المستطيل أولاً، تحافظ على اتساق التخطيط حتى بعد إخفائه لاحقًا.

## إدراج شكل في مستند Word — أفضل الممارسات

عند `insert shape into word document`، ضع في الاعتبار ما يلي:

* **تحديد أبعاد صريحة** – تجنّب الاعتماد على التحجيم التلقائي؛ حدد العرض والارتفاع بالنقاط لضمان تخطيط متسق عبر المنصات.
* **تحديد الموضع** – بشكل افتراضي يتم تثبيت الشكل إلى الفقرة الحالية. استخدم `builder.MoveTo` أو `builder.StartBookmark` لتحديد موقعه بدقة.
* **تطبيق التنسيق مبكرًا** – لون التعبئة، نمط الخط، وتغليف النص يؤثر على المظهر النهائي. حتى الأشكال المخفية تستفيد من تنسيق صحيح لأن الترميز يبقى دون تغيير.
* **توافق الإصدارات** – خاصية `Hidden` متاحة فقط بدءًا من Aspose.Words 24.10. إذا كنت تستهدف إصدارًا أقدم، يمكنك إضافة سمة `<w:hidden/>` يدويًا باستخدام API `Node`.

### إضافة سمة المخفي يدويًا (البديل)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## مثال كامل من البداية إلى النهاية

بجمع كل شيء معًا، إليك برنامج واحد يقوم بـ:

1. إدراج شكل مستطيل.
2. إخفاء الشكل.
3. إدراج إهليلج مرئي للتباين.
4. حفظ المستند.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

تشغيل البرنامج ينتج `demo_output.docx`. عند فتحه، سترى فقط الإهليلج المرجاني؛ المستطيل الأخضر موجود في XML لكنه مخفي عن العرض.

## أسئلة شائعة وحالات خاصة

**س: هل يؤثر إخفاء الشكل على ترقيم الصفحات؟**  
ج: لا. يتم تجاهل الأشكال المخفية من قبل محرك التخطيط، لذا لا تستهلك مساحة. هذا مفيد لمحتوى العنصر النائب الذي لا ينبغي أن يؤثر على فواصل الصفحات.

**س: هل يمكنني إخفاء شكل جزء من رأس أو تذييل الصفحة؟**  
ج: نعم. خاصية `Hidden` نفسها تعمل على الأشكال الموجودة في أي مكان داخل شجرة المستند، بما في ذلك الرؤوس، التذييلات، وحتى داخل الجداول.

**س: ماذا لو احتجت إلى إخفاء عدة أشكال في آن واحد؟**  
ج: قم بالتكرار عبر مجموعة `Document.GetChildNodes(NodeType.Shape, true)` واضبط `Hidden = true` لكل شكل مستهدف.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**س: هل يتم الحفاظ على سمة المخفي عند التحويل إلى PDF؟**  
ج: عند التحويل إلى PDF، يتم حذف الأشكال المخفية افتراضيًا، مطابقةً سلوك عرض Word. إذا كنت تحتاجها في PDF، يجب إلغاء إخفائها قبل التحويل.

## نصائح ومخاطر

* **نصيحة احترافية:** اضبط `shape.WrapType = WrapType.None` قبل الإخفاء إذا كنت تخطط لاحقًا لإلغاء إخفائه دون إزعاج النص المحيط.
* **احذر من إصدارات Aspose.Words القديمة:** خاصية `Hidden` تُطلق استثناء `NotSupportedException` قبل 24.10. استخدم طريقة XML اليدوية في هذه الحالة.
* **الاختبار:** دائمًا افتح ملف `.docx` المُولد في Word واستخدم “Show XML markup” (علامة تبويب المطور) للتحقق من وجود سمة `<w:hidden/>`.

## الخلاصة

أنت الآن تعرف كيفية إخفاء الشكل في Word باستخدام C# و Aspose.Words، بالإضافة إلى كيفية إدراج شكل مستطيل وإدراج شكل في مستند Word مع تحكم كامل في الرؤية. من خلال الاستفادة من خاصية `Hidden` يمكنك الاحتفاظ بالأشكال في نموذج المستند للمعالجة لاحقًا مع تقديم عرض نظيف للمستخدمين النهائيين.

بعد ذلك، استكشف المواضيع ذات الصلة مثل **تحديث خصائص الشكل في وقت التشغيل**، **تحويل الأشكال المخفية إلى صور**، أو **استخدام Open XML SDK للتعامل مباشرة مع العناصر المخفية**. هذه الإضافات ستعمق

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إدراج أشكال في مستندات Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}