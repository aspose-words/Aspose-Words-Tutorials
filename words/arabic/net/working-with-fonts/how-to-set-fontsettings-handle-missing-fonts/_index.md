---
category: general
date: 2026-05-29
description: تعلم كيفية ضبط FontSettings في Aspose.Words ومعالجة الخطوط المفقودة بسلاسة.
  دليل خطوة بخطوة مع كود كامل وأفضل الممارسات.
draft: false
keywords:
- how to set fontsettings
- handle missing fonts
language: ar
og_description: كيفية ضبط FontSettings في Aspose.Words ومعالجة الخطوط المفقودة بسرعة.
  اتبع هذا الدليل للحصول على حل كامل وقابل للتنفيذ.
og_title: كيفية ضبط إعدادات الخط – التعامل مع الخطوط المفقودة
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
    gracefully. Step-by-step guide with complete code and best practices.
  headline: How to Set FontSettings – Handle Missing Fonts
  type: TechArticle
tags:
- Aspose.Words
- FontSettings
- C#
- Document Processing
title: كيفية ضبط إعدادات الخط – التعامل مع الخطوط المفقودة
url: /ar/net/working-with-fonts/how-to-set-fontsettings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية ضبط FontSettings – معالجة الخطوط المفقودة

هل تساءلت يومًا **كيفية ضبط FontSettings** عند العمل مع Aspose.Words وفجأة صادفت مستندًا يشير إلى خط غير مثبت لديك؟ هذه مشكلة شائعة، خاصةً عند معالجة ملفات يقدمها العميل على خادم يحتوي فقط على مجموعة خطوط قليلة. الخبر السار؟ يمكنك التقاط هذه الفجوات و**معالجة الخطوط المفقودة** دون أن يتعطل تطبيقك أو ينتج ملفات PDF غير جميلة.

في هذا الدرس سنستعرض سيناريو واقعي: تحميل ملف DOCX يطلب خط “Calibri” بينما حاوية Linux الخاصة بك لا تحتوي سوى على “DejaVu Sans”. ستشاهد بالضبط كيفية تكوين FontSettings، الاشتراك في تحذيرات الاستبدال، وتوفير خطوط احتياطية بحيث يتم عرض المستند كما قصده المؤلف. لا إطالة—فقط الكود الذي يمكنك إدراجه في مشروعك اليوم.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (تعمل الواجهة البرمجية بنفس الطريقة على .NET Framework 4.7+)
- Aspose.Words for .NET 23.10 أو أحدث (اسم حزمة NuGet هو `Aspose.Words`)
- بيئة تطوير C# أساسية (Visual Studio، Rider، أو VS Code)

إذا كان لديك هذه المتطلبات، لنبدأ.

## الخطوة 1: إنشاء FontSettings والاستماع إلى أحداث الاستبدال

قلب الحل هو كائن `FontSettings`. من خلال إرفاق معالج إلى حدث `FontSubstitutionWarning` ستحصل على تقرير فوري في كل مرة تحتاج فيها Aspose.Words إلى استبدال خط مفقود.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – initialize FontSettings
FontSettings fontSettings = new FontSettings();

