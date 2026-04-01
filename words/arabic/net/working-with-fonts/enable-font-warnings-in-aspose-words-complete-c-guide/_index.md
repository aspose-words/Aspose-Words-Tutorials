---
category: general
date: 2026-04-01
description: تمكين تحذيرات الخط أثناء تحميل مستندات Word باستخدام Aspose.Words. تعلّم
  كيفية التقاط أحداث استبدال الخط باستخدام LoadOptions وإعدادات الخط في C#.
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: ar
og_description: تمكين تحذيرات الخط أثناء تحميل مستندات Word باستخدام Aspose.Words.
  يوضح هذا البرنامج التعليمي كيفية التقاط أحداث استبدال الخط في C#.
og_title: تمكين تحذيرات الخطوط في Aspose.Words – دليل C# الكامل
tags:
- Aspose.Words
- C#
- Font Management
title: تفعيل تحذيرات الخطوط في Aspose.Words – دليل C# الكامل
url: /ar/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تمكين تحذيرات الخطوط في Aspose.Words – دليل C# الكامل

هل تساءلت يوماً لماذا يبدو مستند Word مختلفًا فجأة بعد تحميله برمجياً؟ **قم بتمكين تحذيرات الخطوط** وستعرف فورًا متى تقوم Aspose.Words باستبدال خط مفقود بخط بديل. في هذا الدرس سنستعرض مثالًا عمليًا لا يكتشف هذه الاستبدالات فحسب، بل يوضح أيضًا *سبب* حدوثها.

سنغطي كل ما تحتاجه للبدء: حزمة NuGet المطلوبة، تكوين `LoadOptions` الدقيق، وإخراج منسق في وحدة التحكم يوضح لك أي الخطوط تم استبدالها. في النهاية ستحصل على نمط ثابت وقابل لإعادة الاستخدام لمعالجة المستندات بـ **C#** يعمل مع أي إصدار من Aspose.Words.

## ما ستتعلمه

- كيفية إنشاء كائن `LoadOptions` يتتبع تغيّر الخطوط.  
- هدف حدث `SubstitutionWarning` وكيفية ربطه.  
- عينة كود كاملة قابلة للتنفيذ تطبع تحذيرات واضحة في وحدة التحكم.  
- نصائح للتعامل مع الحالات الخاصة مثل المستندات التي تحتوي فقط على خطوط قياسية.  

لا تحتاج إلى خبرة سابقة في Aspose.Words—فقط إلمام أساسي بـ C# و .NET.

---

![Enable font warnings diagram](placeholder-image.png "Enable font warnings diagram")
*نص بديل: مخطط تمكين تحذيرات الخطوط يوضح تدفق الحدث عند استبدال خط مفقود.*

## الخطوة 1: إعداد LoadOptions وتمكين تحذيرات الخطوط

أول شيء تحتاجه هو كائن `LoadOptions`. هذا الحاوي يخبر Aspose.Words كيف يتعامل مع الملف الذي ستقوم بتحميله. من خلال تعيين نسخة جديدة من `FontSettings` تفتح الباب أمام الأحداث المتعلقة بالخطوط.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**لماذا هذا مهم:**  
إذا تخطيت تعيين `FontSettings`، ستستمر Aspose.Words في استبدال الخطوط المفقودة، لكنك لن تتلقى أي إشعار. آلية التحذير موجودة داخل `FontSettings`، لذا فإن تهيئتها *ضرورية* لهدفنا.

> **نصيحة احترافية:** يمكنك أيضًا توجيه `FontSettings` إلى مجلد خطوط مخصص باستخدام `SetFontsFolder`. سيقلل ذلك من عدد التحذيرات التي ستراها، لأن Aspose.Words سيستطيع العثور فعليًا على الخطوط المفقودة.

## الخطوة 2: الاشتراك في حدث SubstitutionWarning (استبدال الخط)

الآن بعد أن أصبح كائن `FontSettings` موجودًا، نقوم بربطه بحدث `SubstitutionWarning`. هذا الحدث يُطلق **في كل مرة** تستبدل فيها Aspose.Words خطًا مطلوبًا بخط آخر.

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**لماذا هذا مهم:**  
بدون هذا المستمع لن تكون لديك رؤية لعملية الاستبدال. سطر وحدة التحكم يمنحك مسار تدقيق سريع، وهو مفيد خصوصًا أثناء عمليات البناء الآلية أو عند إنشاء ملفات PDF لصناعات تتطلب امتثالًا عاليًا.

