---
category: general
date: 2026-01-14
description: تعلم كيفية استخدام الـ callback في C# لتحويل DOCX إلى markdown، واستخراج
  الصور من Word، وإنشاء أسماء صور فريدة.
draft: false
keywords:
- how to use callback
- convert docx to markdown
- extract images from word
- save word as markdown
- generate unique image names
language: ar
og_description: كيفية استخدام الـ callback في C# لتحويل DOCX إلى markdown، واستخراج
  الصور، وإنشاء أسماء صور فريدة.
og_title: كيفية استخدام الـ Callback في C# – تحويل DOCX إلى Markdown
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: كيفية استخدام Callback في C# – تحويل DOCX إلى Markdown
url: /ar/net/programming-with-markdownsaveoptions/how-to-use-callback-in-c-convert-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية استخدام Callback في C# – تحويل DOCX إلى Markdown

هل تساءلت يومًا **كيف تستخدم callback** عندما تحتاج إلى تحويل مستند Word إلى markdown نظيف؟ لست وحدك. يواجه معظم المطورين مشكلة عندما ينتج التحويل مجموعة من ملفات الصور بأسماء متصادمة أو عندما يشير الـ markdown إلى المجلد الخطأ. الخبر السار؟ باستخدام callback مخصص صغير يمكنك التحكم تمامًا في مكان حفظ كل مورد، وإعطاء كل صورة اسمًا فريدًا، والحفاظ على نظافة الـ markdown.

في هذا الدليل سنستعرض العملية بالكامل: تحميل ملف `.docx`، تكوين callback يحدد **أين** و**كيف** تُحفظ الصور، وأخيرًا كتابة النتيجة كـ markdown. بنهاية الدليل ستتمكن من **تحويل docx إلى markdown**، **استخراج الصور من Word**، و**إنشاء أسماء صور فريدة** دون الحاجة إلى أي تعديل يدوي في كل مرة. لا سكريبتات خارجية، فقط C# صافية و Aspose.Words.

> **المتطلبات المسبقة**  
> • .NET 6+ (أو .NET Framework 4.7+) مثبتة  
> • حزمة NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
> • فهم أساسي لفئات C# و I/O للملفات  

---

![مخطط كيفية استخدام callback](https://example.com/images/callback-diagram.png "مخطط يوضح كيفية استخدام callback لاستخراج الصور")

## كيفية استخدام Callback عند حفظ الموارد

النواة الأساسية للحل تكمن في فئة تُنفّذ `IResourceSavingCallback`. تقوم Aspose.Words باستدعاء هذه الواجهة لكل مورد خارجي (مثل صورة) تحتاج إلى كتابته على القرص. من خلال تجاوز `ResourceSaving` نحصل على تحكم كامل في مسار الهدف واسم الملف.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Custom callback that decides where each image extracted from a Word document will be saved.
/// </summary>
class MyResourceSaver : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Choose the folder where images will be stored.
        string folder = @"YOUR_DIRECTORY/Images/";

        // 2️⃣ Create a unique name – Guid guarantees no collisions.
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // 3️⃣ Combine folder and file name, then tell Aspose to use it.
        args.SavePath = Path.Combine(folder, uniqueName);
        args.Cancel = false; // Let Aspose perform the actual write.
    }
}
```

**لماذا هذا مهم:**  
- **قابلية التنبؤ** – جميع الصور تنتهي في نفس المجلد، مما يجعل مراجع الـ markdown موثوقة.  
- **تسمية خالية من التصادم** – استخدام `Guid.NewGuid()` يعني أنك لن تكتب فوق صورة موجودة، حتى لو كان المستند الأصلي يحتوي على أسماء مكررة.  
- **مرونة** – غيّر `folder` أو مخطط التسمية دون لمس منطق التحويل.

## تكوين خيارات حفظ Markdown (حفظ Word كـ Markdown)

الآن نربط الـ callback بـ `MarkdownSaveOptions`. هذا الكائن يخبر Aspose كيف يتعامل مع التحويل وأي callback يجب تشغيله.

```csharp
// Step 4: Hook our custom callback into the markdown options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver()
};
```

يمكنك أيضًا تعديل خيارات أخرى هنا، مثل `ExportImagesAsBase64` (ضبطه على `false` لأننا نريد ملفات صور منفصلة) أو `ExportHeadersAsHtml` إذا كنت بحاجة إلى مزيد من التحكم في تنسيق العناوين. الإعدادات الافتراضية تنتج بالفعل markdown نظيف يناسب معظم مولّدات المواقع الثابتة.

## تحميل المستند وإجراء التحويل (تحويل DOCX إلى Markdown)

مع إعداد الخيارات جاهزة، الخطوة الأخيرة بسيطة: تحميل ملف `.docx` وطلب من Aspose حفظه كـ markdown.

```csharp
// Step 5: Load the source DOCX and save it as Markdown.
Document doc = new Document(@"YOUR_DIRECTORY/input.docx");

