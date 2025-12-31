---
category: general
date: 2025-12-31
description: التقاط تحذيرات الخطوط في Aspose.Words لاكتشاف الخطوط المفقودة وإدراج
  الخطوط المفقودة في تطبيق .NET الخاص بك. تعلم حل C# خطوة بخطوة.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: ar
og_description: التقاط تحذيرات الخطوط في Aspose.Words لاكتشاف الخطوط المفقودة وإدراجها.
  دليل كامل بلغة C# مع الشيفرة والنصائح.
og_title: التقاط تحذيرات الخطوط – اكتشاف وإدراج الخطوط المفقودة
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: التقاط تحذيرات الخط – الكشف عن الخطوط المفقودة وإدراجها
url: /ar/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# التقاط تحذيرات الخط – اكتشاف وإدراج الخطوط المفقودة

هل احتجت يومًا إلى **التقاط تحذيرات الخط** عند تحميل مستند Word لكنك لم تكن متأكدًا من كيفية إظهار تفاصيل الخط المفقود؟ لست وحدك. في العديد من المشاريع الواقعية، تتسبب الخطوط المفقودة في اضطرابات التخطيط، وبدون تحذيرات مناسبة تنتهي بك المطاردة وراء أخطاء غير مرئية.  

في هذا الدرس سنوضح لك كيفية **اكتشاف الخطوط المفقودة** و**إدراج الخطوط المفقودة** باستخدام Aspose.Words for .NET. في النهاية ستحصل على مقتطف C# جاهز للتنفيذ يطبع كل تحذير استبدال، بحيث يمكنك تسجيله، تنبيهه، أو حتى استبدال الخطوط تلقائيًا.

---

## لماذا يعتبر التقاط تحذيرات الخط مهمًا

عند فتح Aspose.Words لملف DOCX يشير إلى خط غير مثبت على الخادم، يقوم بشكل صامت باستبداله بخط احتياطي. يبدو المستند جيدًا، لكن الدقة البصرية تتأثر — تخيل شعار علامة تجارية يُعرض بنوع خط خاطئ.  

التقاط تلك التحذيرات يتيح لك:

* **الحفاظ على اتساق العلامة التجارية** – تعرف بالضبط أي الخطوط مفقودة.
* **أتمتة الإصلاح** – استبدال الخطوط المفقودة برمجيًا.
* **تدقيق الامتثال** – إنشاء تقارير للمراجعات القانونية أو التصميمية.

باختصار، **التقاط تحذيرات الخط** هو الخط الدفاعي الأول ضد الاستبدال الصامت للخطوط.

---

## إعداد LoadOptions لاكتشاف الخطوط المفقودة

المفتاح لإظهار التحذيرات هو الخاصية `LoadOptions.FontSubstitutionWarning`. بشكل افتراضي تكون مضبوطة على `None`، مما يعني أن Aspose.Words يبتلع الرسائل. تغييرها إلى `All` يخبر المكتبة بتسجيل كل حدث استبدال.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **نصيحة احترافية:** إذا كان لديك مجلد خطوط مخصص، قم بتعيينه إلى `FontSettings.SetFontsFolder("path")` قبل تحميل المستند. بهذه الطريقة يمكنك **اكتشاف الخطوط المفقودة** التي ليست في دليل النظام.

---

## تحميل المستند وإدراج الخطوط المفقودة

الآن بعد أن أصبحت `LoadOptions` جاهزة، الخطوة التالية هي تحميل ملف Word. يُقبل المُنشئ كائن الخيارات، وأي استبدال سيتم تسجيله في `WarningInfoCollection` الخاص بالمستند.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

إذا كان الملف يشير إلى خطوط غير متوفرة، فإن كل خط مفقود يولد إدخال `WarningInfo`. يمكنك **إدراج الخطوط المفقودة** عن طريق التكرار على تلك المجموعة.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

المخرجات النموذجية تبدو هكذا:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

كل سطر يخبرك بالضبط أي خط كان مفقودًا، مما يلبي متطلب **إدراج الخطوط المفقودة**.

---

## قراءة وتفسير WarningInfoCollection

يمكن أن تحتوي `WarningInfoCollection` على أنواع تحذير مختلفة (مثل `DocumentStructure`، `ImageLoading`). للتركيز فقط على مشاكل الخطوط، قم بالترشيح باستخدام `WarningType.FontSubstitution`.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

