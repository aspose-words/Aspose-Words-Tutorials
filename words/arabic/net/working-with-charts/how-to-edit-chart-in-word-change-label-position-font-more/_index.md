---
category: general
date: 2026-07-29
description: كيفية تعديل المخطط في مستند Word — تعلم تغيير موضع تسمية المخطط، وضبط
  تسميات مخطط الأعمدة، وتعديل تسميات بيانات المخطط، وتغيير خط تسمية المخطط.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: ar
lastmod: 2026-07-29
og_description: كيفية تعديل المخطط في Word بسرعة. إتقان تغيير موضع تسمية المخطط، تعديل
  تسميات مخطط الأعمدة، تعديل تسميات بيانات المخطط، وتغيير خط تسمية المخطط.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: كيفية تعديل المخطط في Word – تغيير التسميات والخط
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'كيفية تعديل المخطط في وورد: تغيير موضع التسمية، الخط والمزيد'
url: /ar/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعديل المخطط في Word: تغيير موضع التسمية، الخط والمزيد

تحرير المخطط في مستند Word هو احتياج شائع عندما تريد أن تبدو تقاريرك مصقولة. هل واجهت صعوبة في **تغيير موضع تسمية المخطط** أو جعل التسميات قابلة للقراءة دون الغوص في قوائم لا نهائية؟ لست وحدك—معظم المطورين يواجهون هذا التحدي عند أتمتة إنشاء التقارير. في هذا الدليل سنستعرض مثالًا كاملاً قابلاً للتنفيذ يوضح لك بالضبط كيفية **تعديل تسميات المخطط الشريطي**، **تعديل تسميات بيانات المخطط**، و**تغيير خط تسمية المخطط** باستخدام C# ومكتبة Aspose.Words.

## ما ستتعلمه

- تحميل ملف .docx يحتوي بالفعل على مخطط شريطي.  
- استخراج الشكل (shape) الأول للمخطط والوصول إلى مجموعة تسميات البيانات.  
- **تغيير موضع تسمية المخطط** لجعل الأعمدة تبدو أنظف.  
- **تعديل حجم خط تسميات المخطط الشريطي** لتحسين قابلية القراءة.  
- حفظ المستند المعدل مرة أخرى على القرص.  

لا أدوات خارجية، ولا خطوات يدوية في الواجهة—فقط كود نقي يمكنك إدراجه في أي مشروع .NET. في النهاية ستحصل على حل مستقل يمكنك إعادة استخدامه عبر العشرات من المستندات.

> **المتطلبات المسبقة**  
> - .NET 6.0 أو أحدث (الكود يعمل أيضًا على .NET Framework 4.7+).  
> - Aspose.Words لـ .NET (متاح عبر NuGet).  
> - ملف Word (`BarChart.docx`) يحتوي بالفعل على مخطط شريطي.  

إذا كنت تفتقد أيًا من هذه المتطلبات، احصل على أحدث حزمة Aspose.Words الآن:

```bash
dotnet add package Aspose.Words
```

---

## كيفية تعديل المخطط: استخراج المخطط من مستند Word

الخطوة الأولى في **كيفية تعديل المخطط** هي تحميل المستند وتحديد موقع شكل المخطط. تتعامل Aspose.Words مع المخططات كعُقد `Shape`، لذا يمكننا استخدام `GetChild` مع `NodeType.Shape` للحصول على أول مخطط نجده.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **لماذا هذا مهم:**  
> من خلال الوصول مباشرة إلى كائن `Chart`، تتجنب العبء الناتج عن فتح الملف في Word وتعديل كل تسمية يدويًا. هذا هو الأساس لأي أتمتة **تعديل تسميات بيانات المخطط**.

## تعديل تسميات المخطط الشريطي: تغيير موضع تسمية المخطط

الآن بعد أن حصلنا على كائن `Chart`، لنقوم بالتكرار عبر `DataLabelCollection` الخاصة به. الهدف هو **تغيير موضع تسمية المخطط** بحيث تجلس كل تسمية داخل قاعدة العمود بدلاً من أن تطفو فوقه بشكل غير مريح.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **نصيحة احترافية:**  
> `InsideBase` يعمل جيدًا للمخططات الشريطية العمودية. إذا كنت تتعامل مع مخطط شريطي أفقي، جرّب `InsideEnd` بدلاً من ذلك. تجربة المواضع رخيصة—فقط أعد تشغيل الكود وافتح المستند المحفوظ.

