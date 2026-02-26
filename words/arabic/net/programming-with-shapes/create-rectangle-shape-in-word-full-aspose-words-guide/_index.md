---
category: general
date: 2026-02-26
description: إنشاء شكل مستطيل في Word باستخدام Aspose.Words وتعلم كيفية إضافة الشكل
  إلى Word، وتطبيق الظل على الشكل، وتعيين شفافية الشكل في دقائق.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: ar
og_description: إنشاء شكل مستطيل في Word باستخدام Aspose.Words. تعلم كيفية إضافة الشكل
  إلى Word، وتطبيق الظل على الشكل، وتعيين شفافية الشكل بسرعة.
og_title: إنشاء شكل مستطيل في Word – دليل Aspose.Words الكامل
tags:
- Aspose.Words
- C#
- Word Automation
title: إنشاء شكل مستطيل في Word – دليل Aspose.Words الكامل
url: /ar/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل في Word – دليل Aspose.Words الكامل

هل احتجت يوماً إلى **create rectangle shape** في مستند Word لكنك لم تكن متأكدًا من أين تبدأ؟ لست وحدك—العديد من المطورين يواجهون هذه المشكلة عند أتمتة التقارير أو الفواتير. في هذا الدرس سنستعرض مثالًا كاملاً جاهزًا للتنفيذ يوضح لك كيفية **add shape to Word**، تطبيق ظل خفيف، والتحكم في شفافية الشكل، كل ذلك باستخدام Aspose.Words for .NET.

في نهاية الدليل ستحصل على ملف `.docx` يحتوي على مستطيل نظيف بظل مصقول—مثالي للعلامة التجارية، الإبرازات، أو مجرد إضفاء مظهر أكثر احترافية على مستندك. لا تحتاج إلى أدوات خارجية، فقط بضع أسطر من C#.

## ما الذي ستحتاجه

