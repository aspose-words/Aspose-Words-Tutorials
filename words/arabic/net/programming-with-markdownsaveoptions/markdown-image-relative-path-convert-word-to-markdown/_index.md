---
category: general
date: 2026-04-28
description: تعلم كيفية تعيين مسار نسبي لصورة markdown عند تحويل Word إلى markdown،
  واستخراج الصور من Word، وإنشاء مجلد موارد للصور المصدرة.
draft: false
keywords:
- markdown image relative path
- convert word to markdown
- extract images from word
- create resources folder
- export images from docx
language: ar
og_description: حدد مسارًا نسبيًا لصورة Markdown أثناء تحويل Word إلى Markdown، استخرج
  الصور من Word، وأنشئ مجلد موارد للصور المصدرة.
og_title: مسار الصورة النسبي في ماركداون – تحويل Word إلى ماركداون
tags:
- Aspose.Words
- C#
- Markdown
- Image Export
title: مسار صورة ماركداون النسبي – تحويل Word إلى ماركداون
url: /ar/net/programming-with-markdownsaveoptions/markdown-image-relative-path-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# مسار صورة markdown النسبي – تحويل Word إلى Markdown

هل احتجت إلى **مسار صورة markdown نسبي** أثناء **تحويل Word إلى markdown**؟ لست وحدك. يواجه معظم المطورين مشكلة عندما تشير ملفات Markdown المُولدة إلى الصور في مجلد مسطح، مما يكسر بنية الروابط النسبية التي تتوقعها في موقع ثابت أو مستودع GitHub.

في هذا الدرس سنستعرض حلاً كاملاً من البداية إلى النهاية ي **يستخرج الصور من Word**، **ينشئ مجلد موارد**، ويعيد كتابة مراجع الصور بحيث تستخدم *مسار صورة markdown نسبي* نظيف. في النهاية ستحصل على ملف `.md` جاهز للنشر ومجلد `Resources` منظم يحتوي على كل صورة تم استخراجها من ملف `.docx` الأصلي.

> **ما ستحصل عليه:** برنامج C# واحد (بدون سكريبتات خارجية)، شرح واضح *لماذا* كل جزء مهم، وبعض النصائح العملية التي يمكنك نسخها ولصقها في مشاريعك الخاصة.

---

## المتطلبات المسبقة

قبل أن نغوص في الكود، تأكد من وجود ما يلي:

- **.NET 6.0** أو أحدث مثبت (يمكنك أيضًا استهداف .NET Framework 4.7+، لكن .NET 6 هو الخيار المثالي للمشاريع الجديدة).
- **Aspose.Words for .NET** (أحدث حزمة NuGet وقت كتابة هذا الدرس، الإصدار 23.12). ثبّتها باستخدام:
  ```bash
  dotnet add package Aspose.Words
  ```
- مستند Word يحتوي فعليًا على صور—سنسميه `WithImages.docx`.
- مجلد تريد أن يعيش فيه ملف الـ markdown الناتج والصور، مثال: `C:\Projects\MarkdownExport`.

لا توجد مكتبات إضافية مطلوبة؛ كل شيء آخر يتم التعامل معه بواسطة Aspose.Words.

---

## الخطوة 1: تحميل مستند Word المصدر (نقطة الانطلاق لتحويل Word إلى markdown)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Adjust the path to point at your own .docx file.
        string sourcePath = @"C:\Projects\MarkdownExport\WithImages.docx";

        // Load the document – this is where Aspose.Words parses the Word file.
        Document doc = new Document(sourcePath);
        
        // The rest of the workflow follows…
    }
}
```

*لماذا هذا مهم:* تحميل المستند يمنحنا الوصول إلى شجرة العقد الداخلية، التي تشمل أجزاء الصور التي نحتاج لاحقًا إلى **تصدير الصور من docx**. إذا فشل التحميل، لن تُنفّذ أي خطوة لاحقة، لذا تأكد من صحة المسار وأذونات الملف.

---

## الخطوة 2: تكوين `MarkdownSaveOptions` مع رد نداء مخصص (قلب إنشاء مجلد الموارد)

يتيح لنا `ResourceSavingCallback` التدخل في كل مرة تريد Aspose.Words كتابة ملف صورة. داخل رد النداء سن **ننشئ مجلد فرعي Resources** ونضبط المرجع بحيث يستخدم الـ markdown مسار صورة *markdown image relative path*.

```csharp
// Inside Main(), after loading the document:
string outputFolder = @"C:\Projects\MarkdownExport";
string resourcesFolder = Path.Combine(outputFolder, "Resources");

// Make sure the folder exists before we start saving anything.
Directory.CreateDirectory(resourcesFolder);

// Set up the Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Hook that runs for every image resource.
    ResourceSavingCallback = new MyMarkdownResourceCallback(resourcesFolder)
};

