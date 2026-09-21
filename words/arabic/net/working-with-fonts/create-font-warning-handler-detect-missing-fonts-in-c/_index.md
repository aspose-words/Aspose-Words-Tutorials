---
category: general
date: 2026-02-12
description: إنشاء معالج تحذير الخط لاكتشاف الخطوط المفقودة وتتبعها في Aspose.Words.
  تعلّم كيفية تسجيل التحذيرات بفعالية.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: ar
og_description: إنشاء معالج تحذير الخطوط في C# لاكتشاف الخطوط المفقودة وتعلم كيفية
  تسجيل التحذيرات عندما يقوم Aspose.Words باستبدال الخطوط.
og_title: إنشاء معالج تحذير الخطوط – اكتشاف الخطوط المفقودة
tags:
- Aspose.Words
- C#
- Document Processing
title: إنشاء معالج تحذير الخط – اكتشاف الخطوط المفقودة في C#
url: /ar/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء معالج تحذير الخط – اكتشاف الخطوط المفقودة في C#

هل احتجت يوماً إلى **إنشاء معالج تحذير الخط** لأن مستند Word استبدل صامتاً خطاً لم تتوقعه؟ لست وحدك. عندما تقوم Aspose.Words بتحميل ملف DOCX يشير إلى خط غير موجود على الخادم، فإنها تعود صامتاً إلى خط افتراضي—مما يترك تنسيقك معطوباً بشكل طفيف.  

في هذا الدرس سنوضح لك بالضبط كيفية **اكتشاف الخطوط المفقودة**، **تتبع الخطوط المفقودة**، و**كيفية تسجيل التحذيرات** حتى تتمكن من رصد تلك الاستبدالات قبل أن تؤثر عليك. في النهاية ستحصل على معالج تحذير قابل لإعادة الاستخدام يطبع كل حدث استبدال خط إلى وحدة التحكم (أو أي مسجل تفضله). لا غموض، فقط شفرة واضحة وقابلة للتنفيذ.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (واجهة برمجة التطبيقات هي نفسها لـ .NET Framework 4.6+)
- Aspose.Words لـ .NET مثبت (`dotnet add package Aspose.Words`)
- ملف Word يشير إلى خط غير مثبت على جهازك (مثال: `MissingFont.docx`)

إذا كان لديك هذه المتطلبات بالفعل، رائع—لنبدأ.

## الخطوة 1: إعداد LoadOptions مع رد نداء التحذير  

أول شيء تقوم به عندما تريد **إنشاء معالج تحذير الخط** هو إخبار Aspose.Words بإطلاق رد نداء كلما صادفت مشكلة. `LoadOptions` هو الحاوية لهذا الإعداد.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**لماذا هذا مهم:**  
`LoadOptions` هو المكان الوحيد الذي يمكنك فيه توصيل `IWarningCallback`. بدون ذلك، ستسجل Aspose.Words التحذيرات داخلياً ولن تراها أبداً. من خلال تعيين `FontWarningHandler` نحصل على تحكم كامل فيما يحدث عندما يتم استبدال خط مفقود.

## الخطوة 2: تنفيذ فئة FontWarningHandler  

الآن نكتب فعلياً شفرة **إنشاء معالج تحذير الخط**. الفئة تنفذ `IWarningCallback` وتستقبل كائن `WarningInfo` لكل تحذير تطرحه Aspose.Words.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**شرح:**  
- `info.Type` يخبرنا بفئة التحذير. نهتم بـ `WarningType.FontSubstitution` لأنه يشير إلى خط مفقود.  
- `info.Description` يحتوي على رسالة قابلة للقراءة البشرية مثل *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*  
- بكتابة `Console.WriteLine` نُ **نسجّل التحذيرات** فوراً. في تطبيق واقعي قد تستبدل ذلك بـ `ILogger` أو كاتب ملفات أو خدمة تتبع.

> **نصيحة احترافية:** إذا كنت بحاجة لجمع كل الخطوط المفقودة لتقارير لاحقة، احفظ `info.Description` في `List<string>` بدلاً من طباعتها.

## الخطوة 3: تحميل المستند باستخدام LoadOptions المُكوَّن  

مع وجود رد النداء، سيؤدي تحميل المستند تلقائياً إلى تشغيل معالجنا كلما كان هناك خط مفقود.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**ما ستراه:**  
تشغيل البرنامج يطبع شيئاً مشابهاً لـ:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

