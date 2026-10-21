---
category: general
date: 2026-07-26
description: إدراج مخطط دائري في مستند Word باستخدام Aspose.Words. تعلّم كيفية إضافة
  المخطط، تفجير الشريحة، وعرض النسب المئوية في بضع خطوات فقط.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: ar
lastmod: 2026-07-26
og_description: إدراج مخطط دائري في ملف Word باستخدام Aspose.Words. اتبع هذا الدليل
  لتتعلم كيفية إضافة المخطط، تفجير الشريحة، وعرض النسب المئوية بسرعة.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: إدراج مخطط دائري في Word – دليل Aspose.Words خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: إدراج مخطط دائري في Word باستخدام Aspose.Words – دليل كامل
url: /ar/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج مخطط دائري في Word باستخدام Aspose.Words – دليل كامل

هل احتجت يوماً إلى **إدراج مخطط دائري** في تقرير Word لكن لم تكن متأكدًا من أين تبدأ؟ لست وحدك. في العديد من تطبيقات الأعمال، يضيف المخطط الدائري تأثيرًا بصريًا يجعل البيانات سهلة الفهم فورًا، وتتيح لك Aspose.Words ذلك ببضع أسطر من الشيفرة.

في هذا الدرس سنستعرض الخطوات الدقيقة لـ **add chart to Word**, لتفجير شريحة لتسليط الضوء، وعرض النسب المئوية على تسميات البيانات. في النهاية ستحصل على مثال جاهز للتنفيذ يمكنك إدراجه في أي مشروع .NET.

---

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل مع .NET Core و .NET Framework على حد سواء)
- حزمة Aspose.Words for .NET NuGet مثبتة  
  ```bash
  dotnet add package Aspose.Words
  ```
- فهم أساسي لصياغة C# — لا حاجة لأي شيء معقد
- بيئة تطوير متكاملة (IDE) من اختيارك (Visual Studio، Rider، أو VS Code)

هذا كل شيء. لنبدأ بالعمل.

---

## إدراج مخطط دائري في مستند Word

أول شيء نحتاجه هو كائن `Document` جديد و`DocumentBuilder`. فكر في الـ builder كقلم يكتب مباشرةً على لوحة Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **لماذا هذا مهم:** يمثل الـ `Document` ملف .docx بالكامل، بينما يوفّر الـ `DocumentBuilder` API مريحة لإدراج عناصر مثل المخططات والجداول والنص. هذا هو الأساس لكل عملية **how to add chart**.

---

## كيفية إضافة مخطط إلى Word

الآن بعد أن لدينا builder، يمكننا فعليًا **insert pie chart**. طريقة `insertChart` تأخذ نوع المخطط والأبعاد المطلوبة بالنقاط (1 نقطة = 1/72 بوصة).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **نصيحة:** إذا كنت بحاجة إلى حجم مختلف، فقط عدّل قيم العرض والارتفاع. سيقوم المخطط تلقائيًا بتعديل حجمه ليتناسب مع هوامش الصفحة.

---

## كيفية تفجير شريحة للتأكيد

تعديل بصري شائع هو “تفجير” شريحة لتخرج من الدائرة. هذا يجذب انتباه القارئ إلى أهم جزء.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **لماذا تفجير شريحة؟** عندما تريد إبراز فئة معينة — مثلاً “إيرادات الربع الأول” في تقرير مالي — فإن تفجير الشريحة يجعلها ملحوظة فورًا دون الحاجة إلى نص إضافي.

---

## كيفية عرض النسب المئوية على تسميات البيانات

تبدو معظم المخططات الدائرية أفضل عندما تعرض كل شريحة نسبتها المئوية. تتيح لك Aspose.Words تفعيل ذلك بخاصية واحدة.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **ملاحظة سريعة:** علم `ShowPercentage` يعمل على جميع النقاط في السلسلة، لذا لا تحتاج إلى ضبطه لكل شريحة.

---

## حفظ المستند الذي يحتوي على المخطط

أخيرًا، نقوم بكتابة المستند إلى القرص. اختر أي مجلد تفضله؛ فقط تأكد من أن المسار موجود.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

عند فتح `PieChart.docx` في Microsoft Word سترى مخططًا دائريًا مُصممًا بدقة مع تفجير الشريحة الأولى وعرض النسب المئوية — تمامًا ما تتوقعه من تقرير أعمال مصقول.

---

## مثال كامل يعمل

فيما يلي البرنامج الكامل جاهز للنسخ واللصق. شغّله كتطبيق كونسول وتحقق من ملف الإخراج.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**النتيجة المتوقعة:** افتح ملف `PieChart.docx` المُولد. سترى مخططًا دائريًا من ثلاث شرائح بعنوان “Sales Q1”، مع تفجير الشريحة الأولى وتسمية كل شريحة بـ “30 %”، “45 %”، و “25 %”. الشكل يتطابق مع البيانات التي أدخلناها.

---

## أسئلة شائعة وحالات خاصة

- **ماذا لو احتجت إلى أكثر من سلسلة واحدة؟**  
  فقط أضف كائنات `ChartSeries` إضافية إلى `chart.Series`. يمكن لكل سلسلة أن تمتلك مجموعة بياناتها الخاصة، ألوانها، وإعدادات التفجير.

- **هل يمكنني تغيير ألوان المخطط؟**  
  نعم. كل `ChartPoint` يحتوي على خاصية `Format.Fill.ForeColor` يمكنك تعيينها إلى أي `System.Drawing.Color`.

- **ماذا عن أنواع المخططات المختلفة؟**  
  تشمل تعداد `ChartType` المخططات الشريطية، الخطية، الدونت، والعديد غيرها. استبدل `ChartType.Pie` بأي نوع بصري تحتاجه.

- **هل يمكن تعديل المخطط في Word بعد الإدراج؟**  
  بالتأكيد. يتعامل Word مع المخطط كأنه مخطط Office أصلي، لذا يمكن للمستخدمين النقر المزدوج عليه لفتح محرر المخطط المدمج.

---

## الخلاصة

أنت الآن تعرف بالضبط كيفية **insert pie chart** في مستند Word باستخدام Aspose.Words، **how to add chart to word**، **how to explode slice**، و **how to show percentages** على تسميات البيانات. المثال الكامل أعلاه جاهز للتنفيذ، ويمكنك توسيعه ببيانات مخصصة أو تنسيقات أو سلاسل إضافية.

هل أنت مستعد للخطوة التالية؟ جرّب استبدال المخطط الدائري بمخطط دونت، أو أنشئ دفعة من التقارير ببيانات مختلفة تلقائيًا. إذا كنت مهتمًا بتصورات أخرى، اطلع على أدلّتنا حول **how to add chart** للمخططات الشريطية والخطية، أو استكشف مرجع API **add chart to word** لتخصيصات أعمق.

برمجة سعيدة، ولتكن مستنداتك دائمًا واضحة كقطعة فطيرة مقطعة بدقة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إدراج مخطط عمودي في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [إدراج مخطط مساحة في مستند Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [إنشاء مخطط مبعثر في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}