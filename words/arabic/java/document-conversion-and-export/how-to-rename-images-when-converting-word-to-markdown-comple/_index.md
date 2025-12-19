---
category: general
date: 2025-12-18
description: تعلم كيفية إعادة تسمية الصور أثناء تحويل مستند Word إلى Markdown، بالإضافة
  إلى إرشادات خطوة بخطوة لتحويل ملف docx إلى Markdown وتصديره بكفاءة.
draft: false
keywords:
- how to rename images
- convert word to markdown
- export docx to markdown
- how to convert docx
- how to extract images
language: ar
og_description: اكتشف كيفية إعادة تسمية الصور أثناء تحويل Word إلى Markdown، مع أمثلة
  كاملة على الكود لتصدير ملفات docx إلى Markdown واستخراج الصور.
og_title: كيفية إعادة تسمية الصور – دليل تحويل Word إلى Markdown
tags:
- Aspose.Words
- C#
- Markdown conversion
title: كيفية إعادة تسمية الصور عند تحويل Word إلى Markdown – دليل كامل
url: /ar/java/document-conversion-and-export/how-to-rename-images-when-converting-word-to-markdown-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إعادة تسمية الصور – دليل كامل لتحويل Word إلى Markdown

هل تساءلت يومًا **كيف تعيد تسمية الصور** عندما تقوم بتحويل ملف Word .docx إلى Markdown نظيف؟ لست وحدك. يواجه العديد من المطورين عقبة عندما تصبح أسماء الصور الافتراضية فوضى من GUIDs، مما يجعل الـ Markdown النهائي صعب القراءة والصيانة.  

في هذا الدليل سنستعرض حلاً كاملاً قابلاً للتنفيذ لا يقتصر فقط على **كيفية إعادة تسمية الصور**، بل يوضح لك أيضًا **تحويل Word إلى Markdown**، **تصدير DOCX إلى Markdown**، وحتى **كيفية استخراج الصور** للمعالجة المنفصلة. في النهاية ستحصل على سكريبت C# واحد يقوم بكل ذلك—بدون أدوات إضافية، بدون إعادة تسمية يدوية.

> **معاينة سريعة:** سنستخدم Aspose.Words for .NET، نعدّ استدعاء `MarkdownSaveOptions`، ونعيد تسمية كل صورة مضمّنة إلى اسم فريد وقابل للقراءة من قبل الإنسان. كل الكود جاهز للنسخ‑اللصق.

---

## ما ستتعلمه

- **لماذا إعادة تسمية الصور مهمة** – القابلية للقراءة، تحسين محركات البحث، وإدارة الإصدارات.  
- **كيفية تحويل Word إلى Markdown** باستخدام Aspose.Words.  
- **كيفية تصدير DOCX إلى Markdown** مع معالجة موارد مخصصة.  
- **كيفية استخراج الصور** من DOCX وتخزينها في مجلد تختاره.  
- نصائح عملية، معالجة الحالات الطرفية، ومثال كامل قابل للتنفيذ.

**المتطلبات المسبقة**

- .NET 6.0 أو أحدث (الكود يعمل مع .NET Core و .NET Framework على حد سواء).  
- مكتبة Aspose.Words for .NET (نسخة تجريبية مجانية أو مرخصة).  
- معرفة أساسية بـ C# – إذا كنت تستطيع كتابة `Console.WriteLine` فأنت جاهز.

## كيفية إعادة تسمية الصور أثناء تحويل Word إلى Markdown

هذا هو جوهر الدليل. يوفر لنا `MarkdownSaveOptions.ResourceSavingCallback` نقطة توصيل لكل مورد مضمّن (صور، صوت، إلخ). داخل الاستدعاء نولد اسم ملف جديد، نكتب التيار إلى القرص، ونخبر Aspose بالاسم الجديد.

![مثال على إعادة تسمية الصور – لقطة شاشة لملفات الصور المعاد تسميتها](/images/how-to-rename-images-example.png "كيفية إعادة تسمية الصور أثناء التحويل")

### الخطوة 1: تثبيت Aspose.Words

أضف حزمة NuGet إلى مشروعك:

```bash
dotnet add package Aspose.Words
```

أو عبر وحدة تحكم مدير الحزم:

```powershell
Install-Package Aspose.Words
```

