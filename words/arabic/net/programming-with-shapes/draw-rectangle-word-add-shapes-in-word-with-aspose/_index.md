---
category: general
date: 2026-07-29
description: ارسم مستطيل في Word باستخدام Aspose.Words. تعلّم كيفية إضافة شكل مستطيل،
  وإضافة شكل خط، وإدارة عدة أشكال في مستند واحد.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: ar
lastmod: 2026-07-29
og_description: ارسم مستطيل في Word باستخدام Aspose.Words. اتبع هذا الدليل خطوة بخطوة
  لإضافة شكل مستطيل، وإضافة شكل خط، والعمل مع أشكال متعددة في Word بسهولة.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: رسم مستطيل في وورد – إتقان إضافة الأشكال في وورد
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: رسم مستطيل في وورد – إضافة أشكال في وورد باستخدام Aspose
url: /ar/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – الدليل الكامل لإضافة الأشكال في Word

هل تساءلت يومًا كيف **draw rectangle word** المستندات دون فتح الواجهة كل مرة؟ أنت لست وحدك. يحتاج العديد من المطورين إلى إنشاء ملفات Word في الوقت الفعلي، وأسهل طريقة هي السماح لمكتبة بالقيام بالعمل الشاق. في هذا الدرس سنوضح لك بالضبط **كيفية إضافة الأشكال** — تحديدًا مستطيل وخط — باستخدام Aspose.Words for .NET، وسنركز على العبارة *draw rectangle word* حتى لا تضيع.

تخيلها كاستوديو فن صغير يعيش داخل كودك. بحلول النهاية ستتمكن من **add rectangle shape**، **add line shape**، وحتى دمجها في مجموعات **multiple shapes word**. لا واجهة مستخدم، لا تعديل يدوي، فقط C# نظيف وقابل للتكرار.

## ما ستتعلمه

- إعداد مستند Word جديد باستخدام Aspose.Words.  
- إنشاء **GroupShape** يمكنه احتواء عدة كائنات.  
- **Add rectangle shape** و **add line shape** داخل تلك المجموعة.  
- إدراج الأشكال المجمعة في جسم المستند.  
- حفظ الملف ورؤية النتيجة فورًا.  

إذا كنت مرتاحًا مع C# الأساسي ولديك نسخة من Aspose.Words، فأنت جاهز. لا تحتاج إلى حزم NuGet إضافية بخلاف المكتبة الأساسية.

> **نصيحة احترافية:** Aspose.Words يعمل مع .NET 6، .NET 7، و .NET Framework 4.6+. اختر بيئة التشغيل التي تتطابق مع مشروعك.

