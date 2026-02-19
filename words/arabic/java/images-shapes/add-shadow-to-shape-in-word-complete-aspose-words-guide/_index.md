---
category: general
date: 2026-02-18
description: إضافة ظل إلى الشكل في Word باستخدام Aspose.Words. تعلّم كيفية تغيير لون
  الظل في Word، وتعيين الإزاحات، والضبابية، والشفافية في بضع أسطر فقط.
draft: false
keywords:
- add shadow to shape
- how to change shadow color in word
language: ar
og_description: إضافة ظل إلى الشكل في Word باستخدام Aspose.Words. يوضح هذا الدرس كيفية
  تغيير لون الظل في Word، وضبط الضبابية، والإزاحة، والشفافية.
og_title: إضافة ظل إلى الشكل في Word – دليل Aspose.Words الكامل
tags:
- Aspose.Words
- C#
- Word Automation
title: إضافة ظل إلى الشكل في Word – دليل Aspose.Words الكامل
url: /ar/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/
---

produce final output with same structure.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة ظل إلى الشكل في Word – دليل Aspose.Words الكامل

هل احتجت يومًا إلى **إضافة ظل إلى الشكل** في مستند Word لكن لم تكن متأكدًا من أين تبدأ؟ لست وحدك—فالمطورون غالبًا ما يسألون *كيف تغير لون الظل في Word* عندما يرغبون في لمسة بصرية إضافية.  

في هذا الدرس سنستعرض مثالًا واقعيًا باستخدام مكتبة Aspose.Words for .NET. في النهاية ستحصل على برنامج جاهز للتنفيذ يقوم بتحميل ملف DOCX، يحصل على الشكل الأول، ويطبق ظلًا أزرق شبه شفاف مع تمويه مخصص وإزاحات. لا اختصارات غامضة مثل “انظر إلى الوثائق”—فقط حل كامل يمكنك نسخه ولصقه.

## ما ستتعلمه

- كيفية تحميل مستند Word وتحديد عقدة الشكل.  
- استدعاءات API الدقيقة **لإضافة ظل إلى الشكل**.  
- كيفية **تغيير لون الظل في Word**، وتعيين نصف قطر التمويه، وإزاحات X/Y، والشفافية.  
- نصائح للتعامل مع أشكال متعددة، والظلال الموجودة، وإصدارات Word.  

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يُترجم مع الإصدارات السابقة، لكن يُنصح بـ .NET 6).  
- حزمة NuGet الخاصة بـ Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- فهم أساسي للغة C# ونموذج كائنات Word.  

إذا كان لديك هذه المتطلبات، لنبدأ.

---

## الخطوة 1 – تحميل مستند Word الذي يحتوي على الشكل

أولاً نقوم بإنشاء كائن `Document` يشير إلى ملف المصدر الخاص بنا. يمكن أن يكون المسار مطلقًا أو نسبيًا للملف التنفيذي.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the DOCX that already contains at least one shape.
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **لماذا هذا مهم:** فئة `Document` هي نقطة الدخول لجميع عمليات Aspose.Words. تحميل الملف مرة واحدة يقلل من استهلاك الذاكرة ويسمح لنا باستعلام شجرة العقد بكفاءة.

## الخطوة 2 – استرجاع أول عقدة شكل

الأشكال تعيش داخل تسلسل العقد في المستند. نطلب أول عقدة من النوع `NodeType.SHAPE`. العلم `true` يعني “بحث عميق”. 

```csharp
// Grab the first Shape object in the document (depth‑first search).
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (firstShape == null)
{
    System.Console.WriteLine("No shape found in the document.");
    return;
}
```

> **نصيحة احترافية:** إذا كنت بحاجة لاستهداف شكل معين، قم بالترشيح باستخدام `firstShape.Name` أو `firstShape.AlternativeText` بدلاً من أخذ الأول دائمًا.

