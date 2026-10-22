---
category: general
date: 2026-10-13
description: تحديد عدد الفواصل في مخطط الهستوجرام في مستند Word باستخدام C# وإضافة
  تسميات البيانات لتحسين قابلية القراءة. تعلم كيفية تحميل مستند Word باستخدام C# وتحديث
  المخطط.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set histogram bin count
- add data labels histogram
- how to update word chart
- enable chart data labels
- load word document c#
language: ar
lastmod: 2026-10-13
og_description: حدد عدد صناديق الهيستوجرام في مخطط Word باستخدام C# وقم بتمكين تسميات
  البيانات للحصول على بيانات بصرية أوضح. اتبع هذا الدرس الكامل لتحميل مستند Word باستخدام
  C# وتحديث المخطط.
og_image_alt: Screenshot of a Word histogram chart after setting bin count and enabling
  data labels
og_title: تحديد عدد صناديق الهيستوجرام في مخطط Word باستخدام C# – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Set histogram bin count in a Word chart with C# and add data labels
    to improve readability. Learn how to load a Word document C# and update the chart.
  headline: How to set histogram bin count and add data labels in a Word chart using
    C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart manipulation
title: كيفية ضبط عدد الصناديق في المخطط التكراري وإضافة تسميات البيانات في مخطط Word
  باستخدام C#
url: /ar/net/programming-with-charts/how-to-set-histogram-bin-count-and-add-data-labels-in-a-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعيين عدد صناديق المدرج التكراري وإضافة تسميات البيانات في مخطط Word باستخدام C#

إذا كنت بحاجة إلى **تعيين عدد صناديق المدرج التكراري** في مخطط Word، يوضح لك هذا الدليل كيفية القيام بذلك باستخدام C#. ستتعلم أيضًا كيفية **إضافة تسميات البيانات للمدرج التكراري** بحيث تعرض كل صندوق قيمته، مما يجعل المخطط أسهل للقراءة. يعمل الحل مع أي ملف `.docx` يحتوي على مخطط مدرج تكراري، ويستخدم مكتبة Aspose.Words for .NET.

تحديث المخطط هو مهمة شائعة عندما تقوم بإنشاء تقارير تلقائيًا. بحلول نهاية هذا الدليل ستكون قادرًا على **تحميل مستند Word باستخدام C#**، تعديل عدد صناديق المدرج التكراري، تشغيل تسميات البيانات، وحفظ النتيجة دون تعديل يدوي.

## ما ستتعلمه

* كيفية تحميل مستند Word باستخدام C# (`load word document c#`).
* كيفية تحديد موقع أول مخطط مدرج تكراري داخل المستند (`how to update word chart`).
* الخطوات الدقيقة لـ **تعيين عدد صناديق المدرج التكراري** و **تمكين تسميات البيانات في المخطط**.
* نصائح للتعامل مع مخططات متعددة، أنواع مخططات مختلفة، ومشكلات شائعة.

## المتطلبات المسبقة

