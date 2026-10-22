---
category: general
date: 2026-07-19
description: تجميع الأشكال في Word باستخدام Aspose.Words. تعلّم كيفية إضافة شكل مستطيل،
  تعريف شكل إهليلجي، وإدراج الشكل في مستندات Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: ar
lastmod: 2026-07-19
og_description: تجميع الأشكال في Word باستخدام Aspose.Words. إضافة شكل مستطيل، تعريف
  شكل بيضاوي، وإدراج الشكل في مستندات Word.
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: تجميع الأشكال في Word – دليل C# خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: تجميع الأشكال في Word باستخدام Aspose.Words – دليل C# الكامل
url: /ar/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تجميع الأشكال في Word – دليل C# كامل

هل تساءلت يومًا كيف **تجميع الأشكال في Word** دون العبث بالواجهة؟ لست وحدك. سواء كنت تُنشئ العقود أو النشرات أو المخططات برمجيًا، فإن القدرة على **إضافة شكل مستطيل**، **تعريف شكل بيضاوي**، ثم **تجميع الأشكال في Word** يمكن أن توفر لك ساعات من العمل اليدوي.

في هذا الدرس سنستعرض مثالًا واقعيًا باستخدام **Aspose.Words for .NET**. في النهاية ستعرف بالضبط كيفية **إدراج شكل في Word**، دمجها، وإنتاج مستند مصقول يمكنك إرساله إلى العملاء أو زملائك.

---

## ما ستحتاجه

