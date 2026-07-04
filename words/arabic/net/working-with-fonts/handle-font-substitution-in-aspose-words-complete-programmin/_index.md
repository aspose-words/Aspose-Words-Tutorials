---
category: general
date: 2026-06-17
description: تعامل مع استبدال الخطوط في Aspose.Words واكتشف الخطوط المفقودة بسرعة
  من خلال هذا الدليل خطوة بخطوة لمطوري .NET.
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: ar
og_description: تعامل مع استبدال الخطوط في Aspose.Words وتعرّف على كيفية اكتشاف الخطوط
  المفقودة في مستنداتك من خلال أمثلة شفرة واضحة.
og_title: معالجة استبدال الخطوط في Aspose.Words – الدليل الكامل
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: معالجة استبدال الخطوط في Aspose.Words – دليل البرمجة الكامل
url: /ar/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# معالجة استبدال الخطوط في Aspose.Words – دليل برمجة كامل

هل تساءلت يوماً كيف **تتعامل مع استبدال الخطوط** عندما يشير مستند Word إلى خط غير مثبت على الخادم؟ لست وحدك. في العديد من التطبيقات الواقعية—مثل مولّدات الفواتير أو خدمات التقارير الآلية—تسبب الخطوط المفقودة استبدالات صامتة تُفسد التخطيط.  

الخبر السار هو أن Aspose.Words يوفر لك نظام تحذير مدمج يتيح لك **اكتشاف الخطوط المفقودة** والتفاعل معها بالطريقة التي تريدها. في هذا الدرس سنستعرض كيفية تسجيل معالج تحذير، تحميل مستند، واستخراج أحداث استبدال الخطوط التي تحتاج إلى معرفتها. في النهاية ستتمكن من الإجابة على سؤال “**كيف تكتشف الخطوط المفقودة**؟” باستخدام كود نظيف وجاهز للإنتاج.

## ما يغطيه هذا الدرس

* إعداد Aspose.Words لإطلاق تحذيرات لكل استبدال خط.
* التقاط تلك التحذيرات في معالج مخصص لتتمكن من تسجيلها أو استبدالها أو إيقاف العملية.
* استخدام البيانات الملتقطة **لاكتشاف الخطوط المفقودة** قبل حفظ أو عرض المستند.
* نصائح لاستكشاف الحالات الخاصة—مثل اختيار خط بديل صامتًا.
* مثال كامل قابل للتنفيذ يمكنك إدراجه في أي تطبيق .NET Console.

> **المتطلبات المسبقة** – ستحتاج إلى .NET SDK حديث (6.0+ يعمل جيدًا)، رخصة صالحة لـ Aspose.Words for .NET (أو مفتاح تقييم مؤقت)، وعينة DOCX تشير عمدًا إلى خط غير مثبت لديك. لا توجد مكتبات طرف ثالث أخرى مطلوبة.

---

## ## معالجة استبدال الخطوط باستخدام معالج تحذير مخصص

Aspose.Words يطلق كائن `WarningInfo` في كل مرة لا يستطيع العثور على الخط المطلوب. بشكل افتراضي يتم تجاهل تلك التحذيرات، وهذا هو السبب في أنك غالبًا لا تلاحظ الاستبدال. **لمعالجة استبدال الخطوط**، تستبدل معالج التحذير الافتراضي بآخر يقوم بالفعل بشيء ما.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### لماذا يعمل هذا

* `FontSettings.DefaultWarningHandler` خاصية ثابتة عالمية—بمجرد ضبطها، **كل** عملية Aspose.Words في AppDomain الحالي تستخدم التفويض الخاص بك.
* `WarningInfoCollectionHandler` يستقبل كائن `WarningInfo` يحتوي على `WarningType` و`Description` قابلة للقراءة البشرية. الفلترة على `WarningType.FontSubstitution` تضمن لك رؤية الأحداث التي تهمك فقط.
* استدعاء `doc.Save` يجبر المكتبة على حل جميع الخطوط، وهذا هو الوقت الذي تُطلق فيه التحذيرات. إذا كنت تحتاج فقط إلى فحص المستند دون حفظه، يمكنك استدعاء `doc.UpdatePageLayout()` بدلاً من ذلك.

**الناتج المتوقع في وحدة التحكم** (مع افتراض أن الخط المفقود هو “Papyrus”):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

ذلك السطر هو دليل على أن المكتبة **اكتشفت الخطوط المفقودة** واخترت بديلًا.

---

## ## اكتشاف الخطوط المفقودة قبل العرض

أحيانًا تريد إيقاف العملية بالكامل إذا كان خط مطلوب مفقودًا—ربما لأن إرشادات العلامة التجارية تتطلب طباعة دقيقة. يمكن توسيع معالج التحذير لجمع جميع رسائل الخطوط المفقودة في قائمة، ثم تتخذ قرارًا.

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### كيف يجيب هذا على سؤال “كيف تكتشف الخطوط المفقودة”

