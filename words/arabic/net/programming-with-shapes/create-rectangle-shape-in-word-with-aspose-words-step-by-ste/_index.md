---
category: general
date: 2025-12-29
description: إنشاء شكل مستطيل في مستند Word باستخدام Aspose.Words C#. تعلم كيفية ضبط
  شفافية الشكل، وتعيين لون الظل، وحفظ مستند Word بسهولة.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: ar
og_description: إنشاء شكل مستطيل في مستند Word باستخدام Aspose.Words C#. يوضح هذا
  الدليل كيفية ضبط شفافية الشكل، وتعيين لون الظل، وحفظ مستند Word.
og_title: إنشاء شكل مستطيل في Word – دليل Aspose.Words الكامل
tags:
- Aspose.Words
- C#
- Word Automation
title: إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة
url: /ar/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل في Word – دليل Aspose.Words الكامل

هل احتجت يوماً إلى **إنشاء شكل مستطيل** في مستند Word لكنك لم تكن متأكدًا من أين تبدأ؟ لست وحدك؛ كثير من المطورين يواجهون هذه المشكلة عند أتمتة التقارير أو الفواتير. في هذا الدليل سنستعرض الخطوات الدقيقة لإنشاء شكل مستطيل، ضبط شفافية الشكل، ضبط لون الظل، وأخيرًا **حفظ مستند Word** باستخدام Aspose.Words لـ .NET.  

سنغطي كل شيء من كائن المستند الأولي إلى ملف `.docx` النهائي على القرص، بحيث تكون قادرًا في النهاية على **إنشاء مستند Word** برمجيًا دون تخمين. لا مراجع خارجية، مجرد حل متكامل يمكنك نسخه‑ولصقه في مشروعك.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)
- حزمة NuGet الخاصة بـ Aspose.Words for .NET (`Install-Package Aspose.Words`)
- إلمام أساسي بصياغة C#
- بيئة تطوير من اختيارك (Visual Studio، Rider، VS Code، إلخ)

> **نصيحة احترافية:** إذا كنت تستخدم نسخة تجريبية مجانية من Aspose.Words، ستضيف المكتبة علامة مائية إلى ملف الإخراج. للإنتاج ستحتاج إلى ترخيص صالح.

## الخطوة 1: تهيئة المستند وDocumentBuilder

أول ما نقوم به هو إنشاء مستند Word جديد وفارغ و`DocumentBuilder` يتيح لنا إدراج المحتوى. فكر في الـ Builder كقلم افتراضي يرسم على الصفحة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **لماذا هذا مهم:** بدون `DocumentBuilder` سيتعين عليك تعديل شجرة العقد منخفضة المستوى مباشرةً، وهو أمر عرضة للأخطاء وأكثر صعوبة في القراءة.

## الخطوة 2: إنشاء شكل مستطيل

الآن نقوم فعليًا بـ **إنشاء شكل مستطيل**. طريقة `InsertShape` تأخذ تعداد `ShapeType`، العرض، والارتفاع (بالنقاط). الكائن `Shape` المرتجع يتيح لنا تعديل الخصائص البصرية لاحقًا.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

في هذه المرحلة يكون المستطيل صندوقًا أسود صلبًا مرتبطًا بالفقرة الحالية. يمكنك تحريكه، تغيير حجمه، أو حتى تدويره لاحقًا إذا احتجت.

![إنشاء شكل مستطيل مع ظل](/images/rectangle-shadow.png "مستند Word يظهر شكل مستطيل مع ظل رمادي")

*نص بديل للصورة: إنشاء شكل مستطيل مع ظل في مستند Word*

## الخطوة 3: ضبط شفافية الشكل

الشفافية هي مستوى “الشفافية” لتعبئة الشكل. تستخدم Aspose.Words خاصية `Transparency` التي تتراوح بين `0.0` (معتم) إلى `1.0` (شفاف بالكامل). هنا نقوم **بتعيين شفافية الشكل** إلى 40 % حتى يبقى النص الأساسي مقروءًا.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **حالة خاصة:** إذا كنت بحاجة إلى شكل غير مرئي تمامًا لكن لا يزال الظل ظاهرًا، اضبط `Transparency` إلى `1.0` ومنح الشكل عرض حد غير صفري.

## الخطوة 4: ضبط الظل

ظل خفيف يضيف عمقًا. سنقوم **بتعيين لون الظل** إلى رمادي متوسط، تعديل نصف قطر الضبابية، وإزاحته بضع نقاط أفقياً وعمودياً.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **لماذا هذا مهم:** الظل الحاد أو الداكن جدًا قد يبدو كخلل طباعة. عدّل `Blur` و`Transparency` حتى يصبح طبيعيًا.

## الخطوة 5: حفظ مستند Word

أخيرًا نقوم **بحفظ مستند Word** على القرص. طريقة `Save` تحدد تنسيق الملف تلقائيًا من الامتداد؛ `.docx` هو تنسيق OpenXML الحديث.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

إذا لم يكن المجلد موجودًا، ستطرح Aspose.Words استثناء `ArgumentException`. تأكد من صحة المسار أو أنشئ الدليل مسبقًا.

## مثال كامل يعمل

فيما يلي البرنامج الكامل الجاهز للتنفيذ الذي يجمع جميع الخطوات. انسخه إلى مشروع وحدة تحكم جديد واضغط **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### النتيجة المتوقعة

افتح `ShadowRectangle.docx` في Microsoft Word. يجب أن ترى مستطيلًا رماديًا فاتحًا مع ظل ناعم ومزاح قليلًا، كلاهما مع شفافية 40 %. الشكل موجود على صفحة فارغة، جاهز لإضافة محتوى إضافي.

## أسئلة شائعة وتنوعات

**ماذا لو أردت شكلًا مختلفًا؟**  
استبدل `ShapeType.Rectangle` بأي قيمة أخرى من التعداد (`Ellipse`، `Triangle`، `Star`، إلخ). يبقى باقي الكود كما هو.

**هل يمكنني تغيير لون الحد؟**  
نعم—استخدم `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` ويمكنك أيضًا ضبط `rectangleShape.StrokeWeight = 1.5;`.

**كيف أضع الشكل في موقع محدد على الصفحة؟**  
اضبط `rectangleShape.WrapType = WrapType.None;` ثم عدّل خصائص `rectangleShape.Left` و`rectangleShape.Top` (القيم بالنقاط).

**هل يمكن إضافة نص داخل المستطيل؟**  
بالتأكيد. بعد إنشاء الشكل، يمكنك استدعاء `rectangleShape.AppendChild(new Paragraph(document))` ثم إضافة `Run` بالنص الخاص بك. تذكر ضبط خصائص `rectangleShape.TextBox` إذا أردت تنسيقًا أغنى.

## نصائح احترافية ومخاطر محتملة

- **الترخيص مبكرًا:** إذا نسيت تطبيق ترخيص، ستضيف Aspose.Words علامة مائية على الصفحة الأولى، ما قد يسبب ارتباكًا أثناء الاختبار.
- **نصيحة الأداء:** عند توليد مستندات متعددة داخل حلقة، أعد استخدام كائن `Document` واحد واستدعِ `document.RemoveAllChildren();` بعد كل حفظ لتقليل الضغط على الـ GC.
- **رؤية الظل:** على الشاشات منخفضة الدقة قد يبدو الظل الخفيف غير مرئي. زد `Blur` أو `OffsetX/Y` للتصحيح، ثم قللها للإنتاج.

## الخطوات التالية

الآن بعد أن تعلمت **إنشاء شكل مستطيل**، **ضبط شفافية الشكل**، **ضبط لون الظل**، و**حفظ مستند Word**، فكر في توسيع الدليل:

- إضافة أشكال متعددة وتجميعها.
- إدراج المستطيل داخل خلية جدول لتصميم تقرير.
- دمج الشكل مع `DocumentBuilder.InsertHtml` لتراكب محتوى HTML‑مُنسق.
- استكشاف تأثيرات بصرية أخرى مثل `Glow` أو `Reflection` لمستندات تشبه واجهات المستخدم.

جرّب، اكسر، ثم حسّن—إنشاء المستندات برمجيًا هو ملعب يلتقي فيه التصميم البصري مع الشيفرة.

---

*برمجة سعيدة! إذا واجهت أي صعوبات، اترك تعليقًا أدناه وسنساعدك في حلها.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}