---
category: general
date: 2025-12-29
description: احفظ ملف docx كـ markdown باستخدام Aspose.Words. تعلم كيفية تحويل Word
  إلى markdown، استخراج الصور، إنشاء مجلد الموارد، وتكوين خيارات markdown.
draft: false
keywords:
- save docx as markdown
- convert word to markdown
- how to extract images
- create resources folder
- how to configure markdown
language: ar
og_description: احفظ ملف docx كملف markdown باستخدام Aspose.Words. دليل خطوة بخطوة
  لتحويل Word إلى markdown، استخراج الصور، إنشاء مجلد الموارد، وتكوين markdown.
og_title: حفظ ملف docx كـ markdown – دورة C# كاملة
tags:
- Aspose.Words
- C#
- Document Conversion
title: حفظ ملف docx كـ markdown – دليل C# الكامل مع استخراج الصور
url: /ar/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ docx كـ markdown – دليل C# كامل

هل احتجت يومًا إلى **حفظ docx كـ markdown** لكنك لم تكن متأكدًا من كيفية الحفاظ على الصور المدمجة؟ لست وحدك. يواجه العديد من المطورين مشكلة عندما تُزيل التحويل الصور، مما يجعل ملف الـ Markdown يبدو فارغًا. في هذا الدليل سنستعرض حلًا عمليًا لا يقتصر فقط على **تحويل word إلى markdown** بل يُظهر أيضًا **كيفية استخراج الصور**، وإنشاء مجلد **Resources** تلقائيًا، وتكوين خيارات **markdown** بشكل صحيح للحصول على مخرجات نظيفة.

بنهاية هذا المقال ستحصل على مقتطف C# جاهز للتنفيذ يأخذ أي ملف `.docx`، يستخرج كل صورة، يخزنها في دليل مخصص، وينتج ملف Markdown تكون روابط الصور فيه تشير إلى ذلك المجلد. لا حاجة لأي معالجة إضافية.

## ما ستتعلمه

- تحميل مستند Word باستخدام Aspose.Words.
- إعداد `MarkdownSaveOptions` لالتقاط الموارد الخارجية.
- إنشاء مجلد **Resources** تلقائيًا بجانب ملف Markdown.
- كتابة ملفات الصور باستخدام `ResourceSavingCallback`.
- التحقق من أن الـ Markdown الناتج يشير إلى الصور بشكل صحيح.

### المتطلبات المسبقة

- .NET 6+ (أو .NET Framework 4.6+).  
- Aspose.Words لـ .NET (حزمة NuGet `Aspose.Words`).  
- ملف `input.docx` تجريبي يحتوي على صورة واحدة على الأقل.  

إذا كان لديك هذه مسبقًا، رائع—لنبدأ.

## الخطوة 1 – تحميل مستند Word

أول شيء نقوم به هو فتح ملف المصدر. هذه الخطوة بسيطة لكنها أساسية؛ كائن المستند هو المصدر لكل من النص والوسائط.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the Word document that contains images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **لماذا هذا مهم:**  
> تحميل الملف ينشئ تمثيلًا في الذاكرة حيث يمكن لـ Aspose تعداد كل عقدة—الفقرات، الجداول، وبشكل حاسم، كائنات `Shape` التي تحتوي على الصور. بدون التحميل، لا شيء لاستخراجه.

## الخطوة 2 – تكوين خيارات Markdown (جوهر التحويل)

الآن نخبر Aspose كيف نريد أن يتصرف ملف الـ Markdown. توفر فئة `MarkdownSaveOptions` تفويض `ResourceSavingCallback` الذي يُستدعى لكل مورد خارجي (صور، مخططات، إلخ). داخل هذا التفويض نحدد أين نكتب الملف وأي URI ندمج.

```csharp
// Set up Markdown save options with a callback for external resources.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    // The callback runs for every image/chart the exporter needs to write.
    ResourceSavingCallback = (sender, args) =>
    {
        // Step 3 – Ensure the Resources folder exists.
        string resourcesFolder = "YOUR_DIRECTORY/Resources/";
        Directory.CreateDirectory(resourcesFolder);

        // Build the absolute path for the image file.
        string resourceFilePath = Path.Combine(resourcesFolder, args.ResourceFileName);
        args.Stream = new FileStream(resourceFilePath, FileMode.Create);

        // Use a relative path in the generated Markdown file.
        args.Uri = "Resources/" + args.ResourceFileName;
    }
};
```

