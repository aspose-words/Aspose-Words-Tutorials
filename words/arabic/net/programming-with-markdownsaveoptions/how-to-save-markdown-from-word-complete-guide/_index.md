---
category: general
date: 2026-01-05
description: تعلم كيفية حفظ ملفات الماركداون وتحويل ملفات docx إلى ماركداون مع استخراج
  الصور من Word. يتضمن خطوة بخطوة إنشاء مجلد الموارد.
draft: false
keywords:
- how to save markdown
- convert docx to markdown
- extract images from word
- how to extract images
- create resources folder
language: ar
og_description: كيفية حفظ ماركداون من ملف DOCX، استخراج الصور، وإنشاء مجلد موارد باستخدام
  Aspose.Words في C#.
og_title: كيفية حفظ ماركداون من وورد – دليل كامل
tags:
- Aspose.Words
- C#
- Markdown
title: كيفية حفظ ماركداون من وورد – دليل شامل
url: /ar/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-word-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية حفظ Markdown من Word – دليل شامل

هل تساءلت يومًا **كيف تحفظ markdown** مباشرةً من مستند Word دون فقدان الصور المدمجة؟ لست وحدك. في العديد من المشاريع نحتاج إلى **تحويل docx إلى markdown**، استخراج الصور، والحفاظ على كل شيء منظمًا في مجلد مخصص. يشرح هذا الدرس حلاً نظيفًا وقابلًا للتكرار باستخدام Aspose.Words for .NET.

سنغطي كل ما تحتاجه: تحميل ملف `.docx`، استخراج الصور، إنشاء **مجلد موارد**، وأخيرًا كتابة ملف markdown. في النهاية ستحصل على مقتطف شفرة جاهز يمكنك وضعه في أي تطبيق C# كونسول أو ويب.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من وجود ما يلي:

* .NET 6.0 أو أحدث (الشفرة تعمل أيضًا مع .NET Framework 4.6+).  
* نسخة مرخصة من **Aspose.Words for .NET** – النسخة التجريبية المجانية تكفي للاختبار.  
* ملف Word (`input.docx`) يحتوي على صورة واحدة على الأقل.  
* إلمام أساسي بـ C# و Visual Studio (أو أي بيئة تطوير تفضلها).

لا توجد حزم NuGet إضافية مطلوبة بخلاف Aspose.Words.

## الخطوة 1 – تحميل المستند المصدر

أول شيء نحتاج إلى القيام به هو قراءة ملف Word داخل كائن `Aspose.Words.Document`. هذا الكائن يمنحنا وصولًا كاملاً إلى محتوى المستند، بما في ذلك الصور التي سنستخرجها لاحقًا.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Adjust the path to point at your .docx file
string sourcePath = Path.Combine("YOUR_DIRECTORY", "input.docx");

