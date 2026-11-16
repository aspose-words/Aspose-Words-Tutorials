---
category: general
date: 2026-11-15
description: تعلم كيفية إدراج شكل في مستند Word وتجميع أشكال متعددة باستخدام Aspose.Words
  DocumentBuilder. يتضمن أمثلة على إدراج شكل مستطيل وإدراج أشكال متعددة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: ar
lastmod: 2026-11-15
og_description: كيفية إدراج شكل في ملف Word باستخدام Aspose.Words. يغطي هذا الدليل
  تجميع أشكال متعددة، وإدراج شكل مستطيل، وإضافة أشكال متعددة بكفاءة.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: كيفية إدراج شكل وتجميع أشكال متعددة باستخدام DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: كيفية إدراج شكل وتجميع أشكال متعددة باستخدام DocumentBuilder في C#
url: /ar/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إدراج شكل وتجميع أشكال متعددة باستخدام DocumentBuilder في C#

إذا كنت بحاجة إلى معرفة **how to insert shape** في مستند Word باستخدام Aspose.Words، فإن هذا الدليل يوضح لك الخطوات الدقيقة. ستتعلم أيضًا كيفية **group multiple shapes** بحيث تتصرف ككائن واحد، وكيفية **insert rectangle shape** إلى جانب رسومات أخرى.

غالبًا ما تتطلب أتمتة المستندات إضافة عدة رسومات—مخططات، شعارات، توضيحات—مع الحفاظ على تنظيمها. بنهاية هذا الدرس ستتمكن من **insert multiple shapes**، وضعها داخل مجموعة، وحفظ تخطيط نظيف وقابل لإعادة الاستخدام.

## المتطلبات المسبقة

