---
category: general
date: 2026-04-24
description: رفع الصور إلى CDN أثناء تحويل ملفات DOCX إلى markdown باستخدام Aspose.Words.
  تعلم تصدير Word إلى markdown مع معالجة الصور وتكامل CDN.
draft: false
keywords:
- upload images to cdn
- convert docx to markdown
- export word to markdown
- how to convert docx
- markdown conversion with images
language: ar
og_description: رفع الصور إلى CDN أثناء تحويل DOCX إلى markdown. دليل Java خطوة بخطوة
  يغطي تصدير Word إلى markdown، معالجة الصور، ورفعها إلى CDN.
og_title: رفع الصور إلى CDN أثناء تحويل DOCX إلى Markdown – دليل Java
tags:
- Java
- Aspose.Words
- Markdown
- CDN
- Document Conversion
title: رفع الصور إلى شبكة توصيل المحتوى أثناء تحويل DOCX إلى Markdown – دليل Java
  الكامل
url: /ar/java/document-conversion-and-export/upload-images-to-cdn-while-converting-docx-to-markdown-full/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# رفع الصور إلى CDN أثناء تحويل DOCX إلى Markdown

هل احتجت يوماً إلى **رفع الصور إلى CDN** كجزء من عملية تحويل DOCX‑إلى‑Markdown؟ لست وحدك. يواجه العديد من المطورين مشكلة عندما تشير ملفات markdown المُولدة إلى ملفات صور محلية لا تصل أبداً إلى بيئة الإنتاج. الخبر السار؟ باستخدام Aspose.Words for Java يمكنك التحكم تماماً في مكان وضع كل صورة—سواء بقيت في مجلد “imgs” المحلي أو تم دفعها إلى CDN من اختيارك.

في هذا الدرس سنستعرض مثالاً كاملاً قابلاً للتنفيذ **يحوّل مستند Word إلى markdown**، يحفظ الصور في مجلد فرعي، ويظهر لك كيفية استبدال المسارات المحلية بروابط CDN. بنهاية الدرس ستحصل على ملف markdown جاهز للنشر يُشير إلى صور مستضافة على أي CDN تفضله.

> **ما ستتعلمه**
> - كيفية تحميل ملف DOCX باستخدام Aspose.Words.
> - كيفية تكوين `MarkdownSaveOptions` وتطبيق `IResourceSavingCallback`.
> - أين تُدمج منطق رفع الصور إلى CDN الخاص بك.
> - كيفية التحقق من ناتج markdown النهائي.

لا توجد خدمات خارجية مطلوبة للخطوات الأساسية، لكننا سنناقش أين يمكنك ربط عميل HTTP أو SDK إذا رغبت في دفع الصور إلى Amazon S3 أو Cloudflare أو Azure Blob Storage.

---

## المتطلبات المسبقة

- **Java 17** أو أحدث (الكود يُمكن أن يُترجم مع إصدارات أقدم، لكن 17 هو LTS الحالي).
- **Aspose.Words for Java** 23.9 أو أحدث. يمكنك الحصول عليه من Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

- ملف **DOCX** تريد تحويله (سنسميه `input.docx`).
- اختياريًا: بيانات اعتماد CDN إذا كنت تخطط لرفع الصور فعليًا.

---

## الخطوة 1 – تحميل مستند Word المصدر

أول ما نقوم به هو قراءة ملف DOCX إلى كائن Aspose `Document`. هذا يمنحنا وصولًا كاملاً إلى بنية المستند، بما في ذلك الفقرات والجداول والموارد المضمَّنة.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Load the source Word document from the file system
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **لماذا هذا مهم:**  
> تحميل المستند مسبقًا يتيح لنا فحص محتوياته أو تعديلها قبل أن نتعامل مع كاتب markdown. إذا احتجت إلى إزالة التعليقات أو تطبيق نمط معين، يمكنك فعل ذلك مباشرة بعد هذا السطر.

---

## الخطوة 2 – إعداد خيارات حفظ Markdown

