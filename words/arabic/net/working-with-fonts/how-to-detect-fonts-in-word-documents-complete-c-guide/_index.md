---
category: general
date: 2026-02-24
description: كيفية اكتشاف الخطوط في مستند Word باستخدام Aspose.Words. تعلّم كيفية
  تعيين رد النداء وتحميل مستند Word مع مثال كامل للكود.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: ar
og_description: كيفية اكتشاف الخطوط في مستند Word باستخدام رد نداء تحذيري. يوضح هذا
  الدليل كيفية تعيين رد النداء وتحميل مستند Word باستخدام Aspose.Words.
og_title: كيفية اكتشاف الخطوط في مستندات Word – دليل C# خطوة بخطوة
tags:
- C#
- Aspose.Words
- Document Processing
title: كيفية اكتشاف الخطوط في مستندات Word – دليل C# الكامل
url: /ar/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

Proceed through sections.

Make sure to keep code block placeholders unchanged.

Also keep markdown links unchanged.

There are no markdown links in content except maybe none.

Proceed.

Now produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية اكتشاف الخطوط في مستندات Word – دليل C# كامل

هل تساءلت يومًا **how to detect fonts** التي تكون مفقودة عند تحميل ملف Word؟ ربما صادفت مستندًا يبدو جيدًا في المحرر، لكن ملف PDF الذي تولده يستبدل بعض الخطوط خلف الكواليس. هذا عرض كلاسيكي لظاهرة استبدال الخطوط، واكتشافه مبكرًا يمكن أن يوفر عليك مفاجآت تخطيطية غير مرغوب فيها.

في هذا الدرس سنستعرض حلًا عمليًا: استخدام **Aspose.Words** لتحميل ملف `.docx`، إرفاق رد نداء تحذيري، و**how to set callback** الذي يُبلغ عن كل استبدال للخط. في النهاية لن تعرف فقط **how to detect fonts** برمجيًا، بل ستفهم أيضًا **how to set callback** بشكل صحيح و**load word document** بأمان—كل ذلك في مثال C# واحد قابل للتنفيذ.

> **ما ستحصل عليه**
> * عينة كود جاهزة للنسخ واللصق  
> * شرح خطوة بخطوة لكل سطر  
> * نصائح للتعامل مع الحالات الخاصة مثل وجود عدة خطوط مفقودة أو مجلدات خطوط مخصصة  
> * ناتج متوقع في وحدة التحكم لتتمكن من التحقق من عمل كل شيء

---

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Core)  
- حزمة NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)  
- ملف Word يحتوي عمدًا على إشارة إلى خط غير مثبت لديك (مثل `MissingFont.docx`)  
- Visual Studio، Rider، أو أي محرر تفضله

لا توجد مكتبات أخرى مطلوبة؛ كل ما تبقى هو جزء من بيئة تشغيل .NET القياسية.

---

## كيفية اكتشاف الخطوط في مستند Word

### الخطوة 1: إنشاء Load Options وإرفاق رد نداء تحذيري

أول ما نفعله هو إخبار Aspose.Words أننا نريد أن يتم إعلامنا بأي مشاكل قد تظهر أثناء تحميل الملف. هنا يأتي دور **how to set callback**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**لماذا هذا مهم:**  
`LoadOptions` هو البوابة لتخصيص عملية التحميل. من خلال تعيين نسخة من `FontWarningCollector` إلى `WarningCallback`، سيستدعي Aspose.Words طريقة `Warning` في كل مرة يستبدل فيها خط مفقود بخط بديل. هذا هو جوهر **how to detect fonts** التي لا تتوفر على الجهاز.

---

### الخطوة 2: إعداد كائن LoadOptions

الآن نقوم بإنشاء `LoadOptions` وربط رد النداء الخاص بنا.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**نصيحة احترافية:** إذا كنت بحاجة للتحكم في *مكان* بحث Aspose عن الخطوط البديلة، يمكنك أيضًا تعيين `loadOptions.FontSettings` هنا. هذا مفيد عندما يكون لديك مجلد خطوط خاص على الخادم.

---

### الخطوة 3: تحميل مستند Word

مع إعداد الخيارات جاهزة، ننتقل أخيرًا إلى **load word document**. هذه هي اللحظة التي يقوم فيها Aspose بتحليل ملف DOCX، وإذا كان هناك أي خطوط مفقودة، يتم تشغيل رد النداء الخاص بنا.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**ماذا يحدث خلف الكواليس؟**  
يقوم Aspose.Words بقراءة أجزاء XML في ملف DOCX، ويحل كل إشارة `<w:font>`، ويتحقق من مجموعة الخطوط في النظام. كلما تعذر تلبية إشارة، يستبدل الخط بأول خط بديل متطابق ويطلق تحذير `FontSubstitution`.

