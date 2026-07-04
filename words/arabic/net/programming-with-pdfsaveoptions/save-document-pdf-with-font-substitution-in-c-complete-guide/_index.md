---
category: general
date: 2026-06-05
description: احفظ مستند PDF مع استبدال الخطوط باستخدام C#. تعلّم كيفية تغيير خط PDF،
  استبدال خط PDF، والتعامل مع استبدال الخط في PDF باستخدام Aspose.Words.
draft: false
keywords:
- save document pdf
- replace font pdf
- word to pdf font
- change font pdf
- pdf font substitution
language: ar
og_description: احفظ مستند PDF بسرعة وبشكل موثوق. يوضح هذا الدليل كيفية استبدال خط
  PDF، وتغيير خط PDF، وإجراء استبدال خط PDF باستخدام Aspose.Words.
og_title: حفظ مستند PDF مع استبدال الخطوط في C# – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Save document PDF while replacing fonts using C#. Learn how to change
    font PDF, replace font PDF, and handle PDF font substitution with Aspose.Words.
  headline: Save Document PDF with Font Substitution in C# – Complete Guide
  type: TechArticle
tags:
- C#
- Aspose.Words
- PDF
- Font Substitution
title: حفظ مستند PDF مع استبدال الخطوط في C# – دليل كامل
url: /ar/net/programming-with-pdfsaveoptions/save-document-pdf-with-font-substitution-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ مستند PDF مع استبدال الخط في C# – دليل شامل

هل احتجت يوماً إلى **حفظ مستند PDF** من ملف Word لكن الخطوط تظهر بشكل غير صحيح في الـ PDF النهائي؟ لست وحدك—تعارض الخطوط مشكلة شائعة، خاصة عندما لا تكون الخطوط الأصلية مثبتة على الجهاز الهدف.  

الخبر السار هو أنه يمكنك **استبدال الخط pdf** برمجياً، والحفاظ على هوية العلامة التجارية، وتجنب الخطوط الاحتياطية القبيحة. في هذا الدرس سنستعرض مثال عملي يوضح بالضبط كيفية تغيير خط PDF باستخدام Aspose.Words، بالإضافة إلى بعض الحيل الإضافية لاستبدال الخطوط في PDF بشكل موثوق.

## ما يغطيه هذا الدرس

سنبدأ بتحميل مستند Word، ثم نضبط **PdfSaveOptions** بحيث يتم استبدال أي ظهور للخط المصدر (مثلاً *MyFont*) بنسخة متغيرة من الخط (*MyFontVF*). بعد ذلك سنحفظ الملف كـ PDF ونتحقق من أن الاستبدال تم بنجاح. بنهاية الدرس ستكون قادرًا على:

* سير عمل **save document pdf** في C#.
* استخدام إعدادات **replace font pdf** لتعيين الخطوط القديمة إلى الجديدة.
* تحويل **word to pdf font** دون معالجة يدوية لاحقة.
* التعامل مع الحالات التي لا يُعثر فيها على الخط.
* توسيع النهج إلى أزواج خطوط متعددة باستخدام **pdf font substitution**.

بدون أدوات خارجية، فقط بضع أسطر من الكود ومكتبة Aspose.Words.

