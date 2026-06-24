---
category: general
date: 2026-05-23
description: ضبط رد النداء للتحذير في Aspose لالتقاط تحذيرات استبدال الخطوط في Aspose.Words.
  تعلّم LoadOptions و FontSettings وتنفيذ IWarningCallback.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: ar
og_description: تعيين رد نداء التحذير في Aspose لمراقبة استبدال الخطوط في Aspose.Words.
  يوضح هذا الدليل كيفية استخدام LoadOptions و FontSettings وتنفيذ معالج التحذير.
og_title: تعيين رد النداء للتحذير في Aspose – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: تعيين رد النداء للتحذير Aspose – دليل شامل لتحميل مستند Word
url: /ar/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set warning callback aspose – دليل كامل لتحميل مستندات Word

هل تساءلت يومًا كيف **set warning callback aspose** حتى لا تفوت أي تنبيه باستبدال الخط مرة أخرى؟ أنت لست وحدك. عندما يشير ملف DOCX إلى خط غير مثبت، يقوم Aspose.Words باستبداله بصمت، وبدون رد نداء مناسب قد لا تعرف أن شيئًا قد تغير.

في هذا الدرس سنستعرض مثالًا كاملاً قابلًا للتنفيذ يوضح بالضبط كيفية التقاط تلك التحذيرات. في النهاية ستفهم **Aspose.Words LoadOptions**، وكيفية تكوين **FontSettings**، ولماذا تنفيذ **IWarningCallback** هو أنظف طريقة للبقاء على اطلاع. لا إطالة—فقط الشيفرة التي يمكنك إضافتها إلى مشروع .NET اليوم.

## ما ستتعلمه

- كيفية **set warning callback aspose** على كائن `LoadOptions`.  
- دور **Aspose.Words LoadOptions** عند فتح مستند.  
- تكوين معالجة **Aspose fonts substitution** باستخدام `FontSettings`.  
- كتابة تنفيذ مخصص لـ **IWarningCallback** لتسجيل مشاكل الخطوط.  
- تحميل مستند بأمان مع أفضل ممارسات **Aspose document loading**.

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (تعمل الشيفرة أيضًا على .NET Framework 4.5+).  
- رخصة صالحة لـ Aspose.Words for .NET أو مفتاح تجريبي.  
- Visual Studio أو Rider أو أي محرر C# تفضله.  
- ملف DOCX تجريبي (`fontTest.docx`) يشير إلى خط مفقود (اختياري لكن مفيد).

> **نصيحة محترف:** إذا لم يكن لديك ملف DOCX بخط مفقود، فقط أعد تسمية خط في نمط المستند وشاهد التحذير يُطلق.

---

## كيفية **set warning callback aspose** لتحميل المستند

البرنامج الكامل المستقل موجود أدناه. احفظه باسم `Program.cs`، استعد حزم NuGet، ثم شغّله. سيطبع الطرفية كل تحذير باستبدال خط تولده Aspose.Words أثناء تحميل الملف.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### ناتج الطرفية المتوقع

إذا كان `fontTest.docx` يشير إلى خط غير مثبت، ستظهر لك رسالة مشابهة لـ:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

إذا كانت جميع الخطوط موجودة، السطر الوحيد المطبع سيكون *Document loaded successfully*—بدون تحذيرات، بدون ضوضاء.

![set warning callback aspose example](image.png "set warning callback aspose example")

---

## فهم LoadOptions في Aspose.Words

`LoadOptions` هو البوابة لكل تعديل يمكنك إجراؤه على **aspose document loading**. يتيح لك:

1. **تحديد `FontSettings` مخصص** – مفيد عندما يوزع تطبيقك خطوطه الخاصة.  
2. **إرفاق رد نداء تحذير** – بالضبط ما فعلناه لالتقاط استبدالات الخطوط.  
3. التحكم في اكتشاف تنسيق المستند، معالجة كلمة المرور، وأكثر.

نظرًا لأن `LoadOptions` يُمرَّر إلى مُنشئ `Document`، تُطبق الإعدادات **مرة واحدة**، في اللحظة التي يتم فيها تحليل الملف. لهذا نضمن أن معالج التحذير سيُلاحظ كل استبدال قبل أن يُبنى المستند في الذاكرة.

### متى تستخدم LoadOptions مخصصًا

