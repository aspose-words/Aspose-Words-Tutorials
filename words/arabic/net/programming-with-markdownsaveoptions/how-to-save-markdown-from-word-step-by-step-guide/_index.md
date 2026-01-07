---
category: general
date: 2026-01-06
description: كيفية حفظ markdown من ملف DOCX بسرعة. تعلم تحويل docx إلى markdown، حفظ
  صور Word واستخراج الصور باستخدام Aspose.Words.
draft: false
keywords:
- how to save markdown
- convert docx to markdown
- how to convert docx
- save word images
- how to extract images
language: ar
og_description: كيفية حفظ ماركداون من ملف DOCX باستخدام Aspose.Words. يتضمن تحويل
  DOCX إلى ماركداون، حفظ صور Word واستخراج الصور.
og_title: كيفية حفظ Markdown – دليل التحويل الكامل إلى C#
tags:
- Aspose.Words
- C#
- Markdown conversion
title: كيفية حفظ ماركداون من وورد – دليل خطوة بخطوة
url: /ar/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-word-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية حفظ Markdown – دليل التحويل الكامل بلغة C#

هل تساءلت يومًا **كيفية حفظ markdown** من مستند Word دون فقدان أي صورة؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحتاجون إلى تحويل ملف `.docx` إلى Markdown نظيف مع الحفاظ على كل صورة.

في هذا الدرس ستتعلم **كيفية حفظ markdown**، **تحويل docx إلى markdown**، وحتى **حفظ صور Word** تلقائيًا. في النهاية ستحصل على مقتطف C# جاهز للتنفيذ يقتطف الصور، يطلق عليها أسماء منطقية، ويضع ملف الـ Markdown في المكان الذي تريد.

> **نصيحة احترافية:** النهج الموضح يعمل مع Aspose.Words 23.10 (أو أي نسخة أحدث)، لذا أنت محمي للمستقبل.

![مخطط يوضح كيفية حفظ markdown من ملف DOCX](/images/how-to-save-markdown-diagram.png "كيفية حفظ markdown – مخطط تدفق")

## ما ستحتاجه

- **Aspose.Words for .NET** (حزمة NuGet `Aspose.Words`).  
- .NET 6+ (المثال يُجمع مع .NET 6 أو .NET 7 أو .NET 8).  
- ملف Word بسيط (`input.docx`) يحتوي على نص وعلى الأقل صورة واحدة.  
- بيئة تطوير أو محرر من اختيارك (Visual Studio، VS Code، Rider…).

لا تحتاج إلى مكتبات صور طرف ثالث إضافية — واجهة `IResourceSavingCallback` تقوم بكل العمل الشاق.

## الخطوة 1: تحميل المستند المصدر (كيفية تحويل DOCX)

الخطوة الأولى هي فتح ملف Word الذي تريد تحويله إلى Markdown. هذه هي جزء **كيفية تحويل docx** من العملية.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the source DOCX
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*لماذا هذا مهم:*  
`Document` هو تمثيل Aspose.Words لملف Word. تحميله مرة واحدة يمنحك الوصول إلى كل النصوص، الأنماط، والموارد المدمجة (بما في ذلك الصور).

## الخطوة 2: إعداد خيارات حفظ Markdown مع رد نداء حفظ الموارد

عند طلب حفظ Aspose.Words كـ Markdown، سيحاول كتابة كل مورد خارجي (مثل الصور) إلى القرص. من خلال توفير **رد نداء حفظ الموارد**، تتحكم تمامًا في مكان وضع هذه الملفات وكيفية تسميتها — وهذا هو جوهر **حفظ صور Word**.

```csharp
// Configure Markdown options and attach the callback
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    // The callback will be invoked for each image or other external resource
    ResourceSavingCallback = new ImageSavingCallback()
};
```

*لماذا نستخدم رد نداء؟*  
بدون ذلك، سيقوم Aspose بإسقاط الصور في نفس المجلد مع ملف `.md`، باستخدام أسماء عامة. يسمح لك رد النداء بإنشاء مجلد مخصص (`md_resources`) وإعطاء كل صورة اسمًا فريدًا ومتوقعًا (`img_0.png`, `img_1.jpg`, …). هذا يجعل **كيفية استخراج الصور** من التحويل أمرًا بسيطًا لاحقًا.

## الخطوة 3: حفظ المستند كـ Markdown

الآن بعد أن أصبحت الخيارات جاهزة، التحويل الفعلي هو سطر واحد. هنا حيث يحدث **كيفية حفظ markdown** أخيرًا.

