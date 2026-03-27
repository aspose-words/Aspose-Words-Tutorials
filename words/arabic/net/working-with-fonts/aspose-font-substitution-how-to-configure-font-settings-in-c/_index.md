---
category: general
date: 2026-03-27
description: 'استبدال الخطوط في Aspose بسهولة: تعلم كيفية تكوين إعدادات الخط، التقاط
  التحذيرات، ومعالجة الخطوط المفقودة في تطبيقات .NET الخاصة بك.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: ar
og_description: إتقان استبدال الخطوط في Aspose عن طريق تكوين إعدادات الخط ومعالجة
  الخطوط المفقودة باستخدام رد نداء تحذيري. دليل كامل بلغة C#.
og_title: استبدال الخطوط في Aspose – تكوين إعدادات الخط في C#
tags:
- Aspose.Words
- C#
- Font Management
title: استبدال الخطوط في Aspose – كيفية تكوين إعدادات الخط في C#
url: /ar/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – دليل كامل لتكوين إعدادات الخطوط

هل صادفت مستندًا يقوم فجأة باستبدال الخط المخصص الخاص بك بشيء عام؟ هذا هو **aspose font substitution** يقوم بعمله — استبدال الخطوط المفقودة بأقرب تطابق يمكنه العثور عليه. إنه مفيد، ولكن إذا كنت بحاجة إلى معرفة *بالضبط* أي خط تم استبداله، عليك الاستفادة من نظام التحذير في المكتبة وتكوين إعدادات الخطوط بنفسك.

> **ما ستحتاجه**  
> • .NET 6+ (or .NET Framework 4.7.2+)  
> • Aspose.Words for .NET (latest NuGet)  
> • A DOCX that references a missing font (we’ll call it `MissingFont.docx`)  

هيا نبدأ.

---

## الخطوة 1: تثبيت Aspose.Words وتحضير المشروع

قبل كتابة أي كود، تأكد من الإشارة إلى حزمة Aspose.Words:

