---
category: general
date: 2026-05-29
description: احفظ ملف docx كملف markdown باستخدام Aspose.Words وتعلم كيفية استخراج
  الصور من docx في سير عمل واحد. كود خطوة بخطوة ونصائح.
draft: false
keywords:
- save docx as markdown
- extract images from docx
- convert word to markdown
- convert docx to markdown
- how to extract images
language: ar
og_description: احفظ ملف docx كملف markdown باستخدام Aspose.Words. تعلّم كيفية استخراج
  الصور من ملف docx أثناء تحويل Word إلى markdown، مع تضمين الكود الكامل.
og_title: حفظ ملف docx كـ markdown – دليل كامل مع استخراج الصور
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Save docx as markdown using Aspose.Words and learn how to extract images
    from docx in a single workflow. Step‑by‑step code and tips.
  headline: Save docx as markdown – Complete Guide with Image Extraction
  type: TechArticle
- description: Save docx as markdown using Aspose.Words and learn how to extract images
    from docx in a single workflow. Step‑by‑step code and tips.
  name: Save docx as markdown – Complete Guide with Image Extraction
  steps:
  - name: – Load the source document
    text: First we need a `Document` object that points at the Word file we want to
      transform.
  - name: – Define a callback that extracts images from docx
    text: The magic lives in `IResourceSavingCallback`. Aspose.Words calls `ResourceSaving`
      for every external resource (images, fonts, etc.) it needs to write out. By
      providing our own implementation we gain total control over the file name, folder,
      and even the stream used.
  - name: – Wire the callback into Markdown save options
    text: Now we create a `MarkdownSaveOptions` instance and assign our custom saver.
  - name: – Save the document as markdown
    text: Finally, we ask Aspose.Words to write out the markdown file. The images
      are saved automatically by the callback we just hooked.
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Conversion
title: حفظ ملف docx كـ markdown – دليل كامل مع استخراج الصور
url: /ar/net/programming-with-markdownsaveoptions/save-docx-as-markdown-complete-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ docx كـ markdown – دليل كامل مع استخراج الصور

هل تساءلت يومًا كيف **تحفظ docx كـ markdown** دون فقدان الصور المدمجة داخل ملف Word الخاص بك؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحاولون تحويل مستند غني بالنص إلى markdown نظيف وينتهي بهم الأمر بروابط صور مكسورة.  

في هذا الدرس سنستعرض حلًا عمليًا لا يقتصر فقط على **convert docx to markdown** بل أيضًا **extract images from docx** تلقائيًا. بنهاية الدرس ستحصل على مقتطف C# جاهز للتنفيذ، وعدة نصائح لأفضل الممارسات، وصورة واضحة لما تتوقعه عند تشغيل الكود.

## ما ستتعلمه

- إعداد Aspose.Words لـ .NET لمعالجة تحويل Word إلى markdown.  
- تنفيذ `IResourceSavingCallback` مخصص يحفظ كل صورة مدمجة في مجلد تختاره.  
- فهم لماذا الـ callback مهم وكيف يحافظ على بقاء مراجع الصور سليمة في markdown المُولّد.  
- عرض المثال الكامل القابل للتنفيذ ومخرجات markdown الدقيقة التي ستحصل عليها.  

**المتطلبات المسبقة** – ستحتاج إلى .NET 6 (أو أي نسخة حديثة من .NET)، Visual Studio 2022 (أو VS Code)، ورخصة نشطة لـ Aspose.Words for .NET (الإصدار التجريبي المجاني يكفي للاختبار). لا توجد مكتبات طرف ثالث أخرى مطلوبة.

---

## كيفية حفظ docx كـ markdown باستخدام Aspose.Words

فيما يلي سير العمل على المستوى العالي الذي سنتبعه:

1. تحميل ملف `.docx` المصدر الذي يحتوي على الصور.  
2. إنشاء فئة callback تحدد أين يجب كتابة كل صورة مستخرجة.  
3. ربط الـ callback بـ `MarkdownSaveOptions`.  
4. حفظ المستند – يتم كتابة markdown إلى القرص، وتُحفظ الصور في المجلد المحدد.  

يتم شرح كل خطوة بالتفصيل، ويتم عرض الكود مباشرةً بعد الشرح.

### الخطوة 1 – تحميل المستند المصدر

أولاً نحتاج إلى كائن `Document` يشير إلى ملف Word الذي نريد تحويله.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the source .docx that contains images.
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **لماذا هذا مهم:** تقوم Aspose.Words بتحليل حزمة DOCX، وتبني نموذج كائنات داخلي، وتتيح الوصول إلى كل فقرة، جدول، وصورة. إذا تعذر تحميل الملف، فإن بقية سير العمل لن يتم تشغيله.

