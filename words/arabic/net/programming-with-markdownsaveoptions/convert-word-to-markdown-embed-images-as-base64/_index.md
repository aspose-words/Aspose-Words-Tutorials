---
category: general
date: 2026-01-03
description: حوّل مستند Word إلى Markdown وادمج الصور كـ base64 في خطوة واحدة. تعلّم
  كيفية حفظ Word كـ markdown، إنشاء markdown من Word، واستخدام URI لبيانات الصورة
  بصيغة base64.
draft: false
keywords:
- convert word to markdown
- embed images as base64
- save word as markdown
- base64 image data uri
- generate markdown from word
language: ar
og_description: تحويل Word إلى Markdown وتضمين الصور كـ URIs للبيانات بصيغة base64.
  يوضح هذا الدليل خطوة بخطوة كيفية حفظ Word كـ markdown وإنشاء markdown من Word.
og_title: تحويل Word إلى Markdown – دليل تضمين الصور بصيغة Base64
tags:
- Aspose.Words
- C#
- Markdown
title: تحويل Word إلى Markdown – تضمين الصور كـ Base64
url: /ar/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحويل Word إلى Markdown – تضمين الصور كـ Base64

هل احتجت يوماً إلى **تحويل Word إلى markdown** لكنك واجهت مشكلة الصور؟ لست وحدك. Word يُفضّل تخزين الصور كملفات منفصلة، بينما يفضّل markdown سلاسل `data:image/...;base64,` التي تُبقي كل شيء في ملف واحد.  

في هذا الدرس سنستعرض حلًا كاملاً جاهزًا للتنفيذ **يحفظ Word كـ markdown**، **يضمّن الصور كـ base64**، وحتى يوضح لك كيفية **إنشاء markdown من Word** باستخدام Aspose.Words for .NET. في النهاية ستحصل على ملف `.md` واحد يُظهر المحتوى تمامًا كما في المستند الأصلي—دون الحاجة إلى مجلدات صور خارجية.

## ما ستحتاجه

- **.NET 6.0 أو أحدث** (أي شيء يمكنه الإشارة إلى حزمة NuGet)
- **Aspose.Words for .NET** (الإصدار التجريبي المجاني يكفي للاختبار)
- ملف `.docx` بسيط يحتوي على بعض الصور (سنسميه `input.docx`)
- بيئة التطوير المفضلة لديك (Visual Studio، Rider، VS Code—اختر ما يناسبك)

إذا كان لديك كل ذلك، رائع—لنبدأ. إذا لم يكن، فإن تثبيت حزمة NuGet يتم بسطر واحد:

```bash
dotnet add package Aspose.Words
```

## الخطوة 1: تحميل مستند Word — نقطة الانطلاق لـ **convert word to markdown**

أولاً نحتاج إلى جلب ملف `.docx` إلى الذاكرة. هنا يبدأ سحر التحويل.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file that contains the images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **لماذا هذا مهم:**  
> تحميل المستند يمنح Aspose وصولًا كاملًا إلى النص، الأنماط، وكل الموارد المضمّنة. بدون هذه الخطوة لا شيء يمكن تحويله.

## الخطوة 2: إعداد MarkdownSaveOptions مع رد نداء حفظ الموارد (Resource‑Saving Callback)

يتيح لك Aspose اعتراض كل مورد (مثل الصور) كان سيُكتب عادةً إلى القرص. من خلال توفير `IResourceSavingCallback` مخصص، يمكننا استبدال الحفظ الافتراضي إلى ملف بـ **uri صورة base64**.

```csharp
// Configure Markdown save options so that images become Base64 URIs.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceHandler()
};
```

### المعالج المخصص – تحويل الصور إلى Base64

فيما يلي التنفيذ الكامل. لاحظ كيف نتحقق من `args.ResourceType == ResourceType.Image` ثم:

1. نكتب الصورة إلى `MemoryStream`.
2. نحول مصفوفة البايتات إلى سلسلة Base64.
3. نبني URI من الشكل `data:image/jpeg;base64,` ونعيّنها إلى `args.Uri`.

```csharp
// Custom handler that converts each image resource to a Base64 data URI.
class MyResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only process images – leave other resources untouched.
        if (args.ResourceType == ResourceType.Image)
        {
            // Prepare an in‑memory stream for the image.
            using (MemoryStream ms = new MemoryStream())
            {
                // Save the image using default JPEG options.
                args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                // Build the Base64 data URI.
                string base64 = Convert.ToBase64String(ms.ToArray());
                args.Uri = $"data:image/jpeg;base64,{base64}";
                // No need to keep the stream open after we set the URI.
                args.KeepResourceStreamOpen = false;
            }
        }
    }
}
```

> **نصيحة احترافية:** إذا كان مستند Word الأصلي يستخدم PNGs، استبدل `ImageSaveOptions.DefaultJpeg` بـ `ImageSaveOptions.DefaultPng` وغير نوع MIME وفقًا لذلك (`image/png`).

## الخطوة 3: حفظ المستند كـ Markdown – الخطوة النهائية لـ **save word as markdown**

الآن بعد أن أصبح رد النداء جاهزًا، عملية الحفظ نفسها سطر واحد فقط.

```csharp
// Save the document to a Markdown file. Images are already embedded.
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

عند فتح `output.md` في أي عارض markdown (معاينة VS Code، GitHub، إلخ)، سترى النص تمامًا كما في ملف Word الأصلي، وستظهر الصور مدمجة داخل النص دون ملفات صور منفصلة.

## النتيجة المتوقعة

```markdown
# Sample Title