لماذا الترشيح؟ لأن مستندًا كبيرًا قد يولد أيضًا تحذيرات بخصوص صور تالفة أو ميزات غير مدعومة. بتضييق المجموعة تتجنب الضوضاء وتحافظ على نظافة مخرجات **التقاط تحذيرات الخط**.

---

## مثال كامل يعمل – التقاط تحذيرات الخط في الواقع

فيما يلي البرنامج الكامل المستقل الذي يمكنك وضعه في أي مشروع .NET Console. يوضح كل خطوة من تكوين `LoadOptions` إلى طباعة قائمة مرتبة من الخطوط المفقودة.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**المخرجات المتوقعة في وحدة التحكم**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

إذا لم يحتوي المستند على خطوط مفقودة سترى:

```
All referenced fonts are available – no warnings captured.
```

---

## حالات الحافة الشائعة وكيفية التعامل معها

| الحالة | لماذا يحدث | الحل الموصى به |
|-----------|----------------|-----------------|
| **المستند يستخدم خط OpenType مضمّن** | يمكن لـ Aspose.Words قراءة الخطوط المضمّنة، ولكن فقط إذا لم يكن الملف تالفًا. | تحقق من الـ DOCX في Word أولاً؛ أعد تضمين الخط إذا لزم الأمر. |
| **عدد كبير من التحذيرات** (مثلاً 200+ خط مفقود) | الاستيراد الضخم من الأنظمة القديمة غالبًا ما يشير إلى مجموعة واسعة من الخطوط. | عالج التحذيرات على دفعات: خزنها في قاعدة بيانات، ثم شغّل سكريبت تثبيت الخطوط. |
| **WarningInfoCollection فارغة** | إما أن المستند يحتوي على جميع الخطوط، أو أن `FontSubstitutionWarning` تُركت على `None`. | أعد فحص إعدادات `LoadOptions` وتأكد من تحميل المسار الصحيح للملف. |
| **خطوط مخصصة موجودة على مشاركة شبكة** | قد يتسبب بطء الشبكة في انتهاء مهلة البحث عن الخط. | حمّل الخطوط مسبقًا إلى `FontSettings` باستخدام `SetFontsFolder` واضبط `CacheFontData = true`. |

هذه النصائح تساعدك على **اكتشاف الخطوط المفقودة** بثقة، حتى في البيئات المعقدة.

---

## توضيح بصري

![مثال على التقاط تحذيرات الخط](https://example.com/images/capture-font-warnings.png "مثال على التقاط تحذيرات الخط")

*تظهر لقطة الشاشة تشغيل وحدة التحكم حيث تم الإبلاغ عن خطين مفقودين.*

---

## الخطوات التالية – ما بعد التقارير البسيطة

الآن بعد أن أصبحت قادرًا على **التقاط تحذيرات الخط**، فكر في أتمتة الإصلاح:

1. **استبدال الخطوط تلقائيًا** – استبدل الخطوط المفقودة بخط احتياطي معتمد من الشركة عبر تعديل `FontSettings.SubstitutionSettings`.
2. **تسجيل التحذيرات إلى نظام مراقبة** – وجه رسائل التحذير إلى Serilog أو ELK أو Azure Application Insights.
3. **تقارير موجهة للمستخدم** – أنشئ ملخصًا بصيغة HTML أو PDF للمصممين لمراجعة الخطوط التي تحتاج إلى تثبيت.

جميع هذه الامتدادات تبني على الأساس نفسه الذي غطيناه: تكوين `LoadOptions`، تحميل المستند، وقراءة `WarningInfoCollection`.

---

## الخلاصة

لقد تعلمت الآن كيفية **التقاط تحذيرات الخط** في Aspose.Words، **اكتشاف الخطوط المفقودة**، و**إدراج الخطوط المفقودة** مع مخرجات نظيفة صديقة لوحدة التحكم. النهج بسيط، يتطلب بضع أسطر من C# فقط، ويعمل مع أي نسخة .NET تدعم Aspose.Words 23.x أو أحدث.  

جرّبه على ملف DOCX يحتوي على خط قمت بإلغاء تثبيته عمدًا – ستظهر التحذيرات فورًا. من هناك، يمكنك اتخاذ قرار بتثبيت الخطوط المفقودة، استبدالها برمجيًا، أو مجرد تسجيل المشكلة للمراجعة لاحقًا.

برمجة سعيدة، ولتظهر مستنداتك دائمًا بالخطوط الصحيحة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}