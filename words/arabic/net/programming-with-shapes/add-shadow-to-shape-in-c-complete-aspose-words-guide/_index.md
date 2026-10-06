---
category: general
date: 2026-03-14
description: أضف ظلًا إلى الشكل بسرعة وتعلم كيفية تغيير زاوية الظل، وحفظ المستند مع
  الظل، وأكثر من ذلك في هذا الدرس خطوة بخطوة بلغة C#.
draft: false
keywords:
- add shadow to shape
- change shadow angle
- how to add shape shadow
- save document with shadow
language: ar
og_description: أضف ظلًا إلى الشكل بسرعة، وتعلم كيفية تغيير زاوية الظل، واحفظ المستند
  مع الظل باستخدام Aspose.Words لـ .NET.
og_title: إضافة ظل إلى الشكل في C# – دليل Aspose.Words الكامل
tags:
- Aspose.Words
- C#
- Document Automation
title: إضافة ظل إلى الشكل في C# – دليل Aspose.Words الكامل
url: /ar/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة ظل إلى الشكل في C# – دليل Aspose.Words الكامل

هل احتجت يومًا إلى **إضافة ظل إلى الشكل** لكن لم تكن متأكدًا أي الخصائص يجب تعديلها؟ لست وحدك؛ كثير من المطورين يواجهون هذه المشكلة عند تنسيق مستندات Word برمجيًا. الخبر السار هو أنه باستخدام Aspose.Words يمكنك تمكين ظل واقعي، ضبط زاويته، وحفظ التغييرات في سير عمل واحد مرتب.

في هذا الدرس سنستعرض كل ما تحتاج معرفته: من تحميل المستند، تمكين الظل، ضبط مظهره بدقة، إلى **حفظ المستند مع الظل** في النهاية. بنهاية القراءة ستتمكن من الإجابة على سؤال “كيف أضيف ظلًا إلى الشكل” دون الحاجة للبحث في مشاركات المنتديات المتفرقة.

## ما ستحتاجه

- **Aspose.Words for .NET** (الإصدار 23.10 أو أحدث – واجهة برمجة التطبيقات التي نستخدمها لم تتغير منذ ذلك الحين)
- بيئة تطوير متوافقة مع .NET (Visual Studio، Rider، أو VS Code)
- ملف Word بسيط (`input.docx`) يحتوي بالفعل على شكل واحد على الأقل (مستطيل، صورة، أو SmartArt يعمل)
- معرفة أساسية بـ C# – إذا كتبت برنامج “Hello World” من قبل، فأنت جاهز للبدء

> **Pro tip:** إذا لم يكن لديك مستند جاهز، أنشئ واحدًا بسرعة في Word، أدخل شكلًا عبر *Insert → Shapes*، واحفظه كـ `input.docx` في مجلد المشروع الخاص بك.

## الخطوة 1 – تحميل المستند والحصول على الشكل المستهدف

الأول هو جلب ملف Word إلى الذاكرة وتحديد الشكل الذي تريد تزيينه. Aspose.Words يتعامل مع كل عنصر رسم كعقدة `Shape`، ويمكنك استرجاعها باستخدام `GetChild`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the Word document that contains a shape.
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Retrieve the first shape in the document (index 0). 
// If you have multiple shapes, change the index or loop through them.
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
```

**لماذا هذا مهم:**  
`Document` هو نقطة الدخول لأي تعديل. استدعاء `GetChild` يتجول في شجرة العقد بعمق أولاً، مما يضمن حصولك على أول شكل بغض النظر عن موقعه (رأس، تذييل، أو جسم). إذا تخطيت هذه الخطوة وحاولت الوصول إلى `shape` مباشرة، ستواجه استثناء `NullReferenceException`.

## الخطوة 2 – تمكين تأثير الظل

الظلال تكون معطلة افتراضيًا، لذا يجب تشغيلها قبل تعديل أي خصائص بصرية. هذا سطر واحد، لكنه يفتح مجموعة كاملة من الخيارات.

```csharp
// Turn the shadow on.
shape.Shadow.Enabled = true;
```

> **Did you know?** كائن `Shadow` موجود حتى عندما تكون الميزة معطلة، لذا يمكنك تكوينه مسبقًا وتمكينه لاحقًا دون كتابة كود إضافي.

## الخطوة 3 – ضبط الخصائص الأساسية للظل

الآن نصل إلى الجزء الممتع: تعيين اللون، الشفافية، الضبابية، المسافة، والحجم. هذه القيم تُعبّر بنقاط أو نسب مئوية، كما هو في واجهة Word.

```csharp
// Basic visual settings
shape.Shadow.Color = Color.Black;          // Shadow colour
shape.Shadow.Transparency = 0.3f;          // 30 % transparent
shape.Shadow.BlurRadius = 5.0f;            // Softness of the edge
shape.Shadow.Distance = 3.0f;              // Gap between shape and shadow
shape.Shadow.Size = 100;                   // Scale of the shadow (percent)
```

**Explanation:**  
- **Color** يحدد اللون؛ الأسود يعمل في معظم الحالات، لكن يمكنك مطابقة ألوان العلامة التجارية.  
- **Transparency** هو عدد عشري بين `0` (معتم) و `1` (شفاف تمامًا).  
- **BlurRadius** يتحكم في مدى “طمس” الظل؛ القيم الأكبر تعطي مظهرًا أكثر نعومة.  
- **Distance** يدفع الظل بعيدًا عن الشكل، مما يخلق عمقًا.  
- **Size** يضبط حجم الظل بنسبة مئوية – 100 % يعني أن الظل يطابق حجم الشكل.

## الخطوة 4 – تغيير زاوية الظل (الكلمة المفتاحية الثانوية)

إذا أردت أن يظهر مصدر الضوء من اتجاه مختلف، عدّل خاصية `Angle`. هنا يبرز دور كلمة **change shadow angle**.

```csharp
// Rotate the light source – 45 degrees is a common default.
shape.Shadow.Angle = 45;   // Angle in degrees (0‑360)
```

> **What if you need a dramatic effect?** جرّب `0` لإضاءة من اليسار إلى اليمين، `90` لإضاءة من الأعلى إلى الأسفل، أو `180` لظل عكسي. تذكر أن الزوايا تدور، لذا `360` يعادل `0`.

## الخطوة 5 – حفظ المستند مع الظل

بعد أن يصبح الظل بالمظهر المطلوب، احفظ التغييرات. طريقة `Save` تكتب ملفًا جديدًا مع الحفاظ على الأصلي دون تعديل.

```csharp
// Save the modified document.
doc.Save("YOUR_DIRECTORY/output.docx");
```

الآن لديك ملف `output.docx` حيث الشكل يملك ظلًا مصقولًا. افتحه في Word للتحقق – يجب أن ترى هالة شبه شفافة مائلة حسب الزاوية التي ضبطتها.

## مثال كامل يعمل

فيما يلي البرنامج بالكامل، جاهز للنسخ واللصق في تطبيق Console. التعليقات توضح كل جزء.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Grab the first shape (adjust index if needed).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Enable shadow.
        shape.Shadow.Enabled = true;

        // 4️⃣ Set visual properties.
        shape.Shadow.Color = Color.Black;
        shape.Shadow.Transparency = 0.3f;
        shape.Shadow.BlurRadius = 5.0f;
        shape.Shadow.Distance = 3.0f;
        shape.Shadow.Size = 100;

        // 5️⃣ Change shadow angle (how to add shape shadow from a different direction).
        shape.Shadow.Angle = 45; // Try 0, 90, 180, etc.

        // 6️⃣ Save the result – this is the step that lets you **save document with shadow**.
        doc.Save("YOUR_DIRECTORY/output.docx");

        System.Console.WriteLine("Shadow applied and document saved successfully!");
    }
}
```

