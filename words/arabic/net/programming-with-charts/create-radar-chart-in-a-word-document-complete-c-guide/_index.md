---
category: general
date: 2026-08-10
description: أنشئ مخطط رادار بسرعة وتعلم كيفية إدراج المخطط في مستند Word باستخدام
  Aspose.Words. اتبع هذا الدليل خطوة بخطوة للحصول على نتائج موثوقة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- insert chart into word document
- how to insert radar chart
language: ar
lastmod: 2026-08-10
og_description: إنشاء مخطط رادار في ملف Word باستخدام Aspose.Words. يوضح هذا الدليل
  كيفية إدراج المخطط في مستند Word وتخصيصه لتقديم واضح.
og_image_alt: Radar chart created in a Word document using Aspose.Words
og_title: إنشاء مخطط رادار في Word – تنفيذ كامل بلغة C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: create radar chart quickly and learn how to insert chart into word
    document using Aspose.Words. Follow this step‑by‑step guide for reliable results.
  headline: create radar chart in a Word document – complete C# guide
  type: TechArticle
- description: create radar chart quickly and learn how to insert chart into word
    document using Aspose.Words. Follow this step‑by‑step guide for reliable results.
  name: create radar chart in a Word document – complete C# guide
  steps:
  - name: Set up the project and add Aspose.Words
    text: '1. Open a new Console App project in Visual Studio. 2. Add the Aspose.Words
      package via NuGet:'
  - name: Create a blank document and a builder
    text: A `Document` represents the .docx file, while `DocumentBuilder` provides
      methods to add content.
  - name: Insert radar chart and obtain the Chart object
    text: The `InsertChart` method inserts a chart placeholder and returns a `Shape`.
      Access the underlying `Chart` to modify its settings.
  - name: Enable graduations on both axes for better readability
    text: Graduations (tick marks) improve data interpretation, especially on radar
      charts where radial spacing matters.
  - name: Define the data series for the radar chart
    text: A radar chart requires a category axis (labels) and one or more data series.
      The example adds a single series named *Series 1*.
  - name: Save the document containing the radar chart
    text: Choose a folder where the output should reside. The file extension `.docx`
      ensures compatibility with Microsoft Word, Google Docs, and LibreOffice.
  type: HowTo
tags:
- Aspose.Words
- C#
- Radar chart
- Word automation
title: إنشاء مخطط رادار في مستند Word – دليل C# الكامل
url: /ar/net/programming-with-charts/create-radar-chart-in-a-word-document-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مخطط رادار في مستند Word – دليل C# كامل

إذا كنت بحاجة إلى **إنشاء مخطط رادار** في ملف Word، فإن هذا الدليل يوضح لك الخطوات الدقيقة. ستتعرف على كيفية **إدراج مخطط في مستند Word** باستخدام Aspose.Words، وتكوين تدرجات المحاور، وإضافة سلاسل البيانات بحيث يكون المخطط جاهزًا للعرض.

إن إنشاء مخطط رادار برمجيًا يزيل الجهد اليدوي في رسم الأشكال ومحاذاة البيانات. بنهاية هذا الدليل ستتمكن من الإجابة على سؤال **كيفية إدراج مخطط رادار** في أي ملف .docx، وتخصيص مظهره، وحفظ النتيجة بسطر واحد من الشيفرة.

## المتطلبات المسبقة

