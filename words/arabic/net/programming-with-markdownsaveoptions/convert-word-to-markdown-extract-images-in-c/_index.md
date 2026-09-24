---
category: general
date: 2026-02-18
description: تحويل ملفات Word إلى Markdown واستخراج الصور من ملفات docx باستخدام Aspose.Words.
  تعلم كيفية إنشاء Markdown من Word مع مثال كامل بلغة C#.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- generate markdown from word
- how to convert docx to markdown
language: ar
og_description: تحويل Word إلى Markdown واستخراج الصور من ملفات docx باستخدام Aspose.Words.
  يوضح هذا الدليل كيفية إنشاء markdown من Word خطوة بخطوة.
og_title: تحويل Word إلى Markdown – استخراج الصور في C#
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: تحويل Word إلى Markdown – استخراج الصور في C#
url: /ar/net/programming-with-markdownsaveoptions/convert-word-to-markdown-extract-images-in-c/
---

turning into a Markdown file with images." Should be Arabic.

Also list items.

Let's craft.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحويل Word إلى Markdown – استخراج الصور في C#

هل تساءلت يومًا كيف **تحول Word إلى Markdown** مع استخراج كل صورة من ملف `.docx`؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحتاجون إلى نسخة نظيفة من Markdown لعقد، أو مشاركة مدونة، أو مواصفة تقنية تم إنشاؤها أصلاً في Word. الخبر السار؟ باستخدام Aspose.Words for .NET يمكنك القيام بذلك ببضع أسطر من الشيفرة، وستحصل على ملف markdown *بالإضافة إلى* مجلد يحتوي على الصور الأصلية.

في هذا الدرس سنستعرض برنامج C# كامل جاهز للتنفيذ **ينتج markdown من Word**، يستخرج الصور من docx، ويحفظ كل شيء على القرص. بنهاية الدرس ستعرف بالضبط كيف **تحول docx إلى markdown**، وكيف **استخراج الصور من docx**، وكيفية تعديل العملية لمشاريعك الخاصة.

## ما ستحتاجه

- **Aspose.Words for .NET** (الإصدار 23.10 أو أحدث). يمكنك الحصول على نسخة تجريبية مجانية عبر حزمة NuGet باستخدام `Install-Package Aspose.Words`.
- .NET 6+ SDK (أي نسخة حديثة تعمل بشكل جيد).
- ملف `input.docx` تجريبي يحتوي على صورة واحدة على الأقل.
- مجلد تريد أن تُخزن فيه ملفات markdown وملفات الصور.

لا توجد مكتبات طرف ثالث أخرى مطلوبة. الشيفرة أدناه تشمل جميع توجيهات `using` التي تحتاجها، لذا يمكنك نسخها ولصقها في تطبيق Console والضغط على **F5**.

![Convert Word to Markdown example](/images/convert-word-to-markdown.png "convert word to markdown")

*نص بديل للصورة: توضيح تحويل Word إلى Markdown يُظهر ملف Word يتحول إلى ملف Markdown مع الصور.*

---

## الخطوة 1: تحميل مستند Word المصدر

الخطوة الأولى هي توجيه Aspose.Words إلى الملف الذي تريد تحويله. فكر في `Document` كبوابة لكل ما يحتويه ملف `.docx` — النص، الجداول، الصور، أي شيء.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 👉 Step 1: Load the Word document that contains images.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document document = new Document(inputPath);
```

> **لماذا هذا مهم:** تحميل المستند مرة واحدة يقلل من استهلاك الذاكرة ويسمح للمكتبة بفحص بنية الحزمة الداخلية، وهو أمر أساسي لاستخراج الصور لاحقًا.

---

## الخطوة 2: إخبار Aspose.Words كيف يحفظ كـ Markdown

تأتي Aspose.Words مع فئة `MarkdownSaveOptions`. تتيح لك التحكم في كل شيء من نهايات الأسطر إلى المجلد الذي تُحفظ فيه الموارد الخارجية (مثل الصور).

```csharp
        // 👉 Step 2: Configure Markdown save options with a resource‑saving callback.
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
        {
            // The callback fires for each external resource (e.g., an image) that needs a file.
            ResourceSavingCallback = new ResourceSavingCallback(args =>
            {
                // 👉 Step 3 inside the callback: decide where and how to store each image.
                string resourceFolder = @"YOUR_DIRECTORY\markdown-resources";
                Directory.CreateDirectory(resourceFolder); // creates if it doesn’t exist

                // Give each image a unique name to avoid collisions.
                string uniqueFileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
                args.FileName = Path.Combine(resourceFolder, uniqueFileName);

                // Optional: you could compress PNGs here by manipulating args.Stream.
            })
        };
