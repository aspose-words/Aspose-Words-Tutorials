---
category: general
date: 2026-04-07
description: تعلم كيفية اكتشاف الخطوط وكيفية التقاط التحذيرات أثناء التعامل مع الخطوط
  المفقودة في C# باستخدام Aspose.Words. يتضمن كودًا خطوة بخطوة.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: ar
og_description: كيف تكتشف الخطوط في Aspose.Words؟ اتبع هذا الدرس لالتقاط التحذيرات
  ومعالجة الخطوط المفقودة بسهولة.
og_title: كيفية اكتشاف الخطوط في Aspose.Words – الدليل الكامل
tags:
- Aspose.Words
- C#
- Font handling
title: كيفية اكتشاف الخطوط في Aspose.Words – الدليل الكامل
url: /ar/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية اكتشاف الخطوط في Aspose.Words – دليل كامل

هل تساءلت يومًا **كيف يتم اكتشاف الخطوط** المفقودة من مستند Word قبل نشره في بيئة الإنتاج؟ لست وحدك. في العديد من سيناريوهات الشركات، يمكن أن يتسبب خط غير موجود في تعطل خط أنابيب تحويل PDF أو يسبب عيوبًا في التخطيط تبدو غير احترافية. الخبر السار هو أن Aspose.Words يوفر لك طريقة مدمجة لاكتشاف تلك الخطوط الغائبة وعرض تحذيرات واضحة.

في هذا الدرس سنستعرض خطوة بخطوة **كيفية اكتشاف الخطوط**، **كيفية التقاط التحذيرات**، وأفضل الممارسات **للتعامل مع الخطوط المفقودة** بحيث يبقى تطبيقك قويًا. لا أدوات خارجية، لا تخمين—فقط كود C# نقي يمكنك إدراجه في مشروعك الآن.

> **معاينة سريعة:** في النهاية ستحصل على `FontSubstitutionWarningCollector` قابل لإعادة الاستخدام يجمع كل رسائل استبدال الخط أثناء تحميل المستند، وستعرف كيف تتعامل عندما لا يمكن العثور على خط.

---

## ما ستتعلمه

- كيفية تكوين `LoadOptions` للاستماع إلى تحذيرات استبدال الخط.  
- كيفية التقاط تلك التحذيرات في فئة جامع مخصصة.  
- كيفية معالجة التحذيرات المجمعة وتحديد ما إذا كان يجب إيقاف العملية، أو تسجيلها، أو استبدال الخطوط.  
- معالجة الحالات الحدية للمستندات التي تشير إلى خطوط عن بُعد أو مضمنة.  

**المتطلبات المسبقة:** .NET 6+ (أو .NET Framework 4.6+)، Aspose.Words for .NET (أحدث نسخة)، ومعرفة أساسية بـ C#. إذا لم تستخدم Aspose.Words من قبل، لا تقلق—هذا الدليل يفترض فقط بضع دقائق من إعداد البيئة.

## كيفية اكتشاف الخطوط باستخدام Aspose.Words LoadOptions

الخطوة الأولى لاكتشاف الخطوط المفقودة هي إخبار Aspose.Words بالإبلاغ عنها. يتم ذلك عبر خاصية `LoadOptions.WarningCallback` التي تقبل أي فئة تنفذ `IWarningCallback`. أدناه نقوم بإنشاء جامع صغير يخزن كل تحذير للمراجعة لاحقًا.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**لماذا هذا مهم:** بدون رد نداء التحذير، يقوم Aspose.Words باستبدال الخطوط المفقودة بصمت بخط افتراضي، ولن تعرف أن هناك مشكلة. من خلال التقاط `WarningType.FontSubstitution` نحصل على رؤية كاملة—وهي البيانات التي تحتاجها **لاكتشاف الخطوط** غير المتوفرة على الجهاز المضيف.

