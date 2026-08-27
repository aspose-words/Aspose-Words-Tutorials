---
category: general
date: 2026-02-10
description: قم بتعيين رد الاتصال للتحذير لمراقبة تغييرات الخط أثناء تكوين الخط الافتراضي
  وتعيين خط الاستيراد الافتراضي في Aspose.Words. تعلّم الحل الكامل خطوة بخطوة.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: ar
og_description: قم بتعيين رد نداء التحذير لمراقبة تغييرات الخط أثناء تكوين الخط الافتراضي
  وتعيين خط الاستيراد الافتراضي. اتبع الدليل الكامل لـ Aspose.Words.
og_title: تعيين رد الاتصال للتحذير في C# – دليل كامل
tags:
- Aspose.Words
- C#
- Document Import
title: تعيين رد النداء للتحذير في C# – دليل شامل لمعالجة الخطوط
url: /ar/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين رد نداء التحذير في C# – دليل شامل لمعالجة الخطوط

هل احتجت يوماً إلى **تعيين رد نداء التحذير** عند تحميل مستند Word وتساءلت كيف يمكنك *تكوين الخط الافتراضي* في الوقت نفسه؟ لست وحدك. في العديد من المشاريع الواقعية—مثل مولدات التقارير الآلية أو خطوط تحويل المستندات—يمكن أن تتسبب الخطوط المفقودة في كسر التخطيط بصمت، والطريقة الوحيدة لاكتشاف هذه المشكلات هي **مراقبة تغيّر الخطوط** عبر رد نداء التحذير.

في هذا الدرس سنستعرض مثالاً عملياً يوضح لك كيفية **تعيين رد نداء التحذير**، **تكوين الخط الافتراضي**، وحتى **تعيين خط الاستيراد الافتراضي** باستخدام Aspose.Words for .NET. بنهاية الدرس ستحصل على مقتطف جاهز للتنفيذ، وتفهم سبب أهمية كل جزء، وتعرف كيف تعدله لحالات الحافة مثل مجلدات الخطوط المخصصة أو الاستبدالات الصامتة.

---

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضاً على .NET Framework 4.6+)  
- حزمة NuGet الخاصة بـ Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- مجلد يحتوي على خط الاحتياطي الذي تريد استخدامه (مثال: `fonts/Arial.ttf`)  
- معرفة أساسية بتطبيقات C# console  

لا توجد مكتبات إضافية مطلوبة.

---

## الخطوة 1: إنشاء LoadOptions و **تكوين الخط الافتراضي**

أول شيء تقوم به عندما تريد التحكم في معالجة الخطوط هو إنشاء كائن `LoadOptions`. هذا الكائن يخبر Aspose.Words كيف يتعامل مع الخطوط المفقودة أثناء الاستيراد.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**لماذا هذا مهم:**  
إذا كان المستند المصدر يشير إلى خط غير مثبت على الخادم، سيبحث Aspose.Words في المجلد الذي قمت بتحديده. هذا هو جوهر **تعيين خط الاستيراد الافتراضي**—أنت تخبر المكتبة صراحةً أين تجد بديلًا قبل أن يتم رفع أي تحذير.

---

## الخطوة 2: **تعيين رد نداء التحذير** لـ **مراقبة تغيّر الخطوط**

يقوم Aspose.Words بإصدار `WarningInfoCollection` كلما اضطر إلى استبدال خط، من بين أمور أخرى. من خلال ربط معالج، يمكنك تسجيل أو الاستجابة لكل استبدال.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**لماذا هذا مهم:**  
مجرد **تكوين الخط الافتراضي** لا يكفي إذا كنت بحاجة إلى تدقيق أي الخطوط تم استبدالها فعليًا. يمنحك رد النداء سجلًا لحظيًا، مما يلبي متطلب **مراقبة تغيّر الخطوط** ويساعدك على اكتشاف الاستبدالات غير المتوقعة مبكرًا في خط أنابيب CI.

---

## الخطوة 3: تحميل المستند باستخدام الخيارات المُعدّة

الآن بعد أن أصبحت خيارات التحميل جاهزة بالكامل، يمكنك تحميل أي ملف `.docx` بأمان. سيُطلق رد النداء تلقائيًا إذا حدث استبدال.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**ما ستراه:**  
إذا كان المصدر يستخدم خطًا غير موجود، سيطبع الطرفية شيئًا مثل:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

هذا الإخراج يؤكد أنك نجحت في **تعيين رد نداء التحذير** وأن **خط الاستيراد الافتراضي** تم تطبيقه.

---

