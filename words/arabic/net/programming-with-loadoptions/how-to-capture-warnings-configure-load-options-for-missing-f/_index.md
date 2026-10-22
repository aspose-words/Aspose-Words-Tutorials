---
category: general
date: 2026-03-30
description: كيفية التقاط التحذيرات أثناء تحميل ملف DOCX – تعلم اكتشاف الخطوط المفقودة،
  وتكوين إعدادات الخط، وتحديد خيارات التحميل في C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: ar
og_description: كيفية التقاط التحذيرات أثناء تحميل ملف DOCX – دليل خطوة بخطوة لاكتشاف
  الخطوط المفقودة وتكوين إعدادات الخطوط في C#.
og_title: كيفية التقاط التحذيرات – ضبط خيارات التحميل للخطوط المفقودة
tags:
- Aspose.Words
- C#
- Font management
title: كيفية التقاط التحذيرات – ضبط خيارات التحميل للخطوط المفقودة
url: /ar/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية التقاط التحذيرات – تكوين خيارات التحميل للخطوط المفقودة

هل تساءلت يومًا **عن كيفية التقاط التحذيرات** التي تظهر عندما يحاول مستند استخدام خط غير مثبت لديك؟ هذا السيناريو يسبب مشاكل للعديد من المطورين الذين يعملون مع مكتبات معالجة النصوص، خاصةً عندما تحتاج إلى **اكتشاف الخطوط المفقودة** قبل أن تتعطل عملية تصدير PDF.  

في هذا الدرس سنعرض لك حلًا عمليًا جاهزًا للتنفيذ **يقوم بتكوين إعدادات الخطوط**، **يضبط خيارات التحميل**، ويطبع كل تحذير استبدال إلى وحدة التحكم. بنهاية الدرس ستعرف بالضبط **كيف تتعامل مع الخطوط المفقودة** بطريقة تحافظ على صلابة تطبيقك وسعادة المستخدمين.

## ما ستتعلمه

- كيفية **ضبط خيارات التحميل** بحيث تقوم المكتبة بالإبلاغ عن مشاكل الخطوط بدلاً من استبدالها صامتًا.
- الخطوات الدقيقة **لتكوين إعدادات الخطوط** لالتقاط التحذيرات.
- طرق **اكتشاف الخطوط المفقودة** برمجيًا والتفاعل معها.
- مثال كامل بلغة C# يمكنك نسخه ولصقه يعمل مع أحدث نسخة من Aspose.Words for .NET (v24.10 وقت كتابة هذا الدرس).
- نصائح لتوسيع الحل لتسجيل التحذيرات، أو الاعتماد على خطوط مخصصة، أو إيقاف المعالجة عندما تكون الخطوط الحرجة غير موجودة.

> **المتطلبات المسبقة:** تحتاج إلى تثبيت حزمة NuGet الخاصة بـ Aspose.Words for .NET (`Install-Package Aspose.Words`). لا توجد تبعيات خارجية أخرى مطلوبة.

---

## الخطوة 1: استيراد المساحات الاسمية وتحضير المشروع

أولًا، أضف توجيهات `using` الأساسية. هذا ليس مجرد قالب؛ فهو يخبر المترجم أين توجد `LoadOptions` و `FontSettings` و `Document`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **نصيحة محترف:** إذا كنت تستخدم .NET 6+ يمكنك تمكين عبارات *global using* لتجنب تكرار هذه الأسطر في كل ملف.

---

## الخطوة 2: ضبط خيارات التحميل وتمكين تحذيرات استبدال الخطوط

جوهر **كيفية التقاط التحذيرات** يكمن في كائن `LoadOptions`. بإنشاء نسخة جديدة من `FontSettings` وربط معالج حدث بـ `SubstitutionWarning`، تخبر المكتبة أن تُعلن كل مرة لا تجد فيها الخط المطلوب.

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**لماذا هذا مهم:** بدون الاشتراك في الحدث، تقوم Aspose.Words بالعودة صامتًا إلى خط افتراضي، ولن تعرف أي رموز تم استبدالها. بالاستماع إلى `SubstitutionWarning` تحصل على سجل كامل—وهو أمر حاسم في البيئات التي تتطلب الامتثال.

---

## الخطوة 3: تحميل المستند باستخدام الخيارات المكوَّنة

الآن بعد ربط التحذيرات، قم بتحميل ملف DOCX (أو أي صيغة مدعومة) باستخدام `loadOptions` التي أعددتها للتو. سيتسبب مُنشئ `Document` في تشغيل منطق فحص الخطوط فورًا.

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

إذا كان الملف يشير، على سبيل المثال، إلى *“Comic Sans MS”* على جهاز لا يملك سوى *“Arial”*، سترى شيئًا مشابهًا لهذا:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

