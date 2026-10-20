---
category: general
date: 2026-08-04
description: تتيح لك تخصيص موضع تسمية البيانات للرسوم البيانية في C# وضع التسميات
  في وسط شرائح المخطط. اتبع هذا الدليل خطوة بخطوة باستخدام واجهة برمجة تطبيقات Aspose.Words
  للرسوم البيانية.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: ar
lastmod: 2026-08-04
og_description: يوضح لك تخصيص موضع تسميات البيانات للرسوم البيانية في C# كيفية تمركز
  جميع تسميات البيانات على كل شريحة من رسم بياني في Word. إتقان تموضع تسميات البيانات
  في الرسوم البيانية باستخدام Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: وضع مخصص لتسميات البيانات في المخططات بلغة C# – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: تخصيص موضع تسميات البيانات للمخططات في C#
url: /ar/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تخصيص موضع تسمية البيانات للرسوم البيانية في C#

**Custom Data‑Label Placement for Charts** يتيح لك التحكم بدقة في موضع كل تسمية على رسم بياني داخل مستند Word. في هذا الدرس ستتعلم كيفية توسيط جميع تسميات البيانات على كل شريحة باستخدام C# و Aspose.Words chart API.

ستحصل على مثال كامل قابل للتنفيذ يقوم بتحميل ملف `.docx`، الوصول إلى شكل الرسم البياني الأول، تغيير `Position` لكل تسمية إلى `Center`، وحفظ المستند المحدث. لا توجد مراجع خارجية مطلوبة—فقط مكتبة Aspose.Words for .NET وبيئة تطوير C# أساسية.

**ما ستتعلمه**

* كيفية تحميل مستند Word يحتوي على رسم بياني.  
* كيفية تحديد شكل الرسم البياني باستخدام Aspose.Words chart API.  
* كيفية تطبيق **chart data label positioning** على كل سلسلة في الرسم البياني.  
* كيفية حفظ المستند بحيث تظهر التسميات المتمركزة في Word.  

**المتطلبات المسبقة**

* .NET 6.0 (أو أحدث) مثبتة.  
* Visual Studio 2022 (أو أي بيئة تطوير C#).  
* إشارة إلى حزمة NuGet `Aspose.Words`.  
* ملف Word (`Chart.docx`) يحتوي على رسم بياني واحد على الأقل.

---

## تخصيص موضع تسمية البيانات للرسوم البيانية – الخطوة 1: تحميل المستند

الإجراء الأول هو فتح ملف Word الذي يحتوي على الرسم البياني. `Document` هو نقطة الدخول لأي تعديل باستخدام Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*لماذا هذه الخطوة مهمة*: بدون تحميل المستند لا يمكنك الوصول إلى كائن الرسم البياني. يضمن التحقق من الصحة أن تتلقى رسالة خطأ واضحة إذا كان الملف يفتقر إلى رسم بياني، مما يمنع حدوث مرجع فارغ لاحقًا.

---

## استخدام Aspose.Words chart API للوصول إلى أشكال الرسوم البيانية

تتعامل Aspose.Words مع الرسم البياني ككائن `Chart` متداخل داخل `Shape`. يمكنك استرجاعه عن طريق تحويل النوع للعنصر الفرعي المناسب.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*لماذا هذه الخطوة مهمة*: الوصول المباشر إلى `Chart` يمنحك تحكمًا كاملاً في السلاسل، نقاط البيانات، وخصائص التسميات. إذا لم يكن الشكل رسمًا بيانيًا، يتوقف الكود مبكرًا مع رسالة توضيحية.

---

## ضبط موضع تسمية البيانات في الرسم البياني باستخدام C#

الآن قم بالتكرار عبر كل سلسلة وكل تسمية بيانات، واضبط `Position` إلى `Center`. هذا هو جوهر **Custom Data‑Label Placement for Charts**.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**نصيحة احترافية**: إذا كنت بحاجة إلى موضع مختلف (مثلاً `InsideEnd` لرسم عمودي)، غيّر قيمة التعداد وفقًا لذلك. تعداد `ChartDataLabelPosition` يغطي جميع المواضع القياسية المدعومة من Word.

*لماذا هذه الخطوة مهمة*: تغيير `label.Position` يحدّث تمثيل OOXML الأساسي، بحيث تظهر التسمية متمركزة عند فتح المستند في Microsoft Word.

---

## حفظ مستند Word مع التسميات المحدثة

بعد تعديل الرسم البياني، احفظ التغييرات إلى ملف. يمكنك استبدال الملف الأصلي أو إنشاء نسخة جديدة.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*لماذا هذه الخطوة مهمة*: عملية الحفظ تكتب الـ OOXML المحدث إلى القرص. فتح `ChartLabelsCentered.docx` في Word سيظهر كل تسمية شريحة متمركزة، مما يؤكد نجاح **Custom Data‑Label Placement for Charts**.

---

## الحالات الخاصة والاختلافات

| الحالة | طريقة المعالجة |
|-----------|---------------|
| **رسوم بيانية متعددة** في نفس المستند | كرّر عبر `doc.GetChildNodes(NodeType.Shape, true)` وتحقق من `shape.HasChart` لكل شكل. |
| **أنواع رسوم بيانية مختلفة** (pie, doughnut, bar) | `ChartDataLabelPosition.Center` يعمل مع الرسوم البيانية الدائرية. بالنسبة للرسوم العمودية/الشريطية قد تفضّل `InsideEnd` أو `OutsideEnd`. |
| **نص التسمية يحتاج تنسيقًا** | استخدم `label.TextProperties` لتعيين حجم الخط، اللون، أو الوزن (bold). |
| **التشغيل على .NET Core** | تأكد من الإشارة إلى نسخة .NET Standard من Aspose.Words؛ الـ API هو نفسه. |

---

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه في تطبيق Console. يتضمن جميع توجيهات `using` الضرورية ومعالجة الأخطاء.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**النتيجة المتوقعة**: افتح `ChartLabelsCentered.docx` في Microsoft Word. كل شريحة من الرسم البياني الآن تعرض تسمية البيانات في مركز الشريحة، مما يوفر مظهرًا بصريًا أنظف.

---

## الخلاصة

أصبح لديك الآن حل كامل لـ **Custom Data‑Label Placement for Charts** باستخدام C#. من خلال تحميل المستند، الوصول إلى الرسم البياني عبر Aspose.Words chart API، ضبط `ChartDataLabelPosition.Center` لكل تسمية، وحفظ الملف، يمكنك أتمتة موضع التسميات لأي رسم بياني مبني على Word.

بعد ذلك، استكشف خيارات **chart data label positioning** الأخرى مثل `InsideEnd` أو `OutsideEnd`، أو جرّب **C# chart manipulation** لتغيير الألوان، إضافة أساطير، أو إنشاء رسومات بيانية من الصفر. هذه الإضافات تبني مباشرةً على التقنيات التي تم تغطيتها هنا وتوسّع مهاراتك في أتمتة رسومات Word. Happy coding!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [تخصيص تسمية بيانات الرسم البياني](/words/english/net/programming-with-charts/chart-data-label/)
- [تنسيق عدد تسميات البيانات في الرسم البياني](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [تسمية بيانات الرسم البياني](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}