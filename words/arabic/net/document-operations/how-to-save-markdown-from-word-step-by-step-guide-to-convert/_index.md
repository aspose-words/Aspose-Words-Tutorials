---
category: general
date: 2025-12-18
description: تعلم كيفية حفظ ملفات ماركداون من مستند Word وتحويل Word إلى ماركداون
  مع استخراج الصور من ملفات Word. يوضح هذا الدرس كيفية استخراج الصور وكيفية تحويل
  ملفات docx باستخدام C#.
draft: false
keywords:
- how to save markdown
- convert word to markdown
- extract images from word
- how to extract images
- how to convert docx
language: ar
og_description: كيفية حفظ ملف ماركداون من ملف Word باستخدام C#. تحويل Word إلى ماركداون،
  استخراج الصور من Word، وتعلم كيفية تحويل docx مع مثال كامل للكود.
og_title: كيفية حفظ ماركداون – تحويل Word إلى ماركداون بسهولة
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: كيفية حفظ Markdown من Word – دليل خطوة بخطوة لتحويل Word إلى Markdown
url: /arabic/net/document-operations/how-to-save-markdown-from-word-step-by-step-guide-to-convert/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية حفظ Markdown – تحويل Word إلى Markdown مع استخراج الصور

هل تساءلت يومًا **كيف تحفظ markdown** من مستند Word دون فقدان أي من الصور المدمجة؟ لست وحدك. يحتاج العديد من المطورين إلى تحويل ملف `.docx` إلى markdown نظيف للمواقع الثابتة، أو خطوط أنابيب التوثيق، أو الملاحظات المتحكم فيها بالإصدار، ويرغبون أيضًا في الحفاظ على الصور الأصلية.  

في هذا الدرس ستتعرف بالضبط **كيف تحفظ markdown** باستخدام Aspose.Words for .NET، وتتعلم **كيفية تحويل word إلى markdown**، وتكتشف أفضل طريقة **لاستخراج الصور من word**. في النهاية ستحصل على برنامج C# جاهز للتنفيذ لا يحول ملف الـ docx فحسب، بل يخزن كل صورة في مجلد مخصص—دون الحاجة إلى النسخ واللصق اليدوي.

## المتطلبات المسبقة

- .NET 6+ (أو .NET Framework 4.7.2 وما أعلى)  
- حزمة NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- ملف `input.docx` تجريبي يحتوي على نص، عناوين، وعلى الأقل صورة واحدة  
- معرفة أساسية بـ C# وVisual Studio (أو أي بيئة تطوير تفضلها)  

إذا كان لديك كل ذلك، رائع—لننتقل مباشرة إلى الحل.

## نظرة عامة على الحل

سنقسم العملية إلى أربع قطع منطقية:

1. **تحميل المستند المصدر** – قراءة ملف `.docx` إلى الذاكرة.  
2. **تهيئة خيارات حفظ Markdown** – إخبار Aspose.Words أننا نريد مخرجات markdown.  
3. **تعريف رد نداء لحفظ الموارد** – هنا نُـ **استخراج الصور من word** ونضعها في المجلد الذي تختاره.  
4. **حفظ المستند كملف `.md`** – أخيرًا نكتب ملف markdown إلى القرص.

كل خطوة موضحة أدناه، مع مقتطفات شفرة يمكنك نسخها ولصقها في تطبيق Console.

![مثال على كيفية حفظ markdown](example.png "توضيح لكيفية حفظ markdown من Word")

## الخطوة 1: تحميل المستند المصدر

