---
category: general
date: 2026-06-27
description: تحويل ملفات docx إلى markdown وحفظ الصور من docx باستخدام Aspose.Words. تعلم
  كيفية استخراج الصور من ملف Word وتصدير مستند Word كـ markdown.
draft: false
keywords:
- convert docx to markdown
- save images from docx
- extract images from word file
- export word document as markdown
language: ar
og_description: تحويل ملف docx إلى markdown وحفظ الصور من docx. يوضح هذا الدليل كيفية
  استخراج الصور من ملف Word وتصدير مستند Word كملف markdown.
og_title: تحويل docx إلى markdown وحفظ الصور من docx
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  headline: Convert docx to markdown & save images from docx
  type: TechArticle
- description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  name: Convert docx to markdown & save images from docx
  steps:
  - name: How the code works
    text: '- **Loading the document** (`new Document(inputPath)`) gives us an in‑memory
      representation of the Word file, complete with all its parts—paragraphs, tables,
      and **images**. - **`MarkdownSaveOptions`** is where the magic happens. By attaching
      a `ResourceSavingCallback`, we gain full control over eve'
  - name: Quick sanity check
    text: '- Does the Markdown file open without errors in VS Code’s preview pane?
      ✅ - Are all pictures displayed when you view the file on GitHub? ✅ - Did the
      `Images` directory contain one file per picture from the original `.docx`? ✅'
  - name: What’s next?
    text: '- **Style the Markdown** – add a front‑matter block for Jekyll or Hugo.
      - **Automate the pipeline** – embed this code in an Azure DevOps or GitHub Action
      step. - **Handle tables and footnotes** – explore other `MarkdownSaveOptions`
      flags like `ExportTableBorderStyles`.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Markdown
- Word
title: تحويل ملف docx إلى markdown وحفظ الصور من docx
url: /ar/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-save-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحويل docx إلى markdown وحفظ الصور من docx

هل تساءلت يوماً كيف **تحول docx إلى markdown** دون فقدان الصور المدمجة في ملف Word الخاص بك؟ لست وحدك—غالباً ما يحتاج المطورون إلى نسخة نظيفة من التقرير بصيغة Markdown مع الحفاظ على كل مخطط أو شعار أو لقطة شاشة.

في هذا الدرس سنستعرض مثالاً كاملاً جاهزاً للتنفيذ **يحوّل .docx إلى Markdown**، **يحفظ الصور من docx** إلى مجلد تختاره، ويظهر لك كيفية **استخراج الصور من ملف Word** باستخدام مكتبة Aspose.Words القوية. في النهاية ستعرف أيضاً كيف **تصدّر مستند Word كـ markdown** بسطر واحد من الشيفرة.

## ما الذي ستحتاجه

- .NET 6+ (أو .NET Framework 4.7.2+) مثبت على جهازك  
- إشارة NuGet إلى `Aspose.Words` (الإصدار التجريبي المجاني يكفي)  
- ملف `input.docx` تجريبي يحتوي على صورة واحدة على الأقل  
- بيئة تطوير تفضّلها—Visual Studio، Rider، أو حتى VS Code ستفي بالغرض  

لا أدوات طرف ثالث إضافية، ولا حركات معقدة في سطر الأوامر. مجرد كود C# مباشر.

## تحويل docx إلى markdown – نظرة عامة

الفكرة الأساسية بسيطة:

1. تحميل مستند Word المصدر.  
2. إخبار Aspose.Words كيف تريد معالجة الموارد الخارجية (مثل الصور).  
3. حفظ المستند كـ Markdown، لتقوم المكتبة ببقية العمل.

