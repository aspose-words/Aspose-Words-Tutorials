---
category: general
date: 2026-03-21
description: إنشاء مجلد الأصول أثناء تحويل ملف DOCX إلى Markdown. تعلّم كيفية استخراج
  الصور من Word وحفظ Word كملف Markdown باستخدام C#.
draft: false
keywords:
- create assets folder
- convert docx to markdown
- extract images from word
- extract embedded images
- save word as markdown
language: ar
og_description: إنشاء مجلد الأصول أثناء تحويل ملف DOCX إلى Markdown. يوضح هذا الدرس
  كيفية استخراج الصور من Word وحفظ Word كـ Markdown باستخدام C#.
og_title: إنشاء مجلد الأصول وتحويل DOCX إلى Markdown – دليل كامل
tags:
- Aspose.Words
- C#
- Document Conversion
title: إنشاء مجلد الأصول وتحويل DOCX إلى Markdown باستخدام Aspose.Words
url: /ar/net/programming-with-markdownsaveoptions/create-assets-folder-and-convert-docx-to-markdown-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مجلد الأصول وتحويل DOCX إلى Markdown باستخدام Aspose.Words

هل احتجت يوماً إلى **إنشاء مجلد الأصول** عند تحويل ملف Word إلى Markdown؟ لست وحدك—المطورون يسألون باستمرار كيف يمكن الحفاظ على تنظيم الصور أثناء *تحويل docx إلى markdown*. الخبر السار هو أن Aspose.Words يوفر لك طريقة نظيفة وبرمجية للقيام بالأمرين في خطوة واحدة.

في هذا الدرس سنستعرض العملية بالكامل: تحميل ملف `.docx`، تكوين مُصدّر Markdown، استخراج الصور المضمّنة، وأخيراً حفظ النتيجة كملف `.md` يشير إلى دليل `assets`. في النهاية ستحصل على مقتطف قابل لإعادة الاستخدام يقوم *باستخراج الصور من Word* و*بحفظ Word كـ markdown* دون أي نسخ‑لصق يدوي.

## ما ستحتاجه

- **Aspose.Words for .NET** (الإصدار الأخير، على سبيل المثال، 24.10).  
- بيئة تطوير .NET (Visual Studio، Rider، أو VS Code).  
- ملف `input.docx` تجريبي يحتوي على صورة واحدة على الأقل—وإلا لن ترى خطوة *extract embedded images* تعمل.

لا توجد مكتبات طرف ثالث أخرى مطلوبة؛ كل شيء موجود داخل Aspose.Words.

---

## إنشاء مجلد الأصول وإعداد تحويل Markdown

أول شيء نريده هو مجلد مخصص حيث ستهبط كل صورة يتم استخراجها من مستند Word. فكر فيه كدلو “assets” الذي تراه غالباً في مولّدات المواقع الثابتة. سنترك Aspose.Words يحدد اسم الملف، ثم نضيف مسار المجلد في البداية.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// 1️⃣ Load the source Word document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// 2️⃣ Prepare Markdown save options with a callback that decides where resources go
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new ResourceSavingCallback(info =>
    {
        // 👉 Define the folder that will hold every extracted image
        string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
        Directory.CreateDirectory(assetsFolder); // creates it if it doesn't exist

        // 👉 Tell Aspose to place the current resource inside that folder
        info.FileName = Path.Combine(assetsFolder, info.FileName);
    })
};
```

> **لماذا رد نداء؟**  
> الـ `ResourceSavingCallback` يُطلق لكل كائن مضمّن (صور، كائنات OLE، إلخ). من خلال اعتراضه يمكننا **استخراج الصور من Word** مباشرةً، بدلاً من حفظها في مكان آخر ونقلها لاحقاً. هذا يجعل خطوة *save word as markdown* ذرية ويقلل من عبء الإدخال/الإخراج.

---

## الخطوة 1: تحميل مستند DOCX

قبل أن نتمكن من *convert docx to markdown*، نحتاج إلى كائن `Document`. القالب (المنشئ) يقبل مساراً، أو تدفقاً، أو حتى مصفوفة بايت—اختر ما يناسب سير عملك.

```csharp
// Example using a relative path; adjust for your environment
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **نصيحة:** إذا كنت تعالج التحميلات في واجهة ويب API، مرّر الـ `Stream` المرفوع مباشرة لتجنب كتابة ملف مؤقت.

