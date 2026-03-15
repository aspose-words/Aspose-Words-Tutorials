---
category: general
date: 2026-03-14
description: تعامل مع الخطوط المفقودة بسرعة باستخدام Aspose.Words. تعلم كيفية التقاط
  تحذيرات استبدال الخطوط، وتكوين LoadOptions، وتجنب مشاكل العرض.
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: ar
og_description: معالجة الخطوط المفقودة في Aspose.Words باستخدام جامع التحذيرات. يوضح
  هذا الدرس خطوة بخطوة كيفية اكتشاف وتسجيل استبدالات الخطوط.
og_title: معالجة الخطوط المفقودة في Aspose.Words – دليل C# الكامل
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: معالجة الخطوط المفقودة في Aspose.Words – دليل C# الكامل
url: /ar/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

.

Let's start.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# التعامل مع الخطوط المفقودة في Aspose.Words – دليل C# كامل

هل احتجت يوماً إلى **معالجة الخطوط المفقودة** عند تحميل مستند Word وتساءلت لماذا يبدو مخرجات PDF أو الصورة غير صحيحة؟ لست وحدك. ملفات الخطوط المفقودة هي مصدر مشاكل صامت يمكنه تحويل تقرير مصمم بعناية إلى فوضى مشوشة.  

الخبر السار؟ Aspose.Words يوفّر لك طريقة نظيفة لالتقاط أحداث استبدال الخطوط، تسجيلها، وحتى استبدالها بخط احتياطي إذا رغبت. في هذا الدرس سنستعرض مثالاً كاملاً جاهزاً للتنفيذ يوضح بالضبط كيفية إعداد جامع التحذيرات، ربطه بـ `LoadOptions`، وتحميل مستند قد يحتوي على خطوط مفقودة.

بنهاية هذا الدليل ستتمكن من:

* اكتشاف كل استبدال خط يحدث أثناء تحميل المستند.  
* طباعة رسالة صديقة على وحدة التحكم (أو توجيهها إلى مسجل) لكل خط مفقود.  
* توسيع الحل لاستبدال الخطوط إذا لزم الأمر.  

**المتطلبات المسبقة** – ستحتاج إلى:

* .NET 6.0 أو أحدث (الكود يعمل مع .NET Core و .NET Framework أيضاً).  
* حزمة NuGet الخاصة بـ Aspose.Words for .NET (الإصدار الحالي 23.11).  
* ملف Word يحتوي عمداً على إشارة إلى خط غير مثبت لديك – سنسميه `doc-with-missing-font.docx`.  

إذا كنت مرتاحاً بالفعل مع C# ولديك مشروع مُعد، يمكنك القفز مباشرة إلى الكود. وإلا، استمر في القراءة؛ سنغطي خطوات الإعداد الصغيرة أولاً.

---

## لماذا تُعد معالجة الخطوط المفقودة مهمة؟

عند تحميل Aspose.Words لمستند، يحاول مطابقة كل حرف مع خط مثبت على الجهاز. إذا لم يتم العثور على الخط الدقيق، يقوم باستبداله بصمت بأقرب مطابقة. هذا الاستبدال يمكن أن يغيّر ارتفاع السطر، التباعد بين الحروف، وحتى يسبب اختفاء بعض الأحرف. عبر التقاط حدث `WarningType.FontSubstitution` ستحصل على رؤية شفافة لـ **ما** تم استبداله و**لماذا**، وهو أمر أساسي لـ:

* الحفاظ على اتساق العلامة التجارية (يجب أن يظهر الخط الخاص بشركتك تماماً كما هو مصمم).  
* تصحيح مشكلات تحويل PDF – غالباً ما يكون السبب خط مفقود.  
* بناء خطوط أنابيب مستندات آلية حيث تحتاج إلى وضع علامة على الملفات التي تحتاج إلى مراجعة يدوية.

الآن بعد أن وضّحنا “السبب”، لننتقل إلى **كيفية** التنفيذ.

---

## الخطوة 1 – إعداد جامع التحذيرات

أول شيء نحتاجه هو كائن يمكنه الاستماع إلى تحذيرات Aspose.Words. `DocumentWarnings` يطبق `IWarningCallback`، مما يتيح لنا التفاعل كلما أطلقت المكتبة تحذيراً.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**ما الذي يحدث؟**  
* `DocumentWarnings` هو غلاف خفيف حول واجهة الـ callback.  
* الدالة اللامبدا تتحقق من `e.WarningType` لذا نتجاهل التحذيرات غير المتعلقة (مثل الميزات المهجورة).  
* `e.WarningInfo` يحتوي على اسم الخط المفقود، والذي نطبعه على وحدة التحكم.  

*نصيحة احترافية*: استبدل `Console.WriteLine` بمسجل منظم (Serilog، NLog) في بيئة الإنتاج—بهذا ستحصل على طوابع زمنية ومستويات سجل تلقائياً.

---