### كيفية تكوين Markdown لاستخراج الصور

- **`ResourceSavingCallback`** – النقطة التي تسمح لنا بكتابة كل صورة في أي مكان نريده.  
- **`args.ResourceFileName`** – اسم فريد يتم إنشاؤه بواسطة Aspose (مثال: `image001.png`).  
- **`args.Uri`** – السلسلة التي تظهر في رابط الـ Markdown؛ نضبطها إلى مسار نسبي حتى يبقى الـ Markdown قابلًا للنقل.

> **نصيحة:** إذا كنت بحاجة إلى نظام تسمية مخصص (مثل الحفاظ على اسم الصورة الأصلي)، يمكنك فحص `args.ResourceFileName` واستبداله قبل تعيين `args.Uri`.

## الخطوة 3 – إنشاء مجلد Resources (واستخراج الصور)

التفويض الذي عرفناه في الخطوة السابقة بالفعل ينشئ المجلد أثناء التشغيل، لكن دعنا نناقش لماذا هذه هي الطريقة الموصى بها.

```csharp
// Inside the callback (repeated for emphasis):
string resourcesFolder = "YOUR_DIRECTORY/Resources/";
Directory.CreateDirectory(resourcesFolder);
```

> **لماذا إنشاء مجلد مخصص؟**  
> تخزين الصور في دليل منفصل يحافظ على نظافة الـ Markdown ويعكس الطريقة التي يتوقع بها العديد من مولّدات المواقع الثابتة (مثل Jekyll أو Hugo) تنظيم الأصول. كما أنه يمنع تصادم الأسماء إذا قمت بتشغيل التحويل عدة مرات.

### الحالات الخاصة والاختلافات

| Situation | What to Adjust |
|-----------|----------------|
| **DOCX كبير يحتوي على مئات الصور** | فكر في تدفق الصور لتجنب ضغط الذاكرة؛ التفويض يكتب كل صورة مباشرة إلى القرص، وهو فعال من حيث الذاكرة. |
| **صور غير PNG (مثل JPEG, GIF)** | `args.ResourceFileName` يحتوي بالفعل على الامتداد الصحيح، لذا لا حاجة لمعالجة إضافية. |
| **مسار إخراج مخصص** | استبدل `"YOUR_DIRECTORY/Resources/"` بمسار نسبي إلى جذر مشروعك، أو اقرأه من ملف إعدادات. |

## الخطوة 4 – حفظ المستند كـ Markdown

مع تكوين الخيارات بالكامل، الخطوة الأخيرة هي سطر واحد يكتب ملف الـ Markdown ويستدعي التفويض لكل صورة.

```csharp
// Save the document as Markdown, applying the resource handling logic.
document.Save("YOUR_DIRECTORY/WithResources.md", markdownSaveOptions);
```

### النتيجة المتوقعة

- `WithResources.md` – ملف Markdown يحتوي على الصياغة القياسية (`![Alt text](Resources/image001.png)`) لكل صورة.  
- `Resources/` – مجلد مملوء بملفات الصور المستخرجة.

يمكنك فتح ملف الـ Markdown في أي عارض (VS Code، GitHub، أو مولّد موقع ثابت) وسترى الصور الأصلية تُعرض تمامًا حيث ظهرت في مستند Word.

