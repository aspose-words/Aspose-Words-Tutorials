---
category: general
date: 2026-09-08
description: إنشاء مستند Word فارغ وإضافة مخطط إلى Word باستخدام Aspose.Words. تعلم
  كيفية إدراج مخطط راداري، تمكين التدرجات، وحفظ الملف.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: ar
lastmod: 2026-09-08
og_description: إنشاء مستند Word فارغ وإضافة مخطط إلى Word باستخدام Aspose.Words.
  يوضح هذا الدرس كيفية إدراج مخطط راداري، وتكوين المحاور، وحفظ المستند.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: إنشاء مستند Word فارغ وإضافة مخطط راداري – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: كيفية إنشاء مستند Word فارغ وإضافة مخطط إلى Word
url: /ar/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word فارغ وإضافة مخطط إلى Word

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** لتقرير أو قالب أو دمج بريد آلي، فإن هذا الدليل يشرح لك العملية بالكامل باستخدام C# و Aspose.Words. ستتعلم أيضًا كيفية **إضافة مخطط إلى Word**، وبشكل محدد كيفية **إدراج مخطط راداري**، وتفعيل العلامات، وحفظ النتيجة كملف .docx.

يغطي هذا الشرح كل شيء من إعداد المشروع إلى خطوة التحقق النهائية. في النهاية ستحصل على قطعة كود قابلة لإعادة الاستخدام يمكن إدراجها في أي تطبيق .NET. لا تحتاج إلى خبرة سابقة مع Aspose.Words، لكن يجب أن تكون لديك معرفة أساسية بـ C# و .NET SDK حديث مثبت.

## المتطلبات المسبقة

- .NET 6.0 SDK أو أحدث  
- Aspose.Words for .NET (حزمة NuGet `Aspose.Words`)  
- بيئة تطوير مثل Visual Studio 2022 أو VS Code  
- صلاحية كتابة في المجلد الذي سيُحفظ فيه المستند  

يمكنك تثبيت المكتبة بالأمر التالي:

```bash
dotnet add package Aspose.Words
```

## الخطوة 1: إنشاء مستند Word فارغ

الخطوة الأولى هي **إنشاء مستند Word فارغ** في الذاكرة. تمثل الفئة `Document` الملف بالكامل، بينما توفر `DocumentBuilder` واجهة برمجة تطبيقات سلسة لإضافة المحتوى.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` يبدأ فارغًا، لذا لديك لوحة نظيفة لتضع عليها المخطط. إبقاء المستند فارغًا في هذه المرحلة يجعل من السهل إعادة استخدام نفس الكود لقوالب مختلفة.

## الخطوة 2: إضافة مخطط إلى Word

بعد ذلك، **نضيف مخططًا إلى Word** عن طريق استدعاء `InsertChart`. تتطلب الطريقة نوع المخطط والأبعاد المطلوبة بالنقاط (1 نقطة = 1/72 بوصة).

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar` يخبر Aspose.Words بإنشاء مخطط شعاعي، وهو مثالي لعرض بيانات متعددة المتغيرات بتصميم دائري. قيم الحجم (400 × 300) تناسب معظم الصفحات العمودية، لكن يمكنك تعديلها لتلائم تخطيطك.

## الخطوة 3: إدراج مخطط راداري وتكوين العلامات

الآن **نُدرج مخطط راداري** ونفعّل العلامات (ticks) على كل من المحور الفئوي (X) ومحور القيمة (Y). تُحسّن العلامات من قابلية القراءة من خلال إظهار المواقع الدقيقة لكل نقطة بيانات.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

ضبط `HasGraduations` إلى `true` يرسم علامات على المحاور. المتغير الاختياري `GraduationStep` يتحكم في المسافة بين العلامات على المحور الشعاعي؛ خطوة قيمتها 10 تعني علامة كل 10 درجات.

### نصيحة احترافية
إذا كنت بحاجة إلى عرض تسميات البيانات، استدعِ `radarChart.Series[0].HasDataLabel = true;`. هذا يضيف القيمة الرقمية بجانب كل نقطة، وهو مفيد للعروض التقديمية.

## الخطوة 4: تعبئة المخطط ببيانات عينة (اختياري)

المخطط الراداري بدون بيانات يكون غير مرئي. أدناه طريقة سريعة لإضافة سلسلة من القيم العينية. يمكنك استبدال هذا الجزء بمصدر بياناتك الخاص.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

كل استدعاء لـ `Add` يُدخل نقطة في السلسلة. ترتيب النقاط يتطابق مع المواقع الزاوية حول الدائرة.

## الخطوة 5: حفظ المستند الذي يحتوي على المخطط

أخيرًا، احفظ المستند على القرص. طريقة `Save` تكتب ملف .docx تلقائيًا، مع الحفاظ على المخطط وكل التنسيقات.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

تشغيل البرنامج ينشئ **مستند Word فارغ** يحتوي الآن على مخطط راداري كامل الوظيفة. افتح الملف في Microsoft Word لرؤية النتيجة.

![Radar chart in Word document](radar_chart.png){alt="مخطط راداري تم إدراجه في مستند Word فارغ"}

## الاختلافات الشائعة وحالات الحافة

| الحالة | ما الذي يجب تغييره |
|-----------|----------------|
| **حجم المخطط مختلف** | عدل معلمات العرض/الارتفاع في `InsertChart`. |
| **أنواع مخططات أخرى** | استبدل `ChartType.Radar` بـ `ChartType.Column` أو `ChartType.Pie`، واحتفظ بنفس منطق العلامات. |
| **الحفظ إلى تدفق** | استخدم `document.Save(Stream, SaveFormat.Docx)` |

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [إدراج مخطط منطقة في مستند Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [إنشاء مخطط مبعثر في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [إدراج مخطط عمودي في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}