## الخطوة 4: (اختياري) ضبط سلوك استبدال الخطوط بدقة

أحيانًا قد ترغب في استبدال *جميع* الخطوط المفقودة بعائلة واحدة، بغض النظر عن الطلب الأصلي. يتيح لك Aspose.Words تعيين *خط احتياطي* على مستوى عالمي.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**متى تستخدم هذا:**  
إذا كنت تُنشئ ملفات PDF لعلامة تجارية تسمح بمجموعة محدودة من الخطوط فقط، فإن هذا يضمن التناسق عبر كل المستندات، حتى لو حاول المصدر استخدام خط غريب.

---

## الخطوة 5: حفظ المستند أو معالجته أكثر

بعد التحميل، يمكنك المتابعة بأي معالجة تحتاجها—تحرير، تحويل إلى PDF، استخراج نص، إلخ. إليك مثالًا سريعًا لحفظ المستند كملف PDF مع الحفاظ على الخطوط المستبدلة.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

ستظهر الخطوط الاحتياطية في ملف PDF حيثما تم الاستبدال، مما يمنحك تأكيدًا بصريًا أن **تعيين رد نداء التحذير** عمل كما هو متوقع.

---

## المشكلات الشائعة & نصائح احترافية

| المشكلة | لماذا تحدث | الحل |
|---------|------------|------|
| **رد النداء لا يُطلق أبداً** | لم يتم تعيين `LoadOptions.WarningCallback` *قبل* تحميل المستند. | احرص دائمًا على ربط رد النداء **قبل** استدعاء `new Document(...)`. |
| **مجلد الخطوط غير صحيح** | خطأ إملائي في المسار أو عدم وجود أذونات قراءة. | تأكد من وجود المجلد ومن أن التطبيق يملك صلاحية `Read`. استخدم مسارات مطلقة للموثوقية. |
| **استبدالات متعددة، إخراج صاخب** | مستندات كبيرة تحتوي على العديد من الخطوط المفقودة. | صَفِّ التحذيرات حسب `WarningType.FontSubstitution` (كما هو موضح) أو اكتبها إلى ملف سجل بدلاً من الطرفية. |
| **خط الاحتياطي غير مطبق** | خط الاحتياطي غير مثبت على الجهاز. | ضع ملف `.ttf`/`.otf` في المجلد الذي مررته إلى `SetFontsFolder`. يقوم Aspose.Words بتحميله مباشرةً، دون الحاجة لتثبيته على نظام التشغيل. |

**نصيحة احترافية:** عند تشغيل هذا في خط أنابيب CI/CD، قم بإعادة توجيه مخرجات الطرفية إلى ملف بناء. ستحصل بذلك على سجل تدقيق لكل استبدال خط حدث أثناء عملية البناء.

---

## مثال كامل جاهز للتنفيذ (انسخه‑ألصقه)

فيما يلي البرنامج الكامل الذي يمكنك وضعه في مشروع تطبيق Console جديد. يتضمن جميع الخطوات، وبيانات `using`، وتعليقات توضيحية.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**الإخراج المتوقع في الطرفية** (بافتراض أن `Times New Roman` مفقود):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

شغّل البرنامج، افتح `output.pdf`، وسترى المستند معروضًا بخط الاحتياطي أينما كان ذلك ضروريًا.

---

## الخلاصة

أصبح لديك الآن نمط قوي وجاهز للإنتاج حول كيفية **تعيين رد نداء التحذير** في C#، **تكوين الخط الافتراضي**، **مراقبة تغيّر الخطوط**، و**تعيين خط الاستيراد الافتراضي** عند العمل مع Aspose.Words. من خلال ربط جامع التحذيرات قبل التحميل، وتوجيه `FontSettings` إلى مجلد خطوط موثوق، وإجبار خط احتياطي عالمي إذا لزم الأمر، ستحصل على رؤية وتحكم كاملين في استبدال الخطوط—وهو ما تحتاجه أي خط أنابيب معالجة مستندات قوي.

هل أنت مستعد للخطوة التالية؟ جرّب دمج هذا النهج مع:

- **تحميل الخطوط ديناميكيًا** من قاعدة بيانات (استخدم `FontSettings.SetFontsFolder` في وقت التشغيل).  
- **معالجات تحذير مخصصة** تكتب إلى سجل منظم (JSON أو CSV) للتحليلات.  
- **معالجة مستندات متوازية** حيث يحصل كل خيط على `LoadOptions` خاص به لتجنب التداخل.

لا تتردد في التجربة، وتكييف الكود مع بنية مشروعك، ومشاركة أي اكتشافات في التعليقات. برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}