---
category: general
date: 2026-03-28
description: كيفية التقاط التحذيرات عند تحميل ملف DOCX باستخدام Aspose.Words والحصول
  على رسائل تحذير للخطوط المفقودة. تعلّم كيفية التعامل مع الخطوط المفقودة بفعالية.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: ar
og_description: كيفية التقاط التحذيرات عند تحميل ملف DOCX باستخدام Aspose.Words، الحصول
  على رسائل التحذير، ومعالجة الخطوط المفقودة بأمثلة عملية على الشيفرة.
og_title: كيفية التقاط التحذيرات في Aspose.Words – دليل C# الكامل
tags:
- Aspose.Words
- C#
- Document Processing
title: كيفية التقاط التحذيرات في Aspose.Words – دليل C# الكامل
url: /ar/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية التقاط التحذيرات في Aspose.Words – دليل C# كامل

هل تساءلت يومًا **كيف يمكنك التقاط التحذيرات** التي تظهر عندما تقوم بتحميل مستند Word باستخدام Aspose.Words؟ ربما تلاحظ تغييرات غريبة في الخط وتحتاج إلى معرفة السبب بالضبط. باختصار، يمكنك ربط نظام التحذير الخاص بالمكتبة، **الحصول على رسائل التحذير**، وحتى **معالجة الخطوط المفقودة** قبل أن تفسد تخطيطك.

في هذا الدرس سنستعرض سيناريو واقعي: تحميل ملف DOCX، جمع كل التحذيرات التي ينتجها المحرك، وطباعة تفاصيل أي استبدال للخط يحدث. في النهاية ستحصل على عينة كود جاهزة للتنفيذ، وتفهم “السبب” وراء كل خطوة، وتعرف كيف تُوسّع النهج لمشاريعك الخاصة.

## ما ستتعلمه

- كيفية تكوين `LoadOptions` بحيث تُلتقط التحذيرات تلقائيًا.  
- الطريقة الدقيقة **للحصول على رسائل التحذير** من `WarningInfoCollection`.  
- كيفية التعرف على **الخطوط المفقودة** والتفاعل معها عبر علم `WarningType.FontSubstitution`.  
- نصائح لاستكشاف الحالات الخاصة، مثل المستندات التي تحتوي على خطوط مدمجة أو مجلدات خطوط مخصصة.  

لا توجد مراجع خارجية مطلوبة – كل ما تحتاجه موجود هنا.

---

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا على .NET Framework 4.7+).  
- حزمة NuGet لـ Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- ملف DOCX تجريبي (`input.docx`) إما يفتقر إلى بعض الخطوط أو يستخدم خطوطًا غير مثبتة على جهازك.  

هذا كل شيء. إذا كنت مرتاحًا بالفعل مع C# وVisual Studio، يمكنك نسخ‑لصق الكود وتشغيله فورًا.

---

## الخطوة 1: إعداد خيارات التحميل وكائن رد الاتصال للتحذير

الأمر الأول الذي تقوم به Aspose.Words عند استدعاء `new Document(path, loadOptions)` هو تحليل الملف. أثناء التحليل قد تواجه خطوطًا مفقودة أو ميزات غير مدعومة أو تعليمات قديمة. لالتقاط هذه الأحداث تحتاج إلى كائن **رد اتصال التحذير**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**لماذا هذا مهم:** بدون رد اتصال، تقوم Aspose.Words بتسجيل التحذيرات صامتًا إلى وحدة التحكم (أو تتجاهلها)، مما يجعلك غير مدرك لاستبدالات الخط التي قد تؤثر على التخطيط. من خلال توفير `WarningInfoCollection` مخصص، تحصل على رؤية كاملة.

> **نصيحة احترافية:** إذا كنت تهتم فقط بالتحذيرات المتعلقة بالخطوط، يمكنك تصفيتها لاحقًا – لكن جمع *جميع* التحذيرات يمنحك شبكة أمان للمستقبل.

---

## الخطوة 2: تحميل المستند باستخدام الخيارات المكوّنة

الآن بعد أن أصبح رد الاتصال جاهزًا، قم بتحميل الملف. سيستدعي مُنشئ `Document` رد الاتصال تلقائيًا لأي مشكلة يكتشفها.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**ما الذي يحدث خلف الكواليس؟** تقوم Aspose.Words بتحليل Open XML، حل الأنماط، ومحاولة ربط كل إشارة خط بخط مثبت على النظام. إذا لم يُعثر على مطابقة، تُنشئ إدخال `WarningInfo` من النوع `FontSubstitution`.

---

## الخطوة 3: استرجاع وفحص التحذيرات المجمعة

بعد إكمال التحميل، يحتوي `warningCollector` الآن على كل التحذيرات التي حدثت. لنستخرجها ونركز على رسائل استبدال الخط.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**نموذج الإخراج** (قد يظهر في وحدة التحكم شيء مشابه):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

إذا أردت *جميع* التحذيرات، ما عليك سوى إزالة شرط `if` أو تسجيل `warning.Type` لكل إدخال.

---

## الخطوة 4: معالجة الخطوط المفقودة – أكثر من مجرد تسجيل

التقاط التحذيرات مفيد، لكن غالبًا ما تحتاج إلى **معالجة الخطوط المفقودة** برمجيًا. إليك استراتيجيتان شائعتان:

### 4.1 استبدال الخطوط المفقودة بخط احتياطي محدد

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

الآن أي خط مفقود سيُستبدل بـ *Calibri* بدلاً من الاحتياطي الافتراضي للمكتبة.

### 4.2 تضمين خط بديل بشكل ديناميكي

إذا كان لديك ملف خط مخصص (مثلاً `MyFallback.ttf`) يمكنك تسجيله في وقت التشغيل:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

هذا النهج مفيد عندما توزع خطًا مؤسسيًا محددًا مع تطبيقك.

> **حالة خاصة:** المستندات التي تدمج الخط المطلوب بالفعل ستتجاهل قواعد الاستبدال النظامية. في هذه الحالة، ستكون مجموعة التحذيرات فارغة لهذا الخط، وهذا بالضبط ما تريده.

---

## الخطوة 5: مثال كامل جاهز للتنفيذ (نسخ‑لصق)

فيما يلي برنامج مستقل يوضح كل شيء من البداية إلى النهاية. ما عليك سوى استبدال `YOUR_DIRECTORY/input.docx` بالمسار إلى ملف الاختبار الخاص بك.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**ما المتوقع**

- تقوم وحدة التحكم بطباعة كل تحذير استبدال خط، مسبوقًا برمز تحذير لزيادة الوضوح.  
- يستخدم ملف الـ DOCX الناتج (`output.docx`) *Calibri* في كل موضع تم اكتشاف خط مفقود فيه.  
- لا توجد استثناءات غير معالجة – نظام التحذير يتعامل بأناقة مع أي خط غير معروف.

---

## أسئلة شائعة وإجابات

**س: هل سيعمل هذا مع ملفات PDF المولدة من Word؟**  
ج: نعم. تعتبر Aspose.Words ملفات PDF تنسيقًا آخر للإخراج. يحدث التقاط التحذيرات أثناء مرحلة *التحميل*، لذا فهو مستقل عن عملية التصدير النهائية.

**س: ماذا لو أردت التقاط التحذيرات لجميع عمليات المستند (حفظ، تحويل، إلخ)؟**  
ج: يمكنك إعادة استخدام نفس `WarningInfoCollection` عن طريق تعيينه إلى `Document.WarningCallback` بعد إنشاء المستند. كل عملية لاحقة ستضيف إدخالات جديدة إلى نفس المجموعة.

**س: هل يؤثر رد اتصال التحذير على الأداء؟**  
ج: تأثيره ضئيل. المجموعة فقط تخزن كائنات؛ ما لم تكن تعالج آلاف التحذيرات في حلقة ضيقة، لن تلاحظ أي بطء.

**س: كيف يمكنني كتم التحذيرات التي لا أهتم بها؟**  
ج: نفّذ فئة مخصصة ترث من `IWarningCallback` وقم بالتصفيه داخل طريقة `Warning`. `WarningInfoCollection` المدمجة فقط تخزن ولا تقوم بالتصفيه.

---

## نصائح احترافية ومخاطر

- **نصيحة احترافية:** دائمًا افحص `Warning.Description` – فهو يحتوي على اسم الخط الدقيق الذي كان مفقودًا. هذا يمكن أن يساعدك في اتخاذ قرار بنشر الخط مع تطبيقك.  
- **احذر الخطوط المدمجة:** إذا كان ملف DOCX المصدر يدمج الخط المطلوب بالفعل، لن تصدر Aspose.Words تحذير استبدال، حتى وإن لم يكن الخط مثبتًا محليًا.  
- **سلامة الخيوط:** `WarningInfoCollection` غير آمنة للاستخدام المتعدد الخيوط. إذا قمت بتحميل مستندات متعددة بشكل متزامن، امنح كل خيط مجموعته الخاصة.  
- **فحص الإصدار:** واجهة برمجة التحذيرات مستقرة منذ Aspose.Words 20.8. تأكد من أنك تستخدم نسخة حديثة لتجنب فقدان أنواع التحذيرات الجديدة.

---

## الخلاصة

لقد غطينا **كيفية التقاط التحذيرات** من Aspose.Words، وأظهرنا **كيفية الحصول على رسائل التحذير**، وقدمنا طرقًا عملية **للتعامل مع الخطوط المفقودة** عبر خطوط احتياطية أو مجلدات خطوط مخصصة. المثال الكامل جاهز للإدراج في أي مشروع .NET، والمفاهيم قابلة للتوسيع إلى خطوط أنابيب أتمتة أكبر.

بعد ذلك، قد ترغب في استكشاف:

- استخدام `Document.WarningCallback` لالتقاط التحذيرات أثناء عمليات **الحفظ**.  
- تسجيل التحذيرات في ملف أو نظام تتبع للرقابة في بيئات الإنتاج.  
- توسيع رد الاتصال لاستبدال الخطوط المفقودة تلقائيًا بأنماط ذات علامة تجارية.

لا تتردد في التجربة—غيّر الخط الاحتياطي، أضف مستندات أكثر إلى الدفعة، أو دمج جامع التحذيرات في خط أنابيب CI يُعلم عن الانحرافات المتعلقة بالخطوط. برمجة سعيدة، ولتظهر مستنداتك دائمًا كما تتوقع!  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}