فيما يلي **البرنامج الكامل القابل للتنفيذ**. يمكنك نسخه‑لصقه في مشروع Console جديد والضغط على `Ctrl+F5`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load the source document that contains images
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // Step 2: Configure Markdown save options with a custom callback
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This callback runs for each external resource (images, CSS, etc.)
            ResourceSavingCallback = (sender, args) =>
            {
                // ---------------------------------------------------------
                // Step 3a: Save images to a custom folder using a unique name
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.Image)
                {
                    string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
                    Directory.CreateDirectory(imageFolder); // ensures folder exists

                    // Use a GUID so we never clash with existing files
                    string uniqueName = Guid.NewGuid().ToString() + args.Extension;
                    args.SavePath = Path.Combine(imageFolder, uniqueName);
                }

                // ---------------------------------------------------------
                // Step 3b: Skip CSS files – they aren't needed for plain Markdown
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.CssStyleSheet)
                    args.Cancel = true;
            }
        };

        // -----------------------------------------------------------------
        // Step 4: Export the document to Markdown, applying the options
        // -----------------------------------------------------------------
        string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Markdown saved to " + outputPath);
        Console.WriteLine("Images extracted to " + Path.Combine("YOUR_DIRECTORY", "Images"));
    }
}
```

### كيف يعمل الكود

- **تحميل المستند** (`new Document(inputPath)`) يمنحنا تمثيلاً في الذاكرة لملف Word، بما في ذلك جميع أجزائه—الفقرات، الجداول، و**الصور**.  
- **`MarkdownSaveOptions`** هو المكان الذي يحدث فيه السحر. عبر إرفاق `ResourceSavingCallback`، نحصل على تحكم كامل في كل مورد خارجي تحاول Aspose.Words كتابته.  
- داخل الـ callback نـ **نستخرج الصور من ملف Word** بالتحقق من `args.ResourceType == ResourceType.Image`. يتلقى الـ callback بايتات الصورة، الامتداد الأصلي، وخاصية `SavePath` التي نحددها إلى مجلد ننشئه في الوقت الفعلي. استخدام `Guid.NewGuid()` يضمن اسم ملف فريد، حتى لا تكتب فوق ملفات سابقة عن طريق الخطأ.  
- نتخطى **CSS** (`ResourceType.CssStyleSheet`) لأن Markdown العادي لا يحتاج إلى ورقة أنماط. هذا يحافظ على نظافة الناتج.  
- أخيراً، `doc.Save(outputPath, mdOptions)` يكتب ملف Markdown، مستبدلاً بنى Word بما يعادلها في Markdown (العناوين تصبح `#`، الجداول تصبح صفوف مفصولة بـ `|`، إلخ).

## حفظ الصور من docx – استراتيجية المجلد المخصص

لماذا نحتاج إلى مجلد مخصص؟ تخيّل أنك تولّد توثيقاً لأنابيب CI. تريد أن يكون ملف Markdown وأصوله جنباً إلى جنب في بنية نظيفة وقابلة لإعادة الإنتاج.

```csharp
string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
Directory.CreateDirectory(imageFolder);
```

بعض **النصائح الاحترافية**:

- **اجعل مسار المجلد نسبياً** إلى جذر مشروعك. بهذه الطريقة يمكن لملف Markdown الإشارة إلى الصور عبر رابط نسبي (`![Alt text](Images/abc123.png)`)، وهو ما يعمل على GitHub، GitLab، أو أي مولّد مواقع ثابتة.  
- **إذا كنت تحتاج أسماء حتمية** (مثلاً، يجب أن تحصل الصورة نفسها دائماً على نفس الاسم)، استبدل الـ GUID بعملية تجزئة لبايتات الصورة: `MD5.Create().ComputeHash(args.Data)`. تعديل بسيط لكنه مفيد للتخزين المؤقت.

## استخراج الصور من ملف Word – حالات خاصة

1. **تنسيقات صور متعددة** – تدعم Aspose.Words PNG، JPEG، GIF، BMP، وحتى SVG. خاصية `args.Extension` تحتوي بالفعل على الامتداد الصحيح، لذا لا تحتاج إلى التخمين.  
2. **صور كبيرة جداً** – إذا كان المستند المصدر يحتوي على صور عالية الدقة، قد تكون الملفات الناتجة ضخمة. فكر في إضافة خطوة ضغط بعد الـ callback باستخدام `System.Drawing` أو `ImageSharp`.  
3. **صور مخفية** – يمكن لـ Word تخزين صور في رؤوس/تذييلات أو حتى في مربعات نص. الـ callback يراها جميعاً، لذا ستستخرج **كل** صورة، وليس فقط الظاهرة. إذا أردت فقط صور النص الأساسي، أضف مرشحاً على `args.ImageIndex` أو افحص `args.ImageType`.

