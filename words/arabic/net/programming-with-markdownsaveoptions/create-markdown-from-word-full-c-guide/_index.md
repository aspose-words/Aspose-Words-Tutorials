---
category: general
date: 2026-03-27
description: إنشاء ملف ماركداون من Word باستخدام Aspose.Words C#. تعلم تحويل ملفات
  docx إلى ماركداون، استخراج الصور من Word، وكيفية استخدام الـ callback في دليل واحد.
draft: false
keywords:
- create markdown from word
- convert docx to markdown
- extract images from word
- how to extract images
- how to use callback
language: ar
og_description: إنشاء ملف ماركداون من Word باستخدام Aspose.Words. يوضح هذا الدليل
  كيفية تحويل docx إلى ماركداون، واستخراج الصور من Word، واستخدام رد نداء لمعالجة
  الموارد.
og_title: إنشاء ماركداون من Word – دورة C# كاملة
tags:
- Aspose.Words
- C#
- Markdown
- Word
title: إنشاء ماركداون من Word – دليل C# الكامل
url: /ar/net/programming-with-markdownsaveoptions/create-markdown-from-word-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء markdown من Word – دورة C# كاملة

هل احتجت يومًا إلى **إنشاء markdown من Word** لكن لم تكن متأكدًا من أين تبدأ؟ لست وحدك؛ يواجه العديد من المطورين هذه المشكلة عندما يحاولون نقل المحتوى من ملف .docx إلى مولد موقع ثابت أو مستودع توثيق. الخبر السار؟ باستخدام Aspose.Words يمكنك **تحويل docx إلى markdown**، استخراج كل صورة من الملف الأصلي، والتحكم بدقة في مكان وضع هذه الموارد—كل ذلك عبر رد نداء بسيط.

> **نصيحة احترافية:** إذا كان لديك قالب Word يحتوي على لقطات شاشة أو مخططات أو شعارات، فإن هذه الطريقة ستحافظ على كل عنصر بصري دون الحاجة إلى النسخ واللصق يدويًا.

---

## ما ستحتاجه

- **.NET 6+** (أو .NET Framework 4.6+). يعمل الكود على أي بيئة تشغيل حديثة.
- **Aspose.Words for .NET** (حزمة NuGet `Aspose.Words`). النسخة التجريبية المجانية تكفي لمعظم السيناريوهات.
- مستند **Word** (`input.docx`) يحتوي على نص وعلى الأقل صورة واحدة.
- فهم أساسي للغة C# وVisual Studio (أو أي بيئة تطوير مفضلة لديك).

لا توجد مكتبات إضافية مطلوبة—كل شيء آخر يتم التعامل معه بواسطة Aspose.Words نفسه.

---

## الخطوة 1: إعداد المشروع وتثبيت Aspose.Words

للحفاظ على التنظيم، ابدأ مشروعًا جديدًا من نوع console:

```bash
dotnet new console -n WordToMarkdown
cd WordToMarkdown
dotnet add package Aspose.Words
```

> **لماذا هذه الخطوة مهمة:** تثبيت حزمة NuGet يضمن حصولك على أحدث API، والتي تتضمن الفئة `MarkdownSaveOptions` التي تم تقديمها في الإصدار 22.9. بدونها سيتعين عليك كتابة محول مخصص.

---

## الخطوة 2: تحميل مستند Word المصدر

