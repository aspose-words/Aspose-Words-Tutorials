---
category: general
date: 2026-05-26
description: أنشئ مجلد الأصول أثناء تحويل Word إلى Markdown واستخراج الصور من ملف docx.
  تعلّم كيفية كتابة تدفق الصورة ومعالجة الموارد في Aspose.Words.
draft: false
keywords:
- create assets folder
- convert word to markdown
- extract images from docx
- convert docx with images
- write image stream
language: ar
og_description: أنشئ مجلد الأصول أثناء تحويل Word إلى Markdown. اتبع هذا الدليل خطوة
  بخطوة لاستخراج الصور من ملف docx وكتابة تدفق الصورة باستخدام Aspose.Words.
og_title: إنشاء مجلد الأصول لتحويل Word إلى Markdown
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create assets folder while you convert Word to Markdown and extract
    images from docx. Learn how to write image stream and handle resources in Aspose.Words.
  headline: Create Assets Folder for Convert Word to Markdown
  type: TechArticle
tags:
- Aspose.Words
- C#
- Markdown
- Docx
- Image Extraction
title: إنشاء مجلد الأصول لتحويل Word إلى Markdown
url: /ar/net/programming-with-markdownsaveoptions/create-assets-folder-for-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مجلد الأصول لتحويل Word إلى Markdown

هل احتجت إلى **إنشاء مجلد الأصول** عندما **تحول Word إلى Markdown**؟ إذا كنت تستخرج الصور من ملف DOCX، فإن إعداد ذلك المجلد بشكل صحيح هو الخطوة الأولى لتحويل سلس.  

في هذا الدرس سنستعرض العملية الكاملة لتحويل ملف `.docx` يحتوي على صور إلى ملف Markdown، مع استخراج تلك الصور تلقائيًا إلى دليل فرعي **assets**. في النهاية ستعرف كيف **استخراج الصور من docx**، **كتابة تدفق الصورة** إلى ملفات، والحفاظ على مراجع Markdown مرتبة.

## ما ستتعلمه

- كيفية تكوين **Aspose.Words** لتصدير Markdown  
- الكود الدقيق اللازم **إنشاء مجلد الأصول** أثناء التشغيل  
- كيف يسمح لك **ResourceSavingCallback** **استخراج الصور من docx** و **كتابة تدفق الصورة** إلى ملفات  
- كيفية التحقق من أن Markdown المُولد يربط الصور بشكل صحيح  
- نصائح لمعالجة الحالات الخاصة مثل تكرار أسماء الصور أو عدم وجود أذونات كتابة  

> **المتطلبات المسبقة** – تحتاج إلى .NET 6+ (أو .NET Framework 4.7.2+) وإشارة إلى مكتبة Aspose.Words for .NET. لا توجد أدوات طرف ثالث أخرى مطلوبة.

---

## إنشاء مجلد الأصول لتحويل Markdown

أول شيء يجب أن نضمنه هو وجود دليل **assets** بجوار ملف Markdown الناتج. سيستضيف هذا المجلد كل صورة يستخرجها عملية التحويل.

```csharp
// Ensure the assets folder exists before any conversion starts.
string assetsFolder = Path.Combine(outputDirectory, "assets");
Directory.CreateDirectory(assetsFolder);   // This call is idempotent – it won’t throw if the folder already exists.
```

> **نصيحة احترافية:** `Directory.CreateDirectory` آمن للاستدعاء المتكرر؛ فهو ينشئ المجلد فقط إذا كان غير موجود، مما يعني أنه يمكنك تشغيل التحويل عدة مرات دون القلق بشأن أخطاء “المجلد موجود بالفعل”.

---

## تحويل Word إلى Markdown مع استخراج الصور

الآن نقوم بربط Aspose.Words بكائن `MarkdownSaveOptions`. الجزء الحاسم هو `ResourceSavingCallback`. داخل الـ callback نـ **نكتب تدفق الصورة** (write image stream) إلى مجلد assets الذي أنشئ مسبقًا ثم نعيد كتابة اسم الملف بحيث يشير ملف Markdown إلى الموقع الصحيح.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// -------------------------------------------------------------------
// 1️⃣ Load the source .docx that contains images.
// -------------------------------------------------------------------
Document doc = new Document(@"YOUR_DIRECTORY\WithImages.docx");

// -------------------------------------------------------------------
// 2️⃣ Configure Markdown save options with a custom callback.
// -------------------------------------------------------------------
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // This delegate runs for every embedded resource (images, PDFs, etc.).
    ResourceSavingCallback = new ResourceSavingCallback(resourceInfo =>
    {
        // 2a️⃣ Build the full path for the output file inside the assets folder.
        string fileName = Path.GetFileName(resourceInfo.FileName); // Keep the original name.
        string outputPath = Path.Combine(assetsFolder, fileName);

        // 2b️⃣ Write the incoming stream (the image data) to disk.
        using (FileStream outStream = File.Create(outputPath))
        {
            // The stream contains the raw bytes of the image.
            resourceInfo.Stream.CopyTo(outStream);
        }

        // 2c️⃣ Update the reference that will appear in the Markdown file.
        // This tells Markdown to look for the image under the "assets" sub‑folder.
        resourceInfo.FileName = $"assets/{fileName}";
    })
};

