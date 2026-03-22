---
category: general
date: 2026-03-22
description: إنشاء شكل مستطيل في C# وإضافة ظل إلى الشكل باستخدام Aspose.Words. تعلّم
  كيفية إضافة الظل، وكيفية إنشاء المستطيل، وكيفية ضبط خصائص الظل.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: ar
og_description: إنشاء شكل مستطيل في C# وإضافة ظل إلى الشكل باستخدام Aspose.Words.
  دليل خطوة بخطوة يغطي كيفية إضافة الظل، وكيفية إنشاء المستطيل، وكيفية ضبط الظل.
og_title: إنشاء شكل مستطيل بظل في C# – دليل كامل
tags:
- Aspose.Words
- C#
- Document Automation
title: إنشاء شكل مستطيل بظل في C# باستخدام Aspose.Words
url: /ar/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل مع ظل في C# باستخدام Aspose.Words

هل احتجت يومًا إلى **create rectangle shape** في مستند Word لكنك لم تكن متأكدًا من كيفية إعطائه ظلًا خفيفًا؟ لست وحدك—العديد من المطورين يواجهون هذه المشكلة عندما يبدأون في التعامل مع أتمتة المستندات. في هذا الدليل سنستعرض بالضبط كيفية **add shadow to shape** باستخدام Aspose.Words، وسنجيب أيضًا على “**how to add shadow**”، “**how to create rectangle**”، و “**how to set shadow**” على طول الطريق.

سنبدأ بـ `Document` فارغ، نرسم مستطيلًا، نُفعّل ظله، نضبط الضبابية، المسافة، الزاوية، واللون، وأخيرًا نحفظ الملف. في النهاية ستحصل على ملف `.docx` جاهز للاستخدام يُظهر مستطيلًا رماديًا يطفو فوق الصفحة. لا غموض، مجرد كود بسيط يمكنك نسخه ولصقه في أي مشروع .NET.

## المتطلبات المسبقة

* **Aspose.Words for .NET** (أحدث إصدار حتى مارس 2026). يمكنك الحصول عليه من NuGet باستخدام `Install-Package Aspose.Words`.
* بيئة تطوير .NET – Visual Studio أو Rider أو حتى VS Code مع امتداد C# تعمل بشكل جيد.
* معرفة أساسية بـ C# – لا شيء معقد، فقط القدرة على إنشاء تطبيق Console أو WinForms.

هذا كل شيء. لا مكتبات إضافية، لا خطوات مخفية. جاهز؟ لنبدأ.

## الخطوة 1: تهيئة مستند فارغ جديد

لـ **create rectangle shape**، نحتاج أولاً إلى حاوية – كائن `Document` – الذي يمثل ملف Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

فئة `Document` هي نقطة الدخول لكل ما تقوم به Aspose.Words. فكر فيها كقماش فارغ؛ بدونها لا يمكنك إضافة أي أشكال أو جداول أو نص.

## الخطوة 2: إنشاء المستطيل الذي سيحمل الظل

الآن سنقوم بـ **how to create rectangle** عن طريق إنشاء كائن `Shape` من النوع `Rectangle`. كما نحدد حجمه بالنقاط (1 نقطة ≈ 1/72 بوصة).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

لماذا نختار 200 × 100 نقطة؟ إنه حجم مناسب للعرض – كبير بما يكفي لرؤية الظل بوضوح، ولكن ليس ضخمًا لدرجة أنه يغمر الصفحة. لا تتردد في تعديل هذه القيم لتتناسب مع تخطيطك.

## الخطوة 3: تفعيل تأثير الظل وتكوين مظهره

هذا هو جوهر الدرس: **how to add shadow** و **how to set shadow** للخصائص. تُظهر Aspose.Words كائن `Shadow` على كل شكل، مما يتيح لك تشغيل التأثير وضبط المعلمات البصرية.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** ينعّم الحواف – كلما ارتفعت القيمة كلما بدا الظل أكثر انتشارًا.
* **Distance** يدفع الظل بعيدًا عن المستطيل.
* **Angle** يحدد من أين يبدو الضوء قادمًا؛ 45° يعطي مظهرًا مائلًا وطبيعيًا.
* **Color** يتيح لك اختيار أي `System.Drawing.Color`. اللون الرمادي هو الافتراضي الآمن، لكن يمكنك اختيار `Color.Black` الجريء أو `Color.LightGray` الهادئ.

نصيحة احترافية: إذا قمت بتعيين `Enabled = false`، سيتم تجاهل جميع إعدادات الظل الأخرى، لذا تأكد دائمًا من هذه العلامة.

## الخطوة 4: إدراج الشكل في جسم المستند

