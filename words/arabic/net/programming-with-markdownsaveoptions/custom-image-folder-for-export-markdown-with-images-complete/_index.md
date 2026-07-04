---
category: general
date: 2026-06-20
description: مجلد الصور المخصص يتيح لك تصدير الماركدون مع الصور بسهولة. تعلّم كيفية
  حفظ الصور في دليل محدد وحفظ صور الماركدون في .NET.
draft: false
keywords:
- custom image folder
- export markdown with images
- save images specific directory
- save markdown images
language: ar
og_description: مجلد الصور المخصص يجعل تصدير الماركداون مع الصور بسيطًا. اتبع هذا
  الدليل خطوة بخطوة لحفظ الصور في دليل محدد وحفظ صور الماركداون.
og_title: مجلد صور مخصص – تصدير ماركداون مع الصور
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: custom image folder lets you export markdown with images easily. Learn
    how to save images specific directory and save markdown images in .NET.
  headline: custom image folder for export markdown with images – Complete Guide
  type: TechArticle
- description: custom image folder lets you export markdown with images easily. Learn
    how to save images specific directory and save markdown images in .NET.
  name: custom image folder for export markdown with images – Complete Guide
  steps:
  - name: Guarantees **atomicity** – images and markdown are written together, preventing
      broken links.
    text: Guarantees **atomicity** – images and markdown are written together, preventing
      broken links.
  - name: Eliminates a second file‑system scan, which can be costly for large docs.
    text: Eliminates a second file‑system scan, which can be costly for large docs.
  - name: Gives you the flexibility to rename or compress images on the fly.
    text: Gives you the flexibility to rename or compress images on the fly.
  type: HowTo
tags:
- Aspose.Words
- Markdown
- .NET
title: مجلد صور مخصص لتصدير ماركداون مع الصور – دليل كامل
url: /ar/net/programming-with-markdownsaveoptions/custom-image-folder-for-export-markdown-with-images-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# مجلد صور مخصص – تصدير Markdown مع الصور في .NET

هل احتجت يومًا إلى **مجلد صور مخصص** عند تصدير markdown مع الصور؟ لست الوحيد الذي يواجه هذه المشكلة. سواء كنت تولد وثائق، مشاركات مدونة، أو أدلة API، فإن تنظيم صورك في دليل مخصص يحفظك من شجرة ملفات فوضوية لاحقًا.

في هذا الدرس سنستعرض حلًا كاملًا وجاهزًا للتنفيذ يوضح لك **كيفية حفظ الصور في دليل محدد** أثناء إنشاء ملف markdown. سترى لماذا استخدام callback هو الطريقة الأنظف، وستنتهي الدليل بعينة شفرة كاملة يمكنك إدراجها في أي مشروع .NET.

## ما ستتعلمه

- تكوين Aspose.Words (أو أي مكتبة مشابهة) لإعادة توجيه حفظ الصور.
- تنفيذ callback يكتب كل صورة في **مجلد صور مخصص**.
- استخدام `MarkdownSaveOptions` لربط كل شيء معًا و **حفظ صور markdown** بشكل صحيح.
- نصائح للتعامل مع الحالات الخاصة مثل الأسماء المكررة أو الملفات الكبيرة.

### المتطلبات المسبقة

| المتطلب | لماذا يهم |
|-------------|----------------|
| .NET 6+ (or .NET Framework 4.7+) | الكود يستخدم `FileStream` و `Guid`. |
| Aspose.Words for .NET (or a comparable markdown exporter) | يوفر `MarkdownSaveOptions` وواجهة الـ callback. |
| Basic C# knowledge | ستحتاج إلى فهم الفئات (classes) و الـ streams. |
| An existing `Document` object (`doc`) | يفترض الدرس أنك تمتلك مستندًا (Document) مُعبأ مسبقًا. |

لا تحتاج إلى أدوات خارجية بخلاف ما ذُكر—كل شيء يعمل محليًا.

## الخطوة 1: تعريف Callback يخزن كل صورة في مجلد صور مخصص

