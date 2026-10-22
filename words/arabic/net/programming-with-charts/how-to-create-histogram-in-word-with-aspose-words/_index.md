---
category: general
date: 2026-09-21
description: كيفية إنشاء مخطط تكراري في Word باستخدام Aspose.Words. تعلم كيفية ضبط
  فواصل المخطط التكراري وتكوين فواصل المخطط التكراري لتصوير البيانات بدقة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create histogram in word
- how to set histogram bins
- configure histogram bins
language: ar
lastmod: 2026-09-21
og_description: كيفية إنشاء مخطط تكراري في Word باستخدام Aspose.Words. يوضح لك هذا
  الدرس كيفية ضبط فواصل المخطط التكراري وتكوينها للحصول على مخططات دقيقة.
og_image_alt: Screenshot of a Word document showing a histogram chart created with
  Aspose.Words
og_title: إنشاء مخطط تكراري في Word باستخدام Aspose.Words – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  headline: How to create histogram in Word with Aspose.Words
  type: TechArticle
- description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  name: How to create histogram in Word with Aspose.Words
  steps:
  - name: Prepare the development environment.
    text: Prepare the development environment.
  - name: Build a blank Word document and obtain a `DocumentBuilder`.
    text: Build a blank Word document and obtain a `DocumentBuilder`.
  - name: Insert a histogram chart and adjust its properties.
    text: Insert a histogram chart and adjust its properties.
  - name: Save the document and verify the result.
    text: Save the document and verify the result.
  type: HowTo
tags:
- histogram
- Aspose.Words
- C#
- Word automation
title: كيفية إنشاء مخطط تكراري في Word باستخدام Aspose.Words
url: /ar/net/programming-with-charts/how-to-create-histogram-in-word-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مخطط هيستوجرام في Word باستخدام Aspose.Words

إذا كنت بحاجة إلى إنشاء مخطط هيستوجرام في Word، فإن Aspose.Words يجعل العملية مباشرة. يوضح هذا الدليل كل خطوة، من إعداد المشروع إلى تكوين صناديق الهيستوجرام لتقديم البيانات بوضوح. ستتعرف أيضًا على كيفية ضبط صناديق الهيستوجرام وتكوينها لتتناسب مع متطلبات التقارير الخاصة بك.

## كيفية إنشاء مخطط هيستوجرام في Word – سير العمل العام

يتكون سير العمل العام من أربع مراحل منطقية:

1. إعداد بيئة التطوير.  
2. إنشاء مستند Word فارغ والحصول على `DocumentBuilder`.  
3. إدراج مخطط هيستوجرام وضبط خصائصه.  
4. حفظ المستند والتحقق من النتيجة.

يتم تغطية كل مرحلة بالتفصيل أدناه، ويتم توفير الشيفرة المصدرية الكاملة في نهاية المقال.

## إعداد بيئة التطوير

قبل كتابة أي كود، تأكد من توفر المتطلبات المسبقة التالية:

| المتطلب | السبب |
|--------------|--------|
| .NET 6.0 أو أحدث | يوفر بيئة تشغيل لمشاريع C#. |
| Visual Studio 2022 (أو أي بيئة تطوير تدعم .NET) | يتيح لك تجميع وتصحيح العينة. |
| حزمة Aspose.Words for .NET عبر NuGet | تزودك بفئات `Document` و `DocumentBuilder` وفئات المخططات. |

يمكنك إضافة حزمة Aspose.Words باستخدام سطر أوامر NuGet:

