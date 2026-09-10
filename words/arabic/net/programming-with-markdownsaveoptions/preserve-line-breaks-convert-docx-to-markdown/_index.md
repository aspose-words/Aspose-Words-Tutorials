---
category: general
date: 2026-02-13
description: احفظ فواصل الأسطر أثناء تحويل DOCX إلى markdown. تعلم كيفية حفظ Word
  كـ markdown، وتصدير الفقرات الفارغة، والحفاظ على تنسيق النص دون تغيير.
draft: false
keywords:
- preserve line breaks
- convert docx to markdown
- save word as markdown
- how to export empty
- how to preserve breaks
language: ar
og_description: حافظ على فواصل الأسطر أثناء تحويل DOCX إلى markdown. يوضح هذا الدليل
  كيفية حفظ Word كـ markdown وتصدير الفقرات الفارغة بشكل صحيح.
og_title: 'حافظ على فواصل الأسطر: تحويل DOCX إلى Markdown'
tags:
- Aspose.Words
- C#
- Markdown
title: 'حافظ على فواصل الأسطر: تحويل DOCX إلى ماركداون'
url: /ar/net/programming-with-markdownsaveoptions/preserve-line-breaks-convert-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# الحفاظ على فواصل الأسطر: تحويل DOCX إلى Markdown

هل احتجت يومًا إلى **الحفاظ على فواصل الأسطر** عند تحويل ملف DOCX إلى Markdown؟ إنها مشكلة شائعة—يصبح مستند Word الجميل جدارًا من النص، وتختفي تلك الأسطر الفارغة المتعمدة. الخبر السار؟ يمكنك الاحتفاظ بكل فاصل سطر، حتى الفقرات الفارغة، باستخدام بعض الإعدادات البسيطة.

في هذا الدرس سنستعرض العملية الكاملة لـ **حفظ Word كـ Markdown**، بدءًا من تحميل المستند المصدر وحتى تكوين وضع التصدير الصحيح. في النهاية ستعرف *كيفية تصدير الفقرات الفارغة*، *كيفية الحفاظ على الفواصل* في التخطيطات المعقدة، وستحصل على عينة كود جاهزة للنسخ واللصق. لا أجزاء مفقودة، ولا نهايات “انظر إلى الوثائق” الميتة.

## ما ستتعلمه

- لماذا يعتبر الحفاظ على فواصل الأسطر مهمًا للقراءة وللأدوات اللاحقة.  
- كيفية **تحويل DOCX إلى markdown** باستخدام Aspose.Words for .NET.  
- أي إعدادات `MarkdownSaveOptions` تتحكم في معالجة الفقرات الفارغة.  
- نصائح عملية للتعامل مع الحالات الخاصة مثل الجداول والقوائم وكتل الشيفرة.  
- مثال كامل قابل للتنفيذ يمكنك إدراجه في أي مشروع C# اليوم.

### المتطلبات المسبقة

- .NET 6+ (أو .NET Framework 4.7.2+) مثبت.  
- رخصة لـ **Aspose.Words for .NET** (الإصدار التجريبي المجاني يعمل لهذا العرض).  
- إلمام أساسي بـ C# ومفهوم Markdown.  

إذا كان لديك كل ذلك، فلنبدأ.

![Preserve line breaks diagram](preserve-line-breaks.png "Diagram illustrating how empty paragraphs become line breaks in Markdown")

## الحفاظ على فواصل الأسطر – لماذا هو مهم

عندما يحتوي مستند Word على أسطر فارغة متعمدة—اعتبرها فواصل بصرية بين الأقسام—غالبًا ما تُحذف هذه الأسطر أثناء التحويل. Markdown، بطبيعته، يعامل فاصل سطر واحد كاستمرار لنفس الفقرة، لذا يجب تمثيل السطر الفارغ صراحة. إذا لم **تحافظ على فواصل الأسطر**، قد يبدو الناتج مكتظًا، وقد تقوم المحللات اللاحقة (مثل مولدات المواقع الثابتة) بدمج الأقسام عن غير قصد.

الحفاظ على هذه الفواصل ليس مجرد مسألة جمالية؛ بل يساعد الأدوات التي تعتمد على حدود الفقرات لأمور مثل وضع الحواشي، أو التنسيق المخصص، أو حتى استخراج العناوين بطريقة صديقة للسيو. باختصار، التحويل الدقيق يحترم نية المؤلف.

## تحويل DOCX إلى Markdown باستخدام Aspose.Words

