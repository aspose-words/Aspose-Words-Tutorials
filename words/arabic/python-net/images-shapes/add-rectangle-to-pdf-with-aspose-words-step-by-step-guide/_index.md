---
category: general
date: 2026-03-01
description: أضف مستطيلًا إلى PDF بسرعة باستخدام Aspose.Words. تعلم كيفية إدراج شكل
  PDF، إضافة رسومات إلى PDF، وإنشاء مستند PDF برمجيًا بظل مخصص.
draft: false
keywords:
- add rectangle to pdf
- insert shape pdf
- add graphics to pdf
- create pdf document programmatically
- create pdf with shape
language: ar
og_description: إضافة مستطيل إلى PDF باستخدام Aspose.Words. يوضح هذا الدرس كيفية إدراج
  شكل في PDF، وإضافة رسومات إلى PDF، وإنشاء مستند PDF برمجيًا بلغة C#.
og_title: إضافة مستطيل إلى PDF باستخدام Aspose.Words – دليل كامل
tags:
- pdf
- aspnet
- csharp
- graphics
title: إضافة مستطيل إلى PDF باستخدام Aspose.Words – دليل خطوة بخطوة
url: /ar/python/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة مستطيل إلى PDF باستخدام Aspose.Words – دليل كامل

هل احتجت يومًا إلى **add rectangle to PDF** لكن لم تكن متأكدًا من أي استدعاء API ينجز المهمة؟ لست وحدك — المطورون يسألون باستمرار، “كيف يمكنني إدراج شكل PDF مع الحفاظ على خفة الملف؟” الخبر السار هو أن Aspose.Words يجعل الأمر سهلًا للغاية. في هذا الدرس سنستعرض العملية بالكامل، من إنشاء مستند PDF برمجيًا إلى تنسيق المستطيل بظل.

سنضيف أيضًا بعض الإضافات: ستتعلم كيفية **add graphics to PDF**، وسترى الخطوات الدقيقة لـ **insert shape PDF**، وسننتهي بمثال جاهز للتنفيذ **creates PDF with shape**. لا مراجع خارجية، مجرد حل مستقل يمكنك نسخه ولصقه اليوم.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (Aspose.Words يعمل مع .NET Standard 2.0+)
- ترخيص صالح لـ Aspose.Words for .NET أو مفتاح تقييم مؤقت
- Visual Studio 2022 (أو أي بيئة تطوير تفضلها)
- معرفة أساسية بـ C# — لا شيء معقد، فقط القدرة على تشغيل تطبيق كونسول

هذا كل شيء. إذا كان لديك هذه المتطلبات، فأنت جاهز للبدء.

## الخطوة 1: إنشاء مستند PDF برمجيًا

أول شيء تقوم به عندما تريد **add rectangle to PDF** هو إنشاء مستند فارغ. فكر في فئة `Document` كقماش فارغ؛ كل ما تضيفه لاحقًا يعيش داخله.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – initialise a new empty document
        Document doc = new Document();

        // The rest of the steps follow...
```

لماذا نبدأ بمستند فارغ؟ لأنه يضمن لك التحكم الكامل في كل عنصر — لا رؤوس أو تذييلات صفحات مخفية تحتاج للتعامل معها لاحقًا.

## الخطوة 2: تهيئة DocumentBuilder لإدراج شكل PDF

`DocumentBuilder` هو فرشاة الرسم الخاصة بك. يعرف كيف يضع النصوص، الصور، وبشكل حاسم بالنسبة لنا، الأشكال. بدونها، سيتعين عليك تعديل شجرة العقد منخفضة المستوى بنفسك — كابوس لمعظم المطورين.

```csharp
        // Step 2 – create a builder that will let us add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

لاحظ أننا لم نضف أي صفحات بعد. سيقوم الـ builder بإنشاء صفحة تلقائيًا في المرة الأولى التي تُدخل فيها شيئًا، مما يحافظ على نظافة الكود.

## الخطوة 3: إدراج شكل مستطيل — جوهر “add rectangle to PDF”

الآن يأتي الجزء الممتع: إدراج المستطيل. تدعم طريقة `InsertShape` عشرات القيم من `ShapeType`؛ سنختار `ShapeType.Rectangle` ونعطيه حجمًا قدره 200 × 100 نقطة.

```csharp
        // Step 3 – insert a rectangle (200 × 100 points) into the document
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

في هذه المرحلة يحتوي الـ PDF بالفعل على مستطيل بسيط. إذا فتحت الملف الآن، سترى صندوقًا بسيطًا في الزاوية العلوية اليسرى من الصفحة الأولى. هذا هو الأساس لـ **add graphics to PDF**.

## الخطوة 4: تنسيق المستطيل — إضافة ظل مخصص

المستطيل بدون تنسيق ممل. لنمنحه ظلًا خفيفًا حتى يبرز عندما يُعرض الـ PDF. يتحكم كائن `ShadowFormat` في كل شيء من نصف قطر الضبابية إلى الشفافية.

```csharp
        // Step 4 – configure a custom shadow for the shape
        ShadowFormat shadow = rectangle.ShadowFormat;
        shadow.Visible = true;
        shadow.BlurRadius = 8.0;          // pixels
        shadow.Distance = 5.0;           // points from the shape
        shadow.Direction = 45.0;         // degrees clockwise
        shadow.Opacity = 0.6;            // 0‑1 range
        shadow.Color = Color.Black;
