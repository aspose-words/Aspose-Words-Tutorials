---
category: general
date: 2026-03-01
description: إنشاء FontSettings في C# لاكتشاف الخطوط المفقودة، والتقاط رسائل الخط،
  ومعالجة الخطوط المفقودة باستخدام Aspose.Words. دليل خطوة بخطوة للمطورين.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: ar
og_description: إنشاء FontSettings في C# لاكتشاف الخطوط المفقودة، والتقاط رسائل الخط،
  ومعالجة الخطوط المفقودة باستخدام Aspose.Words. دليل كامل مع الشيفرة.
og_title: إنشاء FontSettings في C# – اكتشاف الخطوط المفقودة والتقاط رسائل الخط
tags:
- Aspose.Words
- C#
- Font Management
title: إنشاء FontSettings في C# – اكتشاف الخطوط المفقودة والتقاط رسائل الخط
url: /ar/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء FontSettings في C# – اكتشاف الخطوط المفقودة وتسجيل رسائل الخط

هل احتجت يومًا إلى **إنشاء FontSettings** في مشروع .NET لكن لم تكن متأكدًا من كيفية اكتشاف الخطوط التي لم يتم تثبيتها على الجهاز المستهدف؟ لست وحدك. في العديد من التطبيقات الواقعية—مثل مولدات التقارير الآلية أو محولات المستندات—يمكن للخطوط المفقودة أن تُفسد التخطيط بصمت، ولن تعرف ذلك إلا عندما يبدو ملف PDF غير صحيح.  

ماذا لو كان بإمكانك **اكتشاف الخطوط المفقودة**، **تسجيل رسائل الخط**، و**معالجة الخطوط المفقودة** قبل أن تفسد مخرجاتك؟ الخبر السار هو أن Aspose.Words يجعل ذلك سهلًا للغاية. في هذا الدرس سنستعرض العملية بالكامل، بدءًا من إعداد كائن `FontSettings` إلى ربط رد نداء التحذير الذي يخبرك بالضبط أي الرموز تم استبدالها.

> **TL;DR:** في النهاية ستحصل على تطبيق C# console جاهز للتشغيل يسجل كل استبدال للخطوط، مما يتيح لك اتخاذ قرار ما إذا كنت ستضمّن بديلًا أو تنبه المستخدم.

---

## المتطلبات المسبقة

- .NET 6 SDK (أو أي نسخة .NET حديثة)  
- Visual Studio 2022 أو VS Code مع امتدادات C#  
- ترخيص Aspose.Words لـ .NET (الإصدار التجريبي المجاني يكفي لهذا العرض)  
- ملف DOCX تجريبي يشير إلى خط غير مثبت لديك (مثال: *Comic Sans MS* على نظام Linux)  

لا توجد حزم NuGet خاصة مطلوبة بخلاف `Aspose.Words`.

---

## الخطوة 1 – تثبيت Aspose.Words وإعداد المشروع

أولًا، أنشئ مشروع console جديد وأضف مكتبة Aspose.Words إلى المشروع.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** إذا كان لديك حل بالفعل، فقط أضف الحزمة عبر واجهة NuGet Package Manager—هذا يجعل تتبع الإصدارات أسهل.

---

## الخطوة 2 – إنشاء FontSettings (الكلمة المفتاحية الأساسية تظهر هنا)

خطوة **إنشاء FontSettings** هي الأساس لأي سير عمل مرتبط بالخطوط. `FontSettings` تخبر Aspose.Words أين يبحث عن الخطوط، سواءً باستخدام مجلدات النظام، وكيفية الرجوع عندما يكون شيء مفقودًا.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

لماذا هذا مهم؟ بدون `FontSettings` مُكوَّن بشكل صحيح، يستبدل المحرك الرموز المفقودة بصمت بخط النظام الافتراضي، ولن ترى أي تحذير.

---

## الخطوة 3 – ربط LoadOptions مع FontSettings

`LoadOptions` يتيح لك تمرير `FontSettings` إلى محمّل المستند. هذا هو الجسر الذي يسمح للمحرك **باكتشاف الخطوط المفقودة** أثناء مرحلة إنشاء `Document`.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

الآن في كل مرة تقوم بتحميل ملف DOCX باستخدام `loadOptions`، سيستشير Aspose.Words الـ `FontSettings` التي أعددناها مسبقًا.

---

## الخطوة 4 – إرفاق رد نداء التحذير لـ **تسجيل رسائل الخط**

Aspose.Words يصدر تحذيرات لمجموعة متنوعة من الحالات—استبدال الخط هو أحدها الشائع. من خلال توفير تنفيذ لـ `IWarningCallback`، يمكنك **تسجيل رسائل الخط** في الوقت الفعلي.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### فئة معالج التحذير

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

حقل `info.Description` يحتوي على رسالة قابلة للقراءة من قبل الإنسان مثل *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* وهذا هو النوع بالضبط من المخرجات التي تحتاجها **للتعامل مع الخطوط المفقودة** بسلاسة.

