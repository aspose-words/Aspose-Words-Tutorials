---
category: general
date: 2026-06-24
description: كيفية استخدام IWarningCallback لاكتشاف الخطوط المفقودة في مستندات Aspose.Words.
  تعلّم مثالًا كاملاً قابلاً للتنفيذ وأفضل الممارسات.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: ar
og_description: كيفية استخدام IWarningCallback لاكتشاف الخطوط المفقودة في Aspose.Words.
  اتبع الدليل خطوة بخطوة للحصول على حل كامل وجاهز للإنتاج.
og_title: كيفية استخدام IWarningCallback – اكتشاف الخطوط المفقودة
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: كيفية استخدام IWarningCallback – اكتشاف الخطوط المفقودة باستخدام Aspose.Words
url: /ar/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية استخدام IWarningCallback – اكتشاف الخطوط المفقودة باستخدام Aspose.Words

استخدام **IWarningCallback** أمر أساسي عندما تعمل مع Aspose.Words وتحتاج إلى **اكتشاف الخطوط المفقودة** في ملف DOCX. في هذا الدليل سنستعرض مثالًا كاملاً يمكن نسخه ولصقه يوضح لك بالضبط كيفية استخدام IWarningCallback لالتقاط تحذيرات استبدال الخطوط، ولماذا هذا مهم، وما الذي يجب فعله بعد التقاطها.

إذا فتحت مستندًا ورأيت نصًا مشوّهًا لأن خطًا مخصصًا لم يكن مثبتًا، فأنت تعرف الإحباط. بنهاية هذا الشرح ستحصل على طريقة موثوقة لعرض تلك المشكلات برمجيًا، وتسجيلها، أو حتى تطبيق خط بديل تلقائيًا.

## ما ستتعلمه

- هدف **IWarningCallback** ومتى يجب استخدامه.  
- كيفية تنفيذ جامع تحذيرات مخصص يعزل أحداث **اكتشاف الخطوط المفقودة**.  
- ربط الجامع بـ **LoadOptions** بحيث يتم مراقبة كل عملية تحميل مستند.  
- التحقق من المخرجات ومعالجة الحالات الخاصة (عدة خطوط مفقودة، تحذيرات صامتة، إلخ).  

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا على .NET Framework 4.6+).  
- Aspose.Words for .NET مثبت عبر NuGet (`Install-Package Aspose.Words`).  
- ملف DOCX يشير إلى خط غير موجود على الجهاز (مثال: `DocumentWithMissingFont.docx`).  

لا توجد مكتبات إضافية مطلوبة—كل شيء موجود داخل Aspose.Words.

---

## كيفية استخدام IWarningCallback لاكتشاف الخطوط المفقودة في Aspose.Words

فيما يلي **البرنامج الكامل القابل للتنفيذ**. انسخه إلى مشروع وحدة تحكم جديد، عدل مسار الملف، ثم شغّله. ستظهر مخرجات في وحدة التحكم لكل تحذير خط مفقود.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### النتيجة المتوقعة

إذا كان ملف `DocumentWithMissingFont.docx` يشير إلى خط يُدعى *“MyFancyFont”* غير مثبت، فستظهر لك شيئًا مثل:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

كل سطر يبدأ بـ **[Missing Font]** يتم توليده بواسطة تنفيذنا لـ **IWarningCallback**، مما يثبت أننا نجحنا في **اكتشاف الخطوط المفقودة**.

---

## الخطوة 1: تنفيذ واجهة IWarningCallback

لماذا نحتاج إلى فئة مخصصة؟ تقوم Aspose.Words بإصدار **تحذيرات** لأسباب متعددة—مشكلات تنسيق الملف، ميزات مهجورة، والأهم بالنسبة لنا، استبدال الخطوط. من خلال تنفيذ `IWarningCallback` نحصل على نقطة ربط تستقبل كل تحذير عند حدوثه. تصفية `WarningType.FontSubstitution` تعزل السيناريو المحدد حيث يكون الخط مفقودًا.

**نصيحة احترافية:** إذا أردت التقاط *كل* التحذيرات للتشخيص، ما عليك سوى إزالة شرط `if` وتسجيل كل `info.Type`.

---

## الخطوة 2: ربط الـ Callback بـ LoadOptions

