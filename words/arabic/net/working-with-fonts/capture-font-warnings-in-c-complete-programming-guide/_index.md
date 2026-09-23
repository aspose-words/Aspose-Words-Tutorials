---
category: general
date: 2026-02-18
description: تعلم كيفية التقاط تحذيرات الخطوط واكتشاف الخطوط المفقودة في C# باستخدام
  Aspose.Words. اتبع هذا الدليل خطوة بخطوة للتعامل مع الخطوط المفقودة بفعالية.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: ar
og_description: التقاط تحذيرات الخطوط في C# وتعلم كيفية اكتشاف الخطوط المفقودة، ومعالجة
  الخطوط المفقودة، وإدراج قائمة بالخطوط المفقودة مع مثال كامل للكود.
og_title: التقاط تحذيرات الخطوط في C# – الدليل الكامل
tags:
- Aspose.Words
- C#
- Font Management
title: التقاط تحذيرات الخط في C# – دليل البرمجة الكامل
url: /ar/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# التقاط تحذيرات الخطوط في C# – دليل برمجة كامل

هل تساءلت يوماً كيف **تلتقط تحذيرات الخطوط** عندما يشير مستند إلى خط غير مثبت على الخادم؟ لست وحدك. في العديد من التطبيقات المؤسسية، تتسبب الخطوط المفقودة في تشوهات التخطيط، والطريقة الوحيدة الموثوقة لاكتشافها هي الاستماع إلى التحذيرات التي تُصدرها المكتبة.  

في هذا الدرس سنعرض لك حلاً جاهزًا للتنفيذ لا يقتصر فقط على **التقاط تحذيرات الخطوط** بل يشمل أيضًا **اكتشاف الخطوط المفقودة**، **معالجة الخطوط المفقودة**، وحتى **قائمة الخطوط المفقودة** حتى تتمكن من اتخاذ قرار استبدالها أو تضمينها أو تنبيه المستخدم. لا حاجة إلى وثائق خارجية—فقط انسخ، الصق، وشغّل.

## ما ستتعلمه

- كيفية تكوين `LoadOptions` لتفعيل تحذيرات استبدال الخطوط.  
- الكود الدقيق الذي تحتاجه لتحميل ملف DOCX واستخراج كل تحذير.  
- لماذا كل خطوة مهمة، بما في ذلك اعتبارات الأداء.  
- معالجة الحالات الخاصة مثل المستندات التي تحتوي على خطوط متعددة السكريبت أو مجلدات خطوط مخصصة.  

**المتطلبات المسبقة**: .NET 6+ (أو .NET Framework 4.6+)، إشارة إلى حزمة **Aspose.Words** على NuGet، وفهم أساسي للغة C#. إذا لم تستخدم Aspose.Words من قبل، لا تقلق—هذا الدليل يشرح لك كل تفاصيله.

![مخطط يوضح تدفق التقاط تحذيرات الخطوط](image.png){alt="مخطط التقاط تحذيرات الخطوط"}

## التقاط تحذيرات الخطوط – لماذا هو مهم

عند تحميل Aspose.Words لمستند، يقوم بهدوء باستبدال أي خط غير متوفر بخط احتياطي. هذا الخط الاحتياطي يحافظ على استمرارية عملية التحميل، لكن النتيجة البصرية قد تكون غير متوازنة تمامًا. من خلال تفعيل علم **SubstitutionWarningLevel.All**، تضيف المكتبة إدخال `WarningInfo` لكل خط مفقود، مما يتيح لك **اكتشاف الخطوط المفقودة** قبل أن يتم عرض المستند أو حفظه.

> **نصيحة احترافية:** إذا كنت تعالج مئات الملفات في مهمة دفعة، فإن تسجيل هذه التحذيرات في مخزن مركزي يمكن أن يوفر لك ساعات من اختبار الجودة اليدوي لاحقًا.

## الخطوة 1: إعداد مشروعك

1. افتح بيئة التطوير المفضلة لديك (Visual Studio، Rider، VS Code).  
2. أنشئ مشروع وحدة تحكم جديد:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. أضف حزمة Aspose.Words:

```bash
dotnet add package Aspose.Words
```

