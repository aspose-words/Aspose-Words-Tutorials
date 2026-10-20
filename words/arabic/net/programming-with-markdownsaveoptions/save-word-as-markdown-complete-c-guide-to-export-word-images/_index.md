---
category: general
date: 2026-04-02
description: تعلم كيفية حفظ مستند Word كملف markdown وتحويل docx إلى markdown مع تصدير
  صور Word واستخراج الصور المضمنة باستخدام Aspose.Words.
draft: false
keywords:
- save word as markdown
- convert docx to markdown
- export word images
- extract embedded images
language: ar
og_description: احفظ مستند Word كملف markdown باستخدام C# و Aspose.Words. يوضح هذا
  الدليل كيفية تحويل docx إلى markdown، وتصدير صور Word، واستخراج الصور المضمنة.
og_title: حفظ Word كـ Markdown – دورة C# كاملة
tags:
- Aspose.Words
- C#
- Document Conversion
title: حفظ Word كـ Markdown – دليل C# الكامل لتصدير صور Word
url: /ar/net/programming-with-markdownsaveoptions/save-word-as-markdown-complete-c-guide-to-export-word-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ Word كـ Markdown – دليل C# الكامل

هل احتجت يومًا إلى **حفظ Word كـ markdown** لكن لم تكن متأكدًا من كيفية الحفاظ على الصور سليمة؟ أنت لست وحدك. يواجه العديد من المطورين صعوبة عندما يحاولون تحويل ملف DOCX إلى markdown ويرغبون في أن تظهر الصور الأصلية بشكل صحيح.  

في هذا الدرس سنستعرض حلًا واحدًا مكتملًا **يحوّل docx إلى markdown**، **يصدّر صور word**، وحتى **يستخرج الصور المدمجة** باستخدام Aspose.Words for .NET. في النهاية ستحصل على برنامج جاهز للتنفيذ ينتج ملف `.md` نظيف إلى جانب مجلد يحتوي على ملفات صور مسماة بترتيب.

> **لماذا العناء؟**  
> Markdown هي اللغة المشتركة للوثائق الحديثة، مولدات المواقع الثابتة، ومدونات المطورين. الحفاظ على أصولك المستندة إلى Word في markdown يعني أنك تستطيع التحكم في إصداراتها، معاينتها فورًا، وتجنب تنسيق `.docx` الضخم في خطوط أنابيب CI.

---

## ما ستحتاجه

- **Aspose.Words for .NET** (أحدث نسخة، مثلاً 23.12). يمكنك الحصول عليها من NuGet: `Install-Package Aspose.Words`.
- **.NET 6+** (أي SDK حديث يعمل؛ الكود يُترجم على .NET Framework 4.7 أيضًا).
- **عينة DOCX** تحتوي على عدد قليل من الصور—سيكون هذا هو مستند الاختبار الخاص بنا.
- **دليل قابل للكتابة** حيث سيقع ملف markdown ومجلد الصور.

لا مكتبات إضافية، ولا حيل سطر أوامر معقدة. فقط الكود أدناه وقليل من إعداد المجلد.

## الخطوة 1 – إعداد رد نداء حفظ الموارد  

عند كتابة Aspose.Words لملف markdown يمكنه تمرير كل صورة لك عبر `IResourceSavingCallback`. من خلال تنفيذ هذه الواجهة نتحكم بدقة في مكان حفظ كل صورة وكيفية تسميتها.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

