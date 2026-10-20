---
category: general
date: 2026-03-28
description: كيفية تعيين الظل على شكل في C# باستخدام Aspose.Words – إضافة ظل إلى الشكل،
  تطبيق الظل، وتخصيص المظهر.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- apply shadow to shape
- how to add shadow
language: ar
og_description: كيفية ضبط الظل على شكل في C# بسرعة. تعلم إضافة الظل إلى الشكل، تطبيق
  الظل، وتعديل الضبابية والمسافة والزاوية.
og_title: كيفية تعيين الظل على شكل في C# – دليل كامل
tags:
- Aspose.Words
- C#
- Document Automation
- Graphics
title: كيفية تعيين الظل على شكل في C# – دليل خطوة بخطوة
url: /ar/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعيين الظل على شكل في C# – دليل برمجة كامل

هل تساءلت يومًا **كيف تُضيف ظلًا** إلى شكل أثناء بناء مستندات Word برمجيًا؟ لست وحدك. في العديد من التقارير والعروض التقديمية أو النشرات، يمكن للظل الخفيف أن يجعل الرسوميات تبرز دون أن تبدو مبتذلة. الخبر السار؟ باستخدام Aspose.Words for .NET يمكنك إضافة ظل إلى الشكل ببضع أسطر من الشيفرة فقط.

في هذا الدرس سنستعرض العملية بالكامل: تحميل ملف DOCX، الحصول على أول شكل، ثم **تطبيق الظل على الشكل** — بما في ذلك اللون، والطمس، والمسافة، والزاوية. في النهاية ستحصل على مقتطف جاهز للتنفيذ يمكنك إدراجه في أي مشروع C#. لا مكتبات إضافية، ولا سحر مخفي.

## ما ستحتاجه

- **Aspose.Words for .NET** (الإصدار 23.9 أو أحدث) – المكتبة التي تجعل التعامل مع Word سهلًا.  
- بيئة تطوير .NET (Visual Studio 2022، Rider، أو سطر الأوامر).  
- ملف DOCX تجريبي يحتوي على شكل واحد على الأقل (مستطيل، صورة، أو SmartArt يكفي).  

إذا كان أيٌ من هذه العناصر غير متوفر، احصل على حزمة NuGet عبر `Install-Package Aspose.Words` وأنشئ ملف Word بسيط مع إدراج شكل يدويًا – فقط للعرض.

## الخطوة 1: تحميل المستند (التحضير لإضافة الظل)

الخطوة الأولى هي فتح ملف المصدر. هنا يبدأ عملية **إضافة الظل إلى الشكل**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the DOCX that holds the shape you want to enhance
        Document doc = new Document("input.docx");
```

> **لماذا هذا مهم:** تحميل المستند يمنحك كائن `Document` يملك جميع العقد، بما فيها الأشكال. بدون ذلك لا شيء لتعديله.

## الخطوة 2: استرجاع الشكل المستهدف (اختيار الشكل الصحيح)

بعد ذلك نحدد الشكل الذي نريد تنسيقه. في هذا المثال نأخذ أول شكل في الفقرة الأولى، لكن يمكنك تعديل الاستعلام لأي مجموعة عقد.

```csharp
        // Grab the first shape inside the first paragraph of the first section
        Shape targetShape = doc.FirstSection.Body.FirstParagraph
            .GetChildNodes(NodeType.Shape, true)[0] as Shape;

        if (targetShape == null)
        {
            Console.WriteLine("No shape found – check your input file.");
            return;
        }
```

> **نصيحة محترف:** `GetChildNodes(NodeType.Shape, true)` يستعرض الشجرة الفرعية بشكل متكرر، مما يضمن عدم تفويت الأشكال المتداخلة مثل WordArt.

## الخطوة 3: الوصول إلى كائن تنسيق الظل (مكان السحر)

كل `Shape` يحتوي على خاصية `ShadowFormat`. هذا الكائن يتحكم في الرؤية، اللون، الطمس، المسافة، والزاوية — كل ما تحتاجه **لتطبيق الظل على الشكل**.

```csharp
        // The ShadowFormat object holds all shadow‑related settings
        ShadowFormat shadow = targetShape.ShadowFormat;
```

> **لماذا نستخدم `ShadowFormat`:** فهو يخفف عنك التعامل مع تمثيل XML الداخلي، بحيث يمكنك تعديل الظلال دون الحاجة إلى OpenXML الخام.

## الخطوة 4: جعل الظل مرئيًا واختيار لون (إضافة ظل إلى الشكل)

لن يظهر الظل إلا بعد ضبط `Visible` إلى `true`. بعد ذلك يمكنك اختيار أي `System.Drawing.Color`. هنا نستخدم رمادي متوسط، لكن حرية التجربة لك.

```csharp
        // Turn the shadow on and give it a subtle gray tone
        shadow.Visible = true;
        shadow.Color = Color.FromArgb(80, 80, 80);   // dark gray
