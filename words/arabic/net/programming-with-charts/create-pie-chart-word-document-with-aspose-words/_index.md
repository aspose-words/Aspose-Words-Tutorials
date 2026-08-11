---
category: general
date: 2026-08-10
description: إنشاء مستند Word يحتوي على مخطط دائري باستخدام Aspose.Words. تعلّم كيفية
  إدراج المخطط، تخصيص ألوان المخطط الدائري، وتغيير لون شريحة الدائرة في C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: ar
lastmod: 2026-08-10
og_description: إنشاء مستند Word يحتوي على مخطط دائري باستخدام Aspose.Words. يوضح
  هذا الدليل كيفية إدراج المخطط، تخصيص ألوان المخطط الدائري، وتغيير لون شريحة الدائرة
  في تطبيق C#.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: إنشاء مخطط دائري في مستند Word – دليل Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: إنشاء مستند Word يحتوي على مخطط دائري باستخدام Aspose.Words
url: /ar/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word يحتوي على مخطط دائري باستخدام Aspose.Words

إذا كنت بحاجة إلى **إنشاء مستند Word يحتوي على مخطط دائري** برمجيًا، فإن هذا الدرس يوضح لك الطريقة بالضبط. سنستعرض إدراج مخطط، **تخصيص ألوان المخطط الدائري**، و**تغيير لون شريحة الدائرة** باستخدام Aspose.Words for .NET.

سترى مثالًا كاملاً قابلاً للتنفيذ يمكنك نسخه إلى Visual Studio، تشغيله، وفتح الملف *.docx* الناتج فورًا للتحقق من المخطط الدائري المنسق. لا حاجة لأي وثائق خارجية—كل ما تحتاجه موجود في هذا الدليل.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6.0 SDK أو أحدث مثبتًا  
* ترخيص صالح لـ Aspose.Words for .NET (أو مفتاح تقييم مؤقت)  
* Visual Studio 2022 (أو أي بيئة تطوير C#)  

يستخدم الكود فقط مساحات الأسماء `Aspose.Words` و `Aspose.Words.Drawing.Charts`، لذا لا توجد حزم NuGet إضافية مطلوبة بخلاف مكتبة Aspose.Words.

## إنشاء مستند Word يحتوي على مخطط دائري – مثال كامل

البرنامج التالي بلغة C# ينشئ مستند Word جديد، يدرج مخططًا دائريًا، ينسق الشريحتين الأوليين، ويحفظ الملف. يتم شرح كل خطوة بالتفصيل.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### شرح كل خطوة

| الخطوة | ما الذي تفعله | لماذا يهم |
|------|--------------|----------------|
| **1** | ينشئ كائن `Document` جديد و `DocumentBuilder`. | يوفر `DocumentBuilder` طرقًا سلسة لإدراج المحتوى، مثل المخططات، في ملف Word. |
| **2** | يستدعي `InsertChart` مع `ChartType.Pie` وحجم ثابت. | `InsertChart` هو **طريقة إدراج المخطط**؛ تحديد العرض/الارتفاع يضمن أن المخطط يتناسب بشكل جيد مع الصفحة. |
| **3** | يضيف سلسلة بيانات بثلاث فئات وقيم رقمية. | المخطط الدائري بدون بيانات يكون غير مرئي؛ تعبئته تُظهر خطوات التنسيق. |
| **4** | يضبط `Explosion` على النقطة الأولى. | تفجير شريحة يجذب الانتباه إلى جزء معين—مفيد لتسليط الضوء على بيانات رئيسية. |
| **5** | يضبط `ForeColor` للنقطتين الأوليين. | هذا هو جوهر **تخصيص ألوان المخطط الدائري**؛ يمكنك استخدام أي `System.Drawing.Color`. |
| **6** | يوضح كيفية **تغيير لون شريحة الدائرة** للشريحات الإضافية. | يبرهن أن التنسيق ليس مقصورًا على الشريحتين الأوليين؛ يمكنك تلوين كل شريحة على حدة. |
| **7** | يحفظ المستند باسم `PieChartStyled.docx`. | يمكن فتح النتيجة النهائية في Microsoft Word أو Google Docs أو أي عارض متوافق. |

#### النتيجة المتوقعة

عند فتح `PieChartStyled.docx` سيظهر صفحة واحدة تحتوي على مخطط دائري بحجم 400 × 300 pt:

* الشريحة 1 (برتقالي) مُنفجرة إلى الخارج.  
* الشريحة 2 (أخضر) تظهر بجوار الشريحة المنفجرة.  
* الشريحة 3 (أزرق فولاذي) تملأ الجزء المتبقي.

يعكس المخطط قيم البيانات (30, 45, 25) والألوان المخصصة التي حددتها.

## كيفية تنسيق الدائرة – نصائح إضافية

* **استخدام ألوان السمة** – بدلاً من كتابة `Color.Orange` صراحةً، يمكنك سحب الألوان من سمة المستند:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **إضافة تسميات البيانات** – إذا أردت إظهار النسب المئوية على المخطط:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **تغيير الحجم ديناميكيًا** – احسب حجم المخطط بناءً على هوامش الصفحة:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

هذه التغييرات توضح مرونة **كيفية تنسيق الدائرة** بعيدًا عن المثال الأساسي.

## أسئلة شائعة

**س: هل يعمل هذا مع .NET Core؟**  
ج: نعم. Aspose.Words for .NET متوافق مع .NET Core، .NET 5، .NET 6، وما بعده. ما عليك سوى الإشارة إلى نفس حزمة NuGet.

**س: ماذا لو أردت مخطط دونات بدلاً من الدائري؟**  
ج: استبدل `ChartType.Pie` بـ `ChartType.Doughnut`. تُطبق نفس واجهات البرمجة (`Explosion`, `ForeColor`) على المخطط الجديد.

**س: هل يمكنني إدراج المخطط في مستند موجود؟**  
ج: افتح الملف الموجود باستخدام `new Document("Existing.docx")`، أنشئ `DocumentBuilder` لهذا المستند، واستدعِ `InsertChart` في الموضع المطلوب.

**س: كيف أتعامل مع مجموعات بيانات كبيرة؟**  
ج: المخططات الدائرية مناسبة لعدد محدود من الفئات (عادةً < 10). إذا كان لديك العديد من الفئات، فكر في استخدام مخطط شريطي أو عمودي بدلاً من ذلك.

## ملخص الكود الكامل

فيما يلي البرنامج الكامل في كتلة واحدة لتسهيل النسخ واللصق:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

تشغيل هذا الكود ينتج مستند Word يحتوي على مخطط دائري منسق كما هو موضح أعلاه.

## الخلاصة

أنت الآن تعرف كيف **تنشئ مستند Word يحتوي على مخطط دائري** باستخدام Aspose.Words، **تخصص ألوان المخطط الدائري**، وت **غير لون شريحة الدائرة** برمجيًا. غطى الدليل إدراج المخطط، تعبئة البيانات، تفجير شريحة، تطبيق ألوان مخصصة، وحفظ النتيجة.  

من هنا يمكنك استكشاف مواضيع ذات صلة مثل **كيفية إدراج مخططات** أخرى غير الدائرية، إضافة وسائط توضيحية، أو إنشاء تقارير متعددة الصفحات تحتوي على مخططات متعددة. جرّب مخططات بألوان وبيانات مختلفة لتتناسب مع احتياجات تقاريرك.

برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف طرق تنفيذ بديلة في مشاريعك.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}