### الخطوة 2 – تعريف callback يستخرج الصور من docx

السحر يكمن في `IResourceSavingCallback`. تقوم Aspose.Words باستدعاء `ResourceSaving` لكل مورد خارجي (صور، خطوط، إلخ) تحتاج إلى كتابته. من خلال توفير تنفيذنا الخاص نحصل على تحكم كامل باسم الملف، المجلد، وحتى الـ stream المستخدم.

```csharp
// Step 2: Define a callback that stores each extracted image in a sub‑folder
// and gives it a unique name.
class MyResourceSaver : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Create (or reuse) a folder for the images.
        string folder = "YOUR_DIRECTORY/markdown_images";
        Directory.CreateDirectory(folder);

        // Build a new file name like "img_0.png", "img_1.jpg", etc.
        string newName = Path.Combine(folder,
            $"img_{args.Index}{Path.GetExtension(args.ResourceFileName)}");

        // Tell Aspose.Words where to write the image.
        args.ResourceFileName = newName;
        args.Stream = new FileStream(newName, FileMode.Create, FileAccess.Write);

        // Allow the default saving process to continue.
        args.Cancel = false;
    }
}
```

> **نصيحة احترافية:** `args.Index` يبدأ من الصفر ويضمن التفرد حتى إذا شاركت صورتان نفس اسم الملف الأصلي. هذا يزيل الخطأ المزعج “اسم ملف مكرر” عند تشغيل التحويل عدة مرات.

### الخطوة 3 – ربط الـ callback بخيارات حفظ Markdown

الآن نقوم بإنشاء مثيل `MarkdownSaveOptions` ونعين الـ saver المخصص الخاص بنا.

```csharp
// Step 3: Configure Markdown save options to use the custom resource saver.
MarkdownSaveOptions opts = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver()
};
```

> **لماذا هذا أساسي:** بدون الـ callback، كانت Aspose.Words ستحقن الصور كسلاسل base‑64 داخل markdown أو ستتخلص منها تمامًا، حسب الإعدادات الافتراضية. الـ callback الخاص بنا يفرض إشارة نظيفة قائمة على ملف تعمل مع أي مولد مواقع ثابتة.

### الخطوة 4 – حفظ المستند كـ markdown

أخيرًا، نطلب من Aspose.Words كتابة ملف markdown. يتم حفظ الصور تلقائيًا بواسطة الـ callback الذي ربطناه للتو.

```csharp
// Step 4: Save the document as Markdown; images will be written to the folder above.
doc.Save("YOUR_DIRECTORY/output.md", opts);
```

عند انتهاء الكود، ستجد:

- `output.md` – تمثيل markdown للملف Word الأصلي.  
- `markdown_images/` – مجلد يحتوي على `img_0.png`، `img_1.jpg`، … لكل صورة كانت موجودة في DOCX.

#### مقتطف markdown المتوقع

```markdown
# Sample Title

Here is some introductory text.

![Image 1](markdown_images/img_0.png)

More text after the picture.
```

رابط الصورة يشير إلى الملف الذي حفظناه في الخطوة 2، لذا أي عارض markdown سيعرض الصورة بشكل صحيح.

---

## استخراج الصور من docx أثناء التحويل إلى markdown

إذا كان هدفك الوحيد هو **كيفية استخراج الصور** من مستند Word، يمكنك إعادة استخدام نفس الـ callback دون الحاجة حتى لحفظ markdown. فقط استدعِ `doc.Save("dummy.md", opts)` أو استخدم `doc.GetChildNodes(NodeType.Shape, true)` لتعداد الصور. سيُستدعى الـ callback لكل صورة، مما يتيح لك تخزينها في أي مكان تريد.

```csharp
// Example: extract images only – we still need a save call to trigger the callback.
doc.Save("YOUR_DIRECTORY/placeholder.md", opts);
```

> **ملاحظة:** يمكن حذف ملف markdown الوهمي بعد الاستخراج؛ فقد قام الـ callback بالفعل بكتابة الصور إلى القرص.

---

## تحويل Word إلى markdown مع معالجة مخصصة للصور

عبارة **convert word to markdown** غالبًا ما تُبحث مع “preserve formatting”. تقوم Aspose.Words بعمل جيد في الحفاظ على العناوين، القوائم، الجداول، وكتل الشيفرة. الشيء الوحيد الذي يجب الانتباه إليه هو تحجيم الصور. بشكل افتراضي يستخدم markdown المُولد أبعاد الصورة الأصلية. إذا كنت تحتاج إلى صور مصغرة، عدل الـ callback لتغيير حجم الصورة قبل كتابتها (مثلاً باستخدام `System.Drawing` أو `ImageSharp`).

