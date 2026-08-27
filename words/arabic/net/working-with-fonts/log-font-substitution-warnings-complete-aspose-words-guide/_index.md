---
category: general
date: 2026-01-14
description: سجّل تحذيرات استبدال الخطوط أثناء تحميل مستندات Word باستخدام Aspose.Words.
  تعلّم كيفية اكتشاف الخطوط المفقودة وكيفية التقاط الخطوط المفقودة في C#.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: ar
og_description: سجّل تحذيرات استبدال الخطوط أثناء تحميل مستندات Word باستخدام Aspose.Words.
  اكتشف كيفية اكتشاف الخطوط المفقودة وتسجيل الخطوط المفقودة في C#.
og_title: سجل تحذيرات استبدال الخط – دليل Aspose.Words الكامل
tags:
- Aspose.Words
- C#
- Document Processing
title: تحذيرات استبدال الخط في السجل – دليل Aspose.Words الكامل
url: /ar/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحذيرات استبدال الخطوط – دليل Aspose.Words الكامل

تسجيل تحذيرات استبدال الخطوط أمر أساسي عندما تحتاج إلى ضمان أن مستند Word سيظهر بنفس الشكل تمامًا بعد تحميله بواسطة Aspose.Words. إذا تساءلت يومًا عن **كيفية اكتشاف الخطوط المفقودة** أو أردت معرفة **كيفية التقاط الخطوط المفقودة**، فأنت في المكان الصحيح.  

في هذا البرنامج التعليمي سنستعرض سيناريو واقعي، نعرض لك الكود الكامل بلغة C#، ونشرح لماذا كل سطر مهم. في النهاية ستتمكن من تسجيل كل حدث استبدال خط واتخاذ الإجراء المناسب—لن يبقى أي تحذير غامض.

![مثال على تحذيرات استبدال الخطوط](/images/font-warnings.png "لقطة شاشة تُظهر مخرجات وحدة التحكم لتسجيل تحذيرات استبدال الخطوط")

## ما ستتعلمه

- كيفية تكوين `LoadOptions` بحيث تقوم Aspose.Words بإصدار تحذيرات مكتوبة لأنواع استبدال الخطوط.  
- الخطوات الدقيقة **لاكتشاف الخطوط المفقودة** أثناء تحميل المستند.  
- طريقة نظيفة **لالتقاط الخطوط المفقودة** وكتابتها إلى سجل خاص أو نظام مراقبة.  
- معالجة الحالات الخاصة (مثل عندما يحتوي المستند على خط غير مثبت على الخادم).  

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.6+).  
- ترخيص صالح لـ Aspose.Words for .NET (أو النسخة التجريبية المجانية).  
- إلمام أساسي بـ C# وتطبيقات وحدة التحكم.  

إذا كان لديك كل ذلك، فلنبدأ.

## الخطوة 1 – إعداد LoadOptions لإصدار تحذيرات مكتوبة

جوهر الحل يكمن في `LoadOptions.FontSubstitutionWarning`. بتحويله إلى `RaiseTypedWarnings` تخبر Aspose.Words بإطلاق حدث **في كل مرة** لا يمكنه العثور على الخط المحدد الذي طلبته.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **لماذا هذا مهم:**  
> السلوك الافتراضي يستبدل الخط المفقود بصمت بأقرب تطابق، ما قد يؤدي إلى تشوهات في التخطيط لا تلاحظها. إصدار التحذيرات المكتوبة يمنحك رؤية كاملة.

## الخطوة 2 – الاشتراك في حدث التحذير

الآن نقوم بربط `loadOptions.FontSubstitutionWarning`. تستقبل الدالة اللامبدا كائن `e` يخبرنا بالخط المفقود بالضبط وأي خط تم استخدامه كبديل.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **نصيحة احترافية:** إذا كنت تشغل هذا على خادم ويب، استبدل `Console.WriteLine` بمسجل منظم (Serilog، NLog، إلخ) حتى تتمكن من الاستعلام عن البيانات لاحقًا.

## الخطوة 3 – تحميل المستند باستخدام الخيارات المكوَّنة

مع وجود آلية التحذير، قم بتحميل المستند كالمعتاد. سيُطلق الحدث تلقائيًا لكل خط مفقود.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### مخرجات وحدة التحكم المتوقعة

