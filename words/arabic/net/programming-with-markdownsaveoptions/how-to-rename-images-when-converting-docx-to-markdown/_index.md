---
category: general
date: 2026-01-08
description: كيفية إعادة تسمية الصور أثناء تحويل DOCX إلى ماركداون. استخراج الصور
  من ملف DOCX، حفظ Word كماركداون، والحفاظ على تنظيم مواردك باستخدام Aspose.Words.
draft: false
keywords:
- how to rename images
- convert docx to markdown
- extract images from docx
- save word as markdown
- how to extract images
language: ar
og_description: كيفية إعادة تسمية الصور أثناء تحويل DOCX إلى markdown. تعلم استخراج
  الصور من docx وحفظ Word كـ markdown مع هيكل مجلد نظيف.
og_title: كيفية إعادة تسمية الصور عند تحويل DOCX إلى Markdown
tags:
- Aspose.Words
- C#
- Document Conversion
title: كيفية إعادة تسمية الصور عند تحويل DOCX إلى Markdown
url: /ar/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إعادة تسمية الصور عند تحويل DOCX إلى Markdown

**كيفية إعادة تسمية الصور** هي عقبة شائعة عندما تقوم بتحويل مستند Word (DOCX) إلى Markdown. هل فتحت ملف `.md` تم إنشاؤه لتجد مجموعة فوضوية من أسماء الصور مثل `image1.png`، `image2.jpeg` وتساءلت كيف تعطيها أسماء ذات معنى؟

في هذا الدرس ستتعلم طريقة نظيفة وقابلة للتكرار لاستخراج الصور من ملف DOCX، وإعادة تسمية كل صورة عند حفظها، والحصول في النهاية على مستند Markdown منظم يشير إلى أسماء الملفات الجديدة. سنستعرض أيضًا كيفية **convert docx to markdown**، **extract images from docx**، و **save word as markdown** باستخدام مكتبة Aspose.Words القوية لـ .NET.

> **نصيحة احترافية:** إذا كنت تستخدم Aspose.Words بالفعل لمهام مستندات أخرى، يمكنك إعادة استخدام كائن `Document` نفسه – لا حاجة لإضافات خارجية.

---

## ما ستحتاجه

- **.NET 6+** (أو .NET Framework 4.7.2+ – الكود يعمل بنفس الطريقة)
- حزمة NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)
- ملف `input.docx` تجريبي يحتوي على صورة واحدة على الأقل
- مجلد تريد أن يعيش فيه ملف الـ markdown والصور المستخرجة  

لا أدوات إضافية، لا محولات خارجية. فقط بضع أسطر من C#.

![مخطط كيفية إعادة تسمية الصور](https://example.com/placeholder.png "مخطط يوضح كيفية إعادة تسمية الصور وحفظها")

---

## الخطوة 1: إعداد رد نداء حفظ الموارد (Primary Keyword Here)

جوهر الحل هو تنفيذ مخصص لـ `IResourceSavingCallback`. يتيح لك هذا الرد نداء التحكم الكامل في اسم الملف وموقع كل مورد مضمّن—وهو بالضبط ما تحتاجه **لإعادة تسمية الصور** أثناء العملية.

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Custom callback that renames each extracted image and places it in a dedicated folder.
/// </summary>
class MyImageRenamer : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Ensure the folder exists – creates it if missing.
        string resourceFolder = "output/markdown_resources";
        Directory.CreateDirectory(resourceFolder);

        // Build a deterministic, readable name: img_0.png, img_1.jpg, …
        string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";

        // Combine folder and new name, then hand it back to Aspose.
        args.FileName = Path.Combine(resourceFolder, newFileName);

        // (Optional) If you need to modify the stream, you can replace args.Stream here.
    }
}
```

**لماذا هذا مهم:**  
بدلاً من السماح لـ Aspose بإنشاء أسماء ملفات عشوائية مستندة إلى GUID، يتيح لك الرد نداء تطبيق نظام تسمية سهل الفهم لاحقًا—مثالي للتحكم في الإصدارات أو خطوط أنابيب التوثيق.

---

## الخطوة 2: تكوين MarkdownSaveOptions لاستخدام الرد نداء

الآن نخبر Aspose أنه عندما يحفظ المستند كـ Markdown، يجب أن يستدعي `MyImageRenamer` الخاص بنا.

```csharp
// Create save options and plug in the callback.
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyImageRenamer()
};
```

لاحظ أننا لم نلمس أي خيارات أخرى. إذا احتجت إلى تعديل مستويات العناوين أو نمط كتل الشيفرة، فإن فئة `MarkdownSaveOptions` تحتوي على عشرات الخصائص—لا تتردد في الاستكشاف.

---

## الخطوة 3: تحميل ملف DOCX وإجراء التحويل

مع ربط الرد نداء، يصبح التحويل سطرًا واحدًا.

```csharp
// Load the source Word document that contains images.
Document doc = new Document("input/input.docx");

