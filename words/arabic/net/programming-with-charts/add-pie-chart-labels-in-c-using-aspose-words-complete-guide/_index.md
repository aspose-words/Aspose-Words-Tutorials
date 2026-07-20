---
category: general
date: 2026-07-20
description: أضف تسميات مخطط دائري باستخدام Aspose.Words لـ .NET. تعلم كيفية تغيير
  تسميات المخطط الدائري، وعرض تسميات النسبة المئوية، وتحديث تسميات سلاسل المخطط بسرعة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: ar
lastmod: 2026-07-20
og_description: إضافة تسميات المخطط الدائري في C# باستخدام Aspose.Words. إتقان تعديل
  تسميات المخطط الدائري، عرض تسميات النسبة المئوية، وتحديث تسميات سلاسل المخطط في
  بضع خطوات فقط.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: إضافة تسميات مخطط دائري في C# – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: إضافة تسميات مخطط دائري في C# باستخدام Aspose.Words – دليل شامل
url: /ar/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة تسميات مخطط الفطيرة في C# باستخدام Aspose.Words – دليل شامل

هل تحتاج إلى **إضافة تسميات مخطط الفطيرة** إلى مستند Word باستخدام C#؟ مع Aspose.Words يمكنك بسهولة **تغيير تسميات مخطط الفطيرة** و**عرض نسب مخطط الفطيرة** مباشرة داخل الملف—بدون الحاجة إلى تعديل يدوي في Word.  

في هذا الدرس سنستعرض الخطوات الدقيقة لـ **إظهار تسميات النسبة المئوية**، وإعادة وضعها، وحتى **تحديث تسميات سلاسل المخطط** للبيانات الديناميكية. في النهاية ستحصل على مقطع شفرة قابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع .NET.

> **معاينة سريعة:** بعد اتباع الدليل، سيفتح الملف `.docx` المحفوظ سيظهر مخطط فطيرة حيث يتم تسمية كل شريحة بنسبتها المئوية، موضوعة خارج الشريحة لأقصى وضوح.

---

## ما ستحتاجه

- **Aspose.Words for .NET** (أحدث نسخة حتى عام 2026). يمكنك الحصول عليها من NuGet: `Install-Package Aspose.Words`.
- **مستند Word** يحتوي بالفعل على مخطط فطيرة أو دونات (سنسميه `Chart.docx`).
- إلمام أساسي بـ **C#** وVisual Studio (أو بيئة التطوير المفضلة لديك).

هذا كل شيء—بدون مكتبات إضافية، بدون COM interop، فقط شفرة مُدارة صافية.

## إضافة تسميات مخطط الفطيرة – التنفيذ الكامل

فيما يلي برنامج **كامل وقابل للتنفيذ** بلغة C# يعمل على تحميل مستند، تعديل أول مخطط فطيرة، وحفظ النتيجة. كل سطر مُعلق لتفهم **سبب** ما نقوم به، وليس فقط **ما** نقوم به.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### النتيجة المتوقعة

افتح `ChartWithCustomLabels.docx` في Microsoft Word. يجب أن ترى مخطط الفطيرة **مع تسميات النسبة المئوية موضوعة خارج كل شريحة**. تبدو التسميات مثل “35 %”، “20 %”، إلخ، مما يجعل المخطط مفهومًا فورًا.

---

## تغيير تسميات مخطط الفطيرة: التموقع والتنسيق

إذا كنت تحتاج فقط إلى **تغيير تسميات مخطط الفطيرة** دون إظهار النسب المئوية، يمكنك تعديل خاصية `Position` إلى أحد القيم التالية:

| تعداد الموضع | التأثير البصري |
|---------------|---------------|
| `InsideEnd`   | التسميات داخل الشريحة، عند الحافة مباشرة. |
| `Center`      | التسميات تظهر في وسط الشريحة (مناسب للفطائر الصغيرة). |
| `OutsideEnd`  | التسميات خارج الشريحة، متصلة بخط ربط (الإعداد الافتراضي). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**نصيحة احترافية:** `OutsideEnd` يعمل بأفضل شكل عندما يحتوي المخطط على العديد من الشرائح؛ فهو يمنع تداخل النص.

## إظهار تسميات النسبة المئوية على مخطط الفطيرة

خاصية `ShowPercentage` هي **علامة منطقية**. ضبطها على `true` يخبر Aspose.Words بحساب مساهمة كل شريحة بناءً على مصدر البيانات الأساسي.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

يمكنك أيضًا دمجها مع `ShowValue` إذا كنت تحتاج إلى كل من القيم الأصلية **و** النسب المئوية:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

عند تفعيل العلامتين معًا، تظهر التسمية مثل “45 % (120)”.

## تحديث تسميات سلاسل المخطط للبيانات الديناميكية

غالبًا ما ستنشئ المخططات في الوقت الفعلي—مثل مبيعات شهرية أو نتائج استبيان. لت **تحديث تسميات سلاسل المخطط** برمجيًا، عدل مجموعة `Series` قبل تعديل تسميات البيانات:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

هذا المقتطف يوضح كيفية **تحديث تسميات سلاسل المخطط** لأي سلسلة، وليس فقط الأولى. إنه مفيد عندما تبني تقارير تجمع بين البيانات الفعلية والمتوقعة.

## الحالات الخاصة والمشكلات الشائعة

| الحالة | ما الذي يجب مراقبته | الحل |
|-----------|-------------------|-----|
| **المخطط ليس فطيرة/دونات** | `Position` قد لا يكون له أي تأثير بصري. | تحقق أن `chart.Type` هو `ChartType.Pie` أو `ChartType.Doughnut`. |
| **لم يتم العثور على مخطط** | `GetChild` يُعيد `null`. | أضف شرط حماية (انظر الكود) وسجّل رسالة مفيدة. |
| **إصدار Word قديم** | بعض ميزات التسميات يتم تجاهلها. | احفظ كـ `.docx` (الصيغة الحديثة) لضمان الدعم الكامل. |
| **عدد كبير من الشرائح** | قد تتداخل التسميات حتى مع `OutsideEnd`. | فكّر في تقليل عدد الشرائح أو زيادة حجم المخطط. |

## مثال كامل يعمل (نسخ‑لصق)

فيما يلي **البرنامج الكامل** الذي يمكنك نسخه إلى مشروع وحدة تحكم جديد. فقط استبدل `YOUR_DIRECTORY` بالمجلد الذي يحتوي على `Chart.docx`.



## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [تعيين الخيارات الافتراضية لتسميات البيانات في مخطط](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [تخصيص سلسلة مخطط واحدة في مخطط](/words/english/net/programming-with-charts/single-chart-series/)
- [إدراج مخطط عمودي في Word باستخدام Aspose.Words لـ .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}