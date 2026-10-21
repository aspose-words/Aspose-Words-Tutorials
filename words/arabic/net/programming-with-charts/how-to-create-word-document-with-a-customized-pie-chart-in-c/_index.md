---
category: general
date: 2026-10-07
description: تعلم كيفية إنشاء مستند Word وإدراج مخطط دائري باستخدام Aspose.Words في
  C#. يوضح الدليل أيضًا كيفية إنشاء ملف Word مع تسميات مخطط مخصصة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: ar
lastmod: 2026-10-07
og_description: إنشاء مستند Word وإدراج مخطط دائري في C#. اتبع هذا الدليل خطوة بخطوة
  لإنشاء ملف Word مع تسميات مخطط مخصصة بالكامل.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: إنشاء مستند Word مع مخطط دائري مخصص في C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: كيفية إنشاء مستند Word مع مخطط دائري مخصص في C#
url: /ar/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word مع مخطط دائري مخصص في C#

إذا كنت بحاجة إلى **إنشاء مستند Word** برمجيًا، يوضح لك هذا الدرس كيفية **إدراج مخطط دائري** وتخصيص تسميات البيانات الخاصة به باستخدام Aspose.Words for .NET. ستتعلم أيضًا كيفية **إنشاء ملف Word** يحتوي على مخطط مُنسق بالكامل، بدءًا من إعداد المشروع وحتى حفظ المستند النهائي.

الدليل يمر بكل خطوة مطلوبة لإضافة مخطط، تعديل مواضع التسميات، تمكين خطوط الربط، وأخيرًا حفظ النتيجة كملف `.docx`. لا تحتاج إلى أدوات خارجية بخلاف مكتبة Aspose.Words، وكود المصدر الكامل مُوفر لتتمكن من نسخه ولصقه وتشغيله فورًا.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6.0 SDK أو أحدث مثبتًا  
* ترخيص صالح لـ Aspose.Words for .NET (أو مفتاح تقييم مجاني)  
* بيئة تطوير متكاملة مثل Visual Studio 2022 أو Visual Studio Code  

ستحتاج أيضًا إلى إضافة حزم NuGet التالية إلى مشروعك:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

هذه الحزم تُوفر الفئات `Document` و `DocumentBuilder` والفئات المتعلقة بالمخططات المستخدمة في الأمثلة أدناه.

## إنشاء مستند Word وإضافة مخطط

الخطوة الأولى هي **إنشاء مستند Word** والحصول على كائن `DocumentBuilder` الذي يتيح لك إدراج المحتوى. يعمل الـ builder كالمؤشر داخل المستند.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

كائن `Document` يمثل ملف Word بالكامل، بينما يوفر `DocumentBuilder` طرقًا مثل `InsertChart` التي تضع الكائنات مباشرةً في تدفق المستند.

## إدراج مخطط دائري في المستند

الآن بعد أن أصبح الـ builder جاهزًا، يمكنك **إدراج مخطط دائري** بحجم محدد. يُضاف المخطط في الموضع الحالي للـ builder.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

تُعيد الدالة `InsertChart` كائن `Chart` يمكنك التلاعب به لاحقًا. تُنشئ البيانات التجريبية أربعة شرائح تمثل مبيعات ربع السنة.

## تخصيص تسميات بيانات المخطط الدائري

لجعل المخطط أكثر وضوحًا، غالبًا ما تحتاج إلى **تخصيص تسميات المخطط الدائري**—وضعها خارج الشرائح وإظهار خطوط الربط. هنا يأتي دور `ChartDataLabelCollection`.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

ضبط `Position` إلى `OutsideEnd` ينقل كل تسمية إلى ما وراء حافة الشريحة، بينما `ShowLeaderLines` يرسم خطًا يربط التسمية بشريحتها. العلامات الاختيارية `ShowValue` و `ShowPercentage` تُظهر القارئ كلًا من القيم الفعلية والنسب المئوية.

**نصيحة محترف:** إذا كنت بحاجة لتنسيق خط التسمية، استخدم `dataLabels.Font` لتحديد الحجم واللون والنمط. يضمن ذلك أن يتطابق المخطط مع هوية علامتك التجارية.

## حفظ وتوليد ملف Word

بعد إكمال تكوين المخطط، يمكنك **إنشاء ملف Word** بحفظ كائن `Document` إلى القرص. اختر تنسيق `.docx` لأقصى توافق مع إصدارات Word الحديثة.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

عند فتح `CustomPieChart.docx`، ستظهر مخططًا دائريًا بأربع شرائح، كل واحدة مُسماة خارج الشريحة، متصلة بخطوط ربط، وتعرض كلًا من القيمة والنسبة المئوية.

![لقطة شاشة لمستند Word يحتوي على مخطط دائري مخصص تم إنشاؤه باستخدام C#](image-placeholder.png)

*تُظهر الصورة النتيجة النهائية لدرس **إنشاء مستند Word**.*

## الاختلافات الشائعة والحالات الخاصة

| السيناريو | كيفية تعديل الكود |
|----------|-------------------|
| **سلاسل متعددة** | أضف كائنات `ChartSeries` إضافية إلى `pieChart.Series`. يمكن لكل سلسلة أن تمتلك مجموعة `DataLabels` الخاصة بها لتنسيق مستقل. |
| **حجم مخطط مختلف** | غيّر قيم العرض والارتفاع في `InsertChart(width, height)`. القيم بوحدات النقاط (1 pt ≈ 1/72 in). |
| **عنوان المخطط** | استخدم `pieChart.Title.Text = "Quarterly Sales"` لإضافة عنوان وصفي. |
| **تصدير إلى PDF** | استدعِ `document.Save("Report.pdf", SaveFormat.Pdf);` بعد بناء المخطط. |
| **معالجة الترخيص** | ضع ملف الترخيص الخاص بك (`Aspose.Words.lic`) في مجلد التطبيق وحمّله باستخدام `new License().SetLicense("Aspose.Words.lic");` قبل إنشاء المستند. |

تتيح لك هذه الاختلافات الإجابة على سؤال **كيفية إضافة مخطط دائري** في العديد من السيناريوهات الواقعية، من التقارير البسيطة إلى لوحات التحكم المعقدة.

## الخلاصة

أنت الآن تعرف كيف **تنشئ مستند Word**، **تدرج مخططًا دائريًا**، وت **تخصص تسميات المخطط الدائري** باستخدام Aspose.Words for .NET. يُظهر المثال الكامل سير عمل نظيف: تهيئة المستند، إضافة المخطط، ضبط موضع تسميات البيانات، تمكين خطوط الربط، وأخيرًا **إنشاء ملف Word** يمكن مشاركته مع أي شخص.

جرّب توسيع هذا الدرس بتجربة أنواع مخططات مختلفة (`ChartType.Column`, `ChartType.Line`) أو بتطبيق لوحات ألوان مخصصة لتتناسب مع علامتك التجارية. إذا واجهت أي مشاكل، راجع وثائق Aspose.Words أو استكشف مواضيع ذات صلة مثل “كيفية إضافة مخطط دائري” مع سلاسل متعددة ومصادر بيانات ديناميكية.

برمجة سعيدة، ولا تتردد في مشاركة نتائجك أو طرح أسئلة متابعة في التعليقات!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إدراج مخطط عمودي في مستند Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [إدراج مخطط مساحي في مستند Word](/words/english/net/programming-with-charts/insert-area-chart/)
- [إدراج مخطط مبعثر في مستند Word](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}