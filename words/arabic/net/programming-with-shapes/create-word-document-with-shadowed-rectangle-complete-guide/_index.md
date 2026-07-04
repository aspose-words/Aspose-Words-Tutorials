---
category: general
date: 2026-04-21
description: إنشاء مستند Word مع مستطيل مُصمم وظل. تعلّم كيفية إضافة الظل، وإدراج
  شكل المستطيل، وتعيين لون الظل، والمزيد في C#.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: ar
og_description: أنشئ مستند Word وأضف شكل مستطيل بظل في C#. اتبع هذا الدليل لتعيين
  لون الظل والتمويه والإزاحات بسهولة.
og_title: إنشاء مستند Word مع مستطيل بظل – خطوة بخطوة
tags:
- Aspose.Words
- C#
- Document Automation
title: إنشاء مستند Word مع مستطيل مظلل – دليل شامل
url: /ar/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word مع مستطيل ظل – دليل كامل

هل احتجت يوماً إلى **إنشاء مستند Word** يبدو أكثر صقلاً من صفحة نص عادية؟ ربما تقوم بإنشاء قالب تقرير أو نشرة إعلانية، ومستطيل بسيط بظل خفيف قد يكون الحل. في هذا الدرس سنستعرض ذلك بالضبط — كيفية إدراج شكل مستطيل، تفعيل الظل، وتخصيص لونه، وضبابه، وإزاحاته — كل ذلك باستخدام C# و Aspose.Words.

سنغطي أيضاً **كيفية إضافة الظل** بطريقة تعمل سواء كنت تستهدف Word 2016 أو 2019 أو أحدث نسخة من Office 365. في النهاية ستحصل على ملف *.docx* جاهز للحفظ يُظهر مستطيلًا مظللًا بشكل جميل، وستفهم “السبب” وراء كل خاصية تقوم بتعيينها.

## المتطلبات المسبقة

- .NET 6 (أو أي إصدار حديث من .NET Framework)  
- حزمة NuGet Aspose.Words لـ .NET (`Install-Package Aspose.Words`)  
- إلمام أساسي بصياغة C#  
- بيئة تطوير متكاملة (IDE) مثل Visual Studio (لكن أي محرر يُمكنه القيام بالمهمة)

لا توجد مكتبات إضافية مطلوبة؛ كل شيء آخر موجود داخل Aspose.Words.

## الخطوة 1 – تهيئة المستند والباني (Create Word Document)

لـ **إنشاء مستند Word** برمجياً تبدأ بفئة `Document`. الـ `DocumentBuilder` هو فرشاتك؛ يتيح لك إضافة النصوص، الأشكال، والعناصر الأخرى.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*لماذا هذا مهم:* كائن `Document` يمثل ملف .docx بالكامل. بدون هذا الكائن لا مكان لإرفاق المستطيل أو ظله.

## الخطوة 2 – إدراج شكل مستطيل (Insert Rectangle Shape)

الآن نقوم فعلياً **بإدراج شكل مستطيل**. طريقة `InsertShape` تأخذ تعداد `ShapeType`، بالإضافة إلى العرض والارتفاع بالنقاط.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*نصيحة محترف:* 1 نقطة ≈ 1/72 إنش، لذا 200 نقطة تعادل تقريباً 2.78 إنش عرضاً. عدّل هذه القيم لتناسب تخطيطك.

## الخطوة 3 – تفعيل الظل (How to Add Shadow)

الظلال معطلة افتراضياً. عكس علم `Visible` لتفعيلها.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*ما الذي يحدث؟* عندما تكون `Visible` true، سيقوم Word برسم ظل إسقاط بناءً على الخصائص الأخرى التي ستحددها لاحقاً.

## الخطوة 4 – تخصيص مظهر الظل (Set Shadow Color, Blur, Offsets)

هنا حيث **تعيين لون الظل**، نصف قطر الضبابية، وإزاحات X/Y. لا تتردد في التجربة — قيم مختلفة تمنحك توهجاً ناعماً، أو ظلًا عميقًا، أو حتى تأثير “عائم”.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*لماذا هذه الأرقام؟* ضبابية 5 نقطة تعطي حافة ناعمة، بينما إزاحة 4 نقطة تنقل الظل إلى الأسفل‑اليمين، محاكاةً لمصدر ضوء من أعلى‑اليسار. غيّر `Color` إلى `Color.Black` لتباين أقوى، أو استخدم `Color.FromArgb(128, 0, 0, 0)` لظل أسود شبه شفاف.

### حالات الحافة والاختلافات