`LoadOptions` هو البوابة التي تخبر Aspose.Words كيف تتعامل مع المستند الوارد. ضبط `WarningCallback` على نسخة من جامعنا يضمن أن الـ callback نشط طوال عملية التحميل. يمكنك إعادة استخدام نفس كائن `LoadOptions` لعدة مستندات، وهو أمر مفيد في خطوط المعالجة الدفعية.

**سؤال شائع:** *ماذا لو حمّلت مستندًا دون تحديد LoadOptions؟*  
الإجابة: ستستمر Aspose.Words في إصدار التحذيرات داخليًا، لكن بدون callback تُهدر صامتًا، وتفقد فرصة **اكتشاف الخطوط المفقودة**.

---

## الخطوة 3: تحميل مستند والتقاط تحذيرات الخطوط المفقودة

المُنشئ `Document` الذي يأخذ مسار ملف و`LoadOptions` يقوم بالعمل الثقيل. أثناء تحليل الملف، أي خط مفقود يُفعّل طريقة `FontWarningCollector.Warning` الخاصة بنا. مخرجات وحدة التحكم تثبت أن الآلية تعمل.

**حالة خاصة:** قد يشير مستند واحد إلى عدة خطوط غير موجودة. يتم استدعاء الـ callback مرة لكل خط مفقود، لذا سترى عدة أسطر—مثالي لإنشاء تقرير شامل.

---

## لماذا نستخدم IWarningCallback بدلاً من الفحص اليدوي للخطوط؟

يمكنك فحص خصائص `Run.Font` يدويًا بعد التحميل، لكن ذلك يتطلب أن ينجح تحميل المستند أولًا—وهو ما قد يفشل إذا كان الخط غير متوفر تمامًا. نظام التحذيرات يعمل **قبل** أي استبدال للخط، مما يمنحك صورة حقيقية لما هو مفقود.

بالإضافة إلى ذلك، الـ callback يُنفّذ **كجزء من خط أنابيب التحميل**، مما يتيح لك الإلغاء المبكر، استبدال الخطوط أثناء التحميل، أو تسجيل تشخيصات مفصلة دون الحاجة إلى جولات إضافية على شجرة المستند.

---

## التعامل مع خطوط مفقودة متعددة بطريقة سلسة

إذا توقعت وجود العديد من الخطوط المفقودة، فكر في تجميعها في مجموعة:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

بعد التحميل، يمكنك التكرار على `MissingFonts`، على سبيل المثال، لكتابة أسماء الخطوط إلى ملف CSV لفريق التصميم.

---

## إضافي: تسجيل التحذيرات إلى ملف

مخرجات وحدة التحكم مناسبة للعرض التجريبي، لكن الكود الإنتاجي عادةً ما يسجل إلى مخزن دائم. استبدل استدعاء `Console.WriteLine` بشيء مثل:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

بهذا ستحصل على سجل تدقيق يمكن مراجعته لاحقًا، مما يلبي متطلبات الامتثال.

---

## الخلاصة

غطّينا **كيفية استخدام IWarningCallback** لـ **اكتشاف الخطوط المفقودة** في Aspose.Words، بدءًا من تنفيذ الـ callback إلى ربطه بـ `LoadOptions` ومعالجة التحذيرات الناتجة. تمنحك هذه الطريقة نظرة فورية على المشكلات المتعلقة بالخطوط، مما يتيح لك التسجيل، الاستبدال، أو تنبيه المستخدمين قبل عرض المستند.

خطوات لاحقة قد تستكشفها:

- **خطوط بديلة:** تعيين خط افتراضي برمجيًا عندما يحدث استبدال.  
- **معالجة دفعية:** حلقة عبر مجلد من المستندات، مع إعادة استخدام نفس `AggregatingFontCollector`.  
- **تغذية راجعة للمستخدم:** عرض تحذيرات الخطوط المفقودة في واجهة مستخدم بدلاً من وحدة التحكم.

جرّبها في مشروعك الخاص—لن تعود تواجه نصًا مشوّهًا غامضًا، بل ستحصل على تشخيصات واضحة وقابلة للتنفيذ. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية تحميل DOCX واكتشاف الخطوط المفقودة – دليل C# كامل](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [كيفية اكتشاف الخطوط في Aspose.Words – معالجة التحذيرات والإعدادات](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [كيفية استخدام LoadOptions في Aspose.Words – دليل كامل](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}