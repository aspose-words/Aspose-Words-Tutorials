---
category: general
date: 2026-02-24
description: إنشاء شكل مستطيل في C# باستخدام Aspose.Words، إضافة ظل إلى الشكل، وحفظ
  المستند كملف PDF. تعلم كيفية إضافة الظل وكيفية حفظ PDF في دقائق.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: ar
og_description: إنشاء شكل مستطيل في C# باستخدام Aspose.Words، ثم إضافة ظل إلى الشكل
  وحفظ المستند كملف PDF – دليل كامل خطوة بخطوة.
og_title: إنشاء شكل مستطيل، إضافة ظل وحفظ PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: إنشاء شكل مستطيل، إضافة ظل وحفظ PDF
url: /ar/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

Let's craft translation.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل، إضافة ظل وحفظ PDF

هل احتجت يومًا إلى **إنشاء شكل مستطيل** في مستند Word ولكنك أيضًا تريد ظلًا ناعمًا وإخراجًا بصيغة PDF؟ لست وحدك. في العديد من مشاريع التقارير أو إنشاء الفواتير، اللمسة البصرية—مثل الظل الخفيف—تُحدث الفرق بين “مجرد ملف آخر” و “مستند احترافي المستوى”.  

في هذا البرنامج التعليمي سنستعرض ذلك بالضبط: باستخدام **Aspose.Words for .NET** لإنشاء شكل مستطيل، إضافة ظل إلى الشكل، وأخيرًا **حفظ المستند كملف PDF**. في النهاية ستحصل على تطبيق C# Console جاهز للتنفيذ ينتج PDF يحتوي على مستطيل مظلل، وستفهم كيف تُعدل الظل أو تغير خيارات التصدير.

## ما ستحتاجه

- .NET 6 SDK (أو أي نسخة حديثة من .NET) – تعمل الواجهة البرمجية بنفس الطريقة على .NET Framework 4.x أيضًا.  
- حزمة NuGet الخاصة بـ Aspose.Words for .NET (`Aspose.Words`) – ثبّتها باستخدام `dotnet add package Aspose.Words`.  
- محرر شفرة – Visual Studio أو VS Code أو Rider سيؤدي الغرض.  

لا توجد خطوات ترخيص إضافية لهذا المثال؛ وضع التقييم المجاني كافٍ لرؤية مخرجات PDF.

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

أولًا، لننشئ مشروع Console ونستورد الفئات التي سنحتاجها.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*لماذا هذا مهم:* `Document` و `DocumentBuilder` يقدمان لنا القماش، بينما `Shape` و `ShadowFormat` يسمحان لنا برسم وتنسيق المستطيل. استيرادهما في البداية يبقي الشيفرة اللاحقة منظمة.

## الخطوة 2: **إنشاء شكل مستطيل** بالأبعاد المطلوبة

الآن ننشئ مستندًا فارغًا ونُدرج مستطيلًا. لاحظ كيف تُعيد طريقة `InsertShape` كائن `Shape` يمكننا تنسيقه فورًا.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*شرح:* الحجم يُعبّر عنه بالنقاط (1 pt = 1/72 in). عدّل الأرقام لتناسب تخطيطك. كما نُعطي الشكل تعبئة باللون الأزرق الفاتح لتبرز الظل.

## الخطوة 3: **إضافة ظل إلى الشكل** – ضبط التأثير بدقة

الظل ليس مجرد “تشغيل/إيقاف”. يمكنك التحكم بلونه، الضبابية، المسافة، الاتجاه، وحتى الشفافية. إليك إعداد عملي يعمل جيدًا لمعظم التقارير.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*لماذا قد تُغيّر هذه القيم:*  
- **BlurRadius** – زدها للحصول على تأثير حالمي، أو قلّها للحصول على حافة حادة.  
- **Direction** – 0° يشير إلى اليمين، 90° للأسفل، 180° إلى اليسار، إلخ. دوّر لتتناسب مع تخطيط صفحتك.  
- **Transparency** – ضعها `0` لظل صلب، `0.5` لنصف شفافية، إلخ.

### كيفية إضافة الظل – طرق بديلة

إذا كنت بحاجة إلى **ظل متعدد الطبقات** (مثلاً ظل خارجي أغمق مع ظل داخلي أفتح)، يمكنك إنشاء شكل ثانٍ، إزاحته، وتعيين `ShadowFormat` مختلف. أو، للحصول على مظهر “بدون ضبابية” سريع، اضبط `BlurRadius = 0`.