- **Aspose.Words for .NET** (أحدث إصدار، مثلاً 24.9). يمكنك الحصول عليه من NuGet باستخدام `Install-Package Aspose.Words`.
- بيئة تطوير .NET (Visual Studio 2022 أو VS Code مع امتداد C# تعمل بشكل جيد).
- إلمام أساسي بصياغة C#—ليس شيئًا معقدًا، فقط عبارات `using` المعتادة وإنشاء الكائنات.

هذا كل شيء. لا مكتبات إضافية، لا تفاعل COM، فقط كود مُدار نقي.

---

## كيفية تجميع الأشكال في Word باستخدام Aspose.Words

فيما يلي تفصيل خطوة بخطوة يعكس الكود الذي لديك بالفعل. كل خطوة تشرح **لماذا** نقوم بذلك، وليس فقط **ماذا** تفعل السطر، حتى تتمكن من تعديل النمط لأي شكل تريده.

### الخطوة 1: إعداد المستند والباني

نبدأ بإنشاء `Document` فارغ و`DocumentBuilder`. الباني هو “قلمنا” الذي يسمح لنا بإدراج المحتوى في أي مكان نحتاجه.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **لماذا؟** كائن `Document` يمثل ملف .docx بالكامل، بينما `DocumentBuilder` يوفر واجهة برمجة تطبيقات مريحة لإدراج العقد (مثل الأشكال) دون التعامل مع شجرة العقد الأساسية.

### الخطوة 2: إضافة شكل مستطيل (add rectangle shape)

الآن نقوم **بإضافة شكل مستطيل** إلى المستند. نحدد حجمه، موقعه، ولون التعبئة لجعله بارزًا.

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **نصيحة:** يمكنك تغيير `FillColor` إلى أي `System.Drawing.Color` تفضله. هذا مفيد عندما تحتاج إلى أقسام ملونة في تقرير.

### الخطوة 3: تعريف شكل بيضاوي (define ellipse shape)

بعد ذلك، **نعرّف شكل بيضاوي**. لاحظ اختلاف `ShapeType` والإزاحة (`Left = 120`) بحيث يجلس البيضاوي بجانب المستطيل.

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **لماذا هذا مهم:** من خلال تحديد مواقع الأشكال صراحةً، تتحكم في كيفية ظهورها قبل تجميعها. إذا اعتمدت على التخطيط التلقائي، قد يبدو التجميع غير مركّز.

### الخطوة 4: (اختياري) إدراج الأشكال الفردية للمعاينة

إذا أردت رؤية كل شكل قبل التجميع، يمكنك **إدراج شكل في Word** بشكل فردي. هذه الخطوة اختيارية لكنها مفيدة للتصحيح.

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **نصيحة احترافية:** علق هذين السطرين بمجرد أن تكون واثقًا من أن الأشكال تبدو صحيحة؛ وإلا ستحصل على رسومات مكررة بعد التجميع.

### الخطوة 5: كيفية تجميع الأشكال – إنشاء GroupShape

هذا هو جوهر الدرس: **كيفية تجميع الأشكال**. ننشئ `GroupShape`، نرفق المستطيل والبيضاوي، ونقرر كيف يتصرف التجميع مع النص المحيط.

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **شرح:** `GroupShape` هو في الأساس لوحة صغيرة تحتفظ بأشكال أخرى. من خلال تعيين `WrapType` إلى `Inline`، يتحرك التجميع بأكمله كوحدة واحدة عند إضافة أو حذف النص.

### الخطوة 6: إدراج الشكل المجمع في المستند (insert shape into word)

الآن **نُدرج الشكل في Word**—لكن هذه المرة هو الحاوية المجمعة، وليس القطع الفردية.

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **ماذا يحدث خلف الكواليس؟** استدعاء `InsertNode` يضيف `GroupShape` إلى مجموعة عقد المستند. لأن التجميع يحتوي بالفعل على المستطيل والبيضاوي، يظهران معًا ككائن واحد.

### الخطوة 7: حفظ المستند

أخيرًا، اكتب الملف إلى القرص. يمكنك تغيير المسار ليتناسب مع بنية مشروعك.

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **النتيجة:** افتح `GroupShape.docx` في Microsoft Word وسترى مستطيلًا أزرق فاتحًا وبيضاويًا مرجانيًا مقفلين معًا. سحب أحدهما يحرك الآخر—تمامًا ما تعد به “تجميع الأشكال في Word”.

---

## تأكيد بصري

فيما يلي نموذج تقريبي لما يبدو عليه الأشكال المجمعة داخل ملف Word.  

![لقطة شاشة للأشكال المجمعة في مستند Word تم إنشاؤه باستخدام Aspose.Words](grouped_shapes_placeholder.png "تجميع الأشكال في Word")

*نص alt للصورة يحتوي على الكلمة المفتاحية الأساسية من أجل إمكانية الوصول وتحسين محركات البحث.*

---

## أسئلة شائعة وحالات خاصة

### ماذا لو احتجت إلى أكثر من شكلين؟

ما عليك سوى الاستمرار في استدعاء `groupShape.AppendChild(yourNewShape);` قبل إدراج المجموعة. لا يفرض API أي حد لعدد الأشكال الفرعية.

### هل يمكنني تدوير أو تغيير حجم المجموعة بأكملها؟

بالطبع. `GroupShape` يرث من `Shape`، لذا يمكنك ضبط خصائص مثل `RotationAngle`، `Width` أو `Height` على المجموعة نفسها، وستتبع جميع الأشكال الفرعية هذه التغييرات.

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### كيف أغيّر لون خلفية المجموعة؟

استخدم `groupShape.FillColor`. هذا يملأ الصندوق الحدودي غير المرئي؛ يمكن أن يكون مفيدًا للتسليط.

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### هل يعمل هذا مع صيغ Word القديمة (.doc)؟

`Aspose.Words` يمكنه الحفظ إلى `.doc` أيضًا—فقط استبدل امتداد الملف في `Save`. ومع ذلك، بعض ميزات الأشكال المتقدمة (مثل التجميع) مدعومة بالكامل فقط في صيغة OOXML `.docx`.

---

## مثال كامل يعمل

انسخ‑الصق الكتلة التالية في تطبيق console جديد لتشاهد العملية كاملةً. لا توجد أجزاء مفقودة؛ هذا **مثال كامل وقابل للتنفيذ**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**الناتج المتوقع:** عند فتح `GroupShape.docx`، سترى كائنًا مجمعًا واحدًا يتكون من مستطيل أزرق فاتح وبيضاوي مرجاني فاتح، مصطفين بجانب بعضهما البعض بشكل مثالي.

---

## ملخص

لقد غطينا الآن كل ما تحتاجه **لتجميع الأشكال في Word** باستخدام Aspose.Words:

1. إنشاء مستند وباني.  
2. **إضافة شكل مستطيل** و**تعريف شكل بيضاوي** بأبعاد صريحة.  
3. (اختياري) **إدراج شكل في Word** لمعاينة سريعة.  
4. استخدام `GroupShape` لـ **كيفية تجميع الأشكال**—إضافة كل عنصر فرعي، ضبط الالتفاف، ثم الإدراج.  
5. حفظ الملف والتحقق من  

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إدراج أشكال في مستندات Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [دروس ظل الشكل في Aspose.Words – إضافة ظل إلى شكل Word في C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}