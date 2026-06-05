---
category: general
date: 2026-06-05
description: تكوين خيارات تحميل المستند في C# لمعالجة تحذيرات استبدال الخطوط وتخصيص
  سلوك التحميل باستخدام رد نداء التحذير.
draft: false
keywords:
- configure document load options
- warning callback
- font substitution warning
- LoadOptions usage
- Aspose.Words document loading
- C# document loading options
language: ar
og_description: قم بتكوين خيارات تحميل المستند في C# لإدارة تحذيرات استبدال الخطوط
  وضبط تحميل المستند بدقة باستخدام رد نداء التحذير.
og_title: تكوين خيارات تحميل المستند في C# – دليل شامل
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  headline: Configure document load options in C# – Complete Guide
  type: TechArticle
- description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  name: Configure document load options in C# – Complete Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works with .NET Framework 4.6+ as well).
      - Aspose.Words for .NET installed (`dotnet add package Aspose.Words`). - Basic
      familiarity with C# syntax.'
  - name: Implement a Warning Callback for Font Substitution
    text: First things first—what’s a **warning callback**? In Aspose.Words it’s a
      delegate that gets invoked whenever the library encounters something worth flagging,
      like a missing font. By catching `WarningType.FontSubstitution` we can log the
      exact font the engine swapped out.
  - name: Set Up LoadOptions with the Callback
    text: Now that we have a callback, we need to **configure document load options**
      to actually use it. `LoadOptions` is a lightweight container that tells Aspose.Words
      how to behave during the `Document` constructor call.
  - name: Load the Document Using the Configured Options
    text: With the callback wired up, the final act is to actually **load the document**.
      The `Document` constructor accepts a file path and the `LoadOptions` we just
      prepared.
  - name: Optional – Verify Loaded Fonts (Edge Case Handling)
    text: Sometimes you might want to *pre‑validate* the document before loading it
      fully, especially in batch processing scenarios. Aspose.Words offers the `FontSettings`
      class that can enumerate required fonts.
  - name: What if the warning callback throws an exception?
    text: The callback runs on the same thread that loads the document. Throwing inside
      the delegate will abort the load and propagate the exception. Wrap your logic
      in a `try/catch` if you need resilience.
  - name: Can I suppress *all* warnings instead of handling them?
    text: Yes—set `loadOptions.WarningCallback = null;` or provide a callback that
      does nothing. Be aware you’ll lose visibility into potential problems.
  - name: Does this work with encrypted DOCX files?
    text: Absolutely. Just add `Password = "yourPassword"` to `LoadOptions` before
      creating the `Document`. The warning callback will still fire for font issues.
  - name: How does this differ from using `DocumentBuilder`?
    text: '`DocumentBuilder` is for *creating* or *modifying* a document after it’s
      loaded. **Configure document load options** influences the *initial* parsing
      stage, which is where font substitution decisions are made.'
  type: HowTo
tags:
- C#
- Aspose.Words
- LoadOptions
- DocumentProcessing
title: تكوين خيارات تحميل المستند في C# – دليل كامل
url: /ar/net/programming-with-loadoptions/configure-document-load-options-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تكوين خيارات تحميل المستند في C# – دليل شامل

هل احتجت يوماً إلى **تكوين خيارات تحميل المستند** في C# لأن سلوك التحميل الافتراضي لم يكن كافياً؟ ربما ترى استبدالات خطوط غير متوقعة أو تريد تسجيل كل تحذير يظهر أثناء استيراد ملف. في هذا الدرس سنستعرض حلاً عملياً من البداية إلى النهاية لا يقتصر فقط على إعداد تلك الخيارات بل يُظهر أيضاً **دالة رد نداء التحذير** لتحذيرات استبدال الخطوط.

سنغطي كل شيء بدءاً من المقتطف الصغير الذي ينشئ رد نداء التحذير وحتى لحظة فتح المستند بإعداداتك المخصصة. في النهاية ستحصل على نمط قابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع Aspose.Words، سواء كنت تعالج الفواتير أو العقود القانونية أو التقارير البسيطة.

## ما ستتعلمه

- كيفية **تكوين خيارات تحميل المستند** باستخدام `LoadOptions`.
- كيفية تنفيذ **دالة رد نداء التحذير** التي تلتقط تنبيهات `FontSubstitution`.
- لماذا يمكن أن يوفر التعامل المبكر مع **تحذير استبدال الخط** مفاجآت تخطيطية غير مرغوبة.
- معالجة الحالات الطرفية للخطوط المفقودة وكيفية الانتقال إلى بديل بشكل سلس.
- عينة شفرة كاملة جاهزة للنسخ واللصق يمكنك تشغيلها اليوم.

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (تعمل الشفرة أيضاً مع .NET Framework 4.6+).
- تثبيت Aspose.Words for .NET (`dotnet add package Aspose.Words`).
- إلمام أساسي بصياغة C#.

