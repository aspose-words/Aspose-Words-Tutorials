---
category: general
date: 2026-08-07
description: إنشاء مخطط دائري في C# بسرعة. تعلم كيفية إدراج مخطط دائري، إضافة تسميات
  البيانات للمخطط الدائري، عرض النسبة المئوية للمخطط، وتخصيص تسميات بيانات المخطط.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: ar
lastmod: 2026-08-07
og_description: إنشاء مخطط دائري في Word باستخدام C# و Aspose.Words. يوضح هذا الدرس
  كيفية إدراج مخطط دائري، إضافة تسميات البيانات للمخطط الدائري، وعرض النسبة المئوية
  للمخطط مع تخصيص تسميات البيانات للمخطط.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: إنشاء مخطط دائري في C# – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: إنشاء مخطط دائري في C# – دليل خطوة بخطوة
url: /ar/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مخطط دائري في Word باستخدام C# – دليل خطوة بخطوة

إذا كنت بحاجة إلى **إنشاء مخطط دائري في مستندات Word** باستخدام C#، فإن هذا الدليل يقدم حلاً كاملاً جاهزًا للتنفيذ. ستتعرف على كيفية **إدراج مخطط دائري**، **إضافة تسميات البيانات للمخطط الدائري**، و**عرض النسبة المئوية للمخطط** مع **تخصيص تسميات بيانات المخطط** للحصول على مظهر مصقول.

إن إنشاء المخططات برمجيًا يوفر عليك تحريرًا يدويًا، خاصةً عندما يجب إنتاج التقارير أو لوحات المعلومات تلقائيًا. في الأقسام أدناه ستتعلم كل ما يلزم لتضمين مخطط دائري مُعنون بالكامل داخل ملف Word باستخدام Aspose.Words for .NET.

