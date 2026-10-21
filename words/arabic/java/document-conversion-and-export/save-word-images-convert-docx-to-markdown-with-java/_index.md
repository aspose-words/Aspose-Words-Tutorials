---
category: general
date: 2026-03-25
description: احفظ صور Word أثناء تحويل ملفات docx إلى markdown باستخدام Aspose.Words
  للغة Java. تعلم كيفية استخراج الصور من Word وإنشاء markdown من ملفات docx في دقائق.
draft: false
keywords:
- save word images
- convert docx to markdown
- extract images from word
- export docx images
- create markdown from docx
language: ar
og_description: احفظ صور Word أثناء تحويل ملف DOCX إلى Markdown. يوضح لك هذا الدليل
  كيفية استخراج الصور من Word وإنشاء ملف markdown من docx باستخدام Java.
og_title: حفظ صور Word – تحويل DOCX إلى Markdown باستخدام Java
tags:
- Aspose.Words
- Java
- Markdown
- Image Extraction
title: حفظ صور Word – تحويل DOCX إلى Markdown باستخدام Java
url: /ar/java/document-conversion-and-export/save-word-images-convert-docx-to-markdown-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ صور Word – تحويل DOCX إلى Markdown باستخدام Java

هل تحتاج إلى **حفظ صور Word** عند تحويل ملف DOCX إلى Markdown؟ لست الوحيد الذي يواجه هذه المشكلة. كثير من المطورين يسألون: *“كيف يمكن استخراج الصور من Word والحصول على ملف markdown نظيف؟”* في هذا الدليل سنرشدك إلى العملية الكاملة — تحميل DOCX، ضبط Aspose.Words بحيث تُحفظ كل صورة في مجلد `assets/`، وأخيرًا كتابة مستند markdown يربط بهذه الصور. في النهاية ستتمكن من **تحويل docx إلى markdown**، **تصدير صور docx**، و**إنشاء markdown من docx** ببضع أسطر من Java.

سنغطي أيضًا المشكلات الشائعة (مثل فقدان الامتدادات) وسنقدم لك نصائح للتعامل مع المخططات أو ملفات SVG التي يعتبرها Aspose.Words موارد. افتح IDE الخاص بك، ولنبدأ.

## ما ستحتاجه

قبل أن نبدأ، تأكد من توفر ما يلي:

- **Java 17** (أو أي JDK حديث؛ Aspose.Words يدعم 8+)
- **Aspose.Words for Java** JAR – يمكنك الحصول عليه من مستودع Maven Central أو تحميل النسخة التجريبية من موقع Aspose.
- ملف **DOCX** يحتوي على صورة واحدة على الأقل (سنسميه `doc-with-images.docx`).
- مجلد تريد أن تُحفظ فيه ملفات markdown والموارد (مثلاً `output/`).

هذا كل شيء — لا مكتبات إضافية، ولا أطر عمل ثقيلة. بسيط، أليس كذلك؟

![مثال حفظ صور Word](image.png "مثال حفظ صور Word")

*نص بديل للصورة: مثال حفظ صور Word يُظهر مجلد assets مع الصور المستخرجة.*

## الخطوة 1 – إعداد مشروع Maven (أو Java عادي)

إذا كنت تستخدم Maven، أضف Aspose.Words كاعتماد:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- check for the latest version -->
</dependency>
```

إذا كنت تفضّل مشروع Java عادي، فقط ضع ملف `aspose-words-24.9.jar` في مسار الـ classpath. لا حاجة لنظام بناء كامل.

> **نصيحة احترافية:** استخدم أحدث نسخة للحصول على تصحيحات الأخطاء للأنساق الصورية الحديثة (WebP، HEIC، إلخ).

## الخطوة 2 – تحميل DOCX الذي يحتوي على صور

أول شيء نقوم به هو قراءة ملف المصدر. فئة `Document` في Aspose.Words تُجرد تنسيق الملف، لذا يمكنك التعامل مع DOCX كما تتعامل مع PDF أو RTF.

```java
import com.aspose.words.*;

public class MarkdownResourceDemo {
    public static void main(String[] args) throws Exception {

        // Load the DOCX file that contains images
        Document document = new Document("output/doc-with-images.docx");
```

لماذا نحمّل المستند أولًا؟ لأن محرك التحويل يحتاج إلى نموذج كائن كامل (فقرات، تشغيلات، صور) قبل أن يقرر أين يضع كل مورد. تخطي هذه الخطوة سيجعل استدعاء الـ callback لاحقًا غير ممكن.

## الخطوة 3 – ضبط خيارات حفظ Markdown مع Callback للموارد

يتيح لك Aspose.Words اعتراض كل مورد خارجي عبر `IResourceSavingCallback`. هنا نخبر المكتبة **كيف نسمي وأين نخزن كل صورة مستخرجة**.

```java
        // Create Markdown save options
        MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();

        // Define how external resources (images, charts, etc.) should be saved
        markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                // Store each resource in the "assets/" folder, preserving its original name
                String extension = args.getResourceFileExtension(); // ".png", ".jpg", …
                String fileName = "assets/" + args.getResourceFileName() + extension;
                args.setResourceFileName(fileName);
            }
        });
