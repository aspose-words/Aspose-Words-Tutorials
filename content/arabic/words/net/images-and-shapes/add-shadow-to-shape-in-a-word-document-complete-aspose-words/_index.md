---
category: general
date: 2025-12-08
description: أضف ظلًا إلى الشكل بسرعة باستخدام Aspose.Words. تعلّم كيفية إنشاء مستند
  Word باستخدام Aspose، وكيفية إضافة ظل للشكل، وتطبيق شفافية الظل في C#.
draft: false
keywords:
- add shadow to shape
- create word document using aspose
- how to add shape shadow
- apply shadow transparency
language: ar
og_description: إضافة ظل إلى الشكل في ملف Word باستخدام Aspose.Words. يوضح هذا الدليل
  خطوة بخطوة كيفية إنشاء مستند، إضافة شكل، وتطبيق شفافية الظل.
og_title: إضافة ظل إلى الشكل – دليل Aspose.Words C#
tags:
- Aspose.Words
- C#
- Word Automation
title: إضافة ظل إلى الشكل في مستند Word – دليل Aspose.Words الكامل
url: /arabic/net/images-and-shapes/add-shadow-to-shape-in-a-word-document-complete-aspose-words/
---

{{< layout-start >}}

{{< layout-start >}}

# إضافة ظل إلى الشكل – دليل Aspose.Words الكامل

هل احتجت يومًا إلى **إضافة ظل إلى الشكل** في ملف Word لكن لم تكن متأكدًا من أي استدعاءات API تستخدم؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحاولون لأول مرة إعطاء مستطيل أو أي عنصر رسم ظلًا مناسبًا، خاصةً عندما يعملون مع Aspose.Words لـ .NET.

في هذا الدرس سنستعرض كل ما تحتاج معرفته: من **إنشاء مستند Word باستخدام Aspose** إلى تكوين الظل، تعديل الضبابية، المسافة، الزاوية، وحتى **تطبيق شفافية الظل**. في النهاية ستحصل على برنامج C# جاهز للتنفيذ ينتج ملف `.docx` يحتوي على مستطيل مظلل بشكل جميل—دون الحاجة إلى تعديل يدوي في Word.

---

## ما ستتعلمه

- كيفية إعداد مشروع Aspose.Words في Visual Studio.  
- الخطوات الدقيقة **لإنشاء مستند Word باستخدام Aspose** وإدراج شكل.  
- **كيفية إضافة ظل إلى الشكل** مع تحكم كامل في الضبابية، المسافة، الزاوية، والشفافية.  
- نصائح لاستكشاف الأخطاء الشائعة (مثل: فقدان الترخيص، الوحدات غير الصحيحة).  
- عينة كود كاملة قابلة للنسخ واللصق يمكنك تشغيلها اليوم.

> **المتطلبات المسبقة:** .NET 6+ (أو .NET Framework 4.7.2+)، ترخيص Aspose.Words صالح (أو النسخة التجريبية المجانية)، ومعرفة أساسية بـ C#.

---

## الخطوة 1 – إعداد مشروعك وإضافة Aspose.Words

أولًا، افتح Visual Studio، أنشئ تطبيق **Console App (.NET Core)** جديد، وأضف حزمة NuGet الخاصة بـ Aspose.Words:

```bash
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** إذا كان لديك ملف ترخيص (`Aspose.Words.lic`)، انسخه إلى جذر المشروع وحمّله عند بدء التشغيل. هذا يمنع ظهور العلامة المائية في وضع التقييم المجاني.

```csharp
// Load the license (optional but recommended)
var license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

---

## الخطوة 2 – إنشاء مستند فارغ جديد

الآن سنقوم فعليًا **بإنشاء مستند Word باستخدام Aspose**. هذا الكائن سيعمل كقماش لأشكالنا.

```csharp
// Step 2: Initialize a new blank document
Document doc = new Document();   // Represents an empty .docx file
```

فئة `Document` هي نقطة الدخول لكل شيء آخر—الفقرات، الأقسام، وبالطبع كائنات الرسم.

---

## الخطوة 3 – إدراج شكل مستطيل

مع جاهزية المستند، يمكننا إضافة شكل. هنا نختار مستطيلًا بسيطًا، لكن نفس المنطق يعمل مع الدوائر، الخطوط، أو المضلع المخصص.

```csharp
// Step 3: Create a rectangular shape that will hold the shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 150,   // Width in points (1 point = 1/72 inch)
    Height = 100    // Height in points
};
```

> **لماذا الشكل؟** في Aspose.Words يمكن لكائن `Shape` أن يحمل نصًا أو صورًا أو يعمل كعنصر زخرفي فقط. إضافة ظل إلى الشكل أسهل بكثير من محاولة تعديل إطار الصورة.

---

## الخطوة 4 – تكوين الظل (إضافة ظل إلى الشكل)

هذا هو جوهر الدرس—**كيفية إضافة ظل إلى الشكل** وضبط مظهره بدقة. خاصية `ShadowFormat` تمنحك تحكمًا كاملاً.

```csharp
// Step 4: Enable the shadow and configure its appearance
rectangle.ShadowFormat.Visible       = true;   // Turn the shadow on
rectangle.ShadowFormat.Blur          = 5.0;    // Blur radius – higher = softer edges
rectangle.ShadowFormat.Distance      = 3.0;    // Offset distance from the shape
rectangle.ShadowFormat.Angle         = 45;     // Direction in degrees (0 = right, 90 = down)
rectangle.ShadowFormat.Transparency  = 0.3;    // 30 % transparent – this is how we **apply shadow transparency**
```

### ما الذي تفعله كل خاصية

