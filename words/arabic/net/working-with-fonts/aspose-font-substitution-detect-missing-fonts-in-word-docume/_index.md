---
category: general
date: 2026-04-05
description: دليل استبدال الخطوط من Aspose لاكتشاف الخطوط المفقودة أثناء تحميل مستند
  Word. تعلّم كيفية تكوين إعدادات الخطوط ومعالجة الخطوط المفقودة بكفاءة.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: ar
og_description: دليل استبدال الخطوط من Aspose لاكتشاف الخطوط المفقودة أثناء تحميل
  مستند Word. تعلّم كيفية تكوين إعدادات الخطوط ومعالجة الخطوط المفقودة بفعالية.
og_title: استبدال الخطوط في Aspose – اكتشاف الخطوط المفقودة في مستندات Word
tags:
- Aspose.Words
- C#
- Font Management
title: استبدال الخطوط في Aspose – اكتشاف الخطوط المفقودة في مستندات Word
url: /ar/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استبدال الخطوط في Aspose – اكتشاف الخطوط المفقودة في مستندات Word

هل صادفت يومًا ملف Word يبدو مثاليًا على جهاز واحد لكنه يظهر تغييرات غريبة في الخطوط على جهاز آخر؟ هذه هي المشكلة الكلاسيكية **aspose font substitution**، وعادةً ما تعني أن بعض الخطوط مفقودة على النظام المستهدف. في هذا الدرس سنوضح لك خطوة بخطوة كيفية **اكتشاف الخطوط المفقودة** عند **تحميل مستند Word**، وكيفية **تكوين إعدادات الخطوط**، وما يجب فعله **للتعامل مع الخطوط المفقودة** بشكل سلس.

سنستعرض مثالًا كاملًا وقابلًا للتنفيذ بلغة C#، نشرح لماذا كل سطر مهم، وحتى نعرض لك مخرجات وحدة التحكم المتوقعة. بنهاية الدرس ستكون قادرًا على اكتشاف استبدال الخطوط في اللحظة التي يتم فيها تحميل المستند—دون الحاجة للتخمين.

## ما ستتعلمه

- كيفية تمكين جامع التشخيص في Aspose.Words لتحذيرات الخطوط.  
- الكود الدقيق اللازم **لتحميل مستند Word** مع **إعدادات خطوط** مخصصة.  
- كيفية التكرار على كائنات `WarningInfo` لسرد كل خط تم استبداله.  
- نصائح لكتم التحذيرات غير المرغوب فيها أو توفير خطوط احتياطية.  
- عينة جاهزة للتنفيذ يمكنك نسخها ولصقها في Visual Studio.

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (تعمل الواجهة البرمجية بنفس الطريقة على .NET Framework).  
- Aspose.Words for .NET (حزمة NuGet `Aspose.Words`).  
- ملف Word يحتوي على خط غير مثبت لديك (مثال: `MissingFont.docx`).  

إذا كان لديك هذه المتطلبات، فلنبدأ.

## الخطوة 1 – تمكين جامع التشخيص (تكوين إعدادات الخطوط)

أولًا وقبل كل شيء: Aspose.Words يسجل تحذيرات استبدال الخطوط فقط إذا طلبت ذلك. يتم ذلك بإنشاء كائن `FontSettings` وتعيينه إلى مثيل `LoadOptions`. فكر في ذلك كتشغيل “أضواء التصحيح” لمعالجة الخطوط.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**لماذا؟**  
بدون كائن `FontSettings` يبقى جامع التحذيرات صامتًا، ولن تعرف أبدًا أي الخطوط تم استبدالها. بتهيئته فارغًا نسمح لـ Aspose باستخدام خطوط النظام الافتراضية *و* تتبع أي استبدالات.

> **نصيحة احترافية:** إذا كنت تعرف أن مجلدًا معينًا يحتوي على خطوط الشركة، فوجه `FontSettings` إليه باستخدام `SetFontsFolder("path")`. يمكن أن يقلل ذلك من عدد تحذيرات الخطوط المفقودة.

## الخطوة 2 – تحميل المستند باستخدام الخيارات المكوَّنة (Load Word Document)

الآن بعد أن تم تفعيل الجامع، قم بتحميل ملف `.docx` الخاص بك باستخدام نفس `LoadOptions`. هذه هي اللحظة التي يقوم فيها Aspose بفحص المستند، والبحث عن كل إشارة إلى خط، وتحديد ما إذا كان هناك حاجة لاستبدال.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**لماذا هذا مهم؟**  
إذا قمت ببساطة باستدعاء `new Document("MissingFont.docx")`، فستُطبق الإعدادات الافتراضية *وسيظل* قائمة التحذيرات فارغة. تمرير `loadOptions` يضمن أن جامع التشخيص متصل بعملية تحميل المستند.

