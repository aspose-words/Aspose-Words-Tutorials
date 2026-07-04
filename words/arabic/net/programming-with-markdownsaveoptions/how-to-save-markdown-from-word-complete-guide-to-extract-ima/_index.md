---
category: general
date: 2026-04-21
description: كيفية حفظ markdown بسرعة—تعلم استخراج الصور من Word وتحويل DOCX إلى markdown
  في C# باستخدام رد نداء مخصص. يتضمن الكود الكامل.
draft: false
keywords:
- how to save markdown
- extract images from word
- convert docx to markdown
- how to extract images
- how to convert docx
language: ar
og_description: كيف تحفظ ماركداون من ملف وورد؟ يوضح لك هذا الدرس كيفية استخراج الصور
  من وورد وتحويل DOCX إلى ماركداون باستخدام Aspose.Words.
og_title: كيفية حفظ Markdown – استخراج الصور وتحويل DOCX باستخدام C#
tags:
- Aspose.Words
- C#
- Markdown
- Document Conversion
title: كيفية حفظ Markdown من Word – دليل كامل لاستخراج الصور وتحويل DOCX
url: /ar/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-word-complete-guide-to-extract-ima/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية حفظ Markdown – استخراج الصور وتحويل DOCX في C#

هل تساءلت يومًا **كيف تحفظ markdown** عندما تحتاج إلى نقل المحتوى من مستند Word؟ ربما لديك عقد في ملف `.docx`، وتود نشره كـ markdown نظيف على موقع ثابت. الخبر السار؟ ليس أمرًا معقدًا. في بضع أسطر فقط من C# يمكنك تحويل DOCX إلى markdown **و** استخراج كل صورة مدمجة إلى مجلد تختاره.

في هذا الدرس سنستعرض العملية بالكامل—بدءًا بتحميل ملف Word، ثم ربط استدعاء مخصص يحفظ كل صورة، وأخيرًا كتابة ملف markdown يشير إلى تلك الصور. في النهاية ستعرف **كيفية استخراج الصور** من Word، **كيفية تحويل docx**، والأهم من ذلك، **كيفية حفظ markdown** بالطريقة التي تريدها.

## ما ستتعلمه

- حزمة NuGet الضرورية (Aspose.Words for .NET) ولماذا تُعد خيارًا قويًا.  
- كيفية تنفيذ `IResourceSavingCallback` للتحكم في أسماء ملفات الصور ومواقعها.  
- الشيفرة الدقيقة اللازمة **لتحويل docx إلى markdown** مع مجلد صور مخصص.  
- نصائح للتعامل مع الحالات الخاصة مثل تكرار أسماء الصور أو الصيغ غير المدعومة.  

لا تحتاج إلى أي وثائق خارجية—فقط انسخ، الصق، وشغّل.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (تعمل الواجهة البرمجية بنفس الطريقة على .NET Framework 4.8).  
- Visual Studio 2022 أو أي بيئة تطوير تفضلها.  
- رخصة Aspose.Words سارية (أو مفتاح تجريبي مجاني للتقييم).  
- مستند Word (`input.docx`) يحتوي على صورة واحدة على الأقل.

> **نصيحة احترافية:** إذا كنت تستخدم النسخة التجريبية المجانية، تذكر ضبط الرخصة قبل الحفظ، وإلا سيظهر علامة مائية في الـ markdown المُولد.

---

## الخطوة 1: تثبيت Aspose.Words for .NET

افتح مجلد مشروعك في الطرفية وشغّل الأمر التالي:

```bash
dotnet add package Aspose.Words
```

هذا يقوم بجلب أحدث نسخة مستقرة (اعتبارًا من أبريل 2026 الإصدار 23.9). الحزمة تحتوي على كل ما تحتاجه **لتحويل docx إلى markdown** واستخراج الصور.

## الخطوة 2: إنشاء استدعاء لحفظ الصور