- **بدون ضبابية:** اضبط `Blur = 0` للحصول على ظل حاد ومحدد.  
- **إزاحات سلبية:** استخدم `OffsetX = -4` لدفع الظل إلى اليسار.  
- **أشكال مختلفة:** نفس خصائص الظل تعمل مع الدوائر، المثلثات، أو حتى الأشكال المرسومة يدوياً — فقط غيّر `ShapeType` في الخطوة 2.  
- **التوافق:** Aspose.Words يكتب بيانات الظل بصيغة Office Open XML، والتي تعمل عبر Word 2010‑2021 و Office 365.

## الخطوة 5 – حفظ المستند (Create Word Document)

أخيراً، احفظ الملف على القرص. يمكنك اختيار أي تنسيق مدعوم (`.docx`, `.pdf`, `.odt`, …) لكن لهذا الدليل سنبقى مع تنسيق Word الكلاسيكي.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

عند فتح **ShadowRectangle.docx** في Microsoft Word سترى مستطيلًا رماديًا بظل خفيف ومضبب موجه إلى أسفل‑اليمين — تماماً ما برمجناه.

### النتيجة المتوقعة

- ملف *.docx* صفحة واحدة.  
- مستطيل 200 pt × 100 pt مركّز في الموضع الذي كان فيه المؤشر عندما تم استدعاء `InsertShape`.  
- ظل رمادي يظهر 4 pts إلى اليمين و4 pts إلى الأسفل، مع ضبابية 5 pts.

إذا بدا الشكل غير مركّز، يمكنك تحريك المؤشر باستخدام `builder.MoveTo` قبل الإدراج، أو تعديل خصائص `Left` و `Top` للمستطيل بعد الإدراج.

## أسئلة شائعة & استكشاف الأخطاء

**س: الظل لا يظهر في Word.**  
ج: تأكد من أن `ShadowFormat.Visible` يساوي `true`. كما يجب التحقق من أنك تستخدم نسخة حديثة من Aspose.Words (تم إضافة خاصية الظل في الإصدار 20.3).

**س: هل يمكنني تطبيق تدرج لوني على الظل؟**  
ج: ليس مباشرة عبر `ShadowFormat`. واجهة Word تدعم ظلالًا متدرجة، لكن مخطط Open XML (الذي يتبعه Aspose.Words) يتيح فقط ظلالًا بلون صلب. ستحتاج إلى تعديل XML الأساسي يدويًا — سيناريو أكثر تقدماً.

**س: ماذا لو أحتاج إلى مستطيل شفاف مع ظل فقط؟**  
ج: اضبط `rectangle.FillColor = Color.Transparent;` بعد الإدراج. سيظل الظل يُظهر لأنه مستقل عن التعبئة.

## نصائح للمحترفين في الكود الإنتاجي

- **إعادة استخدام الباني:** إذا كنت تضيف أشكالاً متعددة، احتفظ بنفس نسخة `DocumentBuilder` — إنشاء نسخة جديدة لكل شكل يضيف عبئًا غير ضروري.  
- **حفظ دفعي:** احفظ مرة واحدة بعد جميع التعديلات؛ عمليات الإدخال/الإخراج المتكررة تبطئ إنشاء المستندات الكبيرة.  
- **معالجة الأخطاء:** غلف الكتلة بالكامل بـ `try / catch` وسجّل استثناءات `Aspose.Words`؛ غالبًا ما تحتوي على أرقام سطر مفيدة إذا كان قالب المستند تالفًا.

## الخطوات التالية (مواضيع ذات صلة)

- **كيفية إضافة الظل** إلى الصور أو مربعات النص (استخدام مماثل لـ `ShadowFormat`).  
- **إدراج شكل مستطيل** داخل خلية جدول لتنسيق مخصص للخلية.  
- **إنشاء مستطيل في Word** باستخدام XML الأصلي لـ Word (لمن يفضّل Open XML الخام).  
- **تعيين لون الظل** بشكل ديناميكي بناءً على إدخال المستخدم أو ألوان السمة.

جرّب ألوانًا مختلفة، نصف قطر ضبابية، وإزاحات — ربما توهج أزرق ناعم لتقرير شركة، أو ظل أسود عميق لنشرة إعلانية درامية. الاحتمالات لا حصر لها، وتغييرات الكود قليلة.

---

### ملخص سريع

- قمنا **بإنشاء مستند Word** من الصفر.  
- قمنا **بإدراج شكل مستطيل** وتفعيل ظله.  
- قمنا **بتعيين لون الظل**، الضبابية، والإزاحات للحصول على مظهر احترافي.  
- حفظنا الملف، جاهز للتوزيع.

الآن لديك أساس قوي لإضافة لمسة بصرية لأي مشروع أتمتة Word. هل لديك أفكار أخرى؟ اترك تعليقًا، ولنستمر في النقاش. برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}