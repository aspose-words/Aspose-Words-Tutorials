---
category: general
date: 2025-12-19
description: تعلم كيفية تحويل DOCX إلى Markdown باستخدام C#. يوضح هذا الدليل خطوة
  بخطوة أيضًا كيفية تصدير Word إلى Markdown، واستخراج الصور من DOCX، وتعيين دقة الصورة،
  والإجابة على كيفية استخراج الصور بكفاءة.
draft: false
keywords:
- convert docx to markdown
- export word to markdown
- extract images from docx
- set image resolution
- how to extract images
language: ar
og_description: تحويل DOCX إلى Markdown باستخدام Aspose.Words في C#. اتبع هذا الدليل
  لتصدير Word إلى Markdown، واستخراج الصور، وتعيين دقة الصورة، وإتقان كيفية استخراج
  الصور.
og_title: تحويل DOCX إلى Markdown – دليل C# الكامل
tags:
- Aspose.Words
- C#
- Markdown
- Document Conversion
title: تحويل DOCX إلى Markdown – دليل C# الكامل لتصدير Word إلى Markdown
url: /ar/net/working-with-markdown/convert-docx-to-markdown-complete-c-guide-for-exporting-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحويل DOCX إلى Markdown – دليل C# كامل

هل احتجت يوماً إلى **تحويل DOCX إلى Markdown** لكن لم تعرف من أين تبدأ؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحاولون نقل محتوى Word الغني إلى Markdown خفيف الوزن للمواقع الثابتة، أو خطوط أنابيب التوثيق، أو الملاحظات التي تُدار بالإصدار. الخبر السار؟ باستخدام Aspose.Words for .NET يمكنك القيام بذلك في بضع أسطر، وستتعلم أيضاً كيفية **تصدير Word إلى Markdown**، **استخراج الصور من DOCX**، و**ضبط دقة الصورة** لتلك الرسومات.

> **نصيحة احترافية:** إذا كنت تعمل مع ملفات Word كبيرة، فعليك دائماً تمكين وضع الاستعادة – فهو يحميك من الأعطال الغامضة لاحقاً.

---

## ما الذي ستحتاجه

- **Aspose.Words for .NET** (أي إصدار حديث، مثل 24.10).  
- .NET 6 أو أحدث (الكود يعمل أيضاً على .NET Framework).  
- هيكل مجلد مثل `YOUR_DIRECTORY/input.docx` ومكان لتخزين الصور (`MyImages`).  
- معرفة أساسية بـ C# – لا تحتاج إلى حيل متقدمة.

---

## الخطوة 1: تحميل DOCX بأمان – الجزء الأول في تحويل DOCX إلى Markdown

عند تحميل ملف Word قد يكون تالفاً، لا تريد أن يتعطل العملية بأكملها. توفر لك فئة `LoadOptions` إعداد **RecoveryMode** الذي يمكنه إما طلب تأكيد من المستخدم، الفشل بصمت، أو الاستمرار تلقائياً.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Step 1: Load the DOCX file using recovery mode to handle possible corruption
LoadOptions loadOptions = new LoadOptions
{
    // Prompt the user for recovery actions (alternatives: Silent, Fail)
    RecoveryMode = RecoveryMode.Prompt
};

Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**لماذا هذا مهم:**  
- **RecoveryMode.Prompt** يطلب من المستخدم ما إذا كان يرغب في المتابعة إذا كان الملف تالفاً، مما يمنع فقدان البيانات بصمت.  
- إذا كنت تفضّل خط أنابيب آلي، غيّر إلى `RecoveryMode.Silent`.  

---

## الخطوة 2: تكوين تصدير Markdown – تصدير Word إلى Markdown مع التحكم في الصور

الآن بعد أن أصبح المستند في الذاكرة، نحتاج إلى إخبار Aspose كيف نريد أن يبدو ملف Markdown. هنا تقوم **بتعيين دقة الصورة**، وتحديد طريقة التعامل مع OfficeMath (المعادلات)، وربط رد نداء لاستخراج **الصور من DOCX** فعلياً.