يوفر لك Aspose.Words تحكمًا دقيقًا في عملية التحويل. الفئة الأساسية هي `MarkdownSaveOptions`، التي تتيح لك تحديد كيفية تصدير الفقرات الفارغة. أدناه سنضبط `EmptyParagraphExportMode` إلى `EmptyLine`، وهو وضع يترجم الفقرة الفارغة في Word إلى سطر فارغ في Markdown.

### تنفيذ خطوة بخطوة

### 1️⃣ تحميل المستند المصدر

أولاً، وجه المكتبة إلى ملف `.docx` الخاص بك. يقوم مُنشئ `Document` بكل العمل الشاق—تحليل الأنماط، الصور، ومعلومات التخطيط.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Adjust the path to match your environment
string inputPath  = @"C:\Docs\MyReport.docx";
Document doc = new Document(inputPath);
```

> **لماذا هذا مهم:** تحميل المستند مبكرًا يمنحك الوصول إلى هيكله الداخلي، مما يسمح لك بتعديل الخيارات بناءً على ما تكتشفه (مثل اكتشاف ما إذا كان الملف يحتوي فعليًا على فقرات فارغة).

### 2️⃣ تكوين خيارات حفظ Markdown

هنا نجيب على سؤال **“كيفية تصدير الفقرات الفارغة”**. يقدم تعداد `EmptyParagraphExportMode` ثلاث خيارات:

| Mode | النتيجة في Markdown |
|------|--------------------|
| `EmptyLine` | يُدرج سطرًا فارغًا (`\n\n`). |
| `PreserveLineBreaks` | يحول كل فاصل سطر إلى فاصل صلب (`  \n`). |
| `None` | يحذف الفقرة الفارغة تمامًا. |

في معظم السيناريوهات التي تريد فيها مجرد فجوة بصرية، `EmptyLine` هو الحل.

```csharp
MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
{
    // Export empty paragraphs as a single empty line.
    // This is the most intuitive way to keep visual spacing.
    EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine,

    // Optional: keep original line breaks inside paragraphs.
    // Uncomment if you need finer control.
    // PreserveLineBreaks = true
};
```

> **نصيحة احترافية:** إذا كنت بحاجة أيضًا إلى الحفاظ على فواصل الأسطر اليدوية (Shift + Enter في Word)، اضبط `PreserveLineBreaks = true`. بهذه الطريقة، تبقى كل من الفقرات الفارغة وفواصل الأسطر الناعمة صالحة بعد التحويل.

### 3️⃣ حفظ المستند كـ Markdown

الآن نكتب ملف الإخراج. يمكنك اختيار أي مجلد تريده؛ فقط تأكد أن الامتداد هو `.md`.

```csharp
string outputPath = @"C:\Docs\MyReport.md";
doc.Save(outputPath, mdOpts);
Console.WriteLine($"✅ Conversion complete! Markdown saved to {outputPath}");
```

هذه هي العملية بالكامل. شغّل البرنامج، افتح ملف `.md`، وسترى الأسطر الفارغة تمامًا حيث كانت في ملف Word الأصلي.

### مثال كامل يعمل

بجمع كل ذلك معًا، إليك تطبيق console مستقل يمكنك تجميعه فورًا:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source DOCX
        string inputPath = @"C:\Docs\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Set up Markdown options to preserve empty paragraphs
        MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
        {
            EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine,
            // PreserveLineBreaks = true   // Uncomment if you need soft line breaks
        };

        // 3️⃣ Save as Markdown
        string outputPath = @"C:\Docs\WithEmptyParas.md";
        doc.Save(outputPath, mdOpts);

        Console.WriteLine($"✅ Document converted! Check: {outputPath}");
    }
}
```

**الناتج المتوقع:** افتح `WithEmptyParas.md` في أي محرر. ستلاحظ أن كل سطر فارغ من `input.docx` يظهر كسطر فارغ في ملف Markdown، محافظًا على الفاصل البصري الذي صممته.

## حفظ Word كـ Markdown – سيناريوهات متقدمة

### معالجة الجداول والقوائم

تتحول الجداول في Word إلى جداول Markdown تلقائيًا، لكن الصفوف الفارغة قد تكون صعبة. إذا كان صف الجدول يحتوي على خلية فارغة فقط، فإن Aspose.Words يتعامل معها كفقرة فارغة. لا يزال `EmptyParagraphExportMode` ساريًا، لذا ستحصل على سطر فارغ **خارج** الجدول—not داخلها. للحفاظ على فجوة بصرية *داخل* الجدول، أدخل مساحة غير قابلة للكسر (`&nbsp;`) في الخلية.

