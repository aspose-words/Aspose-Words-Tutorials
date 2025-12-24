---
category: general
date: 2025-12-23
description: إدراج صور ماركداون في جافا وتعلم كيفية حفظ مستند ماركداون، تحويل مستند
  ماركداون، تصدير المعادلات بصيغة لايتكس، وإجراء تصدير ماركداون في جافا—كل ذلك في
  دليل واحد.
draft: false
keywords:
- embed images markdown
- save document markdown
- convert doc markdown
- export equations latex
- java markdown export
language: ar
og_description: دمج صور ماركداون باستخدام جافا، حفظ مستند ماركداون، تحويل مستند ماركداون،
  تصدير المعادلات بصيغة لايتكس، وإتقان تصدير ماركداون لجافا في دليل عملي واحد.
og_title: دمج الصور في ماركداون – دليل جافا خطوة بخطوة
tags:
- Java
- Markdown
- DocumentConversion
title: دمج الصور في ماركداون – دليل جافا الكامل لحفظ وتحويل وتصدير المعادلات
url: /ar/java/document-conversion-and-export/embed-images-markdown-complete-java-guide-to-save-convert-an/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تضمين الصور في Markdown – دليل Java الكامل لحفظ، تحويل وتصدير المعادلات

هل احتجت يومًا إلى **تضمين الصور في markdown** أثناء إنشاء وثائق من Java؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحاولون الحفاظ على الصور ومعادلات OfficeMath أثناء تحويل المستند إلى markdown.  

في هذا الدرس ستتعرف بالضبط على كيفية **حفظ مستند markdown**، **تحويل مستند markdown**، **تصدير المعادلات إلى LaTeX**، وإجراء **تصدير markdown كامل باستخدام Java** دون فقدان أي صورة. في النهاية، ستحصل على مقتطف جاهز للتنفيذ يكتب ملف `.md`، يضع كل صورة في مجلد `images/`، ويحول OfficeMath إلى La‑TeX.

## ما ستتعلمه

- إعداد `MarkdownSaveOptions` مع تصدير LaTeX لـ OfficeMath.  
- كتابة رد نداء (callback) لحفظ الموارد يقوم بتخزين كل ملف صورة.  
- حفظ المستند إلى Markdown مع الحفاظ على مسارات الصور النسبية.  
- الأخطاء الشائعة (تكرار أسماء الملفات، المجلدات المفقودة) وكيفية تجنبها.  
- كيفية التحقق من النتيجة ودمج الحل في خطوط أنابيب أكبر.

> **المتطلبات المسبقة**: Java 17+، Aspose.Words for Java (أو أي مكتبة توفر واجهات برمجة تطبيقات مشابهة)، إلمام أساسي بصيغة Markdown.

---

## الخطوة 1 – إعداد خيارات حفظ Markdown (Save Document Markdown)

للبدء، ننشئ كائن `MarkdownSaveOptions` ونخبر المكتبة بتصدير OfficeMath كـ LaTeX. هذا هو الجزء المتعلق بـ **export equations latex** في العملية.

```java
// Import required classes
import com.aspose.words.*;

public class MarkdownExporter {
    public static void main(String[] args) throws Exception {
        // Load your source .docx (or .doc) file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 1️⃣ Create Markdown save options and enable LaTeX export for OfficeMath
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setOfficeMathExportMode(OfficeMathExportMode.LaTeX);
```

**لماذا هذا مهم** – بشكل افتراضي، تقوم Aspose.Words بتحويل المعادلات إلى صور، مما يثقل ملف markdown. LaTeX يبقيها خفيفة وقابلة للتحرير.

---

## الخطوة 2 – تعريف رد نداء الصورة (Embed Images Markdown)

تستدعي المكتبة **رد نداء حفظ الموارد** لكل صورة تواجهها. داخل رد النداء نقوم بإنشاء اسم ملف فريد، نكتب الصورة إلى القرص، ثم نعيد المسار النسبي الذي سيستخدمه Markdown.

```java
        // 2️⃣ Define a callback that saves each image resource to a folder and returns its relative path
        markdownOptions.setResourceSavingCallback((resource, stream) -> {
            // Generate a unique file name for the image
            String imageFileName = "img_" + java.util.UUID.randomUUID() + ".png";

            // Ensure the target directory exists
            java.nio.file.Path imageDir = java.nio.file.Paths.get("YOUR_DIRECTORY/images");
            java.nio.file.Files.createDirectories(imageDir);

            // Save the image to the desired directory
            try (java.io.FileOutputStream fos = new java.io.FileOutputStream(
                    imageDir.resolve(imageFileName).toFile())) {
                stream.transferTo(fos);
            }

            // Return the relative path that will be written into the Markdown file
            return "images/" + imageFileName; // <-- this is the embed images markdown part
        });
```

**نصيحة احترافية**: استخدام `UUID.randomUUID()` يضمن أن صورتين لهما نفس الاسم الأصلي لن تتصادما. كذلك، `Files.createDirectories` ينشئ المجلد بهدوء إذا كان مفقودًا—لا مزيد من استثناءات “المجلد غير موجود”.

---

## الخطوة 3 – حفظ المستند كـ Markdown (Java Markdown Export)

الآن نكتفي باستدعاء `doc.save` مع الخيارات التي ضبطناها. تقوم الطريقة بكتابة ملف `.md`، وبفضل رد النداء، تضع كل صورة في المجلد الفرعي `images/`.

