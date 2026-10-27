---
category: general
date: 2026-03-30
description: كيفية حفظ ملفات ماركداون في C# مع استخراج الصور من الماركداون وحفظ المستند
  كملف ماركداون باستخدام Aspose.Words.
draft: false
keywords:
- how to save markdown
- extract images from markdown
- save document as markdown
- markdown resource handling
- C# markdown export
language: ar
og_description: كيفية حفظ ملف ماركداون بسرعة. تعلم استخراج الصور من ماركداون وحفظ
  المستند كملف ماركداون مع مثال كامل للكود.
og_title: كيفية حفظ Markdown – دليل C# الكامل
tags:
- C#
- Markdown
- Aspose.Words
title: كيفية حفظ ملفات ماركداون – دليل كامل مع استخراج الصور
url: /ar/net/programming-with-markdownsaveoptions/how-to-save-markdown-full-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية حفظ Markdown – دليل C# الكامل

هل تساءلت يومًا **how to save markdown** مع الحفاظ على جميع الصور المضمنة سليمة؟ لست الوحيد. يواجه العديد من المطورين مشكلة عندما تقوم مكتبتهم بوضع الصور في مجلد عشوائي أو، والأسوأ، تتركها تمامًا. الخبر السار؟ ببضع أسطر من C# و Aspose.Words يمكنك تصدير مستند إلى markdown، استخراج كل صورة، والتحكم بدقة في مكان حفظ كل ملف.

في هذا الدرس سنستعرض سيناريو واقعي: أخذ كائن `Document`، ضبط `MarkdownSaveOptions`، وإخبار أداة الحفظ أين تضع كل صورة. في النهاية ستتمكن من **save document as markdown**، **extract images from markdown**، والحصول على هيكل مجلد منظم جاهز للنشر. لا مراجع غامضة—فقط مثال كامل وقابل للتنفيذ يمكنك نسخه‑ولصقه.

## ما ستحتاجه

- **.NET 6+** (أي مجموعة تطوير حديثة تعمل)
- **Aspose.Words for .NET** (حزمة NuGet `Aspose.Words`)
- فهم أساسي لبنية C# (سنبقيه بسيطًا)
- كائن `Document` موجود مسبقًا (سننشئ واحدًا لأغراض العرض)

إذا كان لديك هذه المتطلبات، هيا نبدأ.

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

أولاً، أنشئ تطبيقًا جديدًا من نوع console (أو دمجه في الحل الحالي). ثم أضف حزمة Aspose.Words:

```bash
dotnet add package Aspose.Words
```

الآن استورد المساحات الاسمية المطلوبة:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

> **نصيحة احترافية:** احتفظ بعبارات `using` في أعلى الملف؛ فهذا يجعل قراءة الكود أسهل لكل من البشر ومحللات الذكاء الاصطناعي.

## الخطوة 2: إنشاء مستند تجريبي (أو تحميل مستندك الخاص)

للتوضيح، سننشئ مستندًا صغيرًا يحتوي على فقرة وصورة مدمجة. استبدل هذا القسم بـ `Document.Load("YourFile.docx")` إذا كان لديك ملف مصدر بالفعل.

```csharp
// Step 2: Build a simple document with an image
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Add some text
builder.Writeln("Hello, Markdown world!");

// Insert an image from disk (make sure the path exists)
string imagePath = @"YOUR_DIRECTORY/sample-image.png";
builder.InsertImage(imagePath);
```

> **لماذا هذا مهم:** إذا تخطيت الصورة، لن يكون هناك شيء *لاستخراجه* لاحقًا، ولن ترى استدعاء الـ callback يعمل.

## الخطوة 3: ضبط MarkdownSaveOptions مع Callback لحفظ الموارد

هذا هو جوهر الحل. الـ `ResourceSavingCallback` يُستدعى لكل **مورد** خارجي—صور، خطوط، CSS، إلخ. سنستخدمه لإنشاء مجلد فرعي مخصص `Resources` ومنح كل ملف اسمًا فريدًا.

```csharp
// Step 3: Define markdown save options and attach a callback
var markdownSaveOptions = new MarkdownSaveOptions
{
    // This delegate runs for each resource the saver wants to write out
    ResourceSavingCallback = (sender, args) =>
    {
        // Ensure the Resources folder exists (creates it only once)
        string resourcesFolder = @"YOUR_DIRECTORY/Resources/";
        Directory.CreateDirectory(resourcesFolder);

        // Build a unique filename: img_0.png, img_1.jpg, etc.
        string resourceFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";

        // Tell the saver where to place the file
        args.SavePath = Path.Combine(resourcesFolder, resourceFileName);
    }
};
```

**ماذا يحدث؟**  
- `args.Index` هو عداد يبدأ من الصفر، يضمن التفرد.  
- `Path.GetExtension(args.FileName)` يحافظ على نوع الملف الأصلي (PNG، JPG، إلخ).  
- من خلال تعيين `args.SavePath`، نتجاوز الموقع الافتراضي ونحافظ على ترتيب كل شيء.

## الخطوة 4: حفظ المستند كـ Markdown

مع وجود الخيارات، يصبح التصدير سطرًا واحدًا:

```csharp
// Step 4: Export to markdown using the configured options
string outputMarkdown = @"YOUR_DIRECTORY/Doc.md";
doc.Save(outputMarkdown, markdownSaveOptions);
```

بعد التنفيذ ستجد:

- `Doc.md` يحتوي على نص markdown الذي يشير إلى الصور.
- مجلد `Resources` بجواره يحتوي على `img_0.png`، `img_1.jpg`، …  

