---
category: general
date: 2026-02-20
description: تعلم كيفية حفظ صور Word وتحويل مستند Word إلى Markdown باستخدام C#. يوضح
  هذا الدليل خطوة بخطوة أيضًا كيفية استخراج الصور من Word وتصدير Markdown مع الصور.
draft: false
keywords:
- save word images
- convert word to markdown
- extract images from word
- convert docx to md
- export markdown with images
language: ar
og_description: في هذا الدليل نوضح لك كيفية حفظ صور Word وتحويل Word إلى Markdown
  باستخدام Aspose.Words. اتبع الخطوات لتصدير Markdown مع الصور.
og_title: حفظ صور Word أثناء تحويل Word إلى Markdown – دليل C# كامل
tags:
- Aspose.Words
- C#
- Markdown
title: حفظ صور Word أثناء تحويل Word إلى Markdown – دليل C# كامل
url: /ar/net/programming-with-markdownsaveoptions/save-word-images-while-converting-word-to-markdown-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ صور Word أثناء تحويل Word إلى Markdown – دليل C# كامل

هل احتجت يومًا إلى **save word images** عندما تقوم بتحويل مستند Word إلى Markdown؟ لست الوحيد—المطورون يواجهون باستمرار المشكلة التي تختفي فيها الصور بعد عملية بسيطة `convert docx to md`. في هذا الدرس سنستعرض طريقة نظيفة وجاهزة للإنتاج لـ **save word images**، **convert word to markdown**، والحصول على ملف Markdown لا يزال يعرض كل صورة.

تخيل أن لديك دليل مستخدم في `input.docx` وتريد نشره على موقع ثابت. تحتاج إلى النص بصيغة Markdown، ولكنك تحتاج أيضًا إلى لقطات الشاشة، المخططات، والشعارات لتظهر تمامًا في أماكنها. هذه هي المشكلة التي سنحلها—بدون أدوات خارجية، بدون نسخ ولصق يدوي، فقط بضع أسطر من C# و Aspose.Words.

بحلول نهاية هذا الدليل ستتمكن من:

* تحميل ملف `.docx` باستخدام Aspose.Words.  
* تهيئة `MarkdownSaveOptions` بحيث تقوم عملية التحويل أيضًا **extracts images from word**.  
* تنفيذ callback يكتب كل صورة إلى مجلد مخصص باسم فريد.  
* التحقق من أن ملف `.md` المُنشأ يشير إلى الصور بشكل صحيح، أي أنك نجحت في **exported markdown with images**.

> **المتطلبات المسبقة** – ستحتاج إلى .NET 6+ (أو .NET Framework 4.6+)، رخصة Aspose.Words صالحة (أو استخدم النسخة التجريبية المجانية)، وفهم أساسي لـ C#. إذا لم تستخدم Aspose من قبل، لا تقلق؛ الـ API سهل الفهم والكود أدناه مكتمل ومستقل.

## كيفية حفظ صور Word أثناء تحويل Word إلى Markdown

الخطوة الأولى هي **save word images** أثناء عملية التحويل. توفر Aspose.Words `ResourceSavingCallback` التي تُستدعى لكل مورد خارجي—صور، مخططات، SVGs، أيًا كان. من خلال ربط تنفيذنا الخاص نحدد بالضبط أين تُحفظ كل صورة على القرص.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source Word document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Configure Markdown save options and attach a callback that will handle external resources
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This callback will be invoked for every image, letting us control the file name and folder
    ResourceSavingCallback = new MyResourceCallback()
};

// Save the document as Markdown; the callback will store images in a custom folder
document.Save("YOUR_DIRECTORY/output.md", markdownOptions);

