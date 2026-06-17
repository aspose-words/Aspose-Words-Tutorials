---
category: general
date: 2026-04-28
description: كيفية تعيين الظل على شكل بسرعة. تعلّم كيفية إضافة ظل للشكل، وتعيين لون
  الظل، وتخصيص ظل الشكل باستخدام Aspose.Words لـ .NET.
draft: false
keywords:
- how to set shadow
- add shape shadow
- set shadow color
- how to add shadow
- customize shape shadow
language: ar
og_description: كيفية تعيين الظل على شكل في C# باستخدام Aspose.Words. دليل خطوة بخطوة
  يغطي إضافة ظل الشكل، تعيين لون الظل، وتخصيص ظل الشكل.
og_title: كيفية تعيين الظل على شكل في C# – دليل كامل
tags:
- Aspose.Words
- C#
- Document Automation
title: كيفية تعيين الظل على شكل في C# – إضافة ظل للشكل بسهولة
url: /ar/java/images-shapes/how-to-set-shadow-on-a-shape-in-c-add-shape-shadow-easily/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعيين الظل على شكل في C# – إضافة ظل الشكل بسهولة

هل تساءلت يومًا **كيفية تعيين الظل** على شكل دون الغوص في وثائق API اللامتناهية؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحتاجون إلى ظل خفيف لإبراز المخطط، ومع ذلك لا يستطيعون العثور على مثال واضح يُظهر *كلا* من “ما هو” و “لماذا”.  

في هذا الدرس سنستعرض إضافة ظل لل形، تغيير لون الظل، وضبط الضبابية، الإزاحة، والشفافية — كل ذلك باستخدام Aspose.Words for .NET. في النهاية ستحصل على مقطع شفرة جاهز للتنفيذ يمكنك إدراجه في أي مشروع C#، بالإضافة إلى مجموعة من النصائح لتخصيص ظل الشكل في سيناريوهات أكثر تعقيدًا.

> **ملاحظة:** يعمل الكود مع Aspose.Words 22.9 أو أحدث ويتطلب .NET 6+ (أو .NET Framework 4.7.2+).  

![شكل بظل مخصص](shape-shadow.png "شكل بظل مخصص")

## ما ستتعلمه

- **إضافة ظل الشكل** برمجياً إلى الشكل الأول في مستند Word.  
- **تعيين لون الظل** إلى أي `System.Drawing.Color`.  
- **تخصيص ظل الشكل** عن طريق ضبط نصف قطر الضبابية، الإزاحات، والشفافية.  
- كيفية التعامل مع أشكال متعددة وإعادة ضبط إعدادات الظل إذا لزم الأمر.  

لا أدوات خارجية، لا ماكروهات Visual Basic — فقط C# نقي.

---

## المتطلبات المسبقة

| المتطلب | لماذا يهم |
|-------------|----------------|
| **Aspose.Words for .NET** (حزمة NuGet `Aspose.Words`) | يوفر الفئات `Document`، `Shape`، و `ShadowFormat` المستخدمة في المثال. |
| **.NET 6 SDK** (أو .NET Framework 4.7.2) | يضمن التوافق مع أحدث واجهة برمجة التطبيقات. |
| **ملف .docx** يحتوي على شكل واحد على الأقل (مثل مستطيل أو صورة) | الدرس يتعامل مع *أول* شكل؛ يمكنك إنشاء واحد في Word إذا لم يكن لديك. |

ثبت المكتبة باستخدام:

```bash
dotnet add package Aspose.Words
```

---

## خطوة بخطوة: كيفية تعيين الظل على شكل

### 1. تحميل مستند Word

نبدأ بفتح ملف `.docx`. يقوم مُنشئ `Document` بقراءة الملف إلى الذاكرة، مما يمنحنا وصولًا كاملًا إلى عقده.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **لماذا؟** تحميل المستند هو الأساس — بدون ذلك لا يمكنك استعراض شجرة الأشكال.

### 2. استرجاع الشكل الأول (أو أي شكل تحتاجه)

تخزن Aspose.Words الأشكال كعُقد من النوع `NodeType.SHAPE`. تسمح طريقة `GetChild` بالحصول على الشكل *n‑th*؛ هنا نأخذ الفهرس 0، أي الشكل الأول.

```csharp
// Grab the first shape in the document (depth‑first search)
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (firstShape == null)
{
    throw new InvalidOperationException("No shape found in the document.");
}
```

> **نصيحة محترف:** إذا كنت بحاجة إلى **إضافة ظل الشكل** إلى شكل محدد، استبدل الفهرس بالقيمة المناسبة أو كرر عبر `doc.GetChildNodes(NodeType.Shape, true)`.

### 3. الوصول إلى كائن تنسيق الظل

كل `Shape` يحتوي على خاصية `ShadowFormat` تُظهر جميع إعدادات الظل.

```csharp
ShadowFormat shadow = firstShape.ShadowFormat;
```

الآن يمكننا البدء في تعديل الظل.

### 4. تعيين نصف قطر الضبابية – لتنعيم الحواف

قيمة أكبر لنصف قطر الضبابية تجعل الظل يبدو أكثر انتشارًا. القيمة بوحدات النقاط (1 pt ≈ 1/72 inch).

```csharp
shadow.BlurRadius = 5.0; // 5 pt blur – looks nicely soft
```

> **متى يتم الضبط؟** إذا كان الشكل صغيرًا، قد تكون ضبابية 2–3 pt كافية؛ بالنسبة للبانرات الكبيرة، زدها إلى 8–10 pt.

### 5. تحديد الإزاحات الأفقية والرأسية

