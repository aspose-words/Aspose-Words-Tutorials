---
category: general
date: 2026-01-13
description: إنشاء مستند Word باستخدام Aspose.Words وتعلم كيفية إدراج شكل مستطيل،
  وكيفية إضافة الظل، وإضافة ظل الشكل في C#. مثال كامل مرفق.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: ar
og_description: إنشاء مستند Word باستخدام Aspose.Words، تعرف على كيفية إدراج شكل مستطيل
  وكيفية إضافة الظل. اتبع المثال الكامل بلغة C#.
og_title: إنشاء مستند Word مع مستطيل مظلَّل – دليل كامل
tags:
- Aspose.Words
- C#
- Document Automation
title: إنشاء مستند Word مع مستطيل مظلَّل – دليل خطوة بخطوة
url: /ar/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word مع مستطيل مظلَّل – دليل خطوة بخطوة

هل احتجت يومًا إلى **create word document** يحتوي على مستطيل مظلل بشكل جميل، لكنك لم تكن متأكدًا من أين تبدأ؟ لست وحدك — فالكثير من المطورين يواجهون نفس المشكلة عندما يستخدمون Aspose.Words للمرة الأولى.  

في هذا الدرس سنستعرض كل ما تحتاجه لـ **create word document** برمجيًا، **insert rectangle shape**، ونوضح **how to add shadow** حتى يبرز الشكل. في النهاية ستحصل على مقتطف C# جاهز للتنفيذ يمكنك إدراجه في أي مشروع .NET.

## ما ستتعلمه

- الكود الدقيق لـ **how to insert shape** (مستطيل) في ملف Word.  
- الخصائص التي يجب تعديلها لـ **add shape shadow** والتحكم في مظهرها.  
- كيفية حفظ النتيجة والتحقق من ظهور الظل.  
- بعض النصائح العملية وملاحظات الحالات الخاصة التي توفر عليك عناء لاحقًا.  

لا حاجة لأي وثائق خارجية — كل شيء هنا.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من أن لديك:

1. **.NET 6.0** (أو أي نسخة حديثة من .NET) مثبتة.  
2. **license** لـ Aspose.Words for .NET، أو يمكنك استخدام وضع التقييم المجاني للاختبار.  
3. بيئة تطوير — Visual Studio 2022 تعمل بشكل ممتاز، لكن أي محرر يستطيع تجميع C# يكفي.  

هذا كل شيء. لا تحتاج إلى أي حزم NuGet إضافية بخلاف `Aspose.Words`.

## الخطوة 1 – إعداد المشروع وإضافة مرجع Aspose.Words

أولاً، أنشئ تطبيق console جديد وأضف حزمة Aspose.Words:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** إذا كنت تستخدم النسخة التجريبية المجانية، تذكر استدعاء `License.SetLicense` بملف الترخيص الخاص بك؛ وإلا ستضيف المكتبة علامة مائية.

## الخطوة 2 – تهيئة Document Builder

الآن سنبدأ عملية **create word document** الفعلية. فئة `Document` توفر لنا لوحة فارغة، و`DocumentBuilder` يسمح لنا بالرسم عليها.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

لماذا نحتاج إلى builder؟ فهو يُجرد تفاصيل OpenXML منخفضة المستوى، بحيث يمكنك التركيز على *ما* تريد بدلاً من *كيف* يتم هيكلة الملف. هذا هو جوهر **how to insert shape** بسرعة.

## الخطوة 3 – إدراج شكل المستطيل

هنا حيث نقوم فعليًا بـ **insert rectangle shape**. سيكون حجم المستطيل 150 × 100 نقطة (تقريبًا 2 إنش × 1.3 إنش).

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

طريقة `InsertShape` تُعيد كائن `Shape`، يمكننا تخصيصه أكثر. في هذه المرحلة، المستطيل مجرد صندوق أبيض صلب — لا ظل بعد.

## الخطوة 4 – كيفية إضافة الظل (Add Shape Shadow)

إضافة الظل أمر بسيط بشكل مفاجئ بمجرد معرفة الخصائص التي يجب تعديلها. كائن `ShadowFormat` يتحكم في الرؤية، اللون، الضبابية، الإزاحة، والحجم.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