---

## الخطوة 2: تكوين MarkdownSaveOptions – قلب عملية الاستخراج

`MarkdownSaveOptions` يمنحك تحكمًا دقيقًا في سلوك التحويل. أهم خاصية لهدفنا هي `ResourceSavingCallback`، التي قمنا بإعدادها بالفعل. يمكنك أيضًا تعديل تنسيق الصورة، نمط الرابط، وأكثر.

```csharp
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    // Ensure images are saved as PNG by default (you can change this)
    ImageSavingFormat = ImageSaveOptions.SaveFormat.Png,

    // The callback defined earlier handles the assets folder creation
    ResourceSavingCallback = new ResourceSavingCallback(info =>
    {
        string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
        Directory.CreateDirectory(assetsFolder);
        info.FileName = Path.Combine(assetsFolder, info.FileName);
    })
};
```

> **ماذا لو شاركت صورتان نفس الاسم؟**  
> Aspose يضيف تلقائيًا لاحقة رقمية (`image.png`, `image_1.png`, …) لذا لن تفقد أي ملفات.

---

## الخطوة 3: تعريف مجلد الأصول ومعالجة مسارات الصور

يعمل رد النداء *مرة واحدة لكل مورد*. داخلها نقوم بـ:

1. بناء المسار المطلق إلى مجلد `assets` باستخدام `Path.Combine`.  
2. استدعاء `Directory.CreateDirectory`—هذا آمن للتنفيذ المتكرر؛ يتم إنشاء المجلد فقط في أول استدعاء.  
3. استبدال `info.FileName` بالمسار الكامل، لضمان أن كاتب Markdown يكتب الرابط النسبي الصحيح.

```csharp
ResourceSavingCallback = new ResourceSavingCallback(info =>
{
    string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
    Directory.CreateDirectory(assetsFolder);
    info.FileName = Path.Combine(assetsFolder, info.FileName);
})
```

> **نصيحة احترافية:** إذا كنت تحتاج أن يشير ملف Markdown إلى الصور باستخدام عنوان URL صديق للويب (مثال، `/static/assets/`)، استبدل `Path.Combine` بسلسلة تُنشئ عنوان URL النسبي المطلوب.

---

## الخطوة 4: حفظ المستند كـ Markdown

الآن بعد ربط كل شيء، السطر النهائي هو `Save` بسيط. Aspose سيتجول عبر شجرة Word DOM، يكتب صيغة Markdown إلى `output.md`، ويضع كل صورة في دليل `assets` الذي أنشأناه.

```csharp
// 5️⃣ Perform the conversion – this writes both the .md file and the images
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

عند انتهاء العملية سترى بنية مجلد مشابهة لـ:

```
YOUR_DIRECTORY/
├─ input.docx
├─ output.md
└─ assets/
   ├─ image1.png
   └─ image2.png
```

*الشكل 1: تخطيط المجلد بعد التحويل (نص بديل: “create assets folder diagram”).*  

ملف Markdown سيحتوي على روابط مثل `![](assets/image1.png)`، وهو بالضبط ما تتوقعه معظم مولّدات المواقع الثابتة.

---

## مثال كامل يعمل

فيما يلي برنامج جاهز للنسخ واللصق يمكنك تشغيله كتطبيق وحدة تحكم. استبدل `YOUR_DIRECTORY` بالمسار الذي يحتوي على ملف المصدر الخاص بك.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

class Program
{
    static void Main()
    {
        // 👉 Step 1 – Load the DOCX you want to convert
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 👉 Step 2 – Set up Markdown options and the assets folder callback
        MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
        {
            // Optional: force PNG output for all images
            ImageSavingFormat = ImageSaveOptions.SaveFormat.Png,

            // This callback runs for each extracted resource (image, etc.)
            ResourceSavingCallback = new ResourceSavingCallback(info =>
            {
                // 👉 Define where the extracted images will live
                string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
                Directory.CreateDirectory(assetsFolder);

                // 👉 Save each image inside that folder
                info.FileName = Path.Combine(assetsFolder, info.FileName);
            })
        };

        // 👉 Step 3 – Save as Markdown; assets are created automatically
        document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);

        // 🎉 Done! Check YOUR_DIRECTORY for output.md and the assets folder.
    }
}
```

