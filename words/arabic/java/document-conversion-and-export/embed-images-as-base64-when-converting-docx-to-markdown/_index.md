---
category: general
date: 2026-05-26
description: قم بتضمين الصور بصيغة base64 أثناء تحويل ملف docx إلى markdown باستخدام
  Aspose.Words for Java. تعلم كيفية تحويل Word إلى markdown، وحفظ Word كـ markdown،
  ومعالجة الصور.
draft: false
keywords:
- embed images as base64
- convert docx to markdown
- convert word to markdown
- convert images to base64
- save word as markdown
language: ar
og_description: تضمين الصور بصيغة base64 أثناء تحويل ملف docx إلى markdown باستخدام
  Aspose.Words للغة Java. دليل كامل لتحويل مستند Word إلى markdown وحفظه كملف markdown.
og_title: تضمين الصور كـ Base64 عند تحويل DOCX إلى Markdown
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Embed images as base64 while you convert docx to markdown with Aspose.Words
    for Java. Learn to convert word to markdown, save word as markdown, and handle
    images.
  headline: Embed Images as Base64 When Converting DOCX to Markdown
  type: TechArticle
- description: Embed images as base64 while you convert docx to markdown with Aspose.Words
    for Java. Learn to convert word to markdown, save word as markdown, and handle
    images.
  name: Embed Images as Base64 When Converting DOCX to Markdown
  steps:
  - name: 'H3: Why Use `setSaveToMemory(true)`?'
    text: 'When `saveToMemory` is true, Aspose writes the image bytes to a memory
      stream instead of a file. The Markdown exporter then converts that stream to
      a Base64 string and inserts it directly into the Markdown image tag:'
  - name: Troubleshooting Checklist
    text: '| Issue | Likely Cause | Fix | |-------|--------------|-----| | Image appears
      as a broken link | `setSaveToMemory` was omitted | Ensure `args.setSaveToMemory(true);`
      is inside the callback | | Base64 string is truncated | Output file encoding
      mismatch | Save the Markdown using UTF‑8 (default for Asp'
  - name: Convert Only Selected Images
    text: 'If you only want to embed certain images (e.g., those larger than 100 KB),
      add a size check:'
  - name: Use a Different Image Format
    text: The `ResourceSavingArgs` gives you the raw bytes, so you could re‑encode
      JPEGs as PNGs before embedding—useful when the target Markdown consumer prefers
      PNG.
  type: HowTo
tags:
- Aspose.Words
- Java
- Markdown
- Base64
title: تضمين الصور بصيغة Base64 عند تحويل DOCX إلى Markdown
url: /ar/java/document-conversion-and-export/embed-images-as-base64-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تضمين الصور كـ Base64 عند تحويل DOCX إلى Markdown

هل تساءلت يومًا كيف **تضمين الصور كـ base64** أثناء **تحويل docx إلى markdown**؟ لست وحدك—المطورون يسألون باستمرار كيف يمكن الحفاظ على الصور مدمجة دون الحاجة إلى ملفات منفصلة. الخبر السار هو أن Aspose.Words for Java يجعل الأمر سهلًا: يمكنك تحويل مستند Word إلى Markdown وتضمين كل صورة تلقائيًا كسلسلة Base64.

في هذا الدرس سنستعرض العملية بالكامل—من تحميل ملف `.docx` يحتوي على صور، إلى تكوين رد نداء `MarkdownSaveOptions` الذي يقوم بالعمل الشاق، وأخيرًا حفظ النتيجة كملف `.md` نظيف. بنهاية الدرس ستعرف بالضبط كيف **تحويل word إلى markdown**، **تحويل الصور إلى base64**، و**حفظ word كـ markdown** دون ترك مجلدات صور متبقية. لا أدوات خارجية، لا معالجة يدوية بعد—فقط كود Java نقي يمكنك إدراجه في أي مشروع.

## ما ستحتاجه

- **Java 17** (أو أي JDK حديث) – يستخدم الكود صيغة lambda، لكن يمكنك تكييفه مع الإصدارات القديمة.
- مكتبة **Aspose.Words for Java** (أحدث إصدار حتى 2026). أضف تبعية Maven أو ملف JAR إلى مسار الفئة الخاص بك.
- ملف **DOCX** تجريبي يحتوي على صورة واحدة على الأقل.
- بيئة تطوير متكاملة أو محرر نصوص بسيط—Visual Studio Code، IntelliJ IDEA، أو حتى `vim` يكفي.

إذا كان لديك هذه الأدوات بالفعل، رائع—لنبدأ مباشرة.

## الخطوة 1: تحميل مستند Word

أولاً ننشئ كائن `Document` يشير إلى ملف المصدر. هذه هي نفس الخطوة سواء كنت **تحويل docx إلى markdown** أو مجرد قراءة الملف لأغراض أخرى.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Load the source DOCX that contains images
        Document doc = new Document("YOUR_DIRECTORY/doc-with-images.docx");
```

> **لماذا هذا مهم:** كائن `Document` هو نقطة الدخول لكل عملية في Aspose. فهو يحتوي على بنية Word بالكامل—بما في ذلك الصور والجداول والأنماط—حتى يتمكن رد النداء اللاحق من فحص كل مورد.

## الخطوة 2: إنشاء MarkdownSaveOptions وتسجيل رد نداء حفظ المورد

السحر يكمن في `MarkdownSaveOptions`. من خلال إرفاق `IResourceSavingCallback` نحصل على التحكم في كيفية كتابة كل مورد خارجي (مثل الصورة).

```java
        // Configure Markdown save options
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

        // Register the callback that will embed images as Base64
        mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                // The callback fires for every resource Aspose wants to write
                if (args.getResourceType() == ResourceType.IMAGE) {
                    // Tell Aspose we don’t want a separate image file
                    args.setKeepResourceOriginalName(false);
                    // Give the image a predictable name (optional)
                    args.setResourceFileName("image_" + args.getResourceFileName());
                    // Force in‑memory saving – this triggers Base64 embedding
                    args.setSaveToMemory(true);
                }
            }
        });
