---
category: general
date: 2026-02-18
description: إنشاء ملف ماركداون من المستند بخطوات سهلة لتصدير المستند إلى ماركداون
  وحفظ الصور في مجلد فرعي. تعلّم كيفية حفظ المستند كملف ماركداون باستخدام C#.
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: ar
og_description: إنشاء ملف ماركداون من مستند بلغة C# وتعلم كيفية تصدير المستند إلى
  ماركداون مع حفظ الصور في مجلد فرعي. اتبع الدليل خطوة بخطوة.
og_title: إنشاء ملف ماركداون من المستند – تصدير وحفظ الصور
tags:
- C#
- Aspose.Words
- Markdown export
title: إنشاء ماركداون من المستند – تصدير وحفظ الصور
url: /ar/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء markdown من المستند – تصدير وحفظ الصور

هل احتجت يوماً إلى **إنشاء markdown من المستند** لكنك لم تكن متأكدًا من كيفية الحفاظ على الصور المضمنة مرتبة؟ لست وحدك. في العديد من المشاريع نقوم بإنشاء تقارير، أدلة، أو مسودات مدونة برمجيًا، وآخر شيء نريده هو فوضى من ملفات الصور المنتشرة عبر مجلد الإخراج.  

في هذا الدرس سنستعرض حلاً كاملاً جاهزًا للتنفيذ ي **يصدر المستند إلى markdown**، يخزن كل صورة في مجلد فرعي مخصص *md‑resources*، وأخيرًا **يحفظ المستند كملف markdown** باستخدام Aspose.Words for .NET API. في النهاية ستحصل على طريقة واحدة يمكنك إدراجها في أي قاعدة شفرة C#، بالإضافة إلى مجموعة من النصائح للتعامل مع الحالات الخاصة.

> **نظرة سريعة:**  
> • إعداد `MarkdownSaveOptions`  
> • توفير `IResourceSavingCallback` يعيد توجيه الصور إلى مجلد فرعي  
> • استدعاء `Document.Save` مع الخيارات المكوَّنة  

إذا كنت تتساءل لماذا نختار الـ callback بدلاً من المعالجة اللاحقة، استمر في القراءة – سيتم شرح السبب خطوة بخطوة.

---

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)  
- Aspose.Words for .NET (حزمة NuGet `Aspose.Words`)  
- كائن `Document` مصدر (يمكن أن يكون .docx، .pdf، .rtf، إلخ)  

لا توجد مكتبات إضافية مطلوبة؛ واجهة الـ callback مدمجة في Aspose.Words.

---

## الخطوة 1: إنشاء markdown من المستند – تكوين خيارات الحفظ

أول ما نقوم به هو إنشاء كائن `MarkdownSaveOptions`. هذا الكائن يخبر Aspose.Words كيف يجب أن يتصرف التحويل، مثل أي نكهة Markdown تُستخدم، وما إذا كانت الصور تُدمج كـ Base64، وأين تُوضع الملفات المُولدة.

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **لماذا هذا مهم:**  
> بدون إنشاء `MarkdownSaveOptions` صراحةً، تعود المكتبة إلى الإعدادات الافتراضية التي تُدمج الصور مباشرةً في ملف Markdown كسلاسل Base64. هذا يجعل الملف ضخمًا ويُفقد الغرض من وجود مجلد *images* نظيف.

---

## الخطوة 2: تصدير المستند إلى markdown وتعريف معالجة الموارد

الآن نخبر الحافظ **أين** يضع كل صورة. واجهة `IResourceSavingCallback` تُعطينا نقطة ارتطام تُنفّذ لكل مورد (صورة، SVG، إلخ) يتم اكتشافه أثناء التصدير. داخل الـ callback نقوم بـ:

1. التأكد من وجود المجلد الهدف (`md-resources/`).  
2. تعيين `OutputFileName` إلى المجلد مضافًا إليه اسم المورد الأصلي.  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **سؤال شائع:** *ماذا لو أردت دمج الصور بدلًا من حفظها؟*  
> فقط تجاهل الـ callback أو عيّن `args.OutputFileName = null;` – سيقوم الحافظ بدمج الصورة كسلسلة Base64 تلقائيًا.