يتم طباعة هذا السطر مباشرة إلى وحدة التحكم بفضل المعالج الذي ربطناه مسبقًا.

---

## الخطوة 4: التحقق من التحذيرات الملتقطة والتفاعل معها

التقاط التحذيرات هو نصف المعركة فقط؛ غالبًا ما تحتاج إلى اتخاذ قرار بشأن ما ستفعله بعد ذلك. أدناه نمط سريع يخزن التحذيرات في قائمة للتحليل لاحقًا—مثالي إذا أردت تسجيلها في ملف أو إيقاف الاستيراد عندما يكون خط حاسم مفقودًا.

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**معالجة الحالات الخاصة:**  
- **عدة خطوط مفقودة:** ستحتوي القائمة على مدخل واحد لكل استبدال، لذا يمكنك التكرار وبناء تقرير مفصل.  
- **خطوط احتياطية مخصصة:** إذا كان لديك ملفات خطوط خاصة، أضفها إلى `FontSettings` قبل التحميل: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`. ستظهر التحذيرات بعد ذلك الخط الاحتياطي المخصص بدلًا من الخط الافتراضي للنظام.  

---

## الخطوة 5: مثال كامل جاهز للتنفيذ (نسخ‑لصق)

بدمج كل ما سبق، إليك تطبيق console مستقل يمكنك تجميعه وتشغيله الآن.

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**الناتج المتوقع في وحدة التحكم** (عندما يشير الـ DOCX إلى خط مفقود):

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

إذا كان هناك خط *حاسم* مثل “Times New Roman” مفقود، سترى رسالة الإيقاف بدلاً من ذلك.

---

## أسئلة شائعة وملاحظات

| السؤال | الجواب |
|----------|--------|
| **هل يجب استدعاء `SetFontsFolder` لالتقاط التحذيرات؟** | لا. يعمل حدث التحذير مع خطوط النظام الافتراضية. استخدم `SetFontsFolder` فقط عندما تريد توفير خطوط احتياطية إضافية. |
| **هل سيعمل هذا على .NET Core / .NET 5+؟** | بالتأكيد. يدعم Aspose.Words 24.10 جميع بيئات .NET الحديثة. فقط تأكد من أن حزمة NuGet تتطابق مع إطار العمل المستهدف. |
| **ماذا لو أردت تسجيل التحذيرات إلى ملف بدلاً من وحدة التحكم؟** | استبدل `Console.WriteLine(msg);` بأي استدعاء لإطار تسجيل، مثل `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`. |
| **هل يمكنني قمع التحذيرات لخطوط معينة؟** | نعم. داخل معالج الحدث يمكنك الفلترة: `if (e.FontName == "SomeFont") return;`. هذا يمنحك تحكمًا دقيقًا. |
| **هل هناك طريقة لجعل الخطوط المفقودة تُعامل كأخطاء؟** | يمكنك رمي استثناء يدويًا داخل المعالج عندما يتحقق شرط معين، أو ضبط علم وإيقاف العملية بعد إنشاء `Document` كما هو موضح في المثال. |

---

## الخلاصة

أصبح لديك الآن نمط جاهز للإنتاج **لالتقاط التحذيرات** التي تحدث عند تحميل مستندات تحتوي على خطوط مفقودة. من خلال **اكتشاف الخطوط المفقودة**، **تكوين إعدادات الخطوط**، و**ضبط خيارات التحميل** بشكل مناسب، تحصل على رؤية كاملة لأحداث استبدال الخطوط ويمكنك اتخاذ قرار التسجيل أو الاعتماد على خطوط بديلة أو الإيقاف.  

ابدأ بدمج هذه المنطق في خط أنابيب تحويل PDF الخاص بك، أضف خطوط احتياطية مخصصة، أو قم بإرسال قائمة التحذيرات إلى نظام مراقبة. هذا النهج قابل للتوسع من الأدوات الصغيرة إلى خدمات معالجة المستندات على مستوى المؤسسات.

---

### قراءة إضافية وخطوات مستقبلية

- **استكشف المزيد من ميزات FontSettings** – تضمين خطوط مخصصة، التحكم في ترتيب الخطوط الاحتياطية، واعتبارات الترخيص.  
- **دمج مع تحويل PDF** – بعد التقاط التحذيرات، استدعِ `doc.Save("output.pdf");` وتحقق من أن الـ PDF يستخدم الخطوط المتوقعة.  
- **أتمتة الاختبارات** – اكتب اختبارات وحدة تقوم بتحميل مستندات معروفة الخطوط المفقودة وتتحقق من أن قائمة التحذيرات تحتوي على الرسائل المتوقعة.  

إذا واجهت أي صعوبات أو كان لديك أفكار لتحسين الحل، لا تتردد في ترك تعليق. happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}