```java
        // 3️⃣ Save the document as a Markdown file using the configured options
        doc.save("YOUR_DIRECTORY/output.md", markdownOptions);
    }
}
```

عند انتهاء البرنامج، ستحصل على:

- `output.md` يحتوي على نص Markdown مع روابط صور مثل `![](images/img_3f8c9a2e-...png)`.  
- مجلد `images/` مملوء بملفات PNG.  
- جميع معادلات OfficeMath مُصدَّرة كـ LaTeX، مثال: `$$\int_{a}^{b} f(x)\,dx$$`.

**كيف يبدو Markdown** (مقتطف):

```markdown
Here is a picture of the architecture:

![](images/img_7e2b1c4d-...png)

And here is an equation:

$$\frac{a}{b} = c$$
```

---

## الخطوة 4 – التحقق من النتيجة (Convert Doc Markdown)

تحقق سريع يضمن أن التحويل نجح:

1. افتح `output.md` في عارض Markdown (VS Code، Typora، أو معاينة GitHub).  
2. تأكد من أن كل صورة تُعرض صحيح.  
3. تحقق من أن المعادلات تظهر ككتل LaTeX (`$$ … $$`). إذا ظهرت LaTeX بصيغتها الخام، فهذا يعني أن المعاين يدعمها؛ وإلا قد تحتاج إلى إضافة مكوّن MathJax.

إذا فقدت صورة ما، أعد فحص مسار الإرجاع في رد النداء. يجب أن يتطابق المسار النسبي مع بنية المجلدات بالنسبة لملف `.md`.

---

## الخطوة 5 – الحالات الخاصة والأخطاء الشائعة (Save Document Markdown)

| الحالة | لماذا يحدث | الحل |
|-----------|----------------|-----|
| **الصور الكبيرة** تسبب بطء في العرض | تُحفظ الصور بدقة الأصلية | قلل الحجم أو اضغط قبل الحفظ (`ImageIO` يمكن أن يساعد) |
| **تكرار أسماء الملفات** رغم UUID | نادرًا لكن ممكن إذا تصادف UUID | أضف طابع زمنية أو تجزئة قصيرة كإجراء إضافي |
| **مجلد `images/` مفقود** | يُنفّذ رد النداء قبل إنشاء المجلد | استدعِ `Files.createDirectories` *خارج* رد النداء، كما هو موضح |
| **المعادلة لم تُصدّر كـ LaTeX** | ترك `OfficeMathExportMode` على الإعداد الافتراضي | تأكد من استدعاء `setOfficeMathExportMode(OfficeMathExportMode.LaTeX)` قبل الحفظ |

---

## مثال كامل يعمل (جميع الخطوات مجمعة)

```java
import com.aspose.words.*;
import java.io.*;
import java.nio.file.*;
import java.util.UUID;

public class MarkdownExporter {
    public static void main(String[] args) throws Exception {
        // Load source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 1️⃣ Configure Markdown options with LaTeX export
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setOfficeMathExportMode(OfficeMathExportMode.LaTeX);

        // 2️⃣ Callback for image handling
        markdownOptions.setResourceSavingCallback((resource, stream) -> {
            String imageFileName = "img_" + UUID.randomUUID() + ".png";
            Path imageDir = Paths.get("YOUR_DIRECTORY/images");
            Files.createDirectories(imageDir);
            try (FileOutputStream fos = new FileOutputStream(imageDir.resolve(imageFileName).toFile())) {
                stream.transferTo(fos);
            }
            return "images/" + imageFileName;
        });

        // 3️⃣ Save as Markdown
        doc.save("YOUR_DIRECTORY/output.md", markdownOptions);

        System.out.println("Markdown export complete! Check YOUR_DIRECTORY for output.md and images/");
    }
}
```

**الناتج المتوقع في وحدة التحكم**

```
Markdown export complete! Check YOUR_DIRECTORY for output.md and images/
```

افتح `output.md` – يجب أن ترى جميع الصور ومعادلات LaTeX مدمجة بشكل صحيح.

---

## الخلاصة

أصبح لديك الآن وصفة شاملة من البداية إلى النهاية لت **تضمين الصور في markdown** أثناء تنفيذ **تصدير markdown باستخدام Java** الذي يقوم أيضًا بـ **حفظ مستند markdown**، **تحويل مستند markdown**، و**تصدير المعادلات إلى LaTeX**. العنصران الرئيسيان هما تكوين `MarkdownSaveOptions` ورد نداء حفظ الموارد الذي يكتب كل صورة إلى موقع متوقع.

من هنا يمكنك:

- دمج هذا الكود في خط أنابيب بناء أكبر (مثل مهمة Maven أو Gradle).  
- توسيع رد النداء للتعامل مع أنواع موارد أخرى مثل SVG أو GIF.  
- إضافة خطوة ما بعد المعالجة تُعيد كتابة روابط الصور لتشير إلى CDN للوثائق الإنتاجية.

هل لديك أسئلة أو تعديل ترغب في مشاركته؟ اترك تعليقًا، ونتمنى لك برمجة سعيدة! 

--- 

<img src="https://example.com/placeholder-diagram.png" alt="Diagram showing the flow of embed images markdown process" style="max-width:100%;">

*مخطط: تدفق العملية من مستند Word → MarkdownSaveOptions → رد نداء الصورة → مجلد images + ملف Markdown.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}