---

### الخطوة 4: التحقق من الناتج

شغّل البرنامج وراقب وحدة التحكم. لكل خط مفقود ستظهر لك سطر مشابه لـ:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

إذا لم يحتوي المستند على خطوط مفقودة، ستبقى وحدة التحكم صامتة—مما يعني أن **how to detect fonts** لم تُسجّل أي حالات.

---

### الخطوة 5: مثال كامل يعمل (تطبيق Console)

فيما يلي ملف `Program.cs` مستقل يمكنك وضعه في مشروع Console جديد. يتضمن جميع الأجزاء التي ناقشناها بالإضافة إلى أداة صغيرة لإبقاء نافذة وحدة التحكم مفتوحة أثناء التصحيح.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**الناتج المتوقع في وحدة التحكم** (مثال):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

إذا استبدلت `MissingFont.docx` بملف يستخدم فقط الخطوط المثبتة، ستظهر لك فقط سطر “Press any key…”—مؤكدًا أن منطق الكشف يعمل كما هو متوقع.

---

## أسئلة شائعة وحالات خاصة

### ماذا لو أردت التقاط *جميع* التحذيرات، وليس فقط استبدال الخطوط؟

ببساطة احذف شرط `if (info.Type == WarningType.FontSubstitution)`. يحتوي كائن `WarningInfo` على تعداد `Type` يمكنك التفرع بناءً عليه لحالات أخرى (مثل `DocumentStructure`، `ImageLoading`).

### هل يمكنني تسجيل التحذيرات في ملف بدلاً من وحدة التحكم؟

بالتأكيد. استبدل `Console.WriteLine` بأي استدعاء لإطار تسجيل (`Serilog`، `NLog`، إلخ). رد النداء يُنفّذ على نفس الخيط الذي يحمل المستند، لذا تأكد من أن مسجلك آمن للاستخدام المتعدد الخيوط.

### كيف يتصرف هذا في تطبيق ويب؟

في ASP.NET Core عادةً ما تقوم بحقن تنفيذ `IWarningCallback` كـ singleton وتمريره عبر `LoadOptions`. تذكر تجنّب الكتابة مباشرة إلى تدفق الاستجابة—سجّل إلى قاعدة بيانات أو مجموعة في الذاكرة يمكن عرضها لاحقًا عبر نقطة API.

### ماذا عن الخطوط المخصصة المخزنة في مجلد غير نظامي؟

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

الآن سيبحث Aspose.Words في `C:\MyCustomFonts` قبل اللجوء إلى خطوط النظام، مما يقلل عدد تحذيرات الاستبدال التي تراها.

---

## ملخص بصري

![اكتشاف تحذير استبدال الخطوط في Aspose.Words](/images/font-warning-callback.png "كيفية اكتشاف الخطوط باستخدام رد نداء تحذيري")

*تظهر اللقطة ناتج وحدة التحكم عندما يتم استبدال خط مفقود. يحتوي النص البديل على الكلمة المفتاحية الأساسية لتحسين SEO.*

---

## الخاتمة

أصبح لديك الآن نمط جاهز للإنتاج **how to detect fonts** في أي ملف Word تقوم بتحميله باستخدام Aspose.Words. من خلال **how to set callback** ستحصل على رؤى فورية حول الخطوط المفقودة أو المستبدلة، وتعلمت الطريقة الصحيحة لـ **load word document** مع الحفاظ على نظافة وصيانة الكود.

ما الخطوة التالية؟ جرّب توسيع رد النداء لجمع التحذيرات في قائمة، ثم عرضها في واجهة مستخدم أو تقرير آلي. يمكنك أيضًا استكشاف `FontSettings.SubstitutionSettings` للتحكم في *أي* الخطوط تُختار كبدائل.

لا تتردد في التجربة—غيّر المستند، أضف خطوطًا مفقودة أكثر، أو دمج المنطق في خط معالجة مستندات أكبر. إذا واجهت أي صعوبات، اترك تعليقًا أدناه أو تواصل معي عبر GitHub.

برمجة سعيدة، ولتظهر مستنداتك دائمًا بالخطوط التي تتوقعها!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}