// Create the Document instance – this is where the magic starts
Document document = new Document(sourcePath);
```

> **لماذا هذا مهم:** تحميل الملف كـ `Document` يُبسط بنية OOXML المعقدة، مما يتيح لنا العمل مع كائنات عالية المستوى مثل الصور والجداول والفقرات.

## الخطوة 2 – تنفيذ رد نداء حفظ الموارد (Resource‑Saving Callback)

يتيح لك Aspose.Words ربط عملية الحفظ عبر `IResourceSavingCallback`. سنستخدمه للتحكم في مكان حفظ كل صورة مستخرجة. سيقوم رد النداء بإنشاء **مجلد موارد** يحمل اسم المستند المصدر ويكتب كل ملف صورة هناك.

```csharp
// Step 2: Define a callback that decides where each resource (image) is stored
class ResourceSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a folder path like: YOUR_DIRECTORY/Resources/input.docx
        string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "Resources", args.DocumentName);
        Directory.CreateDirectory(resourcesFolder); // Guarantees the folder exists

        // Combine folder path with the original file name (e.g., image001.png)
        string resourcePath = Path.Combine(resourcesFolder, args.ResourceFileName);

        // Override the default name and supply a stream that writes the file
        args.ResourceFileName = resourcePath;
        args.Stream = new FileStream(resourcePath, FileMode.Create);
    }
}
```

> **نصيحة احترافية:** إذا كنت تحتاج إلى بنية مسطحة (جميع الصور في مجلد واحد)، استبدل `Path.Combine(..., args.DocumentName)` باسم مجلد ثابت.

## الخطوة 3 – تكوين خيارات حفظ Markdown

الآن نخبر Aspose.Words باستخدام Markdown كصيغة إخراج ونربط رد النداء الخاص بنا. هذه الخطوة هي التي يحدث فيها فعليًا عملية **تحويل docx إلى markdown**.

```csharp
// Step 3: Prepare the MarkdownSaveOptions and attach the callback
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This tells Aspose.Words to invoke our callback for every resource
    ResourceSavingCallback = new ResourceSavingCallback()
};
```

> **ما الذي يحدث خلف الكواليس؟** المكتبة تمر عبر المستند، تحول تشغيلات الفقرات والجداول والعناصر الأخرى إلى صsyntax Markdown، بينما تُفوض كل عملية كتابة صورة إلى رد النداء الذي قدمناه.

## الخطوة 4 – حفظ المستند كـ Markdown

أخيرًا، نكتب ملف markdown إلى القرص. ستكون الصور قد تم حفظها بالفعل في المجلد الذي أنشأناه في الخطوة السابقة.

```csharp
// Step 4: Save the markdown file alongside the resources folder
string markdownPath = Path.Combine("YOUR_DIRECTORY", "WithImages.md");
document.Save(markdownPath, markdownOptions);

Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
Console.WriteLine("🖼️ Images extracted to the Resources folder.");
```

### النتيجة المتوقعة

* `WithImages.md` – ملف markdown نظيف حيث كل إشارة صورة تبدو هكذا `![Image](Resources/input.docx/image001.png)`.  
* `Resources/input.docx/` – مجلد فرعي يحتوي على جميع الصور المستخرجة (PNG، JPEG، إلخ).

يمكنك فتح ملف markdown في أي عارض (VS Code، GitHub، MkDocs) ورؤية الصور معروضة تمامًا في الموضع الذي كانت فيه في ملف Word الأصلي.

## كيفية استخراج الصور دون تحويل إلى Markdown (مكافأة)

أحيانًا تحتاج فقط إلى الصور، وليس الـ markdown. يمكنك إعادة استخدام نفس منطق رد النداء ولكن استدعاء `document.Save` بصيغة مختلفة، مثل `SaveFormat.Html`. ستُحفظ الصور في نفس المجلد، ويمكنك حذف ملف HTML بعد ذلك.

```csharp
HtmlSaveOptions htmlOptions = new HtmlSaveOptions
{
    ResourceSavingCallback = new ResourceSavingCallback()
};

document.Save(Path.Combine("YOUR_DIRECTORY", "temp.html"), htmlOptions);
```

> **لماذا هذا يعمل:** حفظ HTML أيضًا يُفعل رد نداء الموارد، مما يمنحك حلًا سريعًا “لاستخراج الصور” دون كتابة شفرة إضافية.

## الأخطاء الشائعة وكيفية تجنبها

| المشكلة | السبب | الحل |
|-------|----------------|-----|
| الصور تنتهي بأسماء مكررة | عدة صور تشترك في نفس اسم الملف الأصلي داخل Word. | أضف GUID أو عداد متزايد داخل رد النداء (`args.ResourceFileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";`). |
| روابط Markdown تشير إلى مجلد غير موجود | مسار مجلد `Resources` غير صحيح بالنسبة لملف markdown. | استخدم `Path.GetRelativePath` لحساب مسار نسبي، أو احتفظ بالمجلد بجوار ملف markdown كما هو موضح أعلاه. |
| Aspose.Words يطرح استثناء `FileNotFoundException` | مسار ملف `.docx` المصدر غير صحيح. | تحقق من المسار المطلق باستخدام `Path.GetFullPath` قبل إنشاء كائن `Document`. |
| المستندات الكبيرة تتسبب في أخطاء نفاد الذاكرة | المكتبة تحمل المستند بالكامل في الذاكرة. | قم بقراءة المستند عبر التحميل باستخدام `Document.Load` الذي يقبل `FileStream` بوضع `ReadOnly`. |

