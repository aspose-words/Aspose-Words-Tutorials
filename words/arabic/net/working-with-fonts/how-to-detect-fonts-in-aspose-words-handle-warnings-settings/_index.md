---
category: general
date: 2026-01-03
description: كيفية اكتشاف الخطوط في Aspose.Words ومعالجة التحذيرات باستخدام إعدادات
  خطوط Aspose – دليل خطوة بخطوة للمطورين.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: ar
og_description: كيفية اكتشاف الخطوط في Aspose.Words وتكوين التحذيرات باستخدام إعدادات
  خطوط Aspose. تعلم سير العمل الكامل في دقائق.
og_title: كيفية اكتشاف الخطوط في Aspose.Words – التعامل مع التحذيرات
tags:
- Aspose.Words
- C#
- Document Processing
title: كيفية اكتشاف الخطوط في Aspose.Words – التعامل مع التحذيرات والإعدادات
url: /ar/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية اكتشاف الخطوط في Aspose.Words – معالجة التحذيرات والإعدادات

هل تساءلت يومًا **عن كيفية اكتشاف الخطوط** في مستند Word قبل أن يصل إلى الإنتاج؟ لست الوحيد. فقدان الخطوط يمكن أن يسبب كوابيس في التخطيط، وبدون تحذيرات مناسبة قد تقوم بنشر ملف PDF أو DOCX معطوب دون أن تدرك ذلك.  

في هذا البرنامج التعليمي سنستعرض **كيفية اكتشاف الخطوط** باستخدام Aspose.Words، ونظهر **كيفية معالجة التحذيرات**، ونضبط **إعدادات خطوط Aspose** حتى تتمكن من **تكوين التحذيرات** بالطريقة التي تحتاجها. في النهاية ستحصل على مقطع جاهز للتنفيذ يطبع كل استبدال تقوم به Aspose، وستعرف كيفية تكييفه لمشاريعك الخاصة.

## المتطلبات المسبقة

- .NET 6+ (أو .NET Framework 4.6+).  
- Aspose.Words for .NET مثبت عبر NuGet (`Install-Package Aspose.Words`).  
- ملف Word يحتوي عمداً على إشارة إلى خط مفقود (مثال: *DocumentWithMissingFonts.docx*).  

إذا كان لديك هذه المتطلبات بالفعل، رائع—لنبدأ.

