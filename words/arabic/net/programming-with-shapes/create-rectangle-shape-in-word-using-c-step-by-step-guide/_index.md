---
category: general
date: 2026-01-03
description: إنشاء شكل مستطيل في Word باستخدام C# وإضافة ظل إلى الشكل. تعلم كيفية
  إدراج شكل في Word، إضافة ظل إلى الشكل، وإنشاء مستندات Word برمجيًا.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: ar
og_description: إنشاء شكل مستطيل في Word باستخدام C# وإضافة ظل إلى الشكل. اتبع هذا
  الدليل لإدراج الشكل في Word، وتكوين الظلال، وإنشاء المستندات برمجيًا.
og_title: إنشاء شكل مستطيل في Word باستخدام C# – دليل كامل
tags:
- C#
- Word Automation
- Aspose.Words
title: إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة
url: /ar/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل في Word باستخدام C# – دليل كامل

هل احتجت يومًا إلى **إنشاء شكل مستطيل** في مستند Word لكنك لم تعرف من أين تبدأ؟ لست وحدك—العديد من المطورين يواجهون نفس المشكلة عندما يرغبون في **إضافة ظل إلى الشكل** للحصول على مظهر مصقول. في هذا الدرس سنستعرض الخطوات الدقيقة لـ **إدراج شكل في Word**، وتطبيق ظل خفيف، وأخيرًا **c# generate word document** ملفات يمكنك توزيعها على المستخدمين.

سنغطي كل شيء من إعداد المشروع إلى تعديل خصائص الظل، وسننتهي بعينة كود جاهزة للتنفيذ. لا إطالة، فقط الجوانب العملية التي تنجز المهمة.

## ما ستتعلمه

- كيفية **إنشاء شكل مستطيل** باستخدام Aspose.Words (أو Open XML) في C#  
- الخصائص الدقيقة التي تحتاجها **لإضافة ظل إلى الشكل** لإضفاء العمق  
- أين تضع الشكل باستخدام `DocumentBuilder`  
- كيفية حفظ الملف بحيث يفتح بشكل صحيح في Microsoft Word  
- نصائح، فخاخ، وتنوعات للسيناريوهات الواقعية  

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل على .NET Core و .NET Framework)  
- حزمة NuGet قادرة على معالجة ملفات Word – سنستخدم **Aspose.Words for .NET** لأن واجهتها البرمجية مختصرة. إذا كنت تفضل Open XML SDK، فإن المفاهيم هي نفسها، فقط تختلف الفئات.  
- Visual Studio، VS Code، أو أي بيئة تطوير C# تفضلها  

> **نصيحة محترف:** إذا كنت بميزانية محدودة، تقدم Aspose نسخة تجريبية مجانية مثالية للتعلم. ما عليك سوى استبدال سطر الترخيص بتعليق عند الاختبار.

## الخطوة 1: تثبيت مكتبة معالجة Word

أولاً، أضف المكتبة إلى مشروعك. افتح الطرفية في مجلد الحل وشغّل:

```bash
dotnet add package Aspose.Words
```

إذا كنت تستخدم Open XML SDK، سيكون الأمر `dotnet add package DocumentFormat.OpenXml`. باقي هذا الدليل يفترض استخدام Aspose.Words، لكن استبدال استدعاءات الـ API سهل.

## الخطوة 2: إنشاء مستند فارغ جديد

الآن بعد أن أصبحت المكتبة جاهزة، يمكننا **إنشاء شكل مستطيل** ببدء كائن `Document` نظيف. فكر في ذلك كقماش جديد.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

يوفر لنا `DocumentBuilder` طريقة عالية المستوى لإدراج المحتوى دون الحاجة للغوص في شجرة العقد منخفضة المستوى.

## الخطوة 3: إدراج شكل المستطيل

مع الـ builder في يدك، يمكننا **إدراج شكل في Word**. طريقة `InsertShape` تأخذ نوع الشكل وأبعاده (العرض، الارتفاع) بالنقاط.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

في هذه المرحلة يظهر المستطيل في المستند، لكنه يبدو مسطحًا قليلًا. هنا يأتي دور الخطوة التالية.

## الخطوة 4: إضافة ظل إلى الشكل

الظلال تعطي الشكل إحساسًا بالعمق. كائن `Shadow` يسمح لنا بضبط الضبابية، المسافة، الزاوية، اللون، والشفافية. أدناه تكوين كامل يعمل جيدًا لمعظم التقارير.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**لماذا هذه القيم؟**  
- **BlurRadius** بقيمة `5.0` يحافظ على حافة ناعمة دون أن تبدو مشوشة.  
- **Distance** بقيمة `4.0` يبعد الظل بما يكفي ليكون ملحوظًا.  
- **Angle** `45` يحاكي إضاءة طبيعية من أعلى اليسار، وهو معيار شائع في واجهات المستخدم.  
- **Transparency** `0.3` يمنع الظل من طغيان لون ملء الشكل.

