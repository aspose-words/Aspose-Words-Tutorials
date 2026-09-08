---
category: general
date: 2026-09-08
description: استرجاع فاصل الحاشية النهائية وعرض فاصل الحاشية السفلية عند تحميل مستند
  Word باستخدام Aspose.Words لـ .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve endnote separator
- load word document
- display footnote separator
- Aspose.Words C#
- footnote and endnote handling
language: ar
lastmod: 2026-09-08
og_description: استرجاع فاصل الحاشية الختامية وعرض فاصل الحاشية السفلية عند تحميل
  مستند Word باستخدام Aspose.Words for .NET.
og_image_alt: Console screenshot showing the footnote separator text printed by a
  C# program
og_title: استرجاع فاصل الحاشية السفلية أثناء تحميل مستند Word في C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Retrieve endnote separator and display footnote separator when you
    load a Word document using Aspose.Words for .NET.
  headline: Retrieve endnote separator while loading a Word document in C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word processing
title: استخراج فاصل الحاشية السفلية أثناء تحميل مستند Word في C#
url: /ar/net/working-with-footnote-and-endnote/retrieve-endnote-separator-while-loading-a-word-document-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استرجاع فاصل الحاشية السفلية (endnote separator) أثناء تحميل مستند Word في C#

إذا كنت بحاجة إلى **استرجاع فاصل الحاشية السفلية** من ملف Word، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. ستتعلم أيضًا كيفية **تحميل مستند Word** باستخدام Aspose.Words و**عرض نص فاصل الحاشية السفلية** في وحدة التحكم، كل ذلك في مثال واحد قابل للتنفيذ.

التعامل مع الحواشي السفلية والحواشي النهائية هو مطلب شائع لتطبيقات القانونية، الأكاديمية، أو النشر. يغطي هذا البرنامج التعليمي كل ما تحتاجه—من فتح الملف إلى معالجة الحالات التي يكون فيها الفاصل مفقودًا—حتى تتمكن من دمج الحل في أي مشروع .NET دون تخمين.

## ما يغطيه هذا البرنامج التعليمي

* كيفية **تحميل مستند Word** باستخدام Aspose.Words API.  
* كيفية **استرجاع فاصل الحاشية السفلية** ولماذا يعتبر الفاصل مهمًا.  
* كيفية **عرض فاصل الحاشية السفلية** على وحدة التحكم لأغراض التصحيح أو التسجيل.  
* معالجة الحالات الحدية عندما لا يحتوي المستند على حواشي سفلية أو حواشي نهائية.  
* عينة كود كاملة جاهزة للنسخ واللصق تعمل على .NET 6 أو أحدث.

### المتطلبات المسبقة

| المتطلب | السبب |
|-------------|--------|
| .NET 6 SDK أو أحدث | يوفر بيئة التشغيل لمثال C#. |
| Aspose.Words for .NET (حزمة NuGet `Aspose.Words`) | المكتبة التي توفر `Document.Footnotes` و `Document.Endnotes`. |
| ملف Word (`Footnotes.docx`) يحتوي على حاشية سفلية أو حاشية نهائية واحدة على الأقل | لتوضيح الفواصل. |
| أي بيئة تطوير متكاملة (Visual Studio, Rider, VS Code) | لتجميع وتشغيل البرنامج. |

> **نصيحة محترف:** إذا لم يكن لديك مستند يحتوي على حواشي سفلية، أنشئ واحدًا سريعًا في Microsoft Word: إدراج → حاشية سفلية → اكتب بعض النص، ثم احفظه باسم `Footnotes.docx`.

## تحميل مستند Word باستخدام Aspose.Words

الخطوة الأولى هي **تحميل مستند Word** إلى الذاكرة. تقوم Aspose.Words بقراءة تنسيق الملف وتكوين نموذج كائن يمكنك الاستعلام عنه.

```csharp
using Aspose.Words;
using System;

class Program
{
    static void Main()
    {
        // Step 1: Load the document containing footnotes and endnotes
        // Adjust the path to point to your local file.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");
```

*لماذا هذا مهم*: تحميل المستند هو الشرط المسبق لأي تعديل لاحق. إذا كان مسار الملف غير صحيح، فإن `Document` يطرح استثناء `FileNotFoundException`، لذا تحقق من المسار قبل التشغيل.

## استرجاع فقرة فاصل الحاشية السفلية

فاصل الحاشية السفلية هو الفقرة التي تفصل بصريًا النص الرئيسي عن قائمة الحواشي السفلية. استرجاعه يتيح لك فحصه أو تعديل تنسيقه.

```csharp
        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.Footnotes.Separator;

        // The separator may be null if the document has no footnotes.
        if (footnoteSeparator != null)
        {
            // Step 3: **display footnote separator** text in the console
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }
```

*لماذا هذا مهم*: **عرض فاصل الحاشية السفلية** يساعدك على التحقق من أن الفقرة الصحيحة تم الوصول إليها، خاصةً عندما تحتاج إلى تطبيق تنسيق مخصص (مثل خط أو خط معين).

## استرجاع فقرة فاصل الحاشية النهائية

الآن ن **نسترجع فاصل الحاشية النهائية**. العملية مشابهة للتعامل مع الحواشي السفلية ولكنها تستخدم مجموعة `Endnotes`.

