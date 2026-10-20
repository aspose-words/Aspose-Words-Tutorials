---
category: general
date: 2026-10-20
description: إنشاء مخطط دائري في مستند Word باستخدام Aspose.Words – دليل خطوة بخطوة
  يوضح كيفية تعيين اللون، وإبراز الشريحة، وحفظ مستند Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: ar
lastmod: 2026-10-20
og_description: إنشاء مخطط دائري في مستند Word باستخدام Aspose.Words. تعلّم كيفية
  تعيين اللون، وإبراز الشريحة، وحفظ مستند Word في مثال واحد قابل للتنفيذ.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: إنشاء مخطط دائري في مستند Word – دليل كامل بلغة C#
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: كيفية إنشاء مخطط دائري في مستند Word باستخدام Aspose.Words
url: /ar/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مخطط دائري في مستند Word باستخدام Aspose.Words

إذا كنت بحاجة إلى **إنشاء مخطط دائري** داخل ملف Word، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. ستتعرف على كيفية تعيين لون مخصص، وتفجير شريحة للتأكيد، وأخيرًا **حفظ مستند Word** مع المخطط المضمن.

إنشاء المخططات برمجيًا يزيل الخطوات اليدوية لفتح Word، وإدراج مخطط، وتعديل مظهره. بنهاية هذا الشرح ستحصل على تطبيق C# Console كامل قابل للتنفيذ يقوم بإنشاء مخطط دائري، وتخصيصه، وكتابة النتيجة إلى القرص.

## المتطلبات المسبقة

* .NET 6.0 SDK أو أحدث مثبت  
* ترخيص صالح لـ Aspose.Words for .NET (أو مفتاح تقييم مجاني)  
* بيئة تطوير متكاملة مثل Visual Studio 2022 أو VS Code  

لا توجد حزم NuGet إضافية مطلوبة بخلاف `Aspose.Words`.

## كيفية إنشاء مخطط دائري في مستند Word

الخطوة الأولى هي إنشاء كائن `Document` و `DocumentBuilder`. يتيح لك الـ builder الوصول إلى ميزات Word عالية المستوى، بما في ذلك إدراج المخططات.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

في هذه المرحلة يحتوي المستند بالفعل على مخطط دائري أساسي. الأقسام التالية تشرح **كيفية تفجير شريحة**، **كيفية تعيين لون**، و **كيفية حفظ مستند Word**.

## كيفية تفجير شريحة للتأكيد

تفجير شريحة يفصلها عن باقي الدائرة، مما يجذب انتباه القارئ. تسمح لك واجهة Aspose.Words API بتحديد مسافة التفجير بالنقاط.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

لماذا نقوم بتفجير الشريحة؟ في التقارير التي تبرز فئة معينة—مثل “المنتج الأكثر مبيعًا”—يساعد الفصل البصري على التعرف الفوري على نقطة البيانات.

## كيفية تعيين لون على شريحة المخطط

الألوان المخصصة تحسن من تناسق العلامة التجارية وقابلية القراءة. يمكنك تعيين أي `System.Drawing.Color` لنقطة بيانات محددة.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

لست مقيدًا بالألوان المعرفة مسبقًا؛ يمكنك إنشاء قيمة `Color.FromArgb` للحصول على درجات دقيقة.

## كيفية حفظ مستند Word مع المخطط

بمجرد أن يصبح المخطط كما تريد، يصبح حفظ الملف أمرًا بسيطًا. تقوم طريقة `Document.Save` بكتابة المستند بالصيغ التي تحددها—هنا نستخدم الصيغة الافتراضية `.docx`.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

تشغيل البرنامج ينشئ الملف `PieChart.docx`. فتح الملف في Microsoft Word يظهر مخططًا دائريًا حيث تم تفجير الشريحة الأولى وتلوينها بالأحمر، تمامًا كما حدد الكود.

### النتيجة المتوقعة

* ملف Word باسم **PieChart.docx** في `C:\Temp`.  
* يحتوي المستند على مخطط دائري واحد، بحجم 400 × 300 نقطة.  
* الشريحة 0 مُزاحة بمقدار 20 نقطة ومملوءة بالأحمر، بينما تحتفظ الشرائح الأخرى باللون الافتراضي.  

