---
category: general
date: 2025-12-29
description: تتيح لك خيارات التحميل في Aspose تحميل ملفات DOCX مع تخصيص إعدادات الخطوط
  واكتشاف الخطوط المفقودة. تعرّف على كيفية تحميل ملفات docx مع تحكم كامل.
draft: false
keywords:
- aspose load options
- how to load docx
- custom font settings
- load word document
- detect missing fonts
language: ar
og_description: خيارات التحميل من Aspose تتيح لك تحميل ملفات DOCX مع تخصيص إعدادات
  الخط واكتشاف الخطوط المفقودة. تعرّف على كيفية تحميل ملفات docx مع التحكم الكامل.
og_title: خيارات التحميل في Aspose – تحميل ملف DOCX مع إعدادات الخط المخصصة
tags:
- Aspose.Words
- C#
- Document Processing
title: خيارات التحميل في Aspose – تحميل DOCX مع إعدادات الخط المخصصة
url: /ar/net/programming-with-loadoptions/aspose-load-options-load-docx-with-custom-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# خيارات التحميل في Aspose – تحميل DOCX بإعدادات خطوط مخصصة

هل تساءلت يوماً كيف يمكنك تحميل ملف DOCX في C# دون الوقوع في مشكلة الخطوط المفقودة؟ لست وحدك. **خيارات التحميل في Aspose** تمنحك القدرة على التحكم تماماً في طريقة فتح مستند Word، مما يتيح لك ضبط إعدادات خطوط مخصصة وحتى اكتشاف الخطوط المفقودة قبل أن تصبح مشكلة.

في هذا الدرس سنستعرض العملية الكاملة لتحميل DOCX باستخدام Aspose.Words، وتكوين **إعدادات خطوط مخصصة**، وربط رد نداء تحذيري يُخبرك بالخطوط المفقودة. في النهاية ستتمكن من **تحميل مستندات Word** بثقة، بغض النظر عن الخطوط التي استخدمها المؤلف الأصلي.

> **المتطلبات المسبقة** – تحتاج إلى Aspose.Words for .NET (أحدث نسخة) مضافة إلى مشروعك ومعرفة أساسية بـ C#. لا توجد مكتبات أخرى مطلوبة.

## ما ستتعلمه

- كيفية إنشاء كائن `LoadOptions` وإرفاق رد نداء تحذيري.  
- كيفية إعداد `FontSettings` لـ **إعدادات خطوط مخصصة**.  
- كيفية **تحميل docx** والتحقق من أن الخطوط المفقودة يتم الإبلاغ عنها.  
- نصائح للتعامل مع الحالات الخاصة مثل الخطوط المدمجة أو مجلدات الخطوط على الشبكة.

## الخطوة 1: تثبيت Aspose.Words وتحضير المشروع

أولاً، تأكد من تثبيت Aspose.Words. أسهل طريقة هي عبر NuGet:

```bash
dotnet add package Aspose.Words
```

بعد إضافة الحزمة، أنشئ مشروع console جديد بلغة C# (أو ضع الكود في أي تطبيق موجود). الكود الذي سنكتبه يعمل مع .NET 6+ و .NET Framework 4.7.2+، لذا أنت مغطى في كلا الحالتين.

> **نصيحة احترافية:** إذا كنت تستهدف .NET Core، أضف `using System;` في أعلى الملف؛ عادةً ما يقوم IDE بإدراجه تلقائياً.

## الخطوة 2: تكوين خيارات تحميل Aspose مع رد نداء تحذيري

الآن نصل إلى جوهر الموضوع—**خيارات تحميل Aspose**. تسمح لك فئة `LoadOptions` بتعديل طريقة تحليل المستند. سنستخدمها لـ:

1. إرفاق رد نداء يُفعل كلما تعذر على المحمل العثور على خط مطلوب.  
2. تعيين كائن `FontSettings` يمكن تعديل إعداداته لاحقاً لـ **إعدادات خطوط مخصصة**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Step 2.1 – Create LoadOptions and a FontSettings object
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // FontSettings is where you control where Aspose looks for fonts.
        // You could point it at a folder, a collection, or even a stream.
        FontSettings fontSettings = new FontSettings();

        // --------------------------------------------------------------
        // Step 2.2 – Register a warning callback to detect missing fonts
        // --------------------------------------------------------------
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            // This will be called for each missing font.
            // args.FontInfo can be null, so we guard against it.
            string missingFont = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missingFont}");
        };

        // Attach the FontSettings to the LoadOptions.
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Step 2.3 – (Optional) Add a custom font folder
        // --------------------------------------------------------------
        // If you have a folder with corporate fonts, tell Aspose to use it.
        // Replace "C:\\MyFonts" with the actual path on your machine.
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
```

**لماذا هذا مهم:** بدون رد نداء تحذيري، يقوم Aspose باستبدال الخطوط المفقودة صامتاً، مما قد يسبب مفاجآت في التخطيط لاحقاً. عبر ربط رد النداء، يمكنك **اكتشاف الخطوط المفقودة** مبكراً وتقرر ما إذا كنت ستضمّن بديلًا أو تطلب من المستخدم تثبيت الخط المفقود.

## الخطوة 3: تحميل DOCX باستخدام الخيارات المكوَّنة

مع إعداد `LoadOptions` جاهز، يصبح تحميل DOCX سطرًا واحدًا. يقبل مُنشئ `Document` مسار الملف والخيارات التي بنيناها.

```csharp
        // --------------------------------------------------------------
        // Step 3 – Load the DOCX file while respecting our custom settings
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";

        // The Document constructor will invoke the warning callback
        // for any font it cannot resolve.
        Document doc = new Document(inputPath, loadOptions);

        Console.WriteLine("Document loaded successfully.");
