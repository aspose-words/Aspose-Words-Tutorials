---
category: general
date: 2026-09-14
description: إدراج مخطط راداري في Word باستخدام C#. تعلّم كيفية تعيين عنوان المخطط،
  إضافة عدة سلاسل، وإنشاء المخطط برمجيًا في بضع أسطر فقط.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert radar chart
- set chart title
- create radar chart word
- multiple series radar chart
- create chart programmatically
language: ar
lastmod: 2026-09-14
og_description: إدراج مخطط راداري في Word باستخدام C#. يوضح هذا الدرس كيفية تعيين
  عنوان المخطط، إضافة عدة سلاسل، وإنشاء المخطط برمجيًا.
og_image_alt: Screenshot of a Word document displaying a radar chart with sales data
og_title: إدراج مخطط راداري في Word باستخدام C# – دليل برمجة سريع
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Insert radar chart in Word with C#. Learn how to set chart title, add
    multiple series, and create the chart programmatically in just a few lines.
  headline: Insert radar chart in Word using C# – step‑by‑step guide
  type: TechArticle
tags:
- radar chart
- C#
- Aspose.Words
title: إدراج مخطط راداري في Word باستخدام C# – دليل خطوة بخطوة
url: /ar/net/programming-with-charts/insert-radar-chart-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج مخطط راداري في Word باستخدام C# – دليل خطوة بخطوة

إذا كنت بحاجة إلى **إدراج مخطط راداري** في مستند Word، يوضح لك هذا الدليل كيفية القيام بذلك برمجياً باستخدام C#. ستتعلم أيضاً كيفية **تعيين عنوان المخطط**، إضافة **مخطط راداري متعدد السلاسل**، وحفظ الملف دون مغادرة بيئة التطوير المتكاملة.

يغطي الدليل كل شيء من إعداد المشروع إلى استدعاء `doc.Save` النهائي، بحيث يمكنك نسخ‑لصق المثال الكامل وتشغيله فوراً. لا تحتاج إلى الرجوع إلى أي وثائق خارجية.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6 (أو أحدث) مثبت.
* رخصة صالحة لـ Aspose.Words for .NET (أو مفتاح تقييم مؤقت).
* Visual Studio 2022 أو أي بيئة تطوير C# تفضلها.

> **نصيحة احترافية:** إذا كنت تستخدم النسخة التجريبية المجانية، تذكر ضبط الرخصة قبل إنشاء أول `Document` لتجنب علامة التقييم المائية.

## الخطوة 1: إدراج مخطط راداري في مستند Word

العملية الأولى هي إنشاء `Document` جديد و`DocumentBuilder`. يتيح لك الـ builder الوصول إلى محتوى المستند ويسمح لك بوضع **مخطط راداري** بالضبط حيث تحتاجه.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank Word document.
Document doc = new Document();

// DocumentBuilder provides methods to insert content.
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a radar (radial) chart at the current cursor position.
Chart chart = builder.InsertChart(ChartType.Radar);
```

*لماذا هذه الخطوة مهمة:* `InsertChart` ينشئ كائن مخطط يمكنك تكوينه بالكامل قبل حفظ المستند. استخدام `ChartType.Radar` يخبر Word برسم مخطط شعاعي بدلاً من عمودي أو خطي.

## الخطوة 2: تعيين عنوان المخطط وتدرجات المحاور

المخطط بدون عنوان قد يكون محيراً. هنا **نُعيّن عنوان المخطط** إلى “Sales Radar” ونفعل التدرجات على كلا المحورين (متاح منذ Aspose.Words 24.9 فصاعداً).

```csharp
// Give the chart a meaningful title.
chart.Title.Text = "Sales Radar";

// Enable graduations (grid lines) on both X and Y axes.
chart.AxisX.HasGraduations = true;
chart.AxisY.HasGraduations = true;
```

*لماذا هذه الخطوة مهمة:* العنوان يوفر سياقاً للقراء، والتدرجات تحسن قابلية القراءة من خلال إظهار موقع كل نقطة بيانات على المقياس.

## الخطوة 3: إنشاء سلاسل متعددة للمخطط الراداري

**مخطط راداري متعدد السلاسل** يتيح لك مقارنة فترات مختلفة جنباً إلى جنب. أدناه نضيف سلسلتين—Q1 و Q2—كل منهما يحتوي على ثلاث نقاط بيانات.

```csharp
// Series 1: Q1 data.
chart.Series.Add(
    "Q1",                                 // Series name
    new[] { "Jan", "Feb", "Mar" },        // Category labels
    new[] { 10, 20, 30 }                  // Values
);

