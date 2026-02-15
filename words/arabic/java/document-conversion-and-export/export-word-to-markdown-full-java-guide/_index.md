---
category: general
date: 2026-02-15
description: تصدير مستند Word إلى Markdown في Java باستخدام Aspose.Words. تعلّم كيفية
  تحويل DOCX إلى Markdown وتخزين الصور في مجلد منفصل باستخدام رد نداء مخصص.
draft: false
keywords:
- export word to markdown
- convert docx to markdown
- store images in separate folder
- aspose words markdown
- java document conversion
language: ar
og_description: تصدير Word إلى Markdown باستخدام Aspose.Words. يوضح هذا الدليل كيفية
  تحويل DOCX إلى Markdown وتخزين الصور في مجلد منفصل.
og_title: تصدير Word إلى Markdown – دليل Java الكامل
tags:
- Java
- Aspose.Words
- Markdown
- Image handling
title: تصدير Word إلى Markdown – دليل Java الكامل
url: /ar/java/document-conversion-and-export/export-word-to-markdown-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تصدير Word إلى Markdown – دليل Java كامل

هل تساءلت يومًا كيف **تصدير Word إلى Markdown** دون فقدان أي من الصور المدمجة؟ لست وحدك—المطورون يسألون باستمرار: “كيف أحول DOCX إلى Markdown مع الحفاظ على ترتيب الصور؟” الخبر السار هو أن Aspose.Words for Java يجعل الأمر سهلًا للغاية. في هذا الدرس سنستعرض مثالًا جاهزًا للتنفيذ لا يحول ملف `.docx` إلى Markdown فحسب، بل **يخزن الصور في مجلد منفصل** باستخدام رد نداء مخصص.

سنغطي كل ما تحتاجه: المكتبات المطلوبة، الشيفرة خطوة بخطوة، لماذا كل سطر مهم، وقائمة تحقق سريعة للتأكد. في النهاية ستحصل على نمط قابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع Java.

---

## ما ستحتاجه

| المتطلبات المسبقة | لماذا يهم |
|------------------|-----------|
| **Java 8+** | Aspose.Words يتطلب على الأقل JDK 8. |
| **Aspose.Words for Java** (أحدث نسخة) | يوفر `Document`، `MarkdownSaveOptions`، وواجهة `IResourceSavingCallback`. |
| **ملف DOCX** تريد تحويله | المستند المصدر (`input.docx`). |
| **إذن كتابة** على مجلدات الإخراج | المكتبة ستكتب ملف الـ Markdown ومجلد الصور. |

أضف تبعية Maven (أو حمّل ملف JAR) قبل البدء:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version> <!-- check for the newest release -->
</dependency>
```

---

## الخطوة 1 – تحميل مستند Word المصدر

أول ما نقوم به هو إنشاء كائن `Document` يشير إلى ملف `.docx` الخاص بنا. هذا الكائن يمثل ملف Word بالكامل في الذاكرة، مما يمنحنا إمكانية الوصول إلى محتواه، أنماطه، والموارد المدمجة.

```java
import com.aspose.words.*;