* .NET 6.0 أو أحدث مثبت  
* Visual Studio 2022 (أو أي محرر C#)  
* ترخيص Aspose.Words لـ .NET (الإصدار التجريبي المجاني يعمل للتقييم)  

لا توجد حزم NuGet إضافية مطلوبة بخلاف `Aspose.Words`. تعمل الشيفرة على Windows و macOS و Linux لأن Aspose.Words متعدد المنصات.

## كيفية إنشاء مخطط رادار في مستند Word

يوضح هذا القسم كل عملية مطلوبة **لإنشاء مخطط رادار** من الصفر. يتبع النهج سير العمل النموذجي الموصى به من قبل Aspose.Words: إنشاء `Document`، الحصول على `DocumentBuilder`، إدراج المخطط، تكوين خصائصه، وأخيرًا حفظ الملف.

### الخطوة 1: إعداد المشروع وإضافة Aspose.Words

1. افتح مشروع تطبيق Console جديد في Visual Studio.  
2. أضف حزمة Aspose.Words عبر NuGet:

```bash
dotnet add package Aspose.Words
```

3. إذا كان لديك ملف ترخيص، قم بتحميله في بداية `Main` لتجنب علامات التقييم:

```csharp
// Load license (optional)
Aspose.Words.License license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

**لماذا هذا مهم:** تحميل الترخيص يعطل شريط التقييم ويفتح إمكانيات عرض المخطط بالكامل.

### الخطوة 2: إنشاء مستند فارغ ومُنشئ

`Document` يمثل ملف .docx، بينما `DocumentBuilder` يوفر طرقًا لإضافة المحتوى.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new empty document
Document document = new Document();

// Obtain a builder linked to the document
DocumentBuilder docBuilder = new DocumentBuilder(document);
```

**شرح:** يعمل المُنشئ كالمؤشر؛ كل أمر إدراج يكتب في الموضع الحالي. بدءًا بمستند فارغ يضمن أن يكون مخطط الرادار هو العنصر البصري الأول.

### الخطوة 3: إدراج مخطط رادار والحصول على كائن Chart

طريقة `InsertChart` تُدرج عنصرًا نائبًا للمخطط وتُعيد `Shape`. يمكنك الوصول إلى `Chart` الأساسي لتعديل إعداداته.

```csharp
// Insert a radar chart of 400x300 points
Chart radarChart = docBuilder.InsertChart(ChartType.Radar, 400, 300).Chart;
```

**لماذا هذا يعمل:** `ChartType.Radar` يخبر Aspose.Words بإنشاء مخطط رادار (عنكبوت). تتحكم معلمات الحجم في البصمة البصرية على الصفحة.

### الخطوة 4: تمكين التدرجات على كلا المحورين لتحسين قابلية القراءة

التدرجات (علامات الفواصل) تحسن تفسير البيانات، خاصةً في مخططات الرادار حيث يهم التباعد الشعاعي.

```csharp
// Enable graduations on the radial (X) axis
radarChart.AxisX.HasGraduations = true;
radarChart.AxisX.GraduationLineStyle = LineStyle.Thick;

// Enable graduations on the value (Y) axis
radarChart.AxisY.HasGraduations = true;
radarChart.AxisY.GraduationLineStyle = LineStyle.Thick;
```

**نصيحة احترافية:** استخدام `LineStyle.Thick` يجعل علامات الفواصل بارزة عند طباعة المستند أو عرضه على شاشات عالية الدقة.

### الخطوة 5: تعريف سلاسل البيانات لمخطط الرادار

مخطط الرادار يتطلب محور فئات (تسميات) وسلسلة بيانات واحدة أو أكثر. يضيف المثال سلسلة واحدة باسم *Series 1*.

```csharp
// Remove any default series
radarChart.Series.Clear();

// Add a new series with three categories
radarChart.Series.Add(
    "Series 1",                     // Series name
    new[] { "A", "B", "C" },        // Category labels
    new[] { 10, 20, 15 }            // Corresponding values
);
```

**شرح:** `Series.Add` يربط كل تسمية بقيمة رقمية. يربط المخطط النقاط تلقائيًا، مكونًا الشكل العنكبوتي المميز.

### الخطوة 6: حفظ المستند الذي يحتوي على مخطط الرادار

اختر مجلدًا لحفظ الناتج. امتداد الملف `.docx` يضمن التوافق مع Microsoft Word و Google Docs و LibreOffice.

```csharp
// Save the document with the radar chart
document.Save("RadialChartGraduations.docx");
```

بعد تشغيل البرنامج، افتح `RadialChartGraduations.docx`. سترى مخطط رادار مع تدرجات سميكة على كلا المحورين وسلسلة البيانات معروضة كمتعدد أضلاع مغلق.

![مخطط رادار مع تدرجات](/images/radar-chart.png){: .align-center alt="مخطط رادار تم إنشاؤه في مستند Word باستخدام Aspose.Words" }

**الناتج المتوقع:**  

* مستند Word صفحة واحدة.  
* مخطط رادار بحجم 400 × 300 نقطة ومركز على الصفحة.  
* علامات فواصل سميكة على المحورين الشعاعي والقيمي.  
* سلسلة بيانات واحدة مسماة “Series 1” بالقيم 10، 20، 15.

## كيفية إدراج مخطط في مستند Word – تخصيص إضافي

بينما الخطوات الأساسية أعلاه تجيب على **كيفية إدراج مخطط رادار**، غالبًا ما تحتاج إلى تعديلات إضافية:

| التخصيص | مقتطف الشيفرة | متى يُستخدم |
|---|---|---|
| تغيير عنوان المخطط | `radarChart.Title.Text = "Performance Overview";` | لتوفير سياق للقراء |
| تعيين لون الخلفية | `radarChart.ChartArea.FillFormat.Color = Color.LightYellow;` | للعلامة التجارية أو التباين البصري |
| إضافة سلسلة ثانية | `radarChart.Series.Add("Series 2", new[] {"A","B","C"}, new[] {12,18,22});` | عند مقارنة مجموعات بيانات متعددة |
| ضبط حدود المحور | `radarChart.AxisY.Minimum = 0; radarChart.AxisY.Maximum = 30;` | لإبقاء المخطط ضمن نطاق معروف |

يمكن إدراج هذه المقتطفات بعد **الخطوة 5** وقبل حفظ المستند. إنها توضح التغييرات الشائعة التي يسأل عنها المطورون عندما يبحثون عن **إدراج مخطط في مستند Word**.

## المشكلات الشائعة وكيفية تجنبها

* **غياب الترخيص** – يتم عرض المخطط، لكن تظهر علامة مائية للتقييم. حمّل ترخيصًا صالحًا مبكرًا في `Main`.  
* **حجم المخطط غير صحيح** – استخدام قيم بكسل بدلاً من نقاط يؤدي إلى ناتج مشوه. Aspose.Words يتوقع النقاط (1 pt ≈ 1/72 in).  
* **سلسلة فارغة** – نسيان استدعاء `Series.Clear()` قد يترك بيانات placeholder التي تكتب فوق السلسلة المخصصة.  

معالجة هذه المشكلات تضمن ظهور مخطط الرادار بالضبط كما هو مقصود.

## الخلاصة

أنت الآن تعرف كيف **إنشاء مخطط رادار** في ملف Word باستخدام Aspose.Words لـ .NET. يغطي الدليل كل خطوة من إعداد المشروع إلى حفظ المستند النهائي، ويظهر **كيفية إدراج مخطط رادار**، ويُظهر كيف **إدراج مخطط في مستند Word** مع تدرجات المحاور والبيانات المخصصة. جرب إضافة سلاسل إضافية، وعناوين، وتنسيقات لتكييف المخطط مع احتياجات التقارير الخاصة بك.

**الخطوات التالية**

* استكشف أنواع مخططات أخرى (`ChartType.Pie`، `ChartType.Column`) لتوسيع مجموعة أدوات الأتمتة الخاصة بك.  
* دمج إنشاء المخطط مع دمج البريد للحصول على تقارير مخصصة.  
* راجع وثائق Aspose.Words حول تنسيق المخططات للحصول على خيارات تنسيق متقدمة.  

برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إدراج مخطط منطقة في مستند Word | Aspose.Words لـ .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [إدراج مخطط عمودي في Word باستخدام Aspose.Words لـ .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [إنشاء مخطط مبعثر في Word باستخدام Aspose.Words لـ .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}