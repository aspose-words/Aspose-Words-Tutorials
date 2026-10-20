---
category: general
date: 2026-02-13
description: احفظ ملف Word كـ markdown واستخرج الصور من docx باستخدام C#. تعلم كيفية
  تحويل docx إلى markdown، حفظ الصور من docx، والحفاظ على تنظيم الموارد.
draft: false
keywords:
- save word as markdown
- convert docx to markdown
- how to extract images
- save images from docx
language: ar
og_description: احفظ ملف Word كـ markdown واستخرج الصور من docx مع مثال كامل بلغة
  C#. حوّل docx إلى markdown، احفظ الصور من docx، واحرص على تنظيم كل شيء.
og_title: حفظ الوورد كماركداون – استخراج الصور من ملف docx
tags:
- Aspose.Words
- C#
- Markdown conversion
title: حفظ ملف وورد كماركداون – استخراج الصور من ملف docx
url: /ar/net/programming-with-markdownsaveoptions/save-word-as-markdown-extract-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ ملف Word كـ markdown – استخراج الصور من docx

هل احتجت يوماً إلى **حفظ Word كـ markdown** مع الحفاظ على كل صورة موجودة داخل ملف *.docx* الأصلي؟ ربما تكون تبني مولّد مواقع ثابتة، أو تريد فقط نقل تقرير Word قديم إلى صيغة صديقة لـ Git. على أي حال، النقطة المؤلمة هي نفسها: التحويل يحذف الصور، أو ينتهي بك الأمر إلى مجموعة من الروابط المكسورة.

الأمر هو أنك لست مضطراً لكتابة محلل مخصص أو البحث يدوياً في بنية ZIP لملف *.docx*. باستخدام Aspose.Words يمكنك **تحويل docx إلى markdown** وفي الوقت نفسه **حفظ الصور من docx** إلى مجلد تختاره. في هذا الدليل سنستعرض برنامج C# كامل جاهز للتنفيذ يقوم بذلك بالضبط.

ستحصل على:

* ملف markdown يعكس تخطيط Word الأصلي.
* مجلد “MarkdownResources” يحتوي على كل صورة مستخرجة، مسماة تماماً كما ظهرت في المصدر.
* نمط رد نداء (callback) قابل لإعادة الاستخدام يمكنك تكييفه لـ PDFs، HTML، أو أي صيغة أخرى تدعمها Aspose.

> **المتطلبات المسبقة** – تحتاج إلى .NET 6+ (أو .NET Framework 4.7+)، رخصة صالحة لـ Aspose.Words (أو النسخة التجريبية المجانية)، وVisual Studio أو VS Code. لا توجد حزم NuGet أخرى مطلوبة.

---

## ما يغطيه هذا الدرس

سنقسم الحل إلى خطوات منطقية:

1. **تحميل المستند المصدر** – افتح ملف *.docx* الذي تريد تحويله.  
2. **إنشاء رد نداء لحفظ الموارد** – هذا يخبر Aspose أين يضع كل صورة.  
3. **تهيئة `MarkdownSaveOptions`** – ربط رد النداء بمصدّر markdown.  
4. **حفظ ملف markdown** – سطر واحد يقوم بالعمل الشاق.  

خلال العملية سنشرح *لماذا* كل جزء مهم، ونشير إلى الأخطاء الشائعة (مثل نقص صلاحيات المجلد)، ونوضح لك كيفية تعديل الكود لحالات خاصة مثل استخراج PNG فقط أو تسمية الصور بشكل مخصص.

---

## الخطوة 1 – تحميل المستند المصدر

قبل أي شيء تحتاج إلى كائن `Document` يشير إلى ملف Word الخاص بك. Aspose يختصر بنية ZIP لملف *.docx* بحيث يمكنك التعامل معه كأي كائن مستند آخر.

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Adjust the path to where your .docx lives.
const string inputPath = @"YOUR_DIRECTORY\input.docx";