// Series 2: Q2 data.
chart.Series.Add(
    "Q2",
    new[] { "Jan", "Feb", "Mar" },
    new[] { 15, 25, 35 }
);
```

*لماذا هذه الخطوة مهمة:* إضافة سلاسل متعددة توضح كيفية مقارنة مجموعات البيانات على نفس المخطط الراداري، وهو طلب شائع للتقارير المبيعاتية أو أداء أو نتائج الاستطلاعات.

## الخطوة 4: حفظ مستند Word برمجياً

أخيراً، **تنشئ المخطط برمجياً** وتخزن المستند على القرص. طريقة `Save` تكتب ملف `.docx` يمكن فتحه في Microsoft Word.

```csharp
// Define the output path. Adjust the directory as needed.
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
    "RadialGraduations.docx"
);

// Save the document containing the radar chart.
doc.Save(outputPath);
```

عند فتح `RadialGraduations.docx`، سترى مخططاً رادارياً بعنوان “Sales Radar” مع سلسلتين (Q1 و Q2) مرسومتين مقابل الشهور Jan‑Mar.

### النتيجة المتوقعة

![Radar chart in Word](https://example.com/radar-chart.png){: .align-center alt="مستند Word يظهر مخطط راداري مع سلسلتين من البيانات"}

تؤكد لقطة الشاشة (أو الملف الفعلي) أن المخطط تم إدراجه، وتعيين عنوانه، وتعبئته بشكل صحيح.

## مثال كامل قابل للتنفيذ

بجمع كل ما سبق، إليك برنامج مستقل يمكنك تجميعه وتشغيله:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a radar chart.
        Chart chart = builder.InsertChart(ChartType.Radar);

        // 3. Set chart title and enable axis graduations.
        chart.Title.Text = "Sales Radar";
        chart.AxisX.HasGraduations = true;
        chart.AxisY.HasGraduations = true;

        // 4. Add two data series.
        chart.Series.Add("Q1", new[] { "Jan", "Feb", "Mar" }, new[] { 10, 20, 30 });
        chart.Series.Add("Q2", new[] { "Jan", "Feb", "Mar" }, new[] { 15, 25, 35 });

        // 5. Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialGraduations.docx"
        );
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

شغّل البرنامج، افتح الملف المُنشأ، وتأكد من أن عملية **إدراج مخطط راداري** نجحت.

## أسئلة شائعة وحالات خاصة

| السؤال | الجواب |
|----------|--------|
| **هل يمكنني تغيير نوع المخطط بعد الإدراج؟** | نعم. بعد `InsertChart`، عيّن قيمة جديدة لـ `ChartType` إلى `chart.Type`. ومع ذلك، إنشاء المخطط بالنوع الصحيح من البداية يكون أكثر كفاءة. |
| **ماذا لو احتجت إلى أكثر من سلسلتين؟** | استدعِ `chart.Series.Add` لكل سلسلة إضافية. سيقوم المخطط تلقائياً بتعديل المفتاح (legend) والألوان. |
| **كيف يمكنني تخصيص الألوان أو العلامات؟** | استخدم `chart.Series[i].Format.Fill.ForeColor` لألوان التعبئة و `chart.Series[i].Marker` لأنماط العلامات. |
| **هل الـ API متوافق مع .NET Framework؟** | نفس الشيفرة تعمل مع .NET Framework 4.7+؛ فقط قم بالإشارة إلى ملف Aspose.Words DLL المناسب. |
| **ماذا لو كنت أستخدم نسخة أقدم من Aspose.Words؟** | تم تقديم خاصية التدرجات (`HasGraduations`) في الإصدار 24.9. بالنسبة للإصدارات الأقدم، يمكنك إضافة خطوط شبكة يدوياً باستخدام `chart.AxisX.MajorGridLines` و `chart.AxisY.MajorGridLines`. |

## الخلاصة

أنت الآن تعرف كيف **تدخل مخطط راداري** في مستند Word باستخدام C#، **تعيّن عنوان المخطط**، تضيف **مخطط راداري متعدد السلاسل**، و**تنشئ المخطط برمجياً**. هذا الحل المتكامل يتيح لك أتمتة التقارير، لوحات التحكم، أو أي سيناريو يتطلب مقارنة بصرية بين الفئات.

بعد ذلك، استكشف المواضيع ذات الصلة مثل **تخصيص ألوان المخطط**، **تصدير المخططات كصور**، أو **دمج المخططات في ملفات PDF**. جرّب مجموعات بيانات مختلفة لترى كيف يتكيف التصور الراداري.

برمجة سعيدة!

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}