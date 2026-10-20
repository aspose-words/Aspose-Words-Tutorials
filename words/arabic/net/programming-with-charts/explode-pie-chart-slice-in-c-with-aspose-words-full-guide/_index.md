---
category: general
date: 2026-07-19
description: تفجير شريحة مخطط دائري باستخدام Aspose.Words للغة C#. تعلّم كيفية تفجير
  شريحة الفطيرة، وضبط حجم فتحة الدونات، وتغيير نقاط بيانات المخطط بسرعة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: ar
lastmod: 2026-07-19
og_description: تفجير شريحة مخطط الدائرة باستخدام Aspose.Words للغة C#. يوضح لك هذا
  الدليل كيفية تفجير شريحة المخطط الدائري، وضبط حجم فتحة الدونات، وتغيير نقاط بيانات
  المخطط بفعالية.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: فصل شريحة مخطط دائري في C# – دليل Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: تفجير شريحة مخطط دائري في C# باستخدام Aspose.Words – دليل كامل
url: /ar/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تفجير شريحة مخطط دائري في C# باستخدام Aspose.Words – دليل كامل

هل تساءلت يومًا كيف **explode pie chart slice** في مستند Word باستخدام C#؟ لست وحدك. سواء كنت تُعد عرض مبيعات أو تُصوّر نتائج استبيان، يمكن للشريحة المتفجرة أن تجذب الأنظار إلى المكان الذي تريد بالضبط. في هذا الدرس سنستعرض العملية بالكامل — تحميل المستند، استخراج المخطط، تفجير الشريحة الأولى، تعديل حجم الفتحة الداخلية (دونات)، وحتى تغيير نقاط بيانات المخطط.

سنضيف أيضًا المفاهيم الثانوية التي قد تبحث عنها: **how to explode pie slice**, **adjust doughnut hole size**, و **change chart data points**. لا إطالة، مجرد حل جاهز للنسخ واللصق.

---

## ما الذي ستحتاجه

قبل أن نبدأ، تأكد من وجود التالي:

- **Aspose.Words for .NET** (أحدث نسخة حتى 2026‑07‑19). يمكنك الحصول عليها من NuGet باستخدام `Install-Package Aspose.Words`.
- مشروع **.NET 6+** (أو .NET Framework 4.7.2+ إذا كنت لا تزال تستخدم الإصدارات القديمة).
- ملف Word (`Chart.docx`) يحتوي بالفعل على مخطط دائري أو دونات. إذا لم يكن لديك واحد، أنشئ مخططًا سريعًا في Word واحفظه.

هذا كل ما تحتاجه — لا مكتبات إضافية، لا COM interop، مجرد كود مُدار بالكامل.

---

## تفجير شريحة مخطط دائري – تنفيذ خطوة بخطوة

فيما يلي نقسم المهمة إلى خطوات صغيرة. كل قسم يحتوي على عنوان واضح، مقتطف كود، وتفسير قصير *لـ لماذا* نقوم بما نقوم به.

### الخطوة 1: تثبيت وإضافة مرجع Aspose.Words

أولًا، أضف حزمة Aspose.Words إلى مشروعك. في نافذة Package Manager Console:

```powershell
Install-Package Aspose.Words
```

> **نصيحة احترافية:** إذا كنت تستخدم واجهة NuGet المدمجة في Visual Studio، ابحث عن “Aspose.Words” واضغط Install. هذا يضمن حصولك على أحدث التصحيحات وإمكانية العمل مع المخططات مباشرةً.

### الخطوة 2: تحميل مستند Word الذي يحتوي على المخطط

نحتاج إلى كائن `Document` يشير إلى ملف `.docx` الذي تريد تعديل مخططه.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **لماذا هذا مهم:** `Document` هو نقطة الدخول لكل عملية في Aspose.Words. بالتحقق من وجود المخططات مبكرًا، نتجنب حدوث NullReference لاحقًا عندما نحاول تفجير شريحة.

### الخطوة 3: استرجاع أول عقدة مخطط

معظم الأمثلة تفترض وجود مخطط واحد، لذا سنأخذ الأول. إذا كان لديك عدة مخططات، عدل الفهرس وفقًا لذلك.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **ملاحظة:** التحويل إلى `Chart` آمن بعد أن تأكدنا من وجود مخطط. هذا الكائن يتيح لنا الوصول إلى السلاسل، نقاط البيانات، وإعدادات النوع المحددة للمخطط.

### الخطوة 4: تفجير الشريحة الأولى في مخطط دائري

الآن نصل إلى جوهر الموضوع — **how to explode pie slice**. سنضبط خاصية `Exploded` للنقطة البيانية الأولى.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **لماذا يعمل هذا:** `Exploded` يخبر Word بسحب تلك الشريحة بعيدًا عن المركز، مما يخلق تأثير “الدائرة المتفجرة” الكلاسيكي. الخاصية من نوع Boolean، لذا تعيينها إلى `true` يكفي.

### الخطوة 5: تعديل حجم فتحة الدونات (إذا كان مخططًا من نوع دونات)

إذا كان مخططك من نوع دونات، قد ترغب في **adjust doughnut hole size**. حجم الفتحة يُعبّر عنه كنسبة مئوية من نصف قطر المخطط.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **ما معنى الرقم:** القيمة `30` تعني أن الدائرة الداخلية ستشغل 30 % من نصف القطر الكلي، مما يترك حلقة خارجية أسمك.

### الخطوة 6: تغيير نقاط بيانات المخطط (اختياري)

أحيانًا تحتاج إلى **change chart data points** — ربما قمت بتحديث الأرقام الأساسية وتريد أن ينعكس ذلك بصريًا.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **لماذا قد تحتاج ذلك:** تغيير قيمة نقطة البيانات يعيد حساب نسب الشرائح تلقائيًا، مما يبقي المخطط دقيقًا دون تعديل يدوي في Word.

### الخطوة 7: حفظ المستند المعدل

أخيرًا، اكتب التغييرات إلى القرص. يمكنك استبدال الملف الأصلي أو إنشاء ملف جديد — الخيار لك.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **نصيحة:** استخدم `SaveFormat.Docx` إذا أردت أن تكون صريحًا، لكن `Save(string)` يكتشف الصيغة تلقائيًا من امتداد الملف.

---

## النتيجة المتوقعة

عند فتح `FormattedChart.docx` في Microsoft Word، يجب أن ترى:

- الشريحة الأولى من المخطط الدائري **متفجرة** إلى الخارج.
- إذا كان المخطط دونات، فإن الفتحة المركزية الآن تشغل **30 %** من نصف القطر.
- أي نقاط بيانات تم تعديلها تعكس القيم الجديدة التي قمت بتعيينها.

فيما يلي نموذج توضيحي لما تبدو عليه الشريحة المتفجرة (صورة توضيحية فقط).

![Exploded pie chart slice created with Aspose.Words in C#](exploded-pie-slice.png)

*نص بديل:* **exploded pie chart slice** تُظهر شريحة مسحوبة بعيدًا في مستند Word.

---

## أسئلة شائعة وحالات خاصة

**ماذا لو لم يكن المخطط دائريًا أو دونات؟**  
يتحقق الكود من `ChartType` قبل تطبيق `Exploded` أو `HoleSize`. بالنسبة للمخططات الشريطية أو الخطية أو المساحية، تلك الخصائص غير موجودة، لذا يتخطى المنطق هذه الحالات بأمان.

**هل يمكن تفجير عدة شرائح؟**  
بالطبع. يمكنك حلقة عبر `chart.PieChartData.Series[0].DataPoints` وتعيين `Exploded = true` لأي فهرس تريده.

**هل يجب القلق بشأن تنسيقات الأرقام حسب الثقافة؟**  
Aspose.Words يخزن القيم الرقمية كـ doubles، مستقلًا عن الإعدادات المحلية، لذا لا توجد مشاكل بين الفواصل والنقاط.

**ماذا عن المخططات المدمجة في رؤوس أو تذييلات الصفحات؟**  
استخدم `doc.GetChildNodes(NodeType.Chart, true)` لاسترجاع جميع المخططات، ثم افحص `ParentNode` لكل عقدة لتحديد موقعها. نفس منطق التفجير ينطبق.

---

## الخلاصة

أصبح لديك الآن حل جاهز للنسخ واللصق حول كيفية **explode pie chart slice** باستخدام Aspose.Words في C#. غطينا سير العمل بالكامل — من تحميل المستند، استرجاع المخطط، تفجير الشريحة، **adjusting doughnut hole size**، إلى **changing chart data points** وأخيرًا حفظ الملف.

لا تتردد في التجربة: جرّب تفجير شريحة مختلفة، غيّر حجم الفتحة إلى 45 %، أو حدّث عدة نقاط بيانات مرة واحدة. واجهة Aspose.Words تجعل هذه التعديلات سهلة، وتظهر التغييرات فورًا عند فتح ملف Word.

---

### ما التالي؟

- **تنسيق الشريحة المتفجرة** (تغيير لون التعبئة، الحدود، أو إضافة تسمية بيانات). ابحث عن “Aspose.Words chart formatting”.
- **أتمتة المعالجة الجماعية** لعدة مستندات — حلقة عبر مجلد، تفجير الشرائح، وحفظ النسخ الجديدة.
- **دمج مع Aspose.Slides** إذا كنت تحتاج نفس المخطط في عرض PowerPoint.

هل لديك أسئلة إضافية حول تعديل المخططات، أو ترغب في الغوص أعمق في أنواع المخططات الأخرى؟ اترك تعليقًا أدناه، وتمنياتنا لك ببرمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}