مع جاهزية المستطيل وتكوين ظله، نحتاج إلى وضعه في المستند. أبسط طريقة هي إلحاقه بالفقرة الأولى من القسم الأول.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

إذا كان المستند يحتوي بالفعل على نص، يمكنك تحديد `Paragraph` معين أو حتى خلية `Table` وإدراج الشكل هناك. طريقة `AppendChild` متعددة الاستخدامات – تعمل مع أي نوع `Node`.

## الخطوة 5: حفظ المستند والتحقق من النتيجة

أخيرًا، نكتب الملف إلى القرص. غيّر المسار إلى أي مكان تفضله؛ يجب أن يكون المجلد موجودًا، وإلا ستحصل على استثناء.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

افتح الملف الناتج `ShadowedRectangle.docx` في Microsoft Word (أو LibreOffice) وسترى مستطيلًا رماديًا مع ظل حاد مائل يتجه إلى أسفل‑يمين. إذا كان الظل باهتًا جدًا، زد قيمة `BlurRadius` أو `Distance` وأعد تشغيل الكود – التجربة جزء من المتعة.

![مثال على إنشاء شكل مستطيل مع ظل](rectangle-shadow.png){alt="مثال على إنشاء شكل مستطيل مع ظل"}

### النتيجة المتوقعة

* مستند Word صفحة واحدة.
* مستطيل رمادي بحجم 200 × 100 نقطة موضعه في أعلى‑يسار الصفحة.
* ظل رمادي خفيف إزاحته 8 بكسل بزاوية 45°، مع تمويه 5 بكسل.

## كيفية إضافة ظل إلى الشكل – غوص أعمق

قد تتساءل، *“هل يمكنني تحريك الظل أو جعله يتغير بناءً على إدخال المستخدم؟”* بينما لا تدعم Aspose.Words نفسها الرسوم المتحركة، يمكنك تعديل خصائص الظل برمجيًا قبل الحفظ، مما يخلق عدة إصدارات من نفس المستند بمظهر مختلف. على سبيل المثال، التكرار عبر مجموعة من الألوان:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

هذا المقتطف الصغير يوضح **how to set shadow** بشكل ديناميكي—مفيد لإنشاء تقارير ذات طابع.

## كيفية إنشاء مستطيل – أشكال بديلة

إذا كنت بحاجة إلى مستطيل مستدير الزوايا، ما عليك سوى تغيير `ShapeType`:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

أو، للحصول على مربع مثالي، اجعل `Width` مساويًا لـ `Height`. تنطبق نفس خصائص الظل، لذا أنت مغطى بالفعل بخصوص **how to add shadow** لأي شكل تختاره.

## المشكلات الشائعة واستكشاف الأخطاء

| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| الظل لا يظهر | ترك `Shadow.Enabled` على `false` | عيّن `rectangleShape.Shadow.Enabled = true;` |
| الظل يبدو حادًا جدًا | `BlurRadius` مضبوط على 0 | زد `BlurRadius` إلى ما لا يقل عن 3 |
| المستند يرمي `FileNotFoundException` عند الحفظ | مجلد الوجهة غير موجود | أنشئ المجلد أولًا أو استخدم مسارًا صالحًا |
| الشكل غير مرئي | تم ضبط العرض/الارتفاع على 0 | تأكد من أن كلا البعدين > 0 |

## ملخص – ما أنجزناه

* **Create rectangle shape** في مستند Word جديد باستخدام Aspose.Words.  
* **Add shadow to shape** عن طريق تبديل علم `Shadow.Enabled` وضبط الضبابية، المسافة، الزاوية، واللون.  
* تم توضيح **how to add shadow**, **how to create rectangle**, و **how to set shadow** في مقتطف كود نظيف وقابل لإعادة الاستخدام.  
* تم توفير مثال كامل وجاهز للتنفيذ يمكنك لصقه في أي مشروع C#.

## ما التالي؟

الآن بعد أن أتقنت الأساسيات، فكر في استكشاف:

* **How to add shadow to images** – نفس واجهة برمجة `Shadow` تعمل مع `ShapeType.Image`.
* **Combining multiple shapes** – إنشاء مخططات تدفق أو رسوم بيانية مباشرة في Word.
* **Exporting to PDF** – استدعِ `document.Save("output.pdf")` بعد إضافة الظلال للحصول على نسخة قابلة للطباعة.

لا تتردد في تجربة ألوان وزوايا مختلفة، أو حتى تعبئات تدرجية. الـ API مرن بما يكفي لتتيح لك إنشاء مستندات ذات مظهر احترافي دون الحاجة إلى فتح Word يدويًا.

---

برمجة سعيدة! إذا واجهت أي مشاكل، اترك تعليقًا أدناه أو تحقق من منتديات Aspose.Words – المجتمع سيساعد بسرعة.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}