```

لماذا نهتم بالظل؟ بجانب تحسين المظهر، يمكن للظل أن يساعد في تمييز الرسومات المتداخلة — شيء قد تحتاجه عندما **add graphics to PDF** في تقارير أكثر تعقيدًا.

## الخطوة 5: حفظ الملف — إكمال سير عمل “create PDF with shape”

السطر الأخير يكتب كل شيء إلى القرص. Aspose.Words يختار تلقائيًا نسخة PDF الصحيحة ويضم الموارد اللازمة.

```csharp
        // Step 5 – save the document as a PDF file
        doc.Save(@"C:\Temp\ShapeWithShadow.pdf");
    }
}
```

افتح `ShapeWithShadow.pdf` وسترى مستطيلًا بظل جميل يجلس بفخر على الصفحة. هذا هو سير عمل **create pdf document programmatically** بالكامل، مُختصرًا في أقل من 30 سطرًا من الكود.

## مثال كامل يعمل — إنشاء PDF مع شكل من البداية إلى النهاية

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه في مشروع تطبيق كونسول جديد. يتضمن جميع عبارات `using`، طريقة `Main`، ورأس تعليق مختصر للرجوع إليه مستقبلاً.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectanglePdfDemo
{
    /// <summary>
    /// Demonstrates how to add a rectangle to PDF, configure a shadow,
    /// and save the result using Aspose.Words for .NET.
    /// </summary>
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty PDF document
            Document doc = new Document();

            // 2️⃣ Initialise a DocumentBuilder – the tool that lets us add content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a rectangle shape (200 × 100 points) – this is the core of "add rectangle to pdf"
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

            // 4️⃣ Apply a custom shadow – makes the graphic stand out
            ShadowFormat shadow = rect.ShadowFormat;
            shadow.Visible = true;
            shadow.BlurRadius = 8.0;   // pixels
            shadow.Distance = 5.0;    // points
            shadow.Direction = 45.0;  // degrees
            shadow.Opacity = 0.6;     // semi‑transparent
            shadow.Color = Color.Black;

            // 5️⃣ Save the document – the final step in creating a PDF with shape
            string outputPath = @"C:\Temp\ShapeWithShadow.pdf";
            doc.Save(outputPath);

            Console.WriteLine($"PDF saved successfully to {outputPath}");
        }
    }
}
```

**النتيجة المتوقعة:** PDF من صفحة واحدة حيث يكون مستطيل بحجم 200 × 100 نقطة قريبًا من الزاوية العلوية اليسرى، مزينًا بظل ناعم بزاوية 45 درجة. افتح الملف في أي عارض PDF للتحقق.

## أسئلة شائعة وحالات خاصة

### هل يعمل هذا مع أنواع أشكال أخرى؟

بالطبع. استبدل `ShapeType.Rectangle` بـ `ShapeType.Ellipse` أو `ShapeType.Triangle` أو أي من الخيارات الـ150+ التي يدعمها Aspose.Words. تنطبق نفس خصائص `ShadowFormat`.

### ماذا لو احتجت المستطيل في صفحة معينة؟

بعد إدراج الشكل، يمكنك نقله إلى صفحة مختلفة عن طريق تعديل خاصية `CurrentPage` للـ builder قبل استدعاء `InsertShape`. على سبيل المثال:

```csharp
builder.MoveToPage(3);
Shape rectOnPage3 = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

### هل يمكنني تغيير لون تعبئة المستطيل؟

بالطبع. استخدم خاصية `FillColor`:

```csharp
rect.FillColor = Color.LightBlue;
```

### كيف يؤثر هذا على حجم الملف؟

إضافة شكل بسيط وظل يضيف فقط بضع كيلوبايت. إذا بدأت بتكديس العديد من الرسومات، فكر في ضغط الصور أو استخدام أشكال مبنية على المتجهات للحفاظ على خفة الـ PDF.

### هل يلزم ترخيص للإنتاج؟

Aspose.Words يعمل في وضع التقييم، لكن ملف الـ PDF الناتج سيحتوي على علامة مائية. اشترِ ترخيصًا للاستخدام غير المقيد ولإزالة العلامة المائية.

## نصائح وحيل (مستوى محترف)

- **Batch insertion:** إذا كنت بحاجة إلى عشرات المستطيلات، قم بالتكرار عبر مجموعة من الإحداثيات وأعد استخدام نفس `DocumentBuilder` — يبقى الأداء خطيًا.
- **Layering:** اضبط `rect.WrapType = WrapType.Inline` إذا أردت أن يتدفق المستطيل مع النص، أو `WrapType.Square` للسماح للنص بالالتفاف حوله.
- **PDF/A compliance:** استدعِ `doc.CompatibilityOptions.OptimizeForPdfA = true;` قبل الحفظ إذا كنت تحتاج إلى PDF متوافق مع الأرشفة.

## ملخص بصري

![add rectangle to pdf example](https://example.com/rectangle-shadow.png "add rectangle to pdf example")

توضح الصورة تخطيط الـ PDF النهائي: مستطيل نظيف بظل خفيف، بالضبط ما ينتجه الكود الخاص بنا.

## الخلاصة

أنت الآن تعرف **how to add rectangle to PDF** باستخدام Aspose.Words، وكيفية **insert shape PDF**، وكيفية **add graphics to PDF** مع تنسيق مخصص — كل ذلك أثناء **creating PDF document programmatically** وإنهاءً بمثال **create PDF with shape** يمكنك إعادة استخدامه غدًا.  

بعد ذلك، جرّب استبدال المستطيل بشعار، أو دمج عدة أشكال لبناء مخطط بسيط. يمكنك أيضًا استكشاف التفاف النص، الدوران، أو حتى تضمين رابط داخل الشكل. الـ API غني بما يكفي لتتمكن من تحويل PDF ثابت إلى تقرير تفاعلي غني بالرسومات دون مغادرة C#.

لا تتردد في التجربة، وإذا واجهت أي مشكلة، اترك تعليقًا أدناه. برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}