## الخطوة 3 – الحصول على كائن الظل المرتبط بالشكل

كل `Shape` يحتوي على خاصية `Shadow` قد تكون `null` إذا لم يكن هناك ظل بعد. الوصول إليها يمنحنا كائن `Shadow` قابل للتعديل.

```csharp
// The Shadow object is automatically created if it doesn't exist.
Shadow shapeShadow = firstShape.Shadow;
```

> **حالة حافة:** ملفات Word القديمة (قبل 2007) أحيانًا تخزن الظلال بطريقة مختلفة. Aspose.Words يطبع ذلك إلى شكل موحد، لذا تعمل نفس API عبر DOC و DOCX وحتى RTF.

## الخطوة 4 – تحديد نصف قطر التمويه (بالنقاط)

نصف قطر تمويه بقيمة `5.0` نقاط يعطي حافة ناعمة دون أن تبدو مشوشة.

```csharp
shapeShadow.BlurRadius = 5.0;   // points
```

## الخطوة 5 – تعيين الإزاحات الأفقية والعمودية

الإزاحات تحرك الظل بالنسبة إلى الشكل. القيم الموجبة تحركه إلى اليمين/الأسفل؛ القيم السالبة تحركه إلى اليسار/الأعلى.

```csharp
shapeShadow.OffsetX = 3.0;      // move right 3 points
shapeShadow.OffsetY = 3.0;      // move down 3 points
```

## الخطوة 6 – اختيار لون أزرق للظل  

هنا نوضح **كيفية تغيير لون الظل في Word** باستخدام `System.Drawing.Color`.

```csharp
shapeShadow.Color = Color.Blue;   // any System.Drawing.Color works
```

> **لماذا اللون مهم:** الظل الأزرق يمكن أن يعطي إحساسًا باردًا ومؤسسيًا، بينما اللون الرمادي الداكن أكثر حيادية. اختر ما يتناسب مع هوية علامتك التجارية.

## الخطوة 7 – تعديل شفافية الظل

الشفافية تتراوح بين `0.0` (غير مرئي) إلى `1.0` (معتم بالكامل). سنستخدم `0.6` لتأثير خفيف.

```csharp
shapeShadow.Opacity = 0.6;   // 60% opacity
```

## الخطوة 8 – حفظ المستند المعدل

أخيرًا، اكتب التغييرات إلى القرص. يمكنك استبدال الملف الأصلي أو إنشاء ملف جديد.

```csharp
doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
System.Console.WriteLine("Shadow applied and document saved.");
```

### مثال كامل يعمل

