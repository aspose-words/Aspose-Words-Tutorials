---
category: general
date: 2026-04-10
description: كيفية تعيين الظل على شكل في C# – تعلم كيفية تطبيق الظل الساقط، تغيير
  الشفافية، ضبط الضبابية، وإضافة ظل للشكل باستخدام Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: ar
og_description: كيفية تعيين الظل على شكل في C# – يوضح هذا الدرس كيفية تطبيق الظل المنسدل،
  وتغيير الشفافية، وتعديل الضبابية، وإضافة ظل للشكل مع أمثلة شفرة واضحة.
og_title: كيفية تعيين الظل على شكل في C# – دليل كامل
tags:
- Aspose.Words
- C#
- Document Automation
title: كيفية ضبط الظل على شكل في C# – دليل خطوة بخطوة
url: /ar/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة ظل إلى شكل في C# – دليل شامل

هل تساءلت يومًا **كيفية إضافة ظل** إلى شكل عندما تقوم بإنشاء مستند Word برمجيًا؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحتاجون إلى ظل خفيف لصندوق نص، أو شعار، أو صندوق توضيحي، وتكون وثائق الـ API قليلة.

في هذا الدرس سنستعرض العملية بالكامل: من تحميل ملف `.docx`، واستخراج أول `Shape`، إلى تطبيق ظل سفلي، وتعديل شفافيته، وضبط نصف قطر الضبابية، وأخيرًا وضعه في الموضع المناسب. في النهاية ستحصل على مقطع شفرة قابل لإعادة الاستخدام يعمل مع Aspose.Words .NET 2023 أو أحدث، وستفهم *لماذا* كل خاصية مهمة.

## ما ستحتاجه

- **Aspose.Words for .NET** (حزمة NuGet `Aspose.Words`) – المكتبة التي توفر لنا الفئات `Document` و `Shape` و `ShadowFormat`.  
- **.NET 6+** (أو .NET Framework 4.7.2) – أي بيئة تشغيل حديثة تكفي.  
- ملف Word بسيط (`input.docx`) يحتوي مسبقًا على شكل واحد على الأقل، مثل صندوق نص.  
- Visual Studio أو VS Code أو أي بيئة تطوير مفضلة لديك.

هذا كل شيء. لا أدوات طرف ثالث إضافية، ولا COM interop، فقط C# عادي.

![مثال على كيفية إضافة ظل](image-placeholder.png){:alt="كيفية إضافة ظل إلى شكل في مستند Word"}

## نظرة عامة على كيفية إضافة ظل

الفكرة الأساسية وراء **كيفية إضافة ظل** هي تعديل كائن `ShadowFormat` الموجود داخل `Shape`. فكر في `ShadowFormat` كـ "ورقة أنماط" مصغرة للظل نفسه: تخبر المُعالج ما إذا كان الظل مرئيًا، وما لونه، ومدى شفافيته، ومدى ضبابيته، وأين يقع بالنسبة للشكل.

فيما يلي البرنامج القابل للتنفيذ *الكامل*. يمكنك نسخه ولصقه في تطبيق Console، ثم الضغط على **F5**، ومشاهدة الظل يظهر في الملف `output.docx` المحفوظ.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### لماذا هذه الإعدادات مهمة

- **Visible** – بدون تشغيل هذه العلامة، يتم تجاهل جميع الخصائص الأخرى.  
- **Color** – اللون الرمادي الداكن يحاكي الظل الشائع في واجهات المستخدم؛ يمكنك استبداله بأي `Color`.  
- **Transparency** – القيمة 0.3 تعطي مظهرًا *ناعمًا* مع الحفاظ على وضوح الشكل.  
- **Size** – يتحكم في الضبابية؛ القيمة 6 عادةً ما تكون كافية لإحساس احترافي.  
- **Distance & Angle** – معًا يحددان *الإزاحة*؛ 2 نقطة عند 45° ينتج ظلًا قطريًا خفيفًا.

هذه هي جوهر **كيفية إضافة ظل**. بعد ذلك، سنفصل كل جزء حتى تتمكن من **تطبيق الظل السفلي**، **تغيير الشفافية**، **ضبط الضبابية**، و**إضافة ظل للشكل** بشكل مستقل.