* .NET 6.0 أو أحدث مثبت  
* Visual Studio 2022 (أو أي بيئة تطوير C#)  
* ترخيص Aspose.Words لـ .NET أو مفتاح تقييم مجاني  
* إلمام أساسي بـ C# وفئة Aspose.Words `DocumentBuilder`  

أنت **لا** تحتاج إلى أي مكتبات طرف ثالث أخرى؛ كل ما يلزم هو جزء من Aspose.Words.

## الخطوة 1: تثبيت Aspose.Words عبر NuGet

افتح مشروعك في Visual Studio وشغّل الأمر التالي في نافذة Package Manager Console:

```powershell
Install-Package Aspose.Words
```

تتضمن الحزمة الفئات `DocumentBuilder` و `Shape` و `GroupShape` المستخدمة طوال هذا الدرس.

## الخطوة 2: إنشاء كائن DocumentBuilder – الأساس لـ **how to insert shape**

السطر الأول القابل للتنفيذ في الشيفرة هو إنشاء `DocumentBuilder`. هذا الكائن يمنحك وصولًا مباشرًا إلى شجرة المستند، مما يتيح لك وضع الأشكال بالضبط حيث تريد.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*لماذا هذا مهم*: `DocumentBuilder` يحافظ على مؤشر (نقطة الإدراج). كل استدعاء `Insert...` لاحق يستخدم هذا المؤشر، وهذا هو السبب في أننا ننتقل به لاحقًا إلى `GroupShape` للحفاظ على جميع الأشكال معًا.

## الخطوة 3: **Insert rectangle shape** – الرسمة الأولى التي ستضيفها

المستطيل هو عنصر نائب شائع للجداول أو الصور أو التوضيحات. استخدم `InsertShape` مع `ShapeType.Rectangle` وحدد العرض والارتفاع بالنقاط (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

يظهر المستطيل في موقع المؤشر الحالي. يمكنك تخصيص التعبئة أو نمط الخط أو النص لاحقًا إذا لزم الأمر.

## الخطوة 4: إدراج شكل آخر – إهليلج لتنوع بصري

إضافة أكثر من شكل واحد يوضح **insert multiple shapes**. سيظهر الإهليلج بعد المستطيل في تدفق المستند.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

في هذه المرحلة يحتوي المستند على شكلين مستقلين. إذا قمت بتحريك المؤشر أو إضافة نص، ستبقى الأشكال في موضعها الذي تم إدراجها فيه.

## الخطوة 5: **Group multiple shapes** لتعمل كوحدة واحدة

التجميع ضروري عندما تحتاج إلى تحريك أو تدوير أو تنسيق عدة رسومات معًا. الشيفرة التالية تنشئ `GroupShape`، تنقل مؤشر الـ builder إلى داخله، ثم تُدرج الأشكال نفسها مرة أخرى—هذه المرة تصبح أبناء للمجموعة.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### لماذا نستخدم مجموعة؟

* **تحويل بنقطة واحدة** – تدوير أو تغيير حجم المجموعة بأكملها باستدعاء واحد.  
* **تنظيم منطقي** – شجرة مستند Word تعكس التجميع، مما يجعل التعديلات اللاحقة أسهل.  
* **تخطيط متسق** – تحريك المجموعة يحافظ على المواقع النسبية لأبنائها.

### إضافة المزيد من الأشكال – توسيع **insert multiple shapes** داخل المجموعة

يمكنك الاستمرار في استدعاء `InsertShape` بينما يبقى المؤشر داخل `GroupShape`. على سبيل المثال، لإضافة مثلث:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

كل استدعاء يحترم سياق المجموعة، لذا يصبح المثلث تلقائيًا جزءًا من نفس المجموعة.

## الخطوة 6: حفظ المستند والتحقق من النتيجة

بعد وضع جميع الأشكال، احفظ المستند إلى ملف `.docx`. فتح الملف في Microsoft Word (أو أي عارض متوافق) يجب أن يظهر شكلين منفصلين يليهما كتلة مجموعة تحتوي على نفس المستطيل والإهليلج والمثلث.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### النتيجة المتوقعة

* **الشكلان الأولان** – مستطيل وإهليلج موضعين بشكل مستقل على الصفحة.  
* **كتلة المجموعة** – مستطيل وإهليلج ومثلث يتحركون معًا عندما تنقر على أيٍ منهم في Word.

يمكنك اختبار التجميع عن طريق تحديد أي شكل داخل المجموعة؛ سيقوم Word بتمييز المجموعة بالكامل، مؤكدًا أن عملية **group multiple shapes** نجحت.

## المشكلات الشائعة ونصائح الخبراء

| المشكلة | سبب حدوثها | الحل |
|-------|----------------|-----|
| الأشكال تظهر خارج الصفحة المقصودة | لم يتم نقل مؤشر الـ builder إلى `GroupShape` قبل الإدراج. | دائمًا استدعِ `builder.MoveTo(group)` **قبل** أي استدعاءات `InsertShape` التي تنتمي إلى المجموعة. |
| المجموعة تختفي بعد الحفظ | تم إدراج المجموعة دون إضافتها إلى مجموعة العقد في المستند. | استخدم `builder.InsertNode(group)` فورًا بعد إنشاء `GroupShape`. |
| حجم غير متوقع بسبب DPI المستند | Aspose.Words يستخدم النقاط؛ إذا فكرت بالبيكسل قد تحصل على أبعاد غير متطابقة. | حوّل البيكسل إلى نقاط (`points = pixels * 72 / 96`) أو اعمل مباشرة بالنقاط. |
| تداخل الأشكال غير مقصود | لم يتم تعيين موضع صريح؛ Word يضعها بشكل متسلسل. | عيّن `Shape.Left` و `Shape.Top` بعد الإدراج للتحكم في الموضع الدقيق. |

**نصيحة احترافية:** بعد التجميع، يمكنك استرجاع مجموعة `Shapes` الخاصة بالمجموعة (`group.Shapes`) للتكرار، إعادة التسمية، أو تطبيق تنسيق جماعي.

## الخطوة 7: توسيع المثال – ما التالي؟

الآن بعد أن عرفت **how to insert shape**، **insert rectangle shape**، و **group multiple shapes**، يمكنك استكشاف:

* **تحريك الأشكال المجمعة** – ضبط خصائص الدوران أو الانعكاس على المجموعة.  
* **تطبيق الأنماط** – استخدم `Shape.FillColor`، `Shape.LineFormat`، أو `Shape.TextBox` لإضافة تسميات.  
* **التصدير إلى PDF** – نفس تخطيط المجموعة يُظهر بشكل صحيح عند استدعاء `doc.Save("output.pdf")`.  

جميع هذه الإضافات تعيد استخدام نفس سير عمل `DocumentBuilder`، مما يحافظ على نظافة الكود وسهولة صيانته.

## الخلاصة

أظهر هذا الدرس **how to insert shape** في مستند Word باستخدام Aspose.Words، وكيفية **insert rectangle shape**، وكيفية **group multiple shapes** لتعمل ككائن واحد. باتباع الشيفرة خطوة بخطوة، يمكنك بثقة **insert multiple shapes**، تنظيمها في مجموعات، وإنتاج مستندات احترافية برمجيًا.

لا تتردد في تجربة أنواع أشكال مختلفة، ألوان، وتحولات المجموعة. عندما تكون مستعدًا، دمج النمط في حلول تقارير أو قوالب أكبر لأتمتة تخطيطات المستندات المعقدة. برمجة سعيدة!

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [How to group shapes in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}