هذا كل شيء—بدون ملفات DLL إضافية، بدون COM interop. المكتبة تتضمن كل ما تحتاجه **للتعامل مع الخطوط المفقودة**.

## الخطوة 2: إعداد خيارات التحميل لالتقاط جميع تحذيرات استبدال الخطوط

لجعل المحرك **يلتقط تحذيرات الخطوط**، يجب إبلاغه بتسجيل كل استبدال. المقتطف التالي ينشئ كائن `LoadOptions`، يفعّل مستوى التحذير، ويُشير (اختياريًا) إلى مجلد يحتوي على خطوط مخصصة قد ترغب في استخدامها.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**لماذا هذا مهم:**  
- `SubstitutionWarningLevel.All` يضمن تسجيل **كل** حدث خط مفقود، وليس الأول فقط.  
- بدون هذا العلم، يقوم Aspose.Words باستبدال الخط بهدوء ولن تعرف بوجود المشكلة.

## الخطوة 3: تحميل المستند باستخدام الخيارات المكوَّنة

الآن نفتح الملف فعليًا. استبدل `DocumentWithMissingFonts.docx` بالمسار إلى مستند الاختبار الخاص بك.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

إذا كان الملف يحتوي على أي مراجع لخطوط غير موجودة على الجهاز (أو في المجلد الاختياري الذي أضفته)، سيتم ملء `document.WarningInfoCollection`.

## الخطوة 4: العثور على وعرض أي تحذيرات استبدال خطوط

هذا هو جوهر الدرس: التجول في `WarningInfoCollection` ل**قائمة الخطوط المفقودة**. سنقوم بفلترة حسب `WarningType.FontSubstitution` وطباعة رسالة ودية.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### النتيجة المتوقعة

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

إذا كان المستند يستخدم خطوطًا مثبتة فقط، سترى السطر “✅ No missing fonts detected”.

## الخطوة 5: متقدم – كيفية **معالجة الخطوط المفقودة** برمجيًا

قد يكون طباعة القائمة كافية لأداة تشخيص، لكن العديد من الأنظمة الإنتاجية تحتاج إلى **معالجة الخطوط المفقودة** تلقائيًا. فيما يلي استراتيجيتان شائعتان:

### 5.1 استبدال بخط احتياطي معروف

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 تضمين خط مخصص أثناء التشغيل

إذا كان لديك ملف خط مؤسسي (`MyBrand.ttf`)، يمكنك تضمينه عندما يتم اكتشاف خط مفقود:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **ملاحظة:** قد يؤدي تضمين الخطوط إلى زيادة حجم الملف الناتج، لذا قيم الموازنة بين الدقة وعرض النطاق الترددي.

## الأخطاء الشائعة وكيفية تجنبها

| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| لا تظهر تحذيرات رغم أن المستند يبدو غير صحيح | لم يتم ضبط `SubstitutionWarningLevel` على `All` | تأكد من أن الخطوة 2 تضبط العلم كما هو موضح |
| قائمة التحذيرات تكرر نفس الخط عدة مرات | يحتوي المستند على الخط في عدة أنماط | قم بإزالة التكرار إذا كنت تحتاج إلى قائمة فريدة: `fontWarnings.Select(w => w.Description).Distinct()` |
| تعطل التطبيق عند معالجة ملفات DOCX الكبيرة | التحميل بإعدادات الذاكرة الافتراضية | استخدم `LoadOptions.LoadFormat` أو قم بقراءة الملف عبر تدفق لتقليل الضغط على الذاكرة |

## مثال عملي كامل (جاهز للنسخ واللصق)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

شغّل البرنامج باستخدام `dotnet run`. يجب أن ترى قائمة الخطوط المفقودة مطبوعة في وحدة التحكم، مما يؤكد أنك نجحت في **التقاط تحذيرات الخطوط**.

## الخلاصة

أصبح لديك الآن نمط كامل وجاهز للإنتاج **لالتقاط تحذيرات الخطوط**، **لاكتشاف الخطوط المفقودة**، **للتعامل مع الخطوط المفقودة**، و**لإدراج قائمة بالخطوط المفقودة** باستخدام Aspose.Words في C#. النهج خفيف الوزن، يتطلب بضع أسطر من الكود فقط، ويمكن دمجه في أي خط أنابيب موجود—سواء كنت

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}