الآن نقوم بربط الجامع بـ `LoadOptions` ونحمّل مستندًا:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **نصيحة احترافية:** إذا كنت تتعامل مع العديد من المستندات دفعة واحدة، أعد استخدام نفس مثيل `FontSubstitutionWarningCollector` لكن تذكر استدعاء `Clear()` بين عمليات التحميل لتجنب خلط التحذيرات من ملفات مختلفة.

## التقاط التحذيرات أثناء تحميل المستند

بعد تحميل المستند، يحتفظ الجامع بالفعل بكل التحذيرات المتعلقة بالخطوط. السؤال المنطقي التالي هو: *كيف يمكنني التقاط التحذيرات* بطريقة سهلة للتسجيل أو العرض؟

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

المخرجات النموذجية تبدو هكذا:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**ما الذي يخبرك به هذا:** كل سطر يكشف عن اسم الخط الأصلي والبديل الذي اختاره Aspose.Words. مع هذه المعلومات يمكنك اتخاذ قرار ما إذا كان البديل مقبولًا أو إذا كنت بحاجة إلى تضمين الخط المفقود يدويًا.

## التعامل مع الخطوط المفقودة بشكل سلس

اكتشاف التقاط التحذيرات هو نصف المعركة فقط. القيمة الحقيقية تظهر عندما **تتعامل مع الخطوط المفقودة** بطريقة جاهزة للإنتاج. فيما يلي ثلاث استراتيجيات شائعة:

1. **سجل واستمر** – مناسب لمعالجة الدُفعات حيث تحتاج فقط إلى سجل تدقيق.  
2. **إيقاف عند الخطوط الحرجة** – إلقاء استثناء إذا كان خط معين (مثل خط علامة تجارية) مفقودًا.  
3. **تضمين الخط أثناء التشغيل** – تحميل الخط المفقود من مجلد معروف وتسجيله في Aspose.Words قبل إعادة تحميل المستند.  

### مثال: إيقاف عند خط حرج

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### مثال: تضمين الخطوط المفقودة تلقائيًا

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**لماذا تساعد هذه الأنماط:** من خلال اتخاذ قرار صريح حول ما يجب فعله عندما يكون الخط مفقودًا، تُزيل الاستبدالات الصامتة التي قد تضر بالعلامة التجارية أو القراءة. هذا هو جوهر **التعامل مع الخطوط المفقودة** بطريقة مُتحكم فيها.

## مثال عملي كامل

بجمع كل شيء معًا، إليك برنامج واحد جاهز للتنفيذ يوضح **كيفية اكتشاف الخطوط**، **كيفية التقاط التحذيرات**، وسياسة بسيطة **للتعامل مع الخطوط المفقودة** عن طريق تسجيلها.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**النتيجة المتوقعة:** عند تشغيل البرنامج على مستند يشير إلى خط غير موجود على الجهاز، ستعرض وحدة التحكم كل تحذير استبدال. إذا كان أي تحذير يتعلق بخط من مجموعة `critical`، سيخرج البرنامج مبكرًا، مما يمنع إنشاء PDF معيب.

## الأسئلة المتكررة (FAQs)

| السؤال | الجواب |
|----------|--------|
| *هل أحتاج إلى ترخيص لـ Aspose.Words لاستخدام هذا الكود؟* | نعم، الترخيص الصالح لـ Aspose.Words يزيل العلامات المائية للتقييم ويفتح كامل الوظائف. |
| *هل يمكن لهذه الطريقة اكتشاف الخطوط المضمنة؟* | الخطوط المضمنة هي بالفعل جزء من الملف، لذا لا يطلق Aspose.Words تحذير استبدال. يمكنك فحص `Document.FontInfos` لتعداد الخطوط المضمنة إذا لزم الأمر. |
| *ماذا لو كان الخط المفقود خط نظام على Windows لكنه غير موجود على Linux؟* | سيظهر نفس التحذير على Linux لأن الخط غير مثبت هناك. استخدم استراتيجية “التعامل مع الخطوط المفقودة” لتضمين ملفات `.ttf` المطلوبة مع تطبيقك. |
| *هل جامع التحذيرات يعمل في خيط* |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}