// Save the document as Markdown.
string markdownPath = Path.Combine(outputFolder, "Doc.md");
doc.Save(markdownPath, mdOptions);
```

لاحظ أننا مررنا `resourcesFolder` إلى مُنشئ رد النداء—هذا يبقي مسار المجلد مرنًا ويتجنب كتابة السلاسل النصية صراحةً في جميع أنحاء الكود.

---

## الخطوة 3: تنفيذ رد النداء الذي **ينشئ مجلد الموارد** ويعيد كتابة المسار

```csharp
/// <summary>
/// Handles image extraction and path rewriting for markdown export.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyMarkdownResourceCallback(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the full file system path where the image will be stored.
        string targetPath = Path.Combine(_resourcesFolder, args.ResourceFileName);
        
        // 2️⃣ Ensure the directory exists (in case Aspose creates sub‑folders).
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath));

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = File.Create(targetPath))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Update the markdown reference to use a relative path.
        // This is the crucial line that gives us the markdown image relative path.
        args.ResourceFileName = Path.Combine("Resources", args.ResourceFileName);
    }
}
```

*لماذا هذا يعمل:* يحتوي `args.Stream` على بايتات الصورة الخام. بنسخه إلى ملف داخل مجلد `Resources` ن **نصدر الصور من docx** بأمان. ثم نستبدل `args.ResourceFileName` بعنوان URL نسبي (`Resources/image.png`). عندما تكتب Aspose.Words الـ markdown لاحقًا، ستُدرج تلك السلسلة بالضبط، مما يمنحنا مسار صورة markdown النسبي المطلوب.

---

## الخطوة 4: التحقق من الـ Markdown المُولد (ما يبدو عليه الإخراج النهائي)

افتح `Doc.md` في أي محرر نصوص. يجب أن ترى شيئًا مشابهًا لـ:

```markdown
# Sample Heading

Here is an inline picture:

![Image 0](Resources/Image_0.png)

And a picture inside a table:

![Image 1](Resources/Image_1.jpg)
```

الجزء المهم هو أن كل مرجع صورة يشير إلى `Resources/...` – هذا هو **مسار صورة markdown النسبي** الذي كنا نبحث عنه.

![مثال على مسار صورة markdown النسبي](example.png "مثال على مسار صورة markdown النسبي")

*نصيحة:* إذا فتحت الـ markdown في عارض يحترم الروابط النسبية (معاينة VS Code، GitHub، أو مولد موقع ثابت)، ستظهر الصور بشكل صحيح دون أي إعداد إضافي.

---

## الخطوة 5: المشكلات الشائعة ونصائح المتخصصين

| المشكلة | لماذا يحدث | كيفية الإصلاح |
|-------|----------------|---------------|
| الصور تنتهي في المجلد الجذر بدلاً من `Resources` | لم يتم ربط رد النداء أو لم يتم استبدال `args.ResourceFileName`. | تأكد من ضبط `ResourceSavingCallback` **قبل** استدعاء `doc.Save`. |
| أسماء الملفات تحتوي على أحرف غير صالحة | أحيانًا يطلق Word أسماء للصور تحتوي على مسافات أو رموز يونيكود. | استخدم `Path.GetInvalidFileNameChars()` لتطهير `args.ResourceFileName` داخل رد النداء. |
| المستندات الكبيرة تستغرق وقتًا طويلاً للمعالجة | كل صورة تُكتب بشكل متزامن. | انتقل إلى I/O غير متزامن (`await args.Stream.CopyToAsync(fileStream)`) إذا كنت على .NET 6+ وتحتاج إلى أداء أعلى. |
| الروابط النسبية تنكسر عندما يُنقل الـ markdown | المسار نسبي لموقع ملف الـ markdown. | حافظ على وجود `Doc.md` ومجلد `Resources` معًا، أو عدل رد النداء لاستخدام بادئة نسبية مختلفة (مثل `../assets`). |

---

## الخطوة 6: توسيع الحل (ماذا لو احتجت إلى مزيد من التحكم؟)

- **تنسيقات إخراج متعددة:** استبدل `MarkdownSaveOptions` بـ `HtmlSaveOptions` أو `PdfSaveOptions` مع الحفاظ على نفس رد النداء—ستستدعي Aspose.Words رد النداء لكل صورة بغض النظر عن التنسيق.
- **تسمية الصور مخصصًا:** إذا أردت إعادة تسمية الصور (مثال: `figure-01.png`)، عدل `args.ResourceFileName` داخل رد النداء قبل كتابة الملف.
- **تضمين الصور كـ Base64:** اضبط `args.ResourceFileName` إلى URI بيانات (`data:image/png;base64,...`) وتجاوز كتابة الملف. هذا مفيد لتصدير markdown كملف واحد.

---

## الخاتمة

أصبح لديك الآن برنامج C# كامل الوظائف **يحول Word إلى markdown**، **يستخرج الصور من word**، **ينشئ مجلد موارد**، ويضمن **مسار صورة markdown نسبي** نظيف لكل صورة. الكود مستقل، يعمل مع أحدث نسخة من Aspose.Words، ويمكن إدراجه في أي مشروع .NET بأقل جهد.

ما الخطوة التالية؟ جرّب إمداد الـ markdown المُولد إلى مولد موقع ثابت مثل Hugo أو Jekyll، أو جرب تعديل رد النداء لتضمين الصور مباشرة كـ Base64. إذا صادفت حالات خاصة—مثل صور SVG أو ملفات ضخمة جدًا—ارجع إلى جدول “المشكلات الشائعة”؛ تعديل بسيط عادةً ما يحل المشكلة.

برمجة سعيدة، ولتظل روابط الـ markdown دائمًا تشير إلى المجلد الصحيح!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}