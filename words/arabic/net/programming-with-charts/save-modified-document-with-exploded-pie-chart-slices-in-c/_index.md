---
category: general
date: 2026-10-13
description: 'احفظ المستند المعدل بعد تخصيص مخطط دائري: تفجير الشرائح، تغيير زاوية
  الشريحة الأولى، وعرض تسميات النسبة المئوية في C#.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: ar
lastmod: 2026-10-13
og_description: احفظ المستند المعدل بعد تخصيص مخطط دائري في C#. تعلم كيفية تفجير شرائح
  المخطط الدائري، وتغيير زاوية الشريحة الأولى، وعرض تسميات النسب المئوية.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: حفظ المستند المعدل مع شرائح مخروطة لمخطط الفطيرة – دليل C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: حفظ المستند المعدل مع شرائح مخروطة لمخطط الفطيرة في C#
url: /ar/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ المستند المعدل مع شرائح مخطط الفطيرة المتفجرة في C#

إذا كنت بحاجة إلى **حفظ المستند المعدل** بعد تعديل مخطط فطيرة في Word، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. ستتعلم كيفية تفجير شرائح مخطط الفطيرة، وتغيير زاوية الشريحة الأولى، وعرض تسميات النسبة المئوية—كل ذلك ببضع أسطر من كود C#.

تخصيص المخططات هو طلب شائع عند إنشاء التقارير أو الفواتير أو لوحات التحكم برمجياً. بنهاية هذا الدرس ستتمكن من تحميل ملف DOCX، تعديل مظهر المخطط، و**حفظ المستند المعدل** جاهزاً للتوزيع.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضاً مع .NET Framework 4.6+)
- Aspose.Words for .NET 23.10 أو أحدث (نسخة تجريبية مجانية أو نسخة مرخصة)
- ملف Word (`input.docx`) يحتوي على مخطط فطيرة واحد
- Visual Studio 2022 أو أي بيئة تطوير C#

> **نصيحة:** يتم إضافة حزمة NuGet الخاصة بـ Aspose.Words باستخدام الأمر `dotnet add package Aspose.Words`.

## الخطوة 1: تحميل مستند Word الذي يحتوي على المخطط

الخطوة الأولى هي فتح ملف DOCX المصدر. تمثل فئة `Document` الملف الكامل في الذاكرة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

تحميل المستند يمنحك وصولاً كاملاً إلى كل عقدة، بما في ذلك الأشكال التي تستضيف المخططات.

## الخطوة 2: استرجاع الشكل الأول للمخطط من المستند

يتم تخزين المخططات داخل عقد `Shape`. يمكنك تحديد المخطط الأول باستخدام `GetChild`.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

إذا كان المستند يحتوي على مخططات متعددة، عدل الفهرس (`0`) أو كرر عبر المجموعة. يضمن هذا السطر أن لديك مرجعاً لكائن `Chart` الذي ستقوم بتعديله.

## الخطوة 3: تفجير شرائح مخطط الفطيرة

تفجير شريحة يفصلها عن باقي الفطيرة، مما يجعل المخطط أسهل للقراءة. خاصية `Explode` تعمل على السلسلة بأكملها.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

ضبط `Explode` إلى `true` **يفجر شرائح مخطط الفطيرة** للسلسلة بأكملها، وهو مفيد عندما تريد إبراز كل شريحة.

## الخطوة 4: تغيير زاوية الشريحة الأولى

أحياناً تحتاج إلى أن تبدأ الشريحة الأولى بزاوية مخصصة، على سبيل المثال لتتوافق مع دليل تصميم.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

خاصية `FirstSliceAngle` **تغير اتجاه الشريحة الأولى**، حيث تدور الفطيرة بالكامل لتبدأ الشريحة الأولى عند 30 درجة.

## الخطوة 5: عرض تسميات النسبة المئوية على شرائح الفطيرة

عرض المساهمة الرقمية لكل شريحة غالباً ما يكون مطلوباً في التقارير. علم `DataLabel.ShowPercentage` يفعّل قيم النسبة المئوية.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

