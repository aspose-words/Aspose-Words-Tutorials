---
category: general
date: 2026-10-10
description: ترجمة الفقرة إلى الفرنسية وتعلم كيفية تغيير تسمية بيانات المخطط، تخصيص
  تسمية بيانات المخطط، وحفظ ملف docx المُعدَّل باستخدام Aspose.Words AI.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: ar
lastmod: 2026-10-10
og_description: ترجمة الفقرة إلى الفرنسية وتعلم كيفية تغيير تسمية بيانات المخطط، تخصيص
  تسمية بيانات المخطط، وحفظ ملف docx المُعدَّل باستخدام Aspose.Words AI.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: ترجمة الفقرة إلى الفرنسية وتغيير تسمية المخطط في وورد
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: ترجمة الفقرة إلى الفرنسية وتغيير تسمية المخطط في وورد
url: /ar/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ترجمة فقرة إلى الفرنسية وتغيير تسمية المخطط في Word

إذا كنت بحاجة إلى **ترجمة الفقرة إلى الفرنسية** مع تحديث مخطط داخل نفس مستند Word، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. باستخدام Aspose.Words AI يمكنك ترجمة النص تلقائيًا، ثم تعديل تسمية بيانات المخطط وأخيرًا حفظ ملف `.docx` المعدل—كل ذلك في بضع خطوات بسيطة.

يغطي الدليل كل شيء بدءًا من تحميل الملف المصدر وحتى حفظ التغييرات. في النهاية ستتمكن من ترجمة أي فقرة، تخصيص تسمية بيانات المخطط، وإنتاج ملف Word جديد جاهز للتوزيع. لا تحتاج إلى أي سكريبتات خارجية؛ كل سير العمل موجود في برنامج C# واحد.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)
- رخصة Aspose.Words for .NET (أو مفتاح تقييم مجاني)
- اتصال بالإنترنت لمترجم Google AI (فئة `Translator` تستخدم API جوجل في الخلفية)
- مستند Word (`input.docx`) يحتوي على فقرة واحدة على الأقل ومخطط واحد

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

أنشئ تطبيق console جديد وأضف حزمة Aspose.Words من NuGet:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

الآن أدرج المساحات الاسمية المطلوبة في أعلى ملف `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

هذه الاستيرادات تمنحك القدرة على تحميل المستند، الترجمة بالذكاء الاصطناعي، وتعديل المخططات.

## الخطوة 2: تحميل مستند Word المصدر

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

تحميل الملف ينشئ تمثيلًا في الذاكرة يمكنك الاستعلام عنه وتعديله دون لمس الملف الأصلي على القرص.

## الخطوة 3: ترجمة الفقرة الأولى إلى الفرنسية

الفقرة الأولى غالبًا ما تكون عنوانًا أو جملة تمهيدية، لذا فهي مرشح جيد للترجمة. فئة `Translator` تُجرد استدعاء نموذج AI الخاص بجوجل.

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**لماذا يعمل هذا:**  
`paragraph.Runs.Clear()` يزيل جميع تشغيلات النص الحالية، مما يضمن أن الترجمة الجديدة لا تُلصق بالمحتوى القديم. `new Run(document, translatedText)` ينشئ تشغيلًا جديدًا يرث تنسيق الفقرة.

## الخطوة 4: تحديد المخطط الأول وتخصيص تسمية البيانات الخاصة به

المخططات تُخزن كعُقد `Shape` من النوع `NodeType.Shape`. يمكن جلب المخطط الأول باستخدام `GetChild`.

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**شرح الخطوات الرئيسية:**

- `GetChild(NodeType.Shape, 0, true)` يجري بحثًا بعمق أول ويعيد الشكل الأول، وهو في حالتنا مخطط.
- `ChartSeries` تمثل مجموعة من نقاط البيانات؛ السلسلة الأولى (`Series[0]`) عادةً ما تت对应 إلى مجموعة البيانات الأساسية.
- `ChartDataLabelPosition.OutsideEnd` ينقل التسمية إلى خارج نهاية العمود، مما يحسن القابلية للقراءة.
- ضبط `dataLabel.Text` إلى سلسلة فرنسية يطابق التسمية مع الفقرة المترجمة.

## الخطوة 5: حفظ المستند مع الفقرة المترجمة

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

في هذه المرحلة يحتوي المستند على الفقرة الفرنسية لكنه لا يزال يحمل إعدادات المخطط الأصلية.

## الخطوة 6: حفظ المستند مع المخطط المحدث

يمكنك إعادة استخدام نفس كائن `Document`—لا حاجة لإعادة تحميله—لأن تعديلات المخطط موجودة بالفعل في الذاكرة.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

كلا الملفين الآن جاهزان للتوزيع:

- **`translated.docx`** – يحتوي على الفقرة الفرنسية.
- **`chart-updated.docx`** – يحتوي على الفقرة الفرنسية *و* تسمية المخطط المخصصة.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في `Program.cs`. يَـُـترجم ويعمل مباشرة، بشرط استبدال `YOUR_DIRECTORY` بمسار مجلد حقيقي.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

namespace WordAiDemo
{
    class Program
    {
        static void Main()
        {
            // ---------- Load the source document ----------
            string inputPath = @"YOUR_DIRECTORY/input.docx";
            Document document = new Document(inputPath);
            Console.WriteLine("Document loaded.");

            // ---------- Translate the first paragraph ----------
            Paragraph paragraph = document.FirstSection.Body.FirstParagraph;
            string original = paragraph.GetText();
            string translated = Translator.Translate(original, Language.French);
            Console.WriteLine


## ماذا يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شاملة من الكود مع شروحات خطوة‑بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك الخاصة.

- [تخصيص تسمية بيانات المخطط](/words/english/net/programming-with-charts/chart-data-label/)
- [تنسيق عدد تسميات البيانات في المخطط](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [تسمية بيانات المخطط](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}