## الخطوة 2 – ربط الجامع بـ LoadOptions

`LoadOptions` هو الحارس لكل مستند تفتحه باستخدام Aspose.Words. عبر تعيين كائن `fontWarnings` الخاص بنا إلى خاصية `WarningCallback`، نضمن أن الجامع نشط أثناء عملية التحميل.

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**لماذا نستخدم LoadOptions؟**  
إلى جانب التحذيرات، يتيح لك `LoadOptions` التحكم في معالجة كلمات المرور، الترميز، وحتى تحميل الموارد المخصص. هنا نركز على جانب التحذير، لكن النمط نفسه يعمل مع callbacks أخرى.

---

## الخطوة 3 – تحميل المستند باستخدام الخيارات المكوّنة

الآن نُحمل المستند في الذاكرة. إذا كان أي خط مفقود، سيُطلق جامعنا تحذيراً وستظهر لك سطر على وحدة التحكم لكل استبدال.

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

إذا شغّلت هذا المقتطف مع مستند يشير، على سبيل المثال، إلى *Calibri Light* بينما جهاز الاختبار لديك يحتوي فقط على *Calibri*، ستحصل على مخرجات مشابهة لـ:

```
Font 'Calibri Light' was substituted.
```

هذا هو حلقة الكشف بالكامل—بسيطة، لكنها قوية.

---

## الخطوة 4 – (اختياري) استبدال الخطوط المفقودة بخط بديل معروف

أحياناً لا تريد فقط تسجيل المشكلة؛ بل تريد فرض خط احتياطي بحيث يبدو الناتج المتصوّر متسقاً. Aspose.Words يتيح لك توفير كائن `FontSettings` مخصص يربط الخطوط المفقودة ببديل.

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**شرح**  
* العلامة النجمية `"*"` تخبر Aspose.Words أن تتعامل مع *أي* خط مفقود بنفس الطريقة.  
* يمكنك أيضاً ربط خطوط محددة بشكل فردي إذا احتجت تحكمًا دقيقًا.  
* بعد تعيين `document.FontSettings`، أي عملية تصيير لاحقة (PDF، صورة، HTML) ستحترم الاستبدال.

---

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في تطبيق Console. يتضمن جميع عبارات `using` المطلوبة، معالجة الأخطاء، وتعليقات لتوضيح الفكرة.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**المخرجات المتوقعة** (عند اكتشاف خط مفقود):

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

إذا كان المستند المصدر يحتوي بالفعل على جميع الخطوط المطلوبة، لن يظهر سطر التحذير أبداً—لا شيء يدعو للقلق.

---

## أسئلة شائعة وحالات خاصة

| السؤال | الجواب |
|----------|--------|
| **ماذا لو أردت فقط تسجيل التحذيرات دون استبدال الخطوط؟** | تخطّ خطوة إعداد `FontSettings` تماماً؛ جامع التحذيرات وحده يكفي. |
| **هل يمكن توجيه التحذيرات إلى ملف؟** | نعم—استبدل `Console.WriteLine` بـ `File.AppendAllText("font-warnings.log", …)`. |
| **هل يعمل هذا مع DOC و DOCX و ODT؟** | بالتأكيد. `LoadOptions` يُطبق على جميع الصيغ التي تدعمها Aspose.Words. |
| **ماذا عن الخطوط المدمجة داخل المستند؟** | الخطوط المدمجة تتجاوز آلية الاستبدال؛ تُستخدم كما هي. |
| **هل هناك تأثير على الأداء؟** | العبء ضئيل—فقط callback لكل خط مفقود. للدفعات الكبيرة، فكر في تجميع التحذيرات بدلاً من الكتابة لكل حدث. |

---

## الخلاصة

لقد بيّنّا **كيفية معالجة الخطوط المفقودة** في Aspose.Words عبر ربط جامع `DocumentWarnings` بـ `LoadOptions`، مع إمكانية استبدال الخط بخط احتياطي، وحفظ النتيجة. يوفّر لك هذا النمط رؤية كاملة لأحداث استبدال الخطوط، ما يساعدك على الحفاظ على الدقة البصرية عبر تحويلات PDF أو الصور أو HTML.

خطوات مستقبلية قد ترغب في استكشافها:

* دمج جامع التحذيرات مع إطار تسجيل مركزي.  
* بناء لوحة تحكم UI تُظهر المستندات التي تحتوي على خطوط مفقودة للمعالجة الجماعية.  
* الجمع بين هذا النهج و Aspose.PDF للتحقق من أن ملفات PDF المُولدة تستخدم الخط الاحتياطي فعلياً.  

لا تتردد في التجربة—بدّل `"Arial"` بـ `"Tahoma"` أو حمّل مجموعة مستندات مختلفة. الفكرة الأساسية تبقى نفسها: التقط التحذير، تصرف بناءً عليه، واحرص على أن تبدو مستنداتك كما هو مخطط لها.

برمجة سعيدة! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}