Document doc = new Document(inputPath);
```

*لماذا هذا مهم*: إذا كان مسار الملف غير صحيح، ستطرح Aspose استثناء `FileNotFoundException` ويتوقف سير العمل بالكامل. استخدام ثابت (أو أفضل، قيمة من الإعدادات) يجعل من السهل تبديل الملفات دون تعديل المنطق الأساسي.

> **نصيحة احترافية** – غلف عملية التحميل بكتلة try/catch إذا كان من المتوقع أن يزود المستخدم الملف. بهذه الطريقة يمكنك إظهار رسالة خطأ ودية بدلاً من تتبع الأخطاء.

---

## الخطوة 2 – تعريف رد نداء يحدد مكان حفظ كل صورة

تتيح لك Aspose ربط عملية الحفظ عبر `IResourceSavingCallback`. يتلقى رد النداء كائن `ResourceSavingArgs` لكل مورد خارجي (صور، CSS، إلخ). سنستخدمه لتوجيه كل صورة إلى مجلد مخصص مع الحفاظ على اسم الملف الأصلي.

```csharp
// Step 2: Define a callback that decides where each image is saved.
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a path like: YOUR_DIRECTORY\MarkdownResources\image001.png
        string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "MarkdownResources");
        Directory.CreateDirectory(resourcesFolder); // ensures the folder exists

        string imagePath = Path.Combine(resourcesFolder, args.ResourceFileName);

        // Tell Aspose where to write the file.
        args.ResourceFilePath = imagePath;
        args.Stream = new FileStream(imagePath, FileMode.Create, FileAccess.Write);
    }
}
```

*لماذا هذا مهم*: بدون رد نداء، ستضع Aspose الصور في نفس مجلد ملف markdown وتمنحها أسماء عامة. بالتحكم في المسار، تحافظ على تنظيم مشروعك وتتفادى تصادم الأسماء.

**حالة خاصة** – بعض ملفات Word تضم نفس الصورة عدة مرات. `args.ResourceFileName` يحتوي بالفعل على تجزئة فريدة، لذا لن يحدث استبدال. إذا كنت تفضّل نظام تسمية تسلسلي، يمكنك الحفاظ على عداد ثابت داخل رد النداء.

---

## الخطوة 3 – تهيئة خيارات حفظ Markdown لاستخدام رد النداء المخصص

الآن نربط رد النداء بمصدّر markdown. `MarkdownSaveOptions` يتيح لك أيضاً تعديل مستويات العناوين، حدود كتل الشيفرة، أو ما إذا كنت تريد تضمين الصور كـ Base64 (نحن *لا* نفعل ذلك هنا).

```csharp
// Step 3: Configure Markdown save options to use the custom callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Attach our resource‑saving logic.
    ResourceSavingCallback = new MyMarkdownResourceCallback(),

    // Optional: keep original line breaks for better diff‑friendliness.
    ExportHeadersFooters = false,
    ExportImagesAsBase64 = false
};
```

*لماذا هذا مهم*: الخاصية `ResourceSavingCallback` هي الجسر بين نموذج المستند ونظام الملفات. نسيان ضبطها يعني فقدان الصور، وسيشير ملف markdown إلى ملفات غير موجودة.

---

## الخطوة 4 – حفظ المستند كـ Markdown، مع استدعاء رد النداء لكل مورد

أخيراً، نطلب من Aspose كتابة ملف markdown. ستستدعي المكتبة رد النداء لكل صورة، تكتب ملف الصورة، ثم تُدرج رابطًا نسبيًا في markdown.

```csharp
// Step 4: Save the document as Markdown, invoking the callback for each resource.
const string outputPath = @"YOUR_DIRECTORY\output.md";