* قائمة `missingFonts` تعمل كسجل لكل حدث استبدال.
* بعد `UpdatePageLayout`، يمكنك فحص القائمة وتحديد ما إذا كنت ستستمر، تسجل، أو ترفع استثناء.
* هذا النمط يعمل مع أي صيغة إخراج (PDF، HTML، صور) لأن نظام التحذير مستقل عن الصيغة.

---

## ## نصيحة متقدمة: استبدال الخطوط المفقودة ببديل محدد

إذا كان لديك خط مؤسسي يجب استخدامه، يمكنك إخبار Aspose.Words باستبدال أي خط مفقود ببديلك تلقائيًا. هذا مفيد عندما تريد أن يظل المستند *قابلًا للقراءة* دون معالجة يدوية لاحقة.

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

ضع المقتطف أعلاه **قبل** تحميل المستند. الآن أي خط مفقود—بغض النظر عن اسمه الأصلي—سيُستبدل بـ “Calibri” (أو “Arial” إذا لم يتوفر Calibri). ستظل تتلقى التحذير، لكن المستند سيُعرض بالخط الذي تتحكم فيه.

---

## ## الأخطاء الشائعة وكيفية تجنّبها

| المشكلة | السبب | الحل |
|---------|-------|------|
| **تختفي التحذيرات بعد الاستدعاء الأول** | يتم الكتابة فوق `DefaultWarningHandler` الثابت لاحقًا في التطبيق. | اضبط المعالج **مرة واحدة** عند بدء التطبيق، أو احفظ مرجعًا وأعد تعيينه إذا غيرته. |
| **يُبلغ فقط عن أول خط مفقود** | بعض الـ APIs تجمع التحذيرات؛ تحتاج إلى استدعاء `UpdatePageLayout` أو `Save` لتفريغ الطابور. | افرض تحديث التخطيط أو حفظ بصيغة الإخراج التي تنوي توليدها. |
| **يستمر الاستبدال حتى بعد الإلغاء** | معالج التحذير يُنفذ *بعد* حدوث الاستبدال بالفعل. | استخدم المعالج لتسجيل ثم رمي استثناء لإيقاف المعالجة الإضافية. |
| **خطوط مفقودة في حاويات Linux** | Linux غالبًا ما يفتقر إلى فهرس خطوط Windows، مما يؤدي إلى استبدالات كثيرة. | ركب الخطوط المطلوبة داخل الحاوية أو استخدم `FontSettings.SetFontsFolder` لتوجيه دليل خطوط مخصص. |

---

## ## اكتشاف استبدال الخطوط في سيناريو Web API

إذا كنت تُقدم المستندات عبر ASP.NET Core، ربما لا تريد كتابة نصوص إلى وحدة التحكم. بدلاً من ذلك، اجمع التحذيرات وأعدها كجزء من استجابة HTTP.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

الآن الـ API **يكتشف الخطوط المفقودة** ويعيد حمولة JSON واضحة قبل توليد أي PDF. هذا مثال عملي على “كيف تكتشف الخطوط المفقودة” في خدمة جاهزة للإنتاج.

---

## ## اختبار تنفيذك

1. **أنشئ ملف DOCX تجريبي** يشير إلى خط تعرف أنه غير موجود على الجهاز (مثل “Comic Sans MS” على صورة Docker قليلة).  
2. شغّل تطبيق الـ Console أو نقطة النهاية للـ API.  
3. تحقق من أن وحدة التحكم (أو استجابة HTTP) تسرد تحذير الاستبدال.  
4. اختياريًا، افتح الـ PDF الناتج وتفقد خصائص الخط—يجب أن يُظهر Aspose.Words الخط البديل الذي ضبطته.

إذا رأيت التحذير لكن الـ PDF لا يزال يستخدم خطًا غير متوقع، أعد فحص ترتيب `SubstitutionSettings`؛ أول تطابق يُحتَكم إليه.

---

## ## الخلاصة

غطّينا كل ما تحتاجه **للتعامل مع استبدال الخطوط** في Aspose.Words، من تسجيل معالج تحذير إلى اكتشاف الخطوط المفقودة برمجيًا وحتى استبدالها بخط مؤسسي. من خلال الاستفادة من نظام التحذير المدمج تحصل على رؤية كاملة لكل حدث “خط غير موجود”، وهو ما يجيب مباشرة على سؤال “**كيف تكتشف الخطوط المفقودة**؟” الذي يطرحه كل مطور عند أتمتة توليد المستندات.

ما الخطوة التالية؟ جرّب دمج هذه المنطق مع **تحميل الخطوط ديناميكيًا** (`FontSettings.SetFontsFolder`) لدعم الخطوط التي يرفعها المستخدمون في الوقت الفعلي، أو وسّع معالج التحذير لكتابة السجلات إلى خدمة تسجيل مركزية مثل Serilog. كلما زادت أدواتك في معالجة الخطوط، كلما أصبحت خط أنابيب المستندات أكثر موثوقية.

هل تواجه سيناريو استبدال خطوط معقد؟ اترك تعليقًا أدناه، ودعنا نحل المشكلة معًا. برمجة سعيدة!

## ماذا يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}