جوهر الحل هو فئة (class) تنفذ `IResourceSavingCallback`. داخل `ResourceSaving` نقوم بإنشاء اسم ملف فريد، نبني المسار الكامل داخل المجلد الذي اخترته، ثم نوجه المكتبة لكتابة الصورة هناك.

```csharp
// Step 1: Define a callback that stores each image in a custom folder
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Generate a unique file name for the image
        var fileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // Build the full path inside the desired resources directory
        var fullPath = Path.Combine("YOUR_DIRECTORY", fileName);

        // Redirect the saving stream to the new location
        args.Stream = new FileStream(fullPath, FileMode.Create);
        args.KeepResourceStreamOpen = false;   // close after save

        // Update the markdown reference to point to the new file name
        args.ResourceFileName = fileName;
    }
}
```

**لماذا يعمل هذا:**  
- `Guid.NewGuid()` يضمن اسمًا فريدًا، مما يمنع التصادمات عندما يحتوي المستند المصدر على صور متعددة بنفس اسم الملف الأصلي.  
- عن طريق استبدال `args.Stream` نخبر المصدّر بالضبط أين يكتب البيانات الثنائية.  
- تحديث `args.ResourceFileName` يضمن أن إشارة markdown (`![](img_…​)`) تشير إلى الملف الذي يعيش الآن في **مجلد الصور المخصص** الخاص بك.

> **نصيحة احترافية:** استبدل `"YOUR_DIRECTORY"` بمسار مُنشأ باستخدام `Path.Combine(Environment.CurrentDirectory, "Images")` إذا كنت تريد أن يكون المجلد بجوار ملف markdown تلقائيًا.

## الخطوة 2: ربط الـ Callback بــ Markdown Save Options

بعد ذلك ننشئ كائن `MarkdownSaveOptions` ونُعيّن الـ callback الخاص بنا. هذا يخبر المصدّر باستدعاء `ImageSavingCallback` لكل مورد مدمج يصادفه.

```csharp
// Step 2: Configure Markdown save options to use the callback
var markdownOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new ImageSavingCallback()
};
```

**ما الذي يحدث خلف الكواليس؟**  
عند تشغيل `doc.Save`، تقوم Aspose.Words بالتجول عبر شجرة العقد في المستند. في كل مرة تصادف صورة، تُطلق `ResourceSaving`. الـ callback الخاص بنا يعترض هذا الحدث، يعيد توجيه تدفق الصورة، ويُحدّث رابط markdown. النتيجة؟ جميع الصور تنتهي في المجلد الذي حددته، وملف markdown يشير إليها بشكل صحيح.

## الخطوة 3: حفظ المستند كـ Markdown – يتم حفظ الصور عبر الـ Callback

أخيرًا، نستدعي `Save` مع كائن الخيارات. المكتبة تقوم بالعمل الشاق؛ الـ callback الخاص بنا يتولى وضع الملفات.

```csharp
// Step 3: Save the document as Markdown; images are saved via the callback
doc.Save("YOUR_DIRECTORY/DocWithImages.md", markdownOptions);
```

إذا كان `"YOUR_DIRECTORY"` هو `C:\Docs\MyProject`، سترى:

```
C:\Docs\MyProject\DocWithImages.md
C:\Docs\MyProject\img_3f2a1c4e‑b5d6‑4a7b‑9c8d‑e9f0a1b2c3d4.png
C:\Docs\MyProject\img_7e8f9a0b‑c1d2‑3e4f‑5g6h‑7i8j9k0l1m2n.jpg
```

ملف markdown يحتوي على أسطر مثل:

```markdown
![Image](img_3f2a1c4e‑b5d6‑4a7b‑9c8d‑e9f0a1b2c3d4.png)
```

هذا بالضبط ما تحتاجه **لحفظ صور markdown** في موقع يمكن التنبؤ به.

## مثال كامل يعمل

