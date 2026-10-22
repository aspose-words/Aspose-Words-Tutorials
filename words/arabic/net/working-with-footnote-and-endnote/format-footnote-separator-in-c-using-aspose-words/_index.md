---
category: general
date: 2026-08-10
description: تنسيق فاصل الحاشية في C# باستخدام Aspose.Words لتخصيص خطوط الحواشي والحواشي
  الختامية. تعلم تنسيق الحواشي في C# خلال دقائق.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: ar
lastmod: 2026-08-10
og_description: تنسيق فاصل الحاشية في C# باستخدام Aspose.Words. اتبع هذا الدليل لتنسيق
  فواصل الحواشي والحواشي الختامية بسرعة وبشكل موثوق.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: تنسيق فاصل الحاشية في C# – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: تنسيق فاصل الحاشية في C# باستخدام Aspose.Words
url: /ar/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تنسيق فاصل الحاشية في C# باستخدام Aspose.Words

إذا كنت بحاجة إلى **تنسيق فاصل الحاشية** في مستند Word، يوضح لك هذا الدليل كيفية القيام بذلك باستخدام Aspose.Words لـ .NET. سترى مثالًا كاملاً قابلاً للتنفيذ يغيّر محاذاة ولون فقرة الفاصل، وستتعلم كيفية تطبيق نفس التقنية على فواصل الحواشي الختامية.

يغطي الدليل كل خطوة — من تحميل الملف المصدر إلى حفظ المستند المعدل — بحيث يمكنك نسخ‑لصق الشيفرة في مشروعك الخاص دون الحاجة إلى بحث إضافي.

## ما ستحتاجه

* .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.6+)
* ترخيص صالح لـ Aspose.Words لـ .NET (الإصدار التجريبي المجاني يعمل للتقييم)
* ملف Word يحتوي على حاشية أو حاشية ختامية واحدة على الأقل (مثال: `Footnotes.docx`)
* Visual Studio 2022 أو أي بيئة تطوير C# تفضلها

وجود هذه العناصر جاهزة يتيح لك التركيز على منطق **تنسيق الحاشية في C#** بدلاً من إعداد البيئة.

## الخطوة 1: تحميل المستند الذي يحتوي على الحواشي والحواشي الختامية

العملية الأولى هي إنشاء كائن `Document` يشير إلى ملفك المصدر. تقوم Aspose.Words بقراءة حزمة DOCX بالكامل إلى الذاكرة، مما يمنحك وصولًا كاملاً إلى عقد الحواشي والحواشي الختامية.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*لماذا هذا مهم*: تحميل المستند هو الشرط المسبق لأي تعديل. إذا كان مسار الملف غير صحيح، تقوم Aspose.Words بإلقاء استثناء `FileNotFoundException`، لذا تحقق من المسار قبل المتابعة.

## الخطوة 2: استرجاع عقد الفاصل وفاصل الاستمرار

يتم تخزين فواصل الحواشي والحواشي الختامية كعقد خاصة داخل مجموعات `Footnotes` و `Endnotes`. كل مجموعة تعرض خصائص `Separator` و `ContinuationSeparator` التي تُعيد مرجعًا من نوع `Node`.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*لماذا هذا مهم*: عقدة `Separator` تمثل الخط الذي يفصل بصريًا النص الرئيسي عن كتلة الحاشية. بالحصول على مرجع، يمكنك تعديل تنسيق الفقرة، الخط، أو حتى استبدال العقدة بالكامل.

## الخطوة 3: تغيير النمط البصري لفاصل الحاشية

في معظم مستندات Word يكون الفاصل فقرة واحدة تحتوي على شرطة أو نجمة. يتحقق الشيفرة أدناه ما إذا كان الفاصل `Paragraph`، وإذا كان كذلك، يوسّطها ويغيّر لون النص إلى الرمادي.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### تنسيق فاصل الاستمرار (اختياري)

يظهر فاصل الاستمرار عندما تمتد الحاشية عبر صفحات متعددة. يمكنك تنسيقه بطريقة مشابهة:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*لماذا هذا مهم*: محاذاة الفاصل تحسّن قابلية القراءة، وتغيير اللون يميّزه عن نص الفقرة العادي. يمكنك استبدال `ParagraphAlignment.Center` بـ `Left` أو `Right` لتتناسب مع إرشادات تصميم مستندك.

## الخطوة 4: حفظ المستند المعدل

بعد تطبيق النمط المطلوب، احفظ المستند مرة أخرى على القرص. يمكنك استبدال الملف الأصلي أو إنشاء نسخة جديدة.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

عند فتح `Footnotes_Styled.docx` في Microsoft Word، يظهر فاصل الحاشية متمركزًا ورماديًا، تمامًا كما حددت الشيفرة.

## تنويعات متقدمة

### تنسيق فاصل الحاشية الختامية

إذا كان مستندك يستخدم أيضًا الحواشي الختامية، يمكنك تطبيق نفس المنطق على مجموعة `Endnotes`:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### استخدام سلسلة مخصصة للفاصل

أحيانًا تريد أن يكون الفاصل سلسلة من النجوم (`***`). استبدل الـ runs الحالية بـ run جديد:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### التعامل مع المستندات التي لا تحتوي على عقدة فاصل

حالة نادرة هي مستند يحذف عقدة الفاصل (مثلاً عندما حذفها المؤلف). في هذه الحالة تُعيد `document.Footnotes.Separator` القيمة `null`. احمِ الشيفرة من ذلك:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## الأخطاء الشائعة وكيفية تجنّبها

| المشكلة | سبب حدوثها | الحل |
|---------|------------|------|
| **الفاصل ليس `Paragraph`** | بعض قوالب Word تستخدم `Table` أو `Shape` كفاصل. | تحقق من نوع العقدة باستخدام `is Paragraph` قبل التحويل. |
| `Runs` مجموعة فارغة | قد يكون الفاصل فقرة فارغة. | تحقق من أن `Runs.Count > 0` قبل الوصول إلى `Runs[0]`. |
| لم يتم تطبيق الترخيص | بدون ترخيص، تقوم Aspose.Words بإدراج علامة مائية وقد تقيد استخدام الـ API. | استدعِ `License license = new License(); license.SetLicense("Aspose.Words.lic");` في بداية برنامجك. |
| الحفظ إلى مجلد للقراءة فقط | طريقة `Save` تُلقي استثناء `UnauthorizedAccessException`. | تأكد من أن الدليل الهدف لديه صلاحيات كتابة. |

معالجة هذه المشكلات مبكرًا تمنع استثناءات وقت التشغيل وتضمن تجربة سلسة لتعديل فاصل الحاشية **modify footnote separator**.

## مثال كامل قابل للتنفيذ

فيما يلي تطبيق console مستقل يوضح كل خطوة نوقشت أعلاه. انسخ الشيفرة إلى مشروع console جديد لـ .NET، استبدل مسارات الملفات، وشغّله.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**النتيجة المتوقعة**  

عند فتح `Footnotes_Styled.docx`:

* خط فاصل الحاشية متمركز تحت النص الرئيسي.  
* لونه يظهر كرمادي فاتح، مما يجعله مميزًا بصريًا.  
* إذا كان المستند يحتوي على حواشي ختامية، فإن فواصلها متمركزة أيضًا ومصبوغة بالرمادي (أو اللون الرمادي الداكن

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [معالجة الكلمات مع الحاشية والحاشية الختامية](/words/english/net/working-with-footnote-and-endnote/)
- [تحديد موضع الحاشية والحاشية الختامية](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [العمل مع الحاشية والحاشية الختامية](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}