السطر الأول من الكود يفتح ملف `.docx` الذي تريد تحويله. استبدل `YOUR_DIRECTORY` بالمسار الفعلي على جهازك.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the source Word document that contains images
Document sourceDocument = new Document("YOUR_DIRECTORY/input.docx");
```

> **ماذا يحدث؟** `Document` يقوم بتحليل الملف، يبني شجرة DOM داخلية، ويجعل كل فقرة، جدول، وصورة قابلة للوصول. إذا كان الملف مفقودًا، يرمي Aspose استثناء `FileNotFoundException` واضح، يمكنك التقاطه لتوفير واجهة مستخدم أكثر سلاسة.

---

## الخطوة 3: تكوين خيارات حفظ Markdown مع رد نداء حفظ الموارد

هنا يأتي سحر **كيفية استخدام رد النداء**. يتيح لك رد النداء تحديد مكان وضع كل صورة مستخرجة.

```csharp
// Prepare Markdown save options and attach a custom resource‑saving callback
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver()
};
```

> **لماذا رد نداء؟** بشكل افتراضي، سيقوم Aspose بدمج الصور كسلاسل base‑64 داخل ملف markdown—وهو ما يمثل كابوسًا لإدارة الإصدارات. يمنحك رد النداء تحكمًا كاملاً في أسماء الملفات وبنية المجلدات.

---

## الخطوة 4: حفظ المستند كـ Markdown

الآن نولد ملف `.md`. جميع الصور ستمر عبر رد النداء المحدد في الخطوة التالية.

```csharp
// Save the document as Markdown; images will be processed by the callback
sourceDocument.Save("YOUR_DIRECTORY/Document.md", markdownOptions);
```

إذا سارت الأمور على ما يرام، ستجد `Document.md` في المجلد المستهدف ومجلدًا فرعيًا اسمه `Resources` يحتوي على كل الصور المستخرجة من ملف Word الأصلي.

---

## الخطوة 5: تنفيذ رد النداء الذي يخزن كل صورة مستخرجة

فيما يلي التنفيذ الكامل لـ `MyResourceSaver`. يقوم بإنشاء دليل `Resources` (إذا لم يكن موجودًا)، يبني اسم ملف فريد لكل صورة، ويكتب تدفق الصورة إلى القرص.

```csharp
// Define the callback that stores each extracted image in a sub‑folder
class MyResourceSaver : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Ensure the resources folder exists
        string resourceFolder = "YOUR_DIRECTORY/Resources";
        Directory.CreateDirectory(resourceFolder);

        // 2️⃣ Build a unique file name for each image (e.g., img_0.png)
        string imageFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";

        // 3️⃣ Provide a stream that writes the image to the target file
        string fullPath = Path.Combine(resourceFolder, imageFileName);
        args.Stream = new FileStream(fullPath, FileMode.Create);
        args.KeepResourceStreamOpen = false; // close the stream after saving
    }
}
```

> **شرح الوسائط:**
> - `args.Index` – عداد يبدأ من الصفر يضمن التفرد.
> - `args.FileName` – اسم الملف الأصلي الذي يقترحه Aspose (غالبًا شيء مثل `image001.png`).
> - `args.Stream` – تدفق الإخراج حيث تُكتب بايتات الصورة.
> - `args.KeepResourceStreamOpen` – يُضبط على `false` حتى يقوم Aspose بإغلاق التدفق تلقائيًا، مما يمنع تسرب مقبض الملف.

---

## مثال كامل يعمل

بدمج كل ما سبق، إليك ملف واحد يمكنك نسخه ولصقه في `Program.cs`. تذكر استبدال `YOUR_DIRECTORY` بمسار مطلق أو نسبي يناسب بيئتك.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace WordToMarkdown
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source docx
            Document sourceDocument = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Set up markdown options with our callback
            MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyResourceSaver()
            };

            // 3️⃣ Save as markdown – images will be extracted automatically
            sourceDocument.Save("YOUR_DIRECTORY/Document.md", markdownOptions);

            System.Console.WriteLine("✅ Conversion complete! Check the Resources folder for images.");
        }
    }

    // 4️⃣ Callback implementation (see detailed version above)
    class MyResourceSaver : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourceFolder = "YOUR_DIRECTORY/Resources";
            Directory.CreateDirectory(resourceFolder);

            string imageFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
            string fullPath = Path.Combine(resourceFolder, imageFileName);

            args.Stream = new FileStream(fullPath, FileMode.Create);
            args.KeepResourceStreamOpen = false;
        }
    }
}
```

### النتيجة المتوقعة

- `YOUR_DIRECTORY/Document.md` – ملف markdown يحتوي على روابط صور markdown قياسية، مثال:

  ```markdown
  ![Image 1](Resources/img_0.png)
  ```