## المتطلبات المسبقة والإعداد

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6.0 SDK أو أحدث مثبت.  
* ترخيص صالح لـ Aspose.Words for .NET (أو مفتاح تقييم مؤقت).  
* Visual Studio 2022 (أو أي بيئة تطوير تدعم C#).  

أضف حزمة NuGet الخاصة بـ Aspose.Words إلى مشروعك:

```bash
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** إذا كنت تخطط لإنشاء العديد من المخططات، فعّل وضع **Free‑Form Drawing** (`DocumentBuilder.UseFreeFormDrawing = true`) لتحسين الأداء.

## إنشاء مخطط دائري في Word باستخدام Aspose.Words

الخطوة الأساسية الأولى هي إنشاء مستند Word فارغ وإنشاء كائن `DocumentBuilder`. هذا الكائن يتحكم في جميع الإدخالات اللاحقة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*لماذا هذا مهم*: `Document` يمثل ملف `.docx` بالكامل، بينما `DocumentBuilder` يوفر API سهل لإضافة الفقرات والجداول والمخططات. البدء بمستند نظيف يضمن عدم وجود تنسيقات مخفية تؤثر على تخطيط المخطط.

## إدراج مخطط دائري في المستند

الآن نضع مخططًا دائريًا بالحجم المطلوب. تُعيد طريقة `InsertChart` كائن `Chart` يمكننا تعديل إعداداته لاحقًا.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*لماذا هذا مهم*: علم `ChartType.Pie` يخبر Aspose.Words بإنشاء مخطط دائري. العرض (`400`) والارتفاع (`300`) يُعبَّران بالنقاط، مما يمنحك تحكمًا دقيقًا في البصمة البصرية للمخطط.

## تعبئة المخطط بالبيانات

يحتاج المخطط الدائري إلى سلسلة واحدة على الأقل من القيم الرقمية. هنا نضيف ثلاث فئات: “Apples”، “Bananas”، و“Cherries”.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*لماذا هذا مهم*: كل استدعاء `AddCategory` يُنشئ شريحة. القيمة الرقمية تحدد حجم الشريحة، بينما يصبح النص هو اسم الفئة المعروض عندما تُفعَّل تسميات البيانات.

## إضافة تسميات البيانات للمخطط الدائري وعرض النسبة المئوية

لجعل المخطط معلوماتيًا، نقوم بتمكين تسميات البيانات، وضعها خارج الشرائح، ونطلب من Aspose.Words عرض كل من اسم الفئة والنسبة المئوية.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*لماذا هذا مهم*: ضبط `Position` إلى `OutsideEnd` يحسن قابلية القراءة، خاصةً عندما تكون الشرائح صغيرة. تمكين `ShowCategoryName` و`ShowPercentage` يحقق متطلبات **show percentage chart** ويُلبي هدف **add data labels pie**.

## تخصيص تسميات بيانات المخطط بشكل إضافي (اختياري)

قد ترغب في تغيير الخط، إضافة خط ربط، أو إخفاء المفتاح (legend). المقتطف التالي يوضح بعض التخصيصات الشائعة:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*لماذا هذا مهم*: تخصيص مظهر التسمية يضمن توافق المخطط مع دليل نمط المستند الخاص بك. إزالة المفتاح يقلل من الفوضى البصرية عندما تنقل تسميات البيانات نفس المعلومات.

## حفظ المستند بالمخطط المخصص

أخيرًا، اكتب المستند إلى القرص. اختر مسارًا لديك صلاحية كتابة فيه.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

عند فتح `ChartWithCustomLabels.docx` في Microsoft Word، سترى مخططًا دائريًا حيث كل شريحة مُعنونة باسم الفئة والنسبة المئوية، موضوعة خارج الشريحة، ومُنسقة بإعدادات الخط المخصصة.

### النتيجة المتوقعة

| الشريحة | القيمة | النسبة المئوية | التسمية المعروضة في Word |
|---------|-------|----------------|---------------------------|
| Apples  | 40    | 40 %           | Apples – 40 %             |
| Bananas | 35    | 35 %           | Bananas – 35 %            |
| Cherries| 25    | 25 %           | Cherries – 25 %           |

يجب أن يبدو المخطط مشابهًا للرسمة أدناه:

![مستند Word يعرض مخططًا دائريًا مع تسميات النسبة المئوية خارج كل شريحة](pie-chart-word.png "Create pie chart word example")

*نص alt للصورة يتضمن الكلمة المفتاحية الأساسية لتحسين محركات البحث.*

## التعامل مع سلاسل متعددة وحالات الحافة

المثال الأساسي يستخدم سلسلة واحدة، وهو ما هو شائع للمخطط الدائري. إذا احتجت إلى عرض سلاسل متعددة (مثلاً مقارنة سنتين)، عليك:

1. استدعاء `chart.Series.Add()` لكل سلسلة إضافية.  
2. التأكد من أن كل سلسلة تستخدم نفس الفئات؛ وإلا سيُطلق Aspose.Words استثناء `ArgumentException`.  
3. اختياريًا، ضبط `labels.ShowSeriesName = true` للتمييز بين الشرائح.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

عند وجود سلاسل متعددة، يُظهر المخطط تلقائيًا كـ **pie clustered** (المعروف أيضًا بـ “pie of pies”). راجع النتيجة للتحقق من وضوح التسميات.

## الأخطاء الشائعة وكيفية تجنّبها

| المشكلة | السبب | الحل |
|---------|-------|------|
| تداخل التسميات مع الشرائح | مساحة المخطط صغيرة أو فئات كثيرة | زيادة أبعاد المخطط (`InsertChart(width, height)`) أو تغيير `Position` إلى `InsideEnd`. |
| النسب المئوية لا تُجموع إلى 100 % | أخطاء تقريب في البيانات | استخدم `labels.ShowPercentage = true` (Aspose.Words يُعيد التطبيع تلقائيًا). |
| المخطط يظهر فارغًا في Word | ترخيص مفقود أو انتهاء مدة التقييم | تأكد من تحميل ترخيص Aspose.Words صالح قبل إنشاء المستند. |
| ألوان الخط تختلف عن سمة Word | ضبط خط مخصص في الكود | أزل إعدادات الخط المخصصة أو طابق ألوان سمة Word (`System.Drawing.Color.Black`). |

## الشيفرة الكاملة (قابلة للتنفيذ)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

تشغيل البرنامج ينتج ملف `ChartWithCustomLabels.docx`، الذي يحتوي على مثال **create pie chart word** يحقق جميع المتطلبات المذكورة في الدليل.

## الخلاصة

أصبحت الآن تعرف كيف **تنشئ مخططًا دائريًا في Word** باستخدام C# وAspose.Words. غطى الدليل إدراج المخطط الدائري، **add data labels pie**، **show percentage chart**، و**customize chart data labels** للحصول على ملف Word احترافي قائم على البيانات.  

من هنا يمكنك استكشاف مواضيع ذات صلة مثل **insert pie chart** في فقرات موجودة، إنشاء مخططات **bar** أو **line**، أو أتمتة إنشاء دفعات من التقارير ببيانات متغيرة. جرّب مواضع تسميات مختلفة، أنماط خطوط، وتكوينات سلاسل متعددة لتخصيص الناتج وفق احتياجاتك التقاريرية.

نتمنى لك رسمًا موفقًا!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تُكمل التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}