```

### لماذا نحتاج إلى Callback؟

- **التحكم في التسمية** – بشكل افتراضي قد يولد Aspose GUIDs. الـ callback يتيح لك الاحتفاظ باسم ملف Word الأصلي، وهو أكثر قابلية للقراءة.
- **تنظيم المجلدات** – وضع كل شيء تحت `assets/` يُحاكي الطريقة التي يتوقعها العديد من مولّدات المواقع الثابتة للصور، مما يجعل الـ markdown قابلًا للنقل.
- **أمان الامتداد** – بعض الموارد لا تأتي بامتداد؛ `getResourceFileExtension()` يضمن إضافة لاحقة صحيحة، مما يمنع كسر روابط الصور.

## الخطوة 4 – حفظ المستند كـ Markdown

الآن ننفّذ عملية التحويل فعليًا. طريقة `save` تكتب ملف markdown، وبفضل الـ callback تُسقط كل صورة في المجلد الفرعي `assets/`.

```java
        // Save the document as Markdown, using the configured options
        document.save("output/doc.md", markdownSaveOptions);
    }
}
```

عند انتهاء الكود، سترى:

```
output/
 ├─ doc.md          ← the markdown file
 └─ assets/
      ├─ image1.png
      └─ chart1.svg
```

افتح `doc.md` في أي محرر وستلاحظ روابط صور markdown مثل `![Image1](assets/image1.png)`. هذا هو نتيجة **حفظ صور Word** التي كنت تبحث عنها.

## الخطوة 5 – التحقق من الاستخراج (اختياري لكن مُستحسن)

فحص سريع يحمّك من المفاجآت لاحقًا.

```java
import java.nio.file.*;

public class VerifyExtraction {
    public static void main(String[] args) throws Exception {
        Path assets = Paths.get("output/assets");
        if (Files.isDirectory(assets)) {
            try (DirectoryStream<Path> stream = Files.newDirectoryStream(assets)) {
                System.out.println("Extracted resources:");
                for (Path p : stream) {
                    System.out.println("- " + p.getFileName());
                }
            }
        } else {
            System.out.println("No assets folder found. Did the callback run?");
        }
    }
}
```

تشغيل هذا يجب أن يطبع قائمة بكل صورة، مخطط، أو SVG تم سحبها من DOCX الأصلي. إذا كانت القائمة فارغة، تحقق من أن الـ callback مرفق بشكل صحيح.

## الخطوة 6 – الحالات الخاصة والأخطاء الشائعة

### 1. صور داخل الجداول أو الرؤوس

يتعامل Aspose مع هذه كصور مدمجة، لكن الـ markdown قد يعرضها بشكل مختلف حسب العارض. إذا كنت بحاجة للحفاظ على تنسيق الجدول، فكر في التحويل إلى HTML أولًا، ثم إلى markdown باستخدام أداة مثل `pandoc`.

### 2. صيغ غير مدعومة

قد تواجه إصدارات أقدم من Aspose.Words صعوبة مع صيغ حديثة مثل WebP. الترقية إلى أحدث نسخة (أو تحويل الصورة إلى PNG مسبقًا) يحل المشكلة.

### 3. أسماء ملفات مكررة

إذا كان هناك صورتان تحملان نفس الاسم داخل DOCX، سيكتب الـ callback الأولى فوق الثانية. حل سريع هو إلحاق لاحقة فريدة:

```java
String uniqueName = args.getResourceFileName() + "_" + UUID.randomUUID();
String fileName = "assets/" + uniqueName + extension;
args.setResourceFileName(fileName);
```

### 4. مستندات ضخمة

لملفات DOCX الكبيرة (مئات الميجابايت)، قد ترغب في تدفق الإخراج بدلاً من تحميل الملف بالكامل في الذاكرة. يوفر Aspose.Words `DocumentBuilder` و `LoadOptions` للتعامل مع مثل هذه السيناريوهات، لكن هذا موضوع دليل آخر.

## مثال كامل يعمل

نجمع كل ما سبق في برنامج جاهز للتنفيذ:

```java
// File: MarkdownResourceDemo.java
import com.aspose.words.*;
import java.util.UUID;

public class MarkdownResourceDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the DOCX file that contains images
        Document document = new Document("output/doc-with-images.docx");

        // 2️⃣ Create Markdown save options
        MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();

        // 3️⃣ Define how external resources (images, charts, etc.) should be saved
        markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                // Preserve original name, add a UUID if a duplicate might occur
                String extension = args.getResourceFileExtension(); // ".png", ".jpg", …
                String baseName = args.getResourceFileName();
                String uniqueName = baseName + "_" + UUID.randomUUID();
                String fileName = "assets/" + uniqueName + extension;
                args.setResourceFileName(fileName);
            }
        });

        // 4️⃣ Save the document as Markdown, using the configured options
        document.save("output/doc.md", markdownSaveOptions);

        System.out.println("Conversion complete! Check output/doc.md and the assets folder.");
    }
}
```

### النتيجة المتوقعة

- يحتوي `output/doc.md` على صيغة markdown مع مراجع صور مثل `![Image1](assets/Image1_3f9c2a4e-... .png)`.
- جميع الصور المستخرجة موجودة داخل `output/assets/`.
- لا حاجة لنسخ الملفات يدويًا؛ الـ callback عالج كل شيء.

## الخلاصة

أنت الآن تعرف **كيفية حفظ صور Word** أثناء **تحويل docx إلى markdown** باستخدام Aspose.Words for Java. الخطوات الأساسية هي تحميل المستند، ضبط `Markdown

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}