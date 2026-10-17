---
category: general
date: 2026-02-28
description: تعلم كيفية التعامل مع تحذيرات الخطوط واكتشاف الخطوط المفقودة في Aspose.Words
  باستخدام C#. دليل كامل خطوة بخطوة مع الشيفرة الكاملة.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: ar
og_description: تعامل مع تحذيرات الخطوط في Aspose.Words واكتشف الخطوط المفقودة باستخدام
  مثال C# جاهز للتنفيذ. اتبع الخطوات وشاهد النتيجة.
og_title: معالجة تحذيرات الخطوط في Aspose.Words – دليل شامل
tags:
- Aspose.Words
- C#
- Document Loading
title: معالجة تحذيرات الخطوط في Aspose.Words – اكتشاف الخطوط المفقودة
url: /ar/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# معالجة تحذيرات الخطوط في Aspose.Words – اكتشاف الخطوط المفقودة

هل احتجت يومًا إلى **معالجة تحذيرات الخطوط** عند تحميل مستند Word وتساءلت لماذا يبدو بعض النص غريبًا؟ لست وحدك. الخطوط المفقودة تُطلق تحذيرات استبدال يمكنها أن تُفسد التخطيط البصري بصمت، وإذا لم **تكتشف الخطوط المفقودة** فلن تعرف أبدًا ما الخطأ.

في هذا البرنامج التعليمي سنُظهر لك طريقة عملية لـ **معالجة تحذيرات الخطوط** باستخدام `IWarningCallback` في Aspose.Words. بنهاية الدليل ستتمكن من رصد كل حدث استبدال للخط، تسجيله، وحتى اتخاذ قرار بإلغاء التحميل إذا لزم الأمر. لا مستندات خارجية، مجرد مثال واحد جاهز للنسخ واللصق.

## ما ستتعلمه

- إعداد معالج تحذير مخصص يتفاعل فقط مع تنبيهات استبدال الخط.  
- ربط المعالج بـ `LoadOptions` بحيث يمر كل تحميل مستند من خلاله.  
- التحقق من المخرجات في وحدة التحكم وفهم ما يعنيه كل تحذير.  

**المتطلبات المسبقة**

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.6+).  
- Aspose.Words for .NET مثبت عبر NuGet (`Install-Package Aspose.Words`).  
- ملف Word يشير إلى خط غير مثبت على جهازك (مثلاً خط شركة مخصص).  

إذا كنت تفتقد أيًا من هذه المتطلبات، احصل عليها الآن—وإلا، لنبدأ.

## كيفية معالجة تحذيرات الخطوط في Aspose.Words

فيما يلي البرنامج الكامل القابل للتنفيذ. يتضمن كل شيء من عبارات `using` إلى طريقة `Main`، بحيث يمكنك وضعه في تطبيق console والضغط على **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Expected console output** (assuming the document uses a font you don’t have installed):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

إذا كان المستند لا يحتوي على **خطوط مفقودة**، لن يظهر سطر التحذير أبداً—وبالتالي تكون قد **اكتشفت الخطوط المفقودة** فقط عندما يكون ذلك ضرورياً.

### لماذا يعمل هذا

Aspose.Words يُصدر كائن `WarningInfo` لكل مشكلة غير حرجة يواجهها أثناء تحليل الملف. من خلال تنفيذ `IWarningCallback` تحصل على نقطة ربط داخل هذه العملية. علم `WarningType.FontSubstitution` يُخبرك بالضبط متى اضطر المكتبة لاستبدال الخط المطلوب بخط بديل. هذه هي الطريقة الأكثر موثوقية لـ **معالجة تحذيرات الخطوط** لأنها تعمل *أثناء* التحميل، قبل أن تتعامل مع نموذج كائن المستند.

## اكتشاف الخطوط المفقودة دون كسر تطبيقك

أحيانًا قد ترغب في اعتبار الخط المفقود خطأً فادحًا—ربما توجيهات علامتك التجارية تحظر أي استبدال. يمكنك تعديل المعالج لرمي استثناء بدلاً من مجرد تسجيل:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

الآن سيُلتقط كتلة `try…catch` حول `new Document(...)` المشكلة، مما يتيح لك اتخاذ قرار إما بالإلغاء، أو باللجوء إلى بديل، أو بطلب إدخال من المستخدم.

## إضافي: تصور التحذيرات في تطبيق واجهة مستخدم

إذا كنت تبني تطبيق WinForms أو WPF، استبدل `Console.WriteLine` بنداء صديق للواجهة:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

بهذه الطريقة يرى المستخدم النهائي التحذير فورًا، وتستمر في **معالجة تحذيرات الخطوط** بشكل متسق عبر جميع المنصات.

## الأخطاء الشائعة & نصائح احترافية

- **Pitfall:** نسيان تعيين `WarningCallback`. السلوك الافتراضي هو تجاهل تحذيرات الخطوط، لذا لن تراها أبدًا.  
  **Pro tip:** دائمًا أنشئ كائن `LoadOptions` حتى لو كنت تحتاج فقط إلى معالج التحذير. الأمر غير مكلف وواضح.  

- **Pitfall:** استخدام فاصل المسار الخطأ على أنظمة غير Windows.  
  **Pro tip:** استخدم `Path.Combine` أو سلسلة نصية خام (`@"C:\Docs\MissingFont.docx"` تعمل على Windows؛ على Linux استخدم `"/home/user/docs/MissingFont.docx"`).  

- **Pitfall:** الافتراض أن التحذير سيظهر للخطوط المدمجة.  
  **Pro tip:** الخطوط المدمجة تُعتبر موجودة، لذا لا يظهر تحذير استبدال. اختبر بخطوط *مفقودة فعلاً* لتشاهد المعالج يعمل.  

- **Pitfall:** تسجيل كل أنواع التحذيرات بشكل مفرط.  
  **Pro tip:** صَفِّ حسب `WarningType.FontSubstitution` كما هو موضح—هذا يحافظ على نظافة وحدة التحكم ويركز على سيناريو **اكتشاف الخطوط المفقودة**.  

## ملخص المثال الكامل القابل للتنفيذ

إليك البرنامج بالكامل مرة أخرى، هذه المرة بدون تعليقات لمن يفضّل العرض النظيف:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

انسخ، الصق، شغّل—ستقوم وحدة التحكم الآن بـ **معالجة تحذيرات الخطوط** و**اكتشاف الخطوط المفقودة** تلقائيًا.

## الخطوات التالية

- **Log to a file:** استبدل `Console.WriteLine` بمسجل (مثلاً NLog) لتتبع مستوى الإنتاج.  
- **Batch processing:** كرّر العملية على مجلد من المستندات، واجمع كل أحداث استبدال الخط في تقرير CSV.  
- **Automatic font installation:** اربط معالج التحذير بتحميل الخطوط المفقودة من مستودع الشركة قبل متابعة التحميل.  

كل من هذه الإضافات يبني على الفكرة الأساسية لـ **معالجة تحذيرات الخطوط** بطريقة نظيفة وقابلة لإعادة الاستخدام.

---

*برمجة سعيدة! إذا صادفت أي مشاكل أثناء محاولة **اكتشاف الخطوط المفقودة**، اترك تعليقًا أدناه. سأساعدك بسرور في حلها.*  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}