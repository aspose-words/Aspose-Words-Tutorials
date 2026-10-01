---
category: general
date: 2026-02-26
description: معالجة الخطوط المفقودة في C# باستخدام Aspose.Words. تعلّم كيفية التقاط
  تحذيرات استبدال الخطوط، تنفيذ IWarningCallback، والحفاظ على مظهر مستنداتك بشكل صحيح.
draft: false
keywords:
- handle missing fonts
- Aspose.Words font warning
- C# LoadOptions
- IWarningCallback implementation
- document loading with missing fonts
- font substitution handling
language: ar
og_description: تعامل مع الخطوط المفقودة في C# بسرعة. يوضح هذا الدليل كيفية التقاط
  تحذيرات استبدال الخطوط باستخدام Aspose.Words، وتنفيذ IWarningCallback، والتحقق من
  النتائج.
og_title: معالجة الخطوط المفقودة في C# – دليل Aspose.Words خطوة بخطوة
tags:
- Aspose.Words
- C#
- Document Processing
title: معالجة الخطوط المفقودة في C# باستخدام Aspose.Words – دليل شامل
url: /ar/net/working-with-fonts/handle-missing-fonts-in-c-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# التعامل مع الخطوط المفقودة في C# باستخدام Aspose.Words – دليل شامل

هل احتجت يومًا إلى **معالجة الخطوط المفقودة** عند تحميل مستند Word في C# وتساءلت لماذا يبدو الناتج غريبًا؟ لست وحدك. عندما يشير ملف المصدر إلى خط غير مثبت على الجهاز، يقوم Aspose.Words باستبداله بصمت بآخر، مما قد يخل بتنسيقك أو علامتك التجارية.  

الخبر السار؟ من خلال ربط **دالة رد نداء التحذير**، يمكنك التقاط كل حدث استبدال للخط، تسجيله، وتحديد ما إذا كنت ستوفر بديلاً. في هذا الدرس سنستعرض العملية بالكامل—من إعداد المشروع إلى التحقق من مخرجات الكونسول—حتى لا تُفاجأ بخط غير مرئي مرة أخرى.

> **ما ستحصل عليه**: تطبيق C# Console جاهز للتنفيذ يُبلغ عن كل خط مفقود، يوضح سبب ظهور التحذير، ويظهر لك كيفية توسيع المعالج لمنطق مخصص.

---

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل على .NET Core و .NET Framework على حد سواء)
- Visual Studio 2022 (أو أي بيئة تطوير C# تفضلها)
- **رخصة** لـ Aspose.Words for .NET (الإصدار التجريبي المجاني يكفي للاختبار)
- مستند Word يحتوي على خط غير مثبت لديك (مثال: *Comic Sans MS* على نظام Linux)

إذا كان لديك كل ذلك، لنبدأ.

---

## الخطوة 1: إنشاء مشروع Console جديد وإضافة Aspose.Words

للحفاظ على التنظيم، ابدأ بمشروع Console جديد.

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
dotnet add package Aspose.Words
```

> **نصيحة احترافية**: استخدم العلامة `--framework net6.0` إذا أردت استهداف نسخة تشغيل محددة.

هذا سيجلب أحدث حزمة NuGet لـ Aspose.Words، التي تحتوي على النوعين `LoadOptions` و `IWarningCallback` اللذين سنحتاجهما.

---

## الخطوة 2: تنفيذ معالج التحذير (IWarningCallback)

يقوم Aspose.Words بإصدار كائن `WarningInfo` لكل مشكلة غير حرجة يواجهها أثناء تحميل المستند. من خلال تنفيذ `IWarningCallback`، تحدد ما ستفعله بهذه التحذيرات.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

public class FontWarningHandler : IWarningCallback
{
    // This method is called automatically by Aspose.Words whenever a warning occurs.
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property contains the name of the missing font and the substitute used.
            Console.WriteLine($"⚠️ Missing font detected: {info.Description}");
        }
        // You could also log other warning types here if you wish.
    }
}
```

**لماذا هذا مهم**: بدون معالج، يتم تجاهل تحذيرات استبدال الخطوص بصمت. بطباعة هذه التحذيرات، ستحصل على رؤية فورية للخطوط المفقودة وما استبدله Aspose.Words.

---

## الخطوة 3: ضبط LoadOptions مع رد نداء التحذير

الآن نربط المعالج بعملية تحميل المستند. يتيح لك `LoadOptions` توصيل رد النداء قبل أن يتم تحليل الملف.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Tell Aspose.Words to use our FontWarningHandler.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // 2️⃣ Path to the Word file that contains missing fonts.
        string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

        // 3️⃣ Load the document with the custom options.
        Document doc = new Document(docPath, loadOptions);

        // At this point, any font‑substitution warning has already been printed.
        Console.WriteLine("✅ Document loaded successfully.");
    }
}
```

> **ملاحظة**: استبدل `YOUR_DIRECTORY` بالمجلد الفعلي الذي يحتوي على ملف `.docx` التجريبي. يجب تمرير كائن `LoadOptions` إلى مُنشئ `Document`؛ وإلا سيُطبق السلوك الصامت الافتراضي.

---

## الخطوة 4: تشغيل التطبيق والتحقق من المخرجات

قم بإنشاء (Compile) وتشغيل التطبيق:

```bash
dotnet run
```

إذا كان المستند يشير إلى خط غير موجود على جهازك (مثلاً *Papyrus*)، سترى شيئًا مشابهًا لـ:

```
⚠️ Missing font detected: The font 'Papyrus' was not found. Using 'Times New Roman' as a substitute.
✅ Document loaded successfully.
```

هذا السطر الواحد يخبرك بالضبط أي خط مفقود وأي بديل اختاره Aspose.Words. الآن يمكنك إما تضمين الخط المفقود، تعديل المستند الأصلي، أو قبول الاستبدال.

---

## الخطوة 5: متقدم – جمع التحذيرات للاستخدام لاحقًا

أحيانًا ترغب في تخزين التحذيرات بدلاً من طباعتها فورًا. فيما يلي تعديل سريع للمعالج يجمع الرسائل في قائمة.

```csharp
using System.Collections.Generic;

public class FontWarningCollector : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string msg = $"Missing font: {info.Description}";
            Messages.Add(msg);
        }
    }
}
```

وقم بتحديث `Main` وفقًا لذلك:

```csharp
static void Main()
{
    var collector = new FontWarningCollector();

    LoadOptions lo = new LoadOptions { WarningCallback = collector };
    Document doc = new Document(@"YOUR_DIRECTORY\DocumentWithMissingFont.docx", lo);

    Console.WriteLine("✅ Document loaded.");
    if (collector.Messages.Count > 0)
    {
        Console.WriteLine("\n--- Font Substitution Report ---");
        foreach (var m in collector.Messages)
            Console.WriteLine(m);
    }
}
```

الآن لديك قائمة قابلة لإعادة الاستخدام يمكنك كتابتها إلى ملف سجل، إرسالها إلى خدمة مراقبة، أو عرضها في واجهة مستخدم.

---

## الخطوة 6: الأخطاء الشائعة وكيفية تجنّبها

| المشكلة | السبب | الحل |
|-------|----------------|-----|
| **عدم ظهور أي تحذيرات** | لم يتم ربط رد النداء، أو تم تحميل المستند بدون `LoadOptions`. | تأكد من ضبط `LoadOptions.WarningCallback` **قبل** استدعاء مُنشئ `Document`. |
| **اسم الخط غير صحيح في الرسالة** | بعض الخطوط مضمَّنة في المستند؛ Aspose.Words يُبلغ عن الاسم *الأصلي*، وليس المضمَّن. | تحقق من مراجع الخط في الملف الأصلي؛ تضمين الخطوط يزيل التحذير تمامًا. |
| **تأثير الأداء** | جمع التحذيرات لآلاف المستندات قد يضيف عبئًا. | استخدم `Console.WriteLine` للتصحيح السريع؛ وانتقل إلى المجمع فقط عندما تحتاج إلى البيانات. |

---

## ملخص بصري

![Handle missing fonts illustration showing warning callback flow](/images/handle-missing-fonts.png "Diagram of handling missing fonts with Aspose.Words")

*يوضح المخطط (النص البديل يتضمن الكلمة المفتاحية الأساسية) كيفية اعتراض رد نداء التحذير لأحداث استبدال الخط أثناء تحميل المستند.*

---

## الخاتمة

أنت الآن تعرف **كيفية التعامل مع الخطوط المفقودة** في C# باستخدام Aspose.Words. من خلال ربط `IWarningCallback` داخل `LoadOptions`، تحصل على رؤية كاملة لكل حدث استبدال للخط، يمكنك تسجيله أو اتخاذ إجراء بناءً عليه، وتضمن في النهاية أن المستندات التي تُنشئها تحتفظ بالمظهر والوظيفة المقصودة.

> **ملخص سريع**:  
> 1. أضف Aspose.Words إلى تطبيق Console.  
> 2. نفّذ `FontWarningHandler` (أو مجمع).  
> 3. مرره عبر `LoadOptions` عند تحميل المستند.  
> 4. تحقق من مخرجات الكونسول أو التحذيرات المخزنة.  

من هنا يمكنك استكشاف **تضمين الخطوط المفقودة** (`FontSettings.SubstitutionSettings`) أو **تحميلها تلقائيًا من خادم خطوط الشركة**—كلاهما توسعات طبيعية للنمط الذي بنيناه.

هل لديك أسئلة إضافية حول **تحذير خطوط Aspose.Words**، **LoadOptions في C#**، أو **تحميل المستندات مع خطوط مفقودة**؟ اترك تعليقًا، وتمنياتنا لك ببرمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}