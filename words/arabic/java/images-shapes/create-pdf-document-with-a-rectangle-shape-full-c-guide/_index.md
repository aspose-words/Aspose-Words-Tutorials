---
category: general
date: 2026-03-25
description: إنشاء مستند PDF باستخدام C# وتعلم كيفية إضافة شكل مستطيل، وتعيين لون
  التعبئة، وضبط حجم الشكل، وتعيين شفافية الشكل في بضع خطوات فقط.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: ar
og_description: إنشاء مستند PDF بلغة C# ومعرفة كيفية إضافة مستطيل، وتعيين لون التعبئة،
  والحجم والشفافية للحصول على مخرجات PDF مصقولة.
og_title: إنشاء مستند PDF مع شكل مستطيل – دليل C#
tags:
- C#
- PDF
- Aspose.Words
title: إنشاء مستند PDF مع شكل مستطيل – دليل C# الكامل
url: /ar/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند PDF مع شكل مستطيل – دليل C# الكامل

هل احتجت يومًا إلى **إنشاء مستند PDF** يحتوي على شكل مخصص، لكنك لم تكن متأكدًا من أين تبدأ؟ لست وحدك. سواء كنت تبني مولد تقارير أو نشرة تسويقية، فإن القدرة على رسم مستطيل برمجيًا، وتعيين لون التعبئة، وضبط حجمه وحتى تعديل شفافيته يمكن أن تجعل ملفات PDF الخاصة بك تبدو أكثر احترافية.

في هذا الدرس سنستعرض مثالًا كاملًا وجاهزًا للتنفيذ بلغة C# يقوم **بإنشاء مستند PDF**، **بإضافة شكل مستطيل**، **بتعيين لون التعبئة**، **بتحديد حجم الشكل**، و**بتعيين شفافية الشكل** للحصول على ظل خارجي خفيف. في النهاية ستحصل على ملف PDF واحد (`shadow.pdf`) يمكنك فتحه لرؤية النتيجة.

> **نصيحة احترافية:** نفس النهج يعمل مع أنواع أخرى من الأشكال (إهليلج، خط، إلخ) — فقط استبدل `ShapeType.RECTANGLE` بالنوع الذي تحتاجه.

---

## ما ستحتاجه

| المتطلبات المسبقة | لماذا يهم |
|------------------|-----------|
| **.NET 6+** (أو .NET Framework 4.6+) | مكتبة Aspose.Words تستهدف بيئات تشغيل حديثة. |
| **Aspose.Words for .NET** حزمة NuGet | توفر الفئات `Document`، `Shape`، `ShadowEffect` وغيرها ذات الصلة. |
| **بيئة تطوير C#** (Visual Studio، Rider، VS Code) | تجعل عملية تصحيح الأخطاء وتشغيل العينة سهلة وسلسة. |
| **معرفة أساسية بلغة C#** | ستمكنك من فهم الصياغة دون الحاجة إلى غوص عميق. |

يمكنك تثبيت المكتبة عبر سطر الأوامر:

```bash
dotnet add package Aspose.Words
```

هذا كل شيء — لا ملفات DLL إضافية، ولا تبعيات أصلية. بمجرد أن تكون الحزمة موجودة، سيُترجم الكود أدناه ويعمل.

---

## تنفيذ خطوة بخطوة

فيما يلي نقسم العملية إلى خمس خطوات منطقية. كل خطوة لها عنوان واضح (حتى تتمكن نماذج الذكاء الاصطناعي من فهرستها) ومربع كود قصير يمكنك نسخه‑ولصقه مباشرة.

### ## 1. إنشاء مستند PDF وتحضير القماش

أول شيء نفعله هو إنشاء كائن `Document`. فكر فيه كقماش فارغ سيتحول في النهاية إلى ملف PDF الخاص بك.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **لماذا؟** `Document` يحتوي على جميع الأقسام والفقرات والأشكال. البدء بكائن نظيف يضمن عدم وجود بقايا مخفية من تشغيلات سابقة.

### ## 2. إضافة شكل مستطيل – تعيين لون التعبئة وحجم الشكل

الآن نقوم بإنشاء مستطيل، نمنحه تعبئة صفراء زاهية، ونحدد أبعاده. يغطي هذا كلًا من **إضافة شكل مستطيل** و**تعيين لون التعبئة** وكذلك **تحديد حجم الشكل**.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **ملاحظة:** العرض/الارتفاع يُقاسان بالنقاط (نقطة واحدة = 1/72 بوصة). عدّل هذه القيم لتناسب تخطيطك.