```csharp
// Step 2: Prepare Markdown export options with custom image handling
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // High‑resolution images keep your diagrams crisp
    ImageResolution = 300,

    // Export equations as LaTeX – perfect for static site generators
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // This callback runs for every image the exporter extracts
    ResourceSavingCallback = resourceInfo =>
    {
        // Build the full path where the image will be saved
        string imagePath = Path.Combine("YOUR_DIRECTORY/MyImages", resourceInfo.FileName);
        File.WriteAllBytes(imagePath, resourceInfo.Data);

        // Return the Markdown image reference that will be inserted into the file
        // The alt‑text comes from the original Word image description
        return $"![{resourceInfo.AltText}]({imagePath})";
    }
};
```

**نقاط رئيسية يجب تذكرها:**

- **ImageResolution = 300** يعني أن كل صورة مستخرجة ستحفظ بدقة 300 dpi، وهو عادةً كافٍ للوثائق ذات جودة الطباعة دون زيادة حجم الملف بشكل كبير.  
- **OfficeMathExportMode.LaTeX** يحول معادلات Word إلى صيغة LaTeX، وهي صيغة يفهمها العديد من مولّدات المواقع الثابتة.  
- **ResourceSavingCallback** هو جوهر **كيفية استخراج الصور** – أنت تقرّر المجلد، التسمية، وحتى صيغة Markdown التي تشير إلى الصورة.

---

## الخطوة 3: حفظ ملف Markdown – الخطوة النهائية في تحويل DOCX إلى Markdown

مع كل الإعدادات جاهزة، السطر الأخير يكتب ملف Markdown إلى القرص. يقوم المصدّر تلقائياً باستدعاء رد النداء لكل صورة، لذا ستحصل على مجلد نظيف من الصور وملف `.md` جاهز للنشر.

```csharp
// Step 3: Export the document to Markdown using the configured options
document.Save("YOUR_DIRECTORY/output.md", markdownOptions);
```

بعد تشغيل هذا، ستلاحظ ما يلي:

- `output.md` يحتوي على النص، العناوين، وإشارات الصور.  
- مجلد `MyImages` مملوء بملفات PNG/JPEG (أو أي صيغة استخدمها Word الأصلي).  

---

## كيفية استخراج الصور من DOCX – نظرة أعمق

إذا كان هدفك الوحيد هو سحب الصور من ملف Word — ربما لإنشاء معرض أو خط أنابيب أصول — يمكنك تخطي جزء Markdown واستخدام نمط رد النداء نفسه:

```csharp
// Example: Extract images without generating Markdown
document.Save("dummy.md", new MarkdownSaveOptions
{
    ImageResolution = 150, // lower DPI if you just need thumbnails
    ResourceSavingCallback = info =>
    {
        string path = Path.Combine("YOUR_DIRECTORY/OnlyImages", info.FileName);
        File.WriteAllBytes(path, info.Data);
        // Returning null tells the exporter to ignore inserting a reference
        return null;
    }
});
```

**لماذا نعيد `null`؟**  
إرجاع `null` يخبر Aspose بعدم تضمين أي رابط Markdown، وبالتالي ستحصل على مجلد صور فقط. هذه طريقة سريعة للإجابة على **كيفية استخراج الصور** دون إغراق Markdown الخاص بك.

---

## ضبط دقة الصورة — التحكم في الجودة والحجم

أحياناً تحتاج إلى رسومات عالية الدقة للطباعة، وأحياناً أخرى تحتاج إلى صور مصغرة منخفضة الدقة للويب. خاصية `ImageResolution` في `MarkdownSaveOptions` (أو أي `ImageSaveOptions`) تسمح لك بضبط ذلك بدقة.

| الاستخدام المطلوب | DPI الموصى به |
|-------------------|---------------|
| صور مصغرة للويب | 72‑150 |
| لقطات شاشة للتوثيق | 150‑200 |
| مخططات جاهزة للطباعة | 300‑600 |

تغيير الـ DPI بسيط كضبط القيمة الرقمية:

```csharp
markdownOptions.ImageResolution = 600; // Ultra‑crisp for PDF generation later
```

تذكر: كلما ارتفعت DPI → كلما زاد حجم الملف. احرص على الموازنة وفقاً للمنصة المستهدفة.

---

## الأخطاء الشائعة وكيفية تجنّبها

