---
category: general
date: 2025-12-31
description: احفظ مستند Word كملف Markdown بسرعة باستخدام Aspose.Words. تعلّم كيفية
  تحويل DOCX إلى Markdown، استخراج الصور، وحفظ الصور باستخدام C#.
draft: false
keywords:
- save word as markdown
- convert docx to markdown
- extract images from docx
- how to extract images
- how to save images
language: ar
og_description: احفظ مستند Word كـ Markdown بسرعة باستخدام Aspose.Words. يوضح هذا
  الدليل كيفية تحويل DOCX إلى Markdown، استخراج الصور، وحفظ الصور في C#.
og_title: احفظ مستند Word كملف Markdown – تحويل DOCX واستخراج الصور
tags:
- Aspose.Words
- C#
- Markdown
- Document Conversion
title: حفظ ملف Word كـ Markdown – تحويل DOCX واستخراج الصور
url: /ar/net/programming-with-markdownsaveoptions/save-word-as-markdown-convert-docx-extract-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ Word كـ Markdown – دليل C# كامل

هل تساءلت يومًا كيف **تحفظ Word كـ markdown** دون فقدان الصور الموجودة داخل ملف DOCX؟ لست وحدك. يحتاج العديد من المطورين إلى تحويل ملفات Word الغنية إلى markdown خفيف الوزن للمواقع الثابتة، أو خطوط توثيق، أو ملاحظات مُدارة بالإصدار. الخبر السار؟ باستخدام Aspose.Words يمكنك **حفظ word كـ markdown**، **تحويل docx إلى markdown**، و**استخراج الصور من docx** في روتين واحد منظم.

في هذا الدرس سنستعرض تطبيقًا كاملًا جاهزًا للتنفيذ بلغة C# يعمل على وحدة التحكم ويقوم بذلك بالضبط. بنهاية الدرس ستعرف **كيفية استخراج الصور**، وكيفية التحكم بأسماء ملفات الصور، وكيفية جعل markdown يشير إلى تلك الملفات بشكل صحيح. لا سكريبتات خارجية، ولا نسخ‑لصق يدوي — مجرد كود نظيف يمكنك إدراجه في أي مشروع .NET.

---

## ما ستحتاجه

- **.NET 6.0** أو أحدث (الكود يعمل أيضًا على .NET Framework 4.7+).  
- **Aspose.Words for .NET** (نسخة تجريبية مجانية أو نسخة مرخصة). يمكنك تثبيتها عبر NuGet:

```bash
dotnet add package Aspose.Words
```

- ملف `input.docx` تجريبي يحتوي على صورة واحدة على الأقل.  
- بيئة تطوير أو محرر من اختيارك (Visual Studio، VS Code، Rider — أيًا كان مريحًا لك).

هذا كل شيء. لا مكتبات معالجة صور إضافية، ولا أدوات سطر أوامر معقدة. لنبدأ.

---

## حفظ Word كـ Markdown – تنفيذ خطوة بخطوة

### الخطوة 1: إعداد هيكل المشروع

