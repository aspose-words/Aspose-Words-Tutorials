---
category: general
date: 2026-03-06
description: التقاط تحذيرات الخطوط أثناء تحميل مستند Word في C#. تعلم كيفية اكتشاف
  الخطوط المفقودة، فحص خطوط المستند، والتعامل مع الخطوط المفقودة بكفاءة.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: ar
og_description: التقاط تحذيرات الخطوط أثناء تحميل مستند Word في C#. يوضح هذا الدرس
  كيفية اكتشاف الخطوط المفقودة، والتحقق من خطوط المستند، ومعالجة الخطوط المفقودة.
og_title: التقاط تحذيرات الخط في C# – دليل شامل
tags:
- Aspose.Words
- C#
- Font Management
title: التقاط تحذيرات الخط في C# – دليل كامل
url: /ar/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# التقاط تحذيرات الخطوط في C# – دليل شامل

هل احتجت يومًا إلى **التقاط تحذيرات الخطوط** عند معالجة مستند Word؟ إن التقاط تحذيرات الخطوط أمر أساسي **لاكتشاف الخطوط المفقودة** وضمان أن يكون المخرج النهائي بالضبط كما تريد.  

في هذا البرنامج التعليمي سنستعرض مثالًا عمليًا من البداية إلى النهاية يقوم بتحميل ملف `.docx`، ويراقب عملية التحميل، ويبلغ عن أي استبدالات للخطوط. بحلول النهاية ستعرف كيف **load word document** بأمان، **check document fonts**، و**handle missing fonts** دون أخطاء وقت التشغيل المفاجئة.

## ما ستتعلمه

- كيفية إرفاق جامع تحذيرات إلى Aspose.Words `Document`.
- أنواع التحذيرات التي تشير إلى خط مفقود أو مستبدل.
- طرق لتسجيل أو الاستجابة لتلك التحذيرات في تطبيق من فئة الإنتاج.
- نصائح لتكوين مصادر خطوط مخصصة إذا كنت بحاجة إلى **handle missing fonts** بسلاسة.

> **المتطلب المسبق:** لديك ترخيص صالح لـ Aspose.Words for .NET (أو أنك تستخدم النسخة التجريبية المجانية) وبيئة تطوير .NET (Visual Studio، Rider، أو VS Code). لا توجد مكتبات أخرى مطلوبة.

---

## التقاط تحذيرات الخطوط – خطوة بخطوة

فيما يلي الكود الكامل القابل للتنفيذ. كل قسم مقسم إلى خطوة خاصة به حتى تتمكن من النسخ واللصق، والتجربة، وتوسيع المنطق.

![Capture font warnings diagram](image.png "مخطط يوضح جمع التحذيرات"){: alt="مخطط التقاط تحذيرات الخطوط"}

### الخطوة 1: تحميل مستند Word

أولاً، نحتاج إلى **load word document** الذي قد يحتوي على خطوط غير مثبتة على الجهاز الحالي. يقوم مُنشئ `Document` بالعمل الشاق، لكننا سنبقي الاستدعاء معزولًا حتى تتمكن من استبداله بتدفق أو مصفوفة بايت لاحقًا إذا لزم الأمر.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**لماذا هذا مهم:** تحميل مستند بدون معالج تحذيرات يعني أن أي استبدال للخط يتم تجاهله بصمت. من خلال ضبط `WarningCallback` *قبل* التحميل نضمن رؤية كل تحذير `FontSubstitution` يحدث.

### الخطوة 2: إرفاق جامع تحذيرات

فئة `WarningInfoCollector` هي تنفيذ مدمج لـ `IWarningCallback`. تقوم ببساطة بتخزين كل تحذير في قائمة يمكننا فحصها لاحقًا.

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**نصيحة احترافية:** إذا كنت بحاجة إلى **handle missing fonts** بشكل أكثر حدة (مثل إلغاء التحميل أو الاستبدال بخط احتياطي محدد)، يمكنك استبدال `Console.WriteLine` بمنطق مخصص—إلقاء استثناء، تسجيل إلى ملف، أو حتى إضافة مصدر خط مخصص.

### الخطوة 3: التحقق من المخرجات

شغّل البرنامج من وحدة التحكم. إذا كان ملف `input.docx` يستخدم خطًا غير مثبت، ستظهر لك أسطر مثل:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