| المتطلب | لماذا يهم |
|-------------|----------------|
| .NET 6.0 أو أحدث | يوفر بيئة تشغيل Aspose.Words. |
| Aspose.Words for .NET (v23.9 أو أحدث) | يقدم واجهة برمجة `Chart` المستخدمة لتعديل مخططات Word. |
| ملف Word (`input.docx`) يحتوي على مخطط مدرج تكراري | يعمل الكود على مدرج تكراري موجود؛ يمكنك إنشاء واحد يدويًا في Word للاختبار. |
| Visual Studio 2022 (أو أي بيئة تطوير C#) | يجعل من السهل تجميع وتشغيل العينة. |

ثبت حزمة NuGet باستخدام الأمر التالي:

```bash
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** إذا كنت تخطط لمعالجة العديد من المستندات، فعّل ترخيص Aspose.Words لإزالة علامات التقييم.

## الخطوة 1: تحميل مستند Word (load word document c#)

العملية الأولى هي فتح ملف `.docx` الذي يحتوي على المدرج التكراري. يضمن استخدام `Document.Load` توفر جميع أجزاء المستند، بما في ذلك المخططات، في الذاكرة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Path to the source document
string inputPath = @"C:\Docs\input.docx";

// Load the Word document
Document doc = new Document(inputPath);
```

> **لماذا هذه الخطوة مهمة:** تحميل المستند هو الأساس لأي تعديل. إذا تعذر فتح الملف، ستفشل الخطوات اللاحقة مع استثناء `FileNotFoundException`.

## الخطوة 2: تحديد موقع مخطط المدرج التكراري (how to update word chart)

يقوم Word بتخزين المخططات كعقد `Shape`. نحتاج إلى العثور على أول شكل وتحويله إلى `Chart`. إذا كان مستندك يحتوي على مخططات متعددة، يمكنك التكرار عبر جميع الأشكال وفحص `chart.ChartType`.

```csharp
// Retrieve the first shape in the document (depth‑first search)
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Ensure the shape really is a chart
if (shape?.Chart == null)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Cast the shape to a Chart object
Chart histogramChart = shape.Chart;
```

> **حالة حافة:** إذا لم يحتوي المستند على مخطط، فإن `GetChild` يعيد `null`. الفحص أعلاه يمنع استثناء `NullReferenceException`.

## الخطوة 3: تعيين عدد صناديق المدرج التكراري (set histogram bin count)

تتحكم خاصية `BinCount` في دقة العرض البصرية للمدرج التكراري. ضبطها على قيمة أعلى يخلق المزيد من الأعمدة، مما يمكن أن يكشف عن توزيع بيانات أدق.

```csharp
// Verify that the chart is a histogram
if (histogramChart.ChartType != ChartType.Histogram)
{
    throw new InvalidOperationException("The selected chart is not a histogram.");
}

// Set the desired number of bins (e.g., 15)
histogramChart.HistogramChart.BinCount = 15;
```

> **لماذا تحتاج هذا:** تعديل عدد الصناديق يتيح لك تخصيص المخطط للجمهور. عدد أصغر من الصناديق يبسط العرض، بينما عدد أكبر يوفر تفاصيل أكثر.

## الخطوة 4: تمكين تسميات البيانات في المخطط (add data labels histogram / enable chart data labels)

تجعل تسميات البيانات قيمة كل صندوق مرئية مباشرة على المخطط. هذا مفيد بشكل خاص عندما يتم طباعة المدرج التكراري أو تصديره إلى PDF.

```csharp
// Turn on data labels for each bin
histogramChart.HistogramChart.ShowLabels = true;

// Optional: customize label format (e.g., show percentage)
histogramChart.HistogramChart.Labels.NumberFormat = "#,##0";
```

> **نصيحة عملية:** إذا كنت تفضل النسب المئوية بدلاً من العد الخام، اضبط `NumberFormat = "0%"` وغيّر `ShowPercentage = true`.

## الخطوة 5: حفظ المستند المعدل

بعد التغييرات، اكتب المستند مرة أخرى إلى القرص. يمكنك استبدال الملف الأصلي أو إنشاء ملف جديد.

```csharp
// Path to the output document
string outputPath = @"C:\Docs\output.docx";

// Save the updated document
doc.Save(outputPath);
```

فتح `output.docx` في Microsoft Word الآن يظهر مدرجًا تكراريًا بـ 15 صندوقًا وتسمية بيانات مرئية.

## الخطوة 6: التحقق من النتيجة (المخرجات المتوقعة)

للتأكد من نجاح العملية دون فحص بصري، يمكنك قراءة الخصائص برمجيًا مرة أخرى:

```csharp
// Reload the saved file for verification
Document verifyDoc = new Document(outputPath);
Chart verifyChart = ((Shape)verifyDoc.GetChild(NodeType.Shape, 0, true)).Chart;

Console.WriteLine($"BinCount: {verifyChart.HistogramChart.BinCount}");
Console.WriteLine($"ShowLabels: {verifyChart.HistogramChart.ShowLabels}");
```

يجب أن يعرض الطرفية:

```
BinCount: 15
ShowLabels: True
```

إذا تطابقت القيم، فقد تم تحديث المدرج التكراري بشكل صحيح.

## مثال كامل قابل للتنفيذ

بجمع كل شيء معًا، إليك برنامجًا مستقلًا يمكنك نسخه، لصقه، وتشغيله:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string inputPath = @"C:\Docs\input.docx";
        Document doc = new Document(inputPath);

        // ---------- Step 2: Locate the histogram chart ----------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape?.Chart == null)
            throw new InvalidOperationException("No chart found in the document.");

        Chart histogramChart = shape.Chart;

        // ---------- Step 3: Set histogram bin count ----------
        if (histogramChart.ChartType != ChartType.Histogram)
            throw new InvalidOperationException("The chart is not a histogram.");

        histogramChart.HistogramChart.BinCount = 15;

        // ---------- Step 4: Enable chart data labels ----------
        histogramChart.HistogramChart.ShowLabels = true;
        histogramChart.HistogramChart.Labels.NumberFormat = "#,##0";

        // ---------- Step 5: Save the modified document ----------
        string outputPath = @"C:\Docs\output.docx";
        doc.Save(outputPath);

        // ---------- Step 6: Verify the changes ----------
        Document verifyDoc = new Document(outputPath);
        Chart verifyChart = ((Shape)verifyDoc.GetChild(NodeType.Shape, 0, true)).Chart;

        Console.WriteLine($"BinCount: {verifyChart.HistogramChart.BinCount}");
        Console.WriteLine($"ShowLabels: {verifyChart.HistogramChart.ShowLabels}");
    }
}
```

شغّل البرنامج، ثم افتح `output.docx` لرؤية المدرج التكراري المحدث.

## أسئلة شائعة وحالات حافة

| السؤال | الإجابة |
|----------|--------|
| **ماذا لو كان المستند يحتوي على أكثر من مخطط واحد؟** | استخدم `doc.GetChildNodes(NodeType.Shape, true)` لاسترجاع مجموعة، ثم قم بالتكرار وفحص كل `Chart.ChartType`. |
| **هل يمكنني تغيير عرض الصندوق بدلاً من العدد؟** | نعم. استخدم `histogramChart.HistogramChart.BinWidth` لتحديد عرض ثابت؛ سيتم تجاهل ضبط `BinCount`. |
| **هل واجهة البرمجة متوافقة مع .NET Core؟** | تدعم Aspose.Words for .NET .NET Core، .NET 5+، و .NET Framework. يعمل نفس الكود عبر جميع بيئات التشغيل المدعومة. |
| **كيف يمكن إخفاء وسيلة الإيضاح بعد إضافة التسميات؟** | اضبط `histogramChart.Legend.Visible = false;`. هذا يحافظ على نظافة المخطط عندما تكون التسميات تنقل البيانات بالفعل. |

## الخلاصة

أنت الآن تعرف كيفية **تعيين عدد صناديق المدرج التكراري** و **إضافة تسميات البيانات** إلى مخطط Word باستخدام C#. من خلال تحميل المستند، تحديد موقع المدرج، تعديل `BinCount`، تمكين `ShowLabels`، وحفظ الملف، يمكنك أتمتة تحديثات المخططات في أي خط أنابيب تقارير.

من هنا قد ترغب في استكشاف:

* **كيفية تحديث مخطط Word** الألوان والأنماط،
* **تمكين تسميات البيانات في المخطط** لأنواع مخططات أخرى (دائري، شريطي، خطي)،
* إنشاء مخططات من بيانات خام باستخدام Aspose.Words أو Aspose.Cells،
* دمج المستند المحدث في PDF باستخدام Aspose.PDF.

جرّب عددًا مختلفًا من الصناديق وتنسيقات التسميات للعثور على التوازن البصري الذي يخدم جمهورك بأفضل شكل. برمجة سعيدة!  

![Word histogram after

## ماذا يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [تحديث بيانات سلسلة المخطط في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [تعيين تسميات بيانات موحدة في مخطط عمودي باستخدام Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [تعيين الخيارات الافتراضية لتسميات البيانات في مخطط](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}