قبل أن يحدث أي تحويل، تحتاج المكتبة إلى كائن `Document` يمثل ملف Word الخاص بك.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Step 1: Load the source document
Document doc = new Document(@"C:\MyProjects\Docs\input.docx");
```

> **لماذا هذا مهم:** تحميل الملف يُنشئ نموذج DOM (Document Object Model) في الذاكرة يمكن لـ Aspose.Words استكشافه. إذا كان الملف مفقودًا أو معطوبًا، سيتم رمي استثناء، لذا تأكد من صحة المسار وإمكانية الوصول إلى الملف.

### نصيحة احترافية
ضع كود التحميل داخل كتلة `try/catch` إذا كنت تتوقع أن يُزود المستخدم بالملف. هذا يمنع تطبيقك من الانهيار عند مسار غير صالح.

## الخطوة 2: إنشاء خيارات حفظ Markdown

يمكن لـ Aspose.Words تصدير إلى صيغ متعددة. هنا نقوم بإنشاء `MarkdownSaveOptions`، وإذا رغبت، نضبط بعض الخصائص للحصول على مخرجات أنظف.

```csharp
// Step 2: Create Markdown save options
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    // Use GitHub-flavored markdown (adds tables, task lists, etc.)
    ExportImagesAsBase64 = false, // We'll handle images ourselves
    ExportHeadersFooters = false   // Usually not needed in markdown
};
```

> **لماذا هذا مهم:** ضبط `ExportImagesAsBase64` إلى `false` يخبر المكتبة *بعدم* تضمين الصور مباشرة في markdown. بدلاً من ذلك، ستستدعي `ResourceSavingCallback` التي نعرّفها في الخطوة التالية، مما يمنحنا التحكم الكامل في مكان حفظ الصور.

## الخطوة 3: تعريف رد نداء لتخزين الصور في مجلد مخصص

هذا هو جوهر **كيفية استخراج الصور** من ملف Word أثناء تحويله. يتلقى رد النداء كل مورد (صورة، خط، إلخ) أثناء معالجة الحفظ للمستند.

```csharp
// Step 3: Define a callback to store images in a custom folder
markdownSaveOptions.ResourceSavingCallback = (sender, args) =>
{
    // We only care about images; other resources (like fonts) can be ignored
    if (args.ResourceType == ResourceType.Image)
    {
        // Build a path relative to the markdown file location
        string imagesFolder = "CustomImages";

        // Ensure the folder exists
        if (!Directory.Exists(imagesFolder))
            Directory.CreateDirectory(imagesFolder);

        // Set the destination path for the current image
        args.DestinationPath = Path.Combine(imagesFolder, args.ResourceFileName);
    }
};
```

### الحالات الخاصة والنصائح

- **أسماء صور مكررة:** إذا شاركت صورتان نفس اسم الملف، سيضيف Aspose.Words لاحقة رقمية تلقائيًا. يمكنك أيضًا إضافة GUID لضمان التفرد.  
- **الصور الكبيرة:** للصور ذات الدقة العالية قد ترغب في تقليل حجمها الحفظ. أدرج خطوة تمهيدية باستخدام `System.Drawing` أو `ImageSharp` داخل رد النداء.  
- **أذونات المجلد:** تأكد من أن التطبيق يمتلك صلاحية كتابة إلى الدليل المستهدف، خاصةً عند التشغيل تحت IIS أو حساب خدمة مقيد.

## الخطوة 4: حفظ المستند كملف Markdown باستخدام الخيارات المكوَّنة

الآن كل شيء مُعد. استدعاء واحد سيُنتج ملف `.md` ومجلدًا مليئًا بالصور المستخرجة.

```csharp
// Step 4: Save the document as Markdown using the configured options
string outputPath = @"C:\MyProjects\Docs\output.md";
doc.Save(outputPath, markdownSaveOptions);
```

بعد اكتمال الحفظ ستجد:

- `output.md` يحتوي على نص markdown نظيف مع روابط صور مثل `![Image1](CustomImages/Image1.png)`  
- مجلد فرعي `CustomImages` بجوار ملف markdown يحمل كل صورة مستخرجة.

### التحقق من النتيجة

افتح `output.md` في عارض markdown (VS Code، GitHub، أو مولد موقع ثابت). يجب أن تُعرض الصور بشكل صحيح، ويجب أن يعكس التنسيق العناوين والقوائم والجداول الأصلية في Word.

## مثال كامل يعمل

فيما يلي البرنامج بالكامل، جاهز للترجمة. الصقه في مشروع Console App جديد وعدّل مسارات الملفات حسب الحاجة.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdown
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            string inputPath = @"C:\MyProjects\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure markdown options
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ExportImagesAsBase64 = false,
                ExportHeadersFooters = false
            };

            // 3️⃣ Callback to extract images
            mdOptions.ResourceSavingCallback = (sender, ev) =>
            {
                if (ev.ResourceType == ResourceType.Image)
                {
                    string imagesDir = "CustomImages";
                    if (!Directory.Exists(imagesDir))
                        Directory.CreateDirectory(imagesDir);

                    ev.DestinationPath = Path.Combine(imagesDir, ev.ResourceFileName);
                }
            };

            // 4️⃣ Save as markdown
            string outputPath = @"C:\MyProjects\Docs\output.md";
            doc.Save(outputPath, mdOptions);

            Console.WriteLine("Conversion complete! Markdown saved to:");
            Console.WriteLine(outputPath);
            Console.WriteLine("Images extracted to the 'CustomImages' folder.");
        }
    }
}
```