/// <summary>
/// Custom callback that stores every image in a dedicated Resources folder
/// and gives it a sequential, zero‑padded name (img_0001.png, img_0002.jpg, …).
/// </summary>
class MyMarkdownCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Define the folder that will hold the exported images.
        string resourcesFolder = @"C:\MyExport\Resources\";

        // Ensure the folder exists – creates it the first time the callback runs.
        Directory.CreateDirectory(resourcesFolder);

        // Build a deterministic file name: img_####.<extension>
        args.FileName = Path.Combine(resourcesFolder,
            $"img_{args.ImageIndex:D4}{args.FileExtension}");

        // If you wanted to modify the image stream (e.g., resize or re‑encode)
        // you could replace args.Stream here. For now we just let Aspose write it.
    }
}
```

**لماذا رد نداء؟**  
بدون ذلك سيقوم Aspose بإلقاء الصور بجوار ملف markdown بأسماء GUID مُولدة تلقائيًا—صعب تتبعه وفوضوي للتحكم في الإصدارات. رد النداء يمنحك تحكمًا كاملاً، مما يجعل المخرجات قابلة لإعادة الإنتاج ومنظمة.

## الخطوة 2 – تحميل مستند Word المصدر الخاص بك  

الآن نوجه Aspose إلى ملف DOCX الذي تريد تحويله إلى markdown. فئة `Document` تُجرد تنسيق الملف بالكامل، وتوفر لك نموذج كائن نظيف.

```csharp
// Replace the path with the location of your .docx file.
string inputPath = @"C:\MyExport\input.docx";

Document doc = new Document(inputPath);
```

إذا كان الملف يحتوي على عناصر معقدة (جداول، مخططات، أو صناديق نصية عائمة) سيتعامل Aspose.Words معها تلقائيًا، محولًا ما يمكنه إلى ما يعادله في markdown.

## الخطوة 3 – تكوين خيارات حفظ Markdown  

هنا نربط رد النداء بعملية الحفظ. فئة `MarkdownSaveOptions` تتيح لك أيضًا تعديل بعض الإعدادات الخاصة بـ markdown (مثل استخدام markdown بنكهة GitHub).

```csharp
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Use GitHub‑flavored markdown for better compatibility with GitHub/Bitbucket.
    ExportImagesAsBase64 = false,          // We want separate image files, not inline data URIs.
    ResourceSavingCallback = new MyMarkdownCallback(),
    // Optional: force UTF‑8 encoding (the default, but explicit is clearer).
    Encoding = System.Text.Encoding.UTF8
};
```

**نصيحة احترافية:** إذا احتجت يومًا إلى تضمين الصور مباشرة في markdown (مثلاً لملف README واحد)، اضبط `ExportImagesAsBase64 = true` وتجاوز رد النداء.

## الخطوة 4 – حفظ المستند كـ Markdown  

أخيرًا، نكتب ملف `.md`. سيستدعي Aspose رد النداء الخاص بنا لكل صورة يكتشفها، ويضع الملفات في المجلد الذي حددناه مسبقًا.

```csharp
// Destination markdown file.
string outputPath = @"C:\MyExport\output.md";

doc.Save(outputPath, mdOptions);
```

عند انتهاء الحفظ يجب أن ترى:

- `output.md` – نص markdown المُحوَّل.
- مجلد `Resources\` يحتوي على `img_0001.png`، `img_0002.jpg`، إلخ.

**مقتطف markdown المتوقع** (مقتطع للاختصار):

```markdown
# Sample Document

Here is an introductory paragraph.

![Image 1](Resources/img_0001.png)

More text follows, perhaps a table:

| Header A | Header B |
|----------|----------|
| Cell 1   | Cell 2   |
```

روابط الصور تشير إلى مجلد `Resources`، تمامًا كما أردنا.

## الخطوة 5 – التحقق من الصور المصدَّرة  

من السهل التحقق مرتين أن كل صورة مدمجة تم استخراجها من ملف Word.

```csharp
// Quick sanity check – count the images saved.
string resourcesFolder = @"C:\MyExport\Resources\";
int imageCount = Directory.GetFiles(resourcesFolder).Length;
Console.WriteLine($"Exported {imageCount} image(s) to {resourcesFolder}");
```

إذا كان العدد يطابق عدد الصور التي تراها في DOCX الأصلي، فقد نجحت في **استخراج الصور المدمجة**.

## أسئلة شائعة وحالات حافة  

### ماذا لو كان DOCX يحتوي على رسومات SVG أو EMF؟  
Aspose.Words يحول الصيغ المتجهة إلى PNG بشكل افتراضي. إذا كنت بحاجة إلى صيغة نقطية مختلفة، عدل `args.FileExtension` داخل رد النداء.

### هل يمكنني تغيير نظام تسمية الصور؟  
بالطبع. يمنحك رد النداء تحكمًا كاملاً في `args.FileName`. على سبيل المثال، يمكنك الحفاظ على اسم الصورة الأصلي بقراءة `args.ImageFileName` (إن كان متاحًا) أو إضافة تجزئة لضمان التفرد.

### كيف أتعامل مع مستندات كبيرة تحتوي على مئات الصور؟  
فكّر في تدفق مجلد الإخراج إلى موقع مؤقت وتنظيفه بعد استهلاك markdown. أيضًا، اضبط `mdOptions.ExportImagesAsBase64 = true` إذا كنت تفضّل ملف markdown واحد—مع أن حجم الملف سيزداد.

### هل يعمل هذا على .NET Core على Linux؟  
نعم. الاستدعاء الوحيد الخاص بالمنصة هو `Directory.CreateDirectory`، وهو متعدد المنصات. فقط تأكد من أن صيغة المسار تتوافق مع نظام التشغيل الخاص بك (`/home/user/...` على Linux).

## مثال كامل يعمل  

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في تطبيق Console. يتضمن جميع الأجزاء التي ناقشناها، بالإضافة إلى أداة مساعدة صغيرة لتشغيل markdown في المحرّك الافتراضي (اختياري).

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Diagnostics;
using System.IO;

class MyMarkdownCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        string resourcesFolder = @"C:\MyExport\Resources\";
        Directory.CreateDirectory(resourcesFolder);
        args.FileName = Path.Combine(resourcesFolder,
            $"img_{args.ImageIndex:D4}{args.FileExtension}");
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Load the DOCX.
        string inputPath = @"C:\MyExport\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Configure markdown options with our callback.
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ExportImagesAsBase64 = false,
            ResourceSavingCallback = new MyMarkdownCallback(),
            Encoding = System.Text.Encoding.UTF8
        };

        // 3️⃣ Save as markdown.
        string outputPath = @"C:\MyExport\output.md";
        doc.Save(outputPath, mdOptions);

        // 4️⃣ Verify image count.
        string resourcesFolder = @"C:\MyExport\Resources\";
        int imageCount = Directory.GetFiles(resourcesFolder).Length;
        Console.WriteLine($"✅ Saved markdown to {outputPath}");
        Console.WriteLine($"📁 Exported {imageCount} image(s) to {resourcesFolder}");

        // 5️⃣ (Optional) Open the markdown file for a quick look.
        if (File.Exists(outputPath))
        {
            Process.Start(new ProcessStartInfo
            {
                FileName = outputPath,
                UseShellExecute = true
            });
        }
    }
}
```

شغّل البرنامج، افتح `output.md` في محرّكك المفضّل، وسترى مستند markdown نظيف مع روابط صور صحيحة. هذا كل شيء—سير عمل **convert docx to markdown** الآن مؤتمت بالكامل.

## الخلاصة  

لقد غطينا للتو كيفية **حفظ Word كـ markdown** مع الحفاظ على كل صورة، وبالتالي **تصدير صور word** و**استخراج الصور المدمجة**. النقاط الرئيسية هي:

1. تنفيذ `IResourceSavingCallback` للتحكم في وضع الصور وتسميتها.  
2. استخدام `MarkdownSaveOptions` لربط رد النداء بعملية الحفظ.  
3. التحقق من مجلد الإخراج لضمان استخراج جميع الأصول.

من هنا يمكنك التفرّع—ربما إنشاء مدونة موقع ثابت، تغذية markdown إلى مولّد وثائق، أو دمج التحويل في خط أنابيب CI. إذا كنت بحاجة إلى **convert docx to markdown** بسرعة لعدة ملفات، فقط ضع الكود داخل حلقة وستكون جاهزًا.

هل لديك المزيد من الأسئلة حول Aspose.Words، التعامل مع الجداول، أو تخصيص صياغة markdown؟ اترك تعليقًا، ونتمنى لك برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}