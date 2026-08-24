---
category: general
date: 2026-08-23
description: تعلم كيفية تجميع الأشكال في C# باستخدام Aspose.Words. يغطي الدليل أيضًا
  كيفية إدراج شكل مستطيل وإضافة كلمة shapes للمستندات المعقدة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: ar
lastmod: 2026-08-23
og_description: كيفية تجميع الأشكال في C# باستخدام Aspose.Words. اتبع هذا الدرس الكامل
  لإدراج شكل مستطيل، وإضافة أشكال إلى مستند Word، وتجمّع عدة أشكال بكفاءة.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: كيفية تجميع الأشكال في C# – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: كيفية تجميع الأشكال في C# باستخدام Aspose.Words
url: /ar/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تجميع الأشكال في C# باستخدام Aspose.Words

إذا كنت بحاجة إلى **how to group shapes** في مستند Word برمجيًا، فإن هذا الدليل يوضح لك الخطوات الدقيقة باستخدام Aspose.Words لـ .NET. سواءً كنت تبني مولد تقارير، أو محرك قوالب، أو أداة رسم مخططات، ستتعلم كيفية بدء مجموعة، وإدراج شكل مستطيل، وإضافة محتوى على مستوى الكلمات داخل الأشكال دون مغادرة الكود.

سترى أيضًا كيفية **group multiple shapes** معًا، وهو أمر أساسي عندما تريد نقل أو تدوير أو تنسيق مجموعة من الكائنات ككيان واحد. المثال أدناه يعمل مع أحدث إصدار Aspose.Words 24.x ويتطلب فقط .NET 6 أو أحدث.

## المتطلبات المسبقة

- .NET 6 SDK (أو أي إصدار .NET مدعوم من Aspose.Words)
- Visual Studio 2022 أو VS Code
- حزمة NuGet الخاصة بـ Aspose.Words لـ .NET (`Install-Package Aspose.Words`)
- إلمام أساسي بـ C# ونموذج كائنات Aspose.Words

> **نصيحة احترافية:** استخدم ترخيص التقييم المجاني من Aspose لتجنب قيود العلامة المائية أثناء الاختبار.

## كيفية تجميع الأشكال باستخدام Aspose.Words

فيما يلي برنامج كامل وقابل للتنفيذ يوضح **how to start group**، وإضافة مستطيل، وإنهاء المجموعة. يتبع الكود نفس التدفق المنطقي للمقتطف الذي قدمته، لكنه يضيف سياقًا، ومعالجة أخطاء، وتعليقات لتوضيح الفكرة.

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
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### لماذا كل خطوة مهمة

| الخطوة | الغرض | كيف يرتبط بالكلمات المفتاحية |
|------|---------|--------------------------------|
| **Create a new blank document** | يوفر لوحة رسم نظيفة لعمليات الأشكال. | يهيئ المشهد لـ **add shapes word** لاحقًا. |
| **Initialize DocumentBuilder** | المُنشئ هو الـ API الأساسي لإدراج الكائنات. | مطلوب قبل أن تتمكن من **how to start group**. |
| **StartGroupShape** | يبدأ حاوية منطقية؛ جميع الأشكال التالية تصبح أعضاء في هذه المجموعة. | يجيب مباشرةً على **how to start group**. |
| **InsertShape** (rectangle, ellipse, text) | يضع الأشكال الفردية داخل المجموعة. استدعاء المستطيل يفي بـ **insert rectangle shape**؛ وشكل النص يفي بـ **add shapes word**. | يوضح **group multiple shapes**. |
| **EndGroupShape** | ينهي المجموعة بحيث يمكنك نقلها أو تنسيقها كوحدة واحدة. | يكمل سير عمل **how to group shapes**. |

## إدراج شكل مستطيل – نظرة أعمق

طريقة `InsertShape` تقبل تعداد `ShapeType`، العرض، والارتفاع. لإجراء **insert rectangle shape** مع تنسيق مخصص، يمكنك توسيع المثال:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **لماذا تنسيقه؟** يضمن التنسيق بروز المستطيل عندما يتم إعادة تموضع المجموعة لاحقًا. كما يوضح أن خصائص الشكل يمكن تعيينها *قبل* إغلاق المجموعة.

## إضافة أشكال على مستوى Word (add shapes word)