// Subscribe to the warning event so we can log substitutions
fontSettings.FontSubstitutionWarning += (sender, e) =>
{
    // e.FontFamilyName – the name requested in the source document
    // e.SubstitutedFontFamilyName – the font actually used by the engine
    Console.WriteLine(
        $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
};
```

**لماذا هذا مهم:**  
عندما لا يتمكن المحرك من العثور على *Calibri*، قد ينتقل صامتًا إلى *Arial*. من خلال الاستماع إلى التحذير، تحتفظ بسجل شفاف—مثالي لتصحيح الأخطاء أو إعداد تقارير الامتثال.

> **نصيحة احترافية:** إذا شغلت هذا على خادم CI، وجه المخرجات إلى ملف سجل حتى تتمكن من مراجعة الخطوط المفقودة بعد تشغيل دفعة.

## الخطوة 2: إرفاق FontSettings إلى LoadOptions

`LoadOptions` هو البوابة للتحكم في طريقة تحليل المستند. من خلال تعيين `FontSettings` التي قمنا بتكوينها، ستحترم كل عملية تحميل `Document` لاحقة منطق الاستبدال الخاص بنا.

```csharp
// Step 2 – wire FontSettings into LoadOptions
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**ما الذي يحدث في الخلفية؟**  
أثناء مُنشئ `Document`، تقوم Aspose.Words بقراءة XML الخاص بـ DOCX، وتحديد مراجع الخطوط،—وإذا لم يُعثر على خط—تُطلق التحذير الذي أعددناه مسبقًا. بدون هذا الربط، لن تعرف أبدًا أن استبدالًا قد حدث.

## الخطوة 3: تحميل المستند و(اختياريًا) تعريف خطوط الاحتياط

الآن نُحمل الملف إلى الذاكرة. إذا كان لديك مجلد خطوط احتياطي (مثلاً دليل يحتوي على خطوط OpenType تُوزع مع تطبيقك)، أخبر `FontSettings` أين يبحث. هذه الخطوة اختيارية لكنها غالبًا الطريقة الأنظف *للتعامل مع الخطوط المفقودة*.

```csharp
// Optional: add a folder that contains fallback fonts
fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

// Step 3 – load the document using the prepared LoadOptions
Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);
```

**تنبيه حالة خاصة:**  
إذا كان المستند يحتوي على خط مخصص مضمّن كتيار ثنائي، ستستخدمه Aspose.Words تلقائيًا—لا حاجة للاستبدال. يُطلق التحذير فقط للخطوط النظامية *المفقودة*.

### التحقق من النتيجة

بعد التحميل، قد ترغب في حفظ المستند كـ PDF أو Word للتأكد من أن كل شيء يبدو صحيحًا.

```csharp
// Save as PDF to see the final rendering
doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
```

عند تشغيل البرنامج، سيطبع الطرفية سطورًا مثل:

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
```

إذا رأيت هذه الرسائل، فقد نجحت في **معالجة الخطوط المفقودة** وتعرف بالضبط أي استبدالات حدثت.

## الخطوة 4: متقدم – قواعد استبدال الخطوط المخصصة (اختياري)

أحيانًا تحتاج إلى تعيين حتمي، مثلاً استبدال *Times New Roman* دائمًا بـ *Liberation Serif*. يمكنك تحقيق ذلك باستخدام `FontSettings.SubstitutionTable`.

```csharp
// Define explicit substitution pairs
fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });
```

**لماذا العناء؟**  
القواعد الصريحة تمنحك التحكم في الطباعة، مما يضمن اتساق العلامة التجارية عبر ملفات PDF المُولدة، خاصةً عندما تُنتج مواد تسويقية.

## المشكلات الشائعة وكيفية تجنبها

| المشكلة | العرض | الحل |
|---------|---------|-----|
| **عدم ظهور تحذير** | تعتقد أن الخطوط سليمة لكن المستند يبدو غير صحيح. | تأكد من إرفاق `FontSubstitutionWarning` **قبل** تحميل المستند. |
| **مجلد الاحتياطي غير مفحوص** | لا تزال الاستبدالات تعود إلى خطوط النظام الافتراضية. | استدعِ `SetFontsFolder(path, true)` مع الوسيط الثاني `true` لتفحص المجلدات الفرعية. |
| **تباطؤ الأداء عند دفعات كبيرة** | تحميل 10k مستند يصبح بطيئًا. | خزن نسخة واحدة من `FontSettings` وأعد استخدامها عبر عمليات التحميل؛ تجنّب إنشائها في كل مرة. |
| **تجاهل الخطوط المضمّنة** | توقعت استخدام خط مضمّن مخصص، لكن حدث استبدال. | تحقق من أن ملف DOCX المصدر يضم الخط فعليًا (افتح Word → ملف → معلومات → خطوط). |

## مثال كامل يعمل

فيما يلي البرنامج الكامل الجاهز للنسخ واللصق. يوضح كل شيء من معالجة الأحداث إلى حفظ ملف PDF النهائي.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Set up FontSettings with a warning handler
        FontSettings fontSettings = new FontSettings();
        fontSettings.FontSubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
        };

        // Optional: point to a folder that contains fallback fonts
        fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

        // 2️⃣ Attach FontSettings to LoadOptions
        LoadOptions loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document that may have missing fonts
        Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);

        // 4️⃣ (Optional) Define explicit substitution rules
        fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
        fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });

        // 5️⃣ Save the result – PDF is a common target format
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);

        Console.WriteLine("Document processed and saved successfully.");
    }
}
```

**المخرجات المتوقعة في الطرفية** (مثال):

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
Document processed and saved successfully.
```

شغّل البرنامج، افتح `Output.pdf`، وسترى النص معروضًا بخطوط الاحتياط—لا مربعات أحرف مفقودة، ولا تعطل.

## الخلاصة

أصبح لديك الآن نمط قوي وجاهز للإنتاج **كيفية ضبط FontSettings** في Aspose.Words و**معالجة الخطوط المفقودة** بأناقة. من خلال ربط حدث `FontSubstitutionWarning`، وتحديد دليل خطوط الاحتياط، (وعند الحاجة) تعريف قواعد استبدال صريحة، تحصل على رؤية كاملة وتحكم كامل في الطباعة داخل خطوط أنابيب المستندات الآلية.

ما الخطوة التالية؟ جرّب إضافة مجموعة خطوط مخصصة للخطوط الخاصة بالعلامة التجارية، أو استكشف واجهة برمجة `FontSourceBase` لتحميل الخطوط من قاعدة بيانات أو تخزين سحابي. المبادئ نفسها تنطبق—فقط اربط مصدرًا مختلفًا بـ `FontSettings`.

هل لديك أسئلة حول حالات خاصة، مثل معالجة النصوص من اليمين إلى اليسار أو خطوط الإيموجي؟ اترك تعليقًا أدناه، ونتمنى لك برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}