توفر Aspose.Words فئة `MarkdownSaveOptions` التي تسمح لنا بضبط عملية التحويل بدقة. في هذه الخطوة ننشئ مثيلًا ونفعّل رد الاتصال الخاص بحفظ الموارد الذي سنُفصِّله لاحقًا.

```java
        // Create save options for Markdown output
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

        // Optional: tweak options (e.g., use GitHub‑flavored markdown)
        saveOptions.setExportImagesAsBase64(false); // keep images as external files
```

> **نصيحة:** ترك `ExportImagesAsBase64` على القيمة `false` أمر أساسي إذا كنت تريد رفع الصور إلى CDN. الصور المشفَّرة بـ Base64 ستُدمج داخل markdown، مما يُفقد هدف الاستضافة الخارجية.

---

## الخطوة 3 – تنفيذ رد الاتصال لحفظ الموارد

هذا هو جوهر الدرس. `IResourceSavingCallback` يُستدعى لكل مورد خارجي (صور، CSS، إلخ) تحتاج Aspose إلى كتابته. يمكننا اعتراض الاستدعاء، رفع الصورة إلى CDN، ثم تعديل مرجع markdown.

```java
        // Define a callback to control how external resources (e.g., images) are saved
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                // Only act on image resources
                if (args.getResourceFileType() == ResourceFileType.IMAGE) {
                    // Build a local relative path first (e.g., imgs/picture1.png)
                    String localPath = "imgs/" + args.getResourceFileName();
                    args.setResourceFileName(localPath);

                    // --------------------------------------------------------------
                    // OPTIONAL: Upload to CDN here.
                    // --------------------------------------------------------------
                    // For illustration we’ll pretend to upload and get a CDN URL.
                    // Replace the stub with real SDK calls (AWS S3, Azure Blob, etc.).
                    String cdnUrl = uploadToCdn(args.getResourceBytes(), args.getResourceFileName());

                    // If the upload succeeded, tell Aspose to use the CDN URL instead.
                    if (cdnUrl != null && !cdnUrl.isEmpty()) {
                        args.setResourceUri(cdnUrl);
                    }
                    // --------------------------------------------------------------
                }
            }

            // ----- Helper method that you would replace with real upload logic -----
            private String uploadToCdn(byte[] imageBytes, String fileName) {
                // Placeholder: simulate a CDN URL.
                // In production you might use an HTTP client or cloud SDK.
                // Example: return "https://cdn.example.com/images/" + fileName;
                return "https://cdn.example.com/images/" + fileName;
            }
        });
```

### لماذا نستخدم رد الاتصال؟

- **التحكم في أسماء الملفات:** نخزن كل شيء داخل مجلد `imgs/`، مما يحافظ على نظافة markdown.
- **تكامل CDN:** عبر تعيين `args.setResourceUri(...)` نخبر كاتب markdown بإدراج رابط CDN بدلًا من المسار المحلي.
- **الاستعداد للمستقبل:** إذا غيرت مزود CDN لاحقًا، يكفي تعديل طريقة `uploadToCdn`.

> **خطأ شائع:** نسيان استدعاء `args.setResourceFileName(...)` سيتسبب في أن تقوم Aspose بإسقاط الصورة بجوار ملف markdown باسم عشوائي، مما يُعطِّل الروابط النسبية.

---

## الخطوة 4 – حفظ المستند كـ Markdown

بعد ربط رد الاتصال، الخطوة الأخيرة هي سطر واحد يكتب ملف markdown. يُنفَّذ رد الاتصال تلقائيًا لكل صورة.

