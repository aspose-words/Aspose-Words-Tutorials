---
category: general
date: 2026-09-21
description: إنشاء مستند Word فارغ وتعلم كيفية إدراج مخطط رادار في ملف Word باستخدام
  DocumentBuilder – دليل خطوة بخطوة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: ar
lastmod: 2026-09-21
og_description: إنشاء مستند Word فارغ وإدراج مخطط راداري في ملف Word باستخدام Aspose.Words.
  اتبع هذا الدليل لإنشاء مخطط مستند Word بسرعة.
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: إنشاء مستند Word فارغ وإضافة مخطط راداري – دليل C# كامل
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: كيفية إنشاء مستند Word فارغ وإضافة مخطط راداري في C#
url: /ar/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word فارغ وإضافة مخطط راداري في C#

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** وإدراج مخطط راداري (مخطط شعاعي)، فإن هذا الدليل يقدم حلاً جاهزًا للتنفيذ. ستتعرف على كيفية استخدام Aspose.Words .NET لإنشاء الملف، وإدراج المخطط، وحفظ النتيجة—كل ذلك في بضع خطوات مختصرة.

يوفر المستند الفارغ مساحة عمل نظيفة لأي سيناريو تقارير آلي، وإضافة مخطط راداري يتيح لك تصور البيانات متعددة الأبعاد مباشرة داخل Word. بنهاية هذا الدليل ستكون قادرًا على توليد مخطط داخل مستند Word دون تعديل يدوي.

## ما ستتعلمه

* كيفية **إنشاء مستند Word فارغ** برمجيًا باستخدام C#.
* الكود الدقيق **لإدراج مخطط راداري** باستخدام `DocumentBuilder`.
* طرق **إدراج مخطط في ملف Word** وتخصيص حجمه.
* كيفية **توليد مخطط مستند Word** والتحقق من النتيجة.
* نصائح **لإضافة مخطط شعاعي إلى ملفات Word**، بما في ذلك الأخطاء الشائعة.

### المتطلبات المسبقة

* .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.6+).
* Aspose.Words for .NET (حزمة NuGet `Aspose.Words` الإصدار 23.9 أو أحدث).
* إلمام أساسي بـ C# وVisual Studio أو أي بيئة تطوير مفضلة لديك.

## إنشاء مستند Word فارغ باستخدام C#

الخطوة الأولى هي إنشاء كائن `Document` فارغ. هذا الكائن يمثل ملف `.docx` فارغ تمامًا.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` ينشئ بنية الملف لكنه لا يحتوي على أي أقسام أو صفحات بعد. تقوم Aspose.Words تلقائيًا بإضافة قسم افتراضي عندما تبدأ في إضافة محتوى، وهذا هو السبب في أن الخطوة التالية تعمل دون إعدادات إضافية.

## كيفية إدراج مخطط راداري في ملف Word

المخطط الراداري (المعروف أيضًا بالمخطط الشعاعي) يوضح نقاط البيانات على محاور تنبع من نقطة مركزية. توفر Aspose.Words الدالة `DocumentBuilder.insertChart` لهذا الغرض.

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` تُعيد كائن `Chart` يمكنك تعديل إعداداته لاحقًا. يظهر المخطط في الصفحة الأولى من المستند الفارغ لأن الـ builder يتم وضعه في بداية المستند بشكل افتراضي.

## إدراج مخطط في ملف Word – إضافة سلاسل البيانات

المخطط بدون بيانات يكون غير مرئي. قم بملء المخطط الراداري بسلسلة أو أكثر لجعله ذو معنى.

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

يمكنك إضافة عدد السلاسل التي تحتاجها. كل سلسلة يمكن أن تحمل اسمًا مميزًا يظهر في وسيلة إيضاح المخطط. تتطابق نقاط البيانات مع المحاور الشعاعية؛ والترتيب الذي تضيفه يحدد موقعها حول الدائرة.

## توليد مخطط مستند Word – حفظ الملف

بعد بناء المخطط، احفظ المستند على القرص. اختر موقعًا لديك صلاحية كتابة فيه.

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

عند فتح ملف `.docx` الناتج في Microsoft Word، سترى صفحة فارغة تحتوي على مخطط راداري بحجم 400 × 300 نقطة، ومملوء بالبيانات النموذجية.

### النتيجة المتوقعة

* ملف `RadialChartExample.docx` على سطح المكتب.
* الصفحة الأولى تحتوي على مخطط راداري بخمس نقاط بيانات معنونة بـ “Series 1”.
* لا يظهر أي نص إضافي لأن المستند بدأ فارغًا.

## إضافة مخطط شعاعي إلى Word – التعامل مع الحالات الشائعة

### 1. تغيير حجم المخطط بعد الإدراج

إذا لم تتناسب الأبعاد الأولية مع تخطيطك، قم بتغيير حجم المخطط كالتالي:

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. إدراج المخطط في موقع محدد

يمكنك نقل مؤشر الـ builder إلى إشارة مرجعية (bookmark) أو خلية جدول أو فقرة قبل استدعاء `InsertChart`.

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. تخصيص مظهر المخطط

تتيح Aspose.Words الوصول إلى نموذج كائن المخطط الكامل، مما يسمح لك بتعيين العناوين، وتسميات المحاور، والألوان.

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. التعامل مع الخطوط المفقودة

إذا كان البيئة المستهدفة تفتقر إلى خط مستخدم في المخطط، تقوم Aspose.Words باستبداله بخط افتراضي. لضمان التناسق، قم بدمج الخطوط المطلوبة:

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. التصدير إلى صيغ أخرى

يمكن حفظ نفس المستند كملف PDF أو HTML أو PNG دون تعديل إضافي في الكود:

```csharp
doc.Save("RadialChartExample.pdf");
```

## مثال كامل قابل للتنفيذ

جمع جميع الأجزاء معًا يمنحك برنامجًا واحدًا يمكنك نسخه، لصقه، وتشغيله.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

شغّل هذا البرنامج، افتح الملف المُولد، وسترى مخطط راداري احترافي جاهز للتوزيع.

## الخلاصة

أنت الآن تعرف كيفية **إنشاء مستند Word فارغ**، **كيفية إدراج مخطط راداري**، و**توليد مخطط مستند Word** باستخدام Aspose.Words. باتباع الخطوات أعلاه يمكنك أيضًا **إضافة مخطط شعاعي إلى ملفات Word** في أي خط أنابيب تقارير آلي، وتخصيص الحجم، والنمط، وتصديره إلى صيغ إضافية.

**الخطوات التالية**

* استكشف أنواع مخططات أخرى (`ChartType.Column`, `ChartType.Pie`) لتوسيع مجموعة أدوات التقارير لديك.
* اجمع عدة مخططات في صفحة واحدة عبر استدعاء `InsertChart` بشكل متكرر.
* دمج البيانات من قاعدة بيانات أو ملف CSV لملء السلاسل بشكل ديناميكي.
* راجع وثائق Aspose.Words للحصول على خيارات تنسيق متقدمة مثل تسميات البيانات الشرطية وقوالب المخططات.

لا تتردد في تجربة الكود، تعديل الأبعاد، أو استبدال البيانات النموذجية ببيانات أعمال حقيقية. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إدراج مخطط عمودي في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [إنشاء مخطط مبعثر في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [إدراج مخطط فقاعة في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}