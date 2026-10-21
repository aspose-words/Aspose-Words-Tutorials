---
category: general
date: 2026-08-07
description: استرجاع فاصل الحاشية باستخدام Aspose.Words لـ .NET. تعلّم كيفية استخراج
  فواصل الحواشي والحواشي الختامية، فحص أنواع العقد، وتعديلها في C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: ar
lastmod: 2026-08-07
og_description: استرجاع فاصل الحاشية السفلية باستخدام Aspose.Words لـ .NET. يوضح هذا
  الدليل كيفية استخراج فواصل الحواشي السفلية والنهائية، والتحقق من نوع العقد الخاصة
  بها، وحفظ التغييرات.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: استرجاع فاصل الحاشية في C# – دليل Aspose.Words خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: استرجاع فاصل الحاشية السفلية في C# – دليل Aspose.Words الكامل
url: /ar/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استرجاع فاصل الحاشية السفلية في C# – دليل Aspose.Words الكامل

إذا كنت بحاجة إلى **استرجاع فاصل الحاشية السفلية** من مستند Word، يوضح لك هذا الدرس بالضبط كيفية القيام بذلك باستخدام Aspose.Words for .NET. سواءً كنت تبني خدمة معالجة مستندات أو تقوم بتنظيف تنسيق الحواشي، سترى مثالًا كاملًا قابلاً للتنفيذ يستخرج كل من فواصل الحواشي السفلية والنهائية.

في هذا الدليل ستتعلم كيفية تحميل ملف `.docx`، استدعاء خصائص `FootnoteSeparator` و `EndnoteSeparator`، فحص كائنات `Node` المرتجعة، واختيارياً استبدال خط الفاصل. لا حاجة لأي وثائق خارجية—كل ما تحتاجه مضمّن أدناه.

## المتطلبات المسبقة

* .NET 6.0 أو أحدث (الكود يعمل أيضًا على .NET Framework 4.7.2)
* حزمة Aspose.Words for .NET على NuGet (الإصدار 24.9 أو أحدث)
* مستند Word يحتوي على حواشي سفلية و/أو حواشي نهائية (مثال: `Footnotes.docx`)

يمكنك إضافة حزمة Aspose.Words بالأمر التالي في سطر الأوامر:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

أنشئ مشروع وحدة تحكم جديد أو أضف الكود إلى مشروع موجود. توجيهات `using` المطلوبة مدرجة أدناه.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

هذه المساحات الاسمية تمنحك الوصول إلى فئة `Document`، هيكلية `Node`، وتعداد `NodeType` اللازم لعمليات **استرجاع فاصل الحاشية السفلية**.

## الخطوة 2: تحميل المستند الذي يحتوي على حواشي سفلية ونهائية

العملية الأولى في أي سير عمل Aspose.Words هي تحميل الملف المصدر. استبدل مسار العنصر النائب بالموقع الفعلي لملف `.docx` الخاص بك.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

تحميل الملف يُعد شجرة العقد الداخلية، وهو أمر أساسي لـ **استرجاع فاصل الحاشية السفلية** لأن عقد الفاصل تعيش داخل تلك الشجرة.

## الخطوة 3: استرجاع عقدة فاصل الحاشية السفلية

الآن يمكنك **استرجاع فاصل الحاشية السفلية** بالوصول إلى خاصية `FootnoteSeparator` لكائن `Document`. تمثل هذه العقدة الخط الذي يفصل الحواشي السفلية عن نص الجسم الرئيسي.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

ستكون قيمة `NodeType` هي `Paragraph` لخط الفاصل القياسي. معرفة نوع العقدة يساعدك على تحديد ما إذا كنت بحاجة لتعديل الفاصل أو استبداله بالكامل.

## الخطوة 4: استرجاع عقدة فاصل الحاشية النهائية

وبالمثل، يمكنك **استرجاع فاصل الحاشية النهائية** باستخدام خاصية `EndnoteSeparator`. هذه العقدة تفصل الحواشي النهائية عن المحتوى الرئيسي.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

