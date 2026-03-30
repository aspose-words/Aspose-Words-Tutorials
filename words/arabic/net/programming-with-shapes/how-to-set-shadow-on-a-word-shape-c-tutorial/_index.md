---
category: general
date: 2026-03-30
description: تعلم كيفية ضبط الظل على شكل في Word باستخدام C#. يوضح هذا الدليل أيضًا
  كيفية إضافة ظل للشكل، وضبط شفافية الشكل، وإضافة ظل للمستطيل.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: ar
og_description: كيف تضبط الظل على شكل في Word باستخدام C#؟ اتبع هذا الدليل خطوة بخطوة
  لإضافة ظل للشكل، وضبط شفافية الشكل، وإضافة ظل للمستطيل.
og_title: كيفية إضافة الظل إلى شكل في Word – درس C#
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: كيفية ضبط الظل على شكل في Word – درس C#
url: /ar/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعيين الظل على شكل في Word – دليل C#

هل تساءلت يومًا **كيف تُعيّن الظل** على شكل داخل مستند Word دون الحاجة إلى تعديل الواجهة الرسومية؟ لست وحدك. في العديد من التقارير أو عروض التسويق، يجعل الظل الخفيف المستطيل يبرز، وتوفير الوقت عبر البرمجة يساوي ساعات من العمل اليدوي.

في هذا الدليل سنستعرض مثالًا كاملًا جاهزًا للتنفيذ يُظهر **كيفية تعيين الظل**، بالإضافة إلى **إضافة ظل للشكل**، **ضبط شفافية الشكل**، وحتى **إضافة ظل للمستطيل** لتلك الصناديق التوضيحية الكلاسيكية. في النهاية ستحصل على ملف Word (`output.docx`) يبدو مصقولًا، وستفهم لماذا كل خاصية مهمة.

## المتطلبات المسبقة

- .NET 6+ (أو .NET Framework 4.7.2) مع مترجم C#  
- حزمة Aspose.Words for .NET عبر NuGet (`Install-Package Aspose.Words`)  
- إلمام أساسي بـ C# ونموذج كائنات Word  

لا توجد مكتبات إضافية مطلوبة—كل شيء موجود داخل Aspose.Words.

---

## كيفية تعيين الظل على شكل في Word باستخدام C#

فيما يلي ملف المصدر الكامل. احفظه باسم `Program.cs` وشغّله من بيئة التطوير المتكاملة أو عبر `dotnet run`. يقوم الكود بتحميل ملف `.docx` موجود، يبحث عن أول شكل (مستطيل افتراضي)، يُفعّل ظله، يضبط بعض المعلمات البصرية، ثم يحفظ النتيجة.

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **ما ستراه** – الآن المستطيل يحمل ظلًا أسودًا شفافًا بنسبة 30 %، مُزاح 5 pt إلى اليمين وأسفل، مع تمويه خفيف. افتح `output.docx` في Word للتحقق.

## ضبط شفافية الشكل – لماذا يهم؟

الشفافية ليست مجرد مقبض جمالي؛ فهي تؤثر على قابلية القراءة. القيمة `0.0` تجعل الظل غير شفاف تمامًا، بينما `1.0` تخفيه بالكامل. في المقتطف أعلاه استخدمنا `0.3` لتحقيق تأثير خفيف يعمل على الخلفيات الفاتحة والداكنة على حد سواء. لا تتردد في التجربة:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

تذكّر أن **ضبط شفافية الشكل** يمكن تطبيقه أيضًا على لون تعبئة الشكل إذا كنت بحاجة إلى مستطيل شبه شفاف.

## إضافة ظل للشكل إلى كائنات مختلفة

الكود الذي استخدمناه يستهدف كائن `Shape`، لكن خصائص `ShadowFormat` نفسها موجودة على كائنات **Image**، **Chart**، وحتى **TextBox**. إليك نمطًا سريعًا يمكنك نسخه ولصقه:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

وبالتالي سواء كنت **تضيف ظلًا للشكل** إلى شعار أو أيقونة زخرفية، فإن النهج يبقى هو نفسه.

## كيفية إضافة ظل إلى أي شكل – حالات خاصة

1. **شكل بدون صندوق حد** – بعض أشكال Word (مثل الرسومات الحرّة) لا تدعم الظلال. محاولة تعيين `ShadowFormat.Visible` ستفشل بصمت. تحقق من `shape.IsShadowSupported` إذا احتجت إلى أمان.  
2. **إصدارات Word القديمة** – خصائص الظل ترتبط بميزات Word 2007+. إذا كان عليك دعم Word 2003، سيتجاهل البرنامج الظل عند فتح الملف.  
3. **ظلال متعددة** – حاليًا Aspose.Words يدعم ظلًا واحدًا لكل شكل. إذا كنت بحاجة إلى تأثير طبقتين، قم بنسخ الشكل، أزحه، وطبّق إعدادات ظل مختلفة.

## إضافة ظل للمستطيل – حالة استخدام واقعية

تخيل أنك تُنشئ تقريرًا ربع سنويًا وكل عنوان قسم هو مستطيل ملون. إضافة **ظل للمستطيل** تمنح الصفحة مظهرًا يشبه البطاقة. الخطوات هي نفسها كما في المثال الأساسي؛ فقط تأكد أن الشكل المستهدف هو مستطيل بالفعل (`shape.ShapeType == ShapeType.Rectangle`). إذا احتجت لإنشاء المستطيل من الصفر، راجع المقتطف أدناه:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

تشغيل البرنامج الكامل مع هذه الإضافة سيعطيك مستطيلًا جديدًا يحمل بالفعل تأثير **إضافة ظل للمستطيل** المطلوب.

---

![Word shape with shadow](placeholder-image.png){alt="كيفية تعيين الظل على شكل في Word"}

*الشكل: المستطيل بعد تطبيق إعدادات الظل.*

## ملخص سريع (نشرة نقاط سريعة)

- **تحميل** المستند عبر `new Document(path)`.  
- **تحديد** الشكل عبر `doc.GetChild(NodeType.Shape, index, true)`.  
- **تمكين** الظل: `shape.ShadowFormat.Visible = true;`.  
- **تحديد اللون** باستخدام أي `System.Drawing.Color`.  
- **ضبط الشفافية** (`0.0–1.0`) للتحكم في العتمة.  
- **OffsetX / OffsetY** لتحريك الظل أفقياً/رأسياً (نقاط).  
- **BlurRadius** ينعّم الحافة—القيم الأعلى تعني ظلًا أكثر ضبابية.  
- **حفظ** الملف وفتحّه في Word لرؤية النتيجة.

## ماذا تجرب بعد ذلك؟

- **ألوان ديناميكية** – استخرج لون الظل من سمة أو إدخال المستخدم.  
- **ظلال شرطية** – طبّق الظل فقط عندما يتجاوز عرض الشكل حدًا معينًا.  
- **معالجة دفعة** – كرّر عبر جميع الأشكال في المستند و**أضف ظلًا للشكل** تلقائيًا.  

إذا تابعت الخطوات، فأنت الآن تعرف **كيفية تعيين الظل**، وكيف **تضبط شفافية الشكل**، وكيف **تضيف ظلًا للمستطيل** للحصول على لمسة احترافية. لا تتردد في التجربة، وكسر الأشياء، ثم إصلاحها—البرمجة هي أفضل معلم.

---

*برمجة سعيدة! إذا ساعدك هذا الدليل، اترك تعليقًا أو شارك حيل الظل الخاصة بك. كلما تعلمنا من بعضنا البعض، أصبحت مستندات Word أكثر جاذبية.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}