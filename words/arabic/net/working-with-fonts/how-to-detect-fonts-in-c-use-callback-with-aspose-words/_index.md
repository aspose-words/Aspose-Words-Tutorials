---
category: general
date: 2026-03-17
description: كيفية اكتشاف الخطوط في C# باستخدام Aspose.Words واستدعاء التحذير. تعلّم
  كيفية استخدام استدعاء رد الفعل لالتقاط استبدالات الخطوط المفقودة أثناء تحميل المستندات.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: ar
og_description: كيفية اكتشاف الخطوط في C# باستخدام Aspose.Words. يوضح هذا الدليل كيفية
  استخدام رد الاتصال لالتقاط تحذيرات الخطوط المفقودة أثناء تحميل المستند.
og_title: كيفية اكتشاف الخطوط في C# – استخدام رد الاتصال مع Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: كيفية اكتشاف الخطوط في C# – استخدام رد الاتصال مع Aspose.Words
url: /ar/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

lists.

Also code block placeholders remain.

Also keep any inline code like `IWarningCallback`, `WarningInfo`, etc unchanged.

Also keep markdown links unchanged.

Let's produce Arabic translation.

Be careful with RTL: we can just write Arabic text.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية اكتشاف الخطوط في C# – استخدام رد نداء (Callback) مع Aspose.Words

هل احتجت يوماً إلى **كيفية اكتشاف الخطوط** في مستند Word برمجياً وتساءلت لماذا تبدو بعض الأحرف غريبة بعد التحويل؟ لست وحدك. في العديد من المشاريع الواقعية—مولدات الفواتير، مُصدِّري التقارير، أو خطوط معالجة الدُفعات—تؤدي الخطوط المفقودة إلى مشكلات تخطيط صامتة يصعب تتبعها.

الخبر السار؟ Aspose.Words يوفّر لك طريقة نظيفة للكشف عن هذه المشكلات عبر رد نداء تحذيري. في هذا الدرس ستتعلم **كيفية استخدام رد نداء** لالتقاط كل استبدال للخط يقوم به Aspose أثناء تحميل المستند، وستحصل على مثال جاهز للتنفيذ يطبع تقريراً واضحاً عن الخطوط المفقودة.

سنغطي:

* المتطلبات الأساسية الأدنى (مشروع .NET وحزمة Aspose.Words عبر NuGet).  
* كيفية تنفيذ `IWarningCallback` للاستماع إلى `WarningType.FontSubstitution`.  
* كيفية ربط رد النداء بـ `LoadOptions` وتحميل المستند.  
* ما هو شكل المخرجات، بالإضافة إلى بعض النصائح العملية لتطبيقات الإنتاج.

بنهاية هذا الدرس، ستتمكن من **اكتشاف الخطوط** تلقائيًا في أي ملف DOCX أو DOC أو RTF واتخاذ إجراءات بناءً على معلومات الخط المفقود—سواء كان ذلك تسجيلًا، تنبيهًا للمستخدم، أو استبدال بخط احتياطي.

---

