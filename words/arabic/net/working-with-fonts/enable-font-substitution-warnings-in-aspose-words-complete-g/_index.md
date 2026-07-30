---
category: general
date: 2026-01-11
description: قم بتمكين تحذيرات استبدال الخطوط لاكتشاف الخطوط المفقودة في مستندات .NET
  الخاصة بك. تعلّم كيفية الحصول على اسم الخط المفقود وقائمة الخطوط المفقودة باستخدام
  Aspose.Words.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: ar
og_description: قم بتمكين تحذيرات استبدال الخطوط في Aspose.Words لاكتشاف الخطوط المفقودة،
  والحصول على اسم الخط المفقود، وإدراج الخطوط المفقودة في مستنداتك.
og_title: تمكين تحذيرات استبدال الخط – دليل C# خطوة بخطوة
tags:
- Aspose.Words
- C#
- Document Processing
title: تمكين تحذيرات استبدال الخطوط في Aspose.Words – دليل كامل
url: /ar/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تمكين تحذيرات استبدال الخطوط – دليل كامل

هل تساءلت يوماً لماذا يبدو مستند Word مختلفًا قليلاً بعد تحميله على الخادم؟ من المحتمل أن الخط الذي استخدمه المؤلف الأصلي غير متوفر على جهازك، وأن Aspose.Words استبدله بصمت بأقرب مطابقة. **تمكين تحذيرات استبدال الخطوط** سيمكنك من معرفة الخطوط المفقودة على الفور، وما تم استبداله به، وكيفية اتخاذ الإجراء بناءً على تلك المعلومات.

في هذا البرنامج التعليمي سنستعرض مثالًا عمليًا من البداية إلى النهاية يوضح لك كيفية **اكتشاف الخطوط المفقودة**، استرجاع **اسم الخط المفقود**، وحتى **قائمة الخطوط المفقودة** للتقارير. لا إطالة، مجرد حل واضح يمكنك دمجه في أي مشروع .NET اليوم.

---

## ما ستتعلمه

- كيفية تكوين `LoadOptions` بحيث تقوم Aspose.Words بإصدار تحذيرات مفصلة.
- الكود الدقيق اللازم لتحميل مستند وتعداد التحذيرات المتعلقة بالخطوط.
- طرق استخراج اسم الخط المفقود واستبداله، ثم إخراج تقرير منسق.
- نصائح للتعامل مع الحالات الخاصة، مثل المستندات التي تحتوي على عشرات الخطوط المفقودة أو مجلدات الخطوط المخصصة.

### المتطلبات المسبقة

- .NET 6+ (الكود يعمل أيضًا مع .NET Framework 4.7+)
- Aspose.Words for .NET 23.10 أو أحدث (يمكنك الحصول عليه من NuGet)
- ملف DOCX تجريبي يحتوي على خط غير مثبت على جهازك (سنسميه `MissingFont.docx`)

إذا كان لديك هذه الأساسيات، فلنبدأ.

---

## الخطوة 1: إعداد LoadOptions لتمكين تحذيرات استبدال الخطوط  

The أول شيء تحتاج إلى فعله هو إخبار Aspose.Words أنك تهتم بالخطوط المفقودة. بشكل افتراضي، تقوم المكتبة بتسجيل التحذيرات داخليًا فقط. ضبط `SubstitutionWarningLevel` إلى `Typical` (أو `All` للحصول على أكثر التفاصيل) يفعّل التحذير.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**لماذا هذا مهم:**  
عند ضبط `SubstitutionWarningLevel`, في كل مرة لا تتمكن Aspose.Words من العثور على خط مُشار إليه, تُضيف `FontSubstitutionWarning` إلى مجموعة `Warnings` الخاصة بالمستند. هذه المجموعة هي الطريقة الوحيدة الموثوقة لـ **اكتشاف الخطوط المفقودة** دون الحاجة إلى تحليل المستند يدويًا.

> **نصيحة احترافية:** إذا كنت تتعامل مع مجموعة من المستندات وتريد أن تكون متأكدًا تمامًا من التقاط كل استبدال, استخدم `FontSubstitutionWarningLevel.All`. سيكون أكثر إزعاجًا قليلًا لكنه يضمن عدم تفويت أي تحذير.

---

## الخطوة 2: تحميل المستند باستخدام الخيارات المُكوَّنة  

الآن بعد أن تم تهيئة نظام التحذير, قم بتحميل ملف DOCX الخاص بك باستخدام `LoadOptions` التي أعددناها للتو. يمكن أن يكون المسار مطلقًا أو نسبيًا; فقط تأكد من وجود الملف.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**ما الذي يحدث خلف الكواليس؟**  
تقوم Aspose.Words بتحليل XML الخاص بالمستند, وتحديد كل عنصر `<w:font>`, وتفحص كتالوج الخطوط في النظام (بالإضافة إلى أي مجلدات مخصصة قد تكون أضفتها إلى `FontSettings`). عندما لا تستطيع العثور على خط, تسجل تحذيرًا — وهذا بالضبط ما نحتاجه لـ **قائمة الخطوط المفقودة** لاحقًا.

