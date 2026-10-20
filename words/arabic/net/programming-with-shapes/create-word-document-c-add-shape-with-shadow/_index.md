---
category: general
date: 2026-03-27
description: إنشاء مستند Word باستخدام C# وتعلم كيفية إضافة شكل، وتطبيق الظل على الشكل،
  وتحديد مسافة الظل. دليل خطوة بخطوة لـ Aspose.Words.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: ar
og_description: إنشاء مستند Word باستخدام C# مع شكل مستطيل وظل مخصص. اتبع هذا الدرس
  الكامل لضبط مسافة الظل والنمط.
og_title: إنشاء مستند Word بـ C# – إضافة شكل بظل
tags:
- Aspose.Words
- C#
- Document Automation
title: إنشاء مستند Word باستخدام C# – إضافة شكل بظل
url: /ar/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word C# – إضافة شكل بظل

هل احتجت يوماً إلى **create word document c#** يحتوي على مستطيل مصمم بشكل أنيق؟ ربما تقوم بإنشاء قالب تقرير وتريد ظلًا خفيفًا لجعل التصميم يبرز. في هذا الدرس سنستعرض ذلك بالضبط – كيفية إضافة شكل، تطبيق ظل على الشكل، وحتى تعديل مسافة الظل باستخدام Aspose.Words.

سنبدأ بمستند فارغ، نضيف مستطيلًا، نمنحه ظلًا مسبقًا، ثم نحفظ الملف. في النهاية ستحصل على ملف .docx جاهز للاستخدام يمكنك فتحه في Word ورؤية التأثير فورًا. لا أدوات خارجية، فقط كود C# نقي.

## المتطلبات المسبقة

- .NET 6 (أو أي إطار .NET حديث) مثبت.
- Visual Studio 2022 أو VS Code مع ملحق C#.
- حزمة NuGet Aspose.Words لـ .NET (`Aspose.Words` الإصدار 23.12 أو أحدث).  
  يمكنك إضافتها عبر Package Manager Console:

  ```powershell
  Install-Package Aspose.Words
  ```

هذا كل شيء – لا حاجة إلى DLLs إضافية أو COM interop.

## الخطوة 1: تهيئة مستند جديد وBuilder – أساسيات *create word document c#*

أولاً نحتاج إلى كائن `Document` الذي يمثل ملف Word و`DocumentBuilder` لتعديله.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **لماذا هذه الخطوة مهمة:** فئة `Document` هي الحاوية لجميع أجزاء Word (الصفحات، الأنماط، الصور). الـ builder هو API عالي المستوى يُج abstracts عن التعامل مع العقد منخفضة المستوى، مما يجعل من السهل **create word document c#** دون الحاجة للتعامل مع XML مباشرة.

## الخطوة 2: إدراج شكل مستطيل – *how to create rectangle*  

الآن سنضع مستطيلًا على الصفحة. الحجم يُعبّر عنه بالنقاط (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **نصيحة احترافية:** إذا كنت بحاجة إلى شكل مختلف، فقط استبدل `ShapeType.Rectangle` بـ `ShapeType.Ellipse` أو `ShapeType.Triangle`، إلخ. نفس الكود يعمل مع **how to add shape** من أي نوع.

## الخطوة 3: تطبيق ظل مسبق وتعديله – *apply shadow to shape*  

تأتي Aspose.Words مع عدة صيغ ظل مسبقة. سنستخدم `Preset1` ثم نخصص المسافة، التشويش، الشفافية، واللون.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **لماذا تخصيص الظل؟** خاصية `Distance` تتحكم في بعد الظل عن المستطيل – فكر فيها كـ “الارتفاع” الذي تراه في عرض ثلاثي الأبعاد. تغيير `BlurRadius` ينعّم الحواف، بينما `Transparency` يتيح لك إنشاء مظهر خفيف واحترافي. هذا يغطي متطلب **set shadow distance** ويظهر لك كيفية **apply shadow to shape** بطريقة مرنة.

## الخطوة 4: حفظ المستند – إكمال *create word document c#*  

أخيرًا، احفظ المستند على القرص. عدّل المسار إلى مجلد لديك صلاحية كتابة فيه.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

افتح الملف الناتج في Microsoft Word، وسترى مستطيلًا أزرق فاتحًا مع ظل رمادي ناعم إزاحة 5 pt. هذا هو الدليل البصري على أنك نجحت في **create word document c#** مع شكل مُصمم.

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="مثال create word document c# يظهر مستطيلًا بظل"}

## تنويعات اختيارية وحالات حافة

| السيناريو | ما الذي يجب تغييره | لماذا يهم |
|----------|----------------|----------------|
| **نمط ظل مختلف** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | يوفر لك مظهرًا أكثر دراماتيكية دون الحاجة إلى كود إضافي. |
| **بدون إعداد مسبق – ظل مخصص** | Omit `Format` and set `OffsetX`, `OffsetY` manually. | تحكم كامل في الاتجاه والعمق. |
| **أشكال متعددة** | Call `builder.InsertShape` again before saving. | مفيد للقوالب المعقدة التي تحتوي على أيقونات، شعارات، إلخ. |
| **التوافق مع إصدارات Aspose القديمة** | Use `ShadowEffect` class (available in v20.x). | يضمن تشغيل الكود على المشاريع القديمة. |
| **الحفظ كملف PDF** | `document.Save("ShadowShape.pdf");` | يظهر نفس تأثير الظل في مخرجات PDF. |

> **سؤال شائع:** *ماذا لو لم يظهر الظل في Word؟*  
> تأكد من أنك تستخدم نسخة حديثة من Aspose.Words (≥ 22.9). الإصدارات القديمة كان لديها دعم محدود للظلال. كما تحقق من أن المستند يُفتح في نسخة حديثة من Word (2016+).

## مثال كامل يعمل

فيما يلي البرنامج الكامل الجاهز للنسخ واللصق. يتضمن جميع توجيهات `using`، التعليقات، ومعالجة الأخطاء لتجربة سلسة.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

شغّل البرنامج، انتقل إلى `C:\Temp\ShadowShape.docx`، وسترى المستطيل مع الظل الدقيق الذي قمنا بإعداده.

## ملخص وخطوات قادمة

- أنت الآن تعرف كيف **create word document c#**، وتدرج مستطيلًا، وت **apply shadow to shape** مع **set shadow distance** مخصص.  
- المثال يستخدم Aspose.Words، الذي يُج abstracts عن تعقيدات OpenXML ويضمن عرضًا متسقًا عبر إصدارات Word.  
- هل تريد التعمق أكثر؟ جرّب دمج أشكال متعددة، إضافة نص داخل المستطيل، أو تصدير نفس المستند كملف PDF لرؤية كيفية تحويل الظل.

### مواضيع ذات صلة قد ترغب في استكشافها

- **How to add shape** إلى رأس/تذييل للعلامة التجارية.  
- استخدام **Aspose.Words** لإدراج المخططات والجداول برمجيًا.  
- تخصيص **shadow effects** على الصور بدلاً من الأشكال المتجهية.  
- أتمتة إنشاء المستندات الجماعية للفواتير أو الشهادات.

لا تتردد في التجربة، كسر الكود، ثم إعادة بنائه – هذه أسرع طريقة لاستيعاب المفاهيم. إذا واجهت مشكلة، اترك تعليقًا أدناه أو راجع وثائق Aspose.Words الرسمية للحصول على رؤى أعمق حول API.

برمجة سعيدة، واستمتع بجعل ملفات Word تبدو أكثر صقلًا!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}