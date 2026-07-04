---
category: general
date: 2026-04-24
description: كيفية اكتشاف استبدال الخطوط المفقودة في Aspose.Words باستخدام C#. يوضح
  هذا الدليل كيفية التعامل مع الخطوط المفقودة بشكل موثوق باستخدام تحذيرات FontSettings.
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: ar
og_description: كيفية اكتشاف استبدال الخطوط المفقودة في Aspose.Words باستخدام C#.
  تعلم كيفية التعامل مع الخطوط المفقودة باستخدام تحذيرات FontSettings.
og_title: كيفية اكتشاف الاستبدال في Aspose.Words – دليل شامل
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: كيفية اكتشاف الاستبدال في Aspose.Words – التعامل مع الخطوط المفقودة
url: /ar/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية اكتشاف الاستبدال في Aspose.Words – معالجة الخطوط المفقودة

هل تساءلت يومًا **كيف يتم اكتشاف الاستبدال** عندما يحاول مستند استخدام خط غير مثبت على الخادم الخاص بك؟ إنها مشكلة شائعة، خاصةً عندما تقوم بإنشاء ملفات PDF أو Word في خط أنابيب آلي. الخبر السار هو أن Aspose.Words يوفر لك نقطة ربط مدمجة لاكتشاف هذه الحالة بالضبط، ويمكنك أيضًا **معالجة الخطوط المفقودة** بشكل سلس.

في هذا البرنامج التعليمي سنستعرض مثالًا واقعيًا يوضح **كيف يتم اكتشاف الاستبدال** عبر حدث `FontSettings.Warning`، وسنشرح كيف **معالجة الخطوط المفقودة** دون كسر سير المعالجة. في النهاية ستحصل على مقطع جاهز للتنفيذ، وفهم واضح لأهمية كل سطر، وبعض النصائح لتجنب المشكلات الشائعة.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا على .NET Framework)  
- Aspose.Words لـ .NET (حزمة NuGet `Aspose.Words`) – الإصدار 23.11 أو أحدث  
- مستند تجريبي يشير إلى خط غير مثبت لديك (مثال: `MissingFont.docx`)  
- Visual Studio، VS Code، أو أي بيئة تطوير C# تفضلها  

لا يلزم أي تكوين إضافي بخلاف إضافة حزمة NuGet.

---

## كيفية اكتشاف الاستبدال باستخدام FontSettings

جوهر **كيفية اكتشاف الاستبدال** يكمن في حدث `FontSettings.Warning`. عندما لا يتمكن Aspose.Words من العثور على الخط المطلوب، يُطلق تحذير `WarningType.FontSubstitution`. بالاشتراك في هذا الحدث ستحصل على إشعار فوري، يتضمن اسم الخط الأصلي والخط الذي تم استخدامه كبديل.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**لماذا يعمل هذا:**  
- `LoadOptions.FontSettings` يخبر Aspose.Words باستخدام كائن `FontSettings` الذي أنشأته للتو.  
- الاشتراك في `Warning` يمنحك مكانًا واحدًا لمراقبة *جميع* المشكلات المتعلقة بالخطوط، وليس فقط الخطوط المفقودة.  
- مرشح `WarningType.FontSubstitution` يضمن أنك تتفاعل فقط مع السيناريو المحدد الذي تهتم به – جوهر **كيفية اكتشاف الاستبدال**.

### النتيجة المتوقعة

تشغيل الكود أعلاه مع مستند يشير إلى خط غير موجود سيطبع شيئًا مثل:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

إذا كان المستند يستخدم خطوطًا مثبتة فقط، سيبقى سطر الأوامر صامتًا – إشارة واضحة أن **كيفية اكتشاف الاستبدال** نجحت دون إنذارات كاذبة.

---

## معالجة الخطوط المفقودة بسلاسة

اكتشاف الاستبدال هو نصف المعركة فقط؛ تحتاج أيضًا إلى استراتيجية **معالجة الخطوط المفقودة** حتى يبدو الناتج النهائي كما هو مقصود. أدناه ثلاث طرق عملية يمكنك دمجها واختيارها.

### 1. توفير مجلد خطوط احتياطي

يمكن لـ Aspose.Words البحث في أدلة إضافية عن الخطوط. بتوجيهه إلى مجلد يحتوي على أكثر الخطوط شيوعًا التي تتوقعها، تقلل من احتمال حدوث استبدال تمامًا.

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**لماذا:** عندما يكون الخط الأصلي مفقودًا، يصبح لدى Aspose.Words مجموعة معروفة من البدائل، مما ينتج غالبًا نتيجة بصرية أكثر توقعًا.

### 2. استبدال الخطوط المفقودة برمجيًا

إذا كنت تريد تحكمًا كاملاً، يمكنك استبدال الخط المفقود بآخر محدد بعد الاكتشاف.

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**لماذا:** هذا يخبر المحرك بالخطوط التي يجب تجربتها بالضبط، مما يتيح لك فرض هوية الشركة أو معايير الوصول.

### 3. تسجيل وإيقاف (عند عدم قبول الاستبدال)