// The output markdown will reference the images saved by MyResourceSaver.
doc.Save(@"YOUR_DIRECTORY/output.md", mdOptions);
```

**ما ستراه:**  
- يحتوي `output.md` على صيغة markdown (`![Alt text](Images/img_…png)`) التي تشير إلى مجلد الصور الذي حددته.  
- كل صورة تم استخراجها من `input.docx` تعيش تحت `YOUR_DIRECTORY/Images/` باسم فريد يعتمد على GUID.  

---

## تنويعات شائعة وحالات حافة

### 1️⃣ تغيير مخطط التسمية
إذا كنت تفضّل أسماء قابلة للقراءة (مثلاً `figure_1.png`) بدلاً من GUIDs، استبدل سطر `uniqueName` بشيء مثل:

```csharp
int counter = 0;
string uniqueName = $"figure_{++counter}{Path.GetExtension(args.ResourceFileName)}";
```

فقط تذكّر أن تجعل `counter` حقلًا ثابتًا أو تمرره عبر مُنشئ الـ callback حتى يبقى مستمرًا بين الاستدعاءات.

### 2️⃣ التعامل مع المجلدات الفرعية
بعض المشاريع تنظّم الصور حسب الفصول. يمكنك فحص `args.ResourceFileName` أو حتى نص الفقرة المحيطة لتحديد مجلد فرعي:

```csharp
string chapterFolder = Path.Combine(folder, $"Chapter_{args.ResourceFileName.Substring(0,1)}");
Directory.CreateDirectory(chapterFolder);
args.SavePath = Path.Combine(chapterFolder, uniqueName);
```

### 3️⃣ تخطي صور معينة
إذا كنت تريد استخراج PNGs فقط، أضف شرطًا:

```csharp
if (!args.ResourceFileName.EndsWith(".png", StringComparison.OrdinalIgnoreCase))
{
    args.Cancel = true; // Skip non‑PNG images.
    return;
}
```

### 4️⃣ التحقق من المخرجات
بعد التحويل، يمكنك التحقق برمجيًا من أن كل صورة مُشار إليها في الـ markdown موجودة فعليًا:

```csharp
string markdown = File.ReadAllText(@"YOUR_DIRECTORY/output.md");
var matches = System.Text.RegularExpressions.Regex.Matches(markdown, @"!\[.*?\]\((.*?)\)");
foreach (System.Text.RegularExpressions.Match m in matches)
{
    string imgPath = Path.Combine(@"YOUR_DIRECTORY", m.Groups[1].Value);
    Console.WriteLine(File.Exists(imgPath) ? "OK" : $"Missing: {imgPath}");
}
```

---

## نصائح احترافية لتجربة سلسة

- **أنشئ مجلد Images مسبقًا.** Aspose سيُنشئه تلقائيًا، لكن الإنشاء المسبق يُجنب مشاكل التزامن في السيناريوهات متعددة الخيوط.  
- **استخدم `Path.GetInvalidFileNameChars()`** إذا احتجت إلى تنقية الأسماء القادمة من المستند الأصلي.  
- **حرّر كائن `Document`** عندما تنتهي (ضعه داخل كتلة `using`) لتحرير الموارد الأصلية بسرعة.  
- **اختبر بمستند يحتوي على SVGs.** Aspose يحولها إلى PNG افتراضيًا؛ إذا كنت تحتاج الصيغة الأصلية، عدّل الـ callback وفقًا لذلك.

---

## النتيجة المتوقعة

تشغيل السكريبت على ملف `input.docx` تجريبي يحتوي على صورتين ينتج:

**`output.md` (مقتطف)**
```markdown
# Sample Document

Here is the first image:

![Image 1](Images/img_3f2c1b7e-9a4d-4b6e-8f3a-2d5e6c7b8a9c.png)

And here is the second one:

![Image 2](Images/img_7e8f9a0b-1c2d-3e4f-5a6b-7c8d9e0f1a2b.jpg)
```

**هيكل المجلد**
```
YOUR_DIRECTORY/
│─ input.docx
│─ output.md
└─ Images/
   ├─ img_3f2c1b7e-9a4d-4b6e-8f3a-2d5e6c7b8a9c.png
   └─ img_7e8f9a0b-1c2d-3e4f-5a6b-7c8d9e0f1a2b.jpg
```

جميع مراجع الصور تُحل بشكل صحيح، وقد نجحت في **حفظ Word كـ markdown** مع **استخراج الصور من Word** و **إنشاء أسماء صور فريدة**.

---

## الخلاصة

غطّينا **كيفية استخدام callback** في Aspose.Words لتحويل DOCX إلى markdown، استخراج كل صورة مدمجة، ومنح كل ملف اسمًا مميزًا خالٍ من التصادم. النهج خفيف الوزن، قابل للتخصيص بالكامل، ويعمل مع أي نسخة .NET تدعم Aspose.Words.

ما الخطوة التالية؟ جرّب ربط هذا مع مولّد موقع ثابت مثل Hugo أو Jekyll، أو أتمتة تحويل دفعات لمجلد كامل من المستندات. يمكنك أيضًا تجربة تصدير الجداول كـ markdown أو تعديل الـ callback لتضمين الصور كـ Base64 عندما لا تكون حجم الصورة مشكلة.

هل لديك تعديل ترغب في استكشافه؟ اترك تعليقًا، ولنستكشفه سويًا. برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}