- **عدم وجود مجلد `MyImages`** – سيطرح Aspose استثناءً إذا لم يكن الدليل موجوداً. أنشئه مسبقاً أو دع رد النداء يتحقق من `Directory.Exists` ويستدعي `Directory.CreateDirectory`.  
- **DOCX تالف** – حتى مع `RecoveryMode.Prompt`، قد تكون بعض الملفات غير قابلة للإصلاح. في خطوط أنابيب CI الآلية، غيّر إلى `RecoveryMode.Silent` وسجّل التحذيرات.  
- **حروف غير لاتينية في أسماء الصور** – يستخدم رد النداء `resourceInfo.FileName` الذي قد يحتوي على مسافات أو Unicode. غلف اسم الملف بـ `Uri.EscapeDataString` عند بناء رابط Markdown لتجنب عناوين URL مكسورة.  

```csharp
string safeName = Uri.EscapeDataString(resourceInfo.FileName);
return $"![{resourceInfo.AltText}]({safeName})";
```

---

## مثال كامل يعمل – الصق وشغّله

فيما يلي البرنامج الكامل الذي يمكنك وضعه في تطبيق Console. يتضمن جميع فحوصات الأمان التي نوقشت أعلاه.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        const string baseDir = @"YOUR_DIRECTORY";
        const string inputPath = Path.Combine(baseDir, "input.docx");
        const string outputPath = Path.Combine(baseDir, "output.md");
        const string imagesFolder = Path.Combine(baseDir, "MyImages");

        // Ensure the images folder exists
        if (!Directory.Exists(imagesFolder))
            Directory.CreateDirectory(imagesFolder);

        // 1️⃣ Load the DOCX with recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Prompt
        };
        Document doc = new Document(inputPath, loadOptions);

        // 2️⃣ Configure Markdown export (export word to markdown)
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ImageResolution = 300,
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            ResourceSavingCallback = info =>
            {
                // Build a safe file name for the image
                string safeFileName = Uri.EscapeDataString(info.FileName);
                string imagePath = Path.Combine(imagesFolder, safeFileName);
                File.WriteAllBytes(imagePath, info.Data);
                // Return the markdown image tag
                return $"![{info.AltText}]({imagePath})";
            }
        };

        // 3️⃣ Save as Markdown (convert docx to markdown)
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown file: {outputPath}");
        Console.WriteLine($"Extracted images folder: {imagesFolder}");
    }
}
```

**الناتج المتوقع:**  
عند تشغيل البرنامج سيطبع رسالة نجاح وينشئ `output.md`. عند فتح ملف Markdown سترى العناوين، النقاط، وروابط الصور مثل `![Chart](YOUR_DIRECTORY/MyImages/image1.png)`.

---

## الخلاصة

أصبح لديك الآن حل كامل وجاهز للإنتاج **لتحويل DOCX إلى Markdown** باستخدام C#. غطّى الدليل كيفية **تصدير Word إلى Markdown**، **استخراج الصور من DOCX**، و**ضبط دقة الصورة** لتلك الرسومات. من خلال الاستفادة من `LoadOptions` و `MarkdownSaveOptions`، يمكنك التعامل مع الملفات التالفة، التحكم في جودة الصور، وتحديد بالضبط كيف تظهر كل صورة في Markdown النهائي.

ما الخطوة التالية؟ جرّب استبدال `MarkdownSaveOptions` بـ `HtmlSaveOptions` إذا كنت تحتاج إلى HTML بدلاً من ذلك، أو مرّر Markdown إلى مولّد موقع ثابت مثل Hugo أو Jekyll. يمكنك أيضاً تجربة `ResourceLoadingCallback` لتضمين الصور كسلاسل Base64 لإنتاج ملف واحد.

لا تتردد في تعديل DPI، تغيير بنية مجلد الصور، أو إضافة قواعد تسمية مخصصة. مرونة Aspose.Words تتيح لك تكييف هذا النمط مع أي سير عمل لأتمتة المستندات تقريباً.

برمجة سعيدة، ولتظل توثيقاتك خفيفة الوزن وجميلة دائماً! 

---

> **صورة توضيحية**  
> ![تحويل docx إلى markdown workflow](/images/convert-docx-to-markdown-workflow.png)

*النص البديل:* *مخطط تحويل docx إلى markdown* يوضح خطوات التحميل، التكوين، والحفظ.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}