### ## 3. تطبيق ظل خارجي وتعيين شفافية الشكل

الظلال تضيف عمقًا، والتحكم في شفافيتها هو جوهر **تعيين شفافية الشكل**. أدناه نقوم بإعداد ظل خارجي رمادي بنسبة شفافية 30 ٪.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **لماذا نضبط الشفافية؟** الظل الشفاف بنسبة 30 ٪ يبدو خفيفًا، مما يمنع المستطيل من الظهور “مسطحًا” على الصفحة.

### ## 4. إدراج الشكل في جسم المستند

نضع الآن المستطيل في الفقرة الأولى من القسم الأول للمستند. هذه الخطوة تربط كل شيء معًا.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **حالة خاصة:** إذا كنت تحتاج الشكل في صفحة جديدة، أضف السطر `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` قبل إلحاق الشكل.

### ## 5. حفظ المستند كملف PDF

أخيرًا، نحفظ البنية الموجودة في الذاكرة إلى ملف PDF فعلي. سيُكتب الملف إلى المجلد الذي تحدده.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

عند تشغيل البرنامج، سيظهر ملف باسم `shadow.pdf`. فتحه يُظهر مستطيلًا أصفر مع ظل رمادي ناعم إزاحته 4 نقاط — تمامًا كما وصفه الكود.

> **الناتج المتوقع:** ملف PDF صفحة واحدة حيث يقع المستطيل قرب الزاوية العليا اليسرى للصفحة، مملوء باللون الأصفر، حجمه 200 × 100 نقطة، ومُسقَط عليه ظل خارجي شبه شفاف.

---

## مثال كامل يعمل (جاهز للنسخ واللصق)

فيما يلي ملف المصدر الكامل، جاهز لتضعه في مشروع وحدة تحكم جديد.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **نصيحة:** استبدل `YOUR_DIRECTORY` بمسار مطلق مثل `C:\Temp` أو مسار نسبي مثل `.\output`. سيقوم البرنامج بإنشاء المجلد إذا لم يكن موجودًا بالفعل.

---

## الأسئلة المتكررة (FAQ)

**س: هل يمكنني تغيير موضع المستطيل على الصفحة؟**  
ج: بالتأكيد. اضبط `rectangle.Left` و `rectangle.Top` (كلاهما يُقاس بالنقاط) قبل إلحاقه بالفقرة.

**س: ماذا لو أردت تعبئة شفافة بدلاً من ظل شفاف؟**  
ج: استخدم `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` — الوسيط الأول هو قناة ألفا (0‑255)، حيث 128 يعطي شفافية تقريبًا 50 ٪.

**س: هل يعمل هذا مع .NET Core؟**  
ج: نعم. تدعم Aspose.Words .NET Standard 2.0+، لذا يمكنك تشغيل نفس الكود على .NET 6، .NET 7، أو .NET Framework 4.6+.

**س: كيف يمكنني إضافة أشكال متعددة؟**  
ج: فقط كرّر الخطوات 2‑4 لكل شكل، وربما تُدرجها في فقرات أو أقسام مختلفة.

---

## الخلاصة

لقد **أنشأنا مستند PDF** من الصفر، **أضفنا شكل مستطيل**، **حددنا لون التعبئة**، **عرّفنا حجمه**، و**ضبطنا شفافية الشكل** للحصول على تأثير ظل مصقول. الكود النموذجي مستقل، يعمل في أقل من دقيقة، ويظهر المفاهيم الأساسية التي ستحتاجها لتصميمات PDF أكثر تعقيدًا.

هل أنت مستعد للتحدي التالي؟ جرّب استبدال المستطيل بشكل ذو زوايا مستديرة، أو دمج صورة داخل الشكل، أو إنشاء جدول محتويات تلقائيًا. نفس الـ API يتيح لك دمج النصوص، الصور، والرسوم المتجهة — فالسماء هي الحد.

إذا وجدت هذا الدليل مفيدًا، أعطه نجمة على GitHub، شاركه مع زميل، أو اترك تعليقًا بأفكارك وتعديلاتك. برمجة سعيدة!

---

![create pdf document with rectangle shape example](/images/rectangle-shadow.png "Screenshot showing the created PDF with a yellow rectangle and gray outer shadow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}