---

## تطبيق الظل السفلي على شكل

عندما يسأل الناس “كيف يمكنني **تطبيق الظل السفلي** في C#؟”، غالبًا ما يحتاجون فقط إلى تشغيل خاصية الرؤية وتحديد لون. المقتطف التالي يعزل هاتين السطرين:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **نصيحة احترافية:** إذا كنت تستهدف إصدارات Word القديمة (2003‑2007)، التزم بالألوان القياسية. قد يتم تجاهل بعض قيم ARGB الغريبة من قبل المُعالج القديم.

---

## كيفية تغيير شفافية الظل

الشفافية تُعبّر عنها كـ **float بين 0 و 1**. القيمة **0** تعني ظلًا غير شفاف تمامًا؛ **1** تجعل الظل غير مرئي. معظم المصممين يختارون قيمة بين **0.2‑0.4** للحصول على مظهر طبيعي.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### حالات الحافة

- **القيم السالبة** – Aspose.Words سيقيدها إلى 0، لكن من الأفضل التحقق من صحة الإدخال.  
- **القيم > 1** – تُقيد إلى 1، مما يخفي الظل فعليًا.  

إذا كنت بحاجة للسماح للمستخدمين باختيار نسبة مئوية، حوّلها أولًا:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## كيفية ضبط الضبابية (الحجم) للظل

خاصية **Size** تتحكم في نصف قطر الضبابية. الأرقام الأكبر تنتج ظلًا أكثر نعومة وانتشارًا. تُقاس بالنقاط (pt)، وليس بالبكسل.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### متى تستخدم ضبابية صغيرة مقابل كبيرة

- **ضبابية صغيرة (2‑4 pt)** – مناسبة للتعليقات التوضيحية بأسلوب UI حيث تريد حافة واضحة.  
- **ضبابية كبيرة (8‑12 pt)** – تعمل جيدًا في التقارير المطبوعة أو عندما يكون الشكل بعيدًا عن الخلفية.

---

## إضافة ظل للشكل – التموضع والاتجاه

الجزء الأخير من **إضافة ظل للشكل** هو الإزاحة. خاصيتان تعملان معًا:

| الخاصية | المعنى |
|----------|---------|
| **Distance** | المسافة التي يبعدها الظل عن الشكل (بالنقاط). |
| **Angle**    | اتجاه الإزاحة (0° = يمين، 90° = أسفل، 180° = يسار، 270° = أعلى). |

مثال ينشئ ظلًا خفيفًا أسفل‑يمين:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

يمكنك تجربة الزوايا لمحاكاة ضوء يأتي من مصادر مختلفة. حيلة شائعة هي السماح للمستخدم باختيار “مصدر الضوء” من قائمة منسدلة وربطه بقيمة الزاوية.

---

## مثال كامل يعمل (جميع الخطوات مجتمعة)

فيما يلي نفس البرنامج السابق، لكن مع **تعليقات إضافية** تجعل المنطق واضحًا تمامًا. انسخه إلى `Program.cs` وشغّله؛ سيحتوي ملف الإخراج على صندوق نص بظل مضبوط بدقة.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**النتيجة المتوقعة:** افتح `output.docx`. سيظهر أول صندوق نص ظلًا رماديًا داكنًا، شفافًا بنسبة 30 %، مع ضبابية خفيفة (size = 6) وإزاحة 2 pt بزاوية 45°. التأثير خفيف لكنه واضح—تمامًا ما يهدف إليه معظم مصممي واجهات المستخدم.

---

## أسئلة شائعة ومشكلات محتملة

- **“هل يعمل هذا مع الصور أيضًا؟”**  
  نعم. أي `Shape`—سواء كان صندوق نص، صورة، أو شكل تلقائي—يحتوي على `ShadowFormat`. فقط استبدل منطق استخراج الشكل بالفهرس أو الاسم المناسب.

- **“ماذا لو كان المستند يحتوي على أشكال متعددة؟”**  
  كرّر عبر `doc.GetChildNodes(NodeType.Shape, true)` وطبق نفس الإعدادات على كلٍ منها. يمكنك أيضًا التصفية حسب `shape.Name` أو `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}