هذا المقطع يجيب على **how to add shadow** بوضوح: فعّله، اختر لونًا، اضبط الشفافية، الإزاحة، الضبابية، والحجم. يمكنك تجربة هذه القيم للحصول على ظل كثيف أو ظل رقيق جدًا.

### تنويعات شائعة

- **ألوان مختلفة:** استخدم `Color.Black` لظل كلاسيكي، أو `Color.BlueViolet` لتأثير مميز.  
- **عدم وجود ضبابية:** اضبط `BlurRadius = 0` للحصول على حافة واضحة وحادة.  
- **إزاحات أكبر:** زد `OffsetX`/`OffsetY` لإبعاد الظل أكثر عن الشكل.  

## الخطوة 5 – حفظ المستند والتحقق

أخيرًا، احفظ المستند على القرص. سيكون الملف بصيغة `.docx` قياسية يمكن لأي معالج Word حديث فتحه.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

افتح الملف الناتج *ShadowRectangle.docx* في Microsoft Word. يجب أن ترى مستطيلًا بظل رمادي ناعم مائل إلى أسفل‑يمين — تمامًا ما حددته الشيفرة.

> **الناتج المتوقع:** ملف Word صفحة واحدة يحتوي على مستطيل 150 × 100 نقطة مع ظل رمادي شفاف بنسبة 30 %، إزاحة 5 نقاط، ضبابية 4 نقاط، وحجم 75 % من الشكل.

## مثال كامل يعمل

بجمع كل شيء معًا، إليك البرنامج الكامل الجاهز للتنفيذ:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

شغّل البرنامج (`dotnet run`) وستحصل على ملف Word جديد يحتوي على مستطيل مظلَّل بشكل جميل — مثالي للتقارير، الشهادات، أو أي إشارة بصرية تحتاجها.

## الأسئلة المتكررة (FAQs)

**س: هل يمكنني إدراج أشكال أخرى (إهليلج، نجمة) واستخدام نفس كود الظل؟**  
ج: بالتأكيد. طريقة `InsertShape` تقبل أي قيمة من تعداد `ShapeType`. بمجرد حصولك على كائن `Shape`، تعمل خصائص `ShadowFormat` بنفس الطريقة، لذا فإن **how to add shadow** لا يعتمد على الشكل.

**س: ماذا لو أردت الظل على جانبي الشكل؟**  
ج: Aspose.Words يدعم ظلًا واحدًا فقط لكل شكل. لمحاكاة تأثير مزدوج، قم بنسخ الشكل، إزاحة كل نسخة بشكل مختلف، واضبط `ShadowFormat.Visible` لإحدى النسخ إلى `false` بينما تبقي الظل في النسخة الأخرى مرئيًا.

**س: هل يعمل هذا على .NET Framework 4.8؟**  
ج: نعم. الـ API لا يعتمد على الإصدار؛ فقط أشر إلى ملف Aspose.Words DLL المناسب لإطار العمل المستهدف.

## نصائح ومخاطر

- **لا تنس ضبط `Visible = true`** — وإلا ستُتجاهل خصائص الظل.  
- **قيمة الشفافية تتراوح بين 0.0 (معتم) إلى 1.0 (شفاف تمامًا).** الخطأ الشائع هو استخدام `30` بدلاً من `0.3`.  
- **الحفظ في مجلد للقراءة فقط يسبب استثناء.** تأكد من أن دليل الإخراج قابل للكتابة.  

## الخطوات التالية

الآن بعد أن عرفت **how to insert shape**، **add shape shadow**، و**create word document** باستخدام Aspose.Words، قد ترغب في استكشاف:

- إضافة **نص داخل المستطيل** باستخدام `builder.InsertParagraph()` قبل إدراج الشكل.  
- تطبيق **تعبئات تدرجية** أو **حدود بنقوش** للحصول على تنسيق بصري أغنى.  
- أتمتة إنشاء صفحات متعددة، كل منها يحتوي على شكل مظلل مختلف، لبناء تقارير ديناميكية.  

لا تتردد في التجربة — تغيير لون الظل أو ضبابيته أو حجمه يمكن أن يغيّر مظهر مستندك بشكل كبير.

---

*هل أنت جاهز لنشر هذا في الإنتاج؟ احصل على الشيفرة، عدّل المعلمات، وشاهد ملفات Word الخاصة بك تكتسب لمسة احترافية في ثوانٍ.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}