// -------------------------------------------------------------------
// 3️⃣ Save the document as Markdown.
// -------------------------------------------------------------------
string markdownPath = Path.Combine(outputDirectory, "DocWithImages.md");
doc.Save(markdownPath, mdOptions);
```

### لماذا يعمل هذا

- **`ResourceSavingCallback`** يتم استدعاؤه لكل *مورد مدمج*—وبالتالي تقوم تلقائيًا **استخراج الصور من docx** دون كتابة منطق تحليل إضافي.  
- من خلال تعيين `resourceInfo.FileName = "assets/" + fileName;` نضمن أن يحتوي Markdown المُولد على رابط نسبي مثل `![Image](assets/picture.png)`.  
- يعمل الـ callback **بعد** أن يصبح تدفق الصورة متاحًا، وهذا هو السبب في أننا نستطيع بأمان **كتابة تدفق الصورة** إلى القرص.

## التحقق من النتيجة

بعد تشغيل الكود يجب أن ترى شيئين في `YOUR_DIRECTORY`:

1. `DocWithImages.md` – ملف Markdown يحتوي على مراجع صور تبدو مثل `![Image](assets/picture.png)`.  
2. مجلد `assets` يحتوي على ملفات الصور الفعلية (`picture.png`, `photo.jpg`, …).

افتح ملف Markdown في أي عارض (VS Code، GitHub، أو مولد موقع ثابت). يجب أن تُعرض الصور بشكل صحيح، مما يؤكد أنك نجحت في **تحويل docx مع الصور**.

## معالجة الحالات الشائعة

| الحالة | ما الذي يجب فعله |
|-----------|------------|
| **تكرار أسماء الصور** (مثال: ملفين `image1.png` متطابقين) | إضافة GUID أو عداد متزايد إلى `fileName` قبل الحفظ: <br>`string uniqueName = $"{Path.GetFileNameWithoutExtension(fileName)}_{Guid.NewGuid()}{Path.GetExtension(fileName)}";` |
| **مجلد المصدر للقراءة فقط** | تأكد من أن العملية تعمل تحت حساب يمتلك أذونات كتابة، أو غيّر `assetsFolder` إلى موقع يمكن للمستخدم الكتابة فيه (مثال: `%TEMP%`). |
| **مستندات كبيرة** (مئات الصور) | فكر في تحويل التدفق على دفعات أو زيادة حد الذاكرة للعملية؛ Aspose.Words يتعامل مع الملفات الكبيرة لكن نظام الملفات قد يصبح عنق زجاجة. |
| **موارد غير صور** (مثال: ملفات PDF مدمجة) | نفس الـ callback يعمل؛ فقط كن على علم بأن Markdown لا يمكنه تضمين ملفات PDF مباشرة— قد تحتاج إلى تعديل صيغة الرابط يدويًا. |

## مثال كامل يعمل (جاهز للنسخ واللصق)

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class WordToMarkdownWithAssets
{
    static void Main()
    {
        // -------------------------------------------------------------------
        // Define input and output locations.
        // -------------------------------------------------------------------
        string inputPath   = @"C:\Temp\WithImages.docx";
        string outputDir   = @"C:\Temp\Output";
        string markdownPath = Path.Combine(outputDir, "DocWithImages.md");
        string assetsFolder = Path.Combine(outputDir, "assets");

        // -------------------------------------------------------------------
        // Step 1: Ensure the assets folder exists.
        // -------------------------------------------------------------------
        Directory.CreateDirectory(assetsFolder);

        // -------------------------------------------------------------------
        // Step 2: Load the Word document.
        // -------------------------------------------------------------------
        Document doc = new Document(inputPath);

        // -------------------------------------------------------------------
        // Step 3: Set up Markdown save options with a resource callback.
        // -------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ResourceSavingCallback(resourceInfo =>
            {
                // Determine a safe file name.
                string originalName = Path.GetFileName(resourceInfo.FileName);
                string outputPath   = Path.Combine(assetsFolder, originalName);

                // Write the image (or other binary) stream to the assets folder.
                using (FileStream outStream = File.Create(outputPath))
                {
                    resourceInfo.Stream.CopyTo(outStream);
                }

                // Update the Markdown reference.
                resourceInfo.FileName = $"assets/{originalName}";
            })
        };

        // -------------------------------------------------------------------
        // Step 4: Save as Markdown.
        // -------------------------------------------------------------------
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("Conversion complete!");
        Console.WriteLine($"Markdown: {markdownPath}");
        Console.WriteLine($"Assets folder: {assetsFolder}");
    }
}
```

**الناتج المتوقع** (الكونسول):

```
Conversion complete!
Markdown: C:\Temp\Output\DocWithImages.md
Assets folder: C:\Temp\Output\assets
```

افتح `DocWithImages.md` وسترى روابط الصور تشير إلى `assets/…`. الصور نفسها موجودة في دليل `assets` الذي أنشأته للتو.

## الخلاصة

لقد أوضحنا لك كيفية **إنشاء مجلد الأصول** تلقائيًا أثناء **تحويل Word إلى Markdown**، وكيفية **استخراج الصور من docx** عن طريق **كتابة تدفق الصورة** إلى القرص. المثال الكامل القابل للتنفيذ يوضح الطريقة الموصى بها **لتحويل docx مع الصور** باستخدام Aspose.Words، مع معالجة كل من محتوى Markdown والموارد المرتبطة به في عملية واحدة مرتبة.

هل أنت مستعد للخطوة التالية؟ جرّب تخصيص الـ callback لإعادة تسمية الصور بناءً على النص البديل (alt‑text)، أو جرب صيغ إخراج أخرى مثل HTML أو PDF مع إعادة استخدام نفس منطق مجلد الأصول. النمط يتوسع بسهولة لأي سيناريو تحويل مستند إلى نص.

إذا واجهت أي مشاكل أو لديك أفكار للتحسين، اترك تعليقًا أدناه

## دروس ذات صلة

- [حفظ صور Word – تحويل Word إلى Markdown باستخدام Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [تحويل Word إلى Markdown – تضمين الصور كـ Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [تحويل Word إلى Markdown في C# – دليل كامل مع استخراج الصور](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-in-c-full-guide-with-image-extracti/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}