أنشئ مشروع وحدة تحكم جديد وأضف توجيهات `using` التي يعتمد عليها المثال.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Adjust these paths to match your environment.
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.md";

            // Load the DOCX file.
            Document doc = new Document(inputPath);

            // Configure markdown options with a custom image‑saving callback.
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // Perform the conversion.
            doc.Save(outputPath, mdOptions);

            Console.WriteLine("Conversion complete! Check the markdown and the Resources folder.");
        }
    }
}
```

**لماذا هذا مهم:** تحميل المستند هو الخطوة المنطقية الأولى؛ بدونها لا يمكنك طلب Aspose.Words لتوليد أي شيء. فئة `MarkdownSaveOptions` تمنحك تحكمًا دقيقًا في كيفية معالجة الموارد الخارجية — مثل الصور.

### الخطوة 2: تنفيذ رد الاتصال لحفظ الصور

واجهة `IResourceSavingCallback` تُستدعى لكل *مورد خارجي* يرغب المحول في كتابته. من خلال توفير تنفيذنا الخاص نحدد أين تُحفظ الصور وما هو اسمها.

```csharp
public class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Choose a folder for extracted images.
        string resourcesFolder = @"YOUR_DIRECTORY\Resources";
        Directory.CreateDirectory(resourcesFolder);

        // 2️⃣ Generate a unique filename to avoid collisions.
        string extension = Path.GetExtension(args.FileName); // preserves .png, .jpg, etc.
        string uniqueName = $"img_{Guid.NewGuid()}{extension}";
        string fullPath = Path.Combine(resourcesFolder, uniqueName);

        // 3️⃣ Write the image stream to disk.
        using (FileStream fs = new FileStream(fullPath, FileMode.Create))
        {
            args.Stream.CopyTo(fs);
        }

        // 4️⃣ Tell the markdown writer where the image lives.
        // The markdown file will reference the image relative to its own location.
        args.Uri = $"Resources/{uniqueName}";
    }
}
```

**لماذا هذا مهم:**  
- **إنشاء المجلد** يضمن وجود دليل `Resources` حتى على جهاز جديد.  
- **التسمية بناءً على GUID** تمنع الكتابة فوق ملفات موجودة عندما يتم معالجة نفس الملف المصدر عدة مرات.  
- **تعيين `args.Uri`** يعيد كتابة رابط صورة markdown (`![](Resources/img_…png)`) بحيث يشير ملف `.md` النهائي إلى الموقع الصحيح.

### الخطوة 3: تشغيل المحول والتحقق من النتيجة

قم بترجمة البرنامج وتشغيله:

```bash
dotnet run
```

يجب أن ترى:

```
Conversion complete! Check the markdown and the Resources folder.
```

افتح `output.md` — ستجد نص markdown يعكس محتوى Word الأصلي. كل صورة ستظهر كالتالي:

```markdown
![](Resources/img_3f9c2a1e-7b4d-4e5a-9f6d-2b8c9d0e1f2a.png)
```

وسيحتوي مجلد `Resources` على ملفات PNG/JPEG الفعلية.

---

## أسئلة شائعة ومعالجة الحالات الخاصة

### كيف أتحكم في صيغة الصورة؟

Aspose.Words يحدد الصيغة بناءً على الصورة الأصلية. إذا أردت أن تكون جميع الصور بصيغة PNG، يمكنك فرض ذلك في رد الاتصال:

```csharp
args.Stream = new MemoryStream(); // create a new stream
Image img = Image.FromStream(args.Stream);
img.Save(fullPath, ImageFormat.Png);
args.Uri = $"Resources/{uniqueName}.png";
```

*(يتطلب `System.Drawing.Common` على .NET Core.)*

### ماذا لو كان ملف DOCX يحتوي على مئات الصور؟

نظام تسمية GUID يتوسع بسهولة — كل صورة تحصل على معرف فريد، واستدعاء `Directory.CreateDirectory` غير مكلف. مع ذلك، قد ترغب في تقليل عدد الملفات في كل مجلد لأداء أفضل على نظام الملفات. تعديل بسيط هو إنشاء مجلدات فرعية بناءً على أول حرفين من GUID.

### هل يمكن تضمين الصور كـ Base64 بدلاً من ملفات خارجية؟

نعم. عيّن `args.Uri` إلى URI بيانات:

```csharp
byte[] imgBytes = ((MemoryStream)args.Stream).ToArray();
string base64 = Convert.ToBase64String(imgBytes);
string mime = args.ContentType; // e.g., "image/png"
args.Uri = $"data:{mime};base64,{base64}";
```

احذر أن سلاسل Base64 الكبيرة قد تجعل ملف markdown ضخمًا.

### هل يعمل هذا مع ملفات DOCX محمية بكلمة مرور؟

إذا كان المستند المصدر مشفرًا، حمّله مع كلمة المرور:

```csharp
LoadOptions loadOpts = new LoadOptions { Password = "mySecret" };
Document doc = new Document(inputPath, loadOpts);
```

يبقى باقي خط الأنابيب دون تغيير.

---

## نصائح احترافية ومخاطر يجب الانتباه إليها

- **نصيحة احترافية:** احفظ مجلد `Resources` بجوار ملف markdown في المستودع. بهذه الطريقة تبقى الروابط النسبية صالحة عندما تنقل المستودع إلى جهاز آخر أو إلى خط أنابيب CI.  
- **احذر من:** أسماء الملفات الطويلة جدًا على Windows قد تصل إلى حد 260 حرفًا. عادةً ما تتجنب GUID هذا الحد، لكن إذا أضفت مسارًا طويلاً، فكر في تقصير اسم المجلد.  
- **نصيحة:** بعد التحويل، نفّذ بحثًا سريعًا (`![](`) للتأكد من أن كل إشارة صورة تقود إلى ملف موجود.  
- **تذكر:** فئة `MarkdownSaveOptions` تحتوي أيضًا على علم `ExportImagesAsBase64`. إذا ضبطته على `true` يمكنك تخطي رد الاتصال تمامًا — لكنك ستفقد القدرة على التحكم بأسماء الملفات.

---

## الخاتمة

لقد استعرضنا مثالًا كاملاً جاهزًا للإنتاج ي **حفظ word كـ markdown**، **يحول docx إلى markdown**، و**يستخرج الصور من docx** باستخدام Aspose.Words for .NET. من خلال تنفيذ `IResourceSavingCallback` تحصل على تحكم كامل في مكان تخزين الصور، وكيفية تسميتها، وكيفية إشارة markdown إليها. الحل يعمل مع ملاحظات صفحة واحدة وكذلك مع تقارير ضخمة تحتوي على عشرات الرسوم.

ما الخطوة التالية؟ جرب ربط هذا المحول مع مولد موقع ثابت مثل Hugo أو MkDocs، أو أتمتة تحويل مجموعة كاملة من ملفات التوثيق. يمكنك أيضًا استكشاف تحويل الجداول، الحواشي، أو الأنماط المخصصة عبر تعديل `MarkdownSaveOptions`.

برمجة سعيدة، ولتظل ملفات markdown نظيفة وصورك منظمة دائمًا!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}