شغِّل البرنامج، افتح ملف markdown المُولد، وسترى أن **كيفية حفظ markdown** من Word أصبحت عملية بنقرة واحدة.

## الأسئلة المتكررة

**س: هل يعمل هذا مع ملفات .doc القديمة؟**  
ج: يمكن لـ Aspose.Words فتح صيغ `.doc` القديمة، لكن بعض التخطيطات المعقدة قد لا تُترجم بدقة. للحصول على أفضل النتائج، حوّل الملف إلى `.docx` أولاً.

**س: ماذا لو أردت تضمين الصور كـ Base64 بدلاً من ملفات منفصلة؟**  
ج: اضبط `ExportImagesAsBase64 = true` وتجاهل رد النداء. سيحتوي markdown على سلاسل `![alt](data:image/png;base64,…)`.

**س: هل يمكنني تخصيص صيغة الصورة (مثلاً فرض PNG)؟**  
ج: داخل رد النداء يمكنك فحص `ev.ResourceFileName` وتغيير الامتداد، ثم استخدام مكتبة معالجة صور للتحويل قبل كتابة الملف.

**س: هل هناك طريقة للحفاظ على أنماط Word (غامق، مائل، كود)؟**  
ج: المُصدِّر المدمج إلى markdown يطابق معظم تنسيقات Word الشائعة إلى صيغ markdown. للأنماط المخصصة قد تحتاج إلى معالجة ما بعد التحويل لملف `.md`.

## الأخطاء الشائعة وكيفية تجنّبها

- **مجلد الصور غير موجود** – أنشئ المجلد داخل رد النداء دائمًا؛ وإلا سيُظهر الحفظ خطأ “Path not found”.  
- **فواصل مسارات الملفات** – استخدم `Path.Combine` لتظل مستقلة عن النظام (Windows vs Linux).  
- **المستندات الكبيرة** – للملفات الضخمة، فكر في تدفق الإخراج أو زيادة حد الذاكرة للعملية.

## الخطوات التالية

الآن بعد أن عرفت **كيفية حفظ markdown** و**كيفية استخراج الصور من word**، قد ترغب في:

- **معالجة دفعة من ملفات `.docx`** – كرّر عبر دليل واستدعِ منطق التحويل نفسه.  
- **دمج مع مولد موقع ثابت** – أدخل markdown المُولد مباشرةً إلى Hugo أو Jekyll أو MkDocs.  
- **إضافة بيانات front‑matter** – أضف كتل YAML في بداية كل ملف markdown لـ Hugo/Eleventy.  
- **استكشاف صيغ أخرى** – يدعم Aspose.Words أيضًا HTML وPDF وEPUB إذا احتجت **تحويل docx** إلى صيغة أخرى.

لا تتردد في تجربة الكود، تعديل رد النداء، أو دمج هذا النهج مع أدوات أتمتة أخرى. مرونة Aspose.Words تسمح لك بتكييف خط الأنابيب مع أي تدفق عمل توثيقي تقريبًا.

---

**باختصار:** لقد تعلمت الآن **كيفية حفظ markdown** من مستند Word، **كيفية تحويل word إلى markdown**، والخطوات الدقيقة **لاستخراج الصور من word** مع الحفاظ على بنية الملفات. جرّبها، ودع الأتمتة تتولى الجزء الصعب في دورة توثيقك القادمة. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}