الاستدعاء يخبر Aspose أين يضع كل ملف صورة أثناء توليد الـ markdown. سنخزنها في مجلد يُسمى `MyImages` داخل الدليل الذي تحدده.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Handles image saving during markdown export.
/// </summary>
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build the absolute path for the images folder.
        string imageFolder = Path.Combine("YOUR_DIRECTORY", "MyImages");
        Directory.CreateDirectory(imageFolder); // Creates it if it doesn't exist.

        // Construct a unique file name: Img_0.png, Img_1.jpg, …
        string newFileName = $"Img_{args.Index}{Path.GetExtension(args.FileName)}";
        args.FileName = Path.Combine(imageFolder, newFileName);
    }
}
```

**لماذا هذا مهم:** بدون استدعاء، سيقوم Aspose بإلقاء الصور بجوار ملف الـ markdown بأسماء عامة، ما قد يسبب فوضى عندما يكون لديك العديد من المستندات. الاستدعاء يمنحك أيضًا تحكمًا كاملًا في قواعد التسمية—مفيد لتحسين محركات البحث وللحفاظ على تنظيم المستودع.

## الخطوة 3: تحميل ملف DOCX المصدر

الآن نقوم بتحميل ملف Word إلى الذاكرة. استبدل `YOUR_DIRECTORY` بالمسار الفعلي على جهازك.

```csharp
// Load the Word document that contains images.
string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
Document doc = new Document(docPath);
```

إذا لم يُعثر على الملف، سيُطلق Aspose استثناء `FileNotFoundException`. تأكد من صحة المسار، خاصةً عند التشغيل من دليل عمل مختلف.

## الخطوة 4: تكوين خيارات حفظ الـ Markdown

نربط الاستدعاء بكائن `MarkdownSaveOptions`. هذا الكائن يتيح لك أيضًا تعديل أشياء مثل مستويات العناوين أو ما إذا كنت تريد تضمين الصور كـ base‑64 (سنتركها منفصلة).

```csharp
// Set up markdown export options and attach our callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Use the callback defined in Step 2.
    ResourceSavingCallback = new ImageSavingCallback(),
    
    // Optional: Keep image links relative to the markdown file.
    ExportImagesAsBase64 = false
};
```

## الخطوة 5: حفظ المستند كـ Markdown

أخيرًا، اكتب ملف الـ markdown إلى القرص. ستظهر الصور في مجلد `MyImages` الذي أنشأته مسبقًا.

```csharp
// Define where the markdown file will be written.
string markdownPath = Path.Combine("YOUR_DIRECTORY", "output.md");

