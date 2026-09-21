---
category: general
date: 2026-09-21
description: تعلم كيفية تجميع الأشكال في Word باستخدام Aspose.Words للغة C#. يغطي
  هذا الدليل خطوة بخطوة إنشاء الأشكال وتحديد موقعها وحفظ الأشكال المجمعة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: ar
lastmod: 2026-09-21
og_description: تجميع الأشكال في Word باستخدام Aspose.Words للـ C#. اتبع هذا الدرس
  المختصر لإنشاء وتحديد موضع وحفظ الأشكال المجمعة برمجيًا.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: تجميع الأشكال في Word باستخدام Aspose.Words – دليل C# الكامل
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية تجميع الأشكال في Word باستخدام Aspose.Words للغة C#
url: /ar/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تجميع الأشكال في Word باستخدام Aspose.Words للغة C#

إذا كنت بحاجة إلى **تجميع الأشكال في Word** برمجيًا، فإن Aspose.Words يجعل ذلك بسيطًا. يوضح هذا الدليل كيفية إنشاء شكلين مستطيلين، وضعهما جنبًا إلى جنب، دمجهما في `GroupShape`، وحفظ النتيجة كملف DOCX.

سترى مثالًا كاملاً قابلاً للتنفيذ، وشروحات لأسباب أهمية كل خطوة، ونصائح للتعامل مع الحالات الشائعة مثل تداخل الأشكال أو تغيير الحجم ديناميكيًا. بنهاية هذا الدليل يمكنك دمج تجميع الأشكال في أي مشروع أتمتة Word.

## المتطلبات المسبقة