### الخطوة 2: إعداد MarkdownSaveOptions مع استدعاء إعادة التسمية

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Define the folder where images will be saved
string imageFolder = Path.Combine(Environment.CurrentDirectory, "myImages");
Directory.CreateDirectory(imageFolder);

// Create Markdown save options
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

// Set up the callback that runs for each embedded resource
mdOptions.ResourceSavingCallback = (resource, stream) =>
{
    // Only act on images – other resources (like audio) are left untouched
    if (resource.Type == ResourceType.Image)
    {
        // Generate a friendly, unique name: img_<guid>.png
        string newFileName = $"img_{Guid.NewGuid():N}.png";

        // Build the full path and copy the stream
        string fullPath = Path.Combine(imageFolder, newFileName);
        using (FileStream file = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            stream.CopyTo(file);
        }

        // Tell Aspose the new filename so the Markdown reference is correct
        resource.FileName = newFileName;
    }
};
```

**لماذا يعمل هذا:**  
- الاستدعاء يستقبل كائن `ResourceSavingArgs` (`resource`) و`Stream`.  
- بالتحقق من `resource.Type == ResourceType.Image` نتجنب العبث بالموارد غير الصورية.  
- `Guid.NewGuid():N` ينتج سلسلة سداسية عشرية مكوّنة من 32 حرفًا بدون شرطات، مما يضمن التفرد.  
- تحديث `resource.FileName` يعيد كتابة رابط الصورة في Markdown (`![](img_…png)`).

### الخطوة 3: تحميل DOCX وحفظه كـ Markdown

```csharp
// Path to the source Word document
string docxPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document
Document doc = new Document(docxPath);

// Export to Markdown, applying our custom resource handling
string markdownPath = Path.Combine(Environment.CurrentDirectory, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Conversion complete! Markdown saved to {markdownPath}");
Console.WriteLine($"Images saved to {imageFolder}");
```

هذا كل شيء. تشغيل البرنامج ينتج:

- `output.md` – Markdown نظيف مع مراجع صور مثل `![](img_1a2b3c4d5e6f7g8h9i0j1k2l3m4n5o6p.png)`.  
- مجلد `myImages` يحتوي على كل ملف صورة بنفس الاسم الودي.

## تحويل Word إلى Markdown – مثال كامل

إذا كنت تفضّل سكريبت ملف واحد، انسخ التالي إلى `Program.cs` وشغّله:

```csharp
// Program.cs
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // ---------- Configuration ----------
        string inputDocx = "YOUR_DIRECTORY/input.docx";
        string outputMd = "YOUR_DIRECTORY/output.md";
        string imagesDir = Path.Combine("YOUR_DIRECTORY", "myImages");
        Directory.CreateDirectory(imagesDir);

        // ---------- Step 1: Set up Markdown options ----------
        var mdOptions = new MarkdownSaveOptions();
        mdOptions.ResourceSavingCallback = (resource, stream) =>
        {
            if (resource.Type == ResourceType.Image)
            {
                string uniqueName = $"img_{Guid.NewGuid():N}.png";
                string destPath = Path.Combine(imagesDir, uniqueName);
                using (var file = new FileStream(destPath, FileMode.Create, FileAccess.Write))
                    stream.CopyTo(file);
                resource.FileName = uniqueName;
            }
        };

        // ---------- Step 2: Load DOCX ----------
        var doc = new Document(inputDocx);

        // ---------- Step 3: Save as Markdown ----------
        doc.Save(outputMd, mdOptions);

        Console.WriteLine($"✅ Done! Markdown at {outputMd}");
        Console.WriteLine($"🖼️ Images saved in {imagesDir}");
    }
}
```

**شرح كل كتلة**

| الكتلة | الغرض |
|-------|---------|
| **الإعدادات** | يوحد المسارات بحيث تحتاج لتعديلها مرة واحدة فقط. |
| **الخطوة 1** | ينشئ `MarkdownSaveOptions` وcallback لإعادة التسمية. |
| **الخطوة 2** | يقوم بتحميل ملف `.docx` إلى كائن Aspose `Document`. |
| **الخطوة 3** | ينفذ `Save` باستخدام الخيارات المخصصة، ويكتب كل من الـ Markdown والصور المعاد تسميتها. |

تشغيل باستخدام:

```bash
dotnet run
```

يجب أن ترى رسالتين في وحدة التحكم تؤكدان نجاح العملية.

## تصدير DOCX إلى Markdown – لماذا هذا النهج يتفوق على الأدوات اليدوية

- **الأتمتة** – لا حاجة لفتح Word، النسخ‑اللصق، وإعادة تسمية الملفات يدويًا.  
- **الاتساق** – كل صورة تحصل على اسم متوقع وفريد، وهو أمر رائع لإدارة الإصدارات (Git لن يظن أن الملف تغير لمجرد تغير GUID).  
- **القابلية للتوسع** – يعمل مع مستندات تحتوي على عشرات أو مئات الصور؛ الاستدعاء يُنفّذ تلقائيًا لكل مورد.  
- **القابلية للنقل** – الـ Markdown المُولد يعمل في أي مولّد مواقع ثابتة (Jekyll, Hugo, MkDocs) لأن روابط الصور نسبية ونظيفة.

## كيفية استخراج الصور من ملف DOCX (مكافأة)

أحيانًا تريد فقط الصور الأصلية، دون ملف Markdown. يمكن إعادة استخدام نفس الاستدعاء، أو يمكنك استخدام API `Document` الخاص بـ Aspose مباشرة:

```csharp
using Aspose.Words;
using System.IO;

