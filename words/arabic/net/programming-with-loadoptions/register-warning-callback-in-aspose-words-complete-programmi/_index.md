---
category: general
date: 2026-06-27
description: سجّل رد الاتصال للتحذير في Aspose.Words لالتقاط استبدالات الخطوط ومشكلات
  التحميل. تعلّم خطوة بخطوة كيفية استخدام LoadOptions مع Aspose.Words.
draft: false
keywords:
- register warning callback aspose.words
- aspose.words warning callback
- loadoptions font substitution warning
- document loading warning handling
- aspose.words loadoptions example
language: ar
og_description: سجّل رد الاتصال للتحذير في Aspose.Words لمراقبة استبدالات الخطوط وغيرها
  من تحذيرات التحميل. اتبع هذا الدرس الكامل للحصول على تنفيذ قوي.
og_title: تسجيل رد النداء للتحذير في Aspose.Words – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  headline: Register Warning Callback in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  name: Register Warning Callback in Aspose.Words – Complete Programming Guide
  steps:
  - name: 4.1 Logging to a File Instead of Console
    text: 'In production you rarely want console spam. Swap `Console.WriteLine` for
      a logger (e.g., `Serilog`, `NLog`) or write to a text file:'
  - name: 4.2 Providing a Custom Font Directory
    text: 'If your environment uses corporate fonts, tell Aspose.Words where to look
      before it falls back to substitution:'
  - name: 4.3 Handling Non‑Font Warnings
    text: 'You can broaden the scope to capture any loading warning:'
  - name: 5.1 Verify with a Document That Has Missing Fonts
    text: Create a small DOCX that references a font not installed on your machine
      (e.g., “Comic Sans MS” on a Linux server). Run the loader; you should see a
      substitution message.
  - name: 5.2 Benchmark Overhead
    text: The callback adds negligible overhead—roughly a few microseconds per warning.
      If you’re loading thousands of documents, you might batch log entries or disable
      the callback for non‑critical runs.
  - name: 5.3 Edge Cases
    text: '- **Multiple Substitutions for the Same Font:** Aspose.Words may fire the
      callback multiple times if the same missing font appears on different pages.
      Deduplicate in your logger if needed. - **Encrypted Documents:** If the DOCX
      is password‑protected, you must also set `loadOptions.Password`. The cal'
  type: HowTo
tags:
- aspose-words
- warning-callback
- csharp
- document-processing
title: تسجيل رد نداء التحذير في Aspose.Words – دليل البرمجة الكامل
url: /ar/net/programming-with-loadoptions/register-warning-callback-in-aspose-words-complete-programmi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تسجيل رد النداء للتحذير في Aspose.Words – دليل برمجة كامل

هل تساءلت يومًا كيف **register warning callback in Aspose.Words** حتى تتمكن من رؤية الخطوط التي تم استبدالها بالضبط عند تحميل المستند؟ لست وحدك. يواجه العديد من المطورين مشكلة عندما يؤدي استبدال الخط الصامت إلى خراب تخطيط ملف PDF أو Word تم إنشاؤه.  

في هذا الدرس سنستعرض حلًا عمليًا لا يقوم فقط بتسجيل رد النداء للتحذير في Aspose.Words بل يشرح أيضًا *لماذا* قد ترغب في ذلك، وكيف يعمل رد النداء تحت الغطاء، وما هي الحالات الحدية التي قد تواجهها. في النهاية ستتمكن من تسجيل كل استبدال للخط، والتقاط تحذيرات التحميل الأخرى، وجعل خط أنابيب معالجة المستندات الخاص بك شفافًا.

## ما ستتعلمه

- إعداد **LoadOptions** للتحكم في سلوك تحميل المستند.  
- تسجيل **warning callback** الذي يُستدعى عند استبدال الخطوط وأنواع التحذير الأخرى.  
- تحميل ملف DOCX باستخدام الخيارات المكوَّنة وتفسير ناتج رد النداء.  
- المشكلات الشائعة (الخطوط المفقودة، مجلدات الخطوط المخصصة، واعتبارات الأداء).  

