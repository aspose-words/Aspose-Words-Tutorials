---
category: general
date: 2026-01-06
description: تعلم كيفية الحصول على التحذيرات أثناء تحميل المستندات وكيفية مراقبة الخطوط
  باستخدام Aspose.Words. يغطي هذا الدليل ردود النداء للتحذيرات وتتبع استبدال الخطوط.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: ar
og_description: كيف تحصل على التحذيرات في Aspose.Words؟ اتبع هذا الدليل خطوة بخطوة
  لمراقبة الخطوط والتقاط رسائل الاستبدال أثناء تحميل المستندات.
og_title: كيفية الحصول على التحذيرات في Aspose.Words – مراقبة الخطوط
tags:
- Aspose.Words
- C#
- Font Monitoring
title: كيفية الحصول على التحذيرات في Aspose.Words – مراقبة الخطوط في C#
url: /ar/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية الحصول على التحذيرات في Aspose.Words – مراقبة الخطوط في C#

هل تساءلت يومًا **كيف تحصل على تحذيرات** عندما يحتوي مستند Word على خطوط غير مثبتة على جهازك؟ هذه مشكلة شائعة—تقوم تطبيقك بتبديل الخطوط المفقودة بصمت، ولا تعرف ما تم تغييره. الخبر السار هو أنه يمكنك ربط نظام التحذير في Aspose.Words و**مراقبة الخطوط** في الوقت الفعلي.

في هذا الدرس سنوضح لك بالضبط كيفية التقاط تحذيرات استبدال الخطوط، ولماذا هذا مهم، وماذا تفعل بالمعلومات بمجرد حصولك عليها. لا مستندات خارجية، مجرد مثال كامل قابل للتنفيذ يمكنك لصقه في Visual Studio الآن.

> **نصيحة احترافية:** إذا كنت تبني خط أنابيب تحويل مستندات، فإن تسجيل الخطوط المفقودة مبكرًا يوفر عليك مفاجآت تخطيطية غير سارة في المراحل اللاحقة.

---

## ما ستحتاجه

- **Aspose.Words for .NET** (أحدث نسخة؛ لم يتغير الـ API منذ الإصدار v23.10)
- بيئة تطوير .NET (Visual Studio، Rider، أو VS Code مع امتداد C#)
- ملف `.docx` تجريبي يحتوي على خط غير مثبت لديك (مثلاً **“NonExistentFont”**)

هذا كل ما تحتاجه—لا حزم NuGet إضافية بخلاف Aspose.Words.

---

## الخطوة 1 – إعداد جامع التحذيرات (الكلمة المفتاحية الأساسية في العنوان)

أول شيء تحتاجه هو مكان لتخزين التحذيرات عند حدوثها. توفر Aspose.Words الخاصية `WarningCallback` على `LoadOptions` لهذا الغرض بالضبط.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**لماذا هذا مهم:**  
عندما تواجه المكتبة خطًا مفقودًا، لا ترمي استثناءً؛ بل تُصدر كائن `WarningInfo`. من خلال ربط جامع، تحصل على رؤية كاملة لكل حدث استبدال، مما يتيح لك **مراقبة الخطوط** دون إغراق وحدة التحكم برسائل غير ذات صلة.

---

## الخطوة 2 – تحميل المستند مع خيارات التحذير المفعلة

الآن نقرأ الملف فعليًا. تضمن `LoadOptions` التي أعددناها في الخطوة السابقة أن أي تحذيرات متعلقة بالخطوط تُلتقط.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**ما الذي يحدث خلف الكواليس؟**  
يقوم Aspose.Words بتحليل ملف Word، ويحل الخطوط، وعندما لا يستطيع العثور على خط مطلوب، يلجأ إلى بديل (عادةً Arial). يُطلق هذا البديل تحذير `WarningType.FontSubstitution`، والذي يُسجل في `warningCollector`.

---

## الخطوة 3 – فحص التحذيرات المجمعة (تظهر الكلمة المفتاحية الأساسية مرة أخرى)

بعد تحميل المستند، نقوم ببساطة بالتكرار على `warningCollector` وطباعة أي رسائل استبدال خطوط.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**الناتج المتوقع** (بافتراض أن الخط المفقود هو *“FancyScript”*):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

إذا كان المستند يحتوي على خطوط غير معروفة متعددة، سترى سطرًا واحدًا لكل استبدال—مثالي للتسجيل أو التنبيه.

---

## الخطوة 4 – اختياري: تسجيل أو حفظ معلومات التحذير

في بيئة الإنتاج ربما تريد أكثر من `Console.WriteLine`. إليك مثال سريع يكتب التحذيرات إلى ملف JSON للتحليل لاحقًا.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

الآن لديك سجل دائم يمكنك إحالته إلى لوحة مراقبة، أو حتى تشغيل طلب تلقائي للحصول على ملفات الخطوط المفقودة.

---

## الخطوة 5 – التحقق من النتيجة والتنظيف

شغّل البرنامج. إذا رأيت رسائل الاستبدال، فقد نجحت في **الحصول على التحذيرات** وأنت الآن **تراقب الخطوط** بنشاط. إذا لم يظهر شيء، تحقق مرة أخرى من أن المستند التجريبي فعلاً يشير إلى خط غير مثبت على الجهاز.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

عدد الصفر عادةً يعني إما:

1. تم حل جميع الخطوط (ربما الخط *موجود* محليًا)، أو
2. المستند لم يحتوي على أي مراجع خطوط تحتاج إلى استبدال.

---

## الأخطاء الشائعة وكيفية تجنبها

| الخطأ | السبب | الحل |
|-------|-------|------|
| **لا تظهر أي تحذيرات** | الخط موجود فعليًا على النظام، أو المستند يستخدم خطوطًا مدمجة فقط. | غيّر اسم الخط في الملف المصدر إلى شيء مستحيل (مثلاً `XYZ123`) وجرب مرة أخرى. |
| **عدد كبير من التحذيرات (ضوضاء)** | تقوم بتحميل مستندات متعددة في حلقة دون مسح الجامع. | أعد إنشاء `WarningInfoCollection` لكل مستند، أو استدعِ `warningCollector.Clear()` بعد المعالجة. |
| **تأثير على الأداء** | التسجيل المفرط على القرص يمكن أن يبطئ المعالجة الدفعية. | خزن التحذيرات في الذاكرة واكتبها دفعة واحدة، أو استخدم I/O غير متزامن. |
| **غياب `using Aspose.Words.Loading;`** | فئة `LoadOptions` موجودة في هذا النطاق. | أضف توجيه `using` المفقود كما هو موضح في الخطوة 1. |

---

## توسيع الحل – مراقبة أنواع تحذيرات أخرى

بينما استبدال الخط هو الأكثر وضوحًا، يمكن لـ Aspose.Words إصدار تحذيرات لـ:

- **ميزات مهجورة** (`WarningType.Deprecated`),
- **فقدان محتمل للبيانات** (`WarningType.DataLoss`),
- **صيغ ملفات غير مدعومة** (`WarningType.UnsupportedFileFormat`).

يمكنك توسيع الفلتر في الخطوة 3 لالتقاط هذه أيضًا:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

بهذه الطريقة لن تكون فقط **كيف تراقب الخطوط** بل أيضًا **كيف تحصل على تحذيرات** لأي سيناريو قد تواجهه تطبيقك.

---

## مثال كامل جاهز للتنفيذ (انسخه‑ألصقه)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**شغّله:** ابنِ المشروع، نفّذ، وسترى التحذيرات مطبوعة ومُحفظة. هذا هو الجواب الكامل على **كيفية الحصول على التحذيرات** و**كيفية مراقبة الخطوط** باستخدام Aspose.Words.

---

## الخلاصة

أنت الآن تعرف **كيفية الحصول على التحذيرات** من Aspose.Words، خصوصًا في سيناريو استبدال الخطوط، وتعلمت **كيفية مراقبة الخطوط** طوال عملية تحميل المستند. من خلال ربط `WarningCallback`، وتكرار كائنات `WarningInfo` المجمعة، وربما حفظ البيانات، تحصل على شفافية كاملة حول أحداث الخطوط المفقودة—وهي قدرة أساسية لأي خط أنابيب معالجة مستندات.

ما الخطوة التالية؟ جرّب توسيع فلتر التحذيرات ليشمل فقدان البيانات أو التحذيرات المتعلقة بالميزات المهجورة، أو دمج سجل JSON في لوحة مراقبة مثل Grafana. النمط نفسه يعمل مع جميع أنواع التحذيرات، لذا ستكون مجهزًا جيدًا لمراقبة أي مشكلة قد تُصدرها Aspose.Words.

برمجة سعيدة، ولتظهر مستنداتك دائمًا كما تتوقع!

---

<img src="font-warnings.png" alt="كيفية الحصول على التحذيرات في Aspose.Words" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}