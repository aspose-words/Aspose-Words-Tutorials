---
category: general
date: 2026-08-17
description: كيفية إضافة عناصر تحكم ActiveX وإدراج مخطط دائري في مستند Word باستخدام
  Aspose.Words. تفجير شريحة وحفظه كملف DOCX في بضع خطوات.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: ar
lastmod: 2026-08-17
og_description: كيفية إضافة عناصر تحكم ActiveX، إدراج مخطط دائري، تفجير شريحة، وحفظ
  كملف DOCX باستخدام Aspose.Words – دليل كامل خطوة بخطوة.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: كيفية إضافة ActiveX وإدراج مخطط دائري في مستند Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: كيفية إضافة ActiveX وإدراج مخطط دائري في مستند Word
url: /ar/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة ActiveX وإدراج مخطط دائري في مستند Word

إذا كنت بحاجة إلى **how to add ActiveX** عناصر تحكم وتضمين مخطط في مستند Word، فإن هذا الدرس يوضح لك حلاً كاملاً قابلاً للتنفيذ. باستخدام Aspose.Words يمكنك وضع زر **CommandButton** من نوع ActiveX، إنشاء مخطط دائري، تفجير شريحة لتسليط الضوء، وأخيرًا **save as DOCX** في بضع أسطر من C#.

في الأقسام أدناه ستشاهد كل الاستيرادات المطلوبة، قائمة شفرة كاملة، وتفسيرات لماذا كل خطوة مهمة. بنهاية هذا الدرس ستكون قادرًا على دمج عناصر تحكم تفاعلية وبيانات مرئية في أي ملف .docx تنشئه برمجيًا.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود:

* .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)
* حزمة Aspose.Words for .NET (متاحة عبر NuGet)
* بيئة تطوير مثل Visual Studio 2022 أو VS Code
* إلمام أساسي بـ C# ونموذج كائنات Word

لا توجد مكتبات مخطط طرف ثالث إضافية مطلوبة—Aspose.Words يوفر إنشاء المخططات مدمجًا.

## كيفية إضافة عناصر تحكم ActiveX باستخدام Aspose.Words

تسمح لك عناصر تحكم ActiveX بتضمين عناصر واجهة مستخدم تفاعلية مباشرة في ملف Word. في هذا الدليل نضيف **CommandButton** يمكن ربطه لاحقًا بشيفرة VBA.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**لماذا يعمل هذا:**  
`InsertForms2OleControl` ينشئ حاوية OLE يتعرف عليها واجهة Word كعنصر تحكم ActiveX. ضبط نوع التحكم إلى `CommandButton` وإعطاؤه تسمية يجعله يتصرف كزر قياسي عندما يفتح المستخدم الملف في Word.

ضبط نوع التحكم إلى `CommandButton` وإعطاؤه تسمية يجعل الزر يتصرف كزر قياسي عند فتح الملف في Word.

## إدراج مخطط دائري وتفجير شريحة

المخططات مفيدة لتصوير البيانات دون مغادرة المستند. الخطوات التالية توضح **how to insert chart** وبشكل خاص **pie chart** تكون شريحته الأولى منفصلة.

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**لماذا تفجير الشريحة:**  
استدعاء `SetExplode(0, true)` يخبر Aspose.Words بتحريك النقطة البيانية الأولى، مما يجذب انتباه القارئ إلى ذلك الجزء. هذه تقنية شائعة في العروض لتسليط الضوء على قيمة رئيسية.

## حفظ كـ DOCX

بعد إضافة زر ActiveX والمخطط، احفظ المستند على القرص. هذه الخطوة توضح **save as DOCX** باستخدام الطريقة القياسية.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

الملف `Output.docx` الآن يحتوي على زر تفاعلي، مخطط دائري بشريحة منفصلة، ويمكن فتحه في Microsoft Word دون إضافات إضافية.

## مثال كامل قابل للتنفيذ

بجمع كل شيء معًا، إليك برنامج مستقل يمكنك نسخه إلى تطبيق Console وتشغيله فورًا.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**النتيجة المتوقعة:**  
فتح `Output.docx` في Word يظهر زرًا معنواً *Click Me* ومخططًا دائريًا تكون شريحته الأولى (January) منفصلة عن البقية. الزر جاهز لمعالجة أحداث VBA، ويمكن تعديل المخطط باستخدام أدوات المخططات المدمجة في Word.

## الأسئلة الشائعة وحالات الحافة

* **Can I add other ActiveX types?**  
  نعم. استبدل `Forms2OleControlType.CommandButton` بأي قيمة من تعداد `Forms2OleControlType` (مثل `CheckBox`، `OptionButton`). نمط الإدراج يبقى نفسه.

* **What if I need a different chart type?**  
  استخدم `ChartType.Bar`، `ChartType.Line`، إلخ، في استدعاء `InsertChart`. خطوة **how to insert chart** تظل كما هي؛ فقط قيمة التعداد تتغير.

* **How to control the size of the exploded slice?**  
  Aspose.Words يدعم حاليًا علم تفجير ثنائي (true/false). للتحكم الدقيق (مثل مسافة الإزاحة) ستحتاج إلى تعديل OOXML الأساسي بعد الحفظ.

* **Is the document compatible with older Word versions?**  
  حفظ كـ DOCX يضمن التوافق مع Word 2007 وما بعده. بالنسبة إلى Word 2003 يمكنك تغيير `SaveFormat.Doc` لكن دعم ActiveX محدود في ذلك التنسيق.

* **Do I need to reference `System.Drawing`?**  
  لا. جميع كائنات الرسم توفرها Aspose.Words، لذا الحزمة الوحيدة المطلوبة عبر NuGet هي `Aspose.Words`.

## الخلاصة

أنت الآن تعرف **how to add ActiveX**، **insert a pie chart**، **explode a pie slice**، و**save as DOCX** باستخدام Aspose.Words for .NET. المثال الكامل يغطي كل خطوة من إنشاء المستند إلى حفظه النهائي، ويشرح السبب وراء كل استدعاء API.

بعد ذلك، قد ترغب في استكشاف:

* إضافة ماكرو VBA يستجيب لنقر زر CommandButton (**how to insert chart** وتحديث البيانات تلقائيًا)
* تخصيص مظهر المخطط (الألوان، تسميات البيانات) لتتناسب مع هوية الشركة
* تضمين عناصر تحكم ActiveX إضافية مثل **ComboBox** أو **ListBox** لنماذج أكثر غنى

لا تتردد في تجربة الشفرة، استبدال البيانات النموذجية، ودمج الحل في خطوط إنتاج إنشاء المستندات الخاصة بك. Happy coding!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إدراج مخطط عمودي في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [إدراج مخطط عمودي بسيط في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [إدراج مخطط فقاعة في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}