![كيفية اكتشاف الخطوط في مستند Word باستخدام رد نداء تحذيري من Aspose.Words](https://example.com/images/detect-fonts.png "كيفية اكتشاف الخطوط في مستند Word")

## ما ستحتاجه

* **.NET 6.0** أو أحدث (يمكن أيضًا تجميع المثال مع .NET Framework 4.6+).  
* **Aspose.Words for .NET** – تثبيت عبر NuGet: `Install-Package Aspose.Words`.  
* ملف Word تجريبي يحتوي على إشارة إلى خط غير مثبت لديك (مثال: `MissingFont.docx`).  

لا توجد مكتبات إضافية مطلوبة؛ كل شيء موجود داخل مساحة الاسم Aspose.

---

## كيفية اكتشاف الخطوط باستخدام رد نداء تحذيري

### الخطوة 1: إنشاء فئة رد نداء تحذيري

رد النداء ينفّذ `IWarningCallback`. عندما يواجه Aspose.Words خطًا لا يستطيع العثور عليه، يُطلق `WarningInfo` من النوع `WarningType.FontSubstitution`. فئتنا ببساطة تكتب سطرًا ودودًا إلى وحدة التحكم.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**لماذا هذا مهم:** من خلال تصفية `WarningType.FontSubstitution` نتجنب التحذيرات المزعجة (مثل الميزات المهجورة) ونبقي السجل مركزًا على المشكلة التي نريد حلها—**اكتشاف الخطوط** غير الموجودة على الجهاز.

---

### الخطوة 2: ربط رد النداء بـ `LoadOptions`

`LoadOptions` يتيح لك تخصيص طريقة تحليل المستند. تعيين كائن `FontWarningCollector` إلى الخاصية `WarningCallback` يخبر Aspose باستدعائه كلما صادف خطًا مفقودًا.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**نصيحة:** يمكنك أيضًا ضبط `LoadOptions.FontSettings` هنا إذا رغبت في توفير خط احتياطي برمجيًا. هذا سيناريو متقدم سنذكره لاحقًا.

---

### الخطوة 3: تحميل المستند ومراقبة المخرجات

الآن نقوم بتحميل الملف فعليًا. بمجرد أن يقوم Aspose بتحليل المستند، أي خط لا يمكنه العثور عليه سيُطلق رد النداء الخاص بنا.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**المخرجات المتوقعة في وحدة التحكم** (بافتراض أن المستند يشير إلى *Comic Sans MS* غير المثبت):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

إذا كان المستند يحتوي على عدة خطوط مفقودة، سترى سطرًا لكل خط—وهو بالضبط ما تحتاجه من معلومات **كيفية اكتشاف الخطوط**.

---

## كيفية استخدام رد النداء في سيناريوهات أكثر تعقيدًا

### تسجيل إلى ملف بدلاً من وحدة التحكم

في بيئة الإنتاج قد تحتاج إلى سجل دائم. استبدل `Console.WriteLine` بـ `StreamWriter`:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### جمع التحذيرات للتحليل لاحقًا

أحيانًا تحتاج إلى قائمة الخطوط المفقودة بعد تحميل المستند، ربما لعرضها في نافذة واجهة مستخدم. احفظ التحذيرات في `List<string>` وقدمها عبر خاصية:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### توفير خط احتياطي برمجيًا

إذا كان لديك خط مؤسسي تريد فرضه، يمكنك إضافته إلى `FontSettings` قبل التحميل:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

الآن يقوم Aspose باستبدال الخطوط المفقودة بـ *Arial Unicode MS* مع الاستمرار في الإبلاغ عن الاستبدال عبر رد النداء. هذه طريقة أنيقة لـ **كيفية استخدام رد النداء** لكل من الاكتشاف والتصحيح التلقائي.

---

## الأخطاء الشائعة والنصائح الاحترافية

| الفخ | لماذا يحدث | كيفية التجنب |
|--------|----------------|--------------|
| **نسيان استيراد `Aspose.Words.Warnings`** | واجهة `IWarningCallback` موجودة هناك. | أضف `using Aspose.Words.Warnings;` في أعلى الملف. |
| **تحميل المستند دون `LoadOptions`** | المحمل الافتراضي يستبدل الخطوط بصمت دون إشعار. | دائمًا أنشئ كائن `LoadOptions` وعيّن رد النداء الخاص بك. |
| **تشغيل على خادم بصلاحيات محدودة** | كتابة سجل إلى ملف قد تُثير استثناء `UnauthorizedAccessException`. | استخدم مجلدًا قابلًا للكتابة (مثل دليل بيانات التطبيق) أو اقتصر على المجموعات في الذاكرة. |
| **مشاركة نفس المجمع بين عدة خيوط** | `FontWarningCollector` غير آمن للثلاثة بشكل افتراضي. | أنشئ مجمعًا منفصلًا لكل خيط أو احمِ القائمة بقفل. |
| **الافتراض أن رد النداء يُستدعى للخطوط المدمجة** | الخطوط المدمجة موجودة بالفعل داخل المستند؛ لا يُطلق تحذير. | إذا كنت بحاجة للتحقق من سلامة الخطوط المدمجة، افحص `FontInfo` عبر `FontSettings`. |

---

## مثال كامل جاهز للتنفيذ (انسخه‑ألصقه)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**ما يجب أن تراه** (بافتراض أن الملف يشير إلى خطين غير موجودين):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

إذا كان الملف يستخدم خطوطًا مثبتة فقط، ستطبع وحدة التحكم ببساطة:

```
Document loaded successfully.

No missing fonts detected.
```

---

## الخلاصة

لقد استعرضنا **كيفية اكتشاف الخطوط** في مستند Word عبر ربط رد نداء تحذيري مخصص بـ Aspose.Words. هذه الطريقة خفيفة، ولا تتطلب سوى:

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}