---
language: ar
url: /arabic/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# اكتشاف الخطوط المفقودة في مستندات Aspose.Words – دليل كامل بلغة C#

هل تساءلت يومًا كيف **تكتشف الخطوط المفقودة** عند تحميل ملف Word باستخدام Aspose.Words؟ في عملي اليومي، صادفت بعض ملفات PDF التي بدت غير صحيحة لأن المستند الأصلي استخدم خطًا لم يكن مثبتًا على جهازّي. الخبر السار؟ Aspose.Words يمكنه إخبارك بالضبط عندما يستبدل خطًا، ويمكنك التقاط هذه المعلومة عبر رد نداء تحذير بسيط.

في هذا الدرس سنستعرض **مثالًا كاملاً قابلاً للتنفيذ** يوضح لك كيفية تسجيل كل استبدال للخط، ولماذا يُعد رد النداء مهمًا، وبعض الحيل الإضافية لاكتشاف الخطوط المفقودة بشكل موثوق. لا إطالة، فقط الشيفرة والمنطق الذي تحتاجه لتجعلها تعمل اليوم.

---

## ما ستتعلمه

- كيفية تنفيذ **رد نداء تحذير Aspose.Words** لالتقاط أحداث استبدال الخط.  
- كيفية ضبط **LoadOptions في C#** بحيث يتم استدعاء رد النداء أثناء تحميل المستند.  
- كيفية التحقق من أن اكتشاف الخط المفقود قد نجح، وما هو شكل مخرجات وحدة التحكم.  
- تعديلات اختيارية للمعالجة على دفعات كبيرة أو في بيئات بدون واجهة رسومية.  

**المتطلبات المسبقة** – تحتاج إلى نسخة حديثة من Aspose.Words for .NET (تم اختبار الشيفرة مع الإصدار 23.12)، .NET 6 أو أحدث، وفهم أساسي للغة C#. إذا كان لديك ذلك، فأنت جاهز للبدء.

---

## اكتشاف الخطوط المفقودة عبر رد نداء التحذير

جوهر الحل هو تنفيذ `IWarningCallback`. تقوم Aspose.Words بإطلاق كائن `WarningInfo` للعديد من الحالات، لكننا نهتم فقط بـ `WarningType.FontSubstitution`. دعنا نرى كيف نربط ذلك.

### الخطوة 1: إنشاء جامع تحذيرات الخطوط

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*لماذا هذا مهم*: من خلال تصفية `WarningType.FontSubstitution` نتجنب الفوضى الناتجة عن التحذيرات غير ذات الصلة (مثل الميزات المهجورة). يحتوي `info.Description` بالفعل على اسم الخط الأصلي والبديل المستخدم، مما يمنحك سجلًا واضحًا.

---

## ضبط LoadOptions لاستخدام رد النداء

الآن نخبر Aspose.Words باستخدام جامعنا عند تحميل ملف.

### الخطوة 2: إعداد LoadOptions

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*لماذا هذا مهم*: `LoadOptions` هو المكان الوحيد الذي يمكنك فيه توصيل رد النداء، كلمات مرور التشفير، وسلوكيات التحميل الأخرى. إبقاء ذلك منفصلًا عن مُنشئ `Document` يجعل الشيفرة قابلة لإعادة الاستخدام عبر ملفات متعددة.

---

## تحميل المستند والتقاط الخطوط المفقودة

مع ربط رد النداء، الخطوة التالية هي ببساطة تحميل المستند.

### الخطوة 3: تحميل ملف DOCX (أو أي تنسيق مدعوم)

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

عند قيام مُنشئ `Document` بتحليل الملف، أي خط مفقود سيُفعّل `FontWarningCollector` الخاص بنا. ستظهر سطر في وحدة التحكم مثل:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

هذا السطر هو الدليل الملموس على أن **اكتشاف الخطوط المفقودة** قد نجح.

---

## التحقق من المخرجات – ما المتوقع

شغّل البرنامج من الطرفية أو من Visual Studio. إذا كان المستند الأصلي يحتوي على خط غير مثبت لديك، سترى على الأقل سطرًا واحدًا من “Font substituted”. إذا كان المستند يستخدم خطوطًا مثبتة فقط، سيبقى رد النداء صامتًا وستظهر لك رسالة “Document loaded successfully.” فقط.

**نصيحة**: لتتأكد مرة أخرى، افتح ملف Word في Microsoft Word وانظر إلى قائمة الخطوط. أي خط يظهر في *Replace Fonts* ضمن مجموعة *Home → Font* هو مرشح محتمل للاستبدال.

---

## متقدم: اكتشاف الخطوط المفقودة على نطاق واسع

غالبًا ما تحتاج إلى فحص العشرات من الملفات. النمط نفسه يتوسع بسهولة:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

نظرًا لأن `FontWarningCollector` يكتب إلى وحدة التحكم في كل مرة يُستدعى فيها، ستحصل على تقرير لكل ملف دون أي تعقيدات إضافية. في سيناريوهات الإنتاج قد ترغب في تسجيل النتائج إلى ملف أو قاعدة بيانات – ما عليك سوى استبدال `Console.WriteLine` بمسجلك المفضل.

---

## الأخطاء الشائعة & النصائح الاحترافية

| المشكلة | لماذا يحدث | الحل |
|-------|----------------|-----|
| **عدم ظهور أي تحذيرات** | المستند في الواقع يحتوي فقط على خطوط مثبتة. | تحقق بفتح الملف في Word أو بإزالة خط عمدًا من نظامك. |
| **عدم استدعاء رد النداء** | لم يتم تعيين `LoadOptions.WarningCallback` أو تم استخدام كائن `LoadOptions` جديد لاحقًا. | احتفظ بكائن `LoadOptions` واحد وأعد استخدامه لكل عملية تحميل. |
| **الكثير من التحذيرات غير ذات صلة** | لم تقم بتصفية `WarningType.FontSubstitution`. | أضف شرط `if (info.Type == WarningType.FontSubstitution)` كما هو موضح. |
| **تباطؤ الأداء على ملفات ضخمة** | يعمل رد النداء على كل تحذير، وقد يكون عددها كبيرًا في المستندات الكبيرة. | عطل أنواع التحذيرات الأخرى عبر `LoadOptions.WarningCallback` أو حدد `LoadOptions.LoadFormat` لنوع محدد إذا كنت تعرفه. |

---

## مثال كامل جاهز للنسخ واللصق

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**مخرجات وحدة التحكم المتوقعة** (عند مواجهة خط مفقود):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

إذا لم يحدث استبدال، سترى فقط سطر النجاح.

---

## الخلاصة

أصبح لديك الآن **طريقة كاملة وجاهزة للإنتاج لاكتشاف الخطوط المفقودة** في أي مستند يعالجه Aspose.Words. من خلال الاستفادة من **رد نداء التحذير في Aspose.Words** وضبط **LoadOptions في C#**، يمكنك تسجيل كل استبدال للخط، حل مشاكل التخطيط، وضمان أن ملفات PDF تحتفظ بالمظهر المقصود.

من ملف واحد إلى دفعة ضخمة، يبقى النمط هو نفسه—نفّذ `IWarningCallback`، اربطه بـ `LoadOptions`، ودع Aspose.Words يتولى الجزء الصعب.

هل أنت مستعد للخطوة التالية؟ جرّب دمج هذا مع **تضمين الخطوط** أو **عائلات الخطوط الاحتياطية** لإصلاح المشكلة تلقائيًا، أو استكشف واجهة **DocumentVisitor** لتحليل أعمق للمحتوى. برمجة سعيدة، ولتظل خطوطك دائمًا في مكانها المتوقع!

---

![Detect missing fonts in Aspose.Words – console output screenshot](https://example.com/images/detect-missing-fonts.png "detect missing fonts console output")

{{< layout-end >}}

{{< layout-end >}}