- **Aspose.Words for .NET** (أحدث نسخة حتى أوائل 2026). يمكنك الحصول عليها من NuGet (`Install-Package Aspose.Words`).
- بيئة تطوير .NET (Visual Studio، Rider، أو VS Code مع امتداد C#).
- إلمام أساسي بصياغة C#—لا شيء معقد، مجرد عبارات `using` وإنشاء الكائنات المعتادة.

إذا كان لديك كل ذلك، رائع—لنبدأ.

## إنشاء شكل مستطيل – الخطوات الأساسية

فيما يلي الشيفرة الكاملة. انسخ‑الصقها في مشروع console جديد، اضغط **F5**، وستظهر لك `ShadowDemo.docx` في المجلد الذي تحدده.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### لماذا يعمل هذا

- **`Document`** هو نقطة الدخول؛ يمثل ملف Word بالكامل.
- **`Shape`** مع `ShapeType.Rectangle` يخبر Aspose أننا نريد كائن رسم مستطيل.
- ضبط **`Width`** و **`Height`** يمنح الشكل حجمًا محددًا؛ وإلا سيظهر كعنصر نائب صغير.
- كائن **`Shadow`** يتيح لنا ضبط كل جانب بصري: التمويه، المسافة، الاتجاه، اللون، الشفافية، والانتشار. هذا هو جوهر *apply shadow to shape*.
- أخيرًا، **`AppendChild`** يضيف الشكل إلى الفقرة الأولى في المستند، وهي أبسط طريقة لـ *add shape to Word* دون الحاجة للتعامل مع الجداول أو الرؤوس.

عند فتح `ShadowDemo.docx`، ستلاحظ مستطيلًا رماديًا يجلس بشكل مريح في المستند، وظله يميل إلى الأسفل‑اليمين بزاوية 45°. الظل ليس كتلة صلبة؛ نصف قطر التمويه ينعّم الحواف، والشفافية تجعل الظل يبدو كظل طبيعي وليس تغطية قاسية.

![create rectangle shape example](image.png "create rectangle shape with shadow in Word using Aspose.Words")

*(الصورة أعلاه تُظهر النتيجة النهائية لمقتطف الشيفرة.)*

## إضافة شكل إلى مستند Word – خيارات الموضع

يستخدم المثال **الفقرة الأولى** لأنها أسرع طريقة لرؤية شيء على الشاشة. في السيناريوهات الواقعية قد ترغب في:

- إدراج الشكل في **قسم** أو **رأس/تذييل** محدد.
- وضعه داخل **خلية جدول** لتنسيقه مع البيانات الجدولية.
- تغليفه بخيارات **تغليف النص** (مثل `WrapType.Square`) بحيث يلتف النص المحيط حول المستطيل.

إليك تعديل سريع يضع الشكل في فقرة جديدة مع نمط مخصص:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*نصيحة محترف:* دائمًا أضف الشكل **بعد** ضبط خصائصه؛ وإلا قد تحتاج إلى استدعاء `UpdateLayout` لتحديث المظهر البصري.

## تطبيق ظل على الشكل – ضبط المظهر بدقة

يمكن للظلال أن تغير مظهر المستند بشكل كبير. تُظهر فئة `Shadow` عدة خصائص:

| الخاصية          | ما الذي تتحكم فيه                                 | القيم النموذجية |
|------------------|---------------------------------------------------|----------------|
| `BlurRadius`     | نعومة حواف الظل                                   | 2.0 – 10.0     |
| `Distance`       | المسافة التي يُبعد فيها الظل عن الشكل            | 1.0 – 8.0      |
| `Direction`      | الزاوية بالدرجات (0 = اليسار، 90 = الأعلى)       | 0 – 360        |
| `Color`          | لون الظل (أي `System.Drawing.Color`)             | رمادي، أسود، مخصص |
| `Transparency`   | الشفافية (0 = معتم بالكامل، 1 = شفاف تمامًا)      | 0.0 – 0.5      |
| `Spread`         | توسع الظل قبل تطبيق التمويه                     | 0.0 – 1.0      |

إذا أردت مظهرًا **دقيقًا واحترافيًا**، حافظ على `BlurRadius` بين 4‑6 و `Transparency` حوالي 0.2، تمامًا كما في الشيفرة أعلاه. للحصول على **تأثير دراماتيكي**، زد `Distance` إلى 6، اضبط `Direction` على 135°، وخفض `Transparency` إلى 0.05.

## ضبط شفافية الشكل وانتشار الظل

الشفافية لا تقتصر على الظل فقط؛ يمكنك أيضًا جعل المستطيل نفسه شبه شفاف:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

دمج تعبئة شبه شفافة مع ظل ناعم غالبًا ما يمنح مظهرًا حديثًا—ممتازًا للوحة معلومات أو نماذج تصميم مدمجة في التقارير.

### حالات خاصة يجب الانتباه إليها

1. **إصدارات Word القديمة** (قبل 2007) لا تدعم بعض خصائص الظل. إذا كنت تستهدف ملفات `.doc`، فكر في تبسيط الظل (مثلاً، اضبط `BlurRadius` إلى 0).
2. **الشاشات ذات الكثافة العالية DPI** قد تعرض الظل بشكل مختلف قليلًا. اختبر على البيئة المستهدفة إذا كانت الدقة البصرية حرجة.
3. **الأشكال المتداخلة**—Aspose يرسم الظلال بترتيب الإضافة. أضف الأشكال من الخلف إلى الأمام لتجنب التغطية غير المرغوبة.

## حفظ النتيجة والتحقق منها

طريقة `Document.Save` تكتشف تلقائيًا تنسيق الإخراج من امتداد الملف. لملف **`.docx`** ستحصل على تنسيق Open XML، الذي تفهمه معظم معالجات Word الحديثة. إذا احتجت نسخة **PDF** بنفس النمط البصري، فقط غيّر الامتداد:

```csharp
document.Save("ShadowDemo.pdf");
```

فتح `ShadowDemo.docx` (أو `ShadowDemo.pdf`) يجب أن يُظهر **مستطيلًا بظل**، مما يؤكد أنك نجحت في *create rectangle shape* و *apply shadow to shape* باستخدام Aspose.Words.

## الأسئلة المتكررة

**س: هل يمكنني استخدام شكل مختلف، مثل إهليلج؟**  
ج: بالتأكيد. استبدل `ShapeType.Rectangle` بـ `ShapeType.Ellipse` (أو أي قيمة أخرى من تعداد `ShapeType`). تظل خصائص الظل كما هي.

**س: ماذا لو أردت أن يكون المستطيل قابلًا للنقر؟**  
ج: يمكنك إرفاق ارتباط تشعبي بالشكل:

```csharp
rectangleShape.Href = "https://example.com";
```

**س: هل يعمل هذا على .NET 6+؟**  
ج: نعم. Aspose.Words 23.11 وما بعدها يدعم بالكامل .NET 6، .NET 7، و .NET 8. فقط أشر إلى حزمة NuGet المناسبة.

**س: كيف أغيّر لون الظل ليتطابق مع علامتي التجارية؟**  
ج: استخدم أي `System.Drawing.Color` تفضله:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## الخلاصة

غطينا كل ما تحتاجه **create rectangle shape** في مستند Word، **add shape to Word**، **apply shadow to shape**، و **set shape transparency**. الشيفرة الكاملة القابلة للتنفيذ موجودة في أعلى هذه الصفحة، والتوضيحات تمنحك الثقة لتعديل الأحجام، الألوان، ومعاملات الظل لأي مشروع.

هل أنت مستعد للخطوة التالية؟ جرّب التجربة مع:

- أشكال متعددة مكدسة معًا للحصول على تأثير شارة.
- ضبط الحجم ديناميكيًا بناءً على محتوى المستند (مثلاً، حساب العرض من عمود جدول).
- تصدير المستند إلى PDF أو HTML مع الحفاظ على الظل.

لا تتردد في ترك تعليق إذا واجهت أي صعوبات، أو مشاركة تعديلاتك على موضوع “المستطيل مع الظل”.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}