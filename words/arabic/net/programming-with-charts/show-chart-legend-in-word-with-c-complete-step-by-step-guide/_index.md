---
category: general
date: 2026-06-02
description: عرض مفتاح الرسم البياني في مستند Word باستخدام C#. تعلم كيفية إضافة المفتاح،
  وتطبيق نمط الرسم البياني المسبق، وتخصيص مظهر الرسوم البيانية في Word خلال دقائق.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: ar
og_description: اعرض وسيلة إيضاح المخطط في مستند Word فورًا. يوضح لك هذا الدليل كيفية
  إضافة وسيلة إيضاح، وتطبيق نمط مخطط مسبق، ومعالجة الحالات الخاصة.
og_title: عرض مفتاح الرسم البياني في Word – دليل C# كامل
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: إظهار وسيلة إيضاح المخطط في Word باستخدام C# – دليل كامل خطوة بخطوة
url: /ar/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إظهار وسيلة إيضاح المخطط في Word باستخدام C# – دليل خطوة بخطوة كامل

هل تساءلت يومًا **كيف تضيف وسيلة إيضاح** إلى مخطط موجود داخل مستند Word؟ لست وحدك. في العديد من التقارير، تجعل وسيلة الإيضاح المفقودة البيانات تبدو غامضة، ولا ينبغي أن يكون إصلاح ذلك مصدر صداع.  

في هذا الدرس سنقوم **بإظهار وسيلة إيضاح المخطط** في ملف Word باستخدام Aspose.Words for .NET، وتطبيق نمط مخطط مسبق، والتأكد من ظهور وسيلة الإيضاح في المكان الذي تحتاجه بالضبط. في النهاية ستحصل على عينة جاهزة للتنفيذ يمكنك إدراجها في أي مشروع C#.

## ما يغطيه هذا الدليل

سنتبع سير العمل بالكامل:

1. تحميل ملف *.docx* موجود يحتوي بالفعل على مخطط.  
2. استرجاع المخطط الأول (أو أي مخطط تستهدفه).  
3. **تطبيق نمط مخطط مسبق** لإعطاء الشكل مظهرًا احترافيًا.  
4. **إظهار وسيلة إيضاح المخطط**، وضعها على اليمين، ومعالجة الحالات الخاصة مثل مخططات الشلال.  
5. حفظ المستند المعدل.

لا أدوات خارجية، ولا تعديل يدوي للواجهة—فقط شفرة صافية. المتطلب الوحيد هو وجود إشارة إلى حزمة Aspose.Words NuGet (الإصدار 23.10 أو أحدث) وفهم أساسي للغة C#.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (العينة تعمل أيضًا مع .NET Framework 4.7.2).  
- مكتبة Aspose.Words for .NET مثبتة (`Install-Package Aspose.Words`).  
- ملف Word (`input.docx`) يحتوي بالفعل على مخطط واحد على الأقل.  
- Visual Studio أو Rider أو أي بيئة تطوير تفضلها.

## الخطوة 1: إعداد المشروع وتحميل المستند

أولًا، أنشئ تطبيقًا من نوع console (أو دمج الشفرة في مشروع موجود). أضف توجيهات `using` وحمّل ملف `.docx` .

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **لماذا هذا مهم:** تحميل المستند هو الأساس. بدون كائن `Document` لا يمكنك الوصول إلى كائنات المخطط التي توفرها Aspose.Words.

## الخطوة 2: استرجاع المخطط المستهدف

المخططات تُخزن كعُقد داخل شجرة المستند. طريقة `GetChild` تقوم ببحث عميق، مما يتيح لنا جلب المخطط الأول بغض النظر عن موقعه (رأس الصفحة، النص، التذييل، إلخ).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **نصيحة:** إذا كان لديك عدة مخططات، غيّر الفهرس `0` إلى `1` أو `2` … أو قم بالتكرار عبر `doc.GetChildNodes(NodeType.Chart, true)`.

## الخطوة 3: تطبيق نمط بصري مسبق

غالبًا ما يبدأ المخطط الجذاب بنمط. توفر Aspose.Words عشرات الأنماط المدمجة؛ `ChartStyle.Style12` هو خيار نظيف وعصري.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **كيف يعمل:** خاصية `Style` ترتبط بأنماط المخططات المدمجة في Word التي تراها في الواجهة. اختيار نمط مسبق يوفر عليك ضبط الألوان والخطوط والعلامات يدويًا.

## الخطوة 4: تمكين وسيلة الإيضاح وتحديد موقعها

الآن نأتي إلى نجمة العرض—**إظهار وسيلة إيضاح المخطط**. نقوم بتفعيل وسيلة الإيضاح، ثم نثبتها على الجانب الأيمن من المخطط.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **لماذا اليمين؟** وضع وسيلة الإيضاح على اليمين يحافظ على عرض مساحة البيانات، وهو مفيد خصوصًا لمخططات الأعمدة أو الأشرطة.

## الخطوة 5: التعامل مع مخططات الشلال (حالة خاصة)

مخططات الشلال تتصرف بشكل مختلف قليلًا؛ قد تكون وسيلة الإيضاح مخفية افتراضيًا. الشرط الوقائي التالي يضمن ظهور وسيلة الإيضاح عندما يكون نوع المخطط شلال.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **ملاحظة حالة حافة:** بعض إصدارات Word القديمة تتجاهل `HasLegend` لمخططات الشلال، لذا ضبط `Legend.Show` صراحةً يضمن الظهور.

## الخطوة 6: حفظ المستند المعدل

أخيرًا، اكتب التغييرات مرة أخرى إلى القرص. يمكنك استبدال الملف الأصلي أو إنشاء ملف جديد.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

تشغيل البرنامج سينتج ملف `output.docx` مع وسيلة إيضاح مرئية على اليمين، ومُطبقًا عليه النمط `Style12`. افتح الملف في Word للتحقق من النتيجة.

## مثال كامل يعمل (جميع الخطوات مجمعة)

فيما يلي الشفرة الكاملة الجاهزة للتنفيذ. انسخها والصقها في `Program.cs` (أو أي ملف C#) وعدّل مسارات الملفات.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**الناتج المتوقع:** عند فتح `output.docx` سيظهر المخطط الأصلي مع وسيلة إيضاح محاذاة إلى اليمين، ومُطبقًا عليه النمط الحديث `Style12`. جميع سلاسل البيانات مُعلمة بوضوح، مما يجعل المخطط مفهومًا فورًا.

## الأسئلة المتكررة (FAQ)

### كيف تضيف وسيلة إيضاح إلى مخطط محدد (ليس الأول)؟

استبدل الفهرس `0` في `GetChild(NodeType.Chart, 0, true)` بالموقع الصفري المستهدف لمخططك، أو قم بالتكرار عبر جميع عقد المخطط:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### هل يمكن وضع وسيلة الإيضاح في الأسفل بدلاً من اليمين؟

بالطبع. فقط غيّر تعداد `LegendPosition`:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### ماذا لو كان المخطط يحتوي بالفعل على وسيلة إيضاح وأريد إخفاؤها؟

اضبط `HasLegend` إلى `false`:

```csharp
chart.HasLegend = false;
```

### هل يعمل هذا مع Word 2010، 2016، وما بعده؟

نعم. تقوم Aspose.Words بتجريد نسخة Word الأساسية، لذا يعمل نفس الكود عبر جميع ملفات .docx الحديثة.

## نصائح احترافية ومشكلات شائعة

- **نصيحة احترافية:** بعد تطبيق نمط، لا يزال بإمكانك تعديل العناصر الفردية (الألوان، تسميات البيانات) عبر مجموعة `Chart.Series`. النمط يمنحك أساسًا قويًا.
- **احذر من:** إذا كان المخطط داخل خلية جدول، قد تظهر وسيلة الإيضاح ضيقة. فكر في زيادة حجم المخطط (`chart.Width`, `chart.Height`) قبل تحديد موقع وسيلة الإيضاح.
- **ملاحظة أداء:** تحميل مستندات كبيرة (مئات الميجابايت) قد يستهلك الكثير من الذاكرة. استخدم `LoadOptions` مع `LoadFormat.Docx` لتقليل الحمل إذا كنت تحتاج فقط إلى تعديل المخطط.

## الخطوات التالية

الآن بعد أن عرفت **كيف تضيف وسيلة إيضاح** و**تطبق نمط مخطط مسبق** في Word، قد تستكشف:

- **ألوان مخطط مخصصة** (`chart.Series[i].Format.Fill.ForeColor`).  
- **تنسيق تسميات البيانات** (`chart.Series[i].HasDataLabel = true`).  
- **تصدير المخطط كصورة** (`chart.ToImage()`)، مفيد للتضمين في أماكن أخرى.  

كل من هذه المواضيع يبنى على نفس نموذج الكائنات، لذا ستجد منحنى التعلم سهلًا.

## الخلاصة

لقد قدمنا للتو حلاً نظيفًا من البداية إلى النهاية لـ **إظهار وسيلة إيضاح المخطط** في مستند Word باستخدام C#. من خلال تحميل المستند، استرجاع المخطط، تطبيق نمط مسبق، تمكين وسيلة الإيضاح، ومعالجة خصوصيات مخططات الشلال، ستحصل على مخطط مصقول جاهز لأي تقرير تجاري.  

لا تتردد في تجربة قيم `ChartStyle` أخرى أو مواضع وسيلة الإيضاح—تصوراتك البيانية تستحق أفضل عرض. إذا واجهت أي صعوبات، اترك تعليقًا أدناه؛ برمجة سعيدة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إدراج مخطط عمودي في مستند Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [إخفاء محور المخطط في مستند Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [استخدام واجهة برمجة تطبيقات مخططات Word](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}