إذا كنت بحاجة إلى تضمين نص مباشرة داخل شكل—المعروف عادةً باسم “WordArt” أو “مربع نص”—استخدم `ShapeType.TextPlainText`. بعد الإدراج، يمكنك كتابة نص داخل الشكل باستخدام `DocumentBuilder.Writeln` أو عبر الوصول إلى خاصية `TextBox` الخاصة بالشكل:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

هذا يفي بكلمة المفتاح **add shapes word** ويظهر كيف يمكن للنص أن ينتقل مع المجموعة.

## تجميع أشكال متعددة – سيناريوهات عملية

عند **group multiple shapes**، يمكنك التعامل معها ككائن واحد لتحديد الموقع أو التدوير أو التحجيم. على سبيل المثال، بعد إغلاق المجموعة، يمكنك نقل المجموعة بأكملها:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

أو تدوير المجموعة:

```csharp
group.Rotation = 45; // degrees
```

هذه العمليات ممكنة فقط لأن الأشكال تشترك في نفس المجموعة الأصلية.

## معالجة الحالات الحدية

1. **Nested groups** – يتيح Aspose.Words مجموعات داخل مجموعات. لإنشاء مجموعة متداخلة، استدعِ `StartGroupShape` مرة أخرى قبل استدعاء `EndGroupShape` للمجموعة الداخلية.
2. **Empty groups** – إذا بدأت مجموعة ولكن لم تُدرج أي شكل، سيظل `EndGroupShape` ينشئ حاوية فارغة. هذا غير ضار لكنه قد يزيد حجم الملف قليلًا.
3. **Compatibility** – يعمل ملف DOCX المُولد مع Word 2010 وما بعده. قد تتجاهل الإصدارات القديمة بيانات تجميع المجموعات، لذا اختبر دائمًا مع نسخة Word المستهدفة.

## ملف المصدر الكامل للمرجعية

احفظ ما يلي كملف `Program.cs` في مشروع وحدة تحكم .NET. الكود يُترجم ويُنفّذ دون تعديل.

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
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### النتيجة المتوقعة

فتح `GroupedShapes.docx` في Microsoft Word سيظهر:

- مستطيل بلون كورال فاتح، وإهليلج، ومربع نص—جميعها مرتبطة بصريًا معًا.
- تحديد أي جزء من المجموعة سيحدد أيضًا المجموعة بأكملها (يظهر صندوق حد واحد).
- نقل أو تدوير المجموعة ينقل جميع الأشكال الثلاثة معًا.

## الأسئلة المتكررة

**س: هل يمكنني تجميع أشكال موجودة بالفعل في المستند؟**  
ج: نعم. استرجع كائنات `Shape` الموجودة، استدعِ `builder.StartGroupShape()`، أعد إدراجها باستخدام `builder.InsertShape(existingShape)`، ثم استدعِ `EndGroupShape()`.

**س: هل يؤثر التجميع على XML الأساسي؟**  
ج: يضيف Aspose.Words عنصر `<w:grpSp>` الذي يحتوي على عقدة `<w:sp>` لكل شكل. هذا يتوافق تمامًا مع مواصفة Office Open XML.

**س: ماذا لو احتجت إلى فك التجميع لاحقًا؟**  
ج: لا توجد واجهة برمجة تطبيقات مباشرة لـ “ungroup”، لكن يمكنك التكرار عبر الأشكال الفرعية للمجموعة (`group.GroupShape.Children`) ونسخها إلى جسم المستند.

## الخطوات التالية

الآن بعد أن عرفت **how to group shapes**، فكر في استكشاف المواضيع ذات الصلة التالية:

- **Apply complex formatting to grouped shapes** – تعلم كيفية تعيين تعبئات تدرجية، تأثيرات الظل، وأنماط الخط.
- **Export grouped shapes as images** – استخدم `Shape.GetShapeRenderer().Save(...)` لتحويل المجموعة إلى صورة نقطية.
- **Create dynamic diagrams** – اجمع بين تحديد المواقع المستند إلى البيانات والتجميع لإنشاء مخططات تدفق تلقائيًا.

كل من هذه يبني على الأساس الذي تم تغطيته هنا وسيساعدك على إنشاء مستندات Word أكثر غنى وتفاعلية.

---

*برمجة سعيدة! إذا وجدت هذا الدليل مفيدًا، شاركه مع زملائك أو ضع نجمة على المستودع الذي يحتوي على مشروع العينة.*

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إدراج أشكال في مستندات Word باستخدام Aspose.Words لـ .NET](/words/english/net/working-with-shapes/insert-shape/)
- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words لـ .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}