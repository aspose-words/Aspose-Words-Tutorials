---
category: general
date: 2025-12-25
description: كيفية إضافة الظل في C# مع مثال شفرة بسيط. تعلم كيفية ضبط مسافة الظل،
  تخصيص اللون، وإنشاء عمق لرسوماتك.
draft: false
keywords:
- how to add shadow
- how to set shadow distance
language: ar
og_description: كيفية إضافة الظل في C# موضحة خطوة بخطوة. اتبع الدليل لتعيين مسافة
  الظل واللون والطمس للحصول على أشكال ذات مظهر احترافي.
og_title: كيفية إضافة الظل في C# – دليل البرمجة الكامل
tags:
- C#
- graphics
- Aspose.Words
- shadows
title: كيفية إضافة الظل في C# – دليل البرمجة الكامل
url: /ar/python/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة الظل في C# – دليل برمجة كامل

إضافة الظل في C# هي حاجة شائعة عندما تريد أن تبرز رسوماتك من الصفحة. في هذا الدرس سنستعرض الخطوات الدقيقة لإعداد ظل الشكل، بما في ذلك كيفية ضبط مسافة الظل، تعديل الضبابية، واختيار اللون المناسب.

إذا سبق لك أن حدقت في مستطيل مسطح وفكرت “يمكن أن يستفيد من قليل من العمق”، فأنت في المكان الصحيح. سنبدأ من مستند فارغ، نضيف شكلاً، وننتهي بظل مصقول يبدو كأنه وضعه مصمم. لا إطالة، مجرد مثال عملي يمكن تشغيله وتنسخه اليوم.

## ما ستتعلمه

- إنشاء مستند جديد وإدراج شكل برمجيًا.  
- تطبيق ضبابية ناعمة على ظل الشكل.  
- **كيفية ضبط مسافة الظل** بحيث يظهر الظل بشكل طبيعي مائل.  
- اختيار لون ظل يعمل على أي خلفية.  
- حفظ النتيجة كملف PDF (أو أي تنسيق تحتاجه).  

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل مع .NET Core و .NET Framework).  
- Aspose.Words for .NET (نسخة تجريبية مجانية أو مرخصة).  
- فهم أساسي لصياغة C#.  

هذا كل شيء—لا مكتبات إضافية، لا سحر. لنبدأ.

