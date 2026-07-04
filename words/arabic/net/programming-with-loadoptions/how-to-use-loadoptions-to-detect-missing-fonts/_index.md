---
category: general
date: 2026-06-08
description: تعلم كيفية استخدام LoadOptions في Aspose.Words لاكتشاف الخطوط المفقودة
  أثناء استيراد المستند. دليل خطوة بخطوة يتضمن الشيفرة، الشروحات، وأفضل الممارسات.
draft: false
keywords:
- how to use loadoptions
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- C# document loading
language: ar
og_description: كيفية استخدام LoadOptions في Aspose.Words واكتشاف الخطوط المفقودة
  أثناء تحميل المستند. دليل كامل مع الشيفرة والنصائح العملية.
og_title: كيفية استخدام LoadOptions لاكتشاف الخطوط المفقودة
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  headline: How to Use LoadOptions to Detect Missing Fonts
  type: TechArticle
- description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  name: How to Use LoadOptions to Detect Missing Fonts
  steps:
  - name: Create a Warning Handler
    text: Aspose.Words uses the `IWarningCallback` interface to notify you about non‑critical
      issues, such as font substitution. Implement the interface and decide what to
      do when a warning arrives.
  - name: Attach the Handler to LoadOptions
    text: Now we create a `LoadOptions` instance and tell it to use our `FontWarningHandler`.
      This is the point where **how to use LoadOptions** really shines.
  - name: Load the Document Using the Configured Options
    text: Finally, we feed the `LoadOptions` into the `Document` constructor. If the
      source file references a font that isn’t installed, Aspose.Words will fire the
      warning and your handler will print a message.
  - name: Multiple Documents in a Loop
    text: Often you’ll process a batch of files. The same `LoadOptions` instance can
      be reused, but remember that the `WarningCallback` persists across loads. If
      you need per‑document isolation, instantiate a fresh `LoadOptions` for each
      iteration.
  - name: Custom Font Substitution Logic
    text: 'Instead of merely logging, you might want to substitute a specific missing
      font with a corporate‑approved alternative. Extend the handler:'
  - name: Silencing Unwanted Warnings
    text: If you only care about font issues and want to suppress everything else,
      filter by `WarningType` as shown. Conversely, to log *all* warnings, drop the
      `if` check and output `info.WarningType` alongside `info.Description`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Font Management
title: كيفية استخدام LoadOptions لاكتشاف الخطوط المفقودة
url: /ar/net/programming-with-loadoptions/how-to-use-loadoptions-to-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية استخدام LoadOptions لاكتشاف الخطوط المفقودة

هل تساءلت يومًا **كيف تستخدم LoadOptions** عند تحميل مستند Word باستخدام Aspose.Words؟ في هذا الدرس سنوضح لك بالضبط **كيفية استخدام LoadOptions** **لاكتشاف الخطوط المفقودة** ومعالجتها بأناقة. سواء كنت تبني خدمة تحويل مستندات أو محرك تقارير، فإن الخطوط المفقودة يمكن أن تتسبب في مفاجآت في التخطيط، لذا يجب اكتشافها مبكرًا.

سنمرّ بكل خطوة — من ربط رد نداء التحذير إلى تفسير النتائج — لتنتهي بمثال C# كامل يمكنك إدراجه في أي مشروع .NET. لا مستندات خارجية، مجرد حل متكامل. في النهاية ستعرف لماذا يوجد نظام التحذير، كيف تُفعّله، وماذا تفعل عندما يُطلق رد النداء.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من وجود ما يلي:

- **Aspose.Words for .NET** (أي إصدار حديث؛ الـ API الذي نستخدمه مستقر منذ 2022).
- بيئة تطوير .NET (Visual Studio، Rider، أو VS Code مع امتداد C#).
- ملف Word تجريبي (`input.docx`) يحتوي على خط **ليس** مثبتًا على الجهاز.

هذا كل شيء — لا حزم NuGet إضافية بخلاف Aspose.Words.

## كيفية استخدام LoadOptions مع Aspose.Words

فئة **LoadOptions** هي البوابة لتخصيص طريقة قراءة المستند. من خلال ربط رد نداء تحذير بها، يمكنك **اكتشاف الخطوط المفقودة** في اللحظة التي يقوم فيها Aspose.Words بتحليل الملف. لنشرح ذلك خطوة بخطوة.

### الخطوة 1: إنشاء معالج تحذير

يستخدم Aspose.Words الواجهة `IWarningCallback` لإبلاغك بالمشكلات غير الحرجة، مثل استبدال الخطوط. نفّذ الواجهة وقرّر ما ستفعله عندما يصل تحذير.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

// Step 1: Define a warning handler that will be notified of font substitutions.
class FontWarningHandler : IWarningCallback
{
    // The Process method is called for every warning Aspose.Words generates.
    public void Process(WarningInfo info)
    {
        // We're only interested in font substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

**لماذا هذا مهم:**  
بدون رد نداء، يقوم Aspose.Words باستبدال الخطوط المفقودة بخط افتراضي (عادةً Arial) بصمت. من خلال التقاط تحذير `FontSubstitution` يمكنك تسجيل المشكلة، تنبيه المستخدم، أو حتى استبدال الخط المفقود بخط احتياطي مخصص.

### الخطوة 2: ربط المعالج بـ LoadOptions

الآن ننشئ كائن `LoadOptions` ونخبره باستخدام `FontWarningHandler` الخاص بنا. هنا يبرز **كيفية استخدام LoadOptions** حقًا.

```csharp
using Aspose.Words.LoadOptions;

// Step 2: Create LoadOptions and attach the warning handler.
var loadOptions = new LoadOptions
{
    // The WarningCallback property accepts any IWarningCallback implementation.
    WarningCallback = new FontWarningHandler()
};
```

**لماذا هذا مهم:**  
`LoadOptions` هي مركز إعدادات متعددة لوقت الاستيراد (الترميز، كلمة المرور، إلخ). من خلال تعيين `WarningCallback`، تُفعّل آلية خفيفة الوزن تعتمد على الأحداث تعمل مع أي مستند تُحمّله بهذه الخيارات.

### الخطوة 3: تحميل المستند باستخدام الخيارات المكوّنة

أخيرًا، نمرّر `LoadOptions` إلى مُنشئ `Document`. إذا كان الملف المصدر يشير إلى خط غير مثبت، سيُطلق Aspose.Words التحذير وسيطبع معالجك رسالة.

```csharp
// Step 3: Load the document using the configured LoadOptions.
// Any missing fonts will trigger the FontWarningHandler.
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**ما ستراه:**  
بافتراض أن `input.docx` يستخدم خطًا يُدعى *“MyCustomFont”* غير موجود على الجهاز، سيكون مخرجات وحدة التحكم كالتالي:

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
```

إذا كانت جميع الخطوط موجودة، يبقى رد النداء صامتًا — لا مخرجات، ولا تأثير على الأداء.

## اكتشاف الخطوط المفقودة باستخدام رد نداء التحذير (الكلمة المفتاحية الثانوية في العمل)

تظهر عبارة **detect missing fonts** بشكل طبيعي في العنوان أعلاه، مما يعزز الكلمة المفتاحية الثانوية. دعنا نستعرض بعض التنويعات التي قد تواجهها في المشاريع الواقعية.

### معالجة مستندات متعددة داخل حلقة

غالبًا ما تعالج دفعة من الملفات. يمكن إعادة استخدام نفس كائن `LoadOptions`، لكن تذكّر أن `WarningCallback` يستمر عبر عمليات التحميل. إذا كنت تحتاج إلى عزل كل مستند على حدة، أنشئ كائن `LoadOptions` جديد لكل تكرار.

```csharp
string[] files = Directory.GetFiles(@"C:\Docs", "*.docx");
foreach (var file in files)
{
    var options = new LoadOptions { WarningCallback = new FontWarningHandler() };
    var document = new Document(file, options);
    // Perform further processing...
}
```

### منطق استبدال الخطوط المخصص

بدلاً من مجرد تسجيل التحذير، قد ترغب في استبدال خط مفقود معين ببديل معتمد من الشركة. وسّع المعالج:

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Extract the missing font name from the description.
            string missingFont = info.Description.Split('\'')[1];
            // Choose a fallback based on your policy.
            string fallback = missingFont.Equals("MyCustomFont") ? "Calibri" : "Arial";
            Console.WriteLine($"Missing '{missingFont}'. Using fallback '{fallback}'.");
            // You could also modify FontSettings here if needed.
        }
    }
}
```

الآن لا تقوم فقط **باكتشاف الخطوط المفقودة**، بل تقرّر أيضًا كيفية استبدالها.

### كتم التحذيرات غير المرغوب فيها

إذا كنت تهتم فقط بمشكلات الخطوط وتريد إخفاء كل شيء آخر، قم بالتصفيّة حسب `WarningType` كما هو موضح. وعلى العكس، لتسجيل *جميع* التحذيرات، احذف شرط `if` واطبع `info.WarningType` جنبًا إلى جنب مع `info.Description`.

## مثال كامل قابل للتنفيذ

بتجميع كل ما سبق، إليك برنامج كامل يمكنك تجميعه وتشغيله. استبدل `"YOUR_DIRECTORY/input.docx"` بالمسار إلى ملف الاختبار الخاص بك.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Ensure the Aspose.Words license is set if you have one.
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
            // You can now work with 'doc' – save, modify, export, etc.
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**المخرجات المتوقعة في وحدة التحكم (عند فقدان خط):**

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

إذا لم يكن هناك أي خطوط مفقودة، سترى ببساطة:

```
Document loaded successfully.
```

## الأخطاء الشائعة ونصائح الخبراء

- **الخطأ:** نسيان تعيين `WarningCallback`. ستستمر الـ API في استبدال الخطوط، لكنك لن تعرف أن ذلك حدث.  
  **نصيحة الخبراء:** دائمًا اربط معالجًا عندما تحتاج إلى دقة الخطوط؛ التكلفة شبه معدومة.

- **الخطأ:**


## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}