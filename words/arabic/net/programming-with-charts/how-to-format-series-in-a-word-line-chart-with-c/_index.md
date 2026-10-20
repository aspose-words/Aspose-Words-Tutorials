---
category: general
date: 2026-09-21
description: كيفية تنسيق السلاسل في مخطط خطي في Word باستخدام C#. تعلم كيفية إنشاء
  مستند Word، وإدراج مخطط خطي، وتطبيق تنسيق رقم مخصص.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: ar
lastmod: 2026-09-21
og_description: كيفية تنسيق السلسلة في مخطط خطي في Word باستخدام C#. يوضح لك هذا الدرس
  كيفية إنشاء مستند Word، وإدراج مخطط خطي، وتطبيق تنسيق رقم مخصص.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: كيفية تنسيق السلاسل في مخطط خطي في Word باستخدام C# – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: كيفية تنسيق السلاسل في مخطط خطي في Word باستخدام C#
url: /ar/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تنسيق السلاسل في مخطط خطي في Word باستخدام C#

إذا كنت بحاجة إلى **كيفية تنسيق السلاسل** في مخطط خطي في Word، فإن هذا الدليل يقدم لك حلاً كاملاً وجاهزًا للتنفيذ. ستتعرف على كيفية **إنشاء مستند Word**، **إدراج مخطط خطي**، و**تطبيق تنسيق رقم مخصص** على قيم Y—كل ذلك باستخدام Aspose.Words for .NET.

تصبح أتمتة Word بسيطة بمجرد أن تفهم نموذج كائن المخطط. بنهاية هذا البرنامج التعليمي ستحصل على ملف Word يحتوي على مخطط خطي تُعرض سلاسل البيانات فيه كنسب مئوية بدقة منزلتين عشريتين.

## ما ستحققه

* إنشاء ملف `.docx` فارغ برمجيًا.  
* إضافة مخطط خطي بحجم 400 × 300 نقطة.  
* الوصول إلى السلسلة البيانات الأولى في المخطط.  
* تطبيق رمز التنسيق `#,##0.00%` لجعل قيم Y تظهر كنسب مئوية.  

لا تحتاج إلى أدوات خارجية بخلاف حزمة Aspose.Words NuGet.

## المتطلبات المسبقة

* .NET 6.0 SDK أو أحدث.  
* Visual Studio 2022 (أو أي بيئة تطوير C#).  
* Aspose.Words for .NET 23.10 أو أحدث – تثبيت عبر `dotnet add package Aspose.Words`.  

يعمل الكود على Windows وLinux وmacOS لأن Aspose.Words مستقل عن المنصة.

## إنشاء مستند Word باستخدام Aspose.Words

الخطوة الأولى هي إنشاء كائن `Document`. هذا الكائن يمثل ملف Word بالكامل في الذاكرة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*لماذا هذا مهم*: `Document` هو نقطة الدخول لجميع عمليات معالجة Word. بدون هذا الكائن لا يمكنك إضافة فقرات أو جداول أو مخططات.

## إدراج مخطط خطي في المستند

يكتب `DocumentBuilder` المحتوى داخل `Document`. استدعاء `InsertChart` ينشئ شكل مخطط على الصفحة الحالية.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*لماذا هذا مهم*: `InsertChart` يُعيد كائن `Chart` يمنحك تحكمًا كاملًا في السلاسل والمحاور والتنسيق. معلمات الحجم تُعبّر بالنقاط (1 نقطة = 1/72 بوصة).

## الوصول إلى السلسلة البيانات الأولى

كل مخطط يحتوي على واحد أو أكثر من `ChartSeries`. السلسلة الأولى في الفهرس 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*لماذا هذا مهم*: كائن `ChartSeries` يحمل قيم Y، قيم X، وخيارات التنسيق لخط واحد في المخطط الخطي. تعديل هذا الكائن يغيّر التمثيل البصري للبيانات.

## تطبيق تنسيق رقم مخصص على السلسلة

خاصية `FormatCode` تتحكم في طريقة عرض القيم الرقمية. ضبطها إلى `#,##0.00%` يُخبر Word بمعالجة القيم كنسب مئوية بدقة منزلتين عشريتين.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*لماذا هذا مهم*: بدون تنسيق مخصص، يعرض Word الأرقام العشرية الخام (مثال: `0.15`). رمز التنسيق يحولها إلى `15.00%`، وهو ما تتطلبه غالبًا التقارير التجارية.

## حفظ المستند والتحقق من النتيجة

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

عند فتح `FormattedSeriesLineChart.docx` في Microsoft Word، سترى مخططًا خطيًا حيث تظهر تسميات المحور Y كـ `15.00%`، `30.00%`، `45.00%`، و`60.00%`. حجم المخطط يطابق الأبعاد المحددة في `InsertChart`.

### لقطة الشاشة المتوقعة

> *صورة: صفحة مستند Word تُظهر مخططًا خطيًا مع قيم محور Y مُنسقة كنسب مئوية.*  
> *(نص بديل: لقطة شاشة لمستند Word يُظهر مخططًا خطيًا مع قيم محور Y مُنسقة كنسب مئوية)*

## الاختلافات الشائعة وحالات الحافة

| الحالة | التعديل |
|-----------|------------|
| **سلاسل متعددة** | تكرار عبر `chart.Series` وتعيين `FormatCode` لكل سلسلة. |
| **نوع مخطط مختلف** | استبدال `ChartType.Line` بـ `ChartType.Column` أو `ChartType.Pie`، إلخ. |
| **فواصل خاصة بالمنطقة** | استخدام سلاسل تنسيق تدعم `CultureInfo`، مثل `"# ##0,00 %"` للغات الفرنسية. |
| **مصدر بيانات ديناميكي** | ملء `series.YValues` من قاعدة بيانات أو ملف CSV قبل تطبيق التنسيق. |

**نصيحة احترافية:** دائمًا قم بتطبيق التنسيق **بعد** إضافة قيم Y. تغيير التنسيق أولاً ثم إضافة القيم يعمل أيضًا، لكن تطبيقه لاحقًا يضمن أن يُطبق التنسيق على مجموعة البيانات النهائية.

## ملخص

أنت الآن تعرف **كيفية تنسيق السلاسل** في مخطط خطي في Word باستخدام C#. شمل البرنامج التعليمي:

* إنشاء مستند Word (`create word document`).  
* إدراج مخطط خطي (`insert line chart`، `add chart to word`).  
* الوصول إلى السلسلة الأولى للمخطط.  
* تطبيق تنسيق رقم مخصص (`apply custom number format`) لعرض النسب المئوية.

## الخطوات التالية

* جرب قيم `ChartType` المختلفة لترى كيف تتصرف التصورات الأخرى.  
* أضف عناوين، تسميات المحاور، وأساطير باستخدام `chart.Title`، `chart.AxisX.Title`، و`chart.AxisY.Title`.  
* صدّر المخطط كصورة (`chart.Save` مع `SaveFormat.Png`) للاستخدام في تقارير الويب.

لا تتردد في تعديل هذا النمط لإنشاء لوحات معلومات، تقارير مالية، أو أي مستند يحتاج إلى رسم مخططات برمجية. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شاملة من الكود مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مخطط خطي في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [إدراج مخطط عمودي في مستند Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [إدراج مخطط مساحة في مستند Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}