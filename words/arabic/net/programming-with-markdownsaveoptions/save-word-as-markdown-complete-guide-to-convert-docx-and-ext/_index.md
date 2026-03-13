---
category: general
date: 2026-03-13
description: احفظ مستند Word كملف Markdown وحوّل DOCX إلى Markdown مع استخراج الصور.
  تعلّم كيفية استخراج الصور من DOCX باستخدام Aspose.Words في C#.
draft: false
keywords:
- save word as markdown
- convert docx to markdown
- extract images from docx
- how to extract images
- extract embedded images word
language: ar
og_description: احفظ مستند Word كـ Markdown في C#. يوضح هذا الدليل كيفية تحويل DOCX
  إلى Markdown واستخراج الصور، مع توفير حل جاهز للتنفيذ.
og_title: حفظ ملف وورد كماركداون – تحويل DOCX واستخراج الصور
tags:
- Aspose.Words
- C#
- Markdown
title: حفظ ملف Word كـ Markdown – دليل شامل لتحويل DOCX واستخراج الصور
url: /ar/net/programming-with-markdownsaveoptions/save-word-as-markdown-complete-guide-to-convert-docx-and-ext/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ Word كـ Markdown – دليل كامل لتحويل DOCX واستخراج الصور

هل احتجت يومًا إلى **حفظ Word كـ markdown** لكنك لم تكن متأكدًا من كيفية الحفاظ على الصور سليمة؟ لست وحدك. يواجه العديد من المطورين مشكلة عندما تحتوي ملفات DOCX الخاصة بهم على رسومات مدمجة وتقوم المحولات البسيطة بإنتاج مجموعة من الروابط المكسورة.  

في هذا الدرس سنستعرض حلًا عمليًا **يحوّل DOCX إلى markdown** **ويستخرج** كل صورة إلى مجلد تتحكم فيه. في النهاية ستحصل على ملف `.md` نظيف، ومجلد `markdown_resources` منظم، وفهم قوي لسبب كون نهج الـ callback هو الأكثر موثوقية للتعامل مع الموارد.

> **نصيحة احترافية:** النمط نفسه يعمل مع CSS أو الخطوط أو أي مورد خارجي قد تُصدره Aspose.Words أثناء عملية الحفظ.

![مخطط تدفق تحويل حفظ Word كـ Markdown](conversion-diagram.png "مخطط تدفق التحويل")

## ما ستتعلمه

- كيفية **حفظ Word كـ markdown** باستخدام Aspose.Words for .NET.
- الخطوات الدقيقة **لتحويل docx إلى markdown** مع الحفاظ على الصور.
- تنفيذ قابل لإعادة الاستخدام لـ `IResourceSavingCallback` يقوم **باستخراج الصور من docx**.
- المشكلات الشائعة (مثل أسماء الملفات المكررة، المجلدات المفقودة) وكيفية تجنّبها.
- كيف يبدو markdown المُولّد وأين تُحفظ الصور.

ستحتاج إلى نسخة حديثة من **Aspose.Words for .NET** (تم اختبار الدليل مع الإصدار 24.12) وبيئة تشغيل .NET 6+. لا توجد مكتبات طرف ثالث أخرى مطلوبة.

---

## المتطلبات المسبقة

| المتطلب | لماذا يهم |
|-------------|----------------|
| Aspose.Words for .NET (NuGet `Aspose.Words`) | يوفر الفئة `Document` و `MarkdownSaveOptions`. |
| .NET 6 أو أحدث | يضمن عمل ميزات اللغة مثل عبارات `using` دون الحاجة إلى إعدادات إضافية. |
| ملف DOCX يحتوي على صور (مثال: `Images.docx`) | المصدر الذي سنحوّله ومنه سنستخرج الصور. |
| صلاحية كتابة إلى مجلد الإخراج | يقوم الـ callback بكتابة ملفات الصور؛ بدون إذن ستواجه استثناء. |

إذا كان لديك هذه المتطلبات بالفعل، رائع—لنبدأ.

---

## الخطوة 1: تحميل ملف DOCX المصدر – نقطة البداية لحفظ Word كـ Markdown