**المتطلبات المسبقة:** Visual Studio 2022 (أو أي بيئة تطوير C#)، .NET 6+ runtime، ورخصة Aspose.Words نشطة (الإصدار التجريبي المجاني يعمل للتجربة). لا توجد حزم NuGet إضافية بخلاف `Aspose.Words` مطلوبة.

---

![مخطط يوضح تدفق تسجيل رد النداء للتحذير في Aspose.Words ومعالجة تحذيرات استبدال الخطوط](register-warning-callback-aspose-words.png "register warning callback aspose.words diagram")

## الخطوة 1: إنشاء LoadOptions – نقطة الدخول لمعالجة التحذيرات  

قبل أن يتم استدعاء رد النداء، تحتاج إلى كائن من **LoadOptions**. فكر فيه كلوحة التحكم التي تسلمها إلى Aspose.Words عندما تقول "حمّل هذا الملف، ولكن رجاءً أخبرني إذا كان هناك أي شيء غير صحيح."

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

// Initialize LoadOptions – this object will carry our warning callback.
var loadOptions = new LoadOptions();
```

> **لماذا هذا مهم:** `LoadOptions` يتيح لك تعديل كل شيء من كلمات مرور التشفير إلى مجلدات الخطوط. من خلال إرفاق رد النداء للتحذير بهذا الكائن، تحول عملية صامتة إلى عملية يمكن مراقبتها.

## الخطوة 2: تسجيل رد النداء للتحذير – التقاط استبدالات الخطوط  

الآن يأتي العنصر الرئيسي: **warning callback**. سنقوم بتسجيل طريقة مجهولة (lambda) التي تستدعيها Aspose.Words لكل تحذير تحميل. داخل رد النداء نقوم بتصفية `WarningType.FontSubstitution` ونطبع رسالة ودية.

```csharp
// Register a warning callback to be notified of font substitutions.
loadOptions.WarningCallback = (sender, args) =>
{
    // The callback runs for each loading warning; we care about font substitution warnings.
    if (args.WarningType == WarningType.FontSubstitution)
    {
        // Cast to the more specific warning info type.
        var fontWarning = (FontSubstitutionWarningInfo)args;
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
    // Optional: handle other warning types here (e.g., MissingResource, UnsupportedFeature).
};
```

> **نصيحة احترافية:** إذا كنت ترغب أيضًا في تسجيل الصور المفقودة أو الميزات غير المدعومة، أضف فروع `if` إضافية تتحقق من `args.WarningType`. هذا يجعل تنفيذ **register warning callback in Aspose.Words** الخاص بك مركزًا واحدًا لجميع تشخيصات التحميل.

## الخطوة 3: تحميل المستند باستخدام LoadOptions المكوَّنة  

مع ربط رد النداء، الخطوة التالية هي ببساطة تحميل المستند. مرّر كائن `loadOptions` إلى مُنشئ `Document`. في كل مرة تواجه فيها Aspose.Words خطًا لا يمكنها العثور عليه، سيُستدعى رد النداء الخاص بك ويكتب إلى وحدة التحكم.

```csharp
// Load the DOCX while the warning callback is active.
var doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

شغّل البرنامج، وسترى مخرجات مشابهة لـ:

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
```

هذا هو جوهر **register warning callback aspose.words**—نمط من ثلاث خطوات يمكنك إعادة استخدامه في أي مشروع.

## الخطوة 4: توسيع رد النداء لسيناريوهات العالم الحقيقي  

### 4.1 التسجيل إلى ملف بدلاً من وحدة التحكم  

في بيئة الإنتاج نادراً ما تريد رسائل مزعجة في وحدة التحكم. استبدل `Console.WriteLine` بمسجل (مثل `Serilog`، `NLog`) أو اكتب إلى ملف نصي:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    if (args.WarningType == WarningType.FontSubstitution)
    {
        var info = (FontSubstitutionWarningInfo)args;
        File.AppendAllText("font-warnings.log",
            $"[WARN] {DateTime.Now}: Font '{info.FontName}' → '{info.SubstitutedFontName}'{Environment.NewLine}");
    }
};
```

### 4.2 توفير دليل خطوط مخصص  

إذا كان بيئتك تستخدم خطوطًا مؤسسية، أخبر Aspose.Words أين تبحث قبل أن يلجأ إلى الاستبدال:

```csharp
loadOptions.FontSettings = new FontSettings();
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
```

الآن قد يتم استدعاء رد النداء *أقل* تكرارًا، لأن المحرك يجد الخطوط الصحيحة.

### 4.3 معالجة التحذيرات غير المتعلقة بالخط  

يمكنك توسيع النطاق لالتقاط أي تحذير تحميل:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    switch (args.WarningType)
    {
        case WarningType.FontSubstitution:
            var f = (FontSubstitutionWarningInfo)args;
            Log($"Font '{f.FontName}' → '{f.SubstitutedFontName}'");
            break;
        case WarningType.MissingResource:
            var m = (MissingResourceWarningInfo)args;
            Log($"Missing resource: {m.ResourceType} - {m.ResourceName}");
            break;
        // Add more cases as needed.
    }
};
```

## الخطوة 5: اختبار تنفيذك – ما المتوقع  

### 5.1 التحقق باستخدام مستند يحتوي على خطوط مفقودة  

أنشئ ملف DOCX صغيرًا يشير إلى خط غير مثبت على جهازك (مثلاً “Comic Sans MS” على خادم Linux). شغّل المحمل؛ يجب أن ترى رسالة استبدال.  

### 5.2 قياس عبء الأداء  

يضيف رد النداء عبءً ضئيلًا—حوالي بضعة ميكروثوانٍ لكل تحذير. إذا كنت تقوم بتحميل آلاف المستندات، قد تقوم بتجميع سجلات الدخول أو تعطيل رد النداء للعمليات غير الحرجة.

### 5.3 الحالات الحدية  

- **Multiple Substitutions for the Same Font:** قد يستدعي Aspose.Words رد النداء عدة مرات إذا ظهر الخط المفقود نفسه في صفحات مختلفة. قم بإزالة التكرارات في مسجلك إذا لزم الأمر.  
- **Encrypted Documents:** إذا كان ملف DOCX محميًا بكلمة مرور، يجب أيضًا تعيين `loadOptions.Password`. سيظل رد النداء يُستدعى بعد فك التشفير.  
- **Async Loading:** الـ API متزامن، لكن يمكنك تغليف استدعاء التحميل داخل `Task.Run` للمعالجة في الخلفية؛ يبقى رد النداء آمنًا عبر الخيوط.  

## المشكلات الشائعة وكيفية تجنبها  

| المشكلة | لماذا يحدث | الحل |
|---------|------------|------|
| **لا يوجد أي إخراج** | لم يتم تعيين رد النداء *أو* تم استبدال `WarningCallback` لاحقًا. | تأكد من تعيين رد النداء **مرة واحدة** قبل التحميل، ولا تعيد تعيين `loadOptions` بعد التعيين. |
| **استثناء تحويل غير صحيح** | محاولة تحويل تحذير ليس من نوع `FontSubstitutionWarningInfo`. | تحقق دائمًا من `args.WarningType` قبل التحويل. |
| **تباطؤ الأداء** | تسجيل بشكل متزامن إلى هدف I/O بطيء. | استخدم أطر تسجيل غير متزامنة أو خزن الكتابات في ذاكرة مؤقتة. |
| **الخطوط المخصصة مفقودة** | لم يتم إضافة مجلد الخطوط إلى `FontSettings`. | أضف `SetFontsFolder` كما هو موضح في الخطوة 4.2. |

## مثال كامل يعمل – انسخ‑وشغّل  

فيما يلي برنامج مستقل يمكنك نسخه إلى مشروع تطبيق Console جديد. يوضح التدفق الكامل من البداية إلى النهاية.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

class Program
{
    static void Main()
    {
        // 1️⃣ Create LoadOptions.
        var loadOptions = new LoadOptions();

        // 2️⃣ Register the warning callback (register warning callback Aspose.Words).
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                var fontInfo = (FontSubstitutionWarningInfo)args;
                Console.WriteLine(
                    $"Font '{fontInfo.FontName}' was substituted with '{fontInfo.SubstitutedFontName}'.");
            }
            // Optional: handle other warnings here.
        };

        // Optional: tell Aspose where to find corporate fonts.
        // loadOptions.FontSettings = new FontSettings();
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", true);

        // 3️⃣ Load the document using the configured options.
        string filePath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(filePath, loadOptions);

        // At this point the document is loaded, and any font substitutions have been printed.
        Console.WriteLine("Document loaded successfully.");
    }
}
```

**المخرجات المتوقعة في وحدة التحكم** (مع افتراض وجود خطوط مفقودة):

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
Document loaded successfully.
```

شغّل البرنامج، وسترى بالضبط ما هي الخطوط التي استبدلتها Aspose.Words، مما يمنحك رؤية كاملة لعملية التحميل.

---

## الخلاصة  

لقد غطينا للتو **how to register warning callback in Aspose.Words**، ولماذا تُعد ممارسةً مثالية لأي سير عمل لمعالجة المستندات، وكيفية توسيع النمط للتسجيل، الخطوط المخصصة، ومعالجة التحذيرات بشكل أوسع. بثلاث أسطر من الشيفرة فقط، تحول عملية تحميل الصندوق الأسود إلى خطوة قابلة للتدقيق والتصحيح—بدون تغييرات تخطيطية غامضة بعد الآن.

ما التالي؟ جرّب دمج هذا الرد مع **Aspose.Words SaveOptions** لتسجيل التحذيرات أثناء كل من التحميل *والحفظ*، أو اربط رد النداء بواجهة ويب API تعالج التحميلات في الوقت الفعلي. يمكنك أيضًا استكشاف الكلمات المفتاحية الثانوية الأخرى التي قدمناها—مثل *loadoptions font substitution warning*—لضبط الأداء أو دمجه مع لوحة مراقبة.

هل لديك أسئلة أو سيناريو صعب؟ اترك تعليقًا، ولنحل المشكلة معًا. برمجة سعيدة، ولتظهر ملفات PDF الخاصة بك دائمًا بالخطوط الصحيحة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Aspose Words Java رد النداء المخصص للتوفير](/words/german/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java رد النداء المخصص للتوفير](/words/french/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java رد النداء المخصص للتوفير](/words/spanish/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}