كلا عقدي الفاصل تشتركان في نفس `NodeType` (`Paragraph`) في معظم المستندات، لكن يمكن تخصيصهما بشكل مستقل.

## الخطوة 5: فحص أو تعديل محتوى الفاصل (اختياري)

إذا كنت بحاجة لتغيير المظهر البصري للفاصل—مثل استبدال خط من الشرطات بخط رفيع—يمكنك تحرير عقدة `Paragraph` مباشرة. فيما يلي مثال يستبدل نص الفاصل الافتراضي بسلسلة مخصصة.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

بعد تعديل العقد، يمكنك حفظ المستند لرؤية التغييرات في Word.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## مخرجات وحدة التحكم المتوقعة

عند تشغيل البرنامج مع ملف `Footnotes.docx` الأصلي، يجب أن ترى شيئًا مشابهًا لـ:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

إذا فتحت `Footnotes_Updated.docx` في Microsoft Word، ستظهر فواصل الحواشي السفلية والنهائية النص المخصص الذي أدخلته.

## أسئلة شائعة وحالات خاصة

**ماذا لو لم يحتوي المستند على حواشي سفلية؟**  
خاصية `FootwordSeparator` لا تزال تُعيد عقدة `Paragraph` لأن Word دائمًا يتضمن عنصر نائب للفاصل. ستكون العقدة فارغة، لذا يمكنك إضافة محتوى بأمان أو تركها كما هي.

**هل يمكنني استرجاع الفاصل لقسم معين؟**  
فواصل الحواشي السفلية والنهائية هي على مستوى المستند بالكامل، ليست خاصة بالقسم. إذا كنت تحتاج تحكمًا على مستوى القسم، يجب العمل مع `Section.FootnoteOptions` و `Section.EndnoteOptions` بدلاً من عقد الفاصل العامة.

**هل يعمل هذا مع .NET Core؟**  
نعم. Aspose.Words for .NET متعدد المنصات، ويمكن تشغيل نفس الكود على Windows وLinux وmacOS مع .NET 6+.

**ما نوع العقدة التي يجب أن أتوقعها؟**  
كل من `FootnoteSeparator` و `EndnoteSeparator` تُعيد عقدة `Paragraph` (`NodeType.Paragraph`). إذا صادفت نوعًا مختلفًا، قد يكون المستند تالفًا، ويجب إعادة تحميله أو التحقق من صحة الملف المصدر.

## الكود الكامل للنسخ السريع

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

انسخ الكود إلى ملف `Program.cs`، عدّل مسارات الملفات، وشغّل `dotnet run`. يوضح البرنامج سير عمل **استرجاع فاصل الحاشية السفلية** الكامل، من تحميل المستند إلى حفظ التغييرات.

## الخلاصة

أنت الآن تعرف كيف **تسترجع فاصل الحاشية السفلية** و **تسترجع فاصل الحاشية النهائية** باستخدام Aspose.Words for .NET، وتفحص `document node type` الخاص بهما، وتستبدل محتواهما اختياريًا. تتيح لك هذه التقنية أتمتة تنسيق الحواشي، إنشاء خطوط فاصل مخصصة، أو التحقق من بنية المستند في أي تطبيق C#.

بعد ذلك، قد ترغب في استكشاف مواضيع ذات صلة مثل **استخراج الحواشي السفلية في C#** للنصوص الفردية للحواشي، أو تعلم كيفية **تعديل علامات مرجع الحاشية** باستخدام `FootnoteOptions`. كلا المفهومين يبنيان مباشرةً على أساسيات شجرة العقد التي تم تغطيتها هنا.

برمجة سعيدة، ولا تتردد في تجربة أنماط فاصل مختلفة لتتناسب مع هوية مشروعك!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [معالجة الكلمات مع الحاشية السفلية والنهائية](/words/english/net/working-with-footnote-and-endnote/)
- [إضافة محتوى باستخدام Document Builder في Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [العمل مع الحاشية السفلية والنهائية](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}