```csharp
        // Step 4: Retrieve the endnote separator paragraph
        Paragraph endnoteSeparator = doc.Endnotes.Separator;

        // The separator can also be null if there are no endnotes.
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

*لماذا هذا مهم*: خطوة **استرجاع فاصل الحاشية النهائية** أساسية عندما تحتاج إلى تعديل الفاصل البصري بين المحتوى الرئيسي وقائمة الحواشي النهائية—وهو أمر شائع في النشر الأكاديمي حيث تظهر الحواشي النهائية في نهاية الفصل.

### معالجة الفواصل المفقودة

كل من `Footnotes.Separator` و `Endnotes.Separator` يعيدان `null` عندما لا يعرف المستند فاصلًا. تحقق دائمًا من `null` قبل استدعاء `GetText()` لتجنب استثناء `NullReferenceException`. إذا كنت بحاجة إلى فاصل افتراضي، يمكنك إنشاء واحد:

```csharp
if (endnoteSeparator == null)
{
    endnoteSeparator = new Paragraph(doc);
    endnoteSeparator.AppendChild(new Run(doc, "—")); // Simple dash as a separator
    doc.Endnotes.InsertSeparator(endnoteSeparator);
}
```

يقوم هذا الكود بحقن فاصل بسيط بحيث يمكن للمعالجة اللاحقة الاعتماد على وجوده.

## النتيجة المتوقعة في وحدة التحكم

عند تشغيل العينة على مستند يحتوي على حاشية سفلية واحدة وحاشية نهائية واحدة، يجب أن ترى شيئًا مشابهًا لـ:

```
Document loaded successfully.
Footnote separator text: — 
Endnote separator text: — 
```

إذا كان المستند يفتقر إلى حواشي سفلية أو نهائية، سيطبع البرنامج رسائل “غير موجود” المقابلة، مما يُظهر معالجة الأخطاء بأناقة.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه إلى مشروع C# جديد من نوع console. لا يلزم أي كود إضافي.

```csharp
using Aspose.Words;
using System;

class RetrieveSeparatorsDemo
{
    static void Main()
    {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");

        // Retrieve and display the footnote separator
        Paragraph footnoteSeparator = doc.Footnotes.Separator;
        if (footnoteSeparator != null)
        {
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }

        // Retrieve and display the endnote separator
        Paragraph endnoteSeparator = doc.Endnotes.Separator;
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

احفظ الملف باسم `Program.cs`، أضف حزمة Aspose.Words عبر NuGet (`dotnet add package Aspose.Words`)، ثم نفّذ `dotnet run`. سيطبع البرنامج نصوص الفواصل أو يُخبرك إذا كانت مفقودة.

## الاختلافات الشائعة وسيناريوهات “ماذا لو”

| السيناريو | كيفية تعديل الكود |
|----------|-------------------|
| **فواصل مخصصة متعددة** | استخدم `doc.Footnotes.Separator` لاستبدال الفاصل الافتراضي، ثم أضف فقرات فاصل إضافية يدويًا باستخدام `doc.Footnotes.Add(separatorParagraph)`. |
| **تغيير نمط الفاصل** | بعد استرجاع الفاصل، عدّل `ParagraphFormat` الخاص به (مثال: `footnoteSeparator.ParagraphFormat.Alignment = ParagraphAlignment.Center;`). |
| **العمل مع ملفات .doc** | نفس الـ API يعمل؛ فقط تأكد من أن مسار الملف ينتهي بـ `.doc`. |
| **معالجة العديد من المستندات** | ضع عملية التحميل واسترجاع الفواصل داخل حلقة `foreach`؛ أعد استخدام كائن `Document` واحد فقط إذا قمت بإعادة تعيينه بـ `doc = new Document(path)`. |

## قائمة التحقق من أفضل الممارسات

- ✅ **تحقق دائمًا من `null`** قبل الوصول إلى نص الفاصل.  
- ✅ **قم بعملية Trim** للنتيجة المستخرجة من `GetText()` لإزالة أحرف السطر المخفية.  
- ✅ **حرّر (Dispose) كائنات Document الكبيرة** إذا كنت تعالج ملفات متعددة في دفعة (استخدم `using` أو استدعِ `doc.Dispose()`).  
- ✅ **سجّل نص الفاصل** فقط في بيئة التطوير؛ تجنّب عرضه في سجلات الإنتاج إلا إذا كان ذلك مطلوبًا.  

## الخلاصة

أنت الآن تعرف كيف **تسترجع فاصل الحاشية النهائية** أثناء **تحميل مستند Word** وكيف **تعرض فاصل الحاشية السفلية** في تطبيق console على .NET. يوضح المثال الكامل كيفية التحميل، الاستعلام، ومعالجة الفواصل المفقودة بأمان، مما يمنحك أساسًا قويًا لأي مهمة تتعلق بالحواشي السفلية أو النهائية.

الخطوات التالية التي قد تستكشفها:

* **تخصيص تنسيق الحواشي السفلية/النهائية** – تعديل الخطوط، الحدود، أو أنماط الترقيم.  
* **استخراج محتوى الحواشي السفلية/النهائية** – التجول عبر مجموعات `doc.Footnotes` أو `doc.Endnotes`.  
* **حفظ المستند المعدل** – استخدم `doc.Save("output.docx")` لتثبيت التغييرات.

لا تتردد في تجربة ملفات Word مختلفة، أنماط فواصل مختلفة، وميزات Aspose.Words المتنوعة. برمجة ممتعة!

## ماذا يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [How to Load Word Documents Using Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)
- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Create and Style a Word Document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}