doc.Save(outputPath, mdOptions);
```

عند انتهاء الكود، يجب أن ترى شيئين على القرص:

1. **output.md** – تمثيل Markdown لمحتوى Word الأصلي.  
2. **MarkdownResources/** – مجلد يحتوي على كل صورة مستخرجة (مثال: `image001.png`, `image002.jpg`).

**التحقق** – افتح `output.md` في أي عارض markdown. ستلاحظ وسوم صور مثل `![image001.png](MarkdownResources/image001.png)`. إذا تم عرض الصور، فقد نجحت.

---

## تنويعات شائعة وسيناريوهات “ماذا لو”

### 1. هل تريد تضمين الصور كـ Base64؟

قم بتعيين `ExportImagesAsBase64 = true` في `MarkdownSaveOptions`. ينتج ذلك ملف markdown واحد يحتوي على URI مضمّن للبيانات—مفيد للوثائق ذات الملف الواحد لكنه يزيد حجم الملف بشكل كبير.

### 2. هل تحتاج فقط إلى صور PNG؟

عدّل رد النداء لتصفية الملفات حسب الامتداد:

```csharp
if (Path.GetExtension(args.ResourceFileName).Equals(".png", StringComparison.OrdinalIgnoreCase))
{
    // Save as before.
}
else
{
    // Skip non‑PNG resources.
    args.Cancel = true;
}
```

### 3. تغيير مجلد الإخراج في وقت التشغيل

مرّر مسار المجلد كمعامل سطر أو من ملف إعدادات، ثم استخدم هذا المتغيّر عند بناء `resourcesFolder`. هذا يجعل الأداة قابلة لإعادة الاستخدام عبر مشاريع مختلفة.

### 4. التعامل مع مستندات ضخمة

لملفات Word ضخمة، فكر في تدفق الإخراج لتجنب تحميل كل شيء في الذاكرة. فئة `Document` في Aspose تعمل بالفعل بذاكرة منخفضة، لكن يمكنك أيضاً ضبط `MemoryOptimization = MemoryOptimization.MemoryOptimized` في `LoadOptions`.

---

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في تطبيق Console جديد (`dotnet new console`). تذكّر استبدال `YOUR_DIRECTORY` بمسار فعلي على جهازك وإضافة حزمة NuGet الخاصة بـ Aspose.Words (`dotnet add package Aspose.Words`).

```csharp
// Program.cs
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace DocxToMarkdown
{
    // Step 2: Callback that saves each image into a dedicated folder.
    class MyMarkdownResourceCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "MarkdownResources");
            Directory.CreateDirectory(resourcesFolder);

            string imagePath = Path.Combine(resourcesFolder, args.ResourceFileName);
            args.ResourceFilePath = imagePath;
            args.Stream = new FileStream(imagePath, FileMode.Create, FileAccess.Write);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Load the source document.
            const string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);

            // Step 3: Configure the markdown options.
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyMarkdownResourceCallback(),
                ExportImagesAsBase64 = false,
                ExportHeadersFooters = false
            };

            // Step 4: Save as markdown.
            const string outputPath = @"YOUR_DIRECTORY\output.md";
            doc.Save(outputPath, mdOptions);

            Console.WriteLine("Conversion complete!");
            Console.WriteLine($"Markdown file: {outputPath}");
            Console.WriteLine($"Images folder: {Path.Combine("YOUR_DIRECTORY", "MarkdownResources")}");
        }
    }
}
```

**المخرجات المتوقعة** (في وحدة التحكم):

```
Conversion complete!
Markdown file: C:\Projects\MyDocs\output.md
Images folder: C:\Projects\MyDocs\MarkdownResources
```

افتح `output.md` وسترى صsyntax markdown مع مراجع الصور التي تشير إلى مجلد `MarkdownResources`. جميع الصور تحتفظ بأسمائها الأصلية، لذا يمكنك تتبعها إلى ملف Word المصدر إذا لزم الأمر.

---

## الخلاصة

لقد أظهرنا لك كيفية **حفظ Word كـ markdown** مع استخراج الصور من docx في آنٍ واحد باستخدام Aspose.Words. الفكرة الأساسية هي `IResourceSavingCallback`—فهو يمنحك التحكم الكامل في مكان وضع كل مورد، مما يبقي markdown منظمًا وصورك مرتبة.

في برنامج واحد مستقل يمكنك:

* تحويل أي *.docx* إلى markdown نظيف (`convert docx to markdown`).  
* الحفاظ على كل صورة (`save images from docx`).  
* تخصيص تخطيط الإخراج لسلاسل المعالجة اللاحقة.

ما الخطوات التالية؟ جرّب التحويل إلى HTML أو PDF باستخدام نمط رد النداء نفسه، أو دمج هذا في مهمة CI تقوم تلقائيًا بمزامنة تقارير Word إلى مستودع موقع ثابت. الاحتمالات لا حصر لها، والآن لديك أساس قوي للبناء عليه.

هل لديك أسئلة، أو اكتشفت تعديلًا ذكيًا؟ اترك تعليقًا أدناه—برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}