Here’s a paragraph that originally lived in Word.

![Embedded Image](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhU...
```

سطر `![Embedded Image]` هو **uri صورة base64**—الصورة كاملة مُشفّرة هناك. لا مجلدات إضافية، لا روابط مكسورة.

## الحالات الخاصة وكيفية التعامل معها

| الحالة | ما الذي يجب فعله |
|-----------|------------|
| **صور كبيرة** – Base64 يزيد الحجم بحوالي 33% | فكر في تصغير الحجم قبل التحويل: `args.ResourceData.Save(ms, new ImageSaveOptions { ImageResolution = 72 })`. |
| **صور غير JPEG** (PNG, GIF) | اكتشف الصيغة الأصلية عبر `args.ResourceData.ImageType` واضبط نوع MIME المناسب (`image/png`, `image/gif`). |
| **مستندات طويلة جدًا** (مئات الصور) | راقب استهلاك الذاكرة؛ يمكنك تدفق كل صورة إلى قرص مؤقتًا إذا نفدت الذاكرة. |
| **الحاجة إلى ملفات صور منفصلة** (مثلاً لموقع ثابت) | أرجع `false` من رد النداء للصور التي تريد الاحتفاظ بها كملفات، ودع Aspose يكتبها إلى مج. |

## أسئلة شائعة (مجاوبة مسبقًا)

- **هل يعمل هذا مع ملفات .doc؟** نعم—Aspose.Words يمكنه تحميل ملفات `.doc` القديمة بنفس الطريقة التي يحمل بها `.docx`. فقط استخدم `new Document("myfile.doc")`.
- **ماذا عن الجداول والحواشي؟** كلها مدعومة بالكامل من قبل مُصدّر Markdown. الجداول تتحول إلى جداول markdown؛ الحواشي تصبح إشارات داخلية.
- **هل يمكنني تغيير نكهة markdown؟** يحتوي `MarkdownSaveOptions` على خاصية `MarkdownVersion` (CommonMark, GitHub, إلخ). اضبطها قبل الحفظ إذا كنت تحتاج صياغة معينة.

## مثال كامل وجاهز للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑لصقه في تطبيق Console. يتضمن جميع عبارات `using`، وفئة المعالج، ومعالجة الأخطاء.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                // 1️⃣ Load the source Word document.
                Document doc = new Document("YOUR_DIRECTORY/input.docx");

                // 2️⃣ Prepare Markdown options with our custom image handler.
                MarkdownSaveOptions options = new MarkdownSaveOptions
                {
                    ResourceSavingCallback = new MyResourceHandler()
                };

                // 3️⃣ Save as Markdown – images become Base64 URIs.
                string outputPath = "YOUR_DIRECTORY/output.md";
                doc.Save(outputPath, options);

                Console.WriteLine($"✅ Success! Markdown saved to {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Conversion failed: {ex.Message}");
            }
        }
    }

    // Custom callback that embeds images as Base64 data URIs.
    class MyResourceHandler : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType == ResourceType.Image)
            {
                using (MemoryStream ms = new MemoryStream())
                {
                    // Preserve original format if you prefer PNG/GIF.
                    args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                    string base64 = Convert.ToBase64String(ms.ToArray());
                    args.Uri = $"data:image/jpeg;base64,{base64}";
                    args.KeepResourceStreamOpen = false;
                }
            }
        }
    }
}
```

شغّل البرنامج، افتح الملف `output.md` المُولَّد، وسترى نسخة markdown مطابقة تمامًا لملف Word الخاص بك—**convert word to markdown** لم يكن أبداً أسهل.

## ملخص

بدأنا بمشكلة **convert word to markdown** مع الحفاظ على الصور مدمجة. عبر تحميل المستند، تكوين رد نداء `MarkdownSaveOptions`، ثم حفظ الملف، حصلنا على حل نظيف لـ **save word as markdown** ينتج سلاسل **base64 image data uri**. الآن تعرف أيضًا كيف **تضمّن الصور كـ base64**، وتتعامل مع الحالات الخاصة، وتضبط العملية لأنواع صور مختلفة.

## ما التالي؟

- **إنشاء HTML بدلاً من markdown** – استبدل `MarkdownSaveOptions` بـ `HtmlSaveOptions` وأعد استخدام نفس رد النداء.
- **تحويل دفعة من الملفات** – ضع المنطق داخل حلقة `foreach` على مجلد.
- **دمج العملية في خط أنابيب CI** – أتمتة توليد الوثائق للمواقع الثابتة.

لا تتردد في التجربة، تعديل جودة الصورة، أو حتى إضافة معالجة موارد مخصصة (مثلاً رفع الصور إلى CDN وإدراج الرابط). السماء هي الحد عندما تجمع بين Aspose.Words وقليل من إبداع C#.

Happy coding, and may your markdown always render perfectly! 

![Diagram showing convert word to markdown flow – embed images as base64](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHJlY3Qgd2lkdGg9IjYwMCIgaGVpZ2h0PSI0MDAiIGZpbGw9IiNmZmYiIHN0cm9rZT0iI2NjYyIgLz48dGV4dCB4PSI1MCIgeT0iMjAwIiBmb250LXNpemU9IjM2IiBmaWxsPSIjMDAwIj5JbWFnZSBJbWFnZSBJbWFnZSBJbWFnZTwvdGV4dD48L3N2Zz4= "convert word to markdown flow diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}