```csharp
// Save the document as Markdown, automatically invoking the callback for each image
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

تشغيل الكود ينتج شيئين:

1. `output.md` – ملف Markdown نظيف يحتوي على روابط صور تشير إلى المجلد الذي حددته.  
2. `md_resources/` – مجلد فرعي يحتوي على كل صورة مستخرجة، مسماة وفقًا للمنطق في رد النداء.

## الخطوة 4: تنفيذ رد نداء حفظ الصورة (حفظ صور Word)

فيما يلي التنفيذ الكامل لفئة رد النداء. تقوم بإنشاء مجلد الموارد إذا لم يكن موجودًا، تبني اسم ملف فريد، وتخبر Aspose أين يكتب الملف.

```csharp
/// <summary>
/// Callback that stores each image in a custom folder and gives it a unique name.
/// </summary>
public class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Define the folder where images will be saved
        string resourcesFolder = "YOUR_DIRECTORY/md_resources";
        Directory.CreateDirectory(resourcesFolder);

        // Build a unique file name: img_0.png, img_1.jpg, …
        string imageFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";

        // Set the final path for the image
        args.FileName = Path.Combine(resourcesFolder, imageFileName);

        // If you ever need to skip a particular resource, set args.Cancel = true;
    }
}
```

*نقاط رئيسية يجب تذكرها:*

- `args.Index` يبدأ من الصفر ويضمن التفرد حتى عندما تشترك عدة صور في نفس الاسم الأصلي.  
- `Path.GetExtension(args.FileName)` يحافظ على تنسيق الصورة الأصلي (PNG، JPEG، GIF، إلخ).  
- ضبط `args.Cancel = true` سيتخطى حفظ ذلك المورد — مفيد إذا كنت تريد النص فقط.

## مثال عملي كامل (جميع الأجزاء معًا)

انسخ‑الصق ما يلي في مشروع وحدة تحكم جديد (`dotnet new console`) واستبدل `YOUR_DIRECTORY` بمسار مطلق أو نسبي موجود على جهازك.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source DOCX
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Configure Markdown options + callback
            MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // 3️⃣ Save as Markdown (this triggers the callback for each image)
            document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);

            System.Console.WriteLine("Conversion complete! Check output.md and the md_resources folder.");
        }
    }

    // 4️⃣ Callback implementation (see previous section for details)
    public class ImageSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourcesFolder = "YOUR_DIRECTORY/md_resources";
            Directory.CreateDirectory(resourcesFolder);
            string imageFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
            args.FileName = Path.Combine(resourcesFolder, imageFileName);
        }
    }
}
```

### النتيجة المتوقعة

- **`output.md`** سيحتوي على Markdown مثل:

```markdown
# My Document Title

Here is some introductory text.

![Image 0](md_resources/img_0.png)

More text follows…

![Image 1](md_resources/img_1.jpg)
```

- مجلد **`md_resources`** سيحمل `img_0.png`, `img_1.jpg`, إلخ، مطابقة تمامًا للروابط في ملف الـ Markdown.

## أسئلة شائعة وحالات خاصة

### 1. ماذا لو كان الـ DOCX يحتوي على صور SVG أو WMF؟
يقوم Aspose.Words بتحويل معظم صيغ المتجهات إلى PNG بشكل افتراضي. سيستمر رد النداء في استقبال امتداد `.png`، لذا لا تحتاج إلى معالجة إضافية — فقط كن على علم بأن حجم الناتج قد يكون أكبر.

### 2. هل يمكنني تغيير نمط تسمية الصور؟
بالطبع. استبدل السطر الذي يبني `imageFileName` بأي نمط تفضله (مثل استخدام الاسم الأصلي، GUID، أو عنوان مُصغّر). فقط تأكد من أن `args.FileName` يشير إلى المسار النهائي.

### 3. كيف أتخطى حفظ صورة معينة؟
داخل `ResourceSaving`، افحص `args.FileName` أو `args.Index`. إذا تطابقت شرط معين، اضبط `args.Cancel = true;`. سيظل رابط الـ Markdown مُولدًا، لكن ملف الصورة لن يُكتب — مفيد للرسومات الكبيرة غير المرغوبة.

### 4. هل يعمل هذا على Linux/macOS؟
نعم. يستخدم الكود فقط واجهات برمجة تطبيقات .NET‑standard (`System.IO`) وAspose.Words، وهو متعدد المنصات. فقط تأكد من أن الأدلة المستهدفة لديها أذونات كتابة مناسبة.

## نصائح للاستخدام في الإنتاج

- **معالجة دفعات:** غلف منطق التحويل في حلقة تتكرر على مجلد من ملفات `.docx`.  
- **معالجة الأخطاء:** التقط `Aspose.Words.Fonts.FontSettingsException` إذا كان المصدر يستخدم خطوطًا مفقودة، وسجِّل المشكلة.  
- **الأداء:** أعد استخدام كائن `MarkdownSaveOptions` واحد عند تحويل العديد من المستندات لتقليل استهلاك الذاكرة.  
- **الأمان:** تحقق من صحة مسار الإدخال لتجنب هجمات استغلال مسار الدليل إذا كان اسم الملف يأتي من مدخلات المستخدم.

## الخلاصة

لقد تعلمت الآن **كيفية حفظ markdown** من مستند Word، **تحويل docx إلى markdown**، و**حفظ صور Word** تلقائيًا باستخدام Aspose.Words. نمط رد النداء يمنحك تحكمًا كاملاً في استخراج الصور، تسميتها، وتخزينها — يغطي كل جانب من **كيفية استخراج الصور** أثناء التحويل.

لا تتردد في التجربة: غيّر مجلد الإخراج، عدّل نمط تسمية الصور، أو دمج هذا في خط أنابيب معالجة مستندات أكبر. الأساسيات كلها هنا، والآن لديك مرجع قوي يمكنك مشاركته مع زملائك أو مع المساعدين الذكائيين.

**الخطوات التالية:**  
- استكشف `SaveOptions` أخرى مثل `HtmlSaveOptions` إذا كنت تحتاج إلى HTML بجانب Markdown.  
- دمج هذا مع خطوة توليد PDF لإنتاج تقرير متعدد الصيغ.  
- تعمق في ميزات Aspose.Words المتقدمة مثل معالجة الحقول المخصصة أو عناصر التحكم بالمحتوى.

برمجة سعيدة، واستمتع بتحويل ملفات Word العنيدة إلى Markdown نظيف ومحمول!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}