```

### H3: لماذا نستخدم `setSaveToMemory(true)`؟

عندما تكون `saveToMemory` صحيحة، تقوم Aspose بكتابة بايتات الصورة إلى تدفق ذاكرة بدلاً من ملف. ثم يقوم مُصدّر Markdown بتحويل هذا التدفق إلى سلسلة Base64 وإدراجها مباشرةً في وسم صورة Markdown:

```markdown
![image_image1.png](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

هذا هو جوهر **تضمين الصور كـ base64**.

## الخطوة 3: حفظ المستند كـ Markdown

الآن بعد إعداد رد النداء، الخطوة الأخيرة هي ببساطة استدعاء `save`. هنا نقوم فعليًا **تحويل word إلى markdown** وبسبب رد النداء أيضًا **تحويل الصور إلى base64**.

```java
        // Save the document as Markdown – this triggers the callback
        doc.save("YOUR_DIRECTORY/out.md", mdOptions);
    }
}
```

> **النتيجة:** يحتوي `out.md` على نص Markdown مع تمثيل كل صورة كـ URI من نوع `data:`. لا يتم إنشاء ملفات صور إضافية على القرص، لذا يبقى المجلد مرتبًا.

## الخطوة 4: التحقق من الناتج والمشكلات الشائعة

افتح الملف `out.md` المُولد في أي عارض Markdown (VS Code، GitHub، أو مولد موقع ثابت). يجب أن ترى شيئًا مشابهًا لـ:

```markdown
# Sample Document

Here is an inline image:

![image_image1.png](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

### قائمة التحقق من الأخطاء

| المشكلة | السبب المحتمل | الحل |
|-------|--------------|-----|
| تظهر الصورة كرابط مكسور | تم حذف `setSaveToMemory` | تأكد من وجود `args.setSaveToMemory(true);` داخل رد النداء |
| سلسلة Base64 مقطوعة | عدم توافق ترميز ملف الإخراج | احفظ ملف Markdown باستخدام UTF‑8 (الإعداد الافتراضي لـ Aspose) |
| أسماء ملفات غير متوقعة | `setKeepResourceOriginalName(true)` | اجعلها `false` لفرض منطق التسمية المخصص |

## الخطوة 5: تنويعات متقدمة (اختياري)

### تحويل الصور المختارة فقط

إذا كنت تريد فقط تضمين صور معينة (مثل تلك التي حجمها أكبر من 100 KB)، أضف فحصًا للحجم:

```java
if (args.getResourceType() == ResourceType.IMAGE) {
    if (args.getResourceData().length > 100_000) {
        args.setSaveToMemory(true);
    }
}
```

### استخدام تنسيق صورة مختلف

`ResourceSavingArgs` يمنحك البايتات الخام، لذا يمكنك إعادة ترميز JPEGs إلى PNGs قبل التضمين—مفيد عندما يفضل مستهلك Markdown الهدف تنسيق PNG.

```java
if (args.getResourceFileName().endsWith(".jpg")) {
    // Convert JPEG bytes to PNG bytes (requires an image library)
    byte[] pngBytes = convertJpegToPng(args.getResourceData());
    args.setResourceData(pngBytes);
    args.setResourceFileName(args.getResourceFileName().replace(".jpg", ".png"));
    args.setSaveToMemory(true);
}
```

هذه التعديلات توضح مدى مرونة نهج **تضمين الصور كـ base64** عند **تحويل docx إلى markdown**.

## الخلاصة

لقد تعلمت الآن كيفية **تضمين الصور كـ base64** أثناء **تحويل docx إلى markdown** باستخدام Aspose.Words for Java. من خلال ربط `IResourceSavingCallback` بسيط، تقوم المكتبة بكل العمل الشاق: **تحويل word إلى markdown**، **تحويل الصور إلى base64**، وأخيرًا **حفظ word كـ markdown** باستدعاء `save` واحد.

لا تتردد في التجربة—جرب قواعد تصفية صور مختلفة، أو التحويل إلى مخرجات HTML، أو ربط هذه الخطوة مع مولد موقع ثابت. النمط نفسه يعمل مع صيغ أخرى (HTML، EPUB) أيضًا، لذا يمكنك إعادة استخدام رد النداء أينما احتجت موارد مدمجة.

**الخطوات التالية:**  
- استكشف `HtmlSaveOptions` للحصول على صور HTML مدمجة بـ Base64.  
- اجمع هذا مع خط أنابيب CI لأتمتة إنشاء الوثائق.  
- تعمق في `DocumentVisitor` الخاص بـ Aspose إذا كنت تحتاج إلى تحكم أدق في عملية التحويل.

برمجة سعيدة، واستمتع بملفات Markdown النظيفة والمتكاملة!

## دروس ذات صلة

- [كيفية تضمين الصور في Markdown عند تحويل DOCX](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [تحويل docx إلى markdown – تصدير المعادلات الرياضية إلى LaTeX باستخدام Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [حفظ الصور من Word – دليل Aspose.Words for Java](/words/english/java/document-loading-and-saving/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}