إذا كان `input.docx` يشير إلى خط يُدعى *MyFancyFont* غير مثبت، سترى:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

كل سطر يمثل حدث **اكتشاف الخطوط المفقودة**، مما يمنحك سجلًا كاملاً.

## الخطوة 4 – معالجة الحالات الخاصة والسيناريوهات المتقدمة

### 4.1 عندما لا يحدث استبدال

أحيانًا يستخدم المستند خطوط نظام موجودة بالفعل. في هذه الحالة لا يُطلق حدث التحذير، وستحصل على وحدة تحكم نظيفة بدون مخرجات. هذا مؤشر جيد—بيئتك تحتوي بالفعل على جميع الخطوط المطلوبة.

### 4.2 التقاط التحذيرات للتحليل لاحقًا

إذا كنت بحاجة لتخزين التحذيرات لتقرير ليلي، اجمعها في قائمة:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

بعد التحميل، يمكنك تسلسل `missingFonts` إلى JSON، أو كتابتها إلى قاعدة بيانات، أو إرسال ملخص بالبريد الإلكتروني.

### 4.3 العمل مع ملفات PDF أو صيغ أخرى

نفس نهج `LoadOptions` يعمل مع استدعاءات `Load` لملفات PDF، RTF، وحتى HTML. ما عليك سوى تمرير نفس كائن الخيارات، وستصدر Aspose.Words تحذيرات لأي خط لا يمكنها مطابقته.

## الخطوة 5 – التحقق من النتيجة برمجيًا

إذا كنت تفضّل اختبارًا آليًا بدلاً من مراقبة وحدة التحكم بالعين، تحقق من أن القائمة تحتوي على الإدخالات المتوقعة:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

هذا المقتطف يوضح **كيفية التقاط الخطوط المفقودة** في الكود، وليس فقط في السجلات.

## الأخطاء الشائعة وكيفية تجنّبها

| الخطأ | السبب | الحل |
|-------|--------|------|
| نسيان ضبط `RaiseTypedWarnings` | الإعداد الافتراضي هو `DoNotRaise`، لذا لا تُطلق أي أحداث. | اضبط `FontSubstitutionWarning` صراحةً كما هو موضح في الخطوة 1. |
| استخدام `Console.WriteLine` في تطبيق ويب | مخرجات وحدة التحكم تختفي في IIS/ASP.NET Core. | استبدلها بمسجل دائم (مثل Serilog). |
| تحميل مستند بمسار نسبي | قد يختلف دليل العمل أثناء التشغيل. | استخدم مسارات مطلقة أو `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| تجاهل `SubstitutedFontName` | تفقد الرؤية حول أي خط بديل تم اختياره. | دوّن دائمًا كل من `FontName` و `SubstitutedFontName`. |

## مكافأة: أتمتة تثبيت الخطوط

إذا كنت تتحكم في بيئة النشر، يمكنك تثبيت الخطوط المفقودة مسبقًا باستخدام سكريبت PowerShell:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

تشغيل هذا قبل بدء تطبيقك يزيل معظم تحذيرات **اكتشاف الخطوط المفقودة** تمامًا.

## الخلاصة

غطّينا كل ما تحتاجه لتسجيل **تحذيرات استبدال الخطوط** عند تحميل مستندات Word باستخدام Aspose.Words. من خلال تكوين `LoadOptions`، الاشتراك في حدث التحذير، وربما حفظ النتائج، يمكنك اكتشاف الخطوط المفقودة وفهم **كيفية التقاط الخطوط المفقودة** لأي مشروع .NET.

خذ الكود، عدّل المسجل ليناسب بنية مشروعك، ولن تُفاجئ مرة أخرى باستبدال خط صامت. الخطوات التالية قد تشمل:

- دمج قائمة التحذيرات مع خط أنابيب CI/CD لإيقاف البناء عندما تكون الخطوط الحرجة مفقودة.  
- توسيع النهج لمراقبة استخدام الخطوط عبر مجموعة مستندات.  
- استكشاف API `FontSettings` في Aspose.Words لتوفير خطوط بديلة مخصصة.

هل لديك أسئلة أو سيناريو معقد؟ اترك تعليقًا، وسنحل المشكلة معًا. برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}