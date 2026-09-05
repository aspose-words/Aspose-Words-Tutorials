---
category: general
date: 2026-09-05
description: إنشاء مخطط راداري في Word باستخدام C#. تعلم كيفية إنشاء مستند Word فارغ،
  إضافة مخطط راداري، ضبط حجم المخطط، وتفعيل علامات التحديد بسرعة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: ar
lastmod: 2026-09-05
og_description: إنشاء مخطط راداري في Word باستخدام C#. يوضح لك هذا الدليل كيفية إنشاء
  مستند Word فارغ، إضافة مخطط راداري، ضبط حجم المخطط، وتفعيل علامات الفواصل—كل ذلك
  في دقائق.
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: إنشاء مخطط راداري في Word – دليل C# خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: كيفية إنشاء مخطط راداري وإضافة المخطط إلى Word باستخدام C#
url: /ar/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مخطط راداري وإضافة مخطط إلى Word باستخدام C#

إذا كنت بحاجة إلى **إنشاء مخطط راداري** داخل ملف Word، فإن هذا الدليل سيرشدك خلال العملية بالكامل. ستتعلم كيفية **إنشاء مستند Word فارغ**، وإدراج مخطط راداري، **تحديد حجم المخطط في Word**، وتمكين تدرجات المحور—كل ذلك باستخدام بضع أسطر من كود C#.

إضافة البيانات المرئية إلى التقارير هي متطلب شائع، واستخدام Aspose.Words يجعل الأمر بسيطًا. في الخطوات أدناه نغطي أيضًا كيفية **إضافة مخطط إلى Word** برمجيًا، حتى تتمكن من أتمتة لوحات التحكم، والملخصات المالية، أو أي محتوى قائم على البيانات.

## المتطلبات المسبقة

* .NET 6.0 أو أحدث مثبت  
* ترخيص Aspose.Words for .NET (أو نسخة تجريبية مجانية) – المكتبة توفر فئات `Document` و `DocumentBuilder` وواجهات برمجة التطبيقات الخاصة بالمخططات المستخدمة في هذا الدرس  
* Visual Studio 2022 (أو أي بيئة تطوير C#)  

> **نصيحة احترافية:** إذا كنت تقوم بالاختبار، ضع ملف Aspose.Words DLL في مجلد `bin` الخاص بمشروعك وارجعه عبر NuGet (`Install-Package Aspose.Words`).

## كيفية إنشاء مخطط راداري في مستند Word

الخطوة الأولى هي **إنشاء مستند Word فارغ** سيستضيف المخطط. هذا يمنحك لوحة رسم نظيفة ويسمح لك بالتحكم في بيانات تعريف المستند قبل إضافة أي محتوى.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*لماذا هذا مهم:* كائن `Document` الفارغ يضمن عدم وجود أنماط أو أقسام مخفية تتداخل مع تخطيط المخطط. كما يتيح لك ضبط خصائص المستند (المؤلف، العنوان) لاحقًا إذا لزم الأمر.

## كيفية إضافة مخطط إلى Word باستخدام Aspose.Words

بعد ذلك، أنشئ كائن `DocumentBuilder`. الـ builder هو الأداة الأساسية التي تسمح لك بإدراج النصوص، الصور، والمخططات في المستند.

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

الآن يمكنك **إضافة مخطط راداري** مباشرةً حيث يتم وضع المؤشر. طريقة `InsertChart` تقبل تعداد `ChartType`، العرض، والارتفاع بالنقاط.

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*لماذا 400 × 300؟* هذه الأبعاد توفر مخططًا واضحًا وقابلًا للقراءة على صفحة A4 قياسية. يمكنك تعديل الحجم لاحقًا باستخدام خطوة **تحديد حجم المخطط في Word** إذا كان تخطيطك يتطلب نسبة أبعاد مختلفة.

## ضبط حجم المخطط في Word

إذا كنت بحاجة إلى ضبط الحجم بدقة بعد الإدراج، يمكنك تعديل خصائص `Width` و `Height` للمخطط. هذا مفيد عندما يحدد النص المحيط أو هوامش الصفحة توازنًا بصريًا مختلفًا.

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **ملاحظة:** التحميل الزائد لـ `InsertChart` يحدد الحجم بالفعل، لذا فإن الكود أعلاه اختياري ومُظهر للاكتمال.

## تمكين علامات الفواصل على المحور الشعاعي

المخطط الراداري يكون أكثر فائدة عندما يُظهر المحور الشعاعي تدرجات واضحة. الإعدادات التالية تُفعّل علامات الفواصل وتحدد الفاصل الزاوي بـ 30 درجة، وهو ما يتماشى مع عروض الرادار على نمط البوصلة المعتادة.

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*لماذا هذا مهم:* التدرجات تساعد القراء على تقدير القيم عند كل زاوية، مما يحسن قابلية القراءة لأصحاب المصلحة الذين ليسوا على دراية بالبيانات.

## حفظ المستند الذي يحتوي على المخطط

أخيرًا، احفظ المستند على القرص. يمكنك اختيار أي مجلد تفضله؛ فقط تأكد من وجود المسار.

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

عند فتح `RadialChart.docx` في Microsoft Word، سترى مخططًا راداريًا مُظهرًا بالكامل في وسط الصفحة، بحجم محدد، مع علامات فواصل كل 30 درجة.

### النتيجة المتوقعة

* ملف `.docx` باسم **RadialChart.docx**  
* الصفحة الأولى تحتوي على مخطط راداري بحجم 400 × 300 نقطة  
* المحور X (المحور الشعاعي) يعرض علامات فواصل عند 0°، 30°، 60°، …، 330°  

يمكنك الآن استبدال سلسلة البيانات النائبة بقيمك الخاصة عبر الوصول إلى `radarChart.Series` – لكن ذلك خارج نطاق هذا الدرس الأساسي حول **إضافة مخطط راداري**.

## الاختلافات الشائعة وحالات الحافة

| السيناريو | التعديل |
|----------|------------|
| **نوع مخطط مختلف** | استبدل `ChartType.Radar` بـ `ChartType.Column`، `ChartType.Pie`، إلخ. |
| **مخططات متعددة** | استدعِ `InsertChart` بشكل متكرر؛ كل استدعاء يضع المخطط الجديد بعد السابق. |
| **مجموعات بيانات كبيرة** | استخدم `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` لملء العديد من النقاط. |
| **الحفظ كملف PDF** | استدعِ `document.Save("RadialChart.pdf", SaveFormat.Pdf);` بعد إضافة المخطط. |
| **التشغيل على .NET Core** | تأكد من الإشارة إلى حزمة `Aspose.Words.NETCore`؛ استخدام API هو نفسه. |

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في تطبيق وحدة تحكم. يتضمن جميع الخطوات، وتعديلات الحجم الاختيارية، وتعليقات للتوضيح.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

شغّل البرنامج، افتح الملف الناتج، وسترى المخطط الراداري تمامًا كما هو موصوف.

## الخلاصة

أنت الآن تعرف كيفية **إنشاء مخطط راداري** و**إضافة مخطط إلى Word** باستخدام C#. غطى الدرس إنشاء **مستند Word فارغ**، إدراج مخطط راداري، **تحديد حجم المخطط في Word**، وتمكين تدرجات المحور. مع هذه الأساسيات يمكنك توسيع الحل إلى مخططات متعددة، سلاسل بيانات مخصصة، أو التصدير إلى PDF.

### الخطوات التالية

* استكشف أنواع مخططات أخرى باستخدام `ChartType` (مثل `Bar`، `Line`) – راجع كلمة **add radar chart** للحصول على أمثلة ذات صلة.

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}