![draw rectangle word example](https://example.com/placeholder-image.png "draw rectangle word – grouped shapes in a Word file")

## draw rectangle word – إعداد المستند

قبل أن نتمكن من **draw rectangle word** نحتاج إلى لوحة نظيفة. فئة `Document` هي تلك اللوحة؛ و`DocumentBuilder` هو فرشاتنا.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

السطران أعلاه يمنحاننا ملف `.docx` جديد في الذاكرة. لا شيء يُكتب إلى القرص بعد، مما يعني أنه بإمكاننا التجربة دون إغراق نظام الملفات.

## كيفية إضافة الأشكال – إنشاء حاوية GroupShape

عندما تريد أن تكون **multiple shapes word** ككيان واحد—تتحرك معًا، تدور معًا—تقوم بلفها داخل `GroupShape`. فكر في المجموعة كملف يحتوي على أشكال أخرى.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

لماذا مجموعة؟ لأنه لاحقًا قد ترغب في **add rectangle shape** و **add line shape** ثم تحريكهما معًا. بدون مجموعة، سيتعين عليك إعادة وضع كل شكل على حدة.

## add rectangle shape – إدراج مستطيل داخل المجموعة

الآن بعد أن الحاوية موجودة، دعنا **add rectangle shape**. المستطيل هو `Shape` يكون `ShapeType` الخاص به هو `Rectangle`.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

لاحظ أن قيم `Left` و `Top` نسبية إلى أصل المجموعة، وليس إلى الصفحة. هذا يجعل من السهل محاذاة الأشكال بدقة. سيظهر المستطيل بالقرب من الزاوية العلوية اليسرى للمجموعة.

## add line shape – إضافة خط إلى نفس المجموعة

الخط هو مجرد `Shape` آخر، لكن `ShapeType` الخاص به هو `Line`. سنضعه أسفل المستطيل.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

نظرًا لأن ارتفاع الخط صفر، فإن خاصية `Top` تحدد موضع الخط عموديًا. تتحكم `Width` في طول الخط أفقيًا.

## multiple shapes word – إدراج المجموعة في جسم المستند

لدينا مجموعة الآن تحتوي على **add rectangle shape** و **add line shape**. الخطوة النهائية هي وضع الكل في المستند.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` يضع المجموعة بالضبط حيث يكون `DocumentBuilder` موجودًا حاليًا. إذا كنت تحتاجها في فقرة محددة، حرك الـ builder باستخدام `builder.MoveToParagraph(index)` أولاً.

## حفظ النتيجة – رؤية مخرجات draw rectangle word

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

افتح الملف المُولد في Microsoft Word وسترى مجموعة واحدة تحتوي على مستطيل وخط. يمكنك النقر على المجموعة، سحبها، أو حتى تغيير حجمها—جميع الأشكال تتحرك معًا. هذه هي قوة **multiple shapes word**.

### النتيجة المتوقعة

- ملف `.docx` باسم `GroupShape.docx`.  
- صفحة واحدة تحتوي على مستطيل مجمع (120 × 80 pt) بالقرب من الزاوية العلوية اليسرى.  
- خط أفقي (150 pt طول) موضعه مباشرة أسفل المستطيل.  
- كلا الشكلين قابلان للتحديد ككائن واحد.

إذا نقرت المجموعتين مزدوجًا، سيسمح لك Word بتحرير كل شكل على حدة—مثالي للتعديل الدقيق.

## أسئلة شائعة وحالات خاصة

**ماذا لو احتجت إلى أكثر من شكلين؟**  
استمر في استدعاء `group.AppendChild(yourShape)` لكل كائن إضافي. يمكن للمجموعة احتواء أي عدد من الأشكال، مما يجعلها مثالية للمخططات المعقدة.

**هل يمكنني تغيير لون تعبئة المستطيل؟**  
بالطبع. بعد إنشاء المستطيل، عيّن `rectangle.FillColor = System.Drawing.Color.LightBlue;`. هذا يعمل مع أي شكل يدعم التعبئة.

**هل يجب تعيين `Height = 0` للخط؟**  
نعم، للخط الأفقي المستقيم يجب أن يكون الارتفاع صفرًا. للخط العمودي، عيّن `Width = 0` ومنح `Height` قيمة موجبة.

**هل سيعمل هذا مع ملفات .doc (Word 97‑2003)؟**  
يمكن لـ Aspose.Words حفظ إلى صيغة `.doc` القديمة، لكن قد تكون بعض ميزات الأشكال الحديثة محدودة. استخدم `.docx` للحصول على كامل الدقة.

**كيف أقوم بتدوير المجموعة بأكملها؟**  
يمكنك تعيين `group.Rotation = 45;` (درجة) قبل إدراجها. التدوير ينطبق على كل شكل فرعي.

## ملخص – كيفية إضافة الأشكال في Word برمجيًا

- يبدأ **draw rectangle word** بإنشاء `Document` و `DocumentBuilder`.  
- بناء **GroupShape** لاحتواء **multiple shapes word**.  
- يتم إلحاق **add rectangle shape** و **add line shape** بالمجموعة.  
- إدراج المجموعة في الجسم باستخدام `builder.InsertNode`.  
- حفظ الملف وفتحه للتحقق من النتيجة البصرية.

هذه هي سير العمل بالكامل، مغلفة في قائمة شفرة واحدة سهلة القراءة.

## الخطوات التالية والمواضيع ذات الصلة

الآن بعد أن تعرف **how to add shapes**، فكر في استكشاف:

- **add rectangle shape** مع زوايا مستديرة (`ShapeType.Rectangle` + `CornerRadius`).  
- تنسيق الخطوط بأنماط متقطعة مختلفة (`line.LineFormat.DashStyle`).  
- تضمين الصور جنبًا إلى جنب مع الأشكال لتقارير أكثر غنى.  
- استخدام **multiple shapes word** لبناء مخططات تدفق أو مخططات UML بسيطة.  

كل من هذه المواضيع يبني بشكل طبيعي على الأساس الذي وضعناه هنا، وجميعها يتبع نفس نمط إنشاء الأشكال، تكوينها، وتجميعها إذا لزم الأمر.

---

برمجة سعيدة! إذا واجهت أي مشاكل أو كان لديك حالة استخدام رائعة لتشاركها، اترك تعليقًا أدناه. ملاحظاتك تساعدنا جميعًا على إتقان فن **draw rectangle word** وما بعده.

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شفرات كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}