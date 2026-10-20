---
category: general
date: 2026-02-15
description: تعلم كيفية تحديد امتداد الملف عند تحويل DOCX إلى Markdown، واستخراج الصور،
  وحفظ المخططات بصيغة SVG، وتصدير الصور بصيغة PNG باستخدام Aspose.Words.
draft: false
keywords:
- determine file extension
- convert docx to markdown
- how to extract images
- save charts as svg
- export images as png
language: ar
og_description: اكتشف كيفية تحديد امتداد الملف، استخراج الصور، حفظ المخططات كـ SVG،
  وتصدير الصور كـ PNG عند تحويل DOCX إلى Markdown باستخدام Aspose.Words.
og_title: تحديد امتداد الملف أثناء تحويل DOCX إلى Markdown
tags:
- Aspose.Words
- C#
- Document Conversion
title: تحديد امتداد الملف أثناء تحويل DOCX إلى Markdown – دليل كامل
url: /ar/net/programming-with-markdownsaveoptions/determine-file-extension-while-converting-docx-to-markdown-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحديد امتداد الملف أثناء تحويل DOCX إلى Markdown – دليل كامل

هل تساءلت يومًا كيف **determine file extension** لكل مورد يخرج من ملف DOCX عندما تقوم بتحويله إلى Markdown؟ لست وحدك. في العديد من المشاريع الواقعية نحتاج إلى **convert docx to markdown**، استخراج كل صورة، والحفاظ على المخططات كملفات SVG واضحة—كل ذلك دون الحصول على ملف غامض باسم “resource_3.bin”.  

في هذا الدرس سنستعرض حلًا عمليًا لا يحدد **determine file extension** تلقائيًا فحسب، بل يوضح لك أيضًا **how to extract images**، **save charts as SVG**، و **export images as PNG** باستخدام Aspose.Words for .NET. في النهاية ستحصل على قطعة كود جاهزة للتنفيذ تُنتج ملف *.md* نظيفًا بالإضافة إلى مجلد منظم يحتوي على الأصول.

## ما ستحتاجه

- .NET 6+ (or .NET Framework 4.7.2+) – الـ API يعمل بنفس الطريقة على كلاهما.
- Aspose.Words for .NET (أحدث نسخة، مثلاً 23.9).  
- ملف DOCX يحتوي على صور، مخططات، أو أي مورد مدمج آخر.
- بيئة تطوير مفضلة (Visual Studio، Rider، أو VS Code).  

لا توجد حزم NuGet إضافية مطلوبة بخلاف Aspose.Words.

## الخطوة 1: تحميل مستند DOCX المصدر

أولًا وقبل كل شيء—احصل على ملف Word الذي تريد تحويله. هذه هي النقطة التي يبدأ فيها خط أنابيب التحويل.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the source DOCX. Adjust the path to where your file lives.
Document doc = new Document(@"C:\Docs\Complex.docx");
```

*لماذا هذا مهم:* كائن `Document` هو نقطة الدخول لكل عملية Aspose.Words. إذا تعذر تحميل الملف، لن يعمل أي شيء آخر، لذا تحقق دائمًا من المسار وأذونات الملف.

## الخطوة 2: إعداد مجلد للموارد المستخرجة

عند **determine file extension**، نحتاج أيضًا إلى مكان لوضع ملفات PNG أو SVG أو أي ملفات ثنائية أخرى ننتجها. إنشاء المجلد مسبقًا يجنب استثناءات “الدليل غير موجود” لاحقًا.

```csharp
// Define where the extracted assets will live.
string resourcesFolder = @"C:\Docs\MarkdownResources";

