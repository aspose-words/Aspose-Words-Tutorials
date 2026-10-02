---
category: general
date: 2026-01-10
description: احفظ صور Word أثناء تحويل ملف DOCX إلى Markdown باستخدام Aspose.Words.
  تعلّم كيفية استخراج الصور من ملف DOCX والحفاظ على تنظيمها.
draft: false
keywords:
- save word images
- convert word to markdown
- extract images from docx
- convert docx with images
- save document as markdown
language: ar
og_description: احفظ صور Word أثناء تحويل ملف DOCX إلى Markdown. يوضح لك هذا الدليل
  كيفية استخراج الصور من ملف DOCX والحفاظ على نظافة النتيجة.
og_title: حفظ صور Word – تحويل Word إلى Markdown باستخدام Aspose
tags:
- Aspose.Words
- C#
- Markdown
title: حفظ صور Word – تحويل Word إلى Markdown باستخدام Aspose
url: /ar/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ صور Word – تحويل Word إلى Markdown باستخدام Aspose

هل احتجت يوماً إلى **save word images** عندما تقوم بتحويل ملف `.docx` إلى Markdown؟ لست وحدك. يواجه العديد من المطورين مشكلة عندما تُسقط عملية التحويل الصور في ملف واحد أو، والأسوأ، تُفقدها تماماً.  

في هذا الدرس سنستعرض العملية الكاملة لـ **convert word to markdown** مع الحفاظ على كل صورة، استخراج الصور من docx، والحصول على ملف `output.md` نظيف بالإضافة إلى مجلد Resources مرتب. لا سحر، مجرد C# عادي و Aspose.Words.

## ما ستتعلمه

- كيفية إعداد Aspose.Words في مشروع .NET.  
- لماذا يعتبر `IResourceSavingCallback` المخصص هو المفتاح لـ **save word images** بشكل صحيح.  
- كود خطوة بخطوة يقوم بتحميل ملف DOCX، استخراج الصور، وكتابة ملف Markdown.  
- نصائح للتعامل مع الحالات الخاصة مثل أسماء الملفات المتكررة أو صيغ الصور غير المدعومة.  

**المتطلبات المسبقة**: .NET 6+ (أو .NET Framework 4.7+)، فهم أساسي لـ C#، ورخصة Aspose.Words (الإصدار التجريبي المجاني يكفي للاختبار).  

إذا كنت تتساءل *“لماذا لا أقوم بنسخ الصور يدوياً؟”* – لأن الأتمتة توفر الوقت، تقلل الأخطاء البشرية، وتسمح بالمعالجة على نطاق واسع عندما يكون لديك العشرات من المستندات.

---

## الخطوة 1 – إضافة Aspose.Words إلى مشروعك

أولاً، أضف المكتبة إلى الحل الخاص بك. أسهل طريقة هي عبر NuGet:

```bash
dotnet add package Aspose.Words
```

أو، إذا كنت تفضّل استخدام Package Manager Console في Visual Studio:

```powershell
Install-Package Aspose.Words
```

> **نصيحة محترف:** استخدم أحدث نسخة مستقرة (اعتباراً من يناير 2026 هي 24.9) للحصول على أحدث ميزات تصدير Markdown.

إضافة الـ namespace في أعلى الملف تجعل الكود منظمًا:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

الآن أنت جاهز لـ **save word images** برمجياً.

---

## الخطوة 2 – إنشاء Callback للتحكم في حفظ الصور

يقوم Aspose.Words باستدعاء Callback لكل مورد خارجي (صور، خطوط، إلخ) يحتاج إلى كتابته. من خلال تنفيذ `IResourceSavingCallback` تحدد **أين** تُحفظ كل صورة و**كيف** يُسمّى الملف.

```csharp
// Step 2: Callback that decides the folder and filename for each image.
class MyCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Define a folder relative to your project (adjust as needed).
        string resourcesFolder = @"YOUR_DIRECTORY/Resources/";

        // Ensure the folder exists – creates it on the first run.
        Directory.CreateDirectory(resourcesFolder);

        // Build a unique filename using a GUID to avoid collisions.
        string uniqueFileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // Combine folder and filename, then tell Aspose to write there.
        args.ResourceFileName = Path.Combine(resourcesFolder, uniqueFileName);
        args.Stream = new FileStream(args.ResourceFileName, FileMode.Create);
    }
}
```

**لماذا هذا مهم:** بدون الـ Callback، سيقوم Aspose بإسقاط جميع الصور في نفس المجلد بأسماء عامة مثل `image001.png`. المنطق المخصص يضمن هيكلًا نظيفًا وخاليًا من التعارض—مثالي للمشاريع التي **convert docx with images** على نطاق واسع.

---

## الخطوة 3 – تحميل مستند Word المصدر

الآن وجه Aspose إلى ملف `.docx` الذي تريد تحويله. استبدل `YOUR_DIRECTORY` بالمسار الفعلي على جهازك.

```csharp
// Step 3: Load the Word file that contains the pictures.
Document document = new Document(@"YOUR_DIRECTORY/input.docx");
```

إذا لم يكن الملف موجودًا، سيُطلق Aspose استثناء `FileNotFoundException`. يمكن لشرط `if (!File.Exists(...))` أن يوفر عليك وقت التصحيح.

---

## الخطوة 4 – إعداد MarkdownSaveOptions وإرفاق الـ Callback