public class MarkdownExportDemo {
    public static void main(String[] args) throws Exception {
        // Load the source .docx
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*لماذا هذا مهم:* إذا كان مسار الملف غير صحيح، ستطرح Aspose استثناء `FileNotFoundException`. استخدام مسار مطلق أو مسار نسبي تم حله بشكل صحيح يجنبك هذه المشكلة.

---

## الخطوة 2 – إعداد خيارات حفظ Markdown

`MarkdownSaveOptions` يسمح لنا بتعديل سلوك التحويل. بشكل افتراضي تُحفظ الصور بجوار ملف الـ Markdown بأسماء عامة. سنقوم بتجاوز ذلك لاحقًا، لكن أولاً نحتاج إلى كائن الخيارات.

```java
        // Create options for Markdown export
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
```

*ملاحظة:* يمكنك أيضًا ضبط `mdOptions.setExportImages(true)` إذا رغبت في تشغيل/إيقاف تصدير الصور، لكن القيمة الافتراضية هي بالفعل `true`.

---

## الخطوة 3 – تعريف رد نداء حفظ الموارد (تخزين الصور في مجلد منفصل)

هذا هو جوهر الدرس. من خلال تنفيذ `IResourceSavingCallback` نحصل على تحكم كامل في مكان حفظ كل صورة. يتلقى رد النداء كائن `ResourceSavingArgs` لكل مورد (صور، خطوط، إلخ) تريد Aspose كتابته.

```java
        // Customize image saving location
        mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                // Only intervene for image resources
                if (args.getResourceFileType() == ResourceFileType.IMAGE) {
                    // Build a unique filename based on document hash and original extension
                    String uniqueName = "img_" + doc.hashCode() + "." + args.getResourceFileExtension();
                    args.setResourceFileName(uniqueName);
                    // Store images in a dedicated folder
                    args.setResourceFilePath("YOUR_DIRECTORY/customImages/" + uniqueName);
                }
                // Let Aspose handle other resource types (e.g., fonts) automatically
            }
        });
```

**لماذا نفعل ذلك:**  
- **تجنب تصادم الأسماء:** صورتان لهما نفس الاسم الأصلي ستحصلان على أسماء ملف مميزة.  
- **تنظيم أفضل للمشروع:** جميع الصور تُخزن تحت `customImages/`، مما يبقي مجلد الـ Markdown مرتبًا.  
- **روابط ثابتة:** سيشير الـ Markdown إلى `customImages/img_12345.png`، ويمكنك لاحقًا رفعها إلى CDN أو تضمينها في موقع ثابت.

---

## الخطوة 4 – حفظ المستند كملف Markdown

الآن نخبر Aspose بكتابة ملف الـ Markdown باستخدام الخيارات التي أعددناها. العملية متزامنة؛ عند عودة الدالة يكون الملف والصور موجودين على القرص.

```java
        // Export to Markdown
        doc.save("YOUR_DIRECTORY/CustomMarkdown.md", mdOptions);
    }
}
```

إذا سارت الأمور بسلاسة، ستجد:

- `CustomMarkdown.md` يحتوي على النص المحول مع روابط الصور مثل `![](customImages/img_12345.png)`.  
- جميع ملفات الصور موجودة داخل `YOUR_DIRECTORY/customImages/`.

---

## مثال كامل جاهز للتنفيذ (انسخه‑الصقه)

فيما يلي الفئة الكاملة، جاهزة للترجمة. استبدل `YOUR_DIRECTORY` بالمسار الفعلي على جهازك.

```java
import com.aspose.words.*;

public class MarkdownExportDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source DOCX
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Create Markdown save options
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

        // 3️⃣ Hook into the resource‑saving pipeline
        mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                if (args.getResourceFileType() == ResourceFileType.IMAGE) {
                    String uniqueName = "img_" + doc.hashCode() + "." + args.getResourceFileExtension();
                    args.setResourceFileName(uniqueName);
                    args.setResourceFilePath("YOUR_DIRECTORY/customImages/" + uniqueName);
                }
                // Other resources (fonts, etc.) use default handling
            }
        });

        // 4️⃣ Save as Markdown
        doc.save("YOUR_DIRECTORY/CustomMarkdown.md", mdOptions);
    }
}
```

### النتيجة المتوقعة

افتح `CustomMarkdown.md` في أي محرر نصوص أو عارض Markdown. يجب أن ترى شيئًا مثل:

```markdown
# Sample Document

This is a paragraph from the original Word file.

![](customImages/img_123456789.png)

Another paragraph follows.
```

ملف الصورة `img_123456789.png` سيقع في مجلد `customImages` بجانب ملف الـ Markdown.

---

## نصائح احترافية ومشكلات شائعة

- **وجود المجلد:** Aspose **لن** ينشئ مجلد الصور الهدف تلقائيًا. تأكد من وجود `customImages/` أو أنشئه برمجيًا قبل عملية التصدير.  
  ```java
  new java.io.File("YOUR_DIRECTORY/customImages").mkdirs();
  ```
- **تصادم التجزئات:** استخدام `doc.hashCode()` عادةً آمن، لكن إذا قمت بتحويل المستند عدة مرات قد تحصل على أسماء مكررة. أضف طابع زمنية لزيادة التفرد:  
  ```java
  String uniqueName = "img_" + doc.hashCode() + "_" + System.currentTimeMillis() + "." + args.getResourceFileExtension();
  ```
- **المستندات الكبيرة:** بالنسبة لملفات DOCX التي تحتوي على آلاف الصور، فكر في تدفق الإخراج أو زيادة حجم heap للـ JVM (`-Xmx2g`).  
- **صيغ الصور:** Aspose يحافظ على الصيغة الأصلية للصورة (PNG، JPEG، إلخ). إذا كنت بحاجة إلى تحويل جميع الصور إلى PNG، سيتعين عليك معالجة المجلد لاحقًا أو استخدام واجهات تحويل الصور في Aspose.

---

## الأسئلة المتكررة

**س: هل يعمل هذا مع ملفات .doc أم فقط .docx؟**  
ج: نعم. Aspose.Words يكتشف الصيغة تلقائيًا، لذا يمكنك تمرير `new Document("file.doc")` وسيعمل نفس الخط سير العمل.

**س: ماذا لو أردت تضمين الصور كـ base64 بدلاً من ملفات خارجية؟**  
ج: اضبط `mdOptions.setExportImagesAsBase64(true)`. سيُدمج بيانات الصورة مباشرةً في ملف الـ Markdown، لكنك ستفقد ميزة المجلد المنفصل للصور.

**س: هل يمكنني تغيير امتداد ملف الـ Markdown إلى `.mdx` لمولد موقع ثابت؟**  
ج: بالتأكيد. الوسيط الأول في طريقة `save` هو مجرد اسم ملف، لذا `doc.save("output.mdx", mdOptions);` يعمل بنفس الطريقة.

---

## الخلاصة

لقد **صدرنا Word إلى Markdown** باستخدام Aspose.Words، وأظهرنا كيف **نحول DOCX إلى Markdown**، وقدمنا طريقة نظيفة **لتخزين الصور في مجلد منفصل**. النمط—تحميل → تكوين الخيارات → حقن رد نداء → حفظ—قابل للتوسع لأي مشروع يحتاج إلى تحويل مستندات تلقائي.

خطوات قد ترغب في استكشافها لاحقًا:

- دمج هذا الكود في نقطة نهاية REST باستخدام Spring Boot بحيث يمكن للمستخدمين رفع DOCX والحصول على حزمة Markdown جاهزة للنشر.  
- الجمع مع مولد موقع ثابت (مثل Hugo) لأتمتة خطوط نشر المدونات.  
- استبدال منطق حفظ الصور بتخزين سحابي (AWS S3، Azure Blob) عبر رفع الصور داخل رد النداء وتعيين رابط الـ Markdown إلى URL العام.

هل لديك أسئلة أخرى؟ اترك تعليقًا، ونتمنى لك برمجة سعيدة! 

![مثال تصدير Word إلى markdown](export_word_to_markdown.png "توضيح تصدير Word إلى markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}