## مثال كامل يعمل (نسخ‑لصق)

فيما يلي البرنامج *الكامل* الذي يمكنك تجميعه وتشغيله. استبدل `YOUR_DIRECTORY` بمسار فعلي على جهازك.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace DocxToMarkdown
{
    // Callback that saves each image to a resources folder
    class ResourceSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "Resources", args.DocumentName);
            Directory.CreateDirectory(resourcesFolder);

            string resourcePath = Path.Combine(resourcesFolder, args.ResourceFileName);
            args.ResourceFileName = resourcePath;
            args.Stream = new FileStream(resourcePath, FileMode.Create);
        }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the DOCX
            string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
            Document document = new Document(docPath);

            // 2️⃣ Set up Markdown options with our callback
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ResourceSavingCallback()
            };

            // 3️⃣ Save as Markdown – images are extracted automatically
            string mdPath = Path.Combine("YOUR_DIRECTORY", "WithImages.md");
            document.Save(mdPath, mdOptions);

            Console.WriteLine($"✅ Markdown saved to: {mdPath}");
            Console.WriteLine("🖼️ Images extracted to the Resources folder.");
        }
    }
}
```

شغّل البرنامج (`dotnet run` أو اضغط **F5** في Visual Studio) وسترى رسائل وحدة التحكم التي تؤكد نجاح العملية.

## اختبار المخرجات الخاصة بك

افتح `WithImages.md` في عارض markdown:

```markdown
# Sample Heading

Here is an image extracted from the original Word file:

![Image](Resources/input.docx/image001.png)
```

إذا ظهرت الصورة، فقد نجحت في **كيفية حفظ markdown** مع الحفاظ على المحتوى البصري. إذا لم تظهر، تحقق مرة أخرى من المسار النسبي الذي تم طباعته في وحدة التحكم.

## توسيع الحل

* **تحويل دفعي** – كرّر العملية عبر مجلد يحتوي على ملفات `.docx` متعددة، مع إعادة استخدام نفس منطق رد النداء.  
* **تنسيقات صور مخصصة** – حوّل جميع الصور إلى WebP داخل رد النداء لتقليل حجم الملفات.  
* **معالجة متوازية** – استخدم `Parallel.ForEach` للدفعات الكبيرة، لكن احذر من تعارضات نظام الملفات.

جميع هذه التغييرات لا تزال تجيب على السؤال الأساسي: **كيفية حفظ markdown** من Word مع سير عمل **إنشاء مجلد موارد** منظم.

## الخلاصة

أنت الآن تعرف **كيفية حفظ markdown** من مستند Word، **تحويل docx إلى markdown**، و**استخراج الصور من Word** باستخدام Aspose.Words. المفتاح هو `IResourceSavingCallback` الذي يمنحك التحكم الكامل في مكان حفظ كل صورة، مما يتيح لك **إنشاء مجلد موارد** يتناسب مع بنية مشروعك.

جرّبه، عدّل تسمية المجلد لتناسب معاييرك، وستحصل على خط أنابيب قوي للوثائق، مولدات المواقع الثابتة، أو أي سيناريو يحتاج إلى markdown وصور معًا.

---

*برمجة سعيدة! إذا واجهت أي صعوبات، اترك تعليقًا أدناه أو تواصل معي على GitHub – أنا دائمًا جاهز لجلسة تصحيح سريعة.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}