إذا كان لديك هذه المتطلبات، فلنبدأ.

## تكوين خيارات تحميل المستند – خطوة بخطوة

فيما يلي سير العمل الكامل مقسَّم إلى أربع خطوات واضحة. يتم شرح كل خطوة، ثم يتبعها مقتطف شفرة مختصر يمكنك لصقه مباشرة في Visual Studio.

### الخطوة 1: تنفيذ رد نداء التحذير لاستبدال الخطوط

أولاً، ما هو **رد نداء التحذير**؟ في Aspose.Words هو مُفوض (delegate) يتم استدعاؤه كلما صادفت المكتبة شيئاً يستحق الإشارة إليه، مثل خط مفقود. من خلال التقاط `WarningType.FontSubstitution` يمكننا تسجيل الخط المحدد الذي استبدلته المحرك.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Define a warning callback that reports font substitution warnings
var fontWarningCallback = new IWarningCallback(
    warningInfo =>
    {
        // Check if the warning is about font substitution
        if (warningInfo.WarningType == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or telemetry system
            Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
        }
    });
```

**لماذا هذا مهم:** بدون رد نداء، تقوم المكتبة باستبدال الخطوط المفقودة صامتاً، مما قد يؤدي إلى نص مشوّه في ملف PDF أو DOCX النهائي. من خلال إظهار التحذير تحصل على رؤية واضحة ويمكنك اتخاذ قرار بإدراج الخط المفقود، أو الانتقال إلى بديل، أو تنبيه المستخدم.

> **نصيحة احترافية:** إذا أردت التقاط *جميع* التحذيرات، احذف شرط `if`. سجِّل `warningInfo.Description` لكل حدث.

### الخطوة 2: إعداد LoadOptions مع رد نداء التحذير

الآن بعد أن أنشأنا رد نداء، نحتاج إلى **تكوين خيارات تحميل المستند** لاستخدامه فعلياً. `LoadOptions` هو حاوية خفيفة الوزن تخبر Aspose.Words كيف تتصرف أثناء استدعاء مُنشئ `Document`.

```csharp
// Step 2: Attach the callback to the LoadOptions object
var loadOptions = new LoadOptions
{
    WarningCallback = fontWarningCallback,
    // Optional: enforce strict loading mode (throws on any warning)
    // LoadFormat = LoadFormat.Docx,
    // LoadOptions.LoadFormat can be left null to auto-detect based on file extension
};
```

**لماذا هذا مهم:** من خلال تعيين `WarningCallback`، يتم توجيه كل تحذير يُصدر خلال مرحلة التحميل إلى المُفوض الخاص بنا. يمكنك أيضاً تعديل خصائص `LoadOptions` الأخرى هنا—مثل `LoadFormat` إذا كنت تعرف نوع الملف بدقة، أو `Password` للمستندات المشفرة.

### الخطوة 3: تحميل المستند باستخدام الخيارات المُكوَّنة

مع ربط رد نداء التحذير، الخطوة الأخيرة هي **تحميل المستند** فعلياً. مُنشئ `Document` يقبل مسار الملف و`LoadOptions` التي أعددناها للتو.

```csharp
// Step 3: Load the document with our custom options
string inputPath = @"C:\Docs\input.docx";   // Adjust to your environment
Document doc = new Document(inputPath, loadOptions);
```

إذا كان الملف المصدر يشير إلى خط غير مثبت على الجهاز، ستظهر لك سطر مشابه لـ:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

في وحدة التحكم. هذه الملاحظة الفورية تسمح لك باتخاذ قرار إما بنشر الخط المفقود مع تطبيقك أو استبداله برمجياً.

### الخطوة 4: اختياري – التحقق من الخطوط المحمَّلة (معالجة الحالات الطرفية)

أحياناً قد ترغب في *التحقق المسبق* من المستند قبل تحميله بالكامل، خاصةً في سيناريوهات المعالجة الدفعية. توفر Aspose.Words الفئة `FontSettings` التي يمكنها تعداد الخطوط المطلوبة.

```csharp
// Optional: Check required fonts before full load
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
loadOptions.FontSettings = fontSettings;

