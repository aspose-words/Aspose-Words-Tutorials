---
category: general
date: 2026-10-13
description: تعلم كيفية تعديل تسميات المخطط برمجياً في مستند Word باستخدام C#. يغطي
  هذا الدليل تعديل المخططات في Aspose.Words ومحاذاة التسميات.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: ar
lastmod: 2026-10-13
og_description: قم بضبط تسميات المخطط برمجياً في مستند Word باستخدام C#. اتبع هذا
  الدرس الكامل لتغيير موضع التسميات، والمحاذاة، وأكثر من ذلك.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: تعديل تسميات المخطط في Word برمجياً – دليل خطوة بخطوة بلغة C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: تعديل تسميات المخطط برمجياً في مستند Word باستخدام C#
url: /ar/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعديل تسميات المخطط برمجيًا في مستند Word باستخدام C#

إذا كنت بحاجة إلى **تعديل تسميات المخطط برمجيًا** في مستند Word، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك باستخدام C#. سواءً كنت تُنشئ تقارير، أو تُؤتمت لوحات التحكم، أو تُخصص القوالب، ستشاهد مثالًا كاملاً قابلاً للتنفيذ يغيّر موضع التسمية ومحاذاة المخطط داخل ملف .docx.

ستتعلم أيضًا كيفية استخدام تقنيات **Aspose.Words chart manipulation**، ومعالجة سلاسل متعددة، وتجنب المشكلات الشائعة عند العمل مع كائنات **C# chart data label**.

## المتطلبات المسبقة

* .NET 6.0 (أو أحدث) مثبت  
* Visual Studio 2022 (أو أي بيئة تطوير C#)  
* حزمة NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)  
* مستند Word (`input.docx`) يحتوي على مخطط واحد على الأقل  

هذه العناصر مطلوبة لـ **مثال مخطط مستند Word** الذي سنقوم بتعديله.

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

أنشئ مشروعًا جديدًا من نوع console وأضف توجيهات `using` اللازمة. هذا يُجهّز البيئة لـ **تعديل تسميات المخطط برمجيًا**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*لماذا هذه الخطوة؟*  
تحميل المستند يمنحك الوصول إلى شجرة **مثال مخطط مستند Word** الداخلية، حيث تُخزن المخططات كعُقد شكل (shape).

## الخطوة 2: تحديد أول شكل مخطط

المخططات تُخزن كعُقد `Shape`. الكود التالي يستخرج أول مخطط في المستند، وهو الهدف لتعديلاتنا على التسميات.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*لماذا هذه الخطوة؟*  
طريقة `GetChild` تبحث بشكل متكرر (`true`) وتعيد أول عقدة من النوع `Shape`. التحويل إلى `Chart` يتيح لنا العمل مع API الخاص بالمخطط.

## الخطوة 3: الوصول إلى تسمية البيانات التي تريد تعديلها

كل سلسلة في المخطط لديها مجموعة من تسميات البيانات. بالنسبة لمخطط بسيط، غالبًا ما تكون التسمية الأولى كافية. يوضح الكود أدناه كيفية الوصول إليها.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*لماذا هذه الخطوة؟*  
`ChartSeries` تمثل سلسلة من النقاط. `DataLabelCollection` تحتوي على التسميات لتلك السلسلة، مما يسمح بالتحكم الدقيق في الموضع والمحاذاة.

## الخطوة 4: تغيير موضع التسمية والمحاذاة

الآن نقوم **بتعديل تسميات المخطط برمجيًا** عن طريق ضبط الموضع، والمحاذاة الأفقية، والمحاذاة العمودية. هذه الخصائص تتطابق مع الخيارات التي تراها في واجهة Word.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*لماذا هذه الإعدادات؟*  

* `OutsideEnd` يضع التسمية خارج نهاية كل شريط أو عمود، مما يحسن قابلية القراءة.  
* `HorizontalAlignment.Center` يحافظ على تمركز النص فوق النقطة، بينما `VerticalAlignment.Top` يطابق الحافة العليا للتسمية مع نقطة البيانات، مما يمنع التداخل مع العناصر الأخرى.

### نصيحة احترافية
إذا كان المخطط يحتوي على سلاسل متعددة، قم بالتكرار عبر `chart.Series` وطبق نفس الإعدادات على كل `DataLabelCollection`. هذا يضمن مظهرًا متسقًا عبر المخطط بأكمله.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## الخطوة 5: حفظ المستند المعدل

بعد تعديل التسميات، احفظ التغييرات في ملف جديد. هذا يُكمل عملية **تعديل موضع تسمية المخطط**.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

عند فتح `output.docx`، ستلاحظ أن كل تسمية مخطط قد انتقلت إلى النهاية الخارجية لنقطة البيانات، متمركزة أفقيًا ومُحاذاة إلى الأعلى عموديًا.

## الحالات الخاصة والاختلافات

| الحالة | ما الذي يجب مراقبته | النهج الموصى به |
|-----------|-------------------|----------------------|
| **مخططات متعددة** في نفس المستند | `GetChild` يُعيد فقط أول مخطط. | استخدم `doc.GetChildNodes(NodeType.Shape, true)` للتكرار على جميع أشكال المخططات. |
| **سلسلة بدون تسميات بيانات** | `DataLabelCollection` قد تكون فارغة. | تحقق من `series.HasDataLabels` قبل الوصول إلى المجموعة. |
| **أنواع مخططات مختلفة** (pie, line, scatter) | ليس كل قيم `DataLabelPosition` صالحة. | استخدم `DataLabelPosition.Auto` للمخططات التي تحدد الموضع الأنسب تلقائيًا. |
| **التعريب** | ثوابت المحاذاة لا تعتمد على اللغة، لكن النص المعروض قد يحتاج إلى دعم من اليمين إلى اليسار. | قم بتعيين `dataLabel.TextDirection` إذا كنت بحاجة إلى لغات RTL. |

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه، لصقه، وتشغيله. استبدل `YOUR_DIRECTORY` بمسار مجلد فعلي.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**النتيجة المتوقعة:** عند فتح `output.docx` يظهر كل تسمية مخطط موضوعة خارج نقطة البيانات، متمركزة أفقيًا، ومُحاذاة إلى الأعلى — وهو بالضبط التأثير الذي حققته بـ **تعديل تسميات المخطط برمجيًا**.

## الخلاصة

أنت الآن تعرف كيف **تعدل تسميات المخطط برمجيًا** في مستند Word باستخدام C#. شمل الشرح:

* تحميل مستند باستخدام **Aspose.Words chart manipulation**  
* الوصول إلى **C# chart data label**  
* تغيير **modify chart label position** والمحاذاة  
* حفظ الملف ومعالجة الحالات الخاصة الشائعة  

من هنا يمكنك استكشاف سيناريوهات أكثر تقدمًا، مثل تخصيص خطوط التسميات، إضافة تنسيق شرطي، أو تحديث مخططات متعددة في عملية دفعة. جرّب خيارات `DataLabelPosition` المختلفة لتجد النمط الأنسب لتقاريرك.

---

*هل أنت مستعد لتحسين خط أنابيب التقارير الآلية؟ جرّب إضافة تنسيقات أرقام مخصصة إلى التسميات أو تصدير المخطط كصورة لاستخدامها في ملفات PDF.*

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [تعيين تسميات بيانات موحدة في مخطط عمودي باستخدام Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [تعيين الخيارات الافتراضية لتسميات البيانات في مخطط](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [تحديث بيانات سلسلة المخطط في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}