يمكنك التحقق من التفجير واللون عن طريق تحديد المخطط في Word وفحص خصائص الشريحة.

## نصائح احترافية ومخاطر شائعة

* **نصيحة احترافية:** إذا كنت بحاجة لتغيير عنوان المخطط أو المفتاح، استخدم خصائص `pieChart.Title.Text` و `pieChart.Legend` قبل الحفظ.  
* **احذر من:** نسيان مسح نقاط البيانات الافتراضية قد يؤدي إلى شرائح إضافية غير مرغوبة. احرص دائمًا على استدعاء `Series[0].DataPoints.Clear()` قبل إضافة بياناتك الخاصة.  
* **نصيحة أداء:** للمستندات الكبيرة، أعد استخدام كائن `DocumentBuilder` واحد بدلاً من إنشاء عدة builders؛ هذا يقلل من استهلاك الذاكرة.

## كيفية إنشاء مخطط باستخدام Aspose.Words (سياق إضافي)

طريقة `InsertChart` تدعم العديد من أنواع المخططات بخلاف المخططات الدائرية، مثل المخططات العمودية، الخطية، والمساحية. لتغيير النوع، استبدل `ChartType.Pie` بالقيمة المطلوبة من الـ enum، مثل `ChartType.Column`. بقية خطوات التخصيص (تفجير الشرائح، تعيين الألوان) تتبع نفس النمط، رغم أن ليس كل أنواع المخططات تعرض خاصية “التفجير”.

## كيفية تفجير شريحة في أنواع مخططات أخرى

فقط المخططات من نوع pie تُظهر طريقة `SetExplosion`. إذا حاولت استدعاؤها على مخطط شريطي، ستطرح الـ API استثناء `ArgumentException`. في هذه الحالات، فكر في استخدام تسميات البيانات أو التعليقات لتسليط الضوء على شريط معين.

## كيفية تعيين لون لسلسلة بدلاً من شريحة واحدة

إذا أردت أن تشترك جميع الشرائح في سلسلة بلون واحد، يمكنك التكرار على نقاط البيانات:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

هذا النهج مفيد عندما تحتاج إلى نظام ألوان موحد عبر مخططات متعددة.

## كيفية حفظ مستند Word بصيغ أخرى

يمكن لـ Aspose.Words التصدير إلى PDF، HTML، والعديد من الصيغ الأخرى. غيّر امتداد الملف في `Save` واختياريًا مرّر كائن `SaveOptions`:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

محرك عرض المخطط يحول المخطط تلقائيًا إلى الصيغة المستهدفة، مع الحفاظ على الألوان وإعدادات التفجير.

## الخلاصة

أنت الآن تعرف كيف **تنشئ مخططًا دائريًا** في مستند Word، وتخصص مظهره عبر **تفجير شريحة** و **تعيين لون**، وأخيرًا **تحفظ مستند Word** مع المخطط المدمج. يزودك هذا المثال المتكامل بأساس قوي لأتمتة إنشاء التقارير، لوحات المعلومات، أو أي سيناريو يتطلب إدراج بيانات بصرية برمجيًا.

### الخطوات التالية

* استكشف أنواع مخططات أخرى (`ChartType.Column`, `ChartType.Line`) لتوسيع مجموعة أدوات التقارير الخاصة بك.  
* اجمع عدة مخططات في مستند واحد لبناء لوحات معلومات شاملة.  
* جرب `ChartDataLabel` لعرض النسب المئوية أو القيم مباشرة على الشرائح.  

لا تتردد في تعديل الكود ليتناسب مع مصادر بياناتك الخاصة—سواءً كنت تستخرج القيم من قاعدة بيانات، أو API، أو ملف CSV، فإن سير عمل Aspose.Words يبقى نفسه. نتمنى لك رسم مخططات ممتع!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Explode Pie Chart Slice in C# with Aspose.Words – Full Guide](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Insert Custom Column Chart in Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}