---
category: general
date: 2026-05-04
description: تعلم كيفية استخدام استبدال الخطوط في Aspose لاكتشاف الخطوط المفقودة عند
  تحميل مستند Word واسترجاع تفاصيل الخطوط المفقودة — دليل خطوة بخطوة.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: ar
og_description: إتقان استبدال الخطوط في Aspose لاكتشاف الخطوط المفقودة عند تحميل مستند
  Word واسترجاع معلومات الخطوط المفقودة باستخدام كود C# كامل.
og_title: استبدال الخطوط في Aspose – اكتشاف الخطوط المفقودة في مستندات Word
tags:
- Aspose.Words
- C#
- Font Management
title: 'استبدال الخطوط في Aspose: اكتشاف الخطوط المفقودة في مستندات Word'
url: /ar/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استبدال الخطوط في Aspose – اكتشاف الخطوط المفقودة في مستندات Word

هل تساءلت يوماً لماذا يبدو مستند Word غير صحيح على جهاز آخر؟ غالباً ما يكون السبب هو خط مفقود، و**استبدال الخطوط في Aspose** هو الأداة التي تتيح لك اكتشاف هذه الفجوات قبل أن تتحول إلى كارثة بصرية. في هذا الدرس سنستعرض كيفية **اكتشاف الخطوط المفقودة** في لحظة **تحميل مستند Word**، ثم **استرجاع تفاصيل الخط المفقود** لتتمكن من إصلاحه أو استبداله.

سنغطي كل شيء بدءاً من إعداد رد النداء للتحذير إلى استخراج قائمة نظيفة بالخطوط المفقودة. في النهاية ستحصل على مقتطف C# جاهز للتنفيذ يخبرك بالضبط أي الخطوط لم تُعثر عليها، وستفهم لماذا هذا مهم للحفاظ على دقة المستند.

---

## المتطلبات المسبقة – ما تحتاجه قبل البدء

- **Aspose.Words for .NET** (الإصدار 23.12 أو أحدث يُنصح به).  
- بيئة تطوير .NET (Visual Studio، Rider، أو سطر أوامر `dotnet`).  
- ملف DOCX تجريبي يستخدم خطاً غير مثبت لديك—سميه `DocumentWithMissingFont.docx`.  
- معرفة أساسية بـ C#—لا شيء معقد، فقط القدرة على تشغيل تطبيق كونسول.

إذا كان أي من ذلك غير مألوف لك، توقف وقم بتثبيت حزمة NuGet:

```bash
dotnet add package Aspose.Words
```

هذا كل شيء. لا خطوط إضافية، ولا خدمات خارجية.

---

## الخطوة 1: تحميل مستند Word (وتفعيل فحص الخطوط)

أول شيء تقوم به هو **تحميل مستند Word**. يقوم Aspose.Words بتحليل الملف، وإذا لم يتمكن من العثور على الخط المرجعي، فإنه يضيف تحذير *FontSubstitution*. إليك الشيفرة التي تقوم بالتحميل:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **لماذا هذا مهم:** تحميل المستند مبكراً يمنح Aspose فرصة لفحص كل مقطع نصي، نمط، وكائن مضمّن. إذا لم يُعثر على خط في النظام أو في مجلد الخطوط المخصص ستحصل على تحذير لاحقاً.

---

## الخطوة 2: ربط رد نداء التحذير لالتقاط أحداث الاستبدال

يستخدم Aspose.Words آلية رد نداء لإبلاغك بمشكلات مثل الخطوط المفقودة. من خلال تعيين تنفيذ `IWarningCallback` إلى `doc.WarningCallback`، يمكنك اعتراض كل تحذير عند حدوثه.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **نصيحة احترافية:** يمكنك ربط ردود نداء متعددة (مثل التسجيل، تحديث واجهة المستخدم) عبر نمط مركب، لكن لهذا الدرس يكفي رد نداء واحد لتبقى الأمور واضحة.

---

## الخطوة 3: تنفيذ رد نداء تحذير استبدال الخطوط

الآن نعرّف الفئة التي تقوم بالعمل الفعلي. يتلقى رد النداء كائن `WarningInfo`؛ نقوم بفلترة `WarningType.FontSubstitution` وتخزين الوصف لاستخدامه لاحقاً.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **ما يحدث:** عندما يصادف Aspose خطاً مفقوداً، ينشئ تحذيراً مثل “Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.” يقوم رد النداء بطباعة هذا السطر وحفظه.

---

## الخطوة 4: معالجة المستند (اختياري) وجمع الخطوط المفقودة