## الخطوة 3 – استرجاع وعرض تحذيرات استبدال الخطوط (اكتشاف الخطوط المفقودة)

بعد تحميل المستند في الذاكرة، يقوم Aspose بتخزين أي تحذيرات في `document.WarningCallback.Warnings`. قم بالتكرار عبر تلك المجموعة، صَفِّها حسب `WarningType.FontSubstitution`، واطبع الوصف. كل وصف يخبرك أي خط كان مفقودًا وأي خط استُبدل به.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**مخرجات وحدة التحكم المتوقعة**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

تُظهر هذه المخرجات بالضبط أي الخطوط مفقودة على الجهاز الذي يشغل الكود. الآن يمكنك اتخاذ قرار بتثبيت الخطوط المفقودة، أو تضمينها في المستند، أو الإبقاء على الاستبدال.

![مخرجات وحدة التحكم تُظهر تحذيرات استبدال الخطوط في Aspose](/images/aspose-font-substitution-console.png)

*نص بديل للصورة:* استبدال الخطوط في Aspose – مخرجات وحدة التحكم التي تسرد الخطوط المستبدلة

## الخطوة 4 – اختياري: تخصيص سلوك الاستبدال (التعامل مع الخطوط المفقودة)

أحيانًا لا تريد فقط معرفة *أن* استبدالًا قد حدث—بل تريد التحكم *في كيفية* حدوثه. يتيح لك Aspose.Words تسجيل قاعدة استبدال خطوط مخصصة `IFontSubstitutionRule`. أدناه مثال سريع يجبر أي خط مفقود على الرجوع إلى `Tahoma`.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**متى قد تستخدم هذا؟**  
إذا كنت تُنشئ ملفات PDF لخدمة ويب وتعلم أن كل عميل يمكنه عرض `Tahoma`، فإن إجبار الرجوع يضمن اتساقًا بصريًا دون الحاجة لإرسال عشرات ملفات الخطوط.

## مثال كامل يعمل (جميع الخطوات مجمعة)

إليك البرنامج الكامل الذي يمكنك لصقه في مشروع وحدة تحكم جديد. يتجميع كما هو، بشرط أن تكون قد ثبت حزمة NuGet الخاصة بـ Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

شغّل البرنامج، راقب وحدة التحكم، وسترى كل حدث خط مفقود يُطبع. من هناك يمكنك اتخاذ قرار بتثبيت الخطوط المفقودة، أو تضمينها، أو الإبقاء على الرجوع.

## الأسئلة المتكررة

**س: هل يعمل هذا مع تحويل PDF؟**  
نعم. عندما تستدعي لاحقًا `doc.Save("output.pdf")`، ستكون أي خطوط تم استبدالها أثناء التحميل هي التي تُضمّن في ملف PDF. لذا فإن التقاط التحذيرات مبكرًا يساعدك على تجنّب تغييرات الخط المفاجئة في PDF النهائي.

**س: ماذا لو كان لدي العديد من المستندات للمعالجة؟**  
قم بلف منطق التحميل داخل كتلة try‑catch وأعد استخدام كائن `FontSettings` واحد عبر المستندات. هذا يقلل من الحمل ويحافظ على نشاط جامع التحذيرات لكل ملف.

**س: هل يمكنني كتم التحذيرات تمامًا؟**  
يمكنك تعيين `loadOptions.WarningCallback = null;` قبل التحميل، لكنك ستفقد القدرة على **اكتشاف الخطوط المفقودة**—وهو عادةً ليس ما تريد.

## الخلاصة

لقد غطينا كل ما تحتاجه لإتقان **aspose font substitution**: تمكين جامع التشخيص، تحميل ملف Word بإعدادات **خطوط** مخصصة، استخراج قائمة الخطوط المفقودة، وحتى تجاوز قاعدة الاستبدال الافتراضية لت **التعامل مع الخطوط المفقودة** بطريقتك. ببضع أسطر من C# تحصل على رؤية كاملة لمشكلات الخطوط التي كانت ستختفي خلف تغييرات تخطيطية دقيقة.

ما الخطوات التالية؟ جرّب تضمين الخطوط الأصلية في المستند باستخدام `FontSettings.SetFontsFolder` أو استكشف `FontSourceBase` لتحميل الخطوط من قاعدة بيانات. يمكنك أيضًا تجربة مجموعة `Document.BuiltInStyle` لمعرفة كيفية انتشار تغييرات الخط على مستوى الأنماط.

هل لديك المزيد من الأسئلة حول Aspose.Words أو إدارة الخطوط؟ اترك تعليقًا، استكشف وثائق Aspose الرسمية، أو ابدأ مشروعًا جديدًا وجرب الكود أعلاه. برمجة سعيدة، ولتظهر مستنداتك دائمًا كما هو مقصود!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}