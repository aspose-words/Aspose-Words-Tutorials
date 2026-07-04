---
category: general
date: 2026-06-17
description: حوّل ملفات Word إلى Markdown بسرعة وتعلّم كيفية استخراج الصور من DOCX
  باستخدام رد نداء. مثال خطوة بخطوة لـ Aspose.Words.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- how to use callback
- convert docx to markdown
language: ar
og_description: حوّل مستند Word إلى Markdown باستخدام Aspose.Words وتعرّف على كيفية
  استخراج الصور من DOCX باستخدام رد نداء. مثال كامل للشفرة.
og_title: تحويل Word إلى Markdown – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Convert Word to Markdown quickly and learn how to extract images from
    DOCX using a callback. Step‑by‑step example for Aspose.Words.
  headline: Convert Word to Markdown – Complete Guide with Image Extraction
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Conversion
title: تحويل Word إلى Markdown – دليل شامل مع استخراج الصور
url: /ar/net/programming-with-markdownsaveoptions/convert-word-to-markdown-complete-guide-with-image-extractio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحويل Word إلى Markdown – دليل كامل مع استخراج الصور

هل تساءلت يومًا كيف **تحول Word إلى Markdown** دون فقدان أي صورة؟ لست وحدك. يحتاج العديد من المطورين إلى طريقة موثوقة لتحويل ملفات `.docx` إلى Markdown نظيف مع استخراج كل صورة مدمجة — فكر في إنشاء محتوى موقع ثابت من المستندات القديمة. في هذا الدرس سنستعرض حلًا عمليًا يحقق ذلك تمامًا، وسنظهر أيضًا **كيفية استخدام آلية الـ callback** للتحكم في مكان حفظ تلك الصور على القرص.

بنهاية هذا الدليل ستتمكن من:

* تحويل مستند Word إلى Markdown في استدعاء واحد.  
* استخراج الصور من ملفات DOCX وتخزينها في مجلد مخصص.  
* فهم نمط الـ callback الذي توفره Aspose.Words لمعالجة الموارد بدقة.  

بدون إطالة، مجرد مثال عملي قابل للتنفيذ يمكنك إدراجه في مشروعك.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من توفر ما يلي:

| المتطلب | لماذا يهم |
|-------------|----------------|
| **.NET 6.0+** (أو .NET Framework 4.6.2+) | تدعم Aspose.Words كلاهما؛ الإصدارات الأحدث تعطي أداءً أفضل. |
| حزمة **Aspose.Words for .NET** عبر NuGet | توفر الفئات `Document`، `MarkdownSaveOptions`، وواجهات الـ callback. |
| ملف **DOCX تجريبي** يحتوي على صور (مثل `input.docx`) | سنستخرج تلك الصور لتوضيح الـ callback. |
| بيئة تطوير مثل **Visual Studio 2022** أو **VS Code** | أي محرر يستطيع تجميع C# يكفي. |

يمكنك تثبيت المكتبة عبر سطر الأوامر:

```bash
dotnet add package Aspose.Words
```

هذا كل شيء—لا توجد تبعيات إضافية.

## الخطوة 1: تحميل مستند Word المصدر

أول ما نقوم به هو فتح ملف `.docx`. العملية نفسها سواء كنت ستحوله إلى HTML أو PDF أو Markdown.

```csharp
using Aspose.Words;
using System.IO;

// Load the Word document from disk
Document document = new Document(@"C:\Docs\input.docx");
```

> **نصيحة احترافية:** إذا كنت تتعامل مع تدفقات (مثلاً رفع ملف من نموذج ويب)، فإن `new Document(stream)` يعمل بنفس الفعالية.

## الخطوة 2: تعريف Callback – كيفية استخدام Callback لحفظ الموارد

تتيح لك Aspose.Words اعتراض عملية الحفظ عبر `IResourceSavingCallback`. هذا هو الجزء المتعلق **باستخراج الصور** في دليلنا. من خلال توفير callback نحدد بالضبط أين سيُكتب كل ملف صورة، أو حتى نتخطى الموارد غير المرغوب فيها.