- `YOUR_DIRECTORY/Resources/` – يحتوي على `img_0.png`، `img_1.jpg`، إلخ، وفقًا لترتيب ظهورها في مستند Word الأصلي.

تشغيل البرنامج يطبع رسالة تأكيد ودية، تُخبرك بأن العملية نجحت.

---

## الأسئلة المتكررة (FAQ)

### كيف تستخرج الصور من Word دون فقدان الجودة؟

يقوم رد النداء بكتابة تدفق البايتات الخام مباشرة إلى ملف، مما يحافظ على الدقة الأصلية. لا يحدث أي تحويل أو ضغط ما لم تقم بإضافة منطق معالجة صور خاص داخل `ResourceSaving`.

### هل يمكنني تغيير صيغة الصورة (مثال: PNG → JPEG) أثناء الاستخراج؟

بالتأكيد. داخل `ResourceSaving` يمكنك فحص `args.FileName` أو `args.Stream`، تحميل الصورة باستخدام `System.Drawing` أو `ImageSharp`، ثم إعادة ترميزها قبل الكتابة. فقط تذكر تحديث امتداد رابط markdown وفقًا لذلك.

### ماذا إذا كنت أحتاج أن تشير ملفات markdown إلى CDN بدلاً من مجلد محلي؟

عدّل رد النداء لإضافة عنوان URL أساسي إلى رابط markdown. يمكنك تحقيق ذلك عن طريق تعيين `args.FileName` إلى URL كامل بعد رفع الصورة إلى CDN الخاص بك.

### هل يعمل هذا مع الجداول، الحواشي، أو ميزات Word المتقدمة الأخرى؟

نعم. يقوم Aspose.Words بترجمة معظم بنى Word إلى ما يعادلها في markdown. الجداول تتحول إلى جداول markdown، الحواشي إلى روابط مرجعية، والقوائم المتداخلة تُعالج بسلاسة. إذا ظهر شيء غير متوقع، راجع ملاحظات الإصدار الأخيرة—فـ Aspose يواصل تحسين دقة التحويل.

### كيف تحول docx إلى markdown في خط أنابيب CI/CD؟

ما عليك سوى إضافة الملف التنفيذي `.exe` إلى خطوات البناء، وتوجيهه إلى ملفات `.docx` التي تم إنشاؤها، ثم دفع ملفات `.md` ومجلد `Resources/` إلى مستودع الموقع الثابت. نظرًا لأن العملية حتمية بالكامل، فهي تعمل جيدًا في البيئات الآلية.

---

## الخلاصة

لقد استعرضنا كيفية **إنشاء markdown من Word** باستخدام Aspose.Words، غطينا سير عمل **تحويل docx إلى markdown** بالكامل، وأظهرنا طريقة عملية **لاستخراج الصور من Word** عبر تنفيذ **كيفية استخدام رد النداء** المخصص. النتيجة هي ملف markdown نظيف مع مجلد صور أصلي—مثالي لمواقع التوثيق، المدونات الثابتة، أو أي سير عمل يفضّل الصيغ النصية البسيطة.

الخطوات التالية التي قد تفكر فيها:

- **معالجة دفعات** لعدة ملفات `.docx` في مجلد (استخدام حلقة `Directory.GetFiles`).
- **أنظمة تسمية مخصصة** للصور (مثلاً باستخدام نص التسمية التوضيحية الأصلي).
- **معالجة لاحقة** للmarkdown لاستبدال روابط الصور بروابط CDN.
- استكشاف **صيغ تصدير Aspose الأخرى** مثل HTML، PDF، أو EPUB للنشر متعدد القنوات.

هل لديك أسئلة إضافية أو ملف Word معقد يرفض التحويل؟ اترك تعليقًا أدناه، ولنحل المشكلة سويًا. برمجة سعيدة، واستمتع ببساطة تحويل Word إلى markdown!

---

![مخطط يوضح عملية تحويل Word إلى Markdown](image.png "مخطط إنشاء markdown من Word")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}