```java
        // Save the document as Markdown, applying the custom resource handling
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

عند انتهاء البرنامج، ستجد:

1. `output.md` يحتوي على نص markdown مع مراجع صور تشير إلى CDN الخاص بك (مثال: `![](https://cdn.example.com/images/picture1.png)`).
2. مجلد `imgs/` مُعبَّأ بالصور الأصلية—مفيد للتصحيح أو حالات fallback.

---

## النتيجة المتوقعة

بافتراض أن `input.docx` يحتوي على صورة واحدة باسم `chart.png`، سيظهر `output.md` كالتالي:

```markdown
# My Document Title

Here is an introductory paragraph.

![](https://cdn.example.com/images/chart.png)

More text follows...
```

الصورة الآن تُقدَّم من CDN، مما يعني أن أي مستهلك لاحق (GitHub، مولِّد موقع ثابت، إلخ) سيجلبها من موقع حافة موزَّع عالميًا.

---

## نصائح احترافية وحالات خاصة

| الحالة | ما يجب فعله |
|-----------|------------|
| **DOCX كبير يحتوي على عشرات الصور** | قم برفع الصور دفعةً بشكل غير متزامن لتجنب حجز الخيط الرئيسي. |
| **تنسيق الصورة غير مدعوم من قبل CDN** | حوِّل `args.getResourceBytes()` إلى تنسيق مدعوم (مثل PNG) قبل الرفع. |
| **تحتاج إلى هيكل مجلد مخصص لكل مستند** | استخدم `args.setResourceFileName("docs/" + docId + "/" + args.getResourceFileName());` |
| **CDN يتطلب رؤوس مصادقة** | نفّذ الرفع في `uploadToCdn` باستخدام URL موقع أو SDK يتعامل مع المصادقة. |
| **تريد fallback بصيغة base64 للوثائق غير المتصلة** | عيّن `saveOptions.setExportImagesAsBase64(true)` *مع* الحفاظ على رد الاتصال لرفع CDN إذا رغبت. |

---

## الأسئلة المتكررة

**س: هل يعمل هذا مع إصدارات Aspose.Words القديمة؟**  
ج: تم تقديم واجهة `IResourceSavingCallback` في الإصدار 20.5. إذا كنت تستخدم إصدارًا أقدم، عليك الترقية—الكود سيكون متوافقًا مع الإصدارات المستقبلية وستستفيد أيضًا من تحسينات الأداء.

**س: ماذا لو لم يكن لدي CDN بعد؟**  
ج: طريقة `uploadToCdn` في المثال تُعيد مجرد URL وهمي. يمكنك تشغيل التحويل دون رفع إلى CDN؛ سيشير markdown إلى مسار `imgs/` المحلي بدلاً من ذلك.

**س: هل يمكنني تحويل عدة ملفات DOCX دفعة واحدة؟**  
ج: بالتأكيد. ضع المنطق داخل حلقة، مرّر ملف `input.docx` مختلف ومسار الإخراج لكل تكرار. تذكر إعادة استخدام كائن `MarkdownSaveOptions` واحد إذا كنت تعالج ملفات عديدة لتحسين السرعة.

---

## الخلاصة

لقد أظهرنا لك كيفية **رفع الصور إلى CDN أثناء تحويل DOCX إلى markdown** باستخدام Aspose.Words for Java. العملية تتلخص في ثلاث خطوات أساسية:

1. تحميل مستند Word.
2. ربط `IResourceSavingCallback` الذي يرفع كل صورة ويعيد كتابة رابط markdown.
3. حفظ المستند باستخدام `MarkdownSaveOptions`.

هذا كل ما تحتاجه—لا سكربتات معالجة لاحقة، لا نسخ ولصق يدوي لروابط الصور. الآن لديك ملف markdown نظيف جاهز لمولدات المواقع الثابتة، بوابات الوثائق، أو أي منصة تدعم markdown.

هل أنت مستعد للتحدي التالي؟ جرّب استبدال رفع CDN باستدعاء SDK **Azure Blob Storage**، أو جرب خيارات **GitHub‑flavored markdown** (`saveOptions.setExportImagesAsBase64(true)`). يمكنك أيضًا دمج ذلك في خط أنابيب CI/CD ينشر الوثائق المحدثة تلقائيًا مع كل عملية دفع.

إذا واجهت أي مشكلة أو اكتشفت تحسينًا ذكيًا، لا تتردد بترك تعليق أدناه. برمجة سعيدة، واستمتع بسرعة تقديم الصور من الحافة!

---

![Diagram illustrating the upload images to cdn workflow during DOCX to Markdown conversion](upload-images-to-cdn-diagram.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}