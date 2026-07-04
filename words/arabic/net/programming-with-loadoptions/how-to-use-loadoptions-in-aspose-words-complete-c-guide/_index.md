---
category: general
date: 2026-04-10
description: كيفية استخدام LoadOptions في Aspose.Words لالتقاط تحذيرات استبدال الخطوط
  أثناء تحميل المستندات. تعلّم حلاً خطوة بخطوة بلغة C# مع مثال كامل للكود.
draft: false
keywords:
- how to use loadoptions
- warningcallback
- font substitution warning
- aspose.words loadoptions example
- c# document loading
language: ar
og_description: كيفية استخدام LoadOptions في Aspose.Words لالتقاط تحذيرات استبدال
  الخطوط أثناء تحميل المستندات. يوضح هذا الدليل تنفيذًا كاملاً بلغة C#.
og_title: كيفية استخدام LoadOptions في Aspose.Words – دليل C# الكامل
tags:
- Aspose.Words
- C#
- Document Processing
- Font Management
title: كيفية استخدام LoadOptions في Aspose.Words – دليل C# الكامل
url: /ar/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية استخدام LoadOptions في Aspose.Words – دليل C# كامل

استخدام LoadOptions في Aspose.Words يُعدّ عائقًا شائعًا عندما تحتاج إلى تحكم دقيق في تحميل المستندات. في هذا الدرس سنُظهر لك بالضبط **كيفية استخدام LoadOptions** لالتقاط تحذيرات استبدال الخطوط والرد عليها في C#.  

إذا فتحت ملف DOCX يُشير إلى خط مفقود وتساءلت لماذا يبدو الناتج غريبًا، فأنت في المكان الصحيح. سنستعرض العملية بالكامل، من إنشاء كائن `LoadOptions` إلى طباعة تفاصيل التحذير على وحدة التحكم. في النهاية ستحصل على مقطع جاهز للتنفيذ يمكنك إدراجه في أي مشروع .NET.

## ما ستتعلمه

- لماذا تُعد `LoadOptions` مهمة لاستيراد المستندات بشكل موثوق.  
- كيفية ربط **WarningCallback** يراقب تحديدًا **تحذيرات استبدال الخطوط**.  
- الشيفرة الدقيقة اللازمة لتحميل ملف Word مع تمكين هذه الخيارات.  
- نصائح للتعامل مع الحالات الخاصة، مثل المستندات التي تحتوي على خطوط مفقودة متعددة.  

لا تحتاج إلى وثائق خارجية—كل ما تحتاجه موجود هنا.

## المتطلبات المسبقة

| المتطلب | السبب |
|-------------|--------|
| .NET 6.0 أو أحدث | يوفر بيئة تشغيل لـ C# 10 المستخدمة في الأمثلة. |
| Aspose.Words for .NET (أحدث نسخة) | المكتبة التي تحتوي على `LoadOptions` وبنية التحذير. |
| ملف DOCX قد يُشير إلى خطوط غير مثبتة لديك | لرؤية استدعاء التحذير قيد التنفيذ. |
| Visual Studio 2022 (أو أي بيئة تطوير تفضّلها) | يجعل عملية التصحيح والاختبار سهلة. |

إذا كان لديك هذه المتطلبات، رائع—لنبدأ.

## الخطوة 1 – إنشاء كائن LoadOptions وربط WarningCallback

أول شيء تقوم به عندما **تريد معرفة كيفية استخدام LoadOptions** هو إنشاءه. الجزء الحاسم هو تعيين مُفوض إلى `WarningCallback`. هذا المُفوض يُطلق كلما واجهت Aspose.Words حالة تريد إبلاغك بها—وخاصةً الخط المفقود.

```csharp
using System;
using Aspose.Words;

// Step 1: Build LoadOptions with a warning listener.
LoadOptions loadOptions = new LoadOptions
{
    // The lambda receives the sender (unused) and a WarningInfo object.
    WarningCallback = (sender, args) =>
    {
        // We'll filter for font‑substitution warnings later.
        if (args.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        }
    }
};
```

**لماذا هذا مهم:** بدون استدعاء التحذير، تقوم Aspose.Words بتبديل الخطوط المفقودة بخطوط افتراضية بصمت، وقد لا تلاحظ التحول البصري. عبر تسجيل `WarningCallback`، تحصل على سجل لحظي لكل استبدال، وهو أمر أساسي لسلاسل معالجة المستندات المضمونة الجودة.

## الخطوة 2 – الرد فقط على تحذيرات استبدال الخطوط

قد تتساءل إذا ما كان الاستدعاء سيغمرّك بتحذيرات غير ذات صلة (مثل الميزات المُهملة). الجواب *نعم*—لكن يمكننا تصفيتها. في المقتطف أعلاه نتحقق بالفعل من `args.WarningType == WarningType.FontSubstitution`. هذا السطر هو **حارس تحذير استبدال الخط**، كلمة مفتاحية ثانوية تُبقي المخرجات مركّزة.

إذا احتجت يومًا إلى معالجة أنواع تحذير أخرى، فقط وسّع كتلة `if`:

```csharp
if (args.WarningType == WarningType.FontSubstitution)
{
    // Existing handling…
}
else if (args.WarningType == WarningType.UnknownFileFormat)
{
    Console.WriteLine($"❓ Unknown format: {args.Description}");
}
```

هذا النمط يُظهر مدى مرونة آلية **warningcallback**، مما يتيح لك تخصيص الاستجابات للسيناريوهات التي تهمك بالضبط.

## الخطوة 3 – تحميل المستند باستخدام LoadOptions المُكوَّنة

الآن بعد أن أصبح المستمع جاهزًا، الجزء الأخير هو تمرير كائن `LoadOptions` إلى مُنشئ `Document`. هذه هي اللحظة التي يبرز فيها **مثال Aspose.Words LoadOptions** حقًا.

```csharp
// Step 3: Load the DOCX while the warning callback is active.
try
{
    Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    Console.WriteLine("✅ Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"🚨 Failed to load document: {ex.Message}");
}
```

**ما ستراه:** إذا كان ملف DOCX يُشير إلى خط غير مثبت على الجهاز، ستظهر سطر في وحدة التحكم مثل:

```
⚠️ Font substitution: Font 'Calibri Light' has been substituted with 'Arial'.
✅ Document loaded successfully.
```

هذا الإخراج يؤكد أنك نجحت في **كيفية استخدام LoadOptions** لمراقبة مشاكل الخطوط.

## مثال كامل يعمل (جاهز للنسخ واللصق)

فيما يلي البرنامج الكامل الذي يمكنك تجميعه وتشغيله فورًا. يجمع بين الخطوات الثلاث، ويضيف بعض اللمسات (مثل بانر ترحيبي)، ويظهر معالجة الأخطاء.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        Console.WriteLine("=== Aspose.Words LoadOptions Demo ===");

        // 1️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = (sender, args) =>
            {
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substitution: {args.Description}");
                }
            }
        };

        // 2️⃣ Attempt to load the document.
        try
        {
            // Replace the path with your own file that may contain missing fonts.
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            Console.WriteLine("✅ Document loaded without fatal errors.");

            // Optional: Do something with the document, e.g., save as PDF.
            // doc.Save("output.pdf");
        }
        catch (Exception e)
        {
            Console.WriteLine($"🚨 Error: {e.Message}");
        }

        Console.WriteLine("=== End of Demo ===");
    }
}
```

### المخرجات المتوقعة

تشغيل البرنامج على جهاز لا يحتوي على الخط المُشار إليه في `input.docx` ينتج شيء مشابه لـ:

```
=== Aspose.Words LoadOptions Demo ===
⚠️ Font substitution: Font 'Times New Roman' has been substituted with 'Arial'.
✅ Document loaded without fatal errors.
=== End of Demo ===
```

إذا كانت جميع الخطوط موجودة، سترى فقط رسائل النجاح—ولا تظهر سطور تحذير.

## الأخطاء الشائعة & نصائح احترافية

- **الخطأ:** نسيان تعيين `WarningCallback`. سيستمر الكود في التحميل، لكنك ستفوت تفاصيل الاستبدال.  
  **نصيحة احترافية:** عيّن الاستدعاء فور إنشاء `LoadOptions`؛ فهو بسيط ويُوفّر الكثير لاحقًا.

- **الخطأ:** استخدام مسار نسبي يشير إلى المجلد الخطأ.  
  **نصيحة احترافية:** استخدم `Path.Combine(Environment.CurrentDirectory, "input.docx")` للحصول على بحث ملفات أكثر موثوقية.

- **الخطأ:** الافتراض أن التحذير سيوقف التحميل.  
  **نصيحة احترافية:** تحذيرات استبدال الخطوط هي *تحذيرية*؛ لا تُوقف التحميل. إذا كنت تحتاج إلى تحقق أكثر صرامة، ارمِ استثناءً داخل الاستدعاء عند حدوث استبدال.

- **الخطأ:** تشغيل البرنامج على خادم لا يحتوي على أي خطوط مثبتة (مثل صورة Docker خفيفة).  
  **نصيحة احترافية:** قم بتثبيت الخطوط المطلوبة مسبقًا أو احزمها مع تطبيقك، ثم تحقق عبر الاستدعاء أن لا يحدث استبدال في بيئة الإنتاج.

## متى تستخدم LoadOptions مقابل الفحص بعد التحميل

قد تتساءل، “لماذا لا أقوم بفحص المستند بعد تحميله؟” الجواب يكمن في الأداء والصحة. عبر معالجة التحذيرات **أثناء** التحميل، تلتقط المشكلات مبكرًا—قبل أي حسابات تخطيط أو تحويل إلى PDF. هذا مهم بشكل خاص في خطوط معالجة الدُفعات حيث كل خطوة إضافية تضيف وقتًا.

## توسيع المثال: حفظ تقرير بجميع الخطوط المستبدلة

إذا كنت بحاجة إلى سجل دائم (ربما للامتثال)، عدّل الاستدعاء لجمع الرسائل في قائمة وكتابتها إلى ملف بعد التحميل:

```csharp
var substitutions = new List<string>();

loadOptions.WarningCallback = (s, a) =>
{
    if (a.WarningType == WarningType.FontSubstitution)
    {
        substitutions.Add(a.Description);
        Console.WriteLine($"⚠️ {a.Description}");
    }
};

// After loading:
File.WriteAllLines("font-substitutions.txt", substitutions);
```

الآن لديك كل من رد الفعل على وحدة التحكم وسجل ثابت.

## مواضيع ذات صلة قد تستكشفها لاحقًا

- **كيفية تضمين خطوط مخصصة في Aspose.Words** – يزيل الاستبدال تمامًا.  
- **استخدام LoadOptions لتحديد حجم المستند** – يساعد في الحماية من الملفات الضخمة الضارة.  
- **تحويل Word إلى PDF مع الحفاظ على الطباعة** – يتكامل بشكل جيد مع نهج استدعاء التحذير.  

كل من هذه المواضيع يبني على الأساس الذي أنشأته للتو باستخدام `LoadOptions`.

## الخلاصة

غطّينا **كيفية استخدام LoadOptions** في Aspose.Words من البداية إلى النهاية: أنشئ الخيارات، اربط `WarningCallback` الذي يركز على **تحذيرات استبدال الخطوط**، وحمّل المستند بثقة. المثال الكامل يعمل مباشرة، والنصائح الإضافية تساعدك على تجنّب الفخاخ الشائعة.  

لا تتردد في التجربة—استبدل الاستدعاء بأنواع تحذير أخرى، سجّله إلى قاعدة بيانات، أو دمج المنطق في خدمة ويب تتحقق من ملفات Word المرفوعة. النمط مرن، موثوق، والأهم أنه يمنحك رؤية واضحة للعملية الخفية لاستبدال الخطوط التي قد تُفسد عرض مستندك.

Happy coding, and may your documents always render exactly as intended! 

![مخطط يوضح تدفق استخدام LoadOptions مع استدعاء تحذير في Aspose.Words](https://example.com/images/loadoptions-flow.png "مخطط كيفية استخدام LoadOptions")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}