---

## الخطوة 5 – تحميل المستند وترك رد النداء يقوم بعمله

مع ربط كل شيء، يصبح تحميل المستند بسيطًا. إذا كان الملف المصدر يشير إلى خط غير موجود في النظام، سيُطلق معالج التحذير الخاص بنا.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

عند تشغيل البرنامج، سترى مخرجات console مشابهة لـ:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

هذه المخرجات هي جزء **تسجيل رسائل الخط** من سير العمل لدينا. يمكنك توسيع المعالج لتسجيل إلى ملف، إرسال بيانات قياس، أو حتى إلغاء التحويل إذا كانت الخطوط الحرجة مفقودة.

---

## الخطوة 6 – مثال كامل يعمل (جميع الأجزاء معًا)

فيما يلي برنامج كامل جاهز للنسخ واللصق. الصقه في `Program.cs`، عدّل مسارات الملفات، ثم نفّذ `dotnet run`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### النتيجة المتوقعة

تشغيل البرنامج على جهاز لا يحتوي على *Comic Sans MS* سيطبع شيئًا مشابهًا لـ:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

سيتولد أيضًا ملف `Result.pdf` يستخدم الخطوط المستبدلة، مما يضمن أن التحويل لن يتعطل.

---

## أسئلة شائعة وحالات خاصة

| السؤال | الجواب |
|----------|--------|
| **ماذا لو أردت أن يفشل التحويل بدلاً من الاستبدال؟** | داخل `FontSubstitutionWarningHandler`، ارمِ استثناءً عندما يحتوي `info.Description` على اسم خط حاسم. |
| **هل يمكنني تضمين خط بديل تلقائيًا؟** | نعم. بعد اكتشاف خط مفقود، يمكنك تحميل `FontInfo` احتياطي من مسار معروف وإضافته إلى `fontSettings` عبر `fontSettings.SetFontsFolder`. |
| **هل يعمل هذا على Linux/macOS؟** | بالطبع. `FontSettings` يعمل عبر الأنظمة؛ فقط تأكد من أن المجلد الاحتياطي يحتوي على ملفات `.ttf` أو `.otf` المناسبة. |
| **هل رد النداء التحذيري آمن من حيث الخيوط؟** | يعمل رد النداء على نفس الخيط الذي يحمل المستند، لذا لا تحتاج إلى مزامنة إضافية لتسجيل console. في سيناريوهات متعددة الخيوط، احمِ الموارد المشتركة. |
| **كيف أسجل التحذيرات إلى ملف؟** | استبدل `Console.WriteLine` بـ `File.AppendAllText("font_warnings.log", ...)` أو استخدم أي إطار تسجيل (Serilog، NLog). |

---

## نصائح احترافية للتعامل مع الخطوط في بيئة الإنتاج

1. **تخزين نتائج البحث عن الخطوط مؤقتًا** – إعادة استخدام نفس كائن `FontSettings` عبر تحميلات مستندات متعددة يجنب عمليات مسح نظام الملفات المتكررة.  
2. **قائمة بيضاء للخطوط الحرجة** – إذا كانت علامتك التجارية تتطلب خطًا معينًا، تحقق من وجوده مبكرًا وأوقف العملية برسالة خطأ واضحة.  
3. **استخدام `SetFontFolder` بشكل متكرر** – ضبط `recursive: true` يضمن فحص المجلدات الفرعية، وهو مفيد عندما تقوم بشحن مجموعة خطوط كاملة.  
4. **الدمج مع `FontSubstitutionSettings`** – يمكنك ضبط قواعد الاستبدال بدقة (مثلاً، تفضيل الخطوط التي تحمل نفس اسم العائلة).  

---

## الخلاصة

لقد **أنشأنا للتو FontSettings**، وضبطنا `LoadOptions` لـ **اكتشاف الخطوط المفقودة**، وربطنا رد نداء ي **يسجل رسائل الخط**، وأظهرنا كيفية **معالجة الخطوط المفقودة** بطريقة نظيفة وجاهزة للإنتاج. يتضمن هذا التدفق بضع عشرات الأسطر من C#، لكنه يمنحك رؤية كاملة لمجال الخطوط في أي ملف DOCX تقوم بمعالجته.

بعد ذلك، قد تستكشف:
- **تضمين خطوط احتياطية** مباشرةً في ملف PDF الناتج (`PdfSaveOptions.FontEmbeddingMode`).  
- **استبدال الخطوط برمجيًا** بناءً على قواعد العلامة التجارية للشركة.  
- **دمج مع خط أنابيب CI** لتعليم المستندات التي تستخدم خطوطًا غير مصرح بها تلقائيًا.

جرّبه، عدّل معالج التحذير ليناسب احتياجاتك، ودع خطوط أنابيب المستندات تعمل بثقة—بدون أي خلل غامض في التخطيط ناتج عن استبدال الخطوط غير المرئي.

برمجة سعيدة! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}