> **حالة خاصة:** بعض المستندات القديمة تحتوي على أسماء صور مكررة. الـ callback أعلاه سيستبدل الملف السابق. لتجنب ذلك، يمكنك إلحاق GUID:

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## الخطوة 3: حفظ المستند كـ markdown والتحقق من حفظ الصور

مع تكوين الخيارات بالكامل، المكالمة النهائية هي سطر واحد يكتب ملف Markdown والصور المرتبطة إلى القرص.

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

إذا سارت الأمور بسلاسة سترى:

- `MyReport.md` – تمثيل Markdown للمستند المصدر.  
- `md-resources/` – مجلد بجوار ملف .md يحتوي على كل صورة مستخرجة (مثال: `image001.png`, `image002.jpg`).  

**مقتطف Markdown نموذجي** (تم توليده تلقائيًا بواسطة Aspose.Words):

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **نصيحة احترافية:** افتح ملف `.md` المُولد في VS Code أو أي عارض Markdown؛ يجب أن تُعرض الصور فورًا لأن المسارات النسبية تتطابق مع بنية المجلد.

---

## مثال كامل قابل للتنفيذ

فيما يلي برنامج Console مستقل يمكنك لصقه في مشروع .NET جديد وتشغيله. ينشئ مستند Word بسيط، يضيف صورة، ثم **ينشئ markdown من المستند** مع تخزين الصورة في مجلد فرعي.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**ما يجب أن تراه** بعد التشغيل:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

افتح `ExportedDoc.md` – سيشير مرجع الصورة إلى `md-resources/sample-image.png`، وستظهر الصورة بشكل صحيح في أي عارض Markdown.

---

## تنويعات شائعة الأسئلة

| السيناريو | كيفية تعديل الكود |
|----------|----------------------|
| **تخطي تصدير الصور** (دمج كـ Base64) | احذف `ResourceSavingCallback` بالكامل، أو عيّن `args.OutputFileName = null;` داخل الـ callback. |
| **تغيير صيغة الصورة** (مثلاً جميعها PNG) | داخل الـ callback، عدّل `args.ResourceFileName` واختر تحويل التيار قبل الكتابة إذا لزم الأمر. |
| **اسم مجلد مخصص** | استبدل `"md-resources/"` بأي مسار نسبي أو مطلق تفضله. |
| **معالجة مستندات متعددة دفعة واحدة** | كرّر عبر مجموعة من كائنات `Document`، مع إعادة استخدام نفس نسخة `MarkdownSaveOptions` (تأكد فقط من مسح المجلد أو إعطائه اسمًا فريدًا لكل تشغيل). |

---

## الخاتمة

لقد أظهرنا لك **كيفية إنشاء markdown من المستند**، **تصدير المستند إلى markdown**، و**حفظ الصور في مجلد فرعي** باستخدام نهج نظيف قائم على الـ callback. النقاط الرئيسية هي:

- استخدم `MarkdownSaveOptions` للحصول على تحكم دقيق في عملية التصدير.  
- نفّذ `IResourceSavingCallback` لتوجيه الصور إلى مجلد مخصص، مما يحافظ على نظافة ملف Markdown.  
- نفس النمط يعمل مع أنواع موارد أخرى (SVG، صوت) – فقط افحص `args.ResourceType`.  

بعد ذلك، يمكنك استكشاف **حفظ المستند كـ markdown** مع أنماط عناوين مخصصة، أو دمج هذه العملية في ASP.NET Web API تُعيد ملف ZIP يحتوي على ملف `.md` وموارده. في كل الأحوال، أصبحت اللبنات الآن في صندوق أدواتك.

هل لديك أسئلة، أو لاحظت حالة خاصة لم نغطها؟ اترك تعليقًا أدناه، ونتمنى لك برمجة سعيدة!

---

![إنشاء markdown من مثال المستند](placeholder.png "إنشاء markdown من مثال المستند")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}