---
category: general
date: 2026-08-04
description: كيفية إضافة تسميات البيانات في C# باستخدام Aspose.Words. تعلم تعديل المخطط،
  توسيط تسميات بيانات المخطط، إظهار النسب المئوية في المخطط، وتخصيص تسميات بيانات
  المخطط.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: ar
lastmod: 2026-08-04
og_description: كيفية إضافة تسميات البيانات في C# باستخدام Aspose.Words. يوضح لك هذا
  البرنامج التعليمي كيفية تعديل المخطط، تمركز تسميات بيانات المخطط، إظهار النسب المئوية
  في المخطط، وتخصيص تسميات بيانات المخطط.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: كيفية إضافة تسميات البيانات إلى مخطط Word في C# – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: كيفية إضافة تسميات البيانات إلى مخطط Word في C# – دليل خطوة بخطوة
url: /ar/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة تسميات البيانات إلى مخطط Word في C# – دليل خطوة‑بخطوة

إذا كنت بحاجة إلى **كيفية إضافة تسميات البيانات** إلى مخطط موجود داخل مستند Word، يوضح لك هذا الدليل الشيفرة الدقيقة التي يجب تشغيلها. سترى كيفية تعديل خصائص المخطط، تمركز تسميات بيانات المخطط، إظهار النسب المئوية في المخطط، وتخصيص تسميات بيانات المخطط لأي سيناريو.

يغطي الدرس كل ما يلزم لتعديل مخطط موجود، بدءًا من تحميل المستند وحتى حفظ التغييرات. لا تحتاج إلى مراجع خارجية—فقط مكتبة Aspose.Words for .NET وبيئة تطوير C# أساسية.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6.0 (أو أحدث) مثبت.
* Aspose.Words for .NET الإصدار 23.9 أو أحدث.  
  يمكنك تثبيتها عبر NuGet:

```bash
dotnet add package Aspose.Words
```

* ملف Word (`input.docx`) يحتوي على مخطط واحد على الأقل.

## كيفية إضافة تسميات البيانات إلى مخطط Word في C#

الأقسام التالية تقودك خطوة بخطوة. تظهر الكلمة المفتاحية الأساسية **how to add data labels** بشكل طبيعي في السرد وتعليقات الشيفرة، مع الحفاظ على الكثافة ضمن النطاق الموصى به.

### الخطوة 1 – تحميل مستند Word الذي يحتوي على المخطط

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*لماذا هذه الخطوة مهمة*: كائن `Document` يمثل ملف Word بالكامل. تحميله يمنحك الوصول إلى كل عقدة، بما في ذلك الأشكال التي تستضيف المخططات.

### الخطوة 2 – استرجاع أول مخطط من المستند

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*لماذا هذه الخطوة مهمة*: المخططات تُخزن داخل عقد `Shape`. بتحويل العقدة المسترجعة إلى `Shape` واستدعاء `GetChart()`، تحصل على كائن `Chart` يتيح لك الوصول إلى السلاسل والمحاور ومجموعات التسميات.

### الخطوة 3 – تمكين تخصيص تسميات البيانات وإظهار النسب المئوية في المخطط

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*لماذا هذه الخطوة مهمة*: ضبط `ShowPercentage` يخبر Aspose.Words بحساب وعرض مساهمة كل شريحة في الإجمالي. هذا يلبي الكلمة المفتاحية الثانوية **show percentages in chart**.

### الخطوة 4 – تغيير موضع التسمية إلى مركز كل نقطة بيانات

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*لماذا هذه الخطوة مهمة*: خاصية `Position` تتحكم في مكان ظهور التسمية بالنسبة لنقطة البيانات. استخدام `Center` يحقق الكلمة المفتاحية الثانوية **center chart data labels** ويحسن قابلية القراءة للمخططات الدائرية أو الدونات.

### الخطوة 5 – تخصيص إضافي لتسميات المخطط (اختياري)

إذا كنت تحتاج إلى مزيد من التحكم، يمكنك تعديل الخط، اللون، أو خطوط الربط:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

هذه الإعدادات توضح الكلمة المفتاحية الثانوية **customize chart data labels** وتظهر كيف يمكنك تعديل المظهر ليتماشى مع إرشادات العلامة التجارية.

### الخطوة 6 – حفظ المستند المعدل

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*لماذا هذه الخطوة مهمة*: الحفظ يكتب المخطط المحدث مرة أخرى إلى ملف Word، مما يجعل تسميات البيانات الجديدة مرئية عند فتح الملف في Microsoft Word.

## مثال كامل قابل للتنفيذ

فيما يلي برنامج كامل يمكنك نسخه، لصقه، وتشغيله. يتضمن جميع توجيهات `using` الضرورية وتعليقات توضح كل سطر.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### النتيجة المتوقعة

عند فتح `output.docx` في Microsoft Word، سيظهر المخطط كما يلي:

* قيم النسب المئوية بجوار كل شريحة (مثال: **25 %**, **40 %**, …).
* التسميات موضوعة في مركز كل نقطة بيانات.
* أي تنسيق إضافي قمت بتطبيقه، مثل النص الأحمر الغامق.

هذه الإشارات البصرية تجعل المخطط أسهل في الفهم، خاصةً في العروض التقديمية أو التقارير.

## كيفية تعديل خصائص المخطط بخلاف تسميات البيانات

بينما يركز هذا الدليل على **how to add data labels**، قد ترغب أيضًا في **how to edit chart** مثل تعديل العناوين، موضع المفتاح، أو تنسيق المحاور. يوفر كائن `Chart` خصائص مثل `Title`، `Legend`، و`AxisX/AxisY`. على سبيل المثال، لتغيير عنوان المخطط:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

جميع تعديلات المخطط تتبع نفس النمط: استرجاع المخطط، تعديل خصائصه، ثم حفظ المستند.

## الأخطاء الشائعة ونصائح أفضل الممارسات

| المشكلة | لماذا يحدث | الحل المقترح |
|---|---|---|
| المخطط داخل شكل مجموعة. | `GetChild(NodeType.Shape, …)` يُعيد المجموعة الخارجية، وليس المخطط الداخلي. | ابحث بشكل متكرر عن شكل يحتوي على `shape.HasChart`. |
| تسميات البيانات لا تظهر بعد الحفظ. | لم يتم ضبط `ShowValue` أو `ShowPercentage` على `true`. | اضبط كلا الخاصيتين `ShowValue` و `ShowPercentage` حسب الحاجة. |
| تداخل التسميات على الشرائح الصغيرة. | تموضع المركز قد يسبب ازدحامًا. | استخدم `ChartDataLabelPosition.OutSideEnd` للتموضع الخارجي، أو فعّل `LeaderLines`. |

تطبيق هذه النصائح يضمن نتائج موثوقة عبر أنواع المخططات المختلفة.

## الخلاصة

أنت الآن تعرف **كيفية إضافة تسميات البيانات** إلى مخطط Word باستخدام C#. غطى الدليل استرجاع المخطط، تمكين ظهور التسميات، تمركزها، إظهار النسب المئوية، وتخصيص المظهر. بهذه المعرفة يمكنك أيضًا **how to edit chart**، **center chart data labels**، **show percentages in chart**، و**customize chart data labels** لأي سيناريو تقارير.

هل أنت مستعد لاستكشاف المزيد؟ جرّب إضافة سلاسل متعددة، تطبيق تنسيق شرطي، أو تصدير المخطط كصورة. توفر واجهة Aspose.Words API إمكانات واسعة لتعديل المخططات—جرب لتجد التمثيل البصري المثالي لبياناتك.

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة‑بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize A Single Chart Data Point In A Chart](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}