إذا كنت تحتاج فقط إلى **اكتشاف الخطوط المفقودة**، فإن خطوة التحميل تكفي—فالتنبيهات تُطلق تلقائياً. ومع ذلك، يحتاج العديد من المطورين إلى **استرجاع معلومات الخط المفقود** بعد تنفيذ بعض العمليات (مثل الحفظ أو التحويل). أدناه نجبر عملية صغيرة—حفظ إلى PDF—لضمان إصدار جميع التحذيرات، ثم نستخرج الرسائل المجمعة.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **الناتج المتوقع على الكونسول** (مثال):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

لاحظ كيف يوضح كل سطر الخط الأصلي والخط البديل الذي اختاره Aspose. هذا هو جوهر تقارير **استبدال الخطوط في Aspose**.

---

## الخطوة 5: متقدم – استخدام مصادر خطوط مخصصة لتقليل الاستبدالات

أحياناً تكون لديك الخطوط المفقودة، لكنها ليست في مجلد النظام الافتراضي. يتيح لك Aspose.Words الإشارة إلى دليل مخصص عبر `FontSettings`. إضافة هذه الخطوة يمكن أن تقلل بشكل كبير من عدد تحذيرات الاستبدال.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **لماذا نضيف هذا؟** إذا كنت توزع مستندات عبر أجهزة مختلفة، فإن تجميع الخطوط المطلوبة في مجلد معروف يضمن نفس المظهر البصري في كل مكان. كما يجعل روتين **اكتشاف الخطوط المفقودة** أكثر دقة لأن Aspose سيفحص ذلك المجلد قبل اللجوء إلى الخط البديل.

---

## مثال عملي كامل

نجمع كل ما سبق في برنامج كونسول جاهز للنسخ واللصق. احفظه باسم `Program.cs` وشغّله باستخدام `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**ما يجب أن تراه:** إذا كان ملف DOCX المصدر يشير إلى خطوط غير موجودة لديك، سيطبع الكونسول كل سطر استبدال متبوعاً بملخص مختصر. إذا كانت جميع الخطوط موجودة، ستحصل على رسالة “No missing fonts were detected.”.

---

## الأخطاء الشائعة وكيفية تجنّبها

| المشكلة | لماذا يحدث | الحل |
|---------|------------|------|
| **عدم ظهور أي تحذيرات** | المستند يستخدم خطوط النظام فقط، أو أضفت مجلدًا مخصصًا يحتوي على الخطوط المفقودة. | تأكد من أن ملف DOCX فعلاً يشير إلى خط غير متوفر. يمكنك فتحه في Word وتغيير فقرة إلى خط نادر (مثل “Papyrus”). |
| **تكرار الرسائل** | نفس الخط مستخدم في عدة مقاطع، مما ينتج تحذيرات متعددة. | احذف التكرارات باستخدام `Distinct()` إذا كنت تحتاج فقط إلى مجموعة فريدة. |
| **بطء الأداء على المستندات الكبيرة** | كل تحذير يُعالج على خيط الواجهة. | نفّذ التحميل في مهمة خلفية أو استخدم `Parallel.ForEach` للمعالجة اللاحقة. |
| **خط بديل غير مناسب** | الاستبدال الافتراضي في Aspose قد لا يتوافق مع هوية علامتك التجارية. | عيّن `FontSettings.SubstitutionSettings.DefaultFontName` إلى خط بديل مفضّل (مثل “Calibri”). |

---

## توسيع الحل – تصدير الخطوط المفقودة إلى JSON

إذا كنت تبني خدمة ويب تحتاج لإبلاغ الخطوط المفقودة للعميل، فإن تسلسل القائمة إلى JSON سهل جداً:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

الآن يمكن لواجهة API الخاصة بك إرجاع حمولة JSON نظيفة يمكن لنظام آخر استهلاكها.

---

## الخاتمة

في هذا الدليل استعرضنا **استبدال الخطوط في Aspose** من البداية إلى النهاية: تحميل مستند Word، ربط رد نداء التحذير، التقاط كل حدث *اكتشاف خطوط مفقودة*، وأخيراً **استرجاع معلومات الخط المفقود** للتقارير أو الإصلاح. بإضافة مجلد خطوط مخصص يمكنك تقليل عدد الاستبدالات، ومع بضع أسطر إضافية يمكنك حتى تصدير النتائج كملف JSON.

تذكر أن سلامة المظهر البصري لمستنداتك تعتمد على الخطوط المستخدمة. باستخدام التقنية الموضحة هنا، لن تُفاجأ أبداً بخط بديل غير متوقع مرة أخرى.  

هل أنت مستعد للخطوة التالية؟ جرّب دمج هذه المنطق في خط أنابيب معالجة مستندات أكبر، أو استكشف ميزات أخرى في Aspose.Words مثل تضمين الخطوط (`doc.FontSettings.EmbeddedFonts`). الاحتمالات لا حصر لها، ومستخدموك سيشكرونك على المخرجات المصقولة.

---

![لقطة شاشة ل

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}