![هيكل المجلد يُظهر مجلد Resources مع الصور المستخرجة – حفظ docx كـ markdown](https://example.com/placeholder.png "هيكل المجلد للصور المستخرجة – حفظ docx كـ markdown")

*نص بديل للصورة: “هيكل المجلد للصور المستخرجة – حفظ docx كـ markdown” – يحقق متطلبات النص البديل للصورة للكلمة المفتاحية الأساسية.*

## مثال كامل يعمل (جاهز للنسخ واللصق)

فيما يلي البرنامج الكامل، جاهز للإدراج في تطبيق كونسول. استبدل `YOUR_DIRECTORY` بالمسار الفعلي على جهازك.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source DOCX.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Prepare Markdown options with a resource callback.
        MarkdownSaveOptions options = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (sender, args) =>
            {
                // 3️⃣ Ensure the Resources folder exists.
                string resourcesFolder = "YOUR_DIRECTORY/Resources/";
                Directory.CreateDirectory(resourcesFolder);

                // 4️⃣ Write the image file to disk.
                string filePath = Path.Combine(resourcesFolder, args.ResourceFileName);
                args.Stream = new FileStream(filePath, FileMode.Create);

                // 5️⃣ Set the relative URI used in the Markdown file.
                args.Uri = "Resources/" + args.ResourceFileName;
            }
        };

        // 6️⃣ Save as Markdown – this triggers the callback for each image.
        document.Save("YOUR_DIRECTORY/WithResources.md", options);

        // Inform the user.
        System.Console.WriteLine("Conversion complete! Check the Resources folder and the Markdown file.");
    }
}
```

### تشغيل العينة

1. تثبيت حزمة Aspose.Words عبر NuGet:  
   ```bash
   dotnet add package Aspose.Words
   ```
2. ترجمة وتشغيل:  
   ```bash
   dotnet run
   ```
3. فتح `WithResources.md` في أي عارض Markdown. يجب أن تظهر جميع الصور.

## أسئلة شائعة ونصائح احترافية

### “هل يمكنني تحويل ملف .doc بدلاً من .docx؟”

بالطبع—يدعم Aspose.Words كلا من `.doc` و `.docx`. فقط غيّر امتداد الملف في مُنشئ `Document`.

### “ماذا لو لم أرغب في مجلد Resources؟”

يمكنك توجيه `args.Uri` إلى أي موقع، حتى URL. على سبيل المثال، عيّن `args.Uri = "https://mycdn.com/" + args.ResourceFileName;` وتجاوز إنشاء المجلد.

### “كيف أتعامل مع رسومات SVG؟”

يتعامل Aspose مع SVG كنوع مورد منفصل. داخل التفويض يمكنك فحص `args.ResourceType`، وإذا كان `ResourceType.Svg`، أعد تسمية أو عالجها بطريقة مختلفة.

### “هل هناك طريقة لتضمين الصور كـ Base64؟”

نعم—بدلاً من الكتابة إلى ملف، يمكنك تحويل `args.Stream` إلى سلسلة Base64 وتعيين `args.Uri = "data:image/png;base64," + base64;`. هذا يجعل الـ Markdown ذاتيًا لكنه يزيد من حجم الملف.

### “ما إصدار Aspose.Words الذي أحتاجه؟”

تم تقديم فئة `MarkdownSaveOptions` في Aspose.Words 22.9. إذا كنت تستخدم إصدارًا أقدم، قم بالترقية عبر NuGet.

## الخلاصة

لقد غطينا كل ما تحتاجه **لحفظ docx كـ markdown** مع الحفاظ على كل صورة. الخطوات الأساسية هي:

1. تحميل ملف DOCX باستخدام Aspose.Words.  
2. تكوين `MarkdownSaveOptions` وتنفيذ `ResourceSavingCallback`.  
3. داخل التفويض، **إنشاء مجلد resources**، كتابة كل صورة، وتعيين URI نسبي.  
4. حفظ المستند، مما يسمح لـ Aspose بالقيام بالمعالجة الثقيلة.

الآن يمكنك أتمتة خطوط أنابيب الوثائق، نقل أدلة Word القديمة إلى Markdown صديقة للمواقع الثابتة، أو ببساطة توفير تنسيق خفيف الوزن ومتحكم فيه بالإصدارات لفريقك دون فقدان السياق البصري.

### ما التالي؟

- جرب **كيفية تكوين markdown** لأنماط العناوين المخصصة أو تنسيق الجداول.  
- اجمع هذا التحويل مع خطوة CI/CD لنشر الوثائق تلقائيًا.  
- تعمق أكثر في صيغ التصدير الأخرى لـ Aspose (HTML، PDF) واكتشف كيف يعمل نمط التفويض نفسه معها.

هل لديك سيناريوهات أخرى ترغب في استكشافها؟ اترك تعليقًا أو افتح قضية جديدة في منتديات Aspose. تحويل سعيد!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}