---
category: general
date: 2026-06-02
description: كيفية التعامل مع الخطوط في .NET – اكتشاف الخطوط المفقودة وتتبع تغيّر
  الخطوط باستخدام LoadOptions و FontSettings. تعلّم حلاً كاملاً قابلاً للتنفيذ.
draft: false
keywords:
- how to handle fonts
- detect missing fonts
- track font changes
language: ar
og_description: كيفية التعامل مع الخطوط في .NET – اكتشاف الخطوط المفقودة وتتبع تغييرات
  الخط. اتبع هذا الدليل خطوة بخطوة للحصول على حل كامل وجاهز للتنفيذ.
og_title: كيفية التعامل مع الخطوط في .NET – اكتشاف الخطوط المفقودة
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: how to handle fonts in .NET – detect missing fonts and track font changes
    using LoadOptions and FontSettings. Learn a complete, runnable solution.
  headline: how to handle fonts in .NET – detect missing fonts
  type: TechArticle
tags:
- .NET
- Aspose.Words
- FontSettings
title: كيفية التعامل مع الخطوط في .NET – اكتشاف الخطوط المفقودة
url: /ar/net/working-with-fonts/how-to-handle-fonts-in-net-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية التعامل مع الخطوط في .NET – اكتشاف الخطوط المفقودة

هل تساءلت يومًا **كيف تتعامل مع الخطوط** عندما يشير مستند Word إلى نوع خط غير مثبت على الجهاز؟ لست وحدك. يمكن للخطوط المفقودة أن تحول تقريرًا مصقولًا إلى فوضى مشوشة، وبدون تحذيرات مناسبة قد لا تعرف أبدًا ما تم استبداله.  

في هذا الدرس سنوضح لك بالضبط **كيف تتعامل مع الخطوط** عن طريق اكتشاف الخطوط المفقودة **و** تتبع تغييرات الخط أثناء التشغيل. في النهاية ستحصل على تطبيق console مستقل يسجل كل استبدال، بحيث لا تتفاجأ أبدًا بظهور Helvetica غامضة في مكان Times New Roman.

> **ما ستحصل عليه:** عينة كود جاهزة للنسخ واللصق، شرح لكل سطر، نصائح للمشاريع الواقعية، ونظرة سريعة على الحالات الحدية التي قد تواجهها.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (العينة تستخدم `Program.cs` من المستوى العلوي للتبسيط)  
- Aspose.Words for .NET 23.9 أو أحدث – يمكنك الحصول عليه من NuGet باستخدام `dotnet add package Aspose.Words`  
- مستند Word يُشير عمدًا إلى خط غير موجود لديك (مثال: `MissingFont.docx`)  

لا توجد مكتبات أخرى مطلوبة.

![Diagram showing how the LoadOptions flow into FontSettings and the substitution warning event – how to handle fonts in .NET example](https://example.com/images/font‑handling‑flow.png "how to handle fonts in .NET example")

## الخطوة 1: إعداد LoadOptions مع FontSettings  

أول شيء نحتاجه هو كائن `LoadOptions` يخبر Aspose.Words بمراقبة مشاكل الخطوط.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

// Create LoadOptions and attach a fresh FontSettings instance.
var loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

**لماذا هذا مهم:** `LoadOptions` هو الحارس عندما يُقرأ المستند من القرص. من خلال توفير `FontSettings` مخصص نحصل على نقطة ربط مع محرك حل الخطوط الداخلي، وهو الطريقة الوحيدة **لاكتشاف الخطوط المفقودة** قبل عرض المستند.

## الخطوة 2: الاشتراك في حدث SubstitutionWarning  

Aspose.Words يطلق حدث `SubstitutionWarning` في كل مرة لا يستطيع فيها العثور على الخط الدقيق الذي طلبته. سنسجل التفاصيل حتى تتمكن من رؤية الخطوط المطلوبة وأيها تم استخدامها فعليًا.  

```csharp
// Hook into the warning event – this is where we “track font changes”.
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.RequestedFontName – the name the document asked for.
    // e.SubstitutedFontName – the name Aspose.Words fell back to.
    // e.WarningType – tells you why the substitution happened.
    Console.WriteLine(
        $"[Font Substitution] Requested: {e.RequestedFontName}, " +
        $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
};
```

**لماذا نستمع:** بدون هذا المستمع لن تعرف أبدًا أن استبدالًا قد حدث. يوفر الحدث مسار تدقيق كامل، مما يلبي متطلب “تتبع تغييرات الخط”.

## الخطوة 3: تحميل المستند باستخدام الخيارات المكوَّنة  

الآن نقوم بقراءة الملف فعليًا. لأننا مررنا `loadOptions`، سيطلق Aspose.Words حدث التحذير لأي خط مفقود يصادفه.  

```csharp
// Replace the path with the location of your test document.
string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

Document doc = new Document(docPath, loadOptions);
```

هذا كل شيء – تم الآن تحميل المستند، وتم طباعة أي مشاكل في الخطوط إلى وحدة التحكم.

## الخطوة 4: (اختياري) التحقق من الخطوط المستبدلة في المستند  

إذا كنت ترغب في التحقق مرة أخرى من الخطوط التي انتهى بها الأمر في PDF أو DOCX النهائي، يمكنك استعراض مجموعة خطوط المستند:  

```csharp
Console.WriteLine("\n--- Fonts actually used in the document ---");
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
}
```

تشغيل هذا بعد التحميل سيُدرج كل خط قرر المحرك تضمينه أو الإشارة إليه. مفيد عندما تحتاج إلى إنشاء تقرير لفرق QA.

## مثال كامل يعمل  

انسخ الكتلة أدناه إلى مشروع console جديد (`dotnet new console`) وشغّله. سيُظهر البرنامج كل استبدال ثم يُدرج الخطوط التي نجت من التحميل.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions with FontSettings.
        // -------------------------------------------------
        var loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Step 2: Hook the substitution warning event.
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"[Font Substitution] Requested: {e.RequestedFontName}, " +
                $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
        };

        // -------------------------------------------------
        // Step 3: Load the document (this triggers warnings).
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // Step 4 (optional): List fonts actually used.
        // -------------------------------------------------
        Console.WriteLine("\n--- Fonts actually used in the document ---");
        foreach (FontInfo fontInfo in doc.FontInfos)
        {
            Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
        }

        Console.WriteLine("\nDone. Press any key to exit.");
        Console.ReadKey();
    }
}
```

### النتيجة المتوقعة  

إذا طلب `MissingFont.docx` الخط *“Comic Sans MS”* (الذي ليس مثبتًا) سترى شيئًا مثل:  

```
[Font Substitution] Requested: Comic Sans MS, Used: Arial, Reason: FontNotFound
[Font Substitution] Requested: Times New Roman, Used: Times New Roman, Reason: None

