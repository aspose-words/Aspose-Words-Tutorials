---
category: general
date: 2026-06-20
description: تمكين تحذيرات استبدال الخطوط في C# باستخدام Aspose.Words. تعلّم كيفية
  تكوين LoadOptions، التقاط التحذيرات، ومعالجة الخطوط المفقودة بفعالية.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: ar
og_description: تمكين تحذيرات استبدال الخطوط في C# باستخدام Aspose.Words. يوضح هذا
  الدليل كيفية إعداد LoadOptions، قراءة WarningInfo، وعرض رسائل الخطوط المفقودة.
og_title: تمكين تحذيرات استبدال الخطوط في C# – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: تمكين تحذيرات استبدال الخطوط في C# باستخدام Aspose.Words
url: /ar/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تمكين تحذيرات استبدال الخطوط في C# باستخدام Aspose.Words

هل تساءلت يومًا كيف **تمكن من تمكين تحذيرات استبدال الخطوط** عندما يشير مستند Word إلى خط غير مثبت على الخادم؟ لست وحدك. الخطوط المفقودة يمكن أن تُفسد تخطيط ملفات PDF أو الصور المُولدة بصمت، والطريقة الوحيدة لاكتشاف ذلك مبكرًا هي الاستماع إلى التحذيرات التي تُصدرها Aspose.Words.

في هذا الدرس سنستعرض مثالًا عمليًا يوضح لك بالضبط كيفية تشغيل هذه التحذيرات، استخراجها من مجموعة `WarningInfo`، وطباعة رسائل ذات معنى إلى وحدة التحكم. في النهاية ستعرف كيف تُكوّن **Aspose.Words LoadOptions**، وتعالج **تحذيرات استبدال الخطوط في C#**، وتُحافظ على خط أنابيب معالجة المستندات الخاص بك خاليًا من الأخطاء.

سنتطرق أيضًا إلى بعض الحالات الخاصة—ماذا يحدث إذا قمت بكتم التحذيرات، أو إذا كنت تحتاج إلى تسجيلها بدلاً من طباعتها—وسنُقدّم لك عينة كود جاهزة للنسخ واللصق تعمل مع أحدث إصدار من Aspose.Words لـ .NET (الإصدار 24.10).

## ما الذي ستحتاجه

- .NET 6.0 أو أحدث (الكود يعمل أيضًا على .NET Framework 4.7+)
- إشارة NuGet إلى `Aspose.Words` (قم بالتثبيت عبر `dotnet add package Aspose.Words`)
- ملف Word يحتوي على خط غير مثبت لديك (مثال: `DocumentWithMissingFont.docx`)
- بيئة تطوير متكاملة جيدة (Visual Studio، Rider، أو VS Code)

هذا كل ما تحتاجه—لا خدمات إضافية، لا أدوات مملوكة. جاهز؟ لنبدأ.

## الخطوة 1: تمكين تحذيرات استبدال الخطوط

أول شيء عليك فعله هو إخبار Aspose.Words بأنك تريد أن تتلقى إشعارًا عندما تستبدل خطًا مفقودًا. يتم ذلك عبر خاصية `FontSettings` لكائن `LoadOptions`. بشكل افتراضي، تكون التحذيرات **معطلة** لإبقاء الـ API هادئًا، لذا علينا تشغيلها يدويًا.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **لماذا يعمل هذا:** عندما لا تكون `FontSettings` مساوية لـ `null`، تقوم المكتبة تلقائيًا بملء `Document.WarningInfo` بأي إدخالات من النوع `WarningType.FontSubstitution` تصادفها أثناء تحميل المستند. فكر فيها كأنك تُشغل “وضع التصحيح” للخطوط.

## الخطوة 2: تحميل المستند باستخدام الخيارات المُكوَّنة

الآن بعد أن أصبحت مجموعة التحذيرات نشطة، حمّل مستندك باستخدام `LoadOptions` التي أعددناها للتو. إذا كان المستند يحتوي على خط مفقود، ستستبدل Aspose.Words الخط ببديل وتضيف تحذيرًا إلى قائمة `WarningInfo`.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **نصيحة احترافية:** إذا كنت تُعالج ملفات متعددة في حلقة، أعد استخدام نفس كائن `LoadOptions`—إن إنشاؤه مرة واحدة يوفر بضع مللي ثانية لكل تكرار.

## الخطوة 3: التجوال عبر WarningInfo وعرض رسائل استبدال الخطوط

بعد تحميل المستند، تحتفظ مجموعة `WarningInfo` بكل تحذير حدث أثناء التحميل. نحن نهتم فقط بـ `WarningType.FontSubstitution`، لذا نقوم بفلترة النتائج وفقًا لذلك.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

تشغيل المقتطف أعلاه على مستند يشير إلى الخط المفقود “Papyrus” قد ينتج مخرجات مثل:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

هذه هي **رسائل استبدال الخطوط** التي تبحث عنها—واضحة، قابلة للتنفيذ، وجاهزة للتسجيل أو الإرسال إلى نظام تنبيه.

## مثال كامل يعمل

فيما يلي برنامج Console مستقل يجمع كل شيء معًا. انسخه‑الصقه في مشروع `.csproj` جديد ثم اضغط **Run**.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### المخرجات المتوقعة

إذا كان المستند يشير إلى خطوط غير مثبتة، سترى شيئًا مشابهًا لـ:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

إذا كانت جميع الخطوط موجودة على الجهاز، سيطبع البرنامج ببساطة:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## مشاكل شائعة & نصائح احترافية

| المشكلة | لماذا يحدث | كيفية الإصلاح / التجنب |
|---------|------------|------------------------|
| **اختفاء التحذيرات** | قمت بمسح `FontSettings` أو استخدمت `LoadOptions` بدونها. | احرص دائمًا على إنشاء `FontSettings` حتى لو لم تعدل أي خاصية. |
| **عدد كبير من التحذيرات** | المستند يستخدم خطوطًا غريبة كثيرة. | فكر في إضافة مجلد خطوط مخصص إلى `FontSettings` عبر `SetFontsFolder` لتقليل الاستبدالات. |
| **تأثير الأداء في حلقة ضيقة** | إعادة إنشاء `LoadOptions` في كل تكرار يضيف عبئًا. | أعد استخدام كائن `LoadOptions` واحد عبر جميع المستندات. |
| **غياب مخرجات وحدة التحكم** | تشغيل البرنامج داخل تطبيق GUI حيث يتم تجاهل `Console.WriteLine`. | حول التحذيرات إلى مسجل (`ILogger`) أو اكتبها إلى ملف. |

### معالجة التحذيرات في خدمة حقيقية

في واجهة API ويب ربما لا تريد الكتابة إلى وحدة التحكم. بدلاً من ذلك، قم بتمرير التحذيرات إلى سجل منظم:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

بهذه الطريقة تحتفظ **بمعالجة تحذيرات المستند** مع الحفاظ على نظافة خدمتك.

## توسيع المثال

- **التقاط أنواع تحذيرات أخرى** (مثل `WarningType.UnknownFileFormat`) بإزالة شرط `if`.
- **حفظ تقرير** بجميع التحذيرات بصيغة JSON للتحليلات اللاحقة.
- **فرض خط بديل محدد** عبر ضبط `FontSettings.SubstitutionSettings.DefaultFontName`.

كل هذه توسيعات طبيعية بمجرد إتقانك **تمكين تحذيرات استبدال الخطوط**.

## الخلاصة

أظهرنا لك كيفية **تمكين تحذيرات استبدال الخطوط** في C# باستخدام Aspose.Words، من تكوين `LoadOptions` إلى التجوال عبر `WarningInfo` وطباعة رسائل صديقة للمستخدم. باتباع الخطوات أعلاه يمكنك حماية خطوط أنابيب معالجة المستندات من تغييرات التخطيط الصامتة الناجمة عن الخطوط المفقودة.

الخطوة التالية: جرّب إضافة مجلد خطوط مخصص، سجّل التحذيرات إلى ملف، أو حتى أرسلها إلى لوحة مراقبة. النمط نفسه يعمل لأي سيناريو **معالجة تحذيرات المستند**، سواء كنت تُحوِّل إلى PDF، تُظهر صورًا، أو تُجري دمجًا بريديًا.

هل لديك أسئلة حول **تحذيرات استبدال الخطوط في C#** أو تريد مشاركة حل ذكي؟ اترك تعليقًا أدناه—برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}