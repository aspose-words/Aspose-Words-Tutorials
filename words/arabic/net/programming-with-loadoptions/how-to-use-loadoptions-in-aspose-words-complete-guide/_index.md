---
category: general
date: 2026-01-10
description: تعلم كيفية استخدام LoadOptions للتعامل مع الخطوط المفقودة في Aspose.Words.
  كود خطوة بخطوة، نصائح، وأفضل الممارسات لتحميل المستندات بشكل قوي.
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: ar
og_description: كيفية استخدام LoadOptions للتعامل مع الخطوط المفقودة في Aspose.Words.
  احصل على مثال كامل قابل للتنفيذ مع شروحات ونصائح عملية.
og_title: كيفية استخدام LoadOptions في Aspose.Words – دليل كامل
tags:
- Aspose.Words
- C#
- .NET
title: كيفية استخدام LoadOptions في Aspose.Words – دليل كامل
url: /ar/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية استخدام LoadOptions في Aspose.Words – دليل كامل

هل تساءلت يومًا **how to use LoadOptions** عند تحميل مستند Word قد يفتقد بعض الخطوط؟ لست وحدك في هذه الحيرة. في العديد من المشاريع الواقعية، تنتقل المستندات بين الأجهزة، وغالبًا ما يفتقر النظام الهدف إلى الخطوط الدقيقة التي استخدمها المؤلف. النتيجة؟ استبدالات خطوط غير متوقعة قد تُفسد التخطيط، أو تُخفي أحرفًا مهمة، أو ببساطة تبدو غير متناسقة مع العلامة التجارية.  

لحسن الحظ، توفر Aspose.Words طريقة نظيفة *للتعامل مع الخطوط المفقودة* من خلال كائن `LoadOptions` مع رد نداء تحذير. في هذا الدرس ستتعلم بالضبط **how to use LoadOptions** لالتقاط تحذيرات استبدال الخطوط، وتسجيلها، والحفاظ على استقرار خط أنابيب المعالجة الخاص بك.

سنغطي:

* إعداد فئة رد نداء التحذير  
* تكوين `LoadOptions` باستخدام هذا الرد  
* تحميل مستند مع تتبع الخطوط المفقودة  
* نصائح لاستكشاف الأخطاء وإصلاحها وتوسيع الحل  

لا حاجة إلى وثائق خارجية—كل ما تحتاجه موجود هنا.

---

## ما ستحتاجه

قبل أن نبدأ، تأكد من أن لديك:

* **Aspose.Words for .NET** (أحدث نسخة حتى عام 2026) مثبتة عبر NuGet  
* بيئة تطوير .NET (Visual Studio، Rider، أو VS Code)  
* ملف DOCX تجريبي يشير إلى خط غير مثبت لديك (سنسميه `input.docx`)  

هذا كل شيء—لا مكتبات إضافية مطلوبة.

---

## الخطوة 1 – تعريف رد نداء التحذير لالتقاط استبدال الخطوط

القطعة الأولى من اللغز هي فئة تنفذ `IWarningCallback`. ستستدعي Aspose.Words طريقة `Warning` الخاصة بها كلما صادفت شيئًا يستحق الانتباه—مثل خط مفقود.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**لماذا هذا مهم:**  
من خلال الترشيح على `WarningType.FontSubstitution` نتجنب الفوضى الناتجة عن التحذيرات غير المتعلقة (مثل الميزات المهجورة). يمنحك رد النداء تحكمًا كاملاً—يمكنك تسجيله في ملف، رفع استثناء، أو حتى محاولة تضمين خط بديل برمجيًا.

---

## الخطوة 2 – تكوين LoadOptions مع رد النداء

الآن بعد أن لدينا معالجًا، نحتاج إلى إخبار Aspose.Words باستخدامه. هنا يأتي دور **how to use LoadOptions** عمليًا.

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**نصيحة:** `LoadOptions` يقدم العديد من المفاتيح الأخرى (مثل `Password`، `LoadFormat`، `Encoding`). يمكنك ربطها معًا، لكن لمعالجة الخطوط المفقودة يكون `WarningCallback` هو النجم الرئيسي.

---

## الخطوة 3 – تحميل المستند باستخدام الخيارات المكوَّنة

مع إعداد `LoadOptions` جاهز، يصبح تحميل المستند أمرًا بسيطًا. ستستدعي Aspose.Words رد النداء تلقائيًا لأي خط لا يمكنها العثور عليه.

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**الناتج المتوقع:**  

إذا كان `input.docx` يستخدم خطًا يُدعى *“GothicBold”* غير مثبت، سترى شيئًا مثل:

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

سطر التحذير يظهر **بالضبط عند مواجهة الخط المفقود**، مما يمنحك تغذية راجعة فورية.

---

## الخطوة 4 – (اختياري) متابعة معالجة المستند

عادةً ما ترغب في فعل أكثر من مجرد تحميل الملف. فيما يلي بعض الإجراءات الشائعة بعد التحميل التي تعمل بسلاسة مع إعداد التحذير لدينا.

### 4.1 حفظ المستند كملف PDF

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 استبدال الخطوط المفقودة ببديل معروف