```csharp
using Aspose.Words.Saving;

// Create the callback that controls image output
ResourceSavingCallback resourceCallback = new ResourceSavingCallback(
    (sender, args) =>
    {
        // Folder where all extracted images will live
        string resourcesFolder = @"C:\Docs\MarkdownResources";
        Directory.CreateDirectory(resourcesFolder);

        // Build a unique filename: img_0.png, img_1.jpg, etc.
        string fileName = $"img_{args.Index}{args.Extension}";
        args.Path = Path.Combine(resourcesFolder, fileName);

        // Uncomment the next line if you ever need to skip a resource
        // args.Cancel = true;
    });
```

### لماذا نحتاج Callback؟

* **تحكم دقيق** – أنت تحدد نظام التسمية والموقع.  
* **أداء** – تُكتب فقط الموارد التي تحتاجها إلى القرص.  
* **مرونة** – يعمل مع الصور، الخطوط المدمجة، أو أي أصل خارجي آخر.

## الخطوة 3: تكوين خيارات حفظ Markdown – تحويل DOCX إلى Markdown

الآن نربط الـ callback بمصدّر Markdown. هنا يحدث سحر **تحويل docx إلى markdown**.

```csharp
// Set up Markdown options and attach the callback
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // The callback defined above will be invoked for each image
    ResourceSavingCallback = resourceCallback,

    // Optional: keep original image formats (PNG, JPEG, etc.)
    ExportImagesAsBase64 = false
};
```

إذا كنت تفضّل تضمين الصور مباشرة كسلاسل Base64 داخل Markdown، عيّن `ExportImagesAsBase64 = true`. بالنسبة لمعظم مولّدات المواقع الثابتة، تكون ملفات الصور المنفصلة أنظف.

## الخطوة 4: حفظ المستند – الاستدعاء النهائي لتحويل Word إلى Markdown

مع كل شيء مُعد، استدعاء `Save` واحد يقوم بالمهمة الثقيلة: التحويل واستخراج الصور.

```csharp
// Output Markdown file path
string markdownPath = @"C:\Docs\Doc.md";

// Perform the conversion
document.Save(markdownPath, markdownOptions);
```

بعد تنفيذ هذا السطر، ستجد:

* `Doc.md` – تمثيل Markdown لمستند Word الخاص بك.  
* `C:\Docs\MarkdownResources\` – مجلد يحتوي على `img_0.png`، `img_1.jpg`، إلخ.

### مقتطف Markdown المتوقع

بافتراض أن DOCX الأصلي يحتوي على فقرة مع صورة، سيظهر Markdown المُولّد هكذا:

```markdown
![Image](MarkdownResources/img_0.png)
```

هذا السطر يشير مباشرة إلى ملف الصورة المستخرج، جاهز لبناء موقع ثابت.

## الخطوة 5: التحقق من النتيجة – تأكيد استخراج الصور

افتح `Doc.md` في أي محرر نصوص. يجب أن ترى ص syntax Markdown القياسي، ويجب أن تُحل كل إشارة صورة إلى ملف داخل `MarkdownResources`. جرّب فتح ملف Markdown في عارض مثل معاينة Markdown في VS Code؛ يجب أن تُعرض الصور بشكل صحيح.

إذا كانت صورة مفقودة، تحقق من منطق الـ callback:

* هل مسار المجلد يملك صلاحيات كتابة؟  
* هل تم تعيين `args.Cancel` إلى `true` عن غير قصد؟  

عادةً ما يحل تعديل هذين المكانين أي مشاكل.

## الحالات الخاصة والأخطاء الشائعة

| الحالة | ما الذي يجب مراقبته | الحل المقترح |
|-----------|-------------------|---------------|
| **DOCX يحتوي على صور SVG** | تقوم Aspose.Words بتحويل SVG إلى PNG افتراضيًا. | اقبل إخراج PNG أو قم بمعالجة لاحقة إذا كنت تحتاج SVG أصلي. |
| **مستندات كبيرة (100+ ميغابايت)** | يزداد استهلاك الذاكرة أثناء التحويل. | استخدم `LoadOptions` مع `LoadFormat.Docx` وفعل البث (streaming) إذا كان متاحًا. |
| **تحتاج نظام تسمية مخصص** | قد يتصادم الاسم الافتراضي `img_{index}` مع ملفات موجودة. | عدّل بناء `fileName` داخل الـ callback لإضافة GUID أو اسم الصورة الأصلي (`args.FileName`). |
| **تخطي الصور الزخرفية** | بعض الصور لا تحتاجها في Markdown. | داخل الـ callback، افحص بيانات `args.Image` (مثل `args.Image.Title`) وعين `args.Cancel = true` لتلك التي تريد تجاهلها. |

## مثال كامل يعمل (كل الكود في ملف واحد)

فيما يلي البرنامج الكامل جاهز للنسخ واللصق. استبدل المسارات بمساراتك الخاصة.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source DOCX
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Set up the callback to extract images
            ResourceSavingCallback imgCallback = new ResourceSavingCallback(
                (sender, callbackArgs) =>
                {
                    string resourcesFolder = @"C:\Docs\MarkdownResources";
                    Directory.CreateDirectory(resourcesFolder);

                    string fileName = $"img_{callbackArgs.Index}{callbackArgs.Extension}";
                    callbackArgs.Path = Path.Combine(resourcesFolder, fileName);
                    // Uncomment to skip a specific resource
                    // callbackArgs.Cancel = false;
                });

            // 3️⃣ Configure Markdown options and attach the callback
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = imgCallback,
                ExportImagesAsBase64 = false // Keep images as separate files
            };

            // 4️⃣ Save as Markdown – this also triggers image extraction
            string outputPath = @"C:\Docs\Doc.md";
            doc.Save(outputPath, mdOptions);

            Console.WriteLine("Conversion complete!");
            Console.WriteLine($"Markdown file: {outputPath}");
            Console.WriteLine($"Images saved in: C:\\Docs\\MarkdownResources");
        }
    }
}
```

شغّل البرنامج (`dotnet run` أو اضغط **F5** في Visual Studio). عندما يطبع الطرفية *“Conversion complete!”* تكون قد نجحت في **تحويل Word إلى Markdown** و**استخراج الصور من docx** في خطوة واحدة.

## ملخص – ما تم تغطيته

* **تحويل Word إلى Markdown** باستخدام `MarkdownSaveOptions`.  
* **كيفية استخراج الصور** عبر تنفيذ `IResourceSavingCallback`.  
* **كيفية استخدام callback** للتحكم بأسماء الملفات، مواقعها، وحتى تخطي الموارد.  
* **تحويل docx إلى markdown** من البداية إلى النهاية مع مثال C# قابل للتنفيذ.

## الخطوات التالية

الآن بعد أن لديك أساسًا قويًا، فكر في هذه التوسعات:

* **معالجة دفعات** – تكرار عبر مجلد من ملفات DOCX وإنشاء مجموعة Markdown مطابقة.  
* **إضافة Front‑matter** – إلحاق بيانات YAML في بداية كل ملف Markdown لمولدات المواقع الثابتة مثل Hugo أو Jekyll.  
* **تحسين الصور** – تمرير الصور المستخرجة عبر أداة مثل **ImageMagick** لتقليل حجمها قبل النشر.  

لا تتردد في التجربة—ربما تضيف مُعالج Markdown مخصص أو تدمج هذا في خط أنابيب CI. السماء هي الحد.

---

*برمجة سعيدة! إذا واجهت أي صعوبات، اترك تعليقًا أدناه وسأساعدك في حل المشكلة.*

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Convert Word to Markdown – Embed Images as Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}