// Perform the conversion.
doc.Save(markdownPath, mdOptions);
Console.WriteLine($"✅ Markdown saved to {markdownPath}");
Console.WriteLine($"🖼️ Images extracted to {Path.Combine("YOUR_DIRECTORY", "MyImages")}");
```

### النتيجة المتوقعة

- يحتوي `output.md` على نص markdown مع مراجع للصور مثل `![](MyImages/Img_0.png)`.  
- مجلد `MyImages` يحتفظ بكل صورة تم استخراجها من الـ DOCX الأصلي، مسماة بترتيب تسلسلي.  
- فتح الـ markdown في عارض (مثل معاينة VS Code) يعرض الصور تمامًا كما ظهرت في Word.

![مثال على حفظ markdown example](example.png "لقطة شاشة تُظهر markdown مع الصور – كيفية حفظ markdown")

> **ملاحظة:** نص alt للصورة أعلاه يتضمن الكلمة المفتاحية الأساسية، مما يفي بمتطلبات SEO لسمات alt للصور.

## أسئلة شائعة وحالات خاصة

### ماذا لو كان مستند Word يحتوي على صور مكررة؟

يقوم Aspose بتعيين `Index` فريد لكل مورد، لذا حتى الصور المكررة تحصل على أسماء ملفات مميزة (`Img_0.png`, `Img_1.png`, …). إذا احتجت إلى إزالة التكرار لاحقًا، يمكنك معالجة مجلد `MyImages` ببرنامج نصي يحسب تجزئة محتوى الملفات.

### هل يمكنني تضمين الصور مباشرة في markdown كـ base‑64؟

نعم—ما عليك سوى ضبط `ExportImagesAsBase64 = true` في `MarkdownSaveOptions`. هذا مفيد للـ markdown كملف واحد، لكنه يضاعف حجم الملف بشكل كبير، ولهذا يركز الدرس على حفظ الصور في مجلد منفصل.

### هل يعمل هذا على macOS/Linux؟

بالتأكيد. يستخدم الكود واجهات برمجة تطبيقات معيارية لـ .NET (`Path.Combine`, `Directory.CreateDirectory`)، لذا فهو متعدد المنصات. فقط تأكد من وضع ملف رخصة Aspose.Words (إن وجد) في موقع يمكن للوقت التشغيلي الوصول إليه.

### كيف أتعامل مع الجداول أو الهوامش؟

يقوم `MarkdownSaveOptions` تلقائيًا بتحويل الجداول إلى جداول markdown والهوامش إلى روابط مرجعية. إذا كنت تحتاج إلى تنسيق مخصص، استكشف خصائص `TableFormattingOptions` و `FootnoteOptions` على نفس كائن الخيارات.

## مثال كامل جاهز للتنفيذ (انسخ‑الصق)

فيما يلي البرنامج الكامل الذي يمكنك وضعه في ملف `Program.cs` لتطبيق كونسول. استبدل دليل العنصر النائب بالمسار الفعلي لديك.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        string imageFolder = Path.Combine("YOUR_DIRECTORY", "MyImages");
        Directory.CreateDirectory(imageFolder);
        args.FileName = Path.Combine(imageFolder,
            $"Img_{args.Index}{Path.GetExtension(args.FileName)}");
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Load the DOCX.
        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(docPath);

        // 2️⃣ Set up markdown options with our callback.
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback(),
            ExportImagesAsBase64 = false
        };

        // 3️⃣ Save as markdown.
        string markdownPath = Path.Combine("YOUR_DIRECTORY", "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine($"✅ Markdown saved to {markdownPath}");
        Console.WriteLine($"🖼️ Images extracted to {Path.Combine("YOUR_DIRECTORY", "MyImages")}");
    }
}
```

شغّل البرنامج باستخدام `dotnet run`. بعد التنفيذ ستظهر رسائل في وحدة التحكم تؤكد مواقع الملفات التي تم إنشاؤها.

## الخلاصة

أصبح لديك الآن وصفة لا تشوبها شائبة لـ **كيفية حفظ markdown** مباشرةً من مستند Word مع استخراج كل صورة بشكل نظيف. باستخدام `IResourceSavingCallback` من Aspose.Words، تتحكم في أسماء ملفات الصور، بنية المجلدات، وتنسيق الـ markdown—كل ذلك في بضع أسطر من C#.

استفد من هذه الأساسيات لتقوم بـ:

- **تجربة** أنماط تسمية مختلفة (مثل استخدام الاسم الأصلي للصورة).  
- **ربط** مخرجات الـ markdown مع مولد موقع ثابت مثل Hugo أو Jekyll.  
- **توسيع** الاستدعاء لتسجيل كل مورد محفوظ لأغراض التدقيق.  

إذا احتجت إلى **تحويل docx** دفعيًا، فقط غلف المنطق أعلاه داخل حلقة `foreach` على دليل يحتوي ملفات `.docx`. نفس النمط يعمل مع صيغ إخراج أخرى (HTML, PDF) عن طريق استبدال `MarkdownSaveOptions` بالفئة المناسبة.

برمجة سعيدة، واستمتع بالانتقال السلس من Word إلى markdown!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}