## تغيير خط تسمية المخطط: تعديل حجم الخط للقراءة السهلة

الخط الصغير هو القاتل الصامت لوضوح التقرير. لت **تغيير خط تسمية المخطط**، قم ببساطة بتعيين الخاصية `Font.Size` لكل `ChartDataLabel`. سنرفعها إلى 9 pt، وهو حجم مثالي لمعظم التقارير المطبوعة.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **لماذا نفعل ذلك:**  
> تعديل حجم الخط هو جزء من أفضل ممارسات **تعديل تسميات بيانات المخطط**. الخطوط الأكبر تحسن إمكانية الوصول وتقلل الحاجة إلى المعالجة اليدوية بعد ذلك.

## حفظ المستند المحدث

بعد تعديل المواضع والخطوط، الخطوة الأخيرة في **كيفية تعديل المخطط** هي حفظ التغييرات. Aspose.Words يجعل ذلك سطرًا واحدًا.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

افتح `BarChartCustomLabels.docx` في Word وسترى التسميات داخل الأعمدة، مع خط واضح بحجم 9 pt. لا مزيد من التكشير على الأرقام الصغيرة.

---

## مثال كامل عملي (جميع الخطوات في ملف واحد)

فيما يلي برنامج كونسول كامل جاهز للتنفيذ يوضح التدفق الكامل—من تحميل المستند إلى حفظ النسخة المحدثة. انسخه إلى مشروع كونسول .NET جديد واضغط **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**الناتج المتوقع** عندما تشغل البرنامج:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

افتح الملف الناتج وسترى **تعديل تسميات المخطط الشريطي** موضوعة داخل الأعمدة بحجم خط مريح.

---

## أسئلة شائعة وحالات خاصة

### ماذا لو كان المستند يحتوي على عدة مخططات؟

الكود أعلاه يلتقط *أول* مخطط (`GetChild(NodeType.Shape, 0, true)`). لتعديل جميع المخططات، استبدل الاستدعاء الفردي بحلقة:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### كيف **تغيير خط تسمية المخطط** لسلسلة معينة فقط؟

كل `ChartSeries` له مجموعة `DataLabelCollection` الخاصة به. استهدف سلسلة بواسطة الفهرس:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### هل يعمل هذا مع مخططات الفطيرة أو الخط؟

نعم—`ChartDataLabelPosition` يدعم قيمًا مثل `InsideEnd`، `OutsideEnd`، و`BestFit`. لمخطط الفطيرة قد تفضّل `OutsideEnd` للحفاظ على قابلية قراءة التسميات.

### ماذا عن التعريب (مثلاً، فواصل عشرية مختلفة)؟

Aspose.Words يحترم إعدادات اللغة في المستند. إذا كنت بحاجة إلى فرض تنسيق معين، عدّل `label.NumberFormat` قبل الحفظ.

## ملخص وخطوات قادمة

غطّينا **كيفية تعديل المخطط** في مستند Word من البداية إلى النهاية: تحميل الملف، استخراج المخطط، **تغيير موضع تسمية المخطط**، **تعديل تسميات المخطط الشريطي**، **تعديل تسميات بيانات المخطط**، وأخيرًا **تغيير خط تسمية المخطط** قبل الحفظ. المثال الكامل جاهز للإنتاج ويمكن إدراجه في أي خط أنابيب أتمتة.

هل أنت مستعد للارتقاء؟ فكر في الأفكار التالية:

- **إضافة ألوان لتسميات البيانات** (`dataLabel.Font.Color = Color.Blue;`).  
- **إظهار القيم كنسب مئوية** (`dataLabel.NumberFormat = "0%";`).  
- **إنشاء مخططات برمجيًا** بدلاً من تحميل مخططات موجودة.  

كل هذه تبني على نفس واجهة برمجة التطبيقات التي استخدمناها اليوم، لذا ستشعر بالراحة فورًا.

إذا واجهت أي صعوبات، اترك تعليقًا أدناه أو راجع وثائق Aspose.Words لمزيد من خيارات تخصيص المخططات. برمجة سعيدة، واستمتع بالمخططات ذات التسميات الجميلة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [تخصيص تسمية بيانات المخطط](/words/english/net/programming-with-charts/chart-data-label/)
- [تنسيق رقم تسمية البيانات في مخطط](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [تسمية بيانات المخطط](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}