```

> **لماذا نحتاج إلى رد نداء (callback)؟** `ResourceSavingCallback` يمنحك السيطرة الكاملة على اسم الملف وموقع كل صورة مستخرجة. بدون ذلك، سيقوم Aspose بإلقاء كل شيء في نفس المجلد بأسماء عامة، مما قد يسبب فوضى في المشاريع الكبيرة.

---

## الخطوة 3: حفظ المستند كـ Markdown

بعد ضبط الخيارات، يصبح الحفظ سطرًا واحدًا. تقوم المكتبة بالعمل الشاق: تحويل الفقرات، العناوين، القوائم، الجداول، وبفضل رد النداء—تكتب كل صورة إلى المجلد الذي حددته.

```csharp
        // 👉 Step 4: Save the document as a Markdown file.
        string outputPath = @"YOUR_DIRECTORY\output.md";
        document.Save(outputPath, markdownOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputPath}");
        Console.WriteLine($"Images extracted to: {Path.GetDirectoryName(outputPath)}\\markdown-resources");
    }
}
```

### النتيجة المتوقعة

- يحتوي `output.md` على صيغة markdown (مثال: `![Image](markdown-resources/img_1234.png)`).
- مجلد `markdown-resources` يحتوي على كل صورة من ملف Word الأصلي، كل واحدة باسم فريد.

افتح `output.md` في أي عارض markdown (VS Code، GitHub، أو مولد موقع ثابت) وسترى النص والصور مطابقة لتنسيق Word الأصلي — فقط بصيغة خفيفة الوزن وصديقة للويب.

---

## الخطوة 4: التغييرات الشائعة وحالات الحافة

### 4.1 التعامل مع مجلدات الموارد الموجودة مسبقًا

إذا قمت بتشغيل التحويل عدة مرات، قد يتراكم صور قديمة. يمكن إضافة شرط حماية بسيط لتنظيف المجلد قبل كل تشغيل:

```csharp
if (Directory.Exists(resourceFolder))
{
    foreach (var file in Directory.GetFiles(resourceFolder))
        File.Delete(file);
}
else
{
    Directory.CreateDirectory(resourceFolder);
}
```

### 4.2 تغيير صيغ الصور

أحيانًا تحتاج جميع الصور بصيغة JPEG لتحسين الويب. داخل رد النداء يمكنك إعادة ترميز الـ stream:

```csharp
using (var img = System.Drawing.Image.FromStream(args.Stream))
{
    var jpegStream = new MemoryStream();
    img.Save(jpegStream, System.Drawing.Imaging.ImageFormat.Jpeg);
    jpegStream.Position = 0;
    args.Stream = jpegStream;
    args.FileName = Path.ChangeExtension(args.FileName, ".jpg");
}
```

> **نصيحة احترافية:** `System.Drawing.Common` يعمل على Windows؛ على Linux/macOS قد تفضّل `ImageSharp` لأمان متعدد المنصات.

### 4.3 الحفاظ على أنماط الجداول

إذا كان مستند Word يعتمد بشكل كبير على تنسيق الجداول، يمكنك تعديل `MarkdownSaveOptions`:

```csharp
markdownOptions.ExportTableColumnWidths = true;   // keeps column widths
markdownOptions.ExportTableBorders = true;       // adds markdown border syntax
```

### 4.4 استخدام دليل إخراج مختلف

طريقة `Save` تقبل أي مسار مطلق أو نسبي. في خطوط أنابيب CI يمكنك الإشارة إلى مجلد بناء مؤقت:

```csharp
document.Save(Path.Combine(Path.GetTempPath(), "doc.md"), markdownOptions);
```

---

## الأسئلة المتكررة

**س: هل يعمل هذا مع ملفات `.doc` (الثنائية)؟**  
ج: نعم. `new Document("file.doc")` يكتشف الصيغة تلقائيًا، لذا نفس الشيفرة تتعامل مع كل من `.doc` و `.docx`.

**س: ماذا لو احتوى ملف Word على صور SVG مدمجة؟**  
ج: Aspose.Words يستخرجها بصيغتها الأصلية. إذا كنت بحاجة إلى إصدارات نقطية، سيتعين عليك تحويل تدفق SVG داخل رد النداء (مثلاً باستخدام `Svg.Skia`).

**س: هل يمكنني تخطي استخراج الصور تمامًا؟**  
ج: عيّن `markdownOptions.ExportImagesAsBase64 = true;` لتضمين الصور مباشرة في markdown باستخدام data URIs — مفيد لإنشاء README بملف واحد.

---

## ملخص وخطوات مستقبلية

لقد استعرضنا الآن سير عمل كامل **لتحويل Word إلى Markdown**:

1. تحميل ملف `.docx`.
2. ضبط `MarkdownSaveOptions` مع `ResourceSavingCallback`.
3. حفظ المستند، مع ترك رد النداء يكتب كل صورة إلى مجلد مخصص.

هذا هو الحل الكامل في أقل من 50 سطرًا من C#.

إذا كنت مستعدًا للانتقال إلى المستوى التالي، فكر في:

- **إنشاء موقع ثابت**: مرّر markdown إلى مولد مثل Hugo أو Jekyll.
- **معالجة دفعات**: غلف الشيفرة داخل حلقة `foreach` لمعالجة عشرات الملفات تلقائيًا.
- **معالجة صور متقدمة**: تغيير الحجم، إضافة علامة مائية، أو تحويل الصيغ أثناء التنفيذ باستخدام رد النداء.

لا تتردد في التجربة — غير منطق رد النداء، عدّل خيارات الحفظ، أو دمج هذا في خط أنابيب مستندات أكبر. السماء هي الحد، والآن لديك أساس قوي لأي مشروع **توليد markdown من Word**.

برمجة سعيدة، ولتكن ملفات markdown دائمًا نظيفة وصورك دائمًا موجودة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}