هذا هو تدفق **how to save markdown**، مكتمل مع استخراج الموارد.

## الخطوة 5: التحقق من النتيجة (اختياري لكن موصى به)

افتح `Doc.md` في أي محرر نصوص. يجب أن ترى شيئًا مثل:

```markdown
Hello, Markdown world!

![image](Resources/img_0.png)
```

وسيحتوي مجلد `Resources` على الصورة الأصلية التي أدرجتها. إذا فتحت ملف markdown في عارض (مثل VS Code أو GitHub)، ستظهر الصورة بشكل صحيح.

> **سؤال شائع:** *ماذا لو أردت الصور في نفس مجلد ملف markdown؟*  
> فقط غير `resourcesFolder` إلى `Path.GetDirectoryName(outputMarkdown)` واضبط مسارات صور markdown وفقًا لذلك.

## استخراج الصور من Markdown – تعديلات متقدمة

أحيانًا تحتاج إلى مزيد من التحكم في قواعد التسمية أو ترغب في تخطي أنواع موارد معينة. فيما يلي بعض الاختلافات التي قد تكون مفيدة.

### 5.1 تخطي الموارد غير الصور

```csharp
ResourceSavingCallback = (sender, args) =>
{
    // Only process images; ignore CSS, fonts, etc.
    if (!args.ContentType.StartsWith("image/", StringComparison.OrdinalIgnoreCase))
        return; // Let the default handling continue

    // ...same folder creation logic as before...
};
```

### 5.2 الحفاظ على أسماء الملفات الأصلية

إذا كنت تفضل أسماء الملفات الأصلية بدلاً من `img_0`، فقط احذف جزء `args.Index`:

```csharp
string resourceFileName = args.FileName; // uses the name from the source document
```

### 5.3 استخدام مجلد فرعي مخصص لكل مستند

```csharp
string docName = Path.GetFileNameWithoutExtension(outputMarkdown);
string resourcesFolder = $@"YOUR_DIRECTORY/{docName}_Resources/";
Directory.CreateDirectory(resourcesFolder);
```

هذه الشفرات توضح **extract images from markdown** بطريقة مرنة، لتلبية مختلف اتفاقيات المشروع.

## الأسئلة المتكررة (FAQ)

| السؤال | الجواب |
|----------|--------|
| **هل يعمل هذا مع .NET Core؟** | بالتأكيد—Aspose.Words متعدد المنصات، لذا يعمل نفس الكود على Windows أو Linux أو macOS. |
| **ماذا عن صور SVG؟** | تُعامل ملفات SVG كصور؛ سيستقبل الـ callback امتداد `.svg`. تأكد من أن عارض markdown يدعم SVG. |
| **هل يمكنني تغيير صيغة markdown (مثلاً استخدام وسوم HTML `<img>` )؟** | اضبط `markdownSaveOptions.ExportImagesAsBase64 = false` وعدّل `ExportImagesAsHtml` إذا كنت تحتاج وسوم HTML صافية. |
| **هل هناك طريقة لمعالجة مجموعة من المستندات دفعة واحدة؟** | ضع المنطق السابق داخل حلقة `foreach` على مجموعة ملفات—فقط تذكر إعطاء كل مستند مجلد موارد خاص به. |

## مثال كامل جاهز للتنفيذ (نسخ‑لصق)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a document and add an image
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, Markdown world!");
        string imagePath = @"YOUR_DIRECTORY/sample-image.png"; // <-- change this
        builder.InsertImage(imagePath);

        // 2️⃣ Configure save options with a callback to extract images
        var markdownSaveOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (sender, args) =>
            {
                string resourcesFolder = @"YOUR_DIRECTORY/Resources/";
                Directory.CreateDirectory(resourcesFolder);

                string resourceFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
                args.SavePath = Path.Combine(resourcesFolder, resourceFileName);
            }
        };

        // 3️⃣ Save as markdown
        string outputPath = @"YOUR_DIRECTORY/Doc.md";
        doc.Save(outputPath, markdownSaveOptions);

        Console.WriteLine("Markdown saved successfully!");
        Console.WriteLine($"Check {outputPath} and the Resources folder for images.");
    }
}
```

شغّل البرنامج (`dotnet run`) وسترى رسائل وحدة التحكم التي تؤكد النجاح. الآن جميع الصور مخزنة بترتيب، وملف markdown يشير إليها بشكل صحيح.

## الخلاصة

لقد تعلمت الآن **how to save markdown** بينما **extract images from markdown** وتضمن أن المستند يمكن **saved document as markdown** مع تحكم كامل في مواقع الموارد. الفكرة الأساسية هي `ResourceSavingCallback`—فهو يمنحك سيطرة دقيقة على كل ملف خارجي يولده المصدّر.

من هنا يمكنك:

- دمج هذا التدفق في خدمة ويب تحول ملفات DOCX التي يرفعها المستخدم إلى markdown مباشرة.  
- توسيع الـ callback لإعادة تسمية الملفات وفقًا لاتفاقية تسمية تتوافق مع نظام إدارة المحتوى الخاص بك.  
- الجمع مع ميزات أخرى في Aspose.Words مثل `ExportImagesAsBase64` للحصول على markdown مع صور مدمجة.

جرّبه، عدّل منطق المجلد ليناسب مشروعك، ودع مخرجات markdown تتألق في خط أنابيب التوثيق الخاص بك.

--- 

![how to save markdown example](/assets/how-to-save-markdown.png "how to save markdown example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}