```csharp
// Inside ResourceSaving, you could resize before saving:
using (var original = Image.Load(args.Stream))
{
    var thumbnail = original.Clone(ctx => ctx.Resize(new ResizeOptions
    {
        Size = new Size(300, 0),
        Mode = ResizeMode.Max
    }));
    thumbnail.Save(newName);
}
```

*(المقتطف أعلاه يستخدم ImageSharp – ستحتاج إلى إضافة حزمة NuGet إذا اخترت هذا المسار.)*

---

## المشكلات الشائعة عند تحويل docx إلى markdown

| المشكلة | لماذا يحدث | كيف نتجنبه |
|---------|------------|------------|
| تنتهي الصور كـ سلاسل **base64** | عدم تعيين `ResourceSavingCallback` الافتراضي | دائمًا قدم `IResourceSavingCallback` مخصص |
| روابط مكسورة بعد نقل ملف markdown | المسارات النسبية تشير إلى مجلد لم يعد موجودًا | احتفظ بمجلد `markdown_images` بجوار ملف `.md` أو عدل المسار في `MarkdownSaveOptions.ImageFolder` |
| تكرار أسماء الصور | صورتان تشتركان في نفس الاسم الأصلي | استخدم `args.Index` (كما فعلنا) أو GUID في اسم الملف |
| نفاد الذاكرة في المستندات الضخمة | حفظ صور كبيرة دون تدفق | استخدم `args.Stream = new FileStream(..., FileMode.Create, FileAccess.Write, FileShare.None, 4096, FileOptions.SequentialScan)` للتدفق بكفاءة |

---

## كيفية استخراج الصور – سيناريوهات متقدمة

أحيانًا تحتاج إلى الصور **بدون** أي markdown، ربما لتغذيتها إلى نموذج تعلم آلي. في هذه الحالة يمكنك:

1. تعيين `opts.SaveFormat = SaveFormat.Png` (أو أي تنسيق صورة) لإجبار التصدير على الصور فقط.  
2. أو، إعادة استخدام نفس `MyResourceSaver` لكن استدعاء `doc.Save("dummy.docx", SaveFormat.Docx)` فقط لتفعيل الـ callback.  

كلا النهجين يتيحان لك إعادة استخدام نفس المنطق، مع الحفاظ على مبدأ DRY (لا تكرر نفسك).

---

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه في تطبيق Console. استبدل `YOUR_DIRECTORY` بمسار مطلق أو نسبي موجود على جهازك.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace DocxToMarkdownDemo
{
    // Step 2 – custom callback that saves each image.
    class MyResourceSaver : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string folder = "YOUR_DIRECTORY/markdown_images";
            Directory.CreateDirectory(folder);

            string newName = Path.Combine(folder,
                $"img_{args.Index}{Path.GetExtension(args.ResourceFileName)}");

            args.ResourceFileName = newName;
            args.Stream = new FileStream(newName, FileMode.Create, FileAccess.Write);
            args.Cancel = false;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 1 – load the .docx.
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3 – set up save options with our callback.
            MarkdownSaveOptions opts = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyResourceSaver()
            };

            // Step 4 – save as markdown; images will be extracted automatically.
            doc.Save("YOUR_DIRECTORY/output.md", opts);

            System.Console.WriteLine("Conversion complete! Check output.md and the markdown_images folder.");
        }
    }
}
```

**ما يجب أن تراه بعد التشغيل:**  

- `output.md` يحتوي على نص markdown مع روابط صور مثل `![Image](markdown_images/img_0.png)`.  
- مجلد `markdown_images` مليء بملف واحد لكل صورة مدمجة.

---

## الخلاصة

أنت الآن تمتلك طريقة شاملة من البداية للنهاية **لحفظ docx كـ markdown** مع استخراج الصور من docx بشكل نظيف. المفتاح هو `IResourceSavingCallback` الذي يمنحك تحكمًا كاملًا في مكان وكيفية تخزين كل صورة.  

من هنا يمكنك:

- تعديل الـ callback لإعادة تسمية الملفات باستخدام عناوين ذات معنى (مثلاً بناءً على النص البديل).  
- إضافة معالجة لاحقة لتحويل markdown إلى HTML باستخدام مولد ثابت

## ما الذي يجب أن تتعلمه بعد ذلك؟

- [كيفية تضمين الصور في Markdown عند تحويل DOCX](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [حفظ صور Word – تحويل Word إلى Markdown باستخدام Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [كيفية إعادة تسمية الصور عند تحويل DOCX إلى Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}