// Load the document
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Iterate over all shapes (including inline images)
int imgCount = 0;
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.HasImage)
    {
        imgCount++;
        string imgPath = Path.Combine("YOUR_DIRECTORY/extractedImages", $"extracted_{imgCount}.png");
        shape.ImageData.Save(imgPath);
    }
}
Console.WriteLine($"{imgCount} images extracted.");
```

**نقاط رئيسية**

- `NodeType.Shape` يلتقط كلًا من الصور العائمة والمضمنة داخل النص.  
- `shape.ImageData.Save` يكتب الصورة الثنائية مباشرة إلى القرص.  
- يمكنك دمج هذا المقتطف مع تحويل Markdown إذا كنت بحاجة إلى كلا الناتجين.

## نصائح عملية ومخاطر شائعة

- **تصادم الأسماء:** استخدام GUID يزيل التصادمات عمليًا، لكن إذا احتجت أسماء قابلة للقراءة (مثل `chapter1_figure2.png`)، يمكنك اشتقاق الاسم من `resource.Name` أو نص الفقرة المحيطة.  
- **المستندات الكبيرة:** التيارات تُنسخ مباشرة إلى القرص؛ للملفات الضخمة قد تحتاج إلى تخزين مؤقت أو كتابة إلى موقع مؤقت أولًا.  
- **صور غير PNG:** الاستدعاء أعلاه يفرض امتداد `.png`. إذا كانت الصورة الأصلية JPEG، قد ترغب في الحفاظ على الصيغة الأصلية: `Path.GetExtension(resource.FileName)` أو `resource.ContentType`.  
- **الأداء:** الاستدعاء يعمل بشكل متزامن. إذا كنت تعالج عشرات المستندات بالتوازي، غلف التحويل داخل `Task.Run` أو استخدم مجموعة خيوط لتجنب حجب الواجهة.  
- **الترخيص:** Aspose.Words يعمل بدون ترخيص في وضع التقييم، لكنه يضيف علامة مائية إلى الناتج. ثبّت ملف الترخيص (`Aspose.Words.lic`) للحصول على نتيجة نظيفة.

## الخلاصة

لقد غطينا **كيفية إعادة تسمية الصور** عند تحويل مستند Word إلى Markdown، وأظهرنا لك سير عمل كامل **لتحويل Word إلى Markdown**، وشرحنا **تصدير DOCX إلى Markdown** مع معالجة موارد مخصصة، وحتى شرحنا **كيفية استخراج الصور** من ملف DOCX. الكود مستقل، حديث، وجاهز للإنتاج.

جرّبه—ضع ملف `.docx` في المجلد، شغّل السكريبت، وستظهر لك ملفات Markdown نظيفة وصور مسماة بأسماء مرتبة. من هناك يمكنك دفع الـ Markdown إلى مولّد موقع ثابت، رفع الصور إلى Git، أو إدخال الناتج في خط أنابيب توثيق.

هل لديك أسئلة حول حالات الطرفية أو تريد دمج هذا في خدمة ASP.NET Core؟ اترك تعليقًا، وسنستكشف تلك السيناريوهات معًا. تحويل سعيد!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}