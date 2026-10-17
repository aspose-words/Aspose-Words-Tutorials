---
category: general
date: 2026-03-08
description: تسمح لك إعدادات الخط المخصصة بتعيين إعدادات الخط، وتحميل مستند Word بأمان،
  ومعالجة الخطوط المفقودة باستخدام Aspose.Words.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: ar
og_description: تتيح لك إعدادات الخط المخصصة ضبط إعدادات الخط، تحميل مستند Word بأمان
  ومعالجة الخطوط المفقودة باستخدام Aspose.Words.
og_title: إعدادات الخط المخصص في C# – تحميل Word ومعالجة الخطوط المفقودة
tags:
- Aspose.Words
- C#
- Font Management
title: إعدادات الخطوط المخصصة في C# – تحميل Word ومعالجة الخطوط المفقودة
url: /ar/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إعدادات الخطوط المخصصة في C# – تحميل Word ومعالجة الخطوط المفقودة

هل تساءلت يومًا كيف تعمل **إعدادات الخطوط المخصصة** عندما يشير ملف Word إلى خطوط غير مثبتة لديك؟ إنها مشكلة شائعة—يظهر المستند بشكل جيد على جهاز واحد، ثم فجأة يتحول كل فقرة إلى خط احتياطي على جهاز آخر.  

الخبر السار؟ مع Aspose.Words يمكنك **تعيين إعدادات الخطوط**، **تحميل محتوى مستند Word**، و**معالجة الخطوط المفقودة** كلها في تدفق واحد منظم. أدناه ستجد مثالًا كاملاً وجاهزًا للتنفيذ يوضح بالضبط كيفية القيام بذلك، بالإضافة إلى “السبب” وراء كل خطوة.

## ما ستتعلمه

* إنشاء كائن `LoadOptions` وإرفاق نسخة `FontSettings`.  
* تسجيل رد نداء تحذير حتى تتمكن من رؤية الخطوط التي تم استبدالها.  
* تحميل ملف DOCX قد يفتقد بعض الخطوط، وطباعة تفاصيل الاستبدال إلى وحدة التحكم.  

بنهاية هذا الدليل ستكون قادرًا على نشر تطبيق C# الخاص بك بثقة، مع العلم أن كل سيناريو خط مفقود يتم تسجيله ويمكن معالجته لاحقًا.

> **المتطلبات المسبقة:** Aspose.Words for .NET (الإصدار 23.12 أو أحدث) مثبت عبر NuGet، ومعرفة أساسية بتطبيقات C# في وحدة التحكم.

---

## إعدادات الخطوط المخصصة – تكوين LoadOptions

أول شيء تحتاجه هو كائن `LoadOptions`. هذا يخبر Aspose.Words كيفية معالجة الملف الوارد. من خلال تعيين نسخة جديدة من `FontSettings` نوفر للمكتبة مكانًا للبحث عن الخطوط المخصصة.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**لماذا هذا مهم:**  
إذا تخطيت `FontSettings`، سيعود Aspose.Words إلى مجموعة الخطوط الافتراضية للنظام. هذا يعني أن أي خط مفقود سيُستبدل بصمت، ولن تعرف أي الخطوط تم استبدالها. بإنشاء حاوية `FontSettings` صريحة تحصل على سيطرة كاملة على عملية البحث.

---

## تعيين إعدادات الخطوط على LoadOptions

الآن بعد أن لدينا كائن `FontSettings`، قد تتساءل إلى أين توجهه. عادةً ما تضيف مجلدًا يحتوي على الخطوط التي تُضمّنها مع تطبيقك:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*إذا لم يكن لديك مجلد خاص، يمكنك حذف هذا الجزء—سيظل Aspose.Words يُبلغ عن الخطوط المفقودة عبر رد نداء التحذير.*

**نصيحة احترافية:** استخدم العلامة `recursive: true` إذا كانت خطوطك موزعة عبر مجلدات فرعية. سيوفر عليك إضافة كل مسار يدويًا.

---

## تحميل مستند Word باستخدام إعدادات الخطوط المخصصة

مع إعداد الخيارات، يصبح تحميل المستند سهلًا. مُنشئ `Document` يقبل مسار الملف و`LoadOptions` التي أنشأناها للتو.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**ما الذي يحدث خلف الكواليس؟**  
يقوم Aspose.Words بتحليل ملف DOCX، يتحقق من كل إشارة `<w:font>`، ويستشير `FontSettings` التي قدمتها. إذا لم يُعثر على خط، يُطلق تحذير من النوع `FontSubstitution`. معالجنا المخصص (الموضح لاحقًا) سيُلتقط تلك التحذيرات.

---

## معالجة الخطوط المفقودة عبر رد نداء التحذير

واجهة `IWarningCallback` تتيح لك الاستجابة لأي مشكلات تظهر أثناء التحميل. تنفيذها بسيط:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

عند تحميل المستند، كل خط مفقود سيسبب سطرًا مثل:

```
Font substituted: Arial -> Liberation Sans
```

**لماذا يجب تسجيل ذلك:**  
في بيئة الإنتاج يمكنك توجيه هذه الرسائل إلى ملف أو نظام تتبع، مما يسهل اكتشاف الخطوط التي تحتاج إلى تضمينها أو ترخيصها.

---

## مثال كامل يعمل

فيما يلي برنامج وحدة تحكم مستقل يربط كل شيء معًا. انسخه والصقه في مشروع .NET Core جديد ثم اضغط **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**المخرجات المتوقعة** (بافتراض أن `input.docx` يستخدم خطًا غير موجود لديك):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

إذا كانت جميع الخطوط موجودة، سترى فقط سطر التأكيد النهائي.

---

## أسئلة شائعة وحالات خاصة

| السؤال | الجواب |
|----------|--------|
| **ماذا لو احتجت إلى تضمين الخطوط المفقودة في ملف PDF؟** | بعد التحميل، استدعِ `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` ثم فعّل التضمين باستخدام `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **هل يمكنني كتم التحذيرات بدلاً من تسجيلها؟** | نعم—عيّن `loadOptions.WarningCallback = null;` أو نفّذ رد النداء لتجاهل التحذيرات غير المتعلقة بالخطوط. |
| **هل يعمل هذا مع ملفات `.doc` و `.rtf`؟** | بالتأكيد. نفس كائن `LoadOptions` ينطبق على أي تنسيق يدعمه Aspose.Words. |
| **هل رد النداء آمن للخطوط المتعددة (thread‑safe)؟** | رد النداء يُنفّذ على نفس الخيط الذي يحمل المستند، لذا يمكنك الكتابة بأمان إلى وحدة التحكم. في سيناريوهات متعددة الخيوط، استخدم مجموعة متزامنة أو إطار تسجيل. |

---

## نصائح احترافية ومخاطر

* **نصيحة احترافية:** إذا قمت بتضمين خط غير مثبت على الجهاز الهدف، أضفه إلى المجلد الذي تمرره إلى `SetFontsFolder`. هذا يضمن عرضًا حتميًا.
* **احذر من الترخيص:** بعض الخطوط تتطلب تراخيص تجارية للتضمين. تحقق دائمًا من اتفاقية ترخيص الخط قبل تضمينه.
* **ملاحظة أداء:** تحميل مكتبات خطوط كبيرة قد يبطئ تحليل المستند. حافظ على المجلد خفيفًا—ضمّن فقط الخطوط التي تحتاجها فعليًا.
* **حالة خاصة:** عندما يشير المستند إلى خط باسم *PostScript* بدلاً من اسم العائلة، يظل Aspose.Words يحله طالما ملف الخط موجود في مسار البحث.

---

## الخلاصة

الآن لديك نمط كامل وجاهز للإنتاج لاستخدام **إعدادات الخطوط المخصصة** في C#. من خلال تكوين `LoadOptions`، تسجيل رد نداء التحذير، وإشارة اختيارية إلى مجلد خطوط خاص، يمكنك **تعيين إعدادات الخطوط**، **تحميل محتوى مستند Word** بثقة

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}