// Re-load the document now that we have a custom font folder
Document docWithCustomFonts = new Document(inputPath, loadOptions);
```

**متى تستخدم هذا:** إذا كنت تحتفظ بمستودع خطوط خاص (مثلاً خطوط العلامة التجارية للشركة)، فإن توجيه `FontSettings` إلى ذلك المجلد يضمن أن المحرك يجد الخطوط الصحيحة دون اللجوء إلى الخطوط العامة.

## مثال كامل يعمل

فيما يلي البرنامج بالكامل—انسخه، الصقه، وشغّله. يوضح كل شيء من إنشاء رد نداء التحذير إلى تحميل المستند النهائي.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // 1️⃣ Define the warning callback
        var fontWarningCallback = new IWarningCallback(
            warningInfo =>
            {
                if (warningInfo.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
                }
            });

        // 2️⃣ Configure LoadOptions with the callback
        var loadOptions = new LoadOptions
        {
            WarningCallback = fontWarningCallback,
            // Uncomment the next line to point to a custom font folder
            // FontSettings = new FontSettings { SetFontsFolder(@"C:\MyFonts", true) }
        };

        // 3️⃣ Load the document using the custom options
        string inputFile = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputFile, loadOptions);

        // 4️⃣ (Optional) Save as PDF to verify everything works
        string outputFile = @"YOUR_DIRECTORY/output.pdf";
        doc.Save(outputFile);
        Console.WriteLine($"Document loaded and saved to {outputFile}");
    }
}
```

**الناتج المتوقع**

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Document loaded and saved to C:\Your\Path\output.pdf
```

إذا لم توجد خطوط مفقودة، يبقى رد نداء التحذير صامتاً—لا شيء يدعو للقلق.

## أسئلة شائعة وحالات طرفية

### ماذا لو رمى رد نداء التحذير استثناءً؟

يعمل رد نداء التحذير على نفس الخيط الذي يحمل المستند. إذا تم رمي استثناء داخل المفوض، سيتوقف التحميل وتنتقل الاستثناءات إلى الخارج. احرص على تغليف المنطق بـ `try/catch` إذا كنت تحتاج إلى مرونة أكبر.

### هل يمكنني قمع *جميع* التحذيرات بدلاً من معالجتها؟

نعم—عيّن `loadOptions.WarningCallback = null;` أو قدم رد نداء لا يفعل شيئاً. لكن احذر، فستفقد الرؤية على المشكلات المحتملة.

### هل يعمل هذا مع ملفات DOCX المشفرة؟

بالطبع. فقط أضف `Password = "yourPassword"` إلى `LoadOptions` قبل إنشاء `Document`. سيظل رد نداء التحذير يُستدعى لمشكلات الخطوط.

### كيف يختلف هذا عن استخدام `DocumentBuilder`؟

`DocumentBuilder` يُستخدم *لإنشاء* أو *تعديل* مستند بعد تحميله. **تكوين خيارات تحميل المستند** يؤثر على مرحلة التحليل *الأولية*، حيث تُتخذ قرارات استبدال الخطوط.

## نظرة بصرية

![مخطط يوضح تدفق تكوين خيارات تحميل المستند](https://example.com/images/load-options-flow.png "مخطط يوضح تدفق تكوين خيارات تحميل المستند")

*الصورة توضح التدفق: رد نداء → LoadOptions → مُنشئ Document → معالجة التحذير.*

## الخلاصة

أنت الآن تعرف كيفية **تكوين خيارات تحميل المستند** في C# لالتقاط تحذيرات استبدال الخطوط، وإدخال مجلدات خطوط مخصصة، والحفاظ على سيطرة كاملة على عملية التحميل. يمنحك هذا النمط الثقة بأن كل خط مفقود سيتم الإبلاغ عنه، مما يسمح لك بالحفاظ على دقة المستند عبر أي بيئة.

ما الخطوة التالية؟ جرّب استبدال تسجيل وحدة التحكم بنظام تتبع أكثر قوة، أو دمج هذا النهج مع `DocumentBuilder` لاستبدال الخطوط المفقودة تلقائياً بخط افتراضي للشركة. يمكنك أيضاً استكشاف قيم `WarningType` أخرى مثل `DocumentStructure` للحصول على رؤى أعمق.

برمجة سعيدة، ولتظهر مستنداتك دائماً كما تريد!

## ماذا يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Master Aspose.Words Markdown Load Options in Python for Enhanced Document Processing](/words/english/python-net/document-operations/aspose-words-markdown-load-options-python/)
- [Optimizing Document Loading with HTML, RTF, and TXT Options](/words/english/java/word-processing/optimizing-document-loading-options/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}