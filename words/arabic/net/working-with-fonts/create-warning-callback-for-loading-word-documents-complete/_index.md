---
category: general
date: 2026-03-25
description: إنشاء رد نداء تحذيري لتحميل مستند Word واكتشاف الخطوط المفقودة. تعلّم
  كيفية تكوين إعدادات الخط في Aspose.Words لـ .NET.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: ar
og_description: إنشاء رد نداء تحذيري لتحميل مستند Word مع الكشف عن الخطوط المفقودة.
  يوضح هذا الدليل كيفية تكوين إعدادات الخطوط في Aspose.Words.
og_title: إنشاء رد نداء تحذيري – تحميل مستند Word واكتشاف الخطوط المفقودة
tags:
- Aspose.Words
- C#
- Font handling
title: إنشاء رد نداء تحذيري لتحميل مستندات Word – دليل كامل
url: /ar/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء رد تحذير – تحميل مستند Word واكتشاف الخطوط المفقودة

هل احتجت يوماً إلى **إنشاء رد تحذير** عند تحميل مستند Word وتساءلت لماذا تختفي بعض الخطوط؟ لست وحدك. في العديد من التطبيقات المؤسسية، تتسبب الخطوط المفقودة في فوضى تخطيطية، وبدون رد تحذير مناسب قد لا تلاحظ المشكلة أبداً.  

الخبر السار؟ باستخدام Aspose.Words for .NET يمكنك **تحميل مستند Word**، **اكتشاف الخطوط المفقودة**، و**تكوين إعدادات الخط** كل ذلك في بضع أسطر من الشيفرة النظيفة. في هذا الدرس سنستعرض مثالاً كاملاً قابلاً للتنفيذ، نشرح لماذا كل جزء مهم، ونظهر لك كيف تتحقق من أن رد التحذير يقوم بعمله.

> **ما ستحصل عليه**  
> * برنامج C# كامل يحمل ملف DOCX، يبلغ عن أي استبدال للخطوط، ويسمح لك بتخصيص مسارات البحث عن الخطوط.  
> * فهم لكلاسي `FontSettings`، `LoadOptions`، و`IWarningCallback`.  
> * نصائح للتعامل مع الحالات الخاصة مثل الخطوط المدمجة أو مجلدات الخطوط على مستوى النظام.

---

## المتطلبات المسبقة

- .NET 6+ (أو .NET Framework 4.7.2+) مع مترجم C#.  
- حزمة NuGet الخاصة بـ Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- ملف Word تجريبي (`input.docx`) يستخدم على الأقل خطاً غير مثبت على الجهاز (مثال: *Calibri Light* على حاوية Windows بسيطة).  
- إلمام أساسي بتطبيقات C# console.

لا توجد مكتبات إضافية مطلوبة؛ كل شيء موجود داخل Aspose.Words.

---

## الخطوة 1: إنشاء رد تحذير لاكتشاف الخطوط المفقودة

القطعة **الرئيسية** في هذه الأحجية هي فئة تنفّذ `IWarningCallback`. ستستدعي Aspose.Words هذا الرد كلما واجهت حالة تستدعي تحذيراً – استبدال الخط هو الأكثر شيوعاً.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**لماذا هذا مهم** – بدون رد تحذير سيتعين عليك تصفح السجلات بعد وقوع الحدث. من خلال معالجة التحذيرات في الوقت الفعلي يمكنك اتخاذ قرار إما بإلغاء التحميل، استبدال الخط المفقود بخط بديل، أو ببساطة تسجيل المشكلة للمراجعة لاحقاً.

---

## الخطوة 2: تكوين FontSettings لمعالجة الخطوط المخصصة

قبل أن نقوم بتحميل المستند فعلياً، قد نرغب في إخبار Aspose.Words أين يبحث عن الخطوط غير الموجودة على النظام. هنا يأتي دور `FontSettings`.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**لماذا هذا مهم** – من خلال توجيه Aspose.Words إلى مجلد يحتوي على الخطوط المفقودة، غالباً ما تتجنب الاستبدال تماماً. عندما لا يكون ذلك ممكنًا، فإن اختيار افتراضي معقول (مثل *Arial*) يحافظ على قابلية قراءة المستند.

---

## الخطوة 3: تحميل مستند Word مع رد التحذير المُكوّن

الآن نجمع كل شيء معاً: ننشئ `LoadOptions`، نربط `FontSettings` و`FontWarningHandler`، وأخيراً نحمل المستند.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**لماذا هذا مهم** – `LoadOptions` هو المكان الوحيد الذي تُحدد فيه *كيفية* قراءة المستند. من خلال توفير كل من تكوين الخط ورد التحذير نضمن أن أي خط مفقود يتم البحث عنه في الأماكن الصحيحة **ويُبلغ عنه** فوراً.