![مثال على شكل بظل أسود ناعم – كيفية إضافة الظل](https://example.com/placeholder-shadow.png "مثال على إضافة الظل")

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

أولاً، أنشئ تطبيق console جديد (أو أي مشروع C#) وأضف حزمة NuGet الخاصة بـ Aspose.Words:

```bash
dotnet new console -n ShadowDemo
cd ShadowDemo
dotnet add package Aspose.Words
```

الآن افتح `Program.cs` وأدخل المساحات الاسمية المطلوبة إلى النطاق:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;
```

> **نصيحة محترف:** إذا كنت تستخدم Visual Studio، سيقترح لك IDE عبارات `using` أثناء كتابة `Document`.

## الخطوة 2: إنشاء مستند جديد وإضافة شكل

مع جاهزية المكتبات، يمكننا إنشاء كائن `Document` وإسقاط مستطيل بسيط على الصفحة الأولى.

```csharp
// Step 2: Initialize the document
Document doc = new Document();

// Add a blank page (Aspose.Words creates one automatically)
Section section = doc.FirstSection;

// Insert a rectangle shape – this will be the object we give a shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    // Size the shape (width, height) in points (1 point = 1/72 inch)
    Width = 200,
    Height = 100,
    
    // Position the shape 100 points from the left and 150 from the top
    Left = 100,
    Top = 150,
    
    // Fill the shape with a light gray so the shadow stands out
    FillColor = System.Drawing.Color.LightGray
};

// Add the shape to the document's first page
section.Body.FirstParagraph.AppendChild(rectangle);
```

لماذا المستطيل؟ إنه لوحة محايدة تسمح بتقييم تأثير الظل دون تشتيت. يمكنك استبدال `ShapeType.Rectangle` بـ `Ellipse` أو `Star`—منطق الظل يبقى نفسه.

## الخطوة 3: كيفية إضافة الظل – تطبيق الضبابية، المسافة، واللون

الآن يأتي جوهر الدرس: **كيفية إضافة الظل** إلى ذلك المستطيل. Aspose.Words يوفّر كائن `Shadow` على كل شكل، مما يتيح لك تعديل الضبابية، المسافة، واللون.

```csharp
// Step 3: Access the shape's shadow settings
Shadow shadow = rectangle.Shadow;

// 3a) Apply a soft blur – larger values make the shadow fuzzier
shadow.Blur = 5.0;          // 5 points blur gives a subtle, professional look

// 3b) Set the shadow's offset distance – this determines how far the shadow is displaced
shadow.Distance = 3.0;      // 3 points offset is enough to suggest depth without looking detached

// 3c) Choose a shadow color – black works on most backgrounds, but you can experiment
shadow.Color = Color.Black; // Solid black; you could use Color.FromArgb(128, 0, 0, 0) for semi‑transparent

// OPTIONAL: Rotate the shadow to match a light source direction (45 degrees works well)
shadow.Angle = 45.0;
```

لاحظ التعليق `// 3b) Set the shadow's offset distance`. هذا السطر يجيب مباشرةً على **كيفية ضبط مسافة الظل**. من خلال تعديل `shadow.Distance`، تتحكم في الفجوة البصرية بين الشكل وظله، محاكياً مصدر ضوء موضع بزاوية معينة.

### لماذا هذه القيم؟

- **Blur = 5.0** – ضبابية خفيفة تمنع الظل من أن يكون صلبًا جدًا مع الحفاظ على وضوحه.  
- **Distance = 3.0** – تجعل الظل قريبًا بما يكفي ليبدو كأنه ناتج عن الشكل نفسه.  
- **Color = Black** – يضمن التباين على الخلفيات الفاتحة والداكنة على حد سواء.  

لا تتردد في تعديل هذه الأرقام؛ الـ API يقبل أي قيمة `double` تحتاجها.

## الخطوة 4: حفظ المستند والتحقق من النتيجة

بعد ضبط الظل، نكتب الملف إلى القرص ببساطة. Aspose.Words يمكنه إخراج صيغ متعددة؛ PDF هو خيار شائع للمشاركة.

```csharp
// Step 4: Save the document as a PDF (you could also use .docx, .png, etc.)
string outputPath = "ShadowedShape.pdf";
doc.Save(outputPath, SaveFormat.Pdf);

Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
```

افتح `ShadowedShape.pdf` وسترى مستطيلًا رماديًا مع ظل أسود ناعم مائل قليلاً إلى أسفل‑يمين. إذا كان الظل باهتًا جدًا، زد قيمة `shadow.Blur` أو `shadow.Distance` وأعد التشغيل.

## أسئلة شائعة وحالات خاصة

### ماذا لو أردت ظلًا شفافًا؟

استخدم لون ARGB مع قناة ألفا أقل من 255:

```csharp
shadow.Color = Color.FromArgb(80, 0, 0, 0); // 80/255 opacity = ~31% transparent
```

### هل يمكن تطبيق نفس الظل على عدة أشكال؟

بالطبع. أنشئ طريقة مساعدة:

```csharp
static void ApplyStandardShadow(Shape shape)
{
    shape.Shadow.Blur = 5.0;
    shape.Shadow.Distance = 3.0;
    shape.Shadow.Color = Color.Black;
}
```

استدعِ `ApplyStandardShadow(rectangle);` لكل شكل تضيفه.

### هل يعمل هذا مع إصدارات .NET Framework القديمة؟

نعم. Aspose.Words 22.9+ يدعم .NET Framework 4.5 وما فوق. فقط عدّل ملف المشروع وفقًا لذلك.

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه إلى `Program.cs`. يتجمع ويعمل فورًا (بافتراض تثبيت حزمة NuGet).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;

namespace ShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Initialize the document
            Document doc = new Document();
            Section section = doc.FirstSection;

            // Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 100,
                Top = 150,
                FillColor = System.Drawing.Color.LightGray
            };
            section.Body.FirstParagraph.AppendChild(rectangle);

            // Apply shadow – this is the core of "how to add shadow"
            Shadow shadow = rectangle.Shadow;
            shadow.Blur = 5.0;                // Soft blur
            shadow.Distance = 3.0;            // How to set shadow distance
            shadow.Color = Color.Black;       // Classic black shadow
            shadow.Angle = 45.0;              // Light source direction

            // Save as PDF
            string outputPath = "ShadowedShape.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
        }
    }
}
```

شغّل البرنامج:

```bash
dotnet run
```

ستجد `ShadowedShape.pdf` في مجلد المشروع. افتحه بأي عارض PDF لتتأكد من أن الظل يبدو كما هو موصوف.

## الخلاصة

غطّينا **كيفية إضافة الظل** إلى شكل في C# من البداية إلى النهاية، وأظهرنا **كيفية ضبط مسافة الظل** إلى جانب الضبابية واللون. ببضع أسطر من الكود يمكنك إعطاء رسوماتك مظهرًا احترافيًا ثلاثي الأبعاد—دون الحاجة إلى أدوات تصميم خارجية.

الآن بعد أن أتقنت الأساسيات، جرّب التجربة:

- غيّر لون الظل إلى أزرق خفيف لإحساس أبرد.  
- زد الضبابية للحصول على تأثير حالم ومشتت.  
- طبّق التقنية نفسها على المخططات، الصور، أو مربعات النص.  

كل تعديل يعزز المفاهيم الأساسية نفسها، لذا ستصبح مرتاحًا في تخصيص الظلال لأي سيناريو.

هل لديك أسئلة أخرى؟ اترك تعليقًا، وتمنياتنا لك ببرمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}