### النتيجة المتوقعة

- `output.md` يحتوي على نص Markdown يعكس عناوين Word الأصلية، القوائم النقطية، والجداول.  
- كل صورة من `input.docx` تظهر كـ `![](assets/<imageName>.png)` داخل ملف Markdown.  
- مجلد `assets` يحتوي على ملفات PNG الفعلية، جاهزة لتُقدّم من قبل أي مضيف موقع ثابت.

---

## أسئلة شائعة وحالات خاصة

| السؤال | الإجابة |
|----------|--------|
| **ماذا لو كان الـ DOCX لا يحتوي على صور؟** | رد النداء ببساطة لا يُطلق أبداً، لذا يظل مجلد `assets` فارغاً. لا ضرر. |
| **هل يمكنني تغيير تنسيق الصورة إلى JPEG؟** | نعم—قم بتعيين `ImageSavingFormat = ImageSaveOptions.SaveFormat.Jpeg` داخل `MarkdownSaveOptions`. |
| **هل أحتاج إلى تنظيف مجلد الأصول في عمليات التشغيل المتتالية؟** | من الأفضل حذف أو استبدال الملفات القديمة إذا كنت تُعيد إنشاء نفس ملف Markdown، وإلا قد تتراكم الصور اليتيمة. |
| **كيف يعمل الربط النسبي على أنظمة تشغيل مختلفة؟** | لأننا نستخدم `Path.Combine` للمسار الفعلي وAspose يكتب رابطًا *نسبيًا* (`assets/image.png`)، يعمل Markdown على Windows وmacOS وLinux على حد سواء. |
| **هل يمكنني تضمين مجلد الأصول داخل ملف zip؟** | بالتأكيد—بعد التحويل قم بضغط `output.md` مع دليل `assets`. تظل روابط Markdown صالحة طالما تم الحفاظ على بنية المجلد. |

---

## الخطوات التالية

الآن بعد أن عرفت كيفية **إنشاء مجلد الأصول**، **تحويل docx إلى markdown**، و**استخراج الصور من Word**، قد ترغب في استكشاف:

- **تخصيص نمط Markdown** – قم بتبديل `ExportHeadersAsBold`، `ExportTableHeaders` وغيرها من العلامات في `MarkdownSaveOptions`.  
- **معالجة دفعة** – حلق عبر دليل يحتوي على ملفات `.docx` وأنشئ مجموعة مطابقة من أزواج Markdown/asset.  
- **التكامل مع مولّدات المواقع الثابتة** مثل Hugo أو Jekyll، التي تتوقع تخطيط المجلد الدقيق الذي أنشأناه للتو.  

إذا كنت مهتمًا بسيناريوهات أكثر تقدماً—مثل الحفاظ على حواشي Word أو معالجة كائنات OLE المضمّنة—اطلع على وثائق Aspose.Words الرسمية (ابحث عن “MarkdownSaveOptions” و“ResourceSavingCallback”).

---

## الخلاصة

لقد استعرضنا للتو حلاً كاملاً من البداية إلى النهاية يقوم **بإنشاء مجلد الأصول**، **باستخراج الصور المضمّنة**، و**بحفظ مستند Word كـ Markdown** باستخدام Aspose.Words لـ .NET. النقطة الأساسية هي أن `ResourceSavingCallback` يمنحك تحكمًا كاملاً في مكان وضع كل صورة، مما يتيح لك الحفاظ على نظافة Markdown وجاهزيته للنشر.

جرّبه، عدّل تنسيق الصورة، أو غلف المنطق في خدمة قابلة لإعادة الاستخدام—أياً كان اختيارك، لديك الآن أساس قوي لأي سير عمل *convert docx to markdown* يحتاج إلى *extract images from word* و*save word as markdown*.

برمجة سعيدة! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}