كائن `MarkdownSaveOptions` يتيح لك ضبط عملية التصدير بدقة. هنا نربط الـ `MyCallback` من الخطوة 2.

```csharp
// Step 4: Set up Markdown options and hook the resource‑saving callback.
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // The callback will be invoked for every image.
    ResourceSavingCallback = new MyCallback(),

    // Optional: control how headings are rendered.
    ExportHeadersFooters = false,

    // Optional: preserve original line breaks.
    PreserveOriginalLineBreaks = true
};
```

يمكنك أيضًا تعديل `ImageSavingCallback` إذا احتجت إلى تغيير حجم الصور أثناء العملية، لكن في معظم الحالات التعامل الافتراضي يكفي.

---

## الخطوة 5 – حفظ المستند كملف Markdown

أخيرًا، أخبر Aspose بكتابة ملف Markdown. ستُحفظ جميع الصور في المجلد الذي حددته، وسيشير الـ markdown إلى الصور باستخدام مسارات نسبية.

```csharp
// Step 5: Save the document as Markdown; images are written via the callback.
document.Save(@"YOUR_DIRECTORY/output.md", markdownOptions);
```

عند اكتمال الحفظ، يجب أن ترى شيئًا مشابهًا لـ:

```
output.md
Resources/
   img_3f9a2c1b-7e4d-4b8a-9c2e-1a2b3c4d5e6f.png
   img_a1b2c3d4-e5f6-7890-abcd-ef1234567890.jpg
```

افتح `output.md` في أي محرر—كل إشارة إلى صورة ستظهر كـ `![Image](Resources/img_...png)`. هذا هو نتيجة **save word images** التي أردتها.

---

## أسئلة شائعة ومعالجة الحالات الخاصة

### ماذا لو أردت نظام تسمية مخصص؟

استبدل الـ GUID بنسخة منقحة من اسم الملف الأصلي:

```csharp
string safeName = Path.GetFileNameWithoutExtension(args.ResourceFileName)
                     .Replace(" ", "_")
                     .ToLowerInvariant();
string uniqueFileName = $"{safeName}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";
```

### كيف أتجنب تكرار الصور عبر مستندات متعددة؟

احفظ الصور في مجلد مشترك وتحقق من وجود هاشات متطابقة قبل الكتابة:

```csharp
using (var md5 = System.Security.Cryptography.MD5.Create())
{
    byte[] hash = md5.ComputeHash(File.ReadAllBytes(args.Stream.Name));
    string hashString = BitConverter.ToString(hash).Replace("-", "").ToLowerInvariant();
    string finalPath = Path.Combine(resourcesFolder, $"{hashString}{Path.GetExtension(args.ResourceFileName)}");
    if (!File.Exists(finalPath))
        args.Stream = new FileStream(finalPath, FileMode.Create);
    else
        args.Stream = null; // Skip writing; markdown will reference existing file.
}
```

### هل يعمل هذا مع .NET Core على Linux؟

بالتأكيد. يستخدم الكود واجهات برمجة تطبيقات عبر‑المنصات فقط (`System.IO`). فقط تأكد من أن مسار `Resources` يستخدم الشرطات المائلة للأمام أو `Path.Combine`.

---

## مثال كامل جاهز للنسخ واللصق

فيما يلي البرنامج بالكامل في ملف واحد. استبدل `YOUR_DIRECTORY` بالمجلد الفعلي لديك.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class MyCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        string resourcesFolder = @"YOUR_DIRECTORY/Resources/";
        Directory.CreateDirectory(resourcesFolder);

        string uniqueFileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";
        args.ResourceFileName = Path.Combine(resourcesFolder, uniqueFileName);
        args.Stream = new FileStream(args.ResourceFileName, FileMode.Create);
    }
}

class Program
{
    static void Main()
    {
        // Load the DOCX that contains images.
        Document document = new Document(@"YOUR_DIRECTORY/input.docx");

        // Configure Markdown options and attach the callback.
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyCallback(),
            ExportHeadersFooters = false,
            PreserveOriginalLineBreaks = true
        };

        // Save as Markdown; images are saved to the Resources folder.
        document.Save(@"YOUR_DIRECTORY/output.md", markdownOptions);

        Console.WriteLine("Conversion complete! Check the Resources folder for saved images.");
    }
}
```

شغّل البرنامج (`dotnet run` أو عبر Visual Studio) وستحصل على ملف Markdown يقوم بـ **convert word to markdown** مع الحفاظ على كل صورة.

---

## الخلاصة

لقد تعلمت الآن كيفية **save word images** عند **convert docx with images** إلى Markdown باستخدام Aspose.Words. من خلال ربط `IResourceSavingCallback` مخصص، تتحكم تمامًا في مكان حفظ كل صورة، مما يمنحك هيكل مجلد منظم وروابط موثوقة داخل `output.md`.  

من هنا يمكنك:

- **extract images from docx** لمعالجة منفصلة (مثل OCR).  
- ربط هذا التحويل في خط أنابيب CI لمعالجة دفعات من الملفات.  
- استكشاف صيغ تصدير أخرى (HTML, PDF) باستخدام Callbacks مشابهة.  

جرّبه في مشروع حقيقي، عدّل منطق التسمية ليناسب معاييرك، ودع الأتمتة تتولى الجزء الصعب. برمجة سعيدة!

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}