```

إذا كان الملف المصدر يشير إلى خط غير موجود على النظام أو في المجلد المخصص، ستظهر لك مخرجات مثل:

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
```

هذا الرد الفوري لا يقدر بثمن عندما تبني خط أنابيب معالجة دفعات يجب أن يضمن الحفاظ على الدقة البصرية.

## الخطوة 4: التحقق من المستند المحمَّل (اختياري لكن مفيد)

بعد التحميل، قد ترغب في التأكد من أن محتويات المستند قابلة للوصول. للتحقق السريع، دعنا نطبع نص الفقرة الأولى.

```csharp
        // --------------------------------------------------------------
        // Step 4 – Quick sanity check: print the first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");
    }
}
```

تشغيل البرنامج الآن يعطيك:

```
[Warning] Missing font: Times New Roman
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

## الخطوة 5: الحالات الخاصة والنصائح المتقدمة

### 5.1 التعامل مع الخطوط المدمجة

بعض ملفات DOCX تدمج الخطوط المطلوبة مباشرة. يستخدم Aspose.Words هذه الخطوط تلقائيًا، لذا لن ترى تحذيرات بشأنها. ومع ذلك، إذا قمت عمدًا **بتحميل مستندات Word** التي تُزيل الخطوط المدمجة (مثلاً بعد تحويل)، قد تحتاج إلى توفير الخطوط المفقودة عبر `SetFontsFolder` كما هو موضح سابقًا.

### 5.2 استخدام Memory Stream بدلاً من مسار ملف

إذا كان DOCX موجودًا في قاعدة بيانات أو يأتي من طلب HTTP، يمكنك تحميله من `MemoryStream`:

```csharp
using (var stream = new MemoryStream(byteArrayFromDb))
{
    Document docFromStream = new Document(stream, loadOptions);
    // Continue processing...
}
```

تنطبق نفس **خيارات تحميل Aspose**، ولا يزال رد النداء التحذيري يعمل.

### 5.3 تجاوز استبدال الخطوط عالميًا

إذا رغبت في استبدال الخطوط المفقودة بخط بديل محدد (مثلاً Arial)، يمكنك إضافة قاعدة استبدال:

```csharp
fontSettings.SubstitutionSettings.FontSubstitution.AddSubstitutes("MissingFontName", new[] { "Arial" });
```

اجمع ذلك مع رد نداء التحذير لتسجيل حدث الاستبدال والحفاظ على اتساق المخرجات.

## الخطوة 6: مثال كامل يعمل

فيما يلي البرنامج الكامل جاهز للنسخ واللصق الذي يدمج جميع الخطوات السابقة. احفظه كـ `Program.cs`، استعد حزم NuGet، ثم شغّله.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Create LoadOptions with custom font settings and warning callback
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        FontSettings fontSettings = new FontSettings();

        // Warn about missing fonts
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            string missing = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missing}");
        };

        // Optional: point to a folder with corporate fonts
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

        // Attach settings to load options
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Load the DOCX file
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";
        Document doc = new Document(inputPath, loadOptions);
        Console.WriteLine("Document loaded successfully.");

        // --------------------------------------------------------------
        // Quick sanity check – print first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");

        // --------------------------------------------------------------
        // (Optional) Demonstrate loading from a stream
        // --------------------------------------------------------------
        // byte[] bytes = File.ReadAllBytes(inputPath);
        // using var ms = new MemoryStream(bytes);
        // Document docFromStream = new Document(ms, loadOptions);
        // Console.WriteLine("Loaded from stream.");
    }
}
```

### المخرجات المتوقعة

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

إذا لم تكن هناك خطوط مفقودة، لن تظهر سطور التحذير.

## نظرة بصرية عامة

![مثال خيارات تحميل Aspose](/images/aspose-load-options.png "مخطط يوضح سير عمل خيارات تحميل Aspose")

*المخطط يوضح كيف أن **خيارات تحميل Aspose** تقع بين مصدر الملف وكائن `Document`، مع معالجة حل الخطوط واكتشاف الخطوط المفقودة.*

## الخاتمة

استعرضنا حلًا كاملاً لـ **خيارات تحميل Aspose**، موضحين لك بالضبط **كيفية تحميل docx** مع تطبيق **إعدادات خطوط مخصصة** و**اكتشاف الخطوط المفقودة**. عبر تكوين رد نداء تحذيري وإشارة Aspose إلى مجلد خطوط مخصص، تحصل على رؤية كاملة لمشكلات الخطوط قبل أن تؤثر على العرض.

من هنا يمكنك استكشاف مواضيع ذات صلة مثل **تحويل مستند Word إلى PDF**، إضافة علامات مائية، أو معالجة دفعات من الملفات في مجلد. النمط نفسه—إنشاء `LoadOptions`، إرفاق ردود نداء، ثم استدعاء `new Document(...)`—يعمل عبر كامل API الخاص بـ Aspose.Words.

هل لديك أسئلة حول حالة خاصة، مثل التعامل مع اللغات من اليمين إلى اليسار أو ملفات DOCX المشفرة؟ اترك تعليقًا أو راجع وثائق Aspose.Words للمزيد من التفاصيل. برمجة سعيدة، ولتظهر مستنداتك دائمًا كما هو مقصود!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}