```csharp
// Example: Adding a placeholder to an empty cell
Table table = doc.GetChild(NodeType.Table, 0, true) as Table;
Cell emptyCell = table.Rows[2].Cells[1];
emptyCell.AppendChild(new Paragraph(doc));
emptyCell.FirstParagraph.AppendChild(new Run(doc, "\u00A0")); // non‑breaking space
```

### كتل الشيفرة والنص المسبق التنسيق

إذا كان ملف DOCX يحتوي على شيفرة مسبقة التنسيق، سيقوم Aspose.Words بلفها بثلاثة علامات backticks. تُحفظ الأسطر الفارغة داخل كتلة الشيفرة تلقائيًا، بغض النظر عن `EmptyParagraphExportMode`. ومع ذلك، إذا لاحظت فقدان أسطر فارغة، تحقق مرة أخرى من أن نمط الفقرة في Word الأصلي مضبوط على “No Spacing”. بهذه الطريقة، تتعامل المكتبة مع كل سطر كفقرة منفصلة.

### متى تستخدم `PreserveLineBreaks` بدلاً من ذلك

أحيانًا تحتاج إلى فاصل سطر صلب (`  `) بدلاً من فقرة فارغة كاملة. على سبيل المثال، تعتمد القصائد أو كتل العناوين غالبًا على فواصل سطر واحدة. غيّر الخيار:

```csharp
mdOpts.PreserveLineBreaks = true;   // Turns soft breaks into Markdown hard breaks
mdOpts.EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.None; // optional
```

الآن كل `Shift+Enter` في Word يتحول إلى `  \n` في Markdown، بينما تختفي الفقرات الفارغة تمامًا (إلا إذا احتفظت أيضًا بـ `EmptyLine`).

## كيفية تصدير الفقرات الفارغة بشكل صحيح

الإجابة المختصرة: اضبط `EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine`. الإجابة الطويلة تتضمن فهم *لماذا* هذا يعمل.

- **EmptyParagraphExportMode** يخبر أداة التسلسل *ماذا* تفعل مع فقرة لا تحتوي على أي نص (runs).  
- **EmptyLine** يُدرج سطرين جديدين، وهو ما يفسره Markdown كفاصل فقرات.  
- الأوضاع الأخرى إما تُدمّر الفقرة (`None`) أو تُعامل فواصل الأسطر كفواصل صلبة (`PreserveLineBreaks`).

إذا نسيت ضبط هذا الإعداد، يكون السلوك الافتراضي هو `None`، وتختفي جميع الأسطر الفارغة—وهو بالضبط المشكلة التي نحاول حلها.

## كيفية الحفاظ على الفواصل في المستندات المعقدة

غالبًا ما تمزج المستندات المعقدة بين العناوين، الصور، والحواشي. إليك قائمة تحقق لضمان عدم فقدان أي فواصل أسطر:

| عنصر قائمة التحقق | لماذا يهم |
|----------------|-----------|
| **Validate empty paragraphs** | استخدم `doc.GetChildNodes(NodeType.Paragraph, true)` لعد الفواصل الفارغة قبل التحويل. |
| **Enable `PreserveLineBreaks` for poetry** | يضمن بقاء فواصل السطر الواحدة. |
| **Check image captions** | التسميات التوضيحية هي فقرات منفصلة؛ تحتاج إلى نفس وضع التصدير. |
| **Run a post‑conversion diff** | قارن النص الأصلي (المستخرج عبر `doc.GetText()`) مع ناتج Markdown. |
| **Test with a Markdown viewer** | بعض العارضات تتعامل مع الأسطر الفارغة المتعددة بشكل مختلف؛ تحقق من النتيجة البصرية. |

### كود التحقق النموذجي

```csharp
// Count empty paragraphs before saving
int emptyCount = 0;
NodeCollection paragraphs = doc.GetChildNodes(NodeType.Paragraph, true);
foreach (Paragraph p in paragraphs)
{
    if (p.GetText().Trim().Length == 0)
        emptyCount++;
}
Console.WriteLine($"Document contains {emptyCount} empty paragraph(s).");
```

تشغيل هذا قبل خطوة الحفظ يمنحك الثقة بأن التحويل سيتعامل مع العدد الدقيق من فواصل الأسطر التي تتوقعها.

## المشكلات الشائعة والنصائح الاحترافية

- **المشكلة:** 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}