### النتيجة المتوقعة

- فتح `output.docx` يُظهر الشكل الأصلي الآن محاطًا بظل أسود ناعم.  
- تغيير `Angle` إلى `90` سيجعل الظل يظهر مباشرة أسفل الشكل، محاكياً إضاءة من الأعلى.  
- ضبط `Transparency` إلى `0.0f` ينتج ظلًا معتمًا بالكامل، بينما `1.0f` يجعله غير مرئي (مفيد للتبديل).

## المشكلات الشائعة وكيفية تجنّبها

| المشكلة | سبب حدوثها | الحل |
|---------|------------|------|
| **`shape` is `null`** | المستند لا يحتوي على أشكال أو الفهرس غير صحيح. | تأكد من أن ملف Word يحتوي على شكل، أو استخدم حلقة عبر `doc.GetChildNodes(NodeType.Shape, true)` للعثور على الشكل الصحيح. |
| **Shadow doesn’t appear in Word** | ترك `Shadow.Enabled` على `false` أو نوع الشكل لا يدعم الظلال (مثل النص العادي). | تأكد من أنك تتعامل مع كائن `Shape` (صور، رسومات، SmartArt) وأن `Enabled = true`. |
| **Unexpected colour** | تم ضبط `Color` إلى قيمة تختلف عما تراه في Word بسبب تجاوزات السمة. | استخدم `Color.FromArgb(0,0,0)` للحصول على أسود نقي، أو طابق سمة المستند باستخدام `shape.Shadow.ThemeColor`. |
| **Performance slowdown** | تعديل العديد من الأشكال في مستند كبير دون تجميع. | غلف التغييرات بـ `doc.BeginUpdateWords()` / `doc.EndUpdateWords()` (Aspose.Words v24+). |

## توسيع المثال

- **Multiple Shapes:** استخدم حلقة عبر جميع الأشكال وطبق ظلًا موحدًا، أو غيّر `Angle` لكل شكل للحصول على تأثير ثلاثي الأبعاد.  
- **Dynamic Colours:** استخرج قيم الألوان من ملف إعدادات لتطابق هوية الشركة.  
- **Conditional Shadows:** أضف الظل فقط إذا كان عرض الشكل يتجاوز حدًا معينًا – مفيد لتسليط الضوء على الرسوم الكبيرة.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.Width > 200) // width in points
    {
        s.Shadow.Enabled = true;
        s.Shadow.Color = Color.Gray;
        s.Shadow.Angle = 30;
    }
}
```

## الخلاصة

غطّينا دورة الحياة الكاملة **لإضافة ظل إلى الشكل** باستخدام Aspose.Words for .NET: تحميل المستند، تمكين الظل، تخصيص اللون، الضبابية، المسافة، **تغيير زاوية الظل**، وأخيرًا **حفظ المستند مع الظل**. الكود مكتمل، يعمل مع أي نسخة حديثة من Aspose.Words، ويوضح كل من “كيف” و “لماذا” لكل خاصية.

هل أنت مستعد للخطوة التالية؟ جرّب الظلال المتدرجة، أو اجمع هذه التقنية مع تأثيرات النص لإنشاء تقارير جذابة بصريًا. إذا صادفت حالات خاصة—مثل الأشكال داخل رؤوس أو تذييلات—تذكر حيل traversing شجرة العقد التي ناقشناها.

برمجة سعيدة، ولتكن مستنداتك دائمًا ذات عمق مثالي!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}