![لقطة شاشة لكيفية اكتشاف الخطوط](https://example.com/detect-fonts.png "مثال على إخراج اكتشاف الخطوط")

## كيفية اكتشاف الخطوط باستخدام Aspose.Words

الخطوة الأولى هي إخبار Aspose.Words بأنك تهتم بأحداث استبدال الخطوط. يتم ذلك عبر توفير رد نداء تحذير مخصص من خلال **إعدادات خطوط Aspose**. يتلقى رد النداء كائن `WarningInfo` لكل استبدال، مما يتيح لك **اكتشاف الخطوط** أثناء التشغيل.

### الخطوة 1: إنشاء فئة رد نداء التحذير

قم بتنفيذ واجهة `IWarningCallback`. داخل طريقة `Warning`، قم بفلترة `WarningType.FontSubstitution` وسجّل التفاصيل.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **نصيحة احترافية:** يحتوي النص `info.Description` على كل من اسم الخط المفقود والبديل الذي اختارته Aspose. يمكنك تحليله إذا كنت بحاجة إلى تقرير منظم.

### الخطوة 2: تكوين LoadOptions باستخدام إعدادات خطوط Aspose

أنشئ كائن `LoadOptions`، أرفق كائن `FontSettings` جديد، وعيّن `WarningCallback` إلى المعالج الذي أنشأناه للتو. هذا يخبر Aspose **كيفية تكوين التحذيرات**.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

إذا كان لديك مجلد خطوط خاص، يمكنك إضافته كالتالي:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

هذا السطر يوضح جانبًا آخر من **إعدادات خطوط Aspose**—أنت تتحكم تمامًا في المكان الذي تبحث فيه Aspose عن الخطوط قبل أن تقرر الاستبدال.

### الخطوة 3: تحميل المستند وتفعيل رد النداء

الآن قم بتحميل المستند المستهدف باستخدام `loadOptions`. أثناء تحليل Aspose للملف، أي خط مفقود سيُفعّل معالج التحذير، مما يؤدي إلى **اكتشاف الخطوط** في الوقت الفعلي.

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

عند تشغيل البرنامج، سترى مخرجات مشابهة لـ:

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### الخطوة 4: (اختياري) جمع التحذيرات للاستخدام لاحقًا

إذا كنت بحاجة لتخزين بيانات الاستبدال لتقرير، عدّل المعالج لتجميع الرسائل في قائمة.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

لاحقًا يمكنك كتابة `handler.Substitutions` إلى ملف JSON، إرساله إلى خدمة تسجيل، أو عرضه في واجهة المستخدم.

### الخطوة 5: التحقق من النتيجة برمجيًا

أحيانًا تريد التأكد من عدم حدوث أي استبدال (*لا*) (مثال: في بناء CI). إليك فحص سريع:

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

هذا المقتطف يوضح **كيفية معالجة التحذيرات** بطريقة حتمية، مما يمنحك سيطرة كاملة على خط أنابيب البناء.

## الأسئلة الشائعة (وحالات الحافة)

**ماذا لو احتجت لتجاهل بعض الاستبدالات؟**  
يمكنك إضافة منطق شرطي داخل `Warning` والعودة ببساطة دون تسجيل للخطوط التي تعتبرها مقبولة.

**هل يمكنني كتم جميع التحذيرات والحصول فقط على نتيجة منطقية؟**  
نعم—قم بتعيين `loadOptions.WarningCallback = null` ثم افحص `doc.FontInfo` بعد التحميل (مع أنك ستفقد السجل التفصيلي).

**هل يعمل هذا مع تحويل PDF؟**  
بالتأكيد. نفس آلية التحذير تُفعَّل عند استدعاء `doc.Save("out.pdf")`. سيُلتقط رد النداء أي تبديل للخطوط يتم أثناء خطوة التحويل.

**هل هناك تأثير على الأداء؟**  
العبء إضافي ضئيل—فقط بضع استدعاءات إضافية لكل خط مفقود. بالنسبة للدفعات الكبيرة، قد ترغب في تخزين النتائج مؤقتًا.

## الخلاصة: ما تم تغطيته

- **كيفية اكتشاف الخطوط** عبر تنفيذ `IWarningCallback` مخصص.  
- **كيفية معالجة التحذيرات** عبر `LoadOptions.WarningCallback`.  
- ضبط **إعدادات خطوط Aspose** (إضافة مجلدات خطوط مخصصة، تمكين/تعطيل التحذيرات).  
- **كيفية تكوين التحذيرات** لكل من الإخراج الفوري إلى وحدة التحكم والتحليل لاحقًا.  

مع وجود هذه العناصر، يمكنك معالجة مستندات Word بثقة، وضمان الإشارة إلى الخطوط المفقودة، والحفاظ على اتساق المخرجات عبر البيئات.

## الخطوات التالية

- استكشف `FontSettings.SubstitutionSettings` لمزيد من التحكم الدقيق (مثال: ربط خطوط مفقودة معينة ببدائل مختارة).  
- اجمع هذا النهج مع Aspose.PDF لإنشاء ملفات PDF تحتفظ بالخطوط الدقيقة.  
- أتمتة فحص التحذيرات في خط أنابيب CI/CD لحجب الإصدارات التي تحتوي على مشاكل خطوط—مثالي للفرق التي **تعالج التحذيرات** كجزء من بوابات الجودة.

هل لديك المزيد من الأسئلة حول **إعدادات خطوط Aspose** أو تحتاج مساعدة في دمج ذلك في خدمة أكبر؟ اترك تعليقًا أدناه، وتمنياتنا لك بالبرمجة السعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}