إذا لم يظهر أي إخراج، فإن المستند إما استخدم خطوطًا متوفرة بالفعل **أو** وجدت Aspose.Words خطًا مطابقًا في مجموعة الخطوط الاحتياطية المدمجة. على أي حال، لقد نجحت في **check document fonts**.

---

## اكتشاف الخطوط المفقودة بدون ترخيص (نسخة تجريبية مجانية)

حتى إذا كنت تستخدم النسخة التجريبية لمدة 30 يومًا، فإن آلية التحذير تعمل بنفس الطريقة. الاختلاف الوحيد هو أن النسخة التجريبية تضيف علامة مائية إلى المخرج المُولد، وهذا لا يؤثر على جمع التحذيرات. لذا يمكنك بأمان **detect missing fonts** قبل اتخاذ قرار شراء ترخيص كامل.

---

## معالجة الخطوط المفقودة – خيارات متقدمة

أحيانًا تريد توفير ملفات خطوطك الخاصة (مثل خطوط العلامة التجارية للشركة) حتى لا يحدث الاستبدال. تتيح لك Aspose.Words تسجيل مجلدات خطوط مخصصة:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

ضع الكود أعلاه **قبل** تحميل المستند إذا كنت تريد أن يأخذ المحمل هذه الخطوط في الاعتبار أثناء مرحلة التحليل الأولية. هذه هي الطريقة الأكثر موثوقية لـ **handle missing fonts** دون الاعتماد على خطوط النظام الافتراضية.

---

## الأخطاء الشائعة وكيفية تجنبها

| الخطأ | لماذا يحدث | الحل |
|---------|----------------|-----|
| **تم إرفاق جامع التحذيرات بعد التحميل** | المستند تم تحليله بالفعل، لذا لا تُسجل أي تحذيرات. | إرفاق `WarningCallback` **قبل** استدعاء `new Document(path)`. |
| **ظهور تحذيرات عامة فقط** | قمت بفلترة النوع الخطأ من `WarningType`. | استخدم `WarningType.FontSubstitution` للتركيز على مشاكل الخطوط. |
| **لا يوجد إخراج رغم وجود خطوط مفقودة** | وجدت Aspose.Words خطًا احتياطيًا مدمجًا (مثل Arial). | عطّل الخطوط الاحتياطية المدمجة عبر `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` |
| **تدهور الأداء عند فحص مستندات كبيرة** | جمع كل التحذيرات قد يكون مكلفًا. | قصر الجمع على `FontSubstitution` فقط، أو معالجة التحذيرات على دفعات. |

---

## مثال كامل يعمل (جاهز للنسخ واللصق)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**الإخراج المتوقع في وحدة التحكم** (بافتراض وجود خطين مفقودين):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

إذا بقيت وحدة التحكم صامتة باستثناء رسالة “Document loaded successfully”، فقد قمت بـ **check document fonts** ولم تجد أي خطوط مفقودة.

---

## الخلاصة

لقد أظهرنا لك كيفية **capture font warnings** في C# باستخدام Aspose.Words، وهي طريقة موثوقة لـ **detect missing fonts**، **load word document** بأمان، **check document fonts**، و**handle missing fonts** عبر مصادر خطوط مخصصة.  
مع هذا النمط يمكنك دمج التحقق من الخطوط في أي خط أنابيب أتمتة—سواء كنت تُنشئ ملفات PDF، أو تُحوّل إلى HTML، أو ببساطة تُؤرّخ ملفات Word.

### ما التالي؟

- استكشف API **FontSettings.SubstitutionSettings** لتحديد قواعد احتياطية خاصة بك.
- اجمع بين جمع التحذيرات وإطار تسجيل (Serilog، NLog) للمراقبة في بيئة الإنتاج.
- استخدم نفس النهج لالتقاط أنواع تحذيرات أخرى، مثل دقة الصورة أو الميزات غير المدعومة.

هل لديك المزيد من الأسئلة حول معالجة الخطوط أو Aspose.Words بشكل عام؟ اترك تعليقًا أو شارك في منتديات مجتمع Aspose. برمجة سعيدة، ولتظهر مستنداتك دائمًا بالخطوط التي تتوقعها!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}