```bash
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** استخدم نسخة ثابتة (مثال: `23.9.0`) في بيئة الإنتاج لتجنب التغييرات المفاجئة التي قد تكسر الكود.

## إدراج مخطط هيستوجرام

بعد تجهيز البيئة، أنشئ مشروع وحدة تحكم جديد وافتح ملف `Program.cs`. السطران الأولان من الكود ينشئان مستندًا فارغًا و`DocumentBuilder` يتيح لك تعديل المستند:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank document and a DocumentBuilder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

بعد ذلك، استدعِ `InsertChart` لإضافة هيستوجرام. تتطلب الطريقة نوع المخطط والعرض والارتفاع بالنقاط:

```csharp
// Insert a histogram chart with a specific size (400x300 points)
Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);
```

في هذه المرحلة يحتوي المستند على عنصر نائب فارغ للهيستوجرام. عند فتح ملف *.docx* المُولد، ستظهر منطقة مخطط رمادية جاهزة للبيانات.

![مخطط هيستوجرام كعنصر نائب في مستند Word](/images/histogram-placeholder.png){: .img-fluid alt="لقطة شاشة لمستند Word يظهر عنصر نائب لمخطط هيستوجرام تم إنشاؤه باستخدام Aspose.Words"}

## كيفية ضبط صناديق الهيستوجرام

يقوم الهيستوجرام بتصوير توزيع البيانات الرقمية عن طريق تجميع القيم في *صناديق* (bins). تتحكم خاصية `HistogramBins` في عدد الصناديق التي يعرضها المخطط. ضبط هذه الخاصية قبل إضافة البيانات يضمن أن المخطط يحجز العدد الصحيح من الأعمدة.

```csharp
// Set the number of bins (bars) in the histogram
histogram.HistogramBins = 10;
```

يمكنك تعديل عدد الصناديق ليتناسب مع دقة مجموعة البيانات الخاصة بك. على سبيل المثال، مجموعة بيانات تتراوح من 0 إلى 100 مع عدد صناديق 10 تُنشئ فواصل من 10 وحدات لكل منها (0‑9، 10‑19، …، 90‑100).

> **لماذا هذا مهم:** اختيار عدد قليل جدًا من الصناديق قد يخفي أنماطًا مهمة، بينما اختيار عدد كبير قد ينتج مخططًا صاخبًا. جرّب عدة قيم لتجد النقطة المثالية لبياناتك.

## تكوين صناديق الهيستوجرام لتحسين قابلية القراءة

إلى جانب عدد الصناديق، غالبًا ما ترغب في تسمية كل صندوق حتى يتمكن القارئ من رؤية العدد الدقيق. تتحكم خاصية `ShowBinLabels` في إظهار هذه التسميات:

```csharp
// Display the value of each bin on the chart
histogram.ShowBinLabels = true;
```

عند ضبط `ShowBinLabels` على `true`، يقوم Word بعرض تسمية رقمية فوق كل عمود. هذه الخطوة الصغيرة تحسن بشكل كبير من قابلية تفسير المخطط، خاصة في التقارير التي قد لا يمتلك الجمهور فيها مجموعة البيانات الأصلية.

يمكنك أيضًا تخصيص مظهر التسمية، مثل حجم الخط أو اللون، عبر كائن `HistogramLabel` (متاح في الإصدارات الأحدث من Aspose.Words). يوضح المقتطف التالي تعديلًا شائعًا:

```csharp
// Optional: make bin labels bold and increase font size
histogram.HistogramLabel.Font.Size = 10;
histogram.HistogramLabel.Font.Bold = true;
```

> **حالة خاصة:** إذا ضبطت `HistogramBins` على قيمة أكبر من عدد النقاط البيانات المتميزة، سيظهر بعض الصناديق فارغًا. سيظل المخطط يُعرض بشكل صحيح، لكن المظهر قد يبدو متفرقًا. فكر في تقليل عدد الصناديق في مثل هذه السيناريوهات.

## إضافة سلسلة بيانات إلى الهيستوجرام

يتطلب الهيستوجرام سلسلة بيانات واحدة تمثل القيم الرقمية الأساسية. يمكنك ملء السلسلة باستخدام مصفوفة، أو `List<double>`، أو أي مجموعة قابلة للتعداد. المثال المختصر أدناه يضيف مجموعة بيانات عشوائية:

```csharp
// Create a data series for the histogram
ChartSeries series = histogram.Series[0];
double[] sampleData = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
series.DataPoints.AddRange(sampleData);
```

تحول طريقة `AddRange` كل قيمة إلى صندوق وفقًا للـ `HistogramBins` المحدد مسبقًا. بعد هذه الخطوة، يعرض المخطط هيستوجرامًا مكتملًا.

## حفظ المستند وعرض النتيجة

أخيرًا، اكتب المستند إلى القرص. يمكنك اختيار أي موقع يمكن لتطبيقك الوصول إليه. السطر التالي يحفظ الملف باسم `output.docx`:

```csharp
// Save the document so you can view the chart
doc.Save("output.docx");
```

افتح `output.docx` في Microsoft Word لتشاهد هيستوجرامًا يحتوي على عشرة صناديق، مع قيم مسماة، والبيانات التجريبية التي زودتها. سيشبه المخطط الصورة أدناه:

![الهيستوجرام المكتمل في Word](/images/histogram-complete.png){: .img-fluid alt="مستند Word يعرض مخطط هيستوجرام مكتمل مع عشرة صناديق وتسميات"}

## مثال كامل قابل للتنفيذ

بجمع جميع الأجزاء معًا، إليك برنامج مستقل يمكنك نسخه، لصقه، وتشغيله:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a histogram chart (400×300 points)
        Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);

        // 3️⃣ Configure the histogram
        histogram.HistogramBins = 10;          // How to set histogram bins
        histogram.ShowBinLabels = true;       // Configure histogram bins to show labels
        histogram.HistogramLabel.Font.Size = 10;
        histogram.HistogramLabel.Font.Bold = true;

        // 4️⃣ Add a data series
        ChartSeries series = histogram.Series[0];
        double[] data = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
        series.DataPoints.AddRange(data);

        // 5️⃣ Save the document
        doc.Save("output.docx");
    }
}
```

