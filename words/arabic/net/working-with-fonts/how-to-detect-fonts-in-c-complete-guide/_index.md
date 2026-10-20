---
category: general
date: 2026-04-02
description: كيفية اكتشاف الخطوط في مستندات C# باستخدام Aspose.Words. تعلم تكوين إعدادات
  الخط ومعالجة الخطوط المفقودة بكفاءة.
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: ar
og_description: كيفية اكتشاف الخطوط في مستندات C# باستخدام Aspose.Words. يوضح لك هذا
  الدليل كيفية تكوين إعدادات الخط ومعالجة الخطوط المفقودة.
og_title: كيفية اكتشاف الخطوط في C# – دليل كامل
tags:
- C#
- Aspose.Words
- Document Processing
title: كيفية اكتشاف الخطوط في C# – دليل كامل
url: /ar/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية اكتشاف الخطوط في C# – دليل شامل

هل تساءلت يومًا **كيف يتم اكتشاف الخطوط** المفقودة أو المستبدلة عند تحميل مستند Word في .NET؟ لست وحدك—المطورون يواجهون هذه المشكلة باستمرار عندما يشير مستند إلى خط غير مثبت على الخادم. الخبر السار هو أن Aspose.Words يوفر لك طريقة برمجية نظيفة لاكتشاف هذه الفجوات.

في هذا الدرس سنستعرض مثالًا عمليًا لا يوضح فقط **كيفية اكتشاف الخطوط**، بل يوضح أيضًا كيفية **تكوين إعدادات الخط** و**معالجة الخطوط المفقودة** بشكل سلس. في النهاية ستحصل على قطعة شفرة جاهزة للتنفيذ تطبع كل تحذير استبدال خط، بحيث يمكنك تسجيله أو تنبيهه أو استبدال الخطوط حسب الحاجة.

---

## ما ستحتاجه

- **Aspose.Words for .NET** (الإصدار الأحدث هو الأفضل؛ الشيفرة أدناه تستهدف .NET 6+)
- بيئة تطوير .NET (Visual Studio، Rider، أو VS Code)
- ملف `.docx` تجريبي يشير إلى خط غير مثبت لديك (مفيد للاختبار)

لا توجد حزم NuGet إضافية مطلوبة بخلاف Aspose.Words، والحل يعمل على Windows وLinux وmacOS.

---

## الخطوة 1: تثبيت وإضافة مرجع Aspose.Words

أولاً، أضف المكتبة إلى مشروعك. أمر NuGet بسيط:

```bash
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** إذا كنت تستخدم خادم CI، قم بتثبيت نسخة الحزمة لتجنب التغييرات المفاجئة غير المتوقعة.

---

## الخطوة 2: تكوين إعدادات الخط (وتجهيز خيارات التحميل)

قبل فتح المستند، يمكنك إخبار Aspose.Words أين يبحث عن الخطوط الاحتياطية. هذا هو جزء **تكوين إعدادات الخط** الذي يمنع المحرك من استبدال الخطوط بصمت بما قد لا ترغب فيه.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

لماذا نهتم؟ إذا كان المستند يشير إلى *Comic Sans* لكن خادمك يحتوي فقط على *Calibri*، سيستبدل Aspose.Words الخط بـ *Calibri* ويصدر تحذيرًا. من خلال تكوين مسار البحث، تقلل المفاجآت غير المرغوب فيها.

---

## الخطوة 3: تحميل المستند باستخدام الخيارات المُجهزة

الآن نقوم بفتح الملف فعليًا. يتم تمرير `LoadOptions` التي أنشأناها في الخطوة السابقة مباشرةً إلى مُنشئ `Document`.

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

إذا تعذر العثور على الملف أو كان معطوبًا، يتم إلقاء استثناء—لذا قد ترغب في تغليف ذلك بكتلة try/catch في كود الإنتاج.

---

## الخطوة 4: فحص تحذيرات المستند للبحث عن استبدالات الخط

يقوم Aspose.Words بجمع قائمة من التحذيرات أثناء التحليل. من بينها، `FontSubstitutionWarning` يخبرك بالضبط أي خط تم استبداله.

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

قد تحتوي مجموعة `Warnings` أيضًا على عناصر أخرى (مثل `DocumentStructureWarning`). تصفية `FontSubstitutionWarning` يضمن أننا نبلغ فقط عن سيناريو **معالجة الخطوط المفقودة** الذي نهتم به.

---

## الخطوة 5: جمع كل شيء معًا – مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل. انسخه والصقه في تطبيق Console جديد ثم شغّله؛ سترى كل خط مفقود يُطبع على وحدة التحكم.

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**الناتج المتوقع** (مثال):

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

إذا كان المستند يستخدم فقط الخطوط الموجودة على الجهاز، سترى السطر “No font substitutions detected” بدلاً من ذلك.

---

## الحالات الخاصة والأسئلة الشائعة

### ماذا لو كان المستند لا يحتوي على **أي تحذيرات** على الإطلاق؟

هذا يعني ببساطة أن كل خط تم الإشارة إليه وُجد في مجلدات البحث التي قمت بتكوينها. علمة `anySubstitutions` في المثال يغطي هذه الحالة.

### هل يمكنني **تسجيل** التحذيرات إلى ملف بدلاً من وحدة التحكم؟

بالطبع. استبدل استدعاءات `Console.WriteLine` بمسجل من اختيارك (Serilog، NLog، إلخ). كائن `WarningInfo` يعرض أيضًا `WarningType` و `WarningMessage` إذا كنت بحاجة إلى مزيد من التفاصيل.

### كيف يمكنني **تجاهل** خطوط معينة، مثل خط العلامة التجارية للشركة الذي لا ينبغي استبداله أبداً؟

يمكنك إضافة قاعدة استبدال مخصصة:

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

الآن سيستبدل Aspose.Words فقط *MyBrandFont* بالبدائل المذكورة، وستظل تتلقى تحذيرًا يمكنك اتخاذ إجراء بناءً عليه.

### هل يعمل هذا على حاويات **Linux**؟

نعم—فقط تأكد من ربط مجلد يحتوي على ملفات `.ttf`/`.otf` المطلوبة وتوجيه `SetFontsFolder` إليه. لا يعتمد Aspose.Words على الخطوط المثبتة في نظام التشغيل.

---

## نظرة بصرية

![مخطط تدفق كيفية اكتشاف الخطوط](detect-fonts.png "مخطط يوضح خطوات اكتشاف الخطوط في مستند")

*نص بديل للصورة:* **مخطط تدفق كيفية اكتشاف الخطوط** يوضح التكوين، التحميل، وفحص التحذيرات.

---

## ملخص – ما تعلمناه

- **كيفية اكتشاف الخطوط** المفقودة أو المستبدلة باستخدام تحذيرات Aspose.Words.  
- كيفية **تكوين إعدادات الخط** لتوجيهها إلى مجلدات خطوط مخصصة وتعيين بديل افتراضي.  
- استراتيجيات **معالجة الخطوط المفقودة**، من التسجيل إلى قواعد الاستبدال المخصصة.

كل هذا يندمج في تطبيق Console صغير ومستقل يمكنك إدراجه في أي حل .NET.

---

## الخطوات التالية والمواضيع ذات الصلة

- **تضمين الخطوط** مباشرةً في المستند الناتج لتجنب الاستبدالات المستقبلية (`SaveOptions` مع `EmbedFullFonts`).  
- **استبدال الخط برمجيًا** – استبدال الخطوط المفقودة ببديل محدد قبل الحفظ.  
- **تحسين الأداء** – تخزين `FontSettings` مؤقتًا عند معالجة العديد من المستندات دفعةً واحدة.  

إذا كنت مهتمًا بهذه المواضيع، ابحث عن *configure font settings* و*handle missing fonts*—ستقودك إلى مقالات أعمق حول إدارة الخطوط باستخدام Aspose.Words.

برمجة سعيدة! هل واجهت حالة غريبة للخط؟ اترك تعليقًا، وسنقوم بحل المشكلة معًا.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}