- **معالجة دفعات** من ملفات متعددة حيث تريد استراتيجية تسجيل موحدة.  
- **الخدمات السحابية** التي تحتاج إلى إبلاغ المستدعي بالخطوط المفقودة.  
- **خطوط الأنابيب الاختبارية** التي تتحقق من التزام المستندات بسياسة الخطوط المؤسسية.

---

## تكوين FontSettings لاستبدال خطوط Aspose

كائن `FontSettings` يتحكم في طريقة حل Aspose.Words للخطوط. بشكل افتراضي يبحث في مجلدات الخطوط بالنظام، ثم يلجأ إلى البدائل المدمجة. يمكنك ضبط هذا السلوك:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

هذه الأسطر اختيارية لسيناريو **set warning callback aspose** الأساسي، لكنها توضح كيف يمكنك **تقليل** عدد تحذيرات الاستبدال بتوفير الخطوط المناسبة مسبقًا.

---

## تنفيذ IWarningCallback لتحذيرات استبدال الخطوط

واجهة `IWarningCallback` صغيرة جدًا—فقط طريقة `Warning` واحدة. ومع ذلك تمنحك **تحكمًا كاملاً** في طريقة معالجة التحذيرات:

- **تسجيل إلى ملف** بدلاً من الطرفية.  
- **جمع التحذيرات** في قائمة للتحليل لاحقًا.  
- **إلقاء استثناءات** للتحذيرات الحرجة (مثلًا عندما يكون خط مطلوب مفقود).

إليك مثال سريع يخزن التحذيرات في `List<string>`:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

يمكنك بعد ذلك فحص `handler.Messages` بعد تحميل المستند لتقرر ما إذا كنت ستوقف المعالجة.

---

## تحميل مستند مع معالجة تحذيرات مخصصة (سير عمل كامل)

بدمج كل ما سبق، النمط النهائي الذي ستعيد استخدامه يبدو هكذا:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

هذا المقتطف يوضح تدفق **aspose document loading** الذي ستستخدمه في الإنتاج: تكوين، تحميل، ثم رد فعل. النمط يتوسع بسهولة سواء كنت تعالج ملفًا واحدًا أو تتنقل عبر آلاف الملفات.

---

## أسئلة شائعة وحالات حافة

**ماذا لو كان المستند محميًا بكلمة مرور؟**  
أضف `Password = "secret"` إلى مُهيئ `LoadOptions`. سيظل رد نداء التحذير يعمل بمجرد فك تشفير الملف.

**هل سيُطلق الرد نداءً لأنواع تحذيرات أخرى؟**  
نعم—`WarningInfo.Type` يمكن أن يكون `DocumentStructure`، `UnsupportedFileFormat`، إلخ. في مثالنا نُفلتر لـ `FontSubstitution`، لكن يمكنك تسجيل كل شيء بإزالة شرط `if`.

**هل يؤثر هذا على الأداء؟**  
تأثيره ضئيل. يتم استدعاء الرد نداء فقط عند حدوث تحذير، وهو أقل تواترًا من خطوات التحليل العادية.

**هل يمكنني تعطيل استبدال الخطوط تمامًا؟**  
يمكنك ضبط `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` لكن حينها سيُطلق Aspose.Words استثناءً للخطوط المفقودة بدلًا من استبدالها.

---

## الخلاصة

أنت الآن تعرف بالضبط كيف **set warning callback aspose** لمراقبة أحداث استبدال الخطوط أثناء معالجة **Aspose.Words LoadOptions**. من خلال تكوين `FontSettings`، تنفيذ `IWarningCallback` خفيف الوزن، وتحميل المستند بهذه الخيارات، تحصل على رؤية كاملة لأي تغييرات خطوط يجريها Aspose خلف الكواليس.

من هنا يمكنك:

- توسيع معالج التحذير لكتابة السجلات إلى خدمة تسجيل مركزية.  
- دمج الرد نداء مع استراتيجية بديلة مخصصة للخطوط.  
- استخدام النمط عند بناء واجهة API سحابية تتحقق من المستندات التي يرفعها العملاء.

جرّبه مع ملفات DOCX الخاصة بك، عدّل `FontSettings`، وشاهد الطرفية تُخبرك بالخطوط التي تم استبدالها. برمجة سعيدة، ولتظهر مستنداتك دائمًا كما هو مقصود!

## دروس ذات صلة

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}