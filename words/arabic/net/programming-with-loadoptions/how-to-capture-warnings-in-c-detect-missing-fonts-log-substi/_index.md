---
category: general
date: 2026-04-04
description: تعلم كيفية التقاط التحذيرات، واكتشاف الخطوط المفقودة، وكيفية تسجيل أحداث
  الاستبدال باستخدام Aspose.Words LoadOptions في C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: ar
og_description: كيفية التقاط التحذيرات، واكتشاف الخطوط المفقودة، وكيفية تسجيل أحداث
  الاستبدال باستخدام Aspose.Words LoadOptions في C#.
og_title: كيفية التقاط التحذيرات في C# – اكتشاف الخطوط المفقودة وتسجيل الاستبدال
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: كيفية التقاط التحذيرات في C# – اكتشاف الخطوط المفقودة وتسجيل الاستبدال
url: /ar/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية التقاط التحذيرات في C# – اكتشاف الخطوط المفقودة وتسجيل الاستبدال

هل تساءلت يومًا **عن كيفية التقاط التحذيرات** التي تظهر عندما تقوم بتحميل مستند Word يحتوي على خطوط مفقودة؟ لست وحدك. في العديد من المشاريع الواقعية، تُفقد الخطوط أثناء الترحيل، ويمكن أن يتسبب fallback الصامت في كسر تخطيطك. الخبر السار؟ Aspose.Words توفر لك طريقة نظيفة للاستماع إلى تلك التحذيرات، واكتشاف الخطوط المفقودة، وحتى تسجيل كل استبدال حتى تتمكن من إصلاح المصدر لاحقًا.

في هذا الدرس سنستعرض حلًا كاملًا وجاهزًا للتنفيذ يُظهر **كيفية التقاط التحذيرات**، ويُظهر **اكتشاف الخطوط المفقودة**، ويشرح **كيفية تسجيل الاستبدال**. في النهاية، ستحصل على معالج تحذيرات قابل لإعادة الاستخدام، وكائن `LoadOptions` مُكوَّن بالكامل، وعينة من مخرجات وحدة التحكم يمكنك التحقق منها.

> **المتطلب المسبق:** تحتاج إلى Aspose.Words لـ .NET (الإصدار 24.x أو أحدث) مثبتًا عبر NuGet وبيئة تطوير C# أساسية (Visual Studio 2022 أو VS Code تعمل بشكل جيد).

---

## كيفية التقاط التحذيرات عند تحميل المستندات

جوهر الحل هو فئة تُنفّذ `IWarningCallback`. تقوم Aspose.Words باستدعاء هذا الـ callback تلقائيًا لكل تحذير يتم إنشاؤه أثناء تحميل المستند، بما في ذلك تحذيرات استبدال الخطوط.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **لماذا هذه الخطوة؟**  
> من خلال التصفية على `WarningType.FontSubstitution` نتجنب الفوضى الناتجة عن التحذيرات غير المتعلقة (مثل الميزات المهجورة). هذا يجعل السجل مركزًا على المشكلة المحددة التي تهمك — الخطوط المفقودة.

---

## اكتشاف الخطوط المفقودة باستخدام Aspose.Words

عندما يشير مستند إلى خط غير مثبت على الجهاز، تقوم Aspose.Words باستبداله بأقرب خط متاح وتُصدر تحذيرًا. سيُلتقط المعالج الخاص بنا كل حالة، مما يتيح **اكتشاف الخطوط المفقودة** بفعالية.

لرؤية ذلك عمليًا، نحتاج إلى تكوين `LoadOptions` وإرفاق المعالج:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **نصيحة:** إذا كنت تفضل جمع التحذيرات للمعالجة لاحقًا (مثل الكتابة إلى ملف)، استبدل `Console.WriteLine` بكود يضيف الرسالة إلى `List<string>`.

---

## كيفية تسجيل أحداث الاستبدال