**الناتج المتوقع:** عند فتح `output.docx` سيظهر هيستوجرام بعشرة أعمدة متساوية المسافات، كل عمود مسمى بعدده. يعكس المخطط توزيع مصفوفة `data`، مما يجعل الاتجاهات واضحة على الفور.

## أسئلة شائعة وحلول المشكلات

| السؤال | الجواب |
|----------|--------|
| *ماذا لو احتجت إلى أكثر من سلسلة بيانات؟* | عادةً ما يمثل الهيستوجرام توزيعًا واحدًا. إذا احتجت إلى عدة سلاسل، ففكر في استخدام مخطط عمودي (column chart) بدلاً من ذلك. |
| *هل يمكنني تغيير حجم المخطط بعد الإدراج؟* | نعم. عدّل خصائص `histogram.Width` و `histogram.Height`، أو استدعِ `builder.InsertChart` مرة أخرى بأبعاد مختلفة. |
| *هل يعمل هذا مع .NET Framework 4.8؟* | بالتأكيد. يدعم Aspose.Words .NET Framework 4.5 وما بعده، لذا يعمل نفس الكود دون تعديل. |
| *كيف يمكنني تصدير المخطط كصورة؟* | استخدم `histogram.ToImage()` للحصول على `System.Drawing.Image`، ثم احفظه باستخدام `image.Save("chart.png")`. |

## الخلاصة

أصبحت الآن تعرف كيفية إنشاء مخطط هيستوجرام في Word باستخدام Aspose.Words، وكيفية ضبط صناديق الهيستوجرام، وكيفية تكوينها لإنتاج مخرجات واضحة وموسومة. يوضح المثال الكامل نهجًا جاهزًا للإنتاج يمكنك تكييفه مع أي سيناريو تقارير يعتمد على البيانات.  

بعد ذلك، استكشف المواضيع ذات الصلة مثل **كيفية إنشاء مخططات دائرية في Word**، **تخصيص ألوان المخططات**، و**دمج مصادر بيانات Excel**. كل منها يبني على نفس سير عمل `DocumentBuilder`، لذا يمكنك توسيع الحل بجهد قليل.

رسم مخططات سعيد!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [how to create pdf from Word – Complete C# Guide](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [How to Load Word Documents Using Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}