---
category: general
date: 2026-07-03
description: تصدير الأشكال العائمة ضمن النص أثناء تحويل Word إلى PDF ضمن النص. تعلّم
  كيفية ضبط خيارات PDF وحفظ Word كملف PDF باستخدام Java.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: ar
og_description: تصدير الأشكال العائمة داخل النص عند تحويل مستند Word إلى PDF. يوضح
  هذا الدرس كيفية ضبط خيارات PDF وحفظ مستند Word كملف PDF.
og_title: تصدير الأشكال العائمة داخل النص – دليل تحويل PDF باستخدام Java
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: تصدير الأشكال العائمة داخل النص – دليل كامل لتحويل PDF
url: /ar/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تصدير الأشكال العائمة داخل السطر – دليل كامل لتحويل PDF

هل احتجت يوماً إلى **export floating shapes inline** عند تحويل مستند Word إلى PDF؟ لست وحدك—العديد من المطورين يواجهون هذه المشكلة عندما تنتقل الرسوم التخطيطية أو الأيقونات إلى طبقات منفصلة بشكل غامض. الخبر السار هو أن خيار PDF واحد يمكنه إبقاء تلك الأشكال داخل وسوم `<span>`، مما يحافظ على التخطيط تماماً كما تراه في Word.

في هذا البرنامج التعليمي سنستعرض **كيفية ضبط خيارات PDF** في Java، ونظهر لك الشيفرة الدقيقة لـ **save Word as PDF options**، ونشرح لماذا قد ترغب في **convert Word to PDF inline** بدلاً من التصدير الافتراضي على مستوى الكتلة. في النهاية ستحصل على مقتطف جاهز للتنفيذ يمكنك إدراجه في أي مشروع Maven أو Gradle.

## ما ستتعلمه

- الفرق بين تصدير `<span>` داخل السطر و`<div>` ككتلة للأشكال العائمة.  
- كيفية تكوين `PdfSaveOptions` لإجبار التصدير داخل السطر.  
- شيفرة خطوة بخطوة تقوم بتحميل ملف `.docx`، وتطبيق الخيار، وكتابة ملف PDF.  
- المشكلات الشائعة (خطوط مفقودة، أشكال غير مدعومة) وكيفية تجنّبها.  
- نصائح لاختبار النتيجة وتوسيع النهج لتشمل عناصر مستند أخرى.

**المتطلبات المسبقة** – ستحتاج إلى Java 8 أو أحدث، مكتبة Aspose.Words for Java (أو أي API يعكس فئة `PdfSaveOptions` الخاصة بها)، وملف Word تجريبي يحتوي على أشكال عائمة (البرنامج يستخدم `FloatingShapes.docx`). لا توجد أدوات خارجية أخرى مطلوبة.

---

## الخطوة 1: تحميل مستند Word المصدر

أول شيء تقوم به هو فتح ملف `.docx` الذي تريد تحويله. العملية بسيطة، لكن تأكد من أن المسار مطلق أو يتم حله بشكل صحيح من classpath الخاص بك.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*لماذا هذا مهم:*  
إذا لم يتم تحميل المستند بشكل صحيح، سيتسبب ذلك في رمي استثناء `FileNotFoundException` أثناء تحويل PDF. استخدام `Document` يضمن أن نموذج الكائن الداخلي مُعبأ بالكامل، بما في ذلك أي أشكال عائمة موجودة في الصفحة.

---

## الخطوة 2: إنشاء خيارات حفظ PDF وتعيين الأشكال العائمة داخل السطر

هنا يحدث السحر. بشكل افتراضي تقوم Aspose.Words بتصدير الأشكال العائمة كعناصر `<div>` على مستوى الكتلة، مما قد يعرقل تدفق المستند في PDFs المستندة إلى HTML. ضبط `setExportFloatingShapesAsInlineTag(true)` يخبر المحرك بلف كل شكل داخل وسمة `<span>` داخل السطر بدلاً من ذلك.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*لماذا هذا مهم:*  
- **دقة التخطيط** – الوسوم داخل السطر تحافظ على محاذاة الشكل مع النص المجاور، متجنبة الفجوات غير المرغوب فيها.  
- **قابلية البحث** – العناصر داخل السطر تُفهرس بشكل أفضل من قبل قارئات PDF.  
- **التحكم في التنسيق** – يمكنك استهداف `<span>` باستخدام CSS إذا قمت لاحقاً بتحويل PDF إلى HTML.

> **نصيحة محترف:** إذا احتجت في أي وقت إلى سلوك الكتلة القديم لمستند معين، ما عليك سوى تمرير `false` أو إهمال الاستدعاء تماماً.

---

## الخطوة 3: حفظ المستند كملف PDF باستخدام الخيارات المكوّنة

الآن تجمع بين `Document` المحمّل و`PdfSaveOptions` وتكتب الملف. هذا السطر الواحد يقوم بالعمل الشاق.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*لماذا هذا مهم:*  
طريقة `save` تحترم كل علامة ضبطتها على `pdfOptions`. نسيان تمرير الخيارات سيعيد التصدير إلى الوضع الافتراضي للكتلة، مما يبطل هدف **export floating shapes inline**.