أحيانًا يعني الخط المفقود أن المستند غير صالح لحالتك (مثال: النماذج القانونية). في هذا السيناريو يمكنك رمي استثناء فور حدوث استبدال.

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**لماذا:** الفشل الفوري يمنع الأخطاء اللاحقة، مثل الجداول غير المتراصة أو التوقيعات المكسورة.

---

## مثال عملي كامل – جميع الخطوات مجمعة

فيما يلي برنامج واحد جاهز للنسخ واللصق يوضح **كيفية اكتشاف الاستبدال** *و* عدة طرق **معالجة الخطوط المفقودة**. لا تتردد في التعليق على الأقسام التي لا تحتاجها.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**ما المتوقع:**  
- إذا كان `MissingFont.docx` يشير إلى خط غير موجود على الجهاز، سيطبع سطر الأوامر تحذير الاستبدال.  
- الملف المحفوظ `Processed.docx` يستخدم الخط الاحتياطي الذي قمت بتكوينه (أو الخط الافتراضي للمكتبة).  
- لا تظهر استثناءات غير معالجة إلا إذا أوقفت العملية عمدًا عند حدوث الاستبدال.

---

## الأسئلة الشائعة والحالات الخاصة

| السؤال | الإجابة |
|----------|--------|
| *ماذا لو كان المستند يحتوي على العديد من الخطوط المفقودة؟* | يتم إطلاق حدث التحذير لكل **استبدال**، لذا سترى عدة أسطر. يمكنك تجميعها في قائمة لتقرير ملخص. |
| *هل يعمل هذا مع تحويل PDF؟* | بالتأكيد. يتم احترام نفس `FontSettings` عند استدعاء `doc.Save("out.pdf")`. لا يزال تحذير الاستبدال يُطلق، مما يتيح لك التحقق من دقة المظهر في PDF. |
| *هل يمكنني اكتشاف الاستبدال بعد تحميل المستند؟* | ليس مباشرة. يتم رفع التحذير **أثناء** التحميل أو الحفظ. إذا كنت تحتاج إلى تحليل بعد التحميل، احفظ التحذيرات في مجموعة أثناء مرحلة التحميل. |
| *ماذا عن الخطوط المخصصة المدمجة في DOCX؟* | تُعتبر الخطوط المدمجة موجودة، لذا لا يحدث استبدال. إذا كان الخط المدمج معطوبًا، لا يزال Aspose.Words يطلق تحذيرًا، ويمكنك التقاطه بنفس الطريقة. |
| *هل هناك تأثير على الأداء؟* | قليل. فحص التحذير خفيف؛ التكلفة الفعلية هي تحميل المستند نفسه. إضافة مجلد خطوط قد يزيد من وقت البحث قليلًا، لكن فقط عند التحميل الأول. |

---

## نصائح احترافية ومخاطر يجب تجنبها

- **نصيحة احترافية:** دائمًا اضبط `recursive: true` عند الإشارة إلى مجلد يحتوي على العديد من الخطوط؛ وإلا سيتم تجاهل المجلدات الفرعية.  
- **احذر من:** حساسية الأحرف في Linux. أسماء الخطوط غير حساسة لحالة الأحرف في Windows لكنها حساسة في Linux، لذا استخدم الاسم الدقيق أو أضف كلا المتغيرين.  
- **تذكر:** إذا كنت تعمل في بيئة حاويات، تأكد من أن مجلد الخطوط جزء من الصورة أو مُركب أثناء التشغيل.  
- **نصيحة:** احفظ التحذيرات في `List<string>` إذا كنت بحاجة لتقديم ملخص للمستخدمين النهائيين أو تسجيلها في نظام مراقبة.

## الخلاصة

لقد غطينا **كيفية اكتشاف الاستبدال** للخطوط المفقودة في Aspose.Words، وأظهرنا لك عدة طرق **معالجة الخطوط المفقودة**، وقدّمنا مثالًا كاملًا قابلًا للتنفيذ يمكنك إدراجه في أي مشروع .NET. من خلال الاستفادة من حدث `FontSettings.Warning` ستحصل على رؤية فورية لمشكلات الخطوط، ومع مجلدات احتياطية أو قواعد استبدال صريحة ستحافظ على مظهر الناتج كما تتوقع.

هل أنت مستعد للخطوة التالية؟ جرّب توسيع الحل لتضمين الخط الاحتياطي تلقائيًا في ملف PDF المُولد، أو ربط معالج التحذير بخدمة تسجيل مركزية لخطوط أنابيب المستندات على نطاق واسع. الأنماط التي ناقشناها اليوم—اكتشاف قائم على الأحداث، احتياطي سلس، ومعالجة أخطاء صريحة—تنطبق على العديد من واجهات Aspose الأخرى، لذا أنت الآن مجهز لمواجهة تحديات الخطوط في جميع المجالات.

هل لديك المزيد من الأسئلة حول معالجة الخطوط، تحويل PDF، أو حيل Aspose.Words؟ اترك تعليقًا أدناه، وبرمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}