// Ensure the folder exists – CreateDirectory is idempotent.
Directory.CreateDirectory(resourcesFolder);
```

*نصيحة احترافية:* احفظ مجلد الموارد **بجانب** ملف Markdown النهائي؛ الروابط النسبية تصبح أكثر نظافة.

## الخطوة 3: تكوين MarkdownSaveOptions – قلب العملية

هنا نحدد فعليًا **determine file extension** لكل مورد. تسمح لنا فئة `MarkdownSaveOptions` بإيقاف تضمين Base‑64 وإدخال `ResourceSavingCallback`. داخل هذا الـ callback نفحص `args.ResourceType` ونقرر ما إذا كان يجب أن يكون الملف `.png` أو `.svg` أو شيء آخر.

```csharp
var mdOptions = new MarkdownSaveOptions
{
    // ExportImagesAsBase64 = false forces Aspose to write each image as a separate file.
    ExportImagesAsBase64 = false,

    // This callback runs for every external resource (image, chart, etc.).
    ResourceSavingCallback = (sender, args) =>
    {
        // ---- Step 3‑a: Determine a file extension based on the resource type ----
        string extension = args.ResourceType switch
        {
            // Images become PNG – this satisfies the “export images as png” requirement.
            ResourceType.Image => ".png",

            // Charts are saved as SVG – perfect for web‑friendly scaling.
            ResourceType.Chart => ".svg",

            // Anything else falls back to a generic binary.
            _ => ".bin"
        };

        // ---- Step 3‑b: Build a unique filename to avoid collisions ----
        string fileName = $"resource_{args.Index}{extension}";
        string fullPath = Path.Combine(resourcesFolder, fileName);

        // ---- Step 3‑c: Write the raw bytes to disk ----
        File.WriteAllBytes(fullPath, args.ResourceData);

        // ---- Step 3‑d: Tell the Markdown file where to find this asset ----
        // Use a relative path so the .md file stays portable.
        args.ResourceFileName = $"./MarkdownResources/{fileName}";
    }
};
```

### لماذا نحدد **determine file extension** صراحةً هنا

- **Clarity:** صورة `.png` يمكن التعرف عليها فورًا، بينما ملف `.bin` عشوائي يربك القراء.
- **Compatibility:** العديد من مولّدات المواقع الثابتة (Hugo, Jekyll) تتوقع أن تكون ملفات الصور ذات امتدادات قياسية.
- **Control:** يمكنك توسيع تعبير `switch` لمعالجة ملفات PDF، كائنات OLE، إلخ، دون تعديل باقي الشيفرة.

## الخطوة 4: حفظ المستند كـ Markdown

الآن بعد ضبط الخيارات، الاستدعاء النهائي هو سطر واحد. سيستدعي Aspose الـ callback لكل مورد، يكتب الملفات، وينتج مستند Markdown نظيف يشير إليها.

```csharp
// Save the Markdown file alongside the resources folder.
string markdownPath = @"C:\Docs\Complex.md";
doc.Save(markdownPath, mdOptions);
```

### النتيجة المتوقعة

- `Complex.md` – ملف Markdown يحتوي على روابط صور مثل `![](./MarkdownResources/resource_0.png)`.
- `C:\Docs\MarkdownResources\` – مجلد مملوء بـ:
  - `resource_0.png` (الصورة الأولى)
  - `resource_1.svg` (المخطط الأول)
  - …وهكذا لكل كائن مدمج.

افتح ملف Markdown في VS Code أو عارض؛ يجب أن ترى الصور معروضة بشكل صحيح. إذا ظهر مخطط كصورة نقطية غير واضحة، تحقق مرة أخرى من أن حالة `ResourceType.Chart` تُحوّل إلى `.svg`—هذا هو المفتاح لـ **save charts as svg**.

## الخطوة 5: التحقق والتعديل – المشكلات الشائعة والحالات الحدية

### 5.1 الصور المفقودة

إذا لاحظت روابط مكسورة، تأكد من أن المسار النسبي (`./MarkdownResources/`) يطابق اسم المجلد تمامًا. نظام Windows غير حساس لحالة الأحرف، لكن العديد من مولّدات المواقع الثابتة ليست كذلك.

### 5.2 الموارد غير الصورية

Aspose يمكنه أيضًا كشف كائنات مدمجة مثل PDFs أو حزم OLE. وسّع الـ `switch`:

```csharp
ResourceType.OleObject => ".pdf",
ResourceType.Unknown   => ".bin"
```

### 5.3 المستندات الكبيرة

لملفات DOCX التي تحتوي على عشرات الصور عالية الدقة، قد ترغب في **downscale** قبل الكتابة إلى القرص. أدخل خطوة ما قبل الحفظ:

```csharp
if (args.ResourceType == ResourceType.Image)
{
    using var img = Image.Load(args.ResourceData);
    img.Resize(800, 0, ResizeMode.Max); // keep aspect ratio
    args.ResourceData = img.SaveToBytes(ImageSaveFormat.Png);
}
```

### 5.4 تصدير الصور كـ PNG مقابل الصيغة الأصلية

العينة تُجبر PNG لكل صورة (`export images as png`). إذا كنت تفضل الحفاظ على الصيغة الأصلية (مثلاً JPEG)، استبدل امتداد `.png` بـ `Path.GetExtension(args.ResourceFileName)`. فقط تذكر تعديل نوع MIME في Markdown إذا لزم الأمر.

## مثال كامل يعمل

فيما يلي البرنامج الكامل جاهز للنسخ واللصق. يتم تجميعه كتطبيق سطر أوامر يستهدف .NET 6، لكن يمكنك وضع الشيفرة في أي نوع مشروع.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX.
            Document doc = new Document(@"C:\Docs\Complex.docx");

            // 2️⃣ Create a folder for external resources.
            string resourcesFolder = @"C:\Docs\MarkdownResources";
            Directory.CreateDirectory(resourcesFolder);

            // 3️⃣ Set up Markdown save options with a callback that determines file extensions.
            var mdOptions = new MarkdownSaveOptions
            {
                ExportImagesAsBase64 = false,
                ResourceSavingCallback = (sender, args) =>
                {
                    // Determine proper extension.
                    string extension = args.ResourceType switch
                    {
                        ResourceType.Image => ".png",   // export images as png
                        ResourceType.Chart => ".svg",   // save charts as svg
                        _ => ".bin"
                    };

                    // Unique name and full disk path.
                    string fileName = $"resource_{args.Index}{extension}";
                    string fullPath = Path.Combine(resourcesFolder, fileName);

                    // Write the bytes to disk.
                    File.WriteAllBytes(fullPath, args.ResourceData);

                    // Point the Markdown file to the saved resource.
                    args.ResourceFileName = $"./MarkdownResources/{fileName}";
                }
            };

            // 4️⃣ Save as Markdown.
            string markdownPath = @"C:\Docs\Complex.md";
            doc.Save(markdownPath, mdOptions);

            // 5️⃣ Inform the user.
            System.Console.WriteLine("Conversion complete!");
            System.Console.WriteLine($"Markdown file: {markdownPath}");
            System.Console.WriteLine($"Resources folder: {resourcesFolder}");
        }
    }
}
```

