---
category: general
date: 2026-02-13
description: أضف ظلًا إلى الشكل في C# بسرعة. تعلّم كيفية تطبيق تأثير الظل، وتغيير
  لون الظل، وإنشاء ظل بزاوية 45 درجة باستخدام أمثلة شفرة سهلة.
draft: false
keywords:
- add shadow to shape
- apply shadow effect
- change shadow color
- 45 degree shadow
- how to add shadow
language: ar
og_description: أضف ظلًا إلى الشكل في C# فورًا. يوضح هذا البرنامج التعليمي كيفية تطبيق
  تأثير الظل، وتغيير لون الظل، وتعيين ظل بزاوية 45 درجة.
og_title: إضافة ظل إلى الشكل في C# – دليل خطوة بخطوة لتأثير الظل
tags:
- Aspose.Words
- C#
- Document Automation
title: إضافة ظل إلى الشكل في C# – دليل كامل لتطبيق تأثير الظل
url: /ar/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة ظل إلى الشكل في C# – دليل شامل

هل تساءلت يومًا كيف **تضيف ظلًا إلى الشكل** في مستند Word باستخدام C#؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحتاجون إلى ذلك الظل الخفيف لجعل المخطط يبرز، ولا يستطيعون العثور على مثال جاهز ومختصر.  

خبر سار: هذا الدليل يزودك بالكود الدقيق الذي تحتاجه **لإضافة ظل إلى الشكل**، يشرح لماذا كل سطر مهم، ويظهر لك كيفية تعديل التأثير—سواء أردت ضبابًا رماديًا خفيفًا أو ظلًا جريئًا بزاوية 45 °. خلال الشرح سنقوم أيضًا بـ **تطبيق تأثير الظل**، **تغيير لون الظل**، وسنتحدث عن سيناريو **الظل بزاوية 45 درجة** الكلاسيكي.

## ما ستتعلمه

- كيفية تحميل ملف DOCX، العثور على شكل، وتفعيل ظله.
- معنى كل خاصية للظل (الرؤية، اللون، الشفافية، الحجم، المسافة، الزاوية).
- طرق **تطبيق تأثير الظل** بشكل ديناميكي، مثل التكرار عبر جميع الأشكال أو التعامل مع الكائنات المجمعة.
- نصائح **لتغيير لون الظل** بأمان والتعامل مع المستندات التي لا تحتوي على أشكال.
- كيفية تحقيق **ظل بزاوية 45 درجة** بدقة دون تخمين الزوايا.

لا حاجة لأي وثائق خارجية—فقط انسخ، الصق، وشغّل. في النهاية ستحصل على برنامج يعمل على إضافة ظل احترافي لأي شكل.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا على .NET Framework 4.7+).
- Aspose.Words for .NET (نسخة تجريبية مجانية أو مرخصة). تثبيت عبر NuGet: `dotnet add package Aspose.Words`.
- ملف Word أساسي (`input.docx`) يحتوي بالفعل على شكل واحد على الأقل (مثل مستطيل أو صورة).

> **نصيحة محترف:** إذا لم يكن لديك شكل، أدرجه يدويًا في Word أولًا؛ الدليل يفترض أن الشكل الأول هو الهدف.

---

## الخطوة 1: إعداد المشروع وتحميل المستند