// -----------------------------------------------------------------
// Callback implementation – stores each image in a dedicated folder with a unique name
class MyResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Define the folder where resources will be saved
        string resourceFolder = "YOUR_DIRECTORY/MarkdownResources";
        Directory.CreateDirectory(resourceFolder);

        // Generate a unique file name while preserving the original extension
        string uniqueFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // Tell Aspose.Words where to write the resource
        args.ResourceFileName = Path.Combine(resourceFolder, uniqueFileName);
    }
}
```

هذه هي الحل الكامل—قم بتشغيله وستحصل على `output.md` بالإضافة إلى مجلد `MarkdownResources` المملوء بملفات الصور. سيحتوي Markdown على روابط مثل `![](MarkdownResources/7f3c2a1e-...png)`، مما يعني أنك نجحت في **save word images** و **export markdown with images** في خطوة واحدة.

## تهيئة خيارات Markdown لتحويل docx إلى md

لماذا نحتاج إلى callback أصلاً؟ بشكل افتراضي، تقوم Aspose.Words بدمج الصور كسلاسل base‑64 داخل Markdown، مما يزيد حجم الملف ويجعل التحكم في الإصدارات فوضويًا. ضبط `ResourceSavingCallback` يخبر المكتبة بـ **convert docx to md** *و* كتابة كل صورة إلى القرص بدلاً من تضمينها.

### الخصائص الأساسية التي قد تحتاج لتعديلها

| الخاصية | القيمة النموذجية | متى يجب التغيير |
|----------|---------------|----------------|
| `ExportImagesAsBase64` | `false` (default) | احتفظ بالصور كملفات منفصلة. |
| `ImagesFolder` | `null` (ignored when callback is used) | يمكنك تعيين مجلد ثابت إذا لم تكن بحاجة إلى تسمية ديناميكية. |
| `ExportHeadersFooters` | `true` | حافظ على محتوى الرأس/التذييل الذي قد يحتوي على صور. |
| `EncodeUrls` | `true` | مطلوب إذا كانت مساراتك تحتوي على مسافات أو أحرف غير ASCII. |

> **نصيحة احترافية:** إذا كنت تولد وثائق لعدة لغات، فكر في إضافة رمز اللغة إلى `resourceFolder` (مثال: `MarkdownResources/en`) حتى تبقى مسارات الصور منظمة.

## تنفيذ callback للموارد لاستخراج الصور من word

الـ callback في كتلة الكود السابقة يقوم بالعمل الشاق، لكن دعنا نفصلها قليلاً. `IResourceSavingCallback` يستقبل كائن `ResourceSavingArgs` لكل مورد خارجي. أهم الحقول هي:

* `ResourceFileName` – المسار الذي سيُكتب فيه الملف.  
* `ResourceFileExtension` – الامتداد الأصلي (`.png`, `.jpg`, إلخ).  
* `ResourceType` – يوضح ما إذا كان صورة، مخطط، أو شيء آخر.

يمكنك تصفية الموارد غير الصورية إذا كنت تهتم فقط بالصور:

```csharp
public void ResourceSaving(ResourceSavingArgs args)
{
    // Skip non‑image resources – we only want to save pictures
    if (args.ResourceType != ResourceType.Image)
        return;

    string resourceFolder = "YOUR_DIRECTORY/MarkdownResources";
    Directory.CreateDirectory(resourceFolder);

    string uniqueFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";
    args.ResourceFileName = Path.Combine(resourceFolder, uniqueFileName);
}
```

### معالجة الحالات الخاصة

1. **Duplicate images** – إذا ظهرت الصورة نفسها عدة مرات، سيستمر الـ callback في كتابة ملف جديد لكل ظهور. إذا كنت تفضل إزالة التكرار، احتفظ بـ `Dictionary<string, string>` الذي يربط تجزئة بايتات الصورة باسم ملف موجود.  
2. **Unsupported formats** – يمكن لـ Aspose.Words تصدير PNG، JPEG، GIF، BMP، و TIFF. إذا صادفت تنسيقًا غير مدعوم، ستحتاج إلى تحويله بنفسك (مثال: باستخدام `System.Drawing`).  
3. **Large documents** – بالنسبة لملفات PDF أو DOCX الضخمة، فكر في تدفق الإخراج لتجنب استنفاد الذاكرة. `MarkdownSaveOptions` يدعم `SaveOptions.UseMemoryCache = false`.

## حفظ المستند والتحقق من Markdown المُصدّر مع الصور

بعد تشغيل الكود، افتح `output.md` في أي محرر نصوص. يجب أن ترى شيئًا مثل:

```markdown
# Chapter 1