شغّل البرنامج، افتح `Complex.md`، وسترى منطق **determine file extension** قيد التنفيذ—كل صورة بصيغة PNG، كل مخطط بصيغة SVG، وجميع الروابط تشير إلى الملفات الصحيحة.

## الخلاصة

أنت الآن تعرف **how to determine file extension** لكل مورد عندما **convert docx to markdown**، وكيفية **extract images**، **save charts as SVG**، و **export images as PNG** باستخدام Aspose.Words. المفتاح هو `ResourceSavingCallback` حيث تقرر الامتداد، تكتب البايتات، وتحدد رابطًا نسبيًا.  

من هنا يمكنك:

- دمج مخرجات Markdown في مولّد موقع ثابت.
- توسيع الـ callback لمعالجة ملفات PDF، صوت، أو صيغ مخصصة.
- إضافة ضغط للصور أو وضع علامة مائية قبل الكتابة إلى القرص.

لا تتردد في التجربة—استبدل `.png` بـ `.jpg` إذا كان حجم الملف مهمًا، أو عدّل معالجة المخططات لإنتاج PNG بدلاً من SVG. النمط يبقى نفسه: **determine file extension**، كتابة الملف، وتحديث الرابط.

هل لديك أسئلة حول الحالات الحدية أو ترغب في مشاركة تعديلاتك؟ اترك تعليقًا أدناه، وبرمجة سعيدة!  

![مخطط تحديد امتداد الملف](determine_file_extension.png){: .align-center alt="مثال على تحديد امتداد الملف"}

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}