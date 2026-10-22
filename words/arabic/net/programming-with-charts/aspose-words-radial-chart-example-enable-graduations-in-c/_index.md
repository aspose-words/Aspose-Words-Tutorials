---
category: general
date: 2026-10-13
description: مثال مخطط شعاعي Aspose.Words يوضح كيفية تمكين الفواصل على المخطط الشعاعي
  باستخدام C# و Aspose.Words 24.9+.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: ar
lastmod: 2026-10-13
og_description: مثال مخطط دائري Aspose.Words يوضح تمكين التدرجات على مخطط دائري باستخدام
  C# وأحدث مكتبة 24.9+.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: مثال مخطط شعاعي Aspose.Words – تمكين التدرجات في C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'مثال على مخطط شعاعي Aspose.Words: تمكين التدرجات في C#'
url: /ar/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# مثال مخطط شعاعي Aspose.Words: تمكين العلامات في C#

إذا كنت تبحث عن **مثال مخطط شعاعي Aspose.Words**، فقد وصلت إلى المكان الصحيح. يوضح هذا الدليل الخطوات الدقيقة لتفعيل العلامات (graduations) لمخطط شعاعي باستخدام Aspose.Words for .NET API.

المخططات الشعاعية مفيدة لتصوير البيانات الدورية مثل مقاييس وقت اليوم أو الاتجاهات الموسمية. بشكل افتراضي تكون العلامات (الخطوط الصغيرة حول المحور الدائري) مخفية، مما قد يجعل المخطط أصعب في القراءة. تمكينها يتم بسطر واحد فقط، لكن عليك معرفة نموذج الكائن الصحيح والإصدار الذي يدعم هذه الميزة.

في هذا الدليل ستتعلم كيفية:

* تحميل مستند Word يحتوي مسبقًا على مخطط شعاعي.  
* الوصول إلى شكل المخطط عبر Aspose.Words chart API.  
* تشغيل **رؤية العلامات** (متاح من **Aspose.Words الإصدار 24.9**).  
* حفظ المستند المعدل والتحقق من النتيجة.

الكود الكامل القابل للتنفيذ مرفق، بحيث يمكنك نسخه ولصقه في مشروع وحدة تحكم جديد ورؤية التأثير فورًا.