أول شيء نفعله هو فتح مستند Word. تقوم Aspose.Words بقراءة الملف إلى الذاكرة، مع الحفاظ على جميع البُنى الداخلية (الفقرات، الجداول، الصور، إلخ).

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the DOCX that contains images.
Document sourceDoc = new Document("YOUR_DIRECTORY/Images.docx");
```

> **لماذا هذا مهم:** تحميل الملف مبكرًا يتيح لنا فحص محتوياته (مثال: `sourceDoc.GetChildNodes(NodeType.Shape, true)`) إذا احتجنا إلى تتبع الأخطاء المتعلقة بالصور المفقودة.

---

## الخطوة 2: تكوين خيارات حفظ Markdown مع Callback لحفظ الصور

عند كتابة Aspose.Words لملف markdown، قد تحتاج إلى تخزين موارد خارجية مثل الصور. من خلال إرفاق `ResourceSavingCallback`، نحصل على سيطرة كاملة على مكان وضع تلك الملفات وما هو الاسم الذي ستحصل عليه.

```csharp
// Prepare markdown options and tell Aspose.Words to use our callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // The callback fires for every image, CSS file, etc.
    ResourceSavingCallback = new ImageSavingCallback()
};
```

> **كيفية استخراج الصور:** يتلقى الـ callback كائن `ResourceSavingArgs` يحتوي على تدفق الصورة، اسم الملف الأصلي، وفهرس. يمكننا إعادة تسمية الملف، نقله، أو حتى تخطي حفظه تمامًا.

---

## الخطوة 3: حفظ المستند كـ Markdown – جوهر حفظ Word كـ Markdown

الآن نستدعي `Document.Save`. ستستدعي المكتبة الـ callback الخاص بنا لكل صورة، وتكتب ملف الصورة في المكان الذي حددناه، وأخيرًا تُنتج ملف markdown يحتوي على روابط `![]()` صحيحة.

```csharp
// Execute the conversion. The markdown file will reference the extracted images.
sourceDoc.Save("YOUR_DIRECTORY/DocWithImages.md", mdOptions);
```

في هذه المرحلة يجب أن ترى شيئين في `YOUR_DIRECTORY`:

1. `DocWithImages.md` – تمثيل markdown للملف Word الأصلي.
2. مجلد `markdown_resources` – مجموعة من ملفات `img_0.png`، `img_1.jpg`، … 

---

## الخطوة 4: تنفيذ Callback لحفظ الصور – كيفية استخراج الصور من DOCX

فيما يلي فئة الـ callback الكاملة. تقوم بإنشاء مجلد إذا لزم الأمر، تبني اسم ملف فريد، تكتب تدفق الصورة، ثم تخبر Aspose.Words باستخدام اسم ملفنا (عن طريق تعيين `args.FileName`) وتجاوز حفظه الافتراضي (`args.Stream = null`).

```csharp
public class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Ensure the resources folder exists.
        string resourcesFolder = "YOUR_DIRECTORY/markdown_resources";
        Directory.CreateDirectory(resourcesFolder);

        // 2️⃣ Build a unique name – img_0.png, img_1.jpg, etc.
        string imageFileName = Path.Combine(
            resourcesFolder,
            $"img_{args.ImageIndex}{Path.GetExtension(args.FileName)}");

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = new FileStream(imageFileName, FileMode.Create))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Tell the markdown writer to reference the new name.
        args.FileName = Path.GetFileName(imageFileName);
        args.Stream = null; // Prevent default saving – we already handled it.
    }
}
```

### لماذا يعمل هذا

- **أسماء ملفات حتمية** – استخدام `args.ImageIndex` يضمن التفرد حتى لو كان DOCX الأصلي يحتوي على أسماء مكررة.
- **عزل المجلد** – جميع الأصول المستخرجة تعيش تحت `markdown_resources`، مما يحافظ على تنظيم مشروعك.
- **الأداء** – نقوم بنسخ التدفق مباشرة؛ لا توجد تخزين مؤقت إضافي أو معالجة للصور، لذا يبقى التحويل سريعًا.

---

## الخطوة 5: التحقق من النتيجة – كيف يبدو markdown

افتح `DocWithImages.md` في أي محرر. يجب أن ترى شيئًا مشابهًا لـ:

```markdown
# Sample Document

Here is an illustration:

![](markdown_resources/img_0.png)

Another picture appears below:

![](markdown_resources/img_1.jpg)
```

إذا فتحت ملف markdown في عارض يحترم المسارات النسبية (معاينة VS Code، GitHub، إلخ)، ستظهر الصور بشكل صحيح.

### فحص سريع للتأكد

```bash
# On Linux/macOS
cat YOUR_DIRECTORY/DocWithImages.md | grep -E '\!\[.*\]\(markdown_resources/img_.*\)'
```

يجب أن ترى سطرًا واحدًا لكل صورة؛ يجب أن يتطابق العدد مع عدد الصور المدمجة أصلاً في `Images.docx`.

---

## أسئلة شائعة وحالات خاصة

### ماذا لو كان DOCX يحتوي على رسومات SVG أو EMF؟

تحول Aspose.Words معظم صيغ المتجهات إلى PNG تلقائيًا. سيظل الـ callback يتلقى تدفقًا، وستكون امتداد الملف `.png`. لا حاجة إلى أي كود إضافي.

### كيف أغيّر اسم مجلد الإخراج؟

ما عليك سوى تعديل المتغير `resourcesFolder` في `ImageSavingCallback`. تذكر الحفاظ على نفس المرجع النسبي (`args.FileName = Path.GetFileName(imageFileName)`) حتى تظل روابط markdown صحيحة.

### هل يمكنني تخطي حفظ بعض الصور (مثل الكبيرة جدًا)؟

نعم. افحص `args.Stream.Length` داخل الـ callback. إذا تجاوز حدًا معينًا، يمكنك إما إعادة تسميته إلى عنصر نائب أو تعيين `args.Cancel = true` لتجاهله تمامًا.

```csharp
if (args.Stream.Length > 5 * 1024 * 1024) // >5 MB
{
    args.Cancel = true; // Image will be omitted from markdown.
    return;
}
```

### هل يعمل هذا النهج مع أنواع موارد أخرى مثل CSS؟

بالطبع. يتم استدعاء نفس الـ callback لأي مورد خارجي. يمكنك التفرع بناءً على `args.ContentType` لمعالجة CSS أو الخطوط أو الفيديوهات بشكل مختلف.

---

## مثال كامل جاهز للنسخ واللصق

فيما يلي برنامج مستقل يمكنك وضعه في تطبيق console. عدّل العنصر النائب `YOUR_DIRECTORY` إلى مسار مطلق أو نسبي على جهازك.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main()
        {
            // ① Load the source DOCX that contains images.
            Document sourceDoc = new Document("YOUR_DIRECTORY/Images.docx");

            // ② Configure markdown options with our callback.
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // ③ Save as markdown – images will be stored by the callback.
            sourceDoc.Save("YOUR_DIRECTORY/DocWithImages.md", mdOptions);

            // ④ Inform the user.
            System.Console.WriteLine("Conversion complete! Check the markdown file and the markdown_resources folder.");
        }
    }

    // ⑤ Callback that extracts each image to a custom folder.
    public class ImageSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourcesFolder = "YOUR_DIRECTORY/markdown_resources";
            Directory.CreateDirectory(resourcesFolder);

            string imageFileName = Path.Combine(
                resourcesFolder,
                $"img_{args.ImageIndex}{Path.GetExtension(args.FileName)}");

            using (FileStream fileStream = new FileStream(imageFileName, FileMode.Create))
            {
                args.Stream.CopyTo(fileStream);
            }

            args.FileName = Path.GetFileName(imageFileName);
            args.Stream = null; // Skip default saving.
        }
    }
}
```

شغّل البرنامج، افتح markdown المُولّد، وسترى جميع الصور معروضة تمامًا حيث ظهرت في ملف Word الأصلي.

---

## الخلاصة

لقد غطينا للتو **كيفية حفظ Word كـ markdown** مع **استخراج الصور من docx** باستخدام نمط callback نظيف. الفكرة الأساسية هي أن `IResourceSavingCallback` يمنحك سيطرة كاملة على كل ملف خارجي، مما يجعل التحويل موثوقًا لأي خط أنابيب إنتاج.

في مثال واحد قابل للنسخ واللصق قمنا بـ:

1. تحميل DOCX يحتوي على صور.
2. تكوين `MarkdownSaveOptions` مع `ImageSavingCallback` مخصص.
3. حفظ المستند كـ markdown، مما سمح للـ callback بكتابة كل صورة إلى `markdown_resources`.
4. التحقق من النتيجة ومناقشة كيفية تعديل العملية لحالات خاصة.

من هنا يمكنك:

- **تحويل docx إلى markdown** بالجملة عبر التكرار على مجلد.
- **إعادة تسمية الصور** بناءً على التسميات الأصلية لتحسين SEO.
- **دمج مع مولدات المواقع الثابتة** (مثل Hugo، Jekyll) بنقل مجلد markdown إلى شجرة المحتوى الخاصة بك.
- **توسيع الـ callback** لاستخراج الخطوط المدمجة أو CSS إذا احتجت إلى تصدير HTML مكتمل ذاتيًا.

لا تتردد في التجربة—ربما تستبدل نظام تسمية الصور بـ GUIDs لتحقيق تفرد مطلق، أو تضيف سطر تسجيل لتتبع كل مورد محفوظ. السماء هي الحد عندما تتحكم في عملية الحفظ.

برمجة سعيدة، ولتظهر markdown دائمًا بالصور الصحيحة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}