| الخاصية | التأثير | القيم النموذجية |
|----------|--------|----------------|
| **Visible** | تشغيل أو إيقاف الظل. | `true` / `false` |
| **Blur** | ينعم حواف الظل. | `0` (قاسي) إلى `10` (ناعم جدًا) |
| **Distance** | ينقل الظل بعيدًا عن الشكل. | `1`–`5` نقاط شائعًا |
| **Angle** | يتحكم في اتجاه الإزاحة. | `0`–`360` درجة |
| **Transparency** | يجعل الظل شبه شفاف. | `0` (معتم) إلى `1` (غير مرئي) |

> **حالة خاصة:** إذا ضبطت `Transparency` على `1`، يختفي الظل تمامًا—مفيد لتبديله برمجيًا.

---

## الخطوة 5 – إضافة الشكل إلى المستند

نقوم الآن بربط الشكل بالفقرة الأولى في جسم المستند. يقوم Aspose بإنشاء فقرة تلقائيًا إذا لم توجد.

```csharp
// Step 5: Append the shape to the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);
```

إذا كان المستند يحتوي بالفعل على محتوى، يمكنك إدراج الشكل في أي عقدة باستخدام `InsertAfter` أو `InsertBefore`.

---

## الخطوة 6 – حفظ المستند

أخيرًا، اكتب الملف إلى القرص. يمكنك اختيار أي تنسيق مدعوم (`.docx`, `.pdf`, `.odt`, إلخ)، لكن لهذا الدرس سنبقى على تنسيق Word الأصلي.

```csharp
// Step 6: Save the document with the shadowed shape
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

افتح الملف الناتج `ShadowedShape.docx` في Microsoft Word، وسترى مستطيلًا بظل ناعم بزاوية 45 درجة وشفافية 30 %—تمامًا ما قمنا بتكوينه.

---

## مثال كامل يعمل

فيما يلي البرنامج **الكامل القابل للنسخ واللصق** الذي يجمع جميع الخطوات السابقة. احفظه باسم `Program.cs` وشغّله باستخدام `dotnet run`.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load Aspose.Words license (remove if using trial)
        // -------------------------------------------------
        try
        {
            var license = new License();
            license.SetLicense("Aspose.Words.lic");
        }
        catch (Exception ex)
        {
            Console.WriteLine("License not found – running in evaluation mode: " + ex.Message);
        }

        // -------------------------------------------------
        // 1. Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // 2. Insert a rectangle shape
        // -------------------------------------------------
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 150,
            Height = 100
        };

        // -------------------------------------------------
        // 3. Configure the shadow – this is where we **add shadow to shape**
        // -------------------------------------------------
        rectangle.ShadowFormat.Visible      = true;   // Show the shadow
        rectangle.ShadowFormat.Blur         = 5.0;    // Soft edges
        rectangle.ShadowFormat.Distance     = 3.0;    // Offset distance
        rectangle.ShadowFormat.Angle        = 45;     // Direction in degrees
        rectangle.ShadowFormat.Transparency = 0.3;    // 30 % transparent (apply shadow transparency)

        // -------------------------------------------------
        // 4. Add the shape to the document
        // -------------------------------------------------
        doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);

        // -------------------------------------------------
        // 5. Save the file
        // -------------------------------------------------
        string outFile = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
        doc.Save(outFile);
        Console.WriteLine($"Document created successfully: {outFile}");
    }
}
```

**الناتج المتوقع:** ملف باسم `ShadowedShape.docx` يحتوي على مستطيل واحد بظل خفيف شبه شفاف مائل بزاوية 45°.

---

## تنويعات ونصائح متقدمة

### تغيير لون الظل

بشكل افتراضي يرث الظل لون تعبئة الشكل، لكن يمكنك تعيين لون مخصص:

```csharp
rectangle.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### أشكال متعددة بظلال مختلفة

إذا احتجت إلى عدة أشكال، كرّر خطوات الإنشاء والتكوين. تذكر إعطاء كل شكل اسمًا فريدًا إذا كنت تخطط للإشارة إليه لاحقًا.

### تصدير إلى PDF مع الحفاظ على الظلال

يحافظ Aspose.Words على تأثيرات الظل عند الحفظ إلى PDF:

```csharp
doc.Save("ShadowedShape.pdf");
```

### مشكلات شائعة

| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| الظل غير مرئي | ترك `ShadowFormat.Visible` على `false` | ضبطه إلى `true`. |
| الظل يبدو قاسيًا جدًا | ضبط `Blur` على `0` | زيادة `Blur` إلى 3–6. |
| الظل يختفي في PDF | استخدام نسخة قديمة من Aspose.Words (< 22.9) | الترقية إلى أحدث مكتبة. |

---

## الخلاصة

غطّينا **كيفية إضافة ظل إلى الشكل** باستخدام Aspose.Words، من تهيئة المستند إلى ضبط الضبابية، المسافة، الزاوية، و**تطبيق شفافية الظل**. المثال الكامل يوضح نهجًا نظيفًا وجاهزًا للإنتاج يمكنك تكييفه مع أي شكل أو تخطيط مستند.

هل لديك أسئلة حول **إنشاء مستند Word باستخدام Aspose** لسيناريوهات أكثر تعقيدًا—مثل الجداول ذات الظلال أو الأشكال الديناميكية المستندة إلى البيانات؟ اترك تعليقًا أدناه أو اطلع على الدروس ذات الصلة حول معالجة الصور في Aspose.Words وتنسيق الفقرات.

برمجة سعيدة، واستمتع بإضفاء لمسة بصرية إضافية على مستندات Word الخاصة بك! 

--- 

![مثال على إضافة ظل إلى الشكل](shadowed_shape.png "مثال على إضافة ظل إلى الشكل")

{{< layout-end >}}

{{< layout-end >}}