الإزاحات تتحكم في مدى إزاحة الظل عن الشكل. القيم الموجبة تحرك الظل إلى اليمين/الأسفل؛ القيم السالبة تحركه إلى اليسار/الأعلى.

```csharp
shadow.DistanceX = 3.0; // 3 pt to the right
shadow.DistanceY = 3.0; // 3 pt downwards
```

### 6. تعديل الشفافية (العتامة)

`Transparency` تتراوح بين `0.0` (معتم تمامًا) إلى `1.0` (شفاف تمامًا). قيمة تقريبًا `0.3` تعطي مظهرًا شبه شفاف وناعم.

```csharp
shadow.Transparency = 0.3; // 30 % transparent
```

### 7. اختيار لون الظل – **تعيين لون الظل** إلى أي `System.Drawing.Color`

يمكنك اختيار أي لون معرف مسبقًا أو إنشاء لون مخصص باستخدام قيم RGB.

```csharp
shadow.Color = Color.FromArgb(0, 120, 215); // A calm blue shade
```

إذا كنت تفضل ظلًا أسودًا كلاسيكيًا، استخدم ببساطة `Color.Black`.

### 8. حفظ المستند المعدل

أخيرًا، احفظ التغييرات. يمكنك استبدال الملف الأصلي أو الكتابة إلى موقع جديد.

```csharp
doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
```

---

## مثال عملي كامل (جميع الخطوات في كتلة واحدة)

انسخ‑الصق الكود التالي داخل طريقة `Main` لتطبيق كونسول. سيُترجم مباشرةً، بشرط تثبيت حزمة NuGet.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape (add shape shadow)
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found – aborting.");
            return;
        }

        // 3. Get the shadow formatting object
        ShadowFormat shadow = shape.ShadowFormat;

        // 4. Set blur radius
        shadow.BlurRadius = 5.0;

        // 5. Define offsets
        shadow.DistanceX = 3.0;
        shadow.DistanceY = 3.0;

        // 6. Adjust transparency (0 = opaque, 1 = fully transparent)
        shadow.Transparency = 0.3;

        // 7. Set shadow color (set shadow color)
        shadow.Color = Color.GetBlue(); // or any custom color

        // 8. Save the result
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");

        System.Console.WriteLine("Shadow applied successfully!");
    }
}
```

**النتيجة المتوقعة:** افتح `output_with_shadow.docx` في Word؛ سيظهر الشكل الأول الآن بظل أزرق ناعم، إزاحة 3 pt، ضبابية خفيفة وشفافية 30 %.

---

## تنوعات شائعة وحالات حافة

### إضافة ظلال إلى *جميع* الأشكال

إذا كان مستندك يحتوي على عدة مخططات، قد ترغب في تكرار العملية على كل شكل:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    ShadowFormat sf = s.ShadowFormat;
    sf.BlurRadius = 4.0;
    sf.DistanceX = 2.0;
    sf.DistanceY = 2.0;
    sf.Transparency = 0.25;
    sf.Color = Color.Gray;
}
```

### إعادة ضبط الظل

أحيانًا يكون لل形 ظل مسبق تحتاج إلى إزالته. اضبط `ShadowFormat.Visible` إلى `false`:

```csharp
shape.ShadowFormat.Visible = false;
```

### استخدام لون مخصص مع ألفا (نصف شفاف)

```csharp
shadow.Color = Color.FromArgb(128, 255, 0, 0); // 50 % transparent red
```

### ملاحظة التوافق

واجهة `ShadowFormat` مستقرة عبر إصدارات Aspose.Words، لكن الإصدارات القديمة (< 19.1) استخدمت حقول `ShadowFormat` بأسماء مختلفة قليلاً. دائمًا استهدف أحدث حزمة NuGet للحصول على أفضل النتائج.

---

## نصائح احترافية لظل مصقول

- **توازن بين الضبابية والإزاحة:** ضبابية قوية مع إزاحة صغيرة قد تبدو “متوهجة” بدلًا من ظل حقيقي. جرب الجمع بين `BlurRadius` × `DistanceX/Y`.
- **مطابقة سمة المستند:** إذا كان ملف Word يستخدم سمة داكنة، يمكن للظل الفاتح (`Color.White`) أن يخلق تأثير رفع خفيف.
- **الأداء:** تعديل الظلال على مئات الأشكال قد يضيف بضع مليثانية لكل شكل. اجمع العملية إذا كنت تعالج تقارير ضخمة.
- **الاختبار:** افتح الـ `.docx` الناتج في كل من Word Desktop وWord Online للتأكد من أن الظل يُعرض بشكل متسق.

---

## الخلاصة

لقد غطينا الآن **كيفية تعيين الظل** على شكل باستخدام C#. باتباع الخطوات الثمانية أعلاه يمكنك **إضافة ظل الشكل**، **تعيين لون الظل**، وتخصيص **ظل الشكل** بالكامل ليتناسب مع أي لغة تصميم. المثال مستقل، يعمل فورًا، ويمنحك أساسًا قويًا لتوسيع المنطق إلى أشكال متعددة، ألوان ديناميكية، أو حتى معلمات يحددها المستخدم.

هل أنت مستعد للتحدي التالي؟ جرّب دمج هذه التقنية مع **تدوير الشكل**، أو أنشئ تقريرًا كاملًا حيث يحصل كل مخطط على ظله المميز. الاحتمالات لا حصر لها، والكود الذي تعلمته الآن هو نقطة انطلاق مثالية.

إذا وجدت هذا الدليل مفيدًا، لا تتردد في وضع نجمة على المستودع، ترك تعليق، أو مشاركة حيلك الخاصة في تعديل الظلال أدناه. برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}