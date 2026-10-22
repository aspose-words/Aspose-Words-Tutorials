---
category: general
date: 2026-10-13
description: كيفية تنسيق المخطط في Word باستخدام C# عن طريق تطبيق تنسيق رقم مخصص،
  مثل العملة، على محاور المخطط. مثال على الكود خطوة بخطوة متضمن.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: ar
lastmod: 2026-10-13
og_description: كيفية تنسيق المخطط في Word باستخدام C# يتيح لك تطبيق تنسيق رقم مخصص
  على محاور المخطط، مما يضمن ظهور القيم كعملة أو نسب مئوية أو أي نمط تحتاجه. اتبع
  الدليل خطوة بخطوة.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: كيفية تنسيق المخطط في Word باستخدام C# – تنسيقات الأرقام المخصصة
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: كيفية تنسيق المخطط في Word باستخدام C# وتنسيقات الأرقام المخصصة
url: /ar/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تنسيق المخطط في Word باستخدام C# وتنسيقات الأرقام المخصصة

تنسيق المخطط في Word باستخدام C# هو طلب شائع عندما تحتاج إلى عرض البيانات بشكل احترافي. يوضح هذا الدليل كيفية تطبيق تنسيق رقم مخصص على محور المخطط باستخدام **Aspose.Words for .NET**، بحيث تظهر القيم بالضبط كما تتوقع.

سوف تتعلم كيفية تحميل ملف DOCX، تحديد أول مخطط، قراءة التنسيق الحالي، ثم تعيين نمط جديد مثل العملة بدقتين عشريتين. يغطي الدرس أيضًا كيفية تغيير تنسيق محور المخطط لسلاسل إضافية وكيفية إعادة تعيين التنسيق إذا لزم الأمر.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

* .NET 6.0 أو أحدث مثبت  
* مشروع Visual Studio 2022 (أو أي بيئة تطوير تدعم .NET)  
* حزمة NuGet **Aspose.Words for .NET** (`Aspose.Words`)  
* مستند Word (`input.docx`) يحتوي على مخطط واحد على الأقل

يمكنك إضافة الحزمة بالأمر التالي:

```bash
dotnet add package Aspose.Words
```

## كيفية تنسيق المخطط في Word باستخدام Aspose.Words

البرنامج الكامل التالي يوضح كل خطوة مطلوبة **لتنسيق المخطط** قيم المحور. احفظ الملف باسم `Program.cs` وشغّله من سطر الأوامر أو بيئة التطوير الخاصة بك.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### شرح كل خطوة

| الخطوة | لماذا يهم | الكود الرئيسي |
|------|----------------|----------|
| **تحميل المستند** | تحتاج إلى كائن `Document` للعمل مع ملف Word. | `new Document("input.docx")` |
| **استرجاع المخطط** | تُخزن كائنات `Chart` كعُقد `Shape`؛ التحويل يتيح لك استخدام واجهات برمجة التطبيقات الخاصة بالمخطط. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **الوصول إلى قيم X** | يُطبق تنسيق المحور على مجموعة القيم لسلسلة البيانات. | `chart.ChartData.Series[0].XValues` |
| **قراءة التنسيق الحالي** | معرفة `FormatCode` الحالي يساعدك على اتخاذ قرار ما إذا كنت ستستبدله أو تضيف إليه. | `xValues.FormatCode` |
| **تعيين تنسيق مخصص** | خاصية `FormatCode` تقبل أي نمط متوافق مع Excel، مما يتيح العملة، النسب المئوية، التواريخ، إلخ. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **حفظ المستند** | كتابة التغييرات تُعيد تنسيق المحور الجديد إلى ملف DOCX. | `doc.Save("output_formatted.docx")` |

تشغيل البرنامج ينتج ملف `output_formatted.docx`. افتحه في Word وسترى قيم محور X للمخطط معروضة كـ **$1,234.00**, **$2,345.00**, … بدلاً من الأرقام العادية.

## تطبيق تنسيق رقم مخصص على محور المخطط