![Aspose.Words radial chart example with graduations](https://example.com/images/radial-chart-graduations.png "Aspose.Words radial chart example showing graduations enabled")

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

| Requirement | Why it matters |
|-------------|----------------|
| .NET 6.0 أو أحدث | Aspose.Words for .NET 24.9+ يستهدف .NET Standard 2.0 ويعمل على .NET 6+. |
| Aspose.Words for .NET **24.9** أو أحدث | تم تقديم الخاصية `IsGraduationsVisible` في الإصدار 24.9. الإصدارات الأقدم ستثير `MissingMemberException`. |
| مستند Word (`RadialChart.docx`) يحتوي على مخطط شعاعي | المثال يتعامل مع مخطط موجود؛ إنشاء مخطط من الصفر موضوع منفصل. |
| بيئة تطوير C# (Visual Studio, Rider, VS Code) | أي بيئة يمكنها تجميع مشاريع .NET ستعمل. |
| حزمة NuGet `Aspose.Words` | تثبيت عبر `dotnet add package Aspose.Words --version 24.9.0` (أو أحدث). |

> **نصيحة احترافية:** إذا لم تتمكن من الترقية إلى 24.9، لا يزال بإمكانك تعديل خصائص أخرى للمخطط، لكن العلامات ستظل مخفية لأن الـ API لم تكشف عن هذه العلامة.

## مثال مخطط شعاعي Aspose.Words – دليل خطوة بخطوة

الأقسام التالية تقسم العملية إلى خطوات منفصلة وسهلة المتابعة. كل خطوة تتضمن الكود الدقيق الذي تحتاجه وتفسيرًا قصيرًا لـ *سبب* وجودها.

### الخطوة 1: تحميل المستند الذي يحتوي على مخطط شعاعي

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**لماذا هذا مهم:**  
`Document` هو نقطة الدخول لـ **Aspose.Words chart API**. يقوم بتحميل ملف DOCX إلى الذاكرة، مما يمنحك إمكانية الوصول إلى كل عقدة—فقرات، جداول، وأشكال المخططات. إذا تعذر العثور على الملف، سيطلق `Document` استثناء `FileNotFoundException`، ويجب معالجته في الكود الإنتاجي.

### الخطوة 2: استرجاع أول شكل مخطط من المستند

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**لماذا هذا مهم:**  
المخططات تُخزن كعقد `Shape`. طريقة `GetChild` مع `NodeType.Shape` تتجول في DOM وتعيد أول شكل مطابق. التحويل إلى `Chart` يمنحك الوصول إلى الخصائص الخاصة بالمخطط مثل `RadialChart`. فحص القيمة `null` يضمن حصولك على خطأ واضح إذا لم يحتوي المستند على مخطط، وهو حالة شائعة عند إعادة استخدام القوالب.

### الخطوة 3: تمكين العلامات على المخطط الشعاعي

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**لماذا هذا مهم:**  
`IsGraduationsVisible` يتحكم في الخطوط الصغيرة حول المحور الدائري. عندما تُضبط على `true`، يُظهر المخطط العلامات، مما يحسن قابلية القراءة للمشاهدين الذين يحتاجون إلى قياس القيم بدقة. الخاصية موجودة تحت `RadialChart`، وهو نوع فرعي من `Chart`. إذا جربتها على مخطط غير شعاعي (مثل مخطط شريطي)، ستكون خاصية `RadialChart` `null`، لذا يجب التحقق من نوع المخطط أولاً في السيناريوهات الأكثر تعقيدًا.

#### معالجة المخططات غير الشعاعية (اختياري)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

هذا الفحص يجعل الكود قويًا عندما قد يحتوي المستند المصدر على أنواع مخططات مختلفة.

### الخطوة 4: حفظ المستند المعدل

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**لماذا هذا مهم:**  
استدعاء `Save` يكتب الـ DOM الموجود في الذاكرة مرة أخرى إلى ملف .docx، مما يحفظ التغيير الذي أجريناه على المخطط. يمكن فتح ملف الإخراج في Microsoft Word أو LibreOffice أو أي عارض يدعم DOCX. سترى المخطط الشعاعي مع العلامات الظاهرة.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك لصقه في `Program.cs` لمشروع وحدة تحكم .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### النتيجة المتوقعة

عند فتح `RadialChart_Graduations.docx` في Word، سيظهر المخطط الشعاعي بخطوط العلامات (graduations) حول المحور الدائري، كما هو موضح في لقطة الشاشة السابقة. باقي المخطط (سلسلة البيانات، المفتاح، العنوان) يبقى دون تغيير.

## الاختلافات الشائعة والحالات الطرفية

| Situation | Solution |
|-----------|----------|
| **إصدار Aspose.Words أقدم (< 24.9)** | قم بالترقية إلى أحدث حزمة NuGet. خاصية `IsGraduationsVisible` غير موجودة في الإصدارات السابقة. |
| **وجود مخططات متعددة في نفس المستند** | استخدم `doc.GetChild(NodeType.Shape, index, true)` مع `index` المناسب أو قم بالتكرار عبر `doc.GetChildNodes(NodeType.Shape, true)` وفلترة حسب `ChartType.Radial`. |
| **مخطط تم إنشاؤه برمجيًا** | استخدم `DocumentBuilder` لإدراج مخطط، ثم عيّن `RadialChart.IsGraduationsVisible` على الـ |

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Remove a Chart Series from a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Hide Plot Area Border in a Column Chart with Aspose.Words for .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}