---
category: general
date: 2026-04-28
description: كيفية تصدير markdown من ملف DOCX واستخراج الصور. تعلّم تحويل docx إلى
  markdown، وضع الصور في مجلد، وحفظ Word كـ markdown.
draft: false
keywords:
- how to export markdown
- convert docx to markdown
- extract images from docx
- how to place images
- save word as markdown
language: ar
og_description: كيفية تصدير ماركداون من ملف DOCX باستخدام جافا. يوضح لك هذا الدرس
  كيفية تحويل DOCX إلى ماركداون، استخراج الصور، وتنظيمها.
og_title: كيفية تصدير ماركداون من وورد – دليل كامل
tags:
- Aspose.Words
- Java
- Markdown
- Document Conversion
title: كيفية تصدير ماركداون من وورد – دليل شامل
url: /ar/java/document-conversion-and-export/how-to-export-markdown-from-word-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تصدير Markdown من Word – دليل كامل

هل تساءلت يومًا **كيف تصدر markdown** من مستند Word دون فقدان أي من الصور المدمجة؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحتاجون إلى ملف Markdown نظيف ومجلد صور منظم لمولدات المواقع الثابتة، مواقع الوثائق، أو ملفات README على GitHub.  

في هذا الدرس سنستعرض الخطوات الدقيقة **لتحويل docx إلى markdown**، واستخراج كل صورة من المصدر، و**وضع الصور** في مجلد فرعي `img` بحيث تظل مراجع Markdown سليمة. في النهاية ستحصل على ملف `output.md` جاهز للنشر جنبًا إلى جنب مع دليل `img`—دون الحاجة إلى النسخ واللصق اليدوي.

> **ما ستحصل عليه:** مقطع Java قابل للتنفيذ باستخدام Aspose.Words، شرح واضح لأهمية كل سطر، ونصائح للتعامل مع الحالات الخاصة مثل صور SVG أو الملفات الثنائية الكبيرة.  

*المتطلبات المسبقة:* تثبيت Java 8+، بيئة تطوير (IntelliJ IDEA، Eclipse، أو VS Code)، ورخصة صالحة لـ Aspose.Words for Java (الإصدار التجريبي المجاني يكفي للتجربة).

---

## كيفية تصدير Markdown من مستند Word

### الخطوة 1: تحميل المستند المصدر  

قبل أن يبدأ أي تحويل، نحتاج إلى جلب ملف DOCX إلى الذاكرة. تمثل Aspose.Words ملف Word باستخدام الفئة `Document`.  

```java
import com.aspose.words.Document;
import com.aspose.words.License;

// Load your license (optional for trial)
License license = new License();
license.setLicense("Aspose.Words.Java.lic");

// Step 1 – read the .docx file
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*لماذا هذا مهم:* تحميل الملف يتحقق من صحة الصيغة ويمنحنا الوصول إلى شجرة المستند (فقرات، تشغيلات، صور). إذا كان الملف تالفًا، ستطلق Aspose استثناءً واضحًا، مما يوفر عليك الكثير من وقت التصحيح لاحقًا.

### تحويل DOCX إلى Markdown – إعداد الخيارات  

كائن `MarkdownSaveOptions` يخبر Aspose كيف يتم تسلسل المستند. السلوك الافتراضي يكتب روابط الصور موجهة إلى نفس المجلد الذي يوجد فيه ملف Markdown. سنغيّر ذلك في الخطوة التالية.

```java
import com.aspose.words.MarkdownSaveOptions;
import com.aspose.words.ResourceSavingArgs;
import com.aspose.words.IResourceSavingCallback;
import com.aspose.words.ResourceType;