إذا كنت بحاجة إلى **تطبيق تنسيق رقم مخصص** على محور Y أو على سلاسل إضافية، فإن العملية هي نفسها—فقط استهدف مجموعة مختلفة:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **نصيحة احترافية:** استخدم علامات الاقتباس المزدوجة داخل سلسلة التنسيق لتضمين أحرف حرفية (مثال، `"$"` للعملة). قم بتهريب علامات الاقتباس كما هو موضح أعلاه.

## تنسيق رقم مخصص في Word – التعامل مع لغة Word

يحترم Word لغة المستند عند تفسير تنسيقات الأرقام. إذا كان المستند يستخدم لغة غير أمريكية، قد تحتاج إلى تعديل سلسلة التنسيق:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

اختبار التنسيق على مستند بإعدادات اللغة الألمانية يؤكد أن القيم تظهر كـ **€ 1.234,00**.

## كيفية ضبط خصائص المخطط برمجياً

إلى جانب تنسيق المحور، غالبًا ما تريد **ضبط المخطط** لعناوين، وسلالم، أو تسميات البيانات. إليك مقتطفًا سريعًا يوضح ضبط عنوان المخطط بعد تنسيق المحور:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

دمج هذا مع تنسيق الرقم المخصص يمنحك مخططًا مصقولًا بالكامل جاهزًا للتقارير.

## تغيير تنسيق محور المخطط ديناميكياً بناءً على إدخال المستخدم

في التطبيقات الواقعية قد تسمح للمستخدمين باختيار تنسيق في وقت التشغيل. الطريقة التالية تحزم منطق التنسيق:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

يمكنك استدعاء `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` للعملة أو `SetAxisFormat(chart, 0, "0%")` للنسب المئوية. هذا النهج يحافظ على نظافة الكود الرئيسي ويدعم توسيعات مستقبلية.

## الحالات الحدية والمشكلات الشائعة

| الموقف | ما الذي يجب مراقبته | الإصلاح المقترح |
|-----------|-------------------|---------------|
| المستند يحتوي على **لا مخطط** | `GetChild` يُعيد `null`، مما يسبب استثناء تحويل النوع. | تحقق من `null` قبل التحويل (انظر المثال). |
| وجود مخططات متعددة في نفس المستند | الكود دائمًا يلتقط أول مخطط (`index 0`). | حلق عبر `doc.GetChildNodes(NodeType.Shape, true)` وصفيّف حسب `ShapeType.Chart`. |
| سلسلة **بدون قيم X** (مثل المخططات الدائرية) | الوصول إلى `XValues` قد يثير `ArgumentOutOfRangeException`. | تأكد من أن `Series[i].XValues` غير فارغ قبل التنسيق. |
| عدم تطابق اللغة | قد يظهر رمز العملة بشكل غير صحيح. | عيّن `xValues.FormatCode` صراحةً بالرموز المناسبة للغة. |

## النتيجة المتوقعة

بعد تشغيل البرنامج النموذجي، افتح **output_formatted.docx**. يجب أن يعرض محور X للمخطط الأرقام بالتنسيق المخصص المختار. في مثال العملة، تبدو تسميات المحور كالتالي:

```
$1,000.00
$2,000.00
$3,000.00
```

إذا طبقت تنسيق النسبة المئوية على قيم Y، تظهر تسميات محور Y كالتالي:

```
10%
20%
30%
```

## الخلاصة

أظهر لك هذا الدرس **كيفية تنسيق المخطط** في Word باستخدام C# عبر **تطبيق تنسيق رقم مخصص** على قيم المحور. لديك الآن نمط قابل لإعادة الاستخدام لتعيين العملة، النسب المئوية، أو أي نمط رقمي آخر، بالإضافة إلى إرشادات للتعامل مع اللغات، السلاسل المتعددة، وإدخال المستخدم الديناميكي.

بعد ذلك، قد تستكشف **كيفية ضبط المخطط** لعناوين، تسميات البيانات، أو حتى تصدير المخطط كصورة باستخدام `ChartRenderer`. هذه المواضيع تبني مباشرة على المفاهيم التي تم تغطيتها هنا وستساعدك على إنشاء حلول تقارير مؤتمتة بالكامل.

---


## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Format Secondary X‑Axis and Set Display Units to Thousands in Word Line Charts Using Aspose.Words for .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}