## تصدير مستند Word كـ markdown – التحقق من النتيجة

بعد تشغيل البرنامج، افتح `output.md` في أي عارض Markdown. يجب أن ترى شيئاً مثل:

```markdown
# My Report

Here is an introductory paragraph.

![Image1](Images/3f9c2d1e-7a5b-4c9e-9f6a-2b4e5d6f7a8b.png)

More text follows...
```

لاحظ أن رابط الصورة يشير إلى مجلد **Images** الذي أنشأناه. هذا هو دليل نجاح عملية **تصدير مستند Word كـ markdown**.

### فحص سريع للمنطقية

- هل يفتح ملف Markdown دون أخطاء في نافذة المعاينة في VS Code؟ ✅  
- هل تُعرض جميع الصور عند عرض الملف على GitHub؟ ✅  
- هل يحتوي دليل `Images` على ملف واحد لكل صورة من ملف `.docx` الأصلي؟ ✅  

إذا فشل أي من هذه الفحوصات، أعد مراجعة منطق `ResourceSavingCallback` وتأكد أن المتغيّر `YOUR_DIRECTORY` يشير إلى موقع قابل للكتابة.

## الأخطاء الشائعة وكيفية تجنّبها

| المشكلة | السبب | الحل |
|---------|-------|------|
| **الصور لا تظهر** | الـ callback لم يُستدعَ لأن `ResourceSavingCallback` لم يُعيّن. | عيّن الـ callback **قبل** استدعاء `doc.Save`. |
| **مجلد الصور فارغ** | تم تعيين `args.Cancel = true` لجميع الموارد عن طريق الخطأ. | ألغِ إلغاء CSS فقط (`ResourceType.CssStyleSheet`)، واترك الصور دون إلغاء. |
| **طول مسار الملف كبير على Windows** | استخدام مجلدات متداخلة عميقة مع GUIDs قد يتجاوز 260 حرفاً. | احفظ المجلد في مستوى عالٍ، أو فعّل دعم المسارات الطويلة في Windows 10+. |
| **تكرار أسماء الصور** | استخدام `DateTime.Now.Ticks` بدلاً من GUID قد يتسبب في تصادم عند الحلقات السريعة. | استمر باستخدام `Guid.NewGuid()` لضمان التفرد. |

## الخلاصة

لقد **حوّلنا docx إلى markdown**، **حفظنا الصور من docx**، وأظهرنا كيفية **استخراج الصور من ملف Word** أثناء **تصدير مستند Word كـ markdown** بطريقة نظيفة وقابلة للتكرار. العملية بأكملها تعتمد على `ResourceSavingCallback` في Aspose.Words، الذي يمنحك تحكمًا دقيقًا في كل أصل خارجي.

### ما التالي؟

- **تنسيق Markdown** – أضف كتلة front‑matter لـ Jekyll أو Hugo.  
- **أتمتة الخط الأنابيب** – دمج هذا الكود في خطوة Azure DevOps أو GitHub Action.  
- **معالجة الجداول والحواشي** – استكشف خيارات `MarkdownSaveOptions` أخرى مثل `ExportTableBorderStyles`.  

لا تتردد في تعديل بنية المجلد، إضافة ضغط للصور، أو حتى تبديل صيغة الإخراج إلى HTML باستبدال `MarkdownSaveOptions` بـ `HtmlSaveOptions`. السماء هي الحد عندما يكون لديك أساس صلب لـ **convert docx to markdown**.

برمجة سعيدة، ولتظل توثيقاتك دائمًا جميلة **و** قابلة للقراءة آليًا!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة‑بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Convert Word to Markdown – Embed Images as Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}