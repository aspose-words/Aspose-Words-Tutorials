---
category: general
date: 2026-09-21
description: تعلم كيفية إنشاء مخطط دائري وإدراج المخطط في Word باستخدام Aspose.Words،
  إضافة تسميات البيانات إلى المخطط الدائري، وعرض النسب المئوية على المخطط الدائري
  في بضع خطوات فقط.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: ar
lastmod: 2026-09-21
og_description: إنشاء مخطط دائري في Word باستخدام Aspose.Words، إدراج المخطط في Word،
  إضافة تسميات البيانات إلى المخطط الدائري، وعرض النسب المئوية على المخطط الدائري—كل
  ذلك مع أمثلة شفرة واضحة.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: إنشاء مخطط دائري في Word باستخدام Aspose.Words – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: كيفية إنشاء مخطط دائري في مستند Word باستخدام Aspose.Words
url: /ar/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مخطط دائري في مستند Word باستخدام Aspose.Words

إذا كنت بحاجة إلى **إنشاء مخطط دائري** برمجيًا، فإن Aspose.Words يجعل العملية بسيطة. في هذا البرنامج التعليمي ستتعرف على كيفية **إدراج مخطط في Word**، وتكوين السلسلة، **إضافة تسميات البيانات إلى المخطط الدائري**، وأخيرًا **عرض النسب المئوية على المخطط الدائري** بحيث ينقل الشكل القيم الدقيقة. في النهاية ستحصل على مثال كامل قابل للتنفيذ يمكنك وضعه في أي مشروع .NET.

يغطي هذا الدليل كل ما تحتاج معرفته: حزم NuGet المطلوبة، الكود الكامل بلغة C#، شرح لماذا كل استدعاء API مهم، ونصائح لتخصيص المخطط. لا تحتاج إلى أي وثائق خارجية—فقط انسخ، شغّل، وعدّل.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6.0 SDK أو أحدث مثبت.  
* Visual Studio 2022 (أو أي بيئة تطوير تدعم .NET).  
* ترخيص Aspose.Words for .NET (الإصدار التجريبي المجاني يكفي للاختبار).  
* إلمام أساسي بـ C# وبُنى مستندات Word.

إذا كان لديك كل ذلك، يمكنك الانتقال مباشرة إلى الكود.

## الخطوة 1: إعداد المشروع واستيراد Aspose.Words

أنشئ مشروع وحدة تحكم جديد وأضف حزمة Aspose.Words عبر NuGet:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

تحتوي الحزمة على مساحة الأسماء `Aspose.Words.Drawing.Charts`، التي تضم الفئات `Chart` و `ChartSeries` التي سنستخدمها.

> **نصيحة احترافية:** احفظ ملف الترخيص (`Aspose.Words.lic`) في جذر المشروع وحمّله عند بدء التشغيل لتجنب علامات مائية التقييم.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## الخطوة 2: إنشاء مستند فارغ وDocumentBuilder

الكائن `Document` يمثل ملف Word، بينما يوفر `DocumentBuilder` واجهة برمجة تطبيقات سلسة لإدراج المحتوى.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**لماذا هذا مهم:** يحافظ `DocumentBuilder` على نقطة الإدراج الحالية، مما يضمن ظهور المخطط بالضبط حيث تريد في تدفق المستند.

## الخطوة 3: إدراج مخطط دائري في مستند Word

الآن **نُدرج مخططًا في Word**. طريقة `InsertChart` تستقبل نوع المخطط، العرض، والارتفاع (بالنقاط).

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

في هذه المرحلة يحتوي المخطط على سلسلة بيانات افتراضية بقيم placeholder (25، 25، 25، 25). يمكنك استبدالها لاحقًا إذا لزم الأمر.

## الخطوة 4: الوصول إلى السلسلة الأولى وتخصيص تسميات البيانات

عادةً ما يحتوي المخطط الدائري على سلسلة واحدة. لإ **إضافة تسميات البيانات إلى المخطط الدائري**، نستعيدها ونفعّل عرض النسبة المئوية.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**لماذا نضبط `ShowPercentage`:** هذه الخاصية تخبر Aspose.Words بحساب مساهمة كل شريحة وعرضها كنسبة مئوية. خاصية `Position` تضمن عدم تداخل التسمية مع الشريحة، مما يحسن القابلية للقراءة—خاصةً عندما تكون الشرائح صغيرة.

## الخطوة 5: (اختياري) استبدال بيانات placeholder

إذا أردت قيمًا محددة، استبدل النقاط الافتراضية:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

ستتعدل النسب المئوية المعروضة تلقائيًا لتعكس القيم الجديدة.

## الخطوة 6: حفظ المستند

أخيرًا، اكتب المستند إلى القرص. الامتداد يحدد الصيغة؛ `.docx` ينتج ملف Word حديث.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

تشغيل البرنامج ينتج ملفًا باسم **PieChart.docx** في مجلد الإخراج. فتحه في Microsoft Word يظهر مخططًا دائريًا مع تسمية كل شريحة بنسبتها المئوية، موضوعة خارج الشرائح.

### النتيجة المتوقعة

عند فتح المستند المُنشأ، يجب أن ترى:

* مخطط دائري واحد، بحجم 400 × 300 pt.  
* أربع شرائح (أو عدد النقاط التي أضفتها).  
* تسميات نسب مئوية مثل “40 %”، “30 %”، إلخ، معروضة خارج كل شريحة.

إذا ظهرت التسميات داخل الشرائح، تحقق من ضبط `ChartDataLabelPosition.OutsideEnd` بشكل صحيح.

## الخطوة 7: التغييرات الشائعة والحالات الخاصة

### إضافة عنوان للمخطط

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### تغيير ألوان الشرائح

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### التعامل مع سلسلة فارغة

إذا كان مصدر البيانات قد يكون فارغًا، احمِ نفسك من `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### تصدير إلى PDF بدلاً من Word

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

منطق رسم المخطط يبقى نفسه؛ Aspose.Words يحول تخطيط Word إلى PDF تلقائيًا.

## قائمة المصدر الكاملة

فيما يلي البرنامج الكامل الجاهز للتنفيذ. انسخه إلى `Program.cs` وشغّله باستخدام `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## الخلاصة

الآن تعرف كيف **تنشئ مخططًا دائريًا** في ملف Word باستخدام Aspose.Words، **تدرج المخطط في Word**، **تضيف تسميات البيانات إلى المخطط الدائري**، و**تعرض النسب المئوية على المخطط الدائري**. يوضح المثال سير العمل الكامل—from إعداد المشروع إلى المستند النهائي—لتتمكن من تكييفه لتقارير، لوحات معلومات، أو إنشاء فواتير تلقائيًا.

بعد ذلك، استكشف المواضيع ذات الصلة مثل **كيفية عرض النسب المئوية في وسوم المخطط**، تخصيص ألوان المخطط، أو تحويل مستند Word إلى PDF للتوزيع. جرّب أنواع مخططات مختلفة (شريطية، خطية) باستخدام نفس طريقة `InsertChart` لتوسيع قدرات الأتمتة لديك.

رسم مخططات سعيد!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إدراج مخطط عمودي في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [إنشاء مخطط مبعثر في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [إدراج مخطط مساحي في مستند Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}