---

## مثال كامل يعمل

بجمع كل ما سبق، إليك برنامج مختصر يمكنك تجميعه وتشغيله الآن. استبدل `YOUR_DIRECTORY` بمسار فعلي على جهازك.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**الناتج المتوقع** – بعد تشغيل البرنامج، افتح `FloatingShapes.pdf`. يجب أن ترى الأشكال متلاصقة مع النص، دون مساحة بيضاء إضافية، وستحتوي تمثيلة HTML الداخلية (إذا فحصت بنية PDF) على وسوم `<span>` حول كل شكل.

![Export floating shapes inline example](https://example.com/export-inline.png "Screenshot showing floating shapes rendered inline in the PDF")

*نص بديل للصورة:* **export floating shapes inline** لقطة شاشة لملف PDF يحتوي على أشكال داخل السطر.

---

## أسئلة شائعة وحالات حافة

### 1. “ماذا لو كان المستند يحتوي على SmartArt معقد؟”

يُعامل SmartArt ككائن رسم. علم العلامة داخل السطر يعمل لمعظم الأشكال المتجهية، لكن SmartArt المعقد قد يظل يُصدَّر كصورة. في هذه الحالة، فكر في تسطيح SmartArt في Word قبل التحويل، أو استخدم `pdfOptions.setExportSmartArtAsImage(true)` لإجبار تصديره كصورة.

### 2. “هل يمكنني دمج تصدير داخل السطر والكتلة في نفس المستند؟”

للأسف، التطبيق يطبق الإعداد على مستوى عالمي. إذا احتجت سلوكاً مختلطاً، قسّم المستند إلى أقسام، صدّر كل قسم على حدة بإعدادات مختلفة، ثم دمج ملفات PDF باستخدام `PdfMerger`.

### 3. “هل يؤثر هذا على تضمين الخطوط؟”

لا. يتم التحكم في تضمين الخطوط عبر `pdfOptions.setEmbedFullFonts(true)` (الإعداد الافتراضي). يمكنك تمكينه أو تعطيله بأمان دون لمس علم الشكل داخل السطر.

### 4. “كيف أتحقق من أن الأشكال فعلاً داخل وسوم `<span>`؟”

افتح PDF الناتج بأداة مثل **PDF.js** أو **Adobe Acrobat** → **Edit PDF** → **Object Inspector**. ستلاحظ الشكل ملفوفاً بوسم `<span>` في XML الأساسي. إذا رأيت `<div>`، فإن الخيار لم يُطبق.

---

## توسيع النهج – خيارات ذات صلة

بينما أنت هنا، قد ترغب أيضاً في استكشاف مفاتيح تحويل PDF الأخرى:

| الخيار | ما يفعله | حالة الاستخدام النموذجية |
|--------|----------|---------------------------|
| `setCompressImages(true)` | يقلل حجم الصور | تحميل أسرع |
| `setUseHighQualityRendering(true)` | يحسن جودة الرسم المتجه | PDFs جاهزة للطباعة |
| `setExportDocumentStructure(true)` | يضيف وسوم هيكلية لتحسين إمكانية الوصول | توافق WCAG |
| `setSaveFormat(SaveFormat.PDF)` | يحدد الصيغة صراحةً (نادرًا ما يُحتاج) | خطوط أنابيب متعددة الصيغ |

هذه الإعدادات تتكامل جيداً مع سيناريوهات **convert word to pdf inline** حيث تحتاج إلى كل من دقة التخطيط والأداء.

---

## اختبار التحويل الخاص بك

1. **فحص بصري** – افتح PDF في عارضين (Chrome وAdobe Reader) لتتأكد من محاذاة الأشكال.  
2. **مقارنة آلية** – استخدم مكتبة مثل `pdfbox` لاستخراج XML وتأكيد وجود وسوم `<span>`.  
3. **قياس الأداء** – قسّ الوقت المستغرق مع وبدون `setCompressImages` لتلاحظ الفرق.

مثال سريع باستخدام JUnit:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## الخلاصة

أصبح لديك الآن حل شامل من البداية إلى النهاية لـ **export floating shapes inline** عند **convert Word to PDF inline**. من خلال ضبط `PdfSaveOptions` تتحكم في الوسم HTML المستخدم لكل شكل، مما يبقي ملفات PDF منظمة وقابلة للبحث. تذكّر اختبار النتيجة، تعديل الخيارات المرتبطة مثل ضغط الصور، ومعالجة الحالات الخاصة مثل SmartArt المعقد.

هل أنت مستعد للخطوة التالية؟ جرّب تطبيق التقنية نفسها على **export floating tables inline** أو جرب PDFs مُنسقة بـ CSS باستخدام `HtmlSaveOptions` من Aspose. النمط نفسه—تحميل، تكوين، حفظ—ينطبق على أغلب سيناريوهات التحويل من مستند إلى PDF.

هل لديك أسئلة إضافية حول **how to set pdf options** أو تحتاج مساعدة في **save word as pdf options** لمكتبة مختلفة؟ اترك تعليقاً، ونتمنى لك برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Export Word Document Structure to PDF Document](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}