```bash
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** استخدم أحدث نسخة مستقرة؛ حتى مارس 2026 الإصدار هو 23.11.0. الإصدارات الأحدث تحسن خوارزميات مطابقة الخطوط وتضيف أنواع تحذير إضافية.

أنشئ تطبيقًا جديدًا من نوع console (أو ضع الكود في مشروع موجود) وأضف توجيهات `using` المعتادة:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

هذه المساحات الاسمية تمنحنا الوصول إلى `Document` و `LoadOptions` والفئات المتعلقة بالخطوط التي سنحتاجها.

## الخطوة 2: تكوين إعدادات الخطوط باستخدام LoadOptions

جوهر التحكم في **aspose font substitution** يكمن في `LoadOptions.FontSettings`. من خلال توفير كائن `FontSettings` فارغ نخبر Aspose باستخدام مسارات البحث الافتراضية *و* الإبلاغ عن أي استبدال عبر رد نداء التحذير.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

لماذا لا نكتفي بالإعدادات الافتراضية؟ لأن ربط رد نداء التحذير (الخطوة التالية) يعمل فقط عندما تكون خاصية `FontSettings` غير فارغة. هذه السطر الصغير يمنحنا نقطة ربط بعملية الاستبدال دون تغيير سلوك البحث الفعلي عن الخطوط.

## الخطوة 3: ربط رد نداء التحذير لالتقاط عمليات الاستبدال

Aspose.Words يطبق واجهة `IWarningCallback`. كلما حدث شيء جدير بالذكر — مثل خط مفقود — يستدعي طريقة `Warning` الخاصة بنا. سنقوم بتنفيذ معالج صغير يفلتر `WarningType.FontSubstitution` ويطبع الوصف.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

وهنا المعالج نفسه:

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **لماذا هذا مهم** – بدون رد نداء التحذير، يقوم Aspose باستبدال الخطوط بصمت، ولن تعرف أي خط تم استخدامه. يجعل رد نداء التحذير العملية شفافة، وهو أمر أساسي لتقارير الامتثال أو لتصحيح مشكلات التخطيط.

## الخطوة 4: تحميل المستند باستخدام الخيارات المكوَّنة

الآن نقوم أخيرًا بتحميل المستند، مع تمرير `loadOptions` التي أعددناها للتو. إذا كان الملف المصدر يشير إلى خط غير مثبت، سيتفاعل معالجنا.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

استبدل `YOUR_DIRECTORY` بالمسار الفعلي حيث يوجد `MissingFont.docx`. عند تشغيل البرنامج، يجب أن ترى مخرجات مشابهة لـ:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

هذا السطر يخبرك بالضبط أي خط كان مفقودًا وأي خط بديل اختارته Aspose.

## الخطوة 5: (اختياري) تحسين مسارات البحث عن الخطوط

إذا كان لديك مجلد خاص يحتوي على خطوط الشركة، يمكنك إخبار Aspose بمكان البحث قبل أن يلجأ إلى خطوط النظام. هذا استخدام متقدم لـ **configure font settings**:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

تعيين `recursive: true` يجعل Aspose يفحص المجلدات الفرعية أيضًا. الآن ستجرب المكتبة خطوطك الخاصة أولاً، مما يقلل من احتمال الاستبدال غير المرغوب.

## مثال كامل يعمل

بجمع كل شيء معًا، إليك البرنامج الكامل الجاهز للتنفيذ:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**المخرجات المتوقعة** (عند مواجهة خط مفقود):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

إذا كانت جميع الخطوط موجودة، يعمل البرنامج بصمت (بدون تحذيرات) ولا يزال ينتج ملف PDF.

## أسئلة شائعة وحالات خاصة

### ماذا لو أردت *منع* الاستبدال تمامًا؟

قم بتعيين `FontSettings.SubstitutionSettings` إلى `null` أو استخدم `FontSettings.FontSubstitutionSettings` للتحكم في السلوك. على سبيل المثال:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

الآن سيطرح Aspose استثناءً بدلاً من الاستبدال الصامت، ويمكن التقاطه ومعالجته.

### هل يعمل هذا مع صيغ ملفات أخرى (مثل .doc، .rtf)؟

بالطبع. يمكن تمرير كائن `LoadOptions` نفسه إلى أي مُنشئ `Document` يقبل مسار ملف. سيُستدعى رد نداء التحذير لجميع الصيغ التي تعتمد على الخطوط.

### هل يمكنني التقاط اسم الخط البديل *بالضبط*؟

نعم. يحتوي سلسلة `info.Description` على كل من الخط المفقود والبديل. إذا كنت بحاجة إلى الاسم برمجيًا، يمكنك تحليله أو استخدام كائن `FontInfo` (متاح في الإصدارات الأحدث).

### كيف يتصرف هذا في بيئة متعددة الخيوط؟

`FontSettings` **ليس** آمنًا للمتعدد الخيوط. أنشئ `LoadOptions` منفصل (مع `FontSettings` الخاص به) لكل خيط، أو احمِ الوصول باستخدام قفل.

## الخلاصة

لقد غطينا كل ما تحتاجه لإتقان **aspose font substitution** و **configure font settings** في تطبيق C#:

1. تثبيت Aspose.Words وإضافة توجيهات `using` اللازمة.  
2. إنشاء كائن `LoadOptions` مع `FontSettings` جديد.  
3. ربط `IWarningCallback` مخصص لعرض أحداث الاستبدال.  
4. تحميل المستند، والسماح لرد نداء التحذير بالإبلاغ عن أي خطوط مفقودة.  
5. (اختياري) توسيع مسار البحث أو تعطيل الاستبدال تمامًا.

مع هذا النمط يمكنك تسجيل الخطوط المفقودة للامتثال، تنبيه المستخدمين في واجهة المستخدم، أو تضمين الخطوط البديلة تلقائيًا قبل النشر. بعد ذلك، قد تستكشف **سياسات استبدال خطوط Aspose.Words** أو تدمج سير العمل في خط أنابيب معالجة مستندات أكبر.

برمجة سعيدة، ولتظهر مستنداتك دائمًا بالخط المناسب!  

---  

![مخطط يوضح Aspose.Words يقوم بتحميل مستند، يستدعي FontSettings، يُطلق رد نداء التحذير، ويُخرج معلومات الاستبدال](image-placeholder.png "سير عمل استبدال خطوط Aspose")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}