بجمع كل ذلك معًا، إليك البرنامج الكامل الذي يمكنك نسخه ولصقه وتشغيله:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class AddShadowToShapeDemo
{
    static void Main()
    {
        // 1️⃣ Load the document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Find the first shape
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (firstShape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Get (or create) the shadow object
        Shadow shapeShadow = firstShape.Shadow;

        // 4️⃣ Set blur radius
        shapeShadow.BlurRadius = 5.0;

        // 5️⃣ Set offsets
        shapeShadow.OffsetX = 3.0;
        shapeShadow.OffsetY = 3.0;

        // 6️⃣ Change shadow color (how to change shadow color in Word)
        shapeShadow.Color = Color.Blue;

        // 7️⃣ Set opacity
        shapeShadow.Opacity = 0.6;

        // 8️⃣ Save the result
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
        System.Console.WriteLine("Shadow applied and document saved.");
    }
}
```

**النتيجة المتوقعة:** افتح `output_with_shadow.docx` في Microsoft Word. الآن يعرض الشكل الأول ظلًا أزرقًا ناعمًا، مُزاح 3 pt إلى اليمين والأسفل، مع تمويه معتدل وشفافية 60 %.

---

## التعامل مع أشكال متعددة

إذا كان مستندك يحتوي على عدة رسومات، قم بالتكرار عبرها:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shp in shapes)
{
    // Apply the same shadow settings to each shape
    shp.Shadow.BlurRadius = 5.0;
    shp.Shadow.OffsetX = 3.0;
    shp.Shadow.OffsetY = 3.0;
    shp.Shadow.Color = Color.Blue;
    shp.Shadow.Opacity = 0.6;
}
```

> **ملاحظة:** هذه الطريقة تستبدل أي إعداد ظل موجود. إذا كنت بحاجة للحفاظ على الإعدادات الأصلية، قم باستنساخ كائن `Shadow` أولاً.

## الأخطاء الشائعة والنصائح

| المشكلة | كيفية تجنبه |
|---------|-----------------|
| **Null `Shape`** – المستند لا يحتوي على رسومات. | تحقق دائمًا من `null` بعد `GetChild`. |
| **Shadow already exists** – قد تقوم بالكتابة فوق نمط مخصص عن غير قصد. | اقرأ خصائص `shapeShadow` الحالية قبل تعديلها. |
| **Incorrect color space** – استخدام `System.Drawing.Color` مع نسخة Word أقدم قد يؤدي إلى ألوان غير متوقعة. | التزم بالألوان القياسية أو عرّف ARGB يدويًا (`Color.FromArgb(255, 0, 0, 255)`). |
| **Performance hit on large docs** – التكرار عبر آلاف العقد قد يكون بطيئًا. | استخدم `doc.GetChildNodes(NodeType.Shape, false)` إذا كنت تحتاج فقط إلى الأشكال ذات المستوى الأعلى. |

## ماذا لو أردت تأثير ظل مختلف؟

- **حواف صلبة:** عيّن `BlurRadius = 0`.  
- **إزاحة أكبر:** زد `OffsetX`/`OffsetY` إلى 10 pt أو أكثر.  
- **شفافية مختلفة:** استخدم قيم مثل `0.3` لتوهج خفيف أو `0.9` لمظهر جريء.  
- **ظلال متدرجة:** Aspose.Words لا يدعم الظلال المتدرجة مباشرة؛ ستحتاج إلى إدراج صورة ذات تأثير مسبق.  

## التحقق من النتيجة برمجيًا

أحيانًا قد ترغب في تأكيد إعدادات الظل دون فتح Word:

```csharp
Shadow s = firstShape.Shadow;
System.Console.WriteLine($"Blur: {s.BlurRadius}, OffsetX: {s.OffsetX}, OffsetY: {s.OffsetY}, " +
                         $"Color: {s.Color}, Opacity: {s.Opacity}");
```

إذا طبع الطرفية الأرقام التي ضبطتها، فأنت تعلم أن استدعاء API نجح.

## الخلاصة

لقد أظهرنا **كيفية إضافة ظل إلى الشكل** في مستند Word باستخدام Aspose.Words، ووضحنا **كيفية تغيير لون الظل في Word** مع التمويه والإزاحة والشفافية. الكود الكامل القابل للتنفيذ أعلاه يتيح لك إضافة ظل إلى أي شكل في ثوانٍ، بينما النصائح الإضافية تحميك من الأخطاء الشائعة.  

هل أنت مستعد للتحدي التالي؟ جرّب تطبيق ألوان مختلفة على أشكال منفردة، أو دمج الظلال مع الانعكاسات للحصول على تأثير بصري أغنى. يمكنك أيضًا استكشاف فئة `ShapeStyle` في Aspose.Words لتعديل سمك الخط، أنماط التعبئة، أو الدوران ثلاثي الأبعاد.  

إذا وجدت هذا الدليل مفيدًا، شاركه مع زملائك، ضع نجمة على مستودع Aspose.Words، أو اترك تعليقًا بتجاربك الخاصة. برمجة سعيدة!  

![شكل Word بظل أزرق – مثال إضافة ظل إلى الشكل](https://example.com/images/shape-shadow.png "مثال إضافة ظل إلى الشكل")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}