> **سؤال شائع:** *ماذا لو أردت كتم التحذيرات؟*  
> يمكنك ببساطة فصل المعالج أو تعيين `FontSettings.SubstitutionWarning += null;`. ومع ذلك، عادةً ما يكون إبقاء التحذيرات هو الخيار الأكثر أمانًا لأن الاستبدالات الصامتة قد تؤدي إلى تشوهات في التخطيط.

## الخطوة 3: تحميل المستند باستخدام الخيارات المكوَّنة (معالجة مستندات C#)

مع نظام التحذير جاهزًا، يصبح تحميل المستند أمرًا بسيطًا. مرّر كائن `LoadOptions` إلى مُنشئ `Document`، وستتولى Aspose.Words البقية.

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**لماذا هذا مهم:**  
كائن `LoadOptions` هو الجسر بين الملف الخام وبنية التحذير. إذا حذفته، سيُحمَّل المستند بصمت، وستُستبدل أي خطوط مفقودة دون أي أثر.

> **حالة خاصة:** بعض المستندات تُضمّن ملفات الخطوط التي تحتاجها بالضبط. في هذه الحالة لن يظهر أي تحذير لأن Aspose.Words سيجد الخط المضمّن. الكود أعلاه سيظل يعمل؛ ستحصل فقط على إخراج فارغ في وحدة التحكم.

## الخطوة 4: التحقق من الإخراج والمشكلات الشائعة

شغِّل البرنامج من موجه الأوامر أو من مصحح الأخطاء في بيئتك التطويرية. إذا كان المستند الأصلي يحتوي على خط غير مثبت على الجهاز (أو غير متوفر في مجلد الخطوط المخصص)، ستظهر لك أسطر مثل:

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

إذا لم يُطبع شيء، فإما أن:

1. تم العثور على جميع الخطوط، **أو**  
2. لم يتم ربط معالج `SubstitutionWarning` بشكل صحيح (تحقق مرة أخرى من الخطوة 2).

### لماذا تحدث استبدالات الخطوط؟

- **خط نظام مفقود:** نظام التشغيل لا يملك الخط المطلوب.  
- **صيغة خط غير مدعومة:** Aspose.Words يمكنه قراءة TrueType و OpenType، لكن ليس كل الصيغ المملوكة.  
- **قيود الترخيص:** بعض الخطوط التجارية تمنع التضمين، مما يجبر على استخدام بديل.

فهم *السبب* يساعدك على اتخاذ قرار ما إذا كنت ستوزع الخطوط المفقودة مع تطبيقك أو تعدل تنسيق المستند.

## إضافي: التحكم في الخط البديل

إذا أردت أن يتحول كل خط مفقود إلى عائلة محددة (مثلاً “Calibri”)، يمكنك تعيين قاعدة استبدال عامة:

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

الآن ستستمر وحدة التحكم في تحذيرك، لكن النتيجة البصرية ستكون متسقة عبر جميع الخطوط المفقودة.

---

## ملخص

- **تمكين تحذيرات الخطوط** بإنشاء `LoadOptions` مع `FontSettings` جديد.  
- ربط حدث `SubstitutionWarning` للحصول على تنبيهات فورية كلما تم استبدال خط.  
- تحميل المستند باستخدام الخيارات المكوَّنة، واختياريًا حفظه كـ PDF لملاحظة التأثير البصري.  
- تشخيص سبب الاستبدال، وإذا لزم الأمر، فرض خط بديل محدد.

لقد أضفت الآن شبكة أمان إلى سير عمل **Aspose.Words** تمنع تغييرات التخطيط الصامتة. بعد ذلك، يمكنك استكشاف **إعدادات الخط** مثل `DefaultFontName` أو الغوص في خيارات **عرض المستند** لضبط مخرجات PDF بدقة.

---

### ماذا تجرب بعد ذلك؟

- **استكشاف ميزات أخرى في FontSettings**: `SetFontsFolder`، `LoadFontSources`، و `DefaultFontName`.  
- **دمج التحذيرات مع أطر تسجيل** (Serilog، NLog) لتشخيصات جاهزة للإنتاج.  
- **تجربة صيغ مستندات مختلفة** (`.doc`، `.rtf`، `.html`) لمعرفة كيفية تعامل كل منها مع الخطوط المفقودة.  

هل لديك أسئلة أو سيناريو غريب؟ اترك تعليقًا أدناه، ونتمنى لك برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}