--- Fonts actually used in the document ---
Arial – Regular
Times New Roman – Regular
```

السطر الأول يثبت أننا **نكتشف الخطوط المفقودة** و**نتتبع تغييرات الخط**. السطر الثاني يُظهر استبدالًا لم يكن ضروريًا (بدون تحذير، لأن الخط كان موجودًا).

## الأخطاء الشائعة والنصائح الاحترافية  

| الخطأ | ما يحدث | كيفية الإصلاح / التجنب |
|-------|----------|------------------------|
| **عدم حدوث أحداث التحذير** | قد تعتقد أن الـ API معطلة. | تأكد من *تعيين* `FontSettings` إلى `LoadOptions` **قبل** تحميل المستند. يجب ربط الحدث **قبل** استدعاء `new Document(...)`. |
| **الخطوط المستبدلة لا تبدو صحيحة** | Aspose.Words يلجأ إلى خط عام لا يتطابق مع النمط. | وفر مجلد خطوط مخصص عبر `fontSettings.SetFontsFolder(@"C:\MyFonts", true)`. يمنح هذا المحرك خيارات أكثر قبل أن يلجأ إلى خط عام. |
| **تأثير الأداء على المستندات الكبيرة** | مسح كل خط قد يضيف بضع مليثانية. | قم بتخزين كائن `FontSettings` في الذاكرة إذا قمت بتحميل مستندات متعددة متتالية. إعادة استخدام نفس المثيل يتجنب إعادة قراءة جداول خطوط النظام. |
| **فقدان مخرجات وحدة التحكم في التطبيقات الرسومية** | لن ترى التحذيرات. | أعد توجيه الحدث إلى مسجل (مثل `Serilog`) أو اكتب إلى ملف: `File.AppendAllText("font-warnings.log", …)`. |

## توسيع الحل  

- **تصدير إلى PDF مع خطوط مدمجة** – بعد التحميل، استدعِ `doc.Save("output.pdf", SaveOptions.CreateSaveOptions(SaveFormat.Pdf));` وتأكد من ضبط `PdfSaveOptions.FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll;`.  
- **معالجة دفعة** – غلف منطق التحميل داخل `foreach` على مجلد ملفات DOCX. سجِّل تحذيرات كل ملف إلى CSV لأغراض التدقيق.  
- **واجهة مستخدم صديقة** – اعرض نفس المنطق خلف زر في تطبيق WinForms/WPF، مع عرض التحذيرات في `ListBox`.  

## الخلاصة  

لقد استعرضنا **كيفية التعامل مع الخطوط** في .NET عن طريق تكوين `LoadOptions`، الاشتراك في حدث `SubstitutionWarning`، وأخيرًا تحميل المستند. المثال لا يكتشف **الخطوط المفقودة** فحسب، بل **يتتبع تغييرات الخط** حتى تتمكن من تدقيق كل استبدال.  

جرّبه مع مستنداتك الخاصة، عدّل مسار مجلد الخطوط، ولن تُفاجأ أبدًا بتبديل خط غير متوقع مرة أخرى. إذا وجدت هذا الدليل مفيدًا، فكر في استكشاف مواضيع ذات صلة مثل *“تضمين خطوط مخصصة في PDF باستخدام Aspose.Words”* أو *“إنشاء استراتيجية احتياطي للخطوط لتطبيقات .NET متعددة المنصات”.*  

برمجة سعيدة، ولتظهر مستنداتك دائمًا كما قصدت!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية تحميل DOCX واكتشاف الخطوط المفقودة – دليل C# كامل](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [كيفية اكتشاف الخطوط في Aspose.Words – التعامل مع التحذيرات والإعدادات](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [كيفية استخدام LoadOptions في Aspose.Words – دليل كامل](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}