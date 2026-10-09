---
category: general
date: 2026-03-19
description: تعلم كيفية التقاط التحذيرات في Aspose.Words، وضبط إعدادات الخط الافتراضية،
  واكتشاف الخطوط المفقودة عند تحميل مستند Word.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: ar
og_description: كيفية التقاط التحذيرات في Aspose.Words، وتعيين إعدادات الخط الافتراضية،
  واكتشاف الخطوط المفقودة عند تحميل مستند Word.
og_title: كيفية التقاط التحذيرات – ضبط إعدادات الخط الافتراضية
tags:
- Aspose.Words
- C#
- Document Processing
title: كيفية التقاط التحذيرات – ضبط إعدادات الخط الافتراضية
url: /ar/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية التقاط التحذيرات – تعيين إعدادات الخط الافتراضية

**كيفية التقاط التحذيرات** هي حاجة شائعة عندما تعمل مع Aspose.Words، خاصة إذا كانت مستنداتك تعتمد على خطوط محددة قد لا تكون موجودة على الجهاز الهدف. هل فتحت ملف DOCX وتساءلت لماذا يبدو التخطيط غير صحيح؟ الجواب غالبًا ما يكون مخفيًا في تحذير حول خط مفقود.  

في هذا الدليل سنستعرض **كيفية التقاط التحذيرات** أثناء **تحميل مستند Word**، وتكوين **تعيين إعدادات الخط الافتراضية**، وأخيرًا **اكتشاف الخطوط المفقودة** حتى تتمكن من التعامل معها برمجيًا. لا إطالة—مجرد مثال كامل قابل للتنفيذ مع شرح كل سطر.

> *نصيحة محترف:* التقاط التحذيرات مبكرًا يوفر عليك وقتًا في تصحيح الأخطاء الغامضة في التخطيط لاحقًا.

---

## ما ستحتاجه

- **Aspose.Words for .NET** (أحدث نسخة حتى عام 2026).  
- بيئة تطوير .NET (Visual Studio، Rider، أو VS Code).  
- ملف DOCX تجريبي يشير إلى خط **ليس** مثبتًا لديك (مثال: *Comic Sans MS* على نظام Linux).  

هذا كل ما تحتاجه. لا توجد حزم NuGet إضافية مطلوبة بخلاف Aspose.Words.

---

## الخطوة 1 – فهم لماذا تحتاج إلى التقاط التحذيرات

عند قيام Aspose.Words بتحليل مستند، قد يصادف خطوطًا غير متوفرة على الجهاز المضيف. بشكل افتراضي، تستبدل المكتبة الخط المفقود بخط احتياطي بصمت، مما قد يغيّر فواصل الأسطر، والمسافات، وحتى يؤدي إلى اختفاء النص.  

استخدام **WarningCallback** مع كائن **FontSettings** يمنحك أمرين:

1. **الرؤية** – تحصل على إدخال `WarningInfo` لكل استبدال.  
2. **التحكم** – يمكنك تهيئة خط افتراضي مسبقًا لتقليل المفاجآت البصرية.

فكر فيها كأنك تثبت “مراقبًا” يصرخ في كل مرة يبدل فيها المحرك جزءًا تحت الغطاء.

---

## الخطوة 2 – تعيين إعدادات الخط الافتراضية

الكلمة المفتاحية الثانوية الأولى، **set default font settings**، تظهر هنا. تقوم بإنشاء نسخة من `FontSettings` وتوجهها اختياريًا إلى مجلد يحتوي على خطوطك الاحتياطية.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **لماذا؟**  
> إذا لم تحدد خطًا احتياطيًا، يختار Aspose.Words أول خط نظام يطابق النمط، وقد يكون مختلفًا تمامًا. بتعيين خط افتراضي معروف، تضمن عرضًا متسقًا عبر الأجهزة.

---

## الخطوة 3 – إعداد Callback للتحذيرات لالتقاط التحذيرات

الآن سنوضح **كيفية التقاط التحذيرات** عن طريق ربط `WarningInfoCollection` بخيارات التحميل. ستخزن هذه المجموعة كل تحذير يُصدر أثناء عملية التحميل.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

تُنفّذ `WarningInfoCollection` الواجهة `IWarningCallback`، لذا يقوم Aspose.Words تلقائيًا بدفع كل تحذير إلى `warningInfos`. لا حاجة للاستطلاع.

---

## الخطوة 4 – تحميل مستند Word مع الخيارات المكوَّنة

هنا يبرز الكلمة المفتاحية الثانوية الثانية، **load word document**. نمرر كلًا من `FontSettings` و `WarningCallback` عبر كائن `LoadOptions`.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

إذا كان المستند يشير إلى خط غير مثبت، سيلتقط الـ callback تحذير من نوع `WarningType.FontSubstitution`.

---

## الخطوة 5 – اكتشاف الخطوط المفقودة من التحذيرات المجمعة

أخيرًا، نجيب على الكلمة المفتاحية الثانوية الثالثة، **detect missing fonts**، عبر التكرار على التحذيرات المجمعة.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

المخرجات النموذجية تكون كالتالي:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

هذا السطر يخبرك بالضبط أي خط مفقود وأي خط احتياطي تم استخدامه—معلومات يمكنك تسجيلها، عرضها للمستخدم، أو حتى تشغيل روتين تثبيت خط مخصص.

---

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه في تطبيق Console. يوضح **كيفية التقاط التحذيرات**، **تعيين إعدادات الخط الافتراضية**، **تحميل مستند Word**، و**اكتشاف الخطوط المفقودة** في تدفق واحد.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**النتيجة المتوقعة:** عندما يشير الـ DOCX المحدد إلى خط غير مثبت، يطبع الـ Console تحذيرًا لكل استبدال. إذا كانت جميع الخطوط موجودة، لا ينتج أي إخراج من الحلقة.

---

## الأخطاء الشائعة وحالات الحافة

| الحالة | لماذا يحدث | كيفية التعامل |
|-----------|----------------|------------------|
| **لا تظهر تحذيرات** رغم أن التخطيط يبدو خاطئًا | قد يستخدم المستند خطوطًا *مضمنة*، والتي يعرضها Aspose.Words دون استبدال. | تحقق من `Document.HasEmbeddedFonts` وفكّ الخطوط المضمنة إذا احتجتها على جهاز آخر. |
| **تحذيرات متعددة للـ | 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}