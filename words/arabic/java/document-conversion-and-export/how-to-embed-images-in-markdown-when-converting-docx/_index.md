---
category: general
date: 2026-01-11
description: تعرّف على كيفية تضمين الصور في Markdown أثناء تحويل ملف DOCX، باستخدام
  Base64 للصور الصغيرة وحفظ الموارد الأكبر بشكل منفصل.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- how to convert docx
- embed images as base64
- export word document markdown
language: ar
og_description: تعلم كيفية تضمين الصور في Markdown أثناء تحويل ملف DOCX، باستخدام
  Base64 للصور الصغيرة وحفظ الموارد الكبيرة بشكل منفصل.
og_title: كيفية تضمين الصور في ماركداون عند تحويل DOCX
tags:
- Aspose.Words
- Java
- Markdown
- Image Embedding
title: كيفية تضمين الصور في ماركداون عند تحويل DOCX
url: /ar/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تضمين الصور في Markdown عند تحويل DOCX

هل تساءلت يومًا **كيف تُضمّن الصور** في ملف Markdown ناتج من مستند Word؟ لست وحدك. يواجه معظم المطورين مشكلة عندما تُفقد الصور أثناء التحويل أو تُخزن بطريقة تُفسد التخطيط النهائي.  

في هذا الدليل سنستعرض مثالًا كاملًا جاهزًا للتنفيذ يُظهر **كيفية تضمين الصور** كـ Base64 data URIs للرسومات الصغيرة، بينما تُكتب الأصول الأكبر حجمًا إلى مجلد جانبي. على طول الطريق سنتناول أيضًا **convert docx to markdown**، وسنلمس **how to convert docx** باستخدام Aspose.Words، وسنشرح الفرق بين تضمين الصور كـ Base64 وتصديرها كملفات منفصلة.  

> **نصيحة محترف:** إذا كنت تحتاج فقط إلى إثبات مفهوم سريع، فإن الشيفرة أدناه تعمل مباشرةً مع اعتماد Maven واحد.

---

## ما ستحتاجه

- **Java 17** (أو أي JDK حديث) – الـ API موجه للـ Java، لكن المفاهيم قابلة للتطبيق على لغات أخرى.  
- **Aspose.Words for Java** – مكتبة تجارية تدعم تحويل DOCX → Markdown.  
- **ملف DOCX تجريبي** يحتوي على مزيج من الأيقونات الصغيرة والصور الكبيرة.  
- مجلد تريد أن تُخزن فيه ملفات Markdown ومواردها.

لا أطر إضافية، ولا سكريبتات خارجية. مجرد Java عادي وAspose.Words.

---

## الخطوة 1 – إضافة Aspose.Words إلى مشروعك (convert docx to markdown)

إذا كنت تستخدم Maven، أضف المقتطف التالي إلى ملف `pom.xml`. يمكنك استبدال الإصدار بأحدث نسخة متوفرة عند القراءة.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **لماذا هذا مهم:** Aspose.Words يتولى الجزء الأكبر من تحليل بنية DOCX، استخراج الصور، وتوليد صsyntax Markdown. محاولة كتابة محلل خاص بك قد تُدخلُك في متاهة لا تحتاج إلى خوضها.

---

## الخطوة 2 – تحميل مستند DOCX المصدر

أولًا، وجه الـ API إلى ملف Word الذي تريد تحويله. مُنشئ `Document` يقوم بكل العمل—لا حاجة لتحليل XML يدويًا.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

لاحظ أن التعليق يوضح *لماذا* هذا السطر حاسم: بدون كائن `Document` لا شيء يمكن تحويله.

---

## الخطوة 3 – إعداد MarkdownSaveOptions مع رد نداء لحفظ الموارد

هذا هو جوهر **كيفية تضمين الصور** بشكل صحيح. رد النداء يمنحك نقطة تدخل لكل مورد (صورة، نمط، إلخ) يرغب المحول في كتابته.

```java
        // Step 3: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Step 4: Decide how to handle each image
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    // Small image – embed as Base64
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger image – write to a folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        // Normalize path for Markdown (use forward slashes)
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });
```