// Save as Markdown; images are automatically renamed and stored.
doc.Save("output/output.md", markdownOptions);
```

بعد تشغيل هذا، ستجد:

- `output/output.md` – ملف الـ Markdown مع روابط صور مثل `![Image](markdown_resources/img_0.png)`
- `output/markdown_resources/` – مجلد يحتوي على `img_0.png`، `img_1.jpg`، إلخ.

هذا هو سير عمل **save word as markdown** الكامل، مع دمج إعادة تسمية الصور.

---

## الخطوة 4: التحقق من النتيجة (How to Extract Images)

افتح ملف `output.md` الذي تم إنشاؤه في أي محرر نصوص. يجب أن ترى صيغة صورة markdown تشير إلى الملفات التي أُعيد تسميتها:

```markdown
![Image](markdown_resources/img_0.png)
![Diagram](markdown_resources/img_1.jpg)
```

إذا فتحت مجلد `markdown_resources`، ستجد الصور هناك بنمط `img_#`. هذا يثبت أننا نجحنا في **extract images from docx** ومنحناها أسماء قابلة للتوقع.

---

## أسئلة شائعة وحالات حافة

### ماذا لو أردت الاحتفاظ بأسماء الصور الأصلية؟

استبدل السطر الذي يُنشئ `newFileName` بشيء مشتق من `args.FileName` (الاسم الأصلي) أو من نص ALT الخاص بالصورة إذا كان متوفرًا:

```csharp
string cleanName = Path.GetFileNameWithoutExtension(args.FileName)
                     .Replace(" ", "_")
                     .ToLowerInvariant();
string newFileName = $"{cleanName}{Path.GetExtension(args.FileName)}";
```

### كيف أتعامل مع الأسماء المتكررة؟

أضف `args.Index` كلاحقة، أو حافظ على `HashSet<string>` داخل الرد نداء لضمان التفرد.

### هل يمكنني تغيير صيغة الصورة (مثال: PNG → JPEG)؟

نعم. يمكنك قراءة `args.Stream`، تحويل الصورة باستخدام `System.Drawing` أو `ImageSharp`، ثم تعيين تدفق جديد إلى `args.Stream` وتعديل `args.FileName` وفقًا لذلك.

### هل يعمل هذا مع SVG أو صيغ متجهة أخرى؟

تعامل Aspose.Words مع SVG كموارد صورة، لذا ينطبق نفس الرد نداء. فقط احرص على تعديل امتداد الملف عند إعادة التسمية.

### اعتبارات الأداء؟

يعمل الرد نداء مرة واحدة لكل مورد، لذا فإن الحمل الإضافي قليل. إذا كنت تعالج آلاف الصور، فكر في إنشاء المجلد الهدف دفعة واحدة خارج الرد نداء لتجنب استدعاءات `Directory.CreateDirectory` المتكررة (على الرغم من أن الطريقة بالفعل غير مكلفة).

---

## مثال كامل جاهز للتنفيذ (نسخ‑لصق)

فيما يلي البرنامج الكامل الذي يمكنك وضعه في تطبيق Console. يتضمن جميع عبارات `using`، فئة الرد نداء، ومنطق التحويل.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace DocxToMarkdownRenamer
{
    /// <summary>
    /// Callback that renames each extracted image and stores it in a subfolder.
    /// </summary>
    class MyImageRenamer : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourceFolder = "output/markdown_resources";
            Directory.CreateDirectory(resourceFolder);

            // Example naming scheme: img_0.png, img_1.jpg, …
            string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
            args.FileName = Path.Combine(resourceFolder, newFileName);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the DOCX that contains images.
            Document doc = new Document("input/input.docx");

            // 2️⃣ Set up Markdown options with our renamer.
            MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyImageRenamer()
            };

            // 3️⃣ Save as Markdown – images are renamed automatically.
            doc.Save("output/output.md", markdownOptions);

            Console.WriteLine("Conversion complete! Check the 'output' folder.");
        }
    }
}
```

شغّل البرنامج، وسترى رسالة في وحدة التحكم تؤكد نجاح التحويل. افتح `output/output.md` وستلاحظ فورًا مراجع الصور النظيفة.

---

## الخلاصة

استعرضنا **كيفية إعادة تسمية الصور** عندما **تحول docx إلى markdown** باستخدام Aspose.Words. من خلال الاستفادة من `IResourceSavingCallback` المخصص، تحصل على تحكم كامل بأسماء ملفات الصور، تنظيم المجلدات، وحتى تحويل صيغ الصور إذا لزم الأمر.

باختصار:

- نفّذ رد نداء لإعادة تسمية ونقل كل صورة.  
- اربط الرد نداء بـ `MarkdownSaveOptions`.  
- حمّل مستند Word واحفظه كـ Markdown.  

الآن يمكنك بثقة **extract images from docx**، الحفاظ على نظافة الـ markdown، ودمج العملية في خطوط أنابيب أتمتة أكبر.

**الخطوات التالية:**  
- جرّب تخصيص نظام التسمية ليشمل نص العنوان الأصلي (استخدم `doc.GetChildNodes`).  
- استكشف صيغ إخراج Aspose الأخرى مثل HTML أو PDF مع إعادة استخدام نمط الرد نداء نفسه.  
- دمج هذا مع خط أنابيب CI/CD لتوليد التوثيق تلقائيًا من ملفات Word المصدرية.  

هل لديك أسئلة إضافية حول معالجة الصور، صيغ المستندات الأخرى، أو حيل Aspose؟ اترك تعليقًا أدناه—برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}