Here is a diagram:

![](MarkdownResources/2c7f9a3e-9b4d-4f6a-8d12-5e9f2c7a1b3c.png)

And another screenshot:

![](MarkdownResources/7a1d4e2f-3c9b-4a5d-9e8f-6b2c3d4e5f6a.jpg)
```

إذا كانت روابط الصور تبدو صحيحة، افتح ملف Markdown في عارض (معاينة VS Code، GitHub، أو مولد موقع ثابت). يجب أن تُعرض الصور تلقائيًا، مما يؤكد أنك نجحت في **save word images** و **export markdown with images**.

### سكريبت التحقق السريع

إذا رغبت في أتمتة الفحص، يقرأ المقتطف أدناه ملف Markdown المُولد للبحث عن ملفات مفقودة:

```csharp
using System;
using System.IO;
using System.Text.RegularExpressions;

string mdPath = "YOUR_DIRECTORY/output.md";
string mdFolder = Path.GetDirectoryName(mdPath)!;
string[] lines = File.ReadAllLines(mdPath);

foreach (var line in lines)
{
    var match = Regex.Match(line, @"!\[.*?\]\((.+?)\)");
    if (match.Success)
    {
        string imgPath = Path.Combine(mdFolder, match.Groups[1].Value);
        if (!File.Exists(imgPath))
            Console.WriteLine($"Missing image: {imgPath}");
    }
}
Console.WriteLine("Verification complete.");
```

شغّله بعد التحويل؛ أي صورة مفقودة ستُطبع على وحدة التحكم.

## الأخطاء الشائعة وأفضل الممارسات لتحويل word إلى markdown

| المشكلة | سبب الضرر | الحل |
|---------|--------------|-----|
| **Images end up with long GUID names** | صعب القراءة في نظام التحكم بالمصدر. | قم بمعالجة المجلد لاحقًا لإعادة تسمية الملفات بأسماء ذات معنى (مثال: بناءً على `args.ResourceFileName` الأصلي). |
| **Relative paths break after moving the Markdown file** | روابط `![]()` نسبية لموقع ملف `.md`. | احتفظ بمجلد الصور بجوار ملف Markdown أو استخدم مسار أساسي ثابت في إعدادات الموقع الثابت. |
| **Missing images when `ExportImagesAsBase64` is `true`** | الـ callback لا يُستدعى لأن الصور مدمجة. | تأكد من أن `ExportImagesAsBase64 = false` (الإعداد الافتراضي). |
| **Large documents cause `OutOfMemoryException`** | Aspose يحمل المستند بالكامل في الذاكرة. | استخدم `LoadOptions` مع `LoadFormat.Docx` واضبط علامات `MemoryOptimization` إذا كانت متاحة. |
| **Non‑ASCII file names break on some platforms** | قد يفشل ترميز URL. | استخدم أحرف ASCII فقط أو اضبط `EncodeUrls = true`. |

## الخلاصة

لقد غطينا كل ما تحتاجه لـ **save word images** أثناء **convert word to markdown** باستخدام Aspose.Words. الفكرة الأساسية بسيطة: أرفق `ResourceSavingCallback`، وجهه إلى مجلد تتحكم فيه، ودع المكتبة تقوم بالبقية. بعد التنفيذ ستحصل على ملف `.md` نظيف ومجموعة مرتبة من ملفات الصور—مثالية للنشر أو التحكم بالإصدارات.

إذا كنت ترغب في **extract images from word** لأغراض أخرى (مثال: إنشاء معرض)، فقط أعد استخدام كود الـ callback بدون خطوة حفظ Markdown. بالمثل، النمط نفسه يعمل لـ **convert docx to md** في وظائف الدفعات—فقط قم بالتكرار على مجلد يحتوي على ملفات `.docx` واستدعِ نفس المنطق.

**الخطوات التالية** التي قد تستكشفها:

* دمج عملية التحويل في API ASP.NET Core بحيث يمكن للمستخدمين رفع ملف DOCX والحصول على حزمة Markdown قابلة للتنزيل.  
* إضافة دعم للجداول و

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}