* .NET 6.0 (أو أحدث) مثبت – يدعم Aspose.Words .NET Standard 2.0+، .NET Core، و .NET Framework.  
* رخصة صالحة لـ Aspose.Words for .NET (أو مفتاح تقييم مؤقت) – تعمل المكتبة بدون رخصة لكنها تضيف علامة مائية.  
* Visual Studio 2022 (أو أي بيئة تطوير C#) لتجميع وتشغيل العينة.  

لا توجد حزم NuGet إضافية مطلوبة بخلاف `Aspose.Words`.

## كيفية تجميع الأشكال في Word باستخدام Aspose.Words

جوهر الحل هو كائن **`GroupShape`** الذي يعمل كحاوية للأشكال الفردية. أدناه نقسم العملية إلى خطوات واضحة.

### الخطوة 1: إنشاء مستند فارغ و`DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*لماذا هذه الخطوة؟*  
`Document` يمثل ملف DOCX بالكامل، بينما `DocumentBuilder` يوفر طرقًا سلسة (مثل `InsertShape`) التي تضع العناصر الجديدة تلقائيًا في موضع المؤشر الحالي.

### الخطوة 2: إدراج الشكل المستطيل الأول

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

تضيف استدعاء `InsertShape` الشكل إلى المستند وتعيد كائن `Shape` يمكنك تكوينه لاحقًا (اللون، الحدود، إلخ). يُعبّر عن الحجم بالنقاط (1 pt ≈ 1/72 in).

### الخطوة 3: إدراج المستطيل الثاني وإزاحته

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

تحديد `Left` يضع الشكل بالنسبة إلى هامش الصفحة. يجب أن يكون الإزاحة أكبر من عرض الشكل الأول (100 pt) لتجنب التداخل؛ نستخدم 120 pt لترك فجوة صغيرة.

### الخطوة 4: إنشاء `GroupShape` كبير بما يكفي لكلا المستطيلين

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` يأخذ الـ `Document` المالك وأبعاد الحاوية. يجب أن يتجاوز عرض الحاوية الحد الأيمن لأبعد شكل؛ وإلا سيُقطع الشكل الثاني.

### الخطوة 5: إلحاق الأشكال الفردية بالمجموعة

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

الإلحاق ينقل الأشكال إلى مجموعة داخلية داخل `GroupShape`. بعد هذا الاستدعاء، لا تعد الأشكال كائنات مستقلة في شجرة المستند—بل تنتمي إلى المجموعة.

### الخطوة 6: إدراج الشكل المجمع مرة أخرى في المستند

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` يضع الـ `GroupShape` بالكامل حيث يتواجد المؤشر حاليًا. إذا كنت بحاجة إلى المجموعة في فقرة معينة، انقل الـ builder إلى تلك الفقرة أولاً.

### الخطوة 7: حفظ المستند

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

الملف الناتج يحتوي على مستطيلين يتصرفان ككائن واحد—يمكنك تحريكهما، تغيير حجمهما، أو حذفهما معًا في Microsoft Word.

## الكود الكامل

جمع جميع الخطوات معًا ينتج برنامجًا مستقلًا:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**الناتج المتوقع:** عند فتح *GroupedShapes.docx* في Microsoft Word يظهر مستطيلان جنبًا إلى جنب، يُعاملان ككائن قابل للتحديد واحد. سحب المجموعة يحرك كلا المستطيلين معًا.

## الاختلافات الشائعة وحالات الحافة

| الحالة | التعديل الموصى به |
|-----------|------------------------|
| **أكثر من شكلين** | إنشاء كائنات `Shape` إضافية، وضعها وفقًا لذلك، وإلحاق كل منها إلى نفس `GroupShape`. |
| **حجم ديناميكي** | احسب عرض/ارتفاع المجموعة بناءً على القيم القصوى `Right` و `Bottom` للأشكال الفرعية. |
| **أنواع أشكال مختلفة** | `ShapeType.Ellipse`، `ShapeType.Triangle`، إلخ، يمكن إدراجها بنفس الطريقة؛ حاوية المجموعة لا تهتم بالنوع. |
| **أشكال مدارة** | عيّن `shape.Rotation = 45;` قبل الإلحاق؛ يتم الحفاظ على الدوران داخل المجموعة. |
| **الحفظ كملف PDF** | استدعِ `doc.Save("GroupedShapes.pdf");` – تُحافظ المجموعة على وجودها في عرض PDF. |

**نصيحة احترافية:** بعد التجميع، لا يزال بإمكانك تعديل الأشكال الفردية عبر الوصول إلى `group.GetChildNodes(NodeType.Shape, true)`. هذا مفيد عندما تحتاج إلى تغيير لون تعبئة أحد المستطيلات دون كسر المجموعة.

## كيفية التحقق من التجميع برمجيًا

إذا كنت بحاجة إلى التأكد من أن الأشكال تم تجميعها بشكل صحيح (مثلاً في اختبارات الوحدة)، فافحص شجرة عقد المستند:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

يجب أن يكون الإخراج:

```
Number of groups: 1
Children in first group: 2
```

هذا يؤكد أن **تجميع الأشكال في Word** تم إنشاؤه كما هو متوقع.

## الخلاصة

أنت الآن تعرف كيفية **تجميع الأشكال في Word** باستخدام Aspose.Words للغة C#. تتضمن العملية إنشاء الأشكال الفردية، وضعها، تغليفها داخل `GroupShape`، وإدراج المجموعة مرة أخرى في المستند. باستخدام المثال الكامل أعلاه يمكنك توسيع التقنية لأي عدد من الأشكال، أنواع مختلفة، أو حتى دمجها مع مربعات النص والصور.

بعد ذلك، استكشف المواضيع ذات الصلة مثل **تجميع الأشكال في Aspose.Words**، **معالجة أشكال Word في C#**، و**إدراج شكل باستخدام DocumentBuilder** لمزيد من سيناريوهات أتمتة المستندات المتقدمة. جرب الحجم الديناميكي، التجميع الشرطي، وتصدير إلى PDF للاستفادة الكاملة من قوة Aspose.Words.

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إدراج أشكال في مستندات Word باستخدام Aspose.Words للـ .NET](/words/english/net/working-with-shapes/insert-shape/)
- [إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [دروس ظل الشكل في Aspose.Words – إضافة ظل إلى شكل Word في C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}