ذلك السطر يؤكد أنك نجحت في **اكتشاف الخطوط المفقودة** وأنك الآن **تتبع الخطوط المفقودة** في الوقت الفعلي.

## الخطوة 4: التحقق من عمل المعالج مع سيناريوهات مختلفة  

من السهل افتراض أن المعالج يعمل فقط لملفات DOCX، لكن Aspose.Words يدعم صيغاً عديدة. جرّب تحميل PDF يشير إلى خط مدمج، أو ملف `.doc` أقدم. نفس رد النداء يُفعل لأي صيغة تمر عبر خط أنابيب حل الخطوط.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

إذا كان الـ PDF يشير إلى خط غير مثبت، ستحصل على نفس مخرجات وحدة التحكم. هذا يوضح أن حل **إنشاء معالج تحذير الخط** الخاص بك لا يعتمد على الصيغة.

## الخطوة 5: توسيع المعالج – تسجيل إلى ملف  

مخرجات وحدة التحكم مفيدة للعرض، لكن الشيفرة الإنتاجية عادةً ما تكتب إلى ملف سجل. إليك تعديل سريع.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

الآن في كل مرة يتم فيها استبدال خط، تُضاف الرسالة إلى `font-warnings.log`. هذا يفي بجزء **كيفية تسجيل التحذيرات** من المتطلبات ويمنحك سجل تدقيق دائم.

## الخطوة 6: جمع كل الأجزاء – مثال كامل قابل للتنفيذ  

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑لصقه في تطبيق Console. لا توجد أجزاء مفقودة؛ فقط استبدل مسار الملف بمستندك الخاص.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**النتيجة المتوقعة:**  

- يطبع الطرفية (Console) كل سطر استبدال.  
- `font-warnings.log` الآن يحتوي على سجل مؤرخ لكل حدث خط مفقود.  
- يتم إنشاء ملف `output.pdf` باستخدام الخطوط المستبدلة، مما يضمن نجاح التحويل حتى عندما تكون الخطوط الأصلية غير متوفرة.

## أسئلة شائعة وحالات حافة  

| السؤال | الجواب |
|----------|--------|
| *ماذا لو أردت تجاهل خطوط معينة؟* | داخل `Warning`، تحقق من `info.Description` للحصول على اسم الخط و `return;` مبكراً للخطوط التي تعتبرها مقبولة. |
| *هل سيعمل المعالج مع الخطوط المدمجة؟* | لا—الخطوط المدمجة متاحة دائماً للمستند، لذا لا يحدث تحذير استبدال. |
| *هل يمكنني التقاط أنواع تحذير أخرى (مثل مشاكل دقة الصورة)؟* | بالطبع. احذف شرط `if (info.Type == WarningType.FontSubstitution)` أو أضف كتل `if` إضافية لـ `WarningType.ImageResolution`. |
| *هل المعالج آمن للثريدات؟* | التنفيذ الافتراضي المعروض يكتب إلى ملف دون تزامن. في سيناريوهات متعددة الخيوط، غلف عمليات الكتابة إلى الملف بقفل أو استخدم مسجل متزامن. |

## الخطوات التالية  

الآن بعد أن عرفت **كيفية تسجيل التحذيرات** للخطوط المفقودة، قد ترغب في:

- **اكتشاف الخطوط المفقودة** أثناء عملية استيراد دفعة وإنتاج تقرير ملخص.  
- **تتبع الخطوط المفقودة** عبر مستندات متعددة وإرسال تنبيه بريد إلكتروني عندما يظهر خط معين بشكل متكرر.  
- **دمج مع نظام مراقبة** (مثال: Azure Application Insights) لإظهار اتجاهات استبدال الخطوط بمرور الوقت.  

كل هذه الامتدادات تبني على نفس أساس `IWarningCallback` الذي أنشأناه.

---

*برمجة سعيدة! إذا صادفتك أية شذوذ—ربما مجلد خطوط مخصص أو مشاركة شبكة—اترك تعليقاً أدناه. المجتمع (وأنا) دائماً سعداء بمساعدتك على تحسين استراتيجية تحذير الخطوط الخاصة بك.* 

![مثال على إنشاء معالج تحذير الخط](image-placeholder.png "مثال على إنشاء معالج تحذير الخط")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}