أولًا، أنشئ تطبيقًا من نوع console (أو أي مشروع C#) وأضف مرجع Aspose.Words. ثم حمّل ملف DOCX الذي يحتوي على الشكل الذي تريد تحسينه.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;          // For Shape and ShadowFormat

class Program
{
    static void Main()
    {
        // Load the Word document that contains the shape.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

**لماذا هذا مهم:** `Document` هو نقطة الدخول لجميع مهام معالجة Word. بتحميل الملف مبكرًا، تضمن أن كل عملية تالية تعمل على التمثيل الصحيح في الذاكرة.

---

## الخطوة 2: استرجاع الشكل المستهدف

بعد ذلك، حدد الشكل الذي تنوي تعديلّه. المثال يلتقط الشكل الأول، لكن يمكنك تعديل الفهرس أو التصفية حسب نوع الشكل.

```csharp
        // Retrieve the first shape in the document (adjust the index if needed).
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found. Add a shape to input.docx and try again.");
            return;
        }
```

**شرح:**  
- `GetChild(NodeType.Shape, 0, true)` يتجول في شجرة المستند بعمق أول ويعيد أول شكل يصادفه.  
- فحص الـ null يمنع حدوث `NullReferenceException` عندما لا يحتوي المستند على أشكال—حالة شائعة تُفاجئ المبتدئين.

---

## الخطوة 3: تشغيل الظل

الظل في الشكل معطل بشكل افتراضي. تفعيله بسيط كقلب علم Boolean.

```csharp
        // Turn on the shadow effect for the shape.
        targetShape.ShadowFormat.Visible = true;
```

**ما يحدث:** ضبط `Visible` إلى `true` يخبر Word بأن يرسم ظلًا. بدون هذا السطر، أي إعدادات ظل أخرى تقوم بتغييرها سيتم تجاهلها.

---

## الخطوة 4: ضبط مظهر الظل

الآن نحدد مظهر الظل. الكود أدناه يطابق النمط الشائع “أسود، شفافية 30 %، تمويه 5 pt، إزاحة 3 pt، زاوية 45°”.

```csharp
        // Configure the shadow's appearance.
        // • Black color
        // • 30 % transparent
        // • 5 pt blur radius (size)
        // • 3 pt offset distance
        // • 45° direction (angle)
        targetShape.ShadowFormat.Color = Color.Black;          // change shadow color
        targetShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
        targetShape.ShadowFormat.Size = 5;                     // blur radius
        targetShape.ShadowFormat.Distance = 3;                 // offset distance
        targetShape.ShadowFormat.Angle = 45;                   // 45 degree shadow
```

**لماذا كل خاصية مهمة:**

| Property | Effect | Typical use |
|----------|--------|-------------|
| `Visible` | Turns the shadow on/off | Core to **apply shadow effect** |
| `Color` | Determines the hue of the shadow | Change to gray for subtlety, red for emphasis |
| `Transparency` | 0 = opaque, 1 = fully transparent | 0.3 gives a soft, realistic look |
| `Size` | Controls blur radius (in points) | Larger values create a “feathered” look |
| `Distance` | How far the shadow is offset from the shape | Small distances keep the shape grounded |
| `Angle` | Direction in degrees (0 = right, 90 = up) | 45 gives a classic diagonal drop shadow |

لا تتردد في التجربة—مثلاً، اضبط `Color = Color.Gray` لت **تغيير لون الظل** إلى درجة أفتح، أو استخدم `Angle = 135` للحصول على ظل يسقط إلى الأسفل‑اليسار.

---

## الخطوة 5: حفظ المستند المعدل

أخيرًا، اكتب التغييرات إلى القرص. يمكنك استبدال الملف الأصلي أو إنشاء ملف جديد.

```csharp
        // Save the document with the new shadow.
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
        Console.WriteLine("Shadow added successfully! Check output_with_shadow.docx");
    }
}
```

**النتيجة:** افتح `output_with_shadow.docx` في Word، حدد الشكل، وسترى ظلًا أسودًا واضحًا بزاوية 45 °، شفافية 30 %، وتمويه ناعم. النتيجة البصرية مطابقة لما ستحصل عليه إذا طبقت الظل يدويًا عبر واجهة Word.

---

## إضافي: تطبيق الظل على جميع الأشكال في المستند

إذا كنت بحاجة إلى **تطبيق تأثير الظل** على كل شكل، قم بالتكرار عبر المجموعة بدلاً من استهداف عقدة واحدة.

```csharp
        // Loop through every shape and add the same shadow.
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            shp.ShadowFormat.Visible = true;
            shp.ShadowFormat.Color = Color.Black;
            shp.ShadowFormat.Transparency = 0.3;
            shp.ShadowFormat.Size = 5;
            shp.ShadowFormat.Distance = 3;
            shp.ShadowFormat.Angle = 45;
        }
```

**معالجة الحالات الخاصة:** بعض الأشكال (مثل WordArt) قد تتجاهل بعض الخصائص. اختبر دائمًا على عينة تمثيلية.

---

## تأكيد بصري

فيما يلي لقطة شاشة للشكل بعد تطبيق الظل. لاحظ الإزاحة النظيفة بزاوية 45 ° والشفافية الخفيفة.

![مثال إضافة ظل إلى الشكل](add-shadow-to-shape.png){: .img alt="مثال إضافة ظل إلى الشكل"}

---

## الأسئلة المتكررة

**س: هل يمكنني استخدام تدرج لوني مخصص للظل؟**  
ج: Aspose.Words يدعم فقط الألوان الصلبة لـ `ShadowFormat.Color`. للتدرجات، سيتعين عليك تصدير الشكل كصورة وتطبيق تأثير على مستوى الرسوم.

**س: ماذا لو كان المستند يحتوي على أشكال مجمعة؟**  
ج: كل عضو في المجموعة هو عقدة `Shape` منفصلة. الحلقة الموضحة في قسم “الإضافي” ستتعامل معها تلقائيًا.

**س: هل يعمل هذا مع ملفات Word 2007‑2019؟**  
ج: نعم. Aspose.Words ي抽象 تنسيق الملف، لذا يعمل نفس الكود مع `.doc`، `.docx`، وحتى `.rtf`.

**س: كيف أجعل الظل غير مرئي مرة أخرى؟**  
ج: اضبط `targetShape.ShadowFormat.Visible = false;` ثم احفظ المستند مرة أخرى.

---

## الخاتمة

أنت الآن تعرف بالضبط كيف **تضيف ظلًا إلى الشكل** في C#. من خلال تبديل `ShadowFormat.Visible` وتعديل اللون، الشفافية، الحجم، المسافة، والزاوية، يمكنك **تطبيق تأثير الظل** الذي يتماشى مع أي مواصفات تصميم—بما في ذلك **ظل بزاوية 45 درجة** دقيق.  

سواء كنت تُؤتمت إنشاء تقارير، تبني محرك قوالب، أو مجرد تحسين مخطط واحد، فإن هذه الطريقة تمنحك تحكمًا برمجيًا كاملًا في عمق الشكل البصري. جرب الآن **تغيير لون الظل** بناءً على سمة، أو دمجه مع منطق تعبئة الشكل لإنشاء رسومات ديناميكية تعتمد على البيانات.

برمجة سعيدة، ولا تتردد في التجربة—الظلال رخيصة الإضافة لكنها يمكن أن تحسن القراءة بشكل كبير. إذا وجدت هذا الدليل مفيدًا، شاركه مع زملائك أو اترك تعليقًا بتعديلاتك الخاصة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}