---

## الخطوة 3: التكرار على التحذيرات واستخراج تفاصيل الخط المفقود  

مع وجود المستند في الذاكرة, تحتوي مجموعة `Warnings` على كل `FontSubstitutionWarning`. سنقوم بالتكرار عليها, وتصفية النوع المناسب, وطباعة تقرير سهل القراءة.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**الناتج المتوقع** (بافتراض أن المستند المصدر يشير إلى `MyCustomFont` الذي ليس مثبتًا):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

لاحظ كيف أن كل إدخال يزودك بكل من **اسم الخط المفقود** (`MyCustomFont`) والبديل (`Arial`). هذه هي المعلومات التي تحتاجها لتقرر ما إذا كنت ستدمج الخط الأصلي, أو تطلب من المؤلف استبداله, أو تقبل الاستبدال ببساطة.

---

## الخطوة 4: اختياري – جمع البيانات في قائمة لمعالجة إضافية  

إذا كنت بحاجة لتصدير التقرير إلى CSV, أو إرساله عبر API, أو مجرد الاحتفاظ به في الذاكرة لاستخدامه لاحقًا, يمكنك تخزين التحذيرات في قائمة ذات نوع قوي.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

الآن لديك **قائمة الخطوط المفقودة** بصيغة يمكن لأي نظام لاحق استهلاكها. سواء كنت تزود لوحة معلومات أو تولد سجل تدقيق, البيانات جاهزة.

---

## الخطوة 5: التعامل مع الحالات الخاصة والمشكلات الشائعة  

### عدة خطوط مفقودة في تشغيل واحد  

قوالب الشركات الكبيرة غالبًا ما تشير إلى عشرات الخطوط المخصصة. قد تصبح مجموعة التحذيرات كبيرة, لكن نمط التكرار الموضح أعلاه يتوسع خطيًا, لذا لا توجد مشكلة في الأداء. فقط تذكر الحفاظ على قابلية القراءة—يمكن أن يكون التجميع حسب الصفحة أو النمط مفيدًا إذا كنت تحتاج إلى تحليل أعمق.

### مجلدات الخطوط المخصصة  

إذا كنت تخزن الخطوط في دليل غير قياسي (مثلاً مشاركة شبكة مشتركة), أخبر Aspose.Words بمكان البحث:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

ضبط هذا *قبل* تحميل المستند يمنح المكتبة فرصة للعثور على الخطوط, مما قد يلغي بعض التحذيرات تمامًا.

### كتم التحذيرات المحددة  

أحيانًا تعرف أن استبدالًا معينًا مقبول (مثلاً خط زخرفي لا تمانع استبداله). يمكنك تصفية تلك بعد ذلك:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### توافق الإصدارات  

عدد `FontSubstitutionWarningLevel` ثابت منذ Aspose.Words 20.12. إذا كنت تستخدم إصدارًا أقدم, قد تحتاج إلى الترقية للوصول إلى ميزة مستوى التحذير.

---

## مثال كامل يعمل  

فيما يلي البرنامج الكامل الجاهز للتنفيذ والذي يجمع جميع الخطوات السابقة. الصقه في مشروع وحدة تحكم جديد, أضف حزمة Aspose.Words من NuGet, وحدد `docPath` إلى مستند يشير إلى خط مفقود.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

تشغيل هذا البرنامج سيقوم **بتمكين تحذيرات استبدال الخطوط**, **اكتشاف الخطوط المفقودة**, **الحصول على اسم الخط المفقود**, و **قائمة الخطوط المفقودة** في كل من وحدة التحكم وملف CSV.

---

## الخلاصة  

لقد غطينا الآن كل ما تحتاجه **لتمكين تحذيرات استبدال الخطوط** في Aspose.Words, بدءًا من التكوين الأولي وحتى استخراج قائمة نظيفة بالخطوط المفقودة. باتباع الخطوات أعلاه ستتمكن من تدقيق مستنداتك, وضمان الدقة البصرية, وتجنب المفاجآت غير السارة عند العرض على الخادم.

بعد ذلك, قد ترغب في استكشاف:

- **دمج الخطوط المفقودة** مباشرةً في ملف PDF أو DOCX الناتج (استخدم `FontSettings.EmbeddedFonts`).
- **أتمتة تثبيت الخطوط** على عوامل البناء بناءً على التقرير المُولد.
- **دمج مع خطوط أنابيب CI** لإيقاف عمليات البناء عندما تكون الخطوط الحيوية غير موجودة.

جرّب ذلك, وستحول نظام التحذير البسيط إلى سير عمل كامل لإدارة الخطوط.

برمجة سعيدة, ولتُعثر على جميع خطوطك!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}