### لماذا نحتاج رد نداء؟

- **التحكم:** أنت تقرر ما إذا كانت الصورة تُصبح سلسلة Base64 مدمجة أو ملفًا منفصلًا.  
- **الأداء:** الأيقونات الصغيرة تُدمج داخل Markdown، مما يلغي طلبات HTTP الإضافية.  
- **القابلية للنقل:** الصور الكبيرة تبقى كملفات خارجية، مما يحافظ على حجم Markdown معقولًا.

---

## الخطوة 4 – حفظ المستند كـ Markdown

أخيرًا، أخبر Aspose.Words بكتابة ملف Markdown باستخدام الخيارات التي أعددناها للتو.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

تشغيل البرنامج ينتج شيئين:

1. `output.md` – تمثيل Markdown لمستند DOCX الأصلي.  
2. مجلد `markdown_resources` يحتوي على أي صور كبيرة لم تُدمج.

---

## مثال كامل يعمل (جميع الخطوات في مكان واحد)

فيما يلي ملف المصدر الكامل، جاهز للنسخ واللصق في بيئة التطوير الخاصة بك. استبدل `YOUR_DIRECTORY` بالمسار الفعلي على جهازك.

```java
import com.aspose.words.*;
import java.nio.file.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Small images (<10 KB) become Base64 data URIs
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger images are written to a dedicated folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });

        // Step 3: Save the document as Markdown
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

**الناتج المتوقع:** افتح `output.md` في أي عارض Markdown. الأيقونات الصغيرة تظهر مدمجة، مثلًا:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

الصور الكبيرة تُشار إليها هكذا:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

هذا بالضبط ما تحتاجه **لتضمين الصور** مع الحفاظ على حجم الملف ضمن حدود معقولة.

---

## أسئلة شائعة وحالات حافة

### ماذا لو كانت الصورة JPEG بدلاً من PNG؟

رد النداء أعلاه دائمًا يضيف بادئة `image/png` إلى الـ URI. بالنسبة للـ JPEGs، يمكنك فحص البايتات القليلة الأولى من `args.getData()` أو استخدام `args.getFileName()` لاستنتاج نوع MIME الصحيح:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### هل يمكن تغيير عتبة الحجم؟

بالطبع. الحد `10_000` بايت هو مجرد مثال. إذا كان لديك ميزانية عرض نطاق واسعة، يمكنك رفعه إلى 50 KB أو أكثر. وعلى العكس، خفضه إذا كنت تحتاج ملفات Markdown فائقة الخفة.

### هل يعمل هذا مع الجداول أو كائنات Word أخرى؟

نعم. Aspose.Words يحول الجداول والقوائم وحتى الحواشي السفلية تلقائيًا إلى Markdown. رد النداء للموارد يتدخل فقط للصور، لذا لا تحتاج إلى كود إضافي للعناصر الأخرى.

### ماذا عن أسماء الملفات غير الـ ASCII؟

الـ API يشفّر بأمان أسماء الملفات Unicode عند الكتابة إلى مجلد `markdown_resources`. فقط تأكد أن نظام الملفات يدعم UTF-8 (معظم الأنظمة الحديثة تدعم ذلك).

---

## نصائح محترف لتحويل سلس

- **حافظ على نظافة مجلد الإخراج.** استدعِ `Files.createDirectories` مرة واحدة لكل تحويل، أو احذف المجلد قبل كل تشغيل إذا أردت بداية نظيفة.  
- **تحقق من صحة Markdown.** أدوات مثل `markdownlint` يمكنها اكتشاف الأحرف الغريبة التي قد تُدخلها سلاسل Base64 غير الصحيحة.  
- **قفل نسخة Aspose.Words.** تحديد نسخة معينة يضمن استمرارية عمل الكود حتى بعد تغيّر السلوك في إصدارات رئيسية لاحقة.  
- **استخدم .gitignore** لإضافة `markdown_resources/` إلى قائمة التجاهل.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}