![مخطط يوضح عملية حفظ مستند PDF مع استبدال الخط](https://example.com/save-pdf-diagram.png "تدفق حفظ مستند PDF")

## المتطلبات المسبقة

* .NET 6.0 أو أحدث (الكود يعمل أيضاً على .NET Framework 4.7+).  
* إشارة إلى **Aspose.Words for .NET** (حزمة NuGet `Aspose.Words`).  
* ملف خط TrueType أو OpenType واحد على الأقل تريد تضمينه (مثال: `MyFontVF.ttf`).  
* ملف Word (`sample.docx`) يستخدم الخط الأصلي الذي تخطط لاستبداله.

إذا كان أي من هذه مفقودًا، احصل على حزمة NuGet عبر:

```bash
dotnet add package Aspose.Words
```

الآن لنبدأ.

## الخطوة 1 – تحميل مستند Word المصدر

أولاً: نحتاج إلى كائن `Document` يمثل ملف Word الذي نريد تحويله. هذه الخطوة هي أساس أي عملية **save document pdf**، لأن باقي خط الأنابيب يعمل على هذا التمثيل في الذاكرة.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Saving;

// Load the .docx you want to convert.
Document doc = new Document(@"C:\Docs\sample.docx");

// Optional sanity check – print how many sections we have.
Console.WriteLine($"Document loaded with {doc.Sections.Count} section(s).");
```

> **لماذا هذا مهم:** تحميل المستند يمنحك الوصول إلى نموذج الكائن الكامل، مما يسمح لك بالتلاعب بالخطوط، الأنماط، أو حتى تخطيط الصفحة قبل أن تقوم أخيراً بـ **save document pdf**.

## الخطوة 2 – إنشاء خيارات حفظ PDF وتمكين استبدال الخط

الآن ننشئ مثيلًا من `PdfSaveOptions`. هذا الكائن يحتوي على كل إعداد يمكن ضبطه عند التصدير إلى PDF، من ضغط الصور إلى مستوى الامتثال. بالنسبة لنا الجزء الحاسم هو خاصية `FontSettings`، التي تتيح لنا تعريف قواعد **replace font pdf**.

```csharp
// Step 2: Create PDF save options.
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();

// Enable font substitution.
pdfSaveOptions.FontSettings = new FontSettings();

// Map the source font ("MyFont") to the target variable‑font ("MyFontVF").
pdfSaveOptions.FontSettings.SubstitutionSettings.FontInfoSubstitutions
    .Add("MyFont", new FontInfo("MyFontVF"));
```

> **شرح:**  
> * `PdfSaveOptions` يخبر Aspose.Words كيف يُنشئ ملف PDF.  
> * `FontSettings.SubstitutionSettings.FontInfoSubstitutions` هو قاموس حيث **المفتاح** هو اسم الخط الذي يظهر في مستند Word، و**القيمة** هي `FontInfo` تشير إلى ملف الخط البديل (أو مجرد اسم العائلة إذا كان الخط موجودًا بالفعل في نظام التشغيل).  
> * بإضافة هذا الإدخال نحقق **pdf font substitution** دون تعديل ملف Word الأصلي.

### نصيحة: التعامل مع استبدالات متعددة

إذا احتجت إلى استبدال عدة خطوط، ما عليك سوى إضافة المزيد من الإدخالات:

```csharp
pdfSaveOptions.FontSettings.SubstitutionSettings.FontInfoSubstitutions
    .Add("OldSans", new FontInfo("NewSans"))
    .Add("OldSerif", new FontInfo("NewSerifVF"));
```

## الخطوة 3 – (اختياري) ضبط إعدادات تضمين الخط بدقة

أحيانًا تريد التأكد من أن الخط البديل مُضمّن فعليًا في PDF. هذا يمنع عارضات PDF من الرجوع إلى خط مختلف.

```csharp
// Ensure the target font is embedded.
pdfSaveOptions.FontEmbeddingMode = FontEmbeddingMode.EmbedAllFonts;

// If you want to embed only the subset that is used, use:
// pdfSaveOptions.FontEmbeddingMode = FontEmbeddingMode.EmbedSubset;
```

> **متى تستخدم ذلك:** إذا كان جمهورك المستهدف قد لا يمتلك الخط البديل مثبتًا، فإن التضمين يضمن مظهرًا ثابتًا—وهو أمر أساسي لتجربة **change font pdf** موثوقة.

## الخطوة 4 – حفظ المستند كـ PDF باستخدام الخيارات المكوّنة

أخيرًا، نستدعي `Document.Save`، مع تمرير مسار الإخراج و`PdfSaveOptions` التي ضبطناها للتو. هذه السطر الواحد يقوم بالعمل الشاق: يرسم تخطيط Word، يطبق خريطة **replace font pdf**، ويكتب ملف PDF إلى القرص.

```csharp
// Step 4: Save the document as a PDF using the options we set.
string outputPath = @"C:\Docs\vf.pdf";
doc.Save(outputPath, pdfSaveOptions);

Console.WriteLine($"PDF saved successfully to {outputPath}");
```

عند فتح `vf.pdf`، أي نص كان يستخدم أصلاً *MyFont* سيظهر الآن بـ *MyFontVF*. قد يكون الفرق بصريًا بسيطًا (إذا كنت تستبدل إلى نسخة متغيرة من الخط) أو واضحًا (إذا استبدلت خطًا زخرفيًا بخط مؤسسي).

## الخطوة 5 – التحقق من النتيجة (ما الذي تبحث عنه)

طريقة سريعة لتأكيد الاستبدال هي فحص قائمة خطوط PDF. معظم عارضات PDF تسمح لك بعرض خصائص المستند؛ يجب أن ترى `MyFontVF` مدرجًا وليس `MyFont`. بدلاً من ذلك، يمكنك استخدام أداة مثل **pdfinfo** (جزء من Poppler) لتفريغ جدول الخطوط:

```bash
pdfinfo -f 1 -l 1 -box vf.pdf | grep Font
```

إذا أظهر الإخراج `Font: MyFontVF`، فقد نجحت في تنفيذ **pdf font substitution**.

## المشكلات الشائعة وكيفية تجنّبها

| المشكلة | السبب | الحل |
|-------|--------|------|
| **الخط غير موجود** | ملف الخط البديل غير موجود في مجلد خطوط النظام ولا يتم توفيره عبر `FontInfo`. | حمّل الخط يدويًا: `FontSettings.FontSources.Add(new FileFontSource(@"C:\Fonts\MyFontVF.ttf"));` |
| **اختفاء النص** | الخط البديل لا يحتوي على بعض الأحرف المستخدمة في المستند الأصلي. | تأكد من أن الخط المستهدف يدعم جميع نطاقات Unicode المطلوبة، أو استخدم تضمين الخط الأصلي كخيار ثانوي. |
| **زيادة حجم PDF** | تضمين الخطوط بالكامل لعائلات كبيرة قد يرفع حجم الملف. | استخدم وضع `EmbedSubset` لتضمين الأحرف المستخدمة فقط. |
| **فقدان التنسيق** | الخط المستبدل لا يدعم وزن الخط الأصلي (مثل الـ bold). | اختر عائلة بديلة تتطابق مع النمط، أو عيّن أوزانًا متعددة بشكل فردي. |

## متقدم: تعيين الخطوط ديناميكيًا بناءً على محتوى المستند

إذا كنت بحاجة إلى استبدال الخطوط فقط عندما يتحقق شرط معين (مثلاً فقط في العناوين)، يمكنك استعراض شجرة المستند وتطبيق `FontSettings` مؤقتًا قبل الحفظ. إليك مثالًا مختصرًا:

```csharp
// Find all runs that use "MyFont" in headings and replace them on the fly.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
    {
        foreach (Run run in para.Runs)
        {
            if (run.Font.Name == "MyFont")
                run.Font.Name = "MyFontVF";
        }
    }
}

