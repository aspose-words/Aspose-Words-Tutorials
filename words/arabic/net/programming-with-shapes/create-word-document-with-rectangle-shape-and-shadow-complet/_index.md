---
category: general
date: 2026-01-02
description: إنشاء مستند Word يحتوي على شكل مستطيل، ضبط لون تعبئة الشكل، وحفظ ملف docx
  باستخدام Aspose.Words. تعلم كيفية إنشاء مستطيل بظل في دقائق.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: ar
og_description: إنشاء مستند Word مع مستطيل مخصص، ضبط لون التعبئة، إضافة ظل، وحفظه
  كملف DOCX. الكود الكامل والشروحات.
og_title: إنشاء مستند Word مع شكل مستطيل – خطوة بخطوة
tags:
- Aspose.Words
- C#
- Document Generation
title: إنشاء مستند Word مع شكل مستطيل وظل – دليل شامل
url: /ar/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word مع شكل مستطيل وظل – دليل كامل

هل تساءلت يومًا كيف **create word document** يحتوي على مستطيل مصمم بشكل جميل؟ ربما تحتاج إلى عنصر نائب للشعار، أو لافتة ملونة، أو مجرد إشارة بصرية في تقرير. في هذا الدرس سنقوم **add rectangle shape**، نُعطيه لون تعبئة، نطبق ظلًا خفيفًا، وأخيرًا **save docx file** – كل ذلك باستخدام Aspose.Words لـ .NET.

سوف تحصل على مقتطف C# جاهز للتنفيذ، شرح واضح لكل سطر، ومجموعة من النصائح التي يمكنك إعادة استخدامها في مشاريعك الخاصة. لا إطالة، مجرد حل عملي يمكنك نسخه ولصقه.

## ما ستحتاجه

- .NET 6 أو أحدث (الكود يعمل أيضًا على .NET Framework)  
- Visual Studio 2022 (أو أي محرر تفضله)  
- حزمة NuGet **Aspose.Words** (`Install-Package Aspose.Words`)  

إذا كان لديك هذه بالفعل، رائع – لنبدأ.

## الخطوة 1 – تهيئة مستند جديد (How to create word document)

أول شيء عليك القيام به هو **create word document** في الذاكرة. فكر فيها كفتح لوحة فارغة حيث سترسم المستطيل لاحقًا.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **لماذا هذا مهم:** `Document` تمثل ملف DOCX بالكامل، بينما `DocumentBuilder` هو أداة مساعدة مريحة تسمح لك بإدراج النصوص والجداول والصور والأشكال دون التعامل يدويًا مع شجرة العقد الأساسية.

## الخطوة 2 – إدراج شكل مستطيل (Add rectangle shape)

الآن سنقوم **add rectangle shape** إلى المستند. طريقة `InsertShape` تأخذ نوع الشكل وأبعاده بالنقاط (نقطة واحدة = 1/72 بوصة).

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **نصيحة احترافية:** إذا احتجت يومًا لإنشاء شكل هندسي مختلف (إهليلج، مثلث، إلخ)، فقط غيّر `ShapeType.Rectangle` إلى قيمة الـ enum المطلوبة.

## الخطوة 3 – تكوين الظل (Set shape fill color & shadow)

يمكن للظل أن يجعل الشكل المسطح يبدو أكثر ثلاثي الأبعاد. هنا نقوم بتمكين الظل وتعديل مظهره.

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **لماذا هذه القيم؟** نصف قطر تشويش معتدل ومسافة 5 نقاط يمنع الظل من طغيان الشكل، بينما 45° تحاكي مصدر ضوء يأتي من أعلى اليسار – وهو ما يُستخدم شائعًا في واجهات المستخدم.

## الخطوة 4 – حفظ المستند (Save docx file)

أخيرًا، نقوم **save docx file** إلى القرص. عدّل المسار ليتناسب مع بيئتك.

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

عند فتح `ShadowDemo.docx` في Word، يجب أن ترى مستطيلًا أزرق فاتح مع ظل رمادي ناعم، تمامًا كما في لقطة الشاشة أدناه.

![إنشاء مستند Word مع شكل مستطيل وظل](https://example.com/images/rectangle-shadow.png "إنشاء مستند Word مع شكل مستطيل وظل")

*نص بديل الصورة:* **Create Word Document** يُظهر شكل مستطيل مع ظل.

## مثال كامل وجاهز للتنفيذ (How to create rectangle and save)

بجمع كل شيء معًا، إليك البرنامج الكامل الذي يمكنك نسخه إلى تطبيق كونسول:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### النتيجة المتوقعة

- ملف باسم **ShadowDemo.docx** يظهر في المجلد المستهدف.  
- عند فتحه في Microsoft Word يظهر صفحة واحدة تحتوي على النص “Shadow Demo” يليه مستطيل أزرق فاتح.  
- المستطيل يلقي ظلًا رماديًا ناعمًا بزاوية 45°، مما يمنحه إحساسًا طفيفًا ثلاثي الأبعاد.

## أسئلة شائعة وحالات خاصة

### ماذا لو احتجت إلى حجم مختلف؟

فقط غيّر المعاملات `200, 100` في `InsertShape`. تلك الأرقام تمثل العرض والارتفاع بالنقاط. للحصول على مربع، استخدم قيمًا متطابقة.

### هل يمكن جعل الظل أكثر وضوحًا؟

زد قيمة `BlurRadius` للحصول على حافة أكثر سلاسة، ارفع `Distance` للحصول على إزاحة أكبر، أو قلل `Transparency` (مثلاً `0.1`) لجعله أغمق.

### كيف أضيف حدًا حول المستطيل؟

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### هل هذا متوافق مع إصدارات أقدم من Aspose.Words؟

نعم. فئة `ShadowFormat` موجودة منذ إصدارات 2020 المبكرة. إذا كنت تستخدم نسخة قديمة جدًا، قد تحتاج إلى الترقية للوصول إلى جميع الخصائص.

## نصائح ومخاطر

- **نصيحة احترافية:** احرص دائمًا على تحرير المستندات الكبيرة (`doc.Dispose()`) عند الانتهاء، خاصة في تطبيقات الويب، لتحرير الموارد الأصلية.  
- **احذر من:** استخدام مسار نسبي بدون أذونات مناسبة قد يسبب `UnauthorizedAccessException`. يفضَّل استخدام مسارات مطلقة أو التأكد من أن مجموعة تطبيقات الويب لديها صلاحية كتابة.  
- **تذكر:** خاصية `FillColor` تقبل أي قيمة من `System.Drawing.Color`. لا تتردد في استخدام `Color.FromArgb(255, 173, 216, 230)` للحصول على ظل باستيل مخصص.

## الخطوات التالية

الآن بعد أن عرفت كيفية **create word document**، **add rectangle shape**، **set shape fill color**، و **save docx file**، يمكنك تجربة المزيد:

- إدراج أشكال متعددة وترتيبها باستخدام `RelativeHorizontalPosition` و `RelativeVerticalPosition`.  
- دمج المستطيل مع النص باستخدام `Shape.TextBox` للتعليقات التوضيحية.  
- تصدير نفس المستند إلى PDF (`doc.Save("output.pdf")`) للتوزيع.

إذا كنت فضوليًا حول الرسومات المتقدمة، تفقد دعم Aspose.Words لـ **WordArt**، **الرسوم البيانية**، و **الصور المضمنة**. كل منها يتبع نفس النمط: إنشاء عقدة، ضبط خصائصها، ثم حفظ.

---

### TL;DR

- استخدم `Document` و `DocumentBuilder` لـ **create word document**.  
- استدعِ `InsertShape(ShapeType.Rectangle, …)` لـ **add rectangle shape**.  
- عيّن `FillColor` للخلفية المطلوبة.  
- فعّل `ShadowFormat` واضبط خصائصه للحصول على مظهر مصقول.  
- انتهِ بـ `document.Save("yourPath.docx")` لـ **save docx file**.

برمجة سعيدة، واستمتع بجعل ملفات Word تبدو أكثر أناقة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}