إذا كنت تفضّل بديلًا محددًا (مثل *“Calibri”*), يمكنك تعديل `FontSettings` قبل الحفظ:

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 تسجيل جميع التحذيرات في ملف

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

هذه المقاطع توضح **how to use LoadOptions** بما يتجاوز الحالة الأساسية، مما يمنحك مرونة لحلول جاهزة للإنتاج.

---

## الأخطاء الشائعة وكيفية **Handle Missing Fonts** بأناقة

| المشكلة | لماذا تحدث | طريقة الإصلاح / التخفيف |
|---------|------------|------------------------|
| **لم يتم إرفاق رد النداء** | نسيت تعيين `WarningCallback`. | دائمًا أنشئ كائن `LoadOptions` وعيّن معالجك قبل التحميل. |
| **رد النداء يطبع فقط ولا يخزن** | في خدمة ويب، يختفي إخراج الـ console. | استبدل `Console.WriteLine` بمسجل (Serilog، NLog) أو اكتب إلى مخزن دائم. |
| **عدة خطوط مفقودة، يتم الإبلاغ عن الأول فقط** | رد النداء يرمي استثناءً عند أول تحذير. | حافظ على خفة رد النداء؛ تجنّب الرمي إلا إذا كنت تريد الإيقاف فعلاً. |
| **الخط المستبدل يبدو غير مناسب** | الاستبدال الافتراضي قد يختار خطًا بصريًا مختلفًا. | استخدم `FontSettings.SubstitutionSettings.FontSubstitutionRules` لتفضيل بديلك المفضل. |
| **تأثير الأداء على المستندات الضخمة** | يتم استدعاء رد النداء آلاف المرات. | جمع التحذيرات في قائمة ومعالجتها بعد التحميل، أو ترشيح أسماء الخطوط الفريدة فقط. |

الوعي بهذه السيناريوهات يساعدك على **Handle Missing Fonts** دون مفاجآت.

---

## مثال كامل يعمل – جميع الأجزاء معًا

فيما يلي البرنامج الكامل الجاهز للتنفيذ الذي يوضح التدفق بالكامل. انسخه‑الصقه في مشروع Console، أضف حزمة Aspose.Words عبر NuGet، وسيعمل فورًا.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**تشغيل هذا البرنامج** سيقوم بـ:

1. طباعة أي تحذيرات استبدال خطوط إلى الـ console.  
2. حفظ التخطيط الأصلي كـ `output.pdf`.  
3. حفظ PDF ثانٍ (`output-with-fallback.pdf`) يجبر الاستبدال إلى *Calibri* أو *Arial*.

---

## الأسئلة المتكررة (FAQs)

**س: هل يعمل هذا مع ملفات DOC أو RTF أو HTML؟**  
ج: نعم. `LoadOptions` مستقل عن الصيغة؛ طالما مررت مسار الملف الصحيح، سيعمل رد النداء على التحذير للخطوط المفقودة عبر جميع الصيغ المدعومة.

**س: هل يمكنني قمع التحذيرات تمامًا؟**  
ج: يمكنك تعيين رد نداء لا يفعل شيئًا (`new IWarningCallback { Warning = _ => {} }`) أو ضبط `LoadOptions.WarningCallback = null`. ومع ذلك، فقدان الرؤية قد يجعلك تفوت مشاكل خطية حرجة.

**س: ماذا لو أردت استبدال الخطوط المفقودة بخطوط مدمجة؟**  
ج: استخدم `FontSettings` لتضمين ملف خط بديل (`AddFontSource`). اجمع ذلك مع قواعد الاستبدال للحصول على تجربة سلسة.

**س: هل رد النداء آمن للـ thread؟**  
ج: قد يُستدعى رد النداء من عدة خيوط عند تحميل مستندات ضخمة بشكل متوازي. تأكد من مزامنة أي موارد مشتركة (مثل ملفات السجل).

---

## الخلاصة

لقد استعرضنا **how to use LoadOptions** في Aspose.Words لتعامل أنيق مع الخطوط المفقودة. من خلال تعريف `IWarningCallback` مخصص، ربطه بـ `LoadOptions`، وتحميل المستند بهذه الإعدادات، تحصل على رؤية فورية لأي أحداث استبدال خطوط. بعد ذلك يمكنك تسجيلها، استبدالها، أو تضمين خطوط بديلة لضمان أن مخرجاتك تبدو كما هو مقصود.

تذكر الخطوات الأساسية:

1. تنفيذ رد نداء تحذير يركز على `WarningType.FontSubstitution`.  
2. ربط الرد إلى كائن `LoadOptions`.  
3. تحميل المستند باستخدام هذه الخيارات.  
4. (اختياري) تطبيق قواعد استبدال خطوط إضافية أو تسجيل حسب الحاجة.

لا تتردد في التجربة—استبدل مسجل الـ console بمسجل منظم، أضف تنبيهات بريدية للخطوط المفقودة الحرجة، أو دمج هذا النمط في خط أنابيب معالجة مستندات أكبر. النهج يتوسع بسهولة سواء كنت تتعامل مع ملف واحد أو آلاف الملفات في دفعة.

برمجة سعيدة، ولتظهر مستنداتك دائمًا بالخطوط الصحيحة!  

---

![how to use loadoptions example]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}