إذا أردت تأثيرًا أكثر دراماتيكية، زد قيمة `BlurRadius` وقلل `Transparency`. للحصول على رفع خفيف شبه غير مرئي، عكس هذه القيم.

## الخطوة 5: حفظ المستند

أخيرًا، اكتب الملف إلى القرص. طريقة `Save` تكتشف الصيغة من امتداد الملف، لذا فإن `.docx` يعطيك صيغة Word الحديثة.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

افتح `ShadowRectangle.docx` في Microsoft Word، وسترى مستطيلًا واضحًا مع ظل ناعم—تمامًا ما أردت عندما سألت “**how to add shape**” بلمسة احترافية.

![Create rectangle shape with shadow in Word](placeholder-image.png "Create rectangle shape with shadow in Word")

*نص بديل للصورة: إنشاء شكل مستطيل مع ظل في Word*

## مثال كامل يعمل

نجمع كل ما سبق في برنامج كامل جاهز للتنفيذ. انسخه‑الصقه في تطبيق Console واضغط **F5**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### النتيجة المتوقعة

- الملف `ShadowRectangle.docx` المُولد يحتوي على **شكل مستطيل واحد** مركّز حيث كان موضع المؤشر.  
- المستطيل يعرض **ظل أسود شفاف بنسبة 30 %** مائل بزاوية 45°.  
- لا يُضاف أي محتوى آخر، مما يجعل الملف خفيفًا وسهل الإدماج في تقارير أكبر.

## أسئلة شائعة وحالات حافة

### ماذا لو أردت شكلًا مختلفًا؟

استبدل `ShapeType.Rectangle` بأي قيمة أخرى من تعداد `ShapeType` (مثل `Ellipse`، `Triangle`). واجهة الظل تعمل بنفس الطريقة، لذا يمكنك إعادة استخدام التكوين.

### كيف أغيّر لون التعبئة؟

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### هل يمكنني إضافة الشكل إلى فقرة محددة؟

نعم. انقل `DocumentBuilder` إلى الفقرة المستهدفة باستخدام `builder.MoveToParagraph(index)` قبل استدعاء `InsertShape`. هذا يضمن ظهور الشكل تمامًا حيث تحتاجه.

### ماذا عن صيغ Word القديمة (.doc)؟

فقط غيّر الامتداد:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

ميزة الظل مدعومة في Word 2003 وما بعده، لذا ستظل ترى التأثير.

### استخدام Open XML SDK بدلًا من Aspose؟

الخطوات تبقى: أنشئ `WordprocessingDocument`، أضف عنصر `Drawing`، عيّن خصائص `<a:shadow>`. الـ XML يكون أكثر تفصيلاً، لكن المفاهيم نفسها (الحجم، الضبابية، المسافة، الزاوية) تنطبق.

## نصائح لتجنب المشكلات

- **لا تنسَ الترخيص** إذا كنت تستخدم نسخة Aspose مدفوعة؛ وإلا ستحصل على علامة مائية.  
- **الوحدات هي نقاط**، ليست بكسلات. بكسل الشاشة العادي ≈ 0.75 pt، لذا اضبط الأبعاد وفقًا لذلك.  
- **خصائص الظل تُهمل** إذا كان `WrapType` للشكل مضبوطًا على `Inline`. استخدم `WrapType = WrapType.Square` للأشكال العائمة التي تحترم عرض الظل.  
- **الحفظ إلى مشاركة شبكة** قد يتطلب أذونات صحيحة؛ اختبر المسار دائمًا أولًا.

## الخاتمة

أنت الآن تعرف كيف **تنشئ شكل مستطيل** في مستند Word باستخدام C#، **تضيف ظلًا إلى الشكل**، وتولّد **c# generate word document** ملفات تبدو مصقولة جاهزة للاستخدام. الخطوات الأساسية—تثبيت المكتبة، إنشاء `Document`، إدراج الشكل، ضبط الظل، والحفظ—سهلة التذكر ويمكن تعديلها لأشكال، ألوان، أو بيانات ديناميكية أخرى.

ما الخطوة التالية؟ جرّب تكديس أشكال متعددة، دمج صور، أو توليد تقرير كامل يحتوي على جداول ومخططات. يمكنك أيضًا استكشاف التنسيق الشرطي—تغيير شدة الظل بناءً على قيم البيانات—لجعل مستنداتك ليست مجرد عملية بل جذابة بصريًا.

لا تتردد في التجربة، وإذا واجهت أي غموض، اترك تعليقًا أدناه. برمجة سعيدة، ولتكن مستندات Word دائمًا ذات الظل المثالي!  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}