التسجيل بسيط بقدر توجيه مخرجات التحذير إلى مخزن دائم. أدناه مثال سريع يكتب كل تحذير استبدال إلى ملف نصي يُسمى `font-warnings.log`.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **لماذا التسجيل إلى ملف؟**  
> السجلات الدائمة تتيح لك تدقيق مشاكل الخطوط عبر تشغيلات متعددة، أتمتة التنبيهات، أو تغذية البيانات إلى فحص خط أنابيب البناء.

---

## مثال كامل يعمل

بجمع كل شيء معًا، إليك تطبيق وحدة تحكم مستقل يمكنك نسخه، لصقه، وتشغيله. يُظهر **كيفية التقاط التحذيرات**، **اكتشاف الخطوط المفقودة**، و**كيفية تسجيل الاستبدال** في خطوة واحدة.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### مخرجات وحدة التحكم المتوقعة

إذا كان `input.docx` يشير إلى خط غير مثبت، ستظهر لك رسالة مشابهة لـ:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

إذا قمت بالتبديل إلى `FileLoggingWarningHandler`، ستظهر نفس السطور داخل `font-warnings.log` مع الطوابع الزمنية.

![how to capture warnings console output](image-placeholder.png)

---

## أسئلة شائعة وحالات حافة

### ماذا لو كنت بحاجة إلى التقاط *جميع* التحذيرات، وليس فقط استبدال الخطوط؟

فقط احذف شرط `if (info.Type == WarningType.FontSubstitution)`. سيستقبل الـ callback كل نوع من التحذيرات (`WarningType.DegradedDocument`، `WarningType.UnexpectedContent`، إلخ). يمكنك بعد ذلك التفرع بناءً على `info.Type` لمعالجة كل حالة بشكل مختلف.

### هل يعمل هذا مع ملفات PDF أم فقط مستندات Word؟

`LoadOptions` و `IWarningCallback` جزء من Aspose.Words، لذا ينطبقان على صيغ Word المتوافقة (`.docx`، `.doc`، `.rtf`، `.html`). بالنسبة لملفات PDF ستستخدم آليات التحذير الخاصة بـ Aspose.PDF.

### كيف يمكنني كتم التحذيرات بدلاً من تسجيلها؟

قم بتعيين `LoadOptions.WarningCallback = null` أو نفّذ الـ callback لكن اترك جسم الطريقة فارغًا. ستستمر المكتبة في إجراء الاستبدال بصمت.

### ماذا عن أمان الخيوط (thread‑safety)؟

يتم استدعاء نسخة الـ callback على نفس الخيط الذي يحمل المستند، لذا لا تحتاج إلى مزامنة إضافية إلا إذا شاركت المعالج عبر عمليات تحميل متوازية. في هذه الحالة، احمِ الموارد المشتركة (مثل ملف السجل) باستخدام قفل أو استخدم مجموعات متزامنة.

---

## الخلاصة

لقد غطينا **كيفية التقاط التحذيرات** من Aspose.Words، وأظهرنا لك **كيفية اكتشاف الخطوط المفقودة**، وشرحنا **كيفية تسجيل أحداث الاستبدال** للتحليل لاحقًا. من خلال ربط تنفيذ بسيط لـ `IWarningCallback` داخل `LoadOptions`، ستحصل على رؤية كاملة لمشكلات الخطوط دون إغراق قاعدة الشيفرة الخاصة بك.

ما الخطوات التالية؟ جرّب توسيع المُسجِّل لإرسال رسائل بريد إلكتروني، دمجه مع Azure Monitor، أو تثبيت الخطوط المفقودة تلقائيًا على خادم البناء. يمكنك أيضًا استكشاف أنواع تحذيرات أخرى — `WarningType.DegradedDocument` يمكنه تنبيهك إلى الميزات التي لم تنجُ من عملية التحويل.

هل لديك المزيد من الأسئلة حول معالجة الخطوط أو Aspose.Words بشكل عام؟ اترك تعليقًا أو افتح قضية جديدة في منتديات Aspose. برمجة سعيدة، ولتظهر مستنداتك دائمًا بالخط المناسب!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}