// Save as before – no extra substitution needed because we already changed the runs.
doc.Save(outputPath, pdfSaveOptions);
```

> **لماذا تستخدم هذا؟** يمنحك تحكمًا دقيقًا، حيث يمكنك **change font pdf** فقط في سياقات محددة مع ترك باقي المستند دون تعديل.

## ملخص: مثال كامل يعمل

بجمع كل ما سبق، إليك البرنامج الكامل الجاهز للتنفيذ:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source Word document.
        Document doc = new Document(@"C:\Docs\sample.docx");

        // Prepare PDF save options with font substitution.
        PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
        {
            FontSettings = new FontSettings(),
            FontEmbeddingMode = FontEmbeddingMode.EmbedAllFonts // ensure fonts are embedded
        };

        // Map "MyFont" -> "MyFontVF".
        pdfSaveOptions.FontSettings.SubstitutionSettings.FontInfoSubstitutions
            .Add("MyFont", new FontInfo("MyFontVF"));

        // OPTIONAL: Add a custom font folder if the font isn’t installed system‑wide.
        // pdfSaveOptions.FontSettings.FontSources.Add(new FileFontSource(@"C:\Fonts\MyFontVF.ttf"));

        // Save the PDF.
        string outputPath = @"C:\Docs\vf.pdf";
        doc.Save(outputPath, pdfSaveOptions);

        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

شغّل البرنامج، افتح `vf.pdf`، وسترى الخط الجديد مطبقًا في كل مكان كان فيه *MyFont* الأصلي.

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك الخاصة.

- [Save Word as PDF with Aspose.Words – Complete C# Guide](/words/english/net/basic-conversions/save-word-as-pdf-with-aspose-words-complete-c-guide/)
- [Embed Subset Fonts in PDF Document](/words/english/net/programming-with-pdfsaveoptions/embedded-subset-fonts/)
- [Embed Fonts in PDF Document](/words/english/net/programming-with-pdfsaveoptions/embedded-all-fonts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}