// Step 2 – configure Markdown export
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
```

*نصيحة احترافية:* إذا كنت تحتاج إلى Markdown بنكهة GitHub، اضبط `mdOptions.setExportImagesAsBase64(false);` للحفاظ على الصور كملفات منفصلة بدلاً من تضمينها كـ data URIs.

### استخراج الصور من DOCX أثناء التصدير  

الآن يأتي الجزء الشهي: استخراج كل صورة من DOCX ووضعها في مجلد `img`. الـ `IResourceSavingCallback` يُستدعى لكل مورد خارجي (صور، خطوط، إلخ) تكتبه Aspose أثناء عملية الحفظ.

```java
// Step 3 – tell Aspose where to put image resources
mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) {
        // Only act on image resources
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Build a path like "img/picture1.png"
            String newName = "img/" + args.getResourceFileName();
            args.setResourceFileName(newName);

            // Optional: you could compress the image here
            // InputStream original = args.getResourceStream();
            // args.setResourceStream(compress(original));
        }
    }
});
```

*لماذا نستخدم رد الاتصال:* بدون هذا الـ callback، كانت Aspose ستنشر الصور في نفس دليل `output.md`، مما يجعل المستودع فوضويًا. يمنحنا الـ callback تحكمًا كاملاً في التسمية، بنية المجلدات، وحتى المعالجة اللاحقة (مثل تعديل حجم PNGs).

### حفظ Word كـ Markdown – الكتابة النهائية  

مع تحميل المستند وضبط خيارات الحفظ، نكتب أخيرًا ملف Markdown. تُحفظ الصور تلقائيًا في المجلد الفرعي `img` الذي حددناه.

```java
// Step 4 – write the Markdown file
doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

إذا سارت الأمور بسلاسة، ستحصل على:

```
YOUR_DIRECTORY/
├─ input.docx
├─ output.md
└─ img/
   ├─ image1.png
   ├─ image2.jpg
   └─ ...
```

افتح `output.md` في أي محرر وسترى صيغة صورة Markdown مثل `![Image 1](img/image1.png)`. الروابط بالفعل نسبية، لذا تعمل في GitHub، MkDocs، أو أي مولد مواقع ثابتة.

---

## كيفية وضع الصور في مجلد فرعي (خيارات متقدمة)

أحيانًا تحتاج إلى هيكلية أعمق، مثل `assets/images/`. فقط عدل الـ callback:

```java
String newName = "assets/images/" + args.getResourceFileName();
args.setResourceFileName(newName);
```

أو إذا أردت إعادة تسمية الملفات إلى شيء أكثر وصفًا (مثلاً بناءً على الفقرة المحيطة)، يمكنك فحص `args.getResourceFileName()` و `args.getDocumentNode()` داخل الـ callback. هذه المرونة هي السبب في أن سؤال **كيفية وضع الصور** يربك الكثيرين—Aspose يمنحك النقطة التي يمكنك فيها إضافة المنطق الخاص بك.

### التعامل مع SVG أو الصيغ غير المدعومة  

تحول Aspose.Words معظم صيغ الرسوم النقطية مباشرةً. بالنسبة لـ SVG، قد تحتاج إلى تحويله إلى صورة نقطية أولًا:

```java
if (args.getResourceFileName().endsWith(".svg")) {
    // Convert SVG to PNG on the fly (requires a third‑party lib)
    InputStream svgStream = args.getResourceStream();
    InputStream pngStream = convertSvgToPng(svgStream);
    args.setResourceStream(pngStream);
    args.setResourceFileName(args.getResourceFileName().replace(".svg", ".png"));
}
```

*ملاحظة حول الحالة الخاصة:* ليس كل عارضات Markdown تدعم SVG مضمّنًا. التحويل إلى PNG يضمن التوافق.

---

## حفظ Word كـ Markdown – مثال كامل يعمل  

فيما يلي البرنامج الكامل الجاهز للتنفيذ. انسخه إلى ملف `Main.java`، عدل المسارات، ثم اضغط **Run**.