## الخطوة 4: **حفظ المستند كملف PDF** – التصدير النهائي

مع المستطيل وظله جاهزين، الخطوة الأخيرة هي كتابة الملف كـ PDF. تتولى Aspose.Words عملية التحويل داخليًا؛ كل ما عليك هو استدعاء `Save` بالصيغ المطلوبة.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*نصيحة*: إذا كنت بحاجة للتحكم في توافق PDF (PDF/A، PDF/X) أو تضمين الخطوط، استخدم نسخة مُحمّلة:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

هذا هو ملخص **كيفية حفظ PDF** باختصار.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في `Program.cs`. يَتَرجَم ويعمل كما هو (فقط تأكد من وجود مجلد الإخراج).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### النتيجة المتوقعة

افتح الملف `ShadowRectangle.pdf` المُولد. سترى صفحة واحدة تحتوي على مستطيل أزرق فاتح، ظل رمادي ناعم مائل بزاوية 45° إلى الأسفل‑اليمين، وحواف نظيفة. يجب أن يكون PDF قابلًا للعرض في أي قارئ حديث (Adobe Acrobat، Edge، Chrome).

![إنشاء شكل مستطيل مع ظل في PDF](/images/shadow-rectangle.png "إنشاء شكل مستطيل مع ظل في PDF")

*(يتضمن نص بديل الصورة الكلمة المفتاحية الأساسية لتحسين محركات البحث.)*

## أسئلة شائعة ومعالجة الحالات الخاصة

**ماذا لو اختفى الظل في ملف PDF؟**  
تأكد من أنك تستخدم نسخة حديثة من Aspose.Words (≥23.3). الإصدارات القديمة كان فيها خلل يتجاهل بعض خصائص الظل أثناء تحويل PDF.

**هل يمكنني تغيير لون الظل ليتطابق مع علامتي التجارية؟**  
بالطبع—ما عليك سوى استبدال `System.Drawing.Color.Gray` بأي `Color` تفضله، مثل `Color.FromArgb(128, 0, 0, 255)` لظل أزرق شبه شفاف.

**كيف أضيف ظلًا لأشكال أخرى (إهليلج، نجمة، إلخ)؟**  
يعمل نفس `ShadowFormat` مع أي كائن `Shape`. بعد إنشاء الشكل، احصل على `ShadowFormat` الخاص به واضبط الخصائص.

**ماذا عن مشاكل DPI أو التحجيم؟**  
يحترم عرض PDF حجم النقاط الخاص بالشكل. إذا كنت بحاجة إلى إخراج بدقة أعلى (للطباعة)، عدّل أبعاد الشكل وفقًا لذلك أو اضبط `PdfSaveOptions.ImageResolution`.

**هل يمكنني التصدير إلى صيغ أخرى، مثل PNG؟**  
نعم—ما عليك سوى استدعاء `document.Save("output.png", SaveFormat.Png)`. سيُرسم الظل بنفس الطريقة.

## نصائح احترافية وأفضل الممارسات

- **إعادة استخدام الـ builder**: إذا كنت تضيف عدة أشكال، احتفظ بنسخة واحدة من `DocumentBuilder`؛ هذا أقل تكلفة من إنشاء عدة نسخ.  
- **الحفظ على دفعات**: عند توليد العديد من ملفات PDF داخل حلقة، أعد استخدام كائن `PdfSaveOptions` لتجنب تخصيصات متكررة.  
- **الاختبار**: افتح دائمًا ملف PDF بعد الحفظ للتحقق من ظهور الظل كما هو متوقع. بعض عارضات PDF تُظهر الظلال بشكل مختلف قليلًا؛ Adobe Acrobat هو المرجع الأكثر موثوقية.  
- **الأداء**: للمستندات الكبيرة، عطل الفواصل التلقائية لـ `DocumentBuilder.InsertShape` عن طريق ضبط `builder.PageSetup.DifferentFirstPageHeaderFooter = false` إذا لم تكن بحاجة إليها.

## الخلاصة

غطّينا كل ما تحتاجه **لإنشاء شكل مستطيل**، **لإضافة ظل إلى الشكل**، و**لحفظ المستند كملف PDF** باستخدام Aspose.Words for .NET. الشيفرة مختصرة، والمفاهيم مشروحة، والآن لديك أساس قوي لتجربة أشكال أخرى، أنماط ظل مختلفة، وخيارات تصدير متعددة.  

ما الخطوات التالية؟ جرّب استبدال المستطيل بـ ...

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}