فيما يلي تطبيق console مستقل يمكنك نسخه ولصقه في Visual Studio. ينشئ مستندًا بسيطًا يحتوي على صورة، ثم يصدره باستخدام نهج المجلد المخصص.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, markdown with images!");
        builder.InsertImage("sample.jpg"); // Ensure sample.jpg exists next to the exe

        // 2️⃣ Define the callback (same as earlier)
        var options = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback()
        };

        // 3️⃣ Choose output folder (feel free to change)
        string outputDir = Path.Combine(Environment.CurrentDirectory, "Exported");
        Directory.CreateDirectory(outputDir); // creates if missing

        // 4️⃣ Save markdown and images
        string mdPath = Path.Combine(outputDir, "Document.md");
        doc.Save(mdPath, options);

        Console.WriteLine($"Markdown saved to: {mdPath}");
        Console.WriteLine("Images stored in the same folder.");
    }
}

// Callback class – identical to the earlier snippet
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        var fileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";
        var fullPath = Path.Combine("Exported", fileName);
        args.Stream = new FileStream(fullPath, FileMode.Create);
        args.KeepResourceStreamOpen = false;
        args.ResourceFileName = fileName;
    }
}
```

**الناتج المتوقع**

تشغيل البرنامج يطبع شيء مثل:

```
Markdown saved to: C:\MyApp\Exported\Document.md
Images stored in the same folder.
```

افتح `Document.md` وسترى إشارة صورة markdown تشير إلى `img_…​`. ملف الصورة يعيش بجوار ملف markdown، تمامًا كما يحدد تصميم **مجلد الصور المخصص**.

## معالجة الحالات الشائعة

| الحالة | الحل |
|-----------|----------|
| **أسماء ملفات مكررة** | استخدام `Guid` يتجنب التكرارات بالفعل؛ إذا كنت تفضّل أسماء قابلة للقراءة، أضف عدادًا (`img_001.png`, `img_002.png`). |
| **مجموعة صور كبيرة** | قم ببث الصورة مباشرة إلى القرص كما هو موضح؛ تجنّب تحميل الصورة بالكامل إلى الذاكرة. |
| **مجلدات إخراج مختلفة لكل تشغيل** | مرّر المجلد الهدف كمعامل في مُنشئ `ImageSavingCallback` بدلاً من كتابة `"Exported"` صراحة. |
| **عدم وجود أذونات كتابة** | تأكد من تشغيل التطبيق بصلاحيات كافية أو اختر مجلدًا قابلًا للكتابة من قبل المستخدم مثل `%TEMP%`. |
| **موارد غير صور (مثل CSS)** | الـ callback يُستدعى لأي مورد؛ يمكنك فحص `args.ResourceType` ومعالجة الصور فقط. |

## لماذا استخدام Callback بدلاً من المعالجة اللاحقة؟

قد تتساءل، “لماذا لا نولّد markdown أولًا، ثم ننقل الصور لاحقًا؟” نهج الـ callback:

1. يضمن **الذرة** – تُكتب الصور و markdown معًا، مما يمنع الروابط المكسورة.
2. يلغي الحاجة إلى فحص نظام ملفات ثاني، وهو ما قد يكون مكلفًا للوثائق الكبيرة.
3. يمنحك المرونة لإعادة تسمية أو ضغط الصور أثناء العملية.

باختصار، هو أكثر **طريقة قوية لتصدير markdown مع الصور** مع الحفاظ على كل شيء في **مجلد صور مخصص**.

## الخلاصة

لقد غطينا كل ما تحتاجه **لحفظ الصور في دليل محدد** و **لحفظ صور markdown** باستخدام استراتيجية **مجلد صور مخصص**. من خلال تنفيذ `IResourceSavingCallback`، وتكوين `MarkdownSaveOptions`، واستدعاء `doc.Save`، ستحصل على تنظيم نظيف للمجلدات وإشارات markdown موثوقة—كل ذلك في بضع عشرات من أسطر الشفرة.

التالي، قد تستكشف:

- إضافة ضغط للصور داخل الـ callback.
- إنشاء `README.md` يربط تلقائيًا بالمجلد.
- توسيع الـ callback لمعالجة أنواع موارد أخرى مثل CSS أو السكريبتات.

جرّبه في خط أنابيب التوثيق التالي—ستشكرك نفسك المستقبلية على هيكل المجلد المرتب.

برمجة سعيدة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [save docx as markdown – Full C# Guide with Image Extraction](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}