هذه الخطوة **تعرض تسميات النسبة المئوية** مباشرة على المخطط، وتلبي أيضاً متطلب **عرض النسب المئوية للفطيرة**.

## الخطوة 6: حفظ المستند المعدل

بعد تطبيق جميع التخصيصات، احفظ التغييرات في ملف جديد. طريقة `Save` تكتب ملف DOCX المحدث إلى القرص.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

الآن لديك **حفظ المستند المعدل** الذي يحتوي على مخطط فطيرة متفجر، وشريحة أولى مدورة، وتسمية نسب مئوية مرئية.

![حفظ المستند المعدل مع عرض مخطط الفطيرة المتفجر](/images/pie-chart-exploded.png "حفظ المستند المعدل مع شرائح مخطط الفطيرة المتفجرة وتسمية النسب المئوية")

*توضح اللقطة الشاشة النتيجة النهائية بعد حفظ المستند.*

## مثال كامل قابل للتنفيذ

بتجميع الأجزاء معاً، إليك البرنامج الكامل الذي يمكنك نسخه‑ولصقه في مشروع وحدة تحكم:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### النتيجة المتوقعة

فتح `output.docx` سيعرض مخطط فطيرة حيث:

- كل شريحة مفصولة قليلاً (**شرائح مخطط الفطيرة المتفجرة**)
- الشريحة الأولى تبدأ بزاوية إزاحة 30 درجة (**تغيير الشريحة الأولى**)
- كل شريحة تُظهر مساهمتها كنسبة مئوية (**عرض تسميات النسبة المئوية**, **عرض النسب المئوية للفطيرة**)
- تم **حفظ المستند المعدل** دون تعديل الأصل.

## أسئلة شائعة وحالات حافة

| السؤال | الإجابة |
|----------|--------|
| **ماذا لو لم يحتوي المستند على مخطط؟** | يتحقق الكود من `null` بعد `GetChild`. إذا لم يوجد مخطط، يمكنك إما إضافة واحد برمجياً أو إيقاف العملية برسالة واضحة. |
| **هل يمكنني تفجير شريحة واحدة فقط؟** | نعم. استخدم `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` حيث `i` هو فهرس الشريحة. |
| **كيف أغير تنسيق التسمية (مثلاً إظهار القيمة + % )؟** | اضبط `chart.PieChart.DataLabel.ShowValue = true;` ويفضل أيضاً `chart.PieChart.DataLabel.ShowPercentage = true;` لدمج الاثنين. |
| **هل يتم الحفاظ على نمط المخطط بعد الحفظ؟** | Aspose.Words يحتفظ بجميع الأنماط، بما في ذلك الألوان والخطوط، عندما تقوم بـ **حفظ المستند المعدل**. |
| **هل يمكنني معالجة عدة مخططات في نفس الملف؟** | كرر عبر جميع عقد `Shape` باستخدام `NodeType.Shape` وصفيها بـ `shape.HasChart`. طبق نفس الخطوات على كل مخطط. |

## الخلاصة

أنت الآن تعرف كيف **تحفظ المستند المعدل** بعد تخصيص مخطط فطيرة في Word برمجياً. غطى الدليل تفجير شرائح مخطط الفطيرة، تغيير زاوية الشريحة الأولى، وعرض تسميات النسبة المئوية—مستوفياً متطلبات **عرض تسميات النسبة المئوية**, **تفجير شرائح مخطط الفطيرة**, **عرض النسب المئوية للفطيرة**, و**تغيير الشريحة الأولى**.

بعد ذلك، فكر في استكشاف:

- إضافة سلاسل بيانات ديناميكياً (`chart.Series.Add(...)`)  
- تخصيص موضع الأسطورة وعناوين المخطط  
- تحويل DOCX إلى PDF مع الحفاظ على تنسيق المخطط  

لا تتردد في تجربة زوايا مختلفة، إعدادات التفجير، أو تنسيقات التسميات لتتناسب مع احتياجات تقاريرك. Happy coding!

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك الخاصة.

- [كيفية حفظ المستند المعدل في C# باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [تحديث بيانات سلسلة المخطط في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [إدراج مخطط عمودي في مستند Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}