```java
// Main.java
import com.aspose.words.*;

public class Main {
    public static void main(String[] args) throws Exception {
        // --------------------------------------------------------------------
        // 1️⃣ Load the DOCX file
        // --------------------------------------------------------------------
        License license = new License();
        // Uncomment the next line if you have a license file
        // license.setLicense("Aspose.Words.Java.lic");

        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // --------------------------------------------------------------------
        // 2️⃣ Prepare Markdown options
        // --------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        // Keep images as separate files (GitHub‑flavored)
        mdOptions.setExportImagesAsBase64(false);

        // --------------------------------------------------------------------
        // 3️⃣ Callback – extract and relocate images
        // --------------------------------------------------------------------
        mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                if (args.getResourceType() == ResourceType.IMAGE) {
                    // Place every image in the "img" folder
                    String newName = "img/" + args.getResourceFileName();
                    args.setResourceFileName(newName);

                    // Example: compress PNGs (pseudo‑code)
                    // if (newName.endsWith(".png")) {
                    //     args.setResourceStream(compressPng(args.getResourceStream()));
                    // }
                }
            }
        });

        // --------------------------------------------------------------------
        // 4️⃣ Save as Markdown
        // --------------------------------------------------------------------
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        System.out.println("✅ Markdown export complete! Check the img folder for pictures.");
    }
}
```

**النتيجة المتوقعة:** يحتوي `output.md` على نص Markdown نظيف، وكل مرجع صورة يشير إلى `img/<filename>`. افتح الملف في معاينة Markdown في VS Code للتحقق من أن الصور تُعرض بشكل صحيح.

---

## أسئلة شائعة ومشكلات محتملة

| السؤال | الجواب |
|----------|--------|
| *ماذا لو كان ملف DOCX يحتوي على خطوط مدمجة؟* | اضبط `mdOptions.setExportFontsAsBase64(true)` إذا كنت تحتاجها، لكن معظم معالجات Markdown تتجاهل الخطوط. |
| *هل يمكنني التصدير إلى بنية مجلد مختلفة؟* | بالتأكيد—عدّل سلسلة `newName` في الـ callback إلى أي مسار تريده. |
| *هل يعمل هذا مع ملفات .doc؟* | نعم. Aspose.Words تقرأ `.doc` بنفس الطريقة؛ فقط غيّر امتداد الملف في مُنشئ `Document`. |
| *ماذا عن الصور الكبيرة؟* | فكر في إضافة خطوة ضغط داخل الـ callback (مثلاً باستخدام `javax.imageio` لتقليل الجودة). |
| *هل الرخصة مطلوبة للإنتاج؟* | النسخة التجريبية تضيف علامة مائية إلى الصفحة الأولى من الناتج. للاستخدام التجاري، احصل على رخصة لإزالتها. |

---

## الخلاصة

أنت الآن تعرف **كيفية تصدير markdown** من ملف Word، **تحويل docx إلى markdown**، **استخراج الصور من docx**، و**كيفية وضع الصور** في مجلد مخصص—كل ذلك ببضع أسطر من Java باستخدام Aspose.Words. المثال الكامل أعلاه جاهز للإدماج في أي مشروع، ويمكنك تعديل الـ callback ليتناسب مع أنظمة التسمية المخصصة أو المعالجة اللاحقة الإضافية.

ما الخطوة التالية؟ جرّب إمداد Markdown المُولد إلى مولد موقع ثابت مثل Jekyll أو Hugo، جرب صيغ صور مختلفة، أو اربط هذا التحويل بسلسلة CI آلية. النمط نفسه يعمل مع PDF، HTML، أو حتى نص عادي—فقط استبدل فئة `SaveOptions`.

برمجة سعيدة، ولتظل وثائقك دائمًا نظيفة وغنية بالصور!  

---  

![مخطط يوضح كيفية تصدير markdown من Word – التدفق من DOCX إلى Markdown مع الصور في مجلد فرعي](https://example.com/placeholder.png "مخطط تصدير markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}