---

## الخطوة 4: التحقق من النتيجة – ماذا يجب أن ترى؟

شغّل البرنامج من سطر الأوامر. إذا كان `input.docx` يستخدم خطاً غير مثبت ولا يوجد أيضاً في `C:\SharedFonts`، سترى شيئاً مثل:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

إذا كانت جميع الخطوط متوفرة، لن يظهر سطر التحذير أبداً. هذه الحلقة السريعة من التغذية الراجعة لا تقدر بثمن أثناء خطوط معالجة المستندات الآلية حيث يمكن أن تتسبب استبدالات الخط الصامتة في كسر إرشادات العلامة التجارية.

---

## الخطوة 5: الأخطاء الشائعة ونصائح أفضل الممارسات

| المشكلة | كيفية تجنّبها |
|---------|-----------------|
| **نسيت إضافة مرجع `Aspose.Words.Fonts`** | تأكد من وجود `using Aspose.Words.Fonts;` في أعلى الملف؛ وإلا سيشتكي المترجم من أنواع مفقودة. |
| **مسار مجلد الخطوط غير صحيح** | تحقق من المسار واضبط `recursive: true` إذا كان لديك مجلدات فرعية. استخدم `Path.GetFullPath` للتصحيح. |
| **وجود ردود تحذير متعددة** | Aspose.Words يطبق فقط آخر `WarningCallback` تم تعيينه. احتفظ بمعالج واحد يوزع المنطق إذا احتجت إلى تعقيد أكبر. |
| **التشغيل على خادم بدون واجهة مستخدم** | كتابة إلى الـ Console مقبولة، لكن لتطبيقات الويب قد تفضّل تسجيل إلى ملف أو نظام مراقبة بدلاً من `Console.WriteLine`. |
| **المستندات الكبيرة تؤثر على الأداء** | أعد استخدام نسخة واحدة من `FontSettings` عبر عمليات تحميل متعددة؛ إن إنشاؤها مراراً قد يكون مكلفاً. |

**نصيحة احترافية:** إذا كنت تحتاج إلى *جمع* التحذيرات للتحليل لاحقاً، احفظها في `List<string>` داخل المعالج بدلاً من طباعتها مباشرة.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

يمكنك بعد ذلك فحص `handler.Messages` بعد تحميل المستند.

---

## الخطوة 6: توسيع الحل – ماذا لو أردت تضمين خط بديل؟

أحياناً تريد أن يتم *تضمين* الخط المفقود في ملف PDF الناتج حتى يرى المشاهدون النهائيون الشكل الدقيق. بعد تحميل المستند، يمكنك فرض التضمين:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

هذا المقتطف يوضح كيف يمكن توسيع نهج **تكوين إعدادات الخط** ليشمل ما بعد التحميل.

---

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في مشروع Console App جديد. يتضمن جميع القطع التي نوقشت أعلاه.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**الناتج المتوقع** (عند وجود خط مفقود):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

إذا لم يحدث استبدال، ستظهر فقط رسائل النجاح.

---

## الخلاصة

لقد **أنشأنا رد تحذير** يكتشف بموثوقية **الخطوط المفقودة** أثناء **تحميل مستند Word** باستخدام Aspose.Words، وأظهرنا كيف **نُكوّن إعدادات الخط** للتحكم في أماكن بحث المكتبة عن الخطوط وأي بديل يُستخدم. بربط `FontSettings` و`LoadOptions` معاً، تحصل على رؤية كاملة لمشكلات الخط – لا مزيد من الأخطاء الصامتة في التخطيط.

ما الخطوة التالية؟ جرّب استبدال `FontWarningHandler` بمدقق يكتب إلى قاعدة بيانات، أو جرب **قواعد استبدال الخطوط** لتعيين خطوط مفقودة إلى بدائل معتمدة للعلامة التجارية. يمكنك أيضاً استكشاف **تحميل الخطوط ديناميكياً** من التخزين السحابي إذا كان تطبيقك يعمل في بيئة حاوية.

هل لديك أسئلة حول حالة خاصة – مثل التعامل مع ميزات OpenType أو ملفات DOCX المشفرة؟ اترك تعليقاً أدناه، وتمنياتنا لك ببرمجة سعيدة!  

---

![Create warning callback diagram](https://example.com/images/create-warning-callback.png "Create warning callback diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}