```

> **خطأ شائع:** نسيان تمكين `Visible` يؤدي إلى فشل صامت — يظهر الشكل دون تغيير رغم ضبط الخصائص الأخرى.

## الخطوة 5: ضبط المظهر – الطمس، المسافة، والزاوية (تحسين الشكل)

الآن نضبط التأثير البصري. `BlurRadius` ينعّم الحواف، `Distance` يبعد الظل عن الشكل، و`Angle` يحدد اتجاه مصدر الضوء.

```csharp
        // Adjust how the shadow looks
        shadow.BlurRadius = 5.0;   // in points – higher = softer
        shadow.Distance   = 3.0;   // how far the shadow is offset
        shadow.Angle      = 45.0;  // degrees clockwise from the horizontal
```

> **حالة خاصة:** إذا ضبطت مسافة سلبية، سيظهر الظل *داخل* الشكل، وهو ما يمكن أن يُستَخدم لتأثير النقش البارز.

## الخطوة 6: حفظ المستند المحدث (شاهد النتيجة)

أخيرًا، اكتب التغييرات إلى القرص. يمكنك استبدال الملف الأصلي أو إنشاء ملف جديد.

```csharp
        // Persist the changes – you’ll see the shadow in Word or any viewer
        doc.Save("output-with-shadow.docx");
        Console.WriteLine("Shadow applied successfully! Check output-with-shadow.docx");
    }
}
```

تشغيل البرنامج ينتج `output-with-shadow.docx`. افتحه في Microsoft Word وستلاحظ أن الشكل المحدد الآن يحمل ظلًا رماديًا ناعمًا بزاوية 45°، طمسه 5 نقطة وإزاحته 3 نقطة.

![Diagram showing shadow applied to a shape](https://example.com/images/shadow-diagram.png "Diagram showing shadow applied to a shape")

*نص بديل: مخطط يوضح تطبيق الظل على شكل* – هذه الصورة توضح تأثير قبل/بعد.

## كيفية إضافة الظل – تنوعات شائعة وحالات خاصة

على الرغم من أن الخطوات الأساسية بسيطة، فإن السيناريوهات الواقعية غالبًا ما تتطلب تعديلات. إليك بعض الحالات “ماذا لو” التي قد تواجهها.

### 1. أشكال متعددة، ظلال مختلفة

إذا كان المستند يحتوي على عدة رسومات، يمكنك حلقة عبر مجموعة الأشكال وتعيين إعدادات ظل فريدة لكل شكل.

```csharp
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            ShadowFormat sf = shp.ShadowFormat;
            sf.Visible = true;
            sf.Color = Color.FromArgb(100, 100, 150); // bluish tint
            sf.BlurRadius = 3.0;
            sf.Distance = 2.0;
            sf.Angle = 30.0;
        }
```

### 2. ظلال شفافة

تتيح لك Aspose.Words ضبط قناة ألفا عبر `Color.FromArgb(alpha, r, g, b)`. استخدم قيمة ألفا منخفضة (مثلاً 50) للحصول على تأثير شبه شفاف خفيف.

```csharp
        shadow.Color = Color.FromArgb(50, 0, 0, 0); // 20% opacity black
```

### 3. إزالة الظل

أحيانًا تحتاج إلى إيقاف الظل بعد تطبيقه. ما عليك سوى ضبط `Visible` إلى `false`.

```csharp
        shadow.Visible = false;
```

### 4. مخاوف التوافق

الميزات الظلية المستخدمة هنا مدعومة في Word 2007 + (صيغة DOCX). إذا كنت تستهدف الصيغة الثنائية القديمة `.doc`، قد يتم تجاهل الظل لأن الصيغة تفتقر إلى العناصر XML اللازمة. في هذه الحالة، فكر في الحفظ كـ DOCX أو استخدم إشارة بصرية بديلة.

## ملخص ما أنجزناه

- **تم تحميل** ملف DOCX باستخدام Aspose.Words.  
- **تم جلب** أول شكل من المستند.  
- **تم الوصول** إلى كائن `ShadowFormat` الخاص به.  
- **تم تمكين** الظل، وضبط اللون، نصف قطر الطمس، المسافة، والزاوية.  
- **تم حفظ** ملف جديد يُظهر التأثير بوضوح.  

كل هذه الخطوات تجيب على سؤال **كيف تُضيف ظلًا** إلى شكل، وتوضح أيضًا كيفية **إضافة الظل إلى الشكل**، **تطبيق الظل على الشكل**، وحتى **كيفية إضافة الظل** في سيناريوهات أكثر تعقيدًا.

## الخطوات التالية والمواضيع ذات الصلة

بعد إتقانك لتنسيق الظل، قد ترغب في استكشاف:

- **تعبئات متدرجة** للأشكال (`Shape.FillFormat.GradientFill`).  
- **تأثيرات النص** مثل التوهج أو الانعكاس (`TextEffect`).  
- **إدراج أشكال جديدة برمجيًا** (`doc.FirstSection.Body.AppendChild(new Shape(...))`).  
- **التصدير إلى PDF** مع الحفاظ على الظلال (`doc.Save("output.pdf")`).  

كل موضوع من هذه المواضيع يبني على نفس مبادئ نموذج الكائنات الذي استخدمناه هنا، لذا ستشعر بالراحة فورًا.

---

*برمجة سعيدة! إذا واجهت أي مشكلة، اترك تعليقًا أدناه أو راجع وثائق Aspose.Words API لمزيد من العمق.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}