---
category: general
date: 2026-04-21
description: تعلم كيفية اكتشاف الخطوط، التقاط التحذيرات، تكوين رد النداء، وإحصاء التحذيرات
  باستخدام Aspose.Words في C#. دليل خطوة بخطوة لمعالجة الخطوط بشكل موثوق.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: ar
og_description: كيف تكتشف الخطوط في Aspose.Words؟ يوضح لك هذا البرنامج التعليمي كيفية
  التقاط التحذيرات، وتكوين رد النداء، وعدّ التحذيرات في C#.
og_title: كيفية اكتشاف الخطوط في Aspose.Words – دليل كامل
tags:
- Aspose.Words
- C#
- Document Processing
title: كيفية اكتشاف الخطوط في Aspose.Words – دليل كامل
url: /ar/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية اكتشاف الخطوط في Aspose.Words – دليل شامل

هل تساءلت يومًا **كيف تكتشف الخطوط** المفقودة عند تحميل مستند Word؟ هذا السيناريو يظهر كثيرًا أكثر مما ترغب، خاصةً عند التعامل مع ملفات قديمة أو نشر عبر منصات مختلفة. في هذا الدرس سنستعرض مثالًا كاملاً وقابلاً للتنفيذ يَـ​**يُلقِط التحذيرات**، **يُكوّن رد نداء (callback)**، و**يُعدد التحذيرات** حتى تعرف دائمًا أي الخطوط تم استبدالها.

سنستخدم Aspose.Words for .NET (الإصدار 24.9 وقت كتابة هذا الدرس) وC# عادي. لا خدمات خارجية، لا سحر—فقط الـ API وبعض الأسطر من الشيفرة. في النهاية ستتمكن من رصد كل استبدال للخط، تسجيله، وحتى اتخاذ قرار بإلغاء التحميل إذا كان الخط حاسمًا مفقودًا.  

### ما الذي ستحتاجه
- **Aspose.Words for .NET** (تثبيت عبر NuGet: `Install-Package Aspose.Words`)
- .NET 6.0 أو أحدث (الشيفرة تعمل أيضًا على .NET Framework)
- ملف DOCX تجريبي يحتوي على إشارة إلى خط غير موجود على الجهاز (مثال: “MyCustomFont.ttf”)
- Visual Studio، Rider، أو أي محرر C# تفضله

> **نصيحة احترافية:** إذا لم يكن لديك مستند يحتوي على خطوط مفقودة، ما عليك سوى إعادة تسمية ملف خط على نظامك أو تعديل XML داخل الـ DOCX للإشارة إلى عائلة خط غير موجودة.

---

## كيفية اكتشاف الخطوط باستخدام Aspose.Words

الفكرة الأساسية هي ربط نظام التحذير في Aspose.Words. عندما لا يتمكن المكتبة من العثور على الخط المطلوب، تُصدر تحذيرًا من نوع `WarningType.FontSubstitution`. من خلال توفير تنفيذ مخصص لـ `IWarningCallback`، يمكنك **اكتشاف الخطوط** التي تم استبدالها أثناء عملية التحميل.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **لماذا يعمل هذا:** تستدعي Aspose.Words طريقة `Warning` لكل مشكلة غير حرجة. عبر تخزين كائنات `WarningInfo` تحصل على وصول كامل للنوع، الرسالة، والسياق—وهو بالضبط ما تحتاجه **لاكتشاف الخطوط** التي تم استبدالها.

---

## كيفية التقاط التحذيرات عند تحميل المستند

الآن بعد أن أصبح لدينا جامع للتحذيرات، نحتاج إلى إخبار `LoadOptions` باستخدامه. هذه هي خطوة **كيفية التقاط التحذيرات** في اللغز.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **حالة حافة:** إذا قمت بتحميل مستند من تدفق (`new Document(stream, loadOptions)`)، يعمل نفس رد النداء—فقط مرّر الـ stream بدلاً من مسار الملف.

في هذه المرحلة يصبح المستند محملاً بالكامل، لكن أي تحذيرات استبدال خطوط تُخزن بأمان داخل `warningCollector.Warnings`.

---

## كيفية تعداد التحذيرات والإبلاغ عن استبدال الخطوط

أخيرًا، نمرّ على التحذيرات المجمعة ون **نعد التحذيرات** التي تتعلق تحديدًا باستبدال الخطوط. هذه الخطوة تحوّل البيانات الخام إلى تقرير مقروء.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**الناتج المتوقع** (مثال):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

إذا لم يحتوي المستند على خطوط مفقودة، فإن الحلقة ببساطة لا تُنتج أي مخرجات—لا شيء يدعو للقلق.

---

## مثال كامل يعمل (جميع الخطوات في ملف واحد)

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في مشروع Console. يربط معًا **كيفية اكتشاف الخطوط**، **كيفية التقاط التحذيرات**، **كيفية تكوين رد النداء**، و**كيفية تعداد التحذيرات** في تدفق موحد.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**تشغيل هذا البرنامج** سيطبع كل خط اضطر Aspose.Words لاستبداله. يمكنك توجيه المخرجات إلى ملف سجل، رفع تنبيه، أو حتى إلغاء التحميل إذا كان خط حاسم مفقودًا.

---

## أسئلة شائعة وملاحظات

### ماذا لو أردت إيقاف التحميل عند فقدان خط مطلوب؟
يمكنك فحص كائنات `WarningInfo` داخل رد النداء ورمي استثناء عندما يظهر اسم خط معين. سيؤدي الاستثناء إلى إلغاء التحميل، مما يمنحك السيطرة الكاملة.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### هل يعمل هذا مع ملفات PDF أو صيغ أخرى؟
نعم. يستخدم Aspose.Words نفس بنية التحذير للـ PDF، RTF، وHTML. فقط غيّر امتداد الملف ويبقى باقي الشيفرة كما هو.

### كيف يمكنني تسجيل التحذيرات إلى ملف بدلاً من وحدة التحكم؟
استبدل `Console.WriteLine` بأي إطار تسجيل تفضله (`Serilog`، `NLog`، إلخ). تُظهر فئة `WarningInfo` الخصائص `Message`، `Source` و`Exception` لتوفير سجلات مفصلة.

### هل سيؤثر هذا على الأداء؟
العبء إضافي ضئيل—فAspose.Words يولد التحذيرات داخليًا بالفعل. إضافة رد نداء مجرد يخزنها في قائمة، وهو O(n) بالنسبة لعدد التحذيرات. بالنسبة للمستندات المعتادة، يكون التأثير أقل من 1 % من إجمالي زمن التحميل.

---

## ملخص بصري

![كيفية اكتشاف الخطوط في Aspose.Words – مخطط تدفق التحذير](https://example.com/images/font-detection-diagram.png "كيفية اكتشاف الخطوط")

*النص البديل:* **كيفية اكتشاف الخطوط** – مخطط يُظهر رد النداء للتحذير، الجمع، وخطوات التعداد.

---

## الخاتمة

لقد غطينا **كيفية اكتشاف الخطوط** في Aspose.Words عبر **التقاط التحذيرات**، **تكوين رد نداء**، و**تعداد التحذيرات**. يُظهر مثال الشيفرة الكامل نمطًا جاهزًا للإنتاج يمكنك إدراجه في أي تطبيق .NET.  

بعد ذلك، قد ترغب في استكشاف:

- **كيفية التقاط التحذيرات** لمشكلات أخرى (مثل مشاكل تحويل الصور)
- **كيفية تكوين رد نداء** لأطر تسجيل مخصصة
- **كيفية تعداد التحذيرات** عبر مستندات متعددة في مهمة دفعة
- استخدام **Aspose.Words.Fonts.FontSettings** لتوفير مجلدات خطوط احتياطية، مما قد يقلل عدد الاستبدالات من الأساس.

جرّبه، عدّل الجامع ليناسب أسلوب التسجيل لديك، ولن تُفاجئ مرة أخرى باستبدال خط غير متوقع. إذا واجهت أي صعوبات، اترك تعليقًا أدناه—برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}