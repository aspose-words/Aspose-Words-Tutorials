---
category: general
date: 2026-05-26
description: إنشاء PDF قابل للوصول في Java مع كود خطوة بخطوة. تعلّم كيفية وضع علامات
  PDF لتسهيل الوصول وتمكين وضع العلامات باستخدام PdfSaveOptions.
draft: false
keywords:
- create accessible pdf
- how to tag pdf for accessibility
- how to create tagged pdf
- add accessibility tags to pdf
- enable pdf tagging
language: ar
og_description: إنشاء ملف PDF قابل للوصول في Java مع كود خطوة بخطوة. تعلم كيفية وضع
  علامات PDF لتسهيل الوصول وتمكين وضع العلامات باستخدام PdfSaveOptions.
og_title: إنشاء PDF قابل للوصول في Java – دليل كامل للوسم
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create accessible PDF in Java with step‑by‑step code. Learn how to
    tag PDF for accessibility and enable PDF tagging using PdfSaveOptions.
  headline: Create Accessible PDF in Java – Full Tagging Guide
  type: TechArticle
- description: Create accessible PDF in Java with step‑by‑step code. Learn how to
    tag PDF for accessibility and enable PDF tagging using PdfSaveOptions.
  name: Create Accessible PDF in Java – Full Tagging Guide
  steps:
  - name: 1. Set Document Language
    text: Screen readers use the language attribute to pronounce text correctly.
  - name: 2. Provide a Title and Subject
    text: Metadata helps assistive tools give context before the user even opens the
      file.
  - name: 3. Tag Images with Alternative Text
    text: If you embed pictures, they need `alt` descriptions.
  - name: 4. Mark Table Headers
    text: Tables are notorious for confusing readers unless you flag header rows.
  type: HowTo
tags:
- PDF
- Java
- Accessibility
title: إنشاء PDF ميسّر في جافا – دليل كامل للوسم
url: /ar/java/document-conversion-and-export/create-accessible-pdf-in-java-full-tagging-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء PDF يمكن الوصول إليه في Java – دليل كامل للوسم

هل تساءلت يومًا كيف يمكنك **إنشاء PDF يمكن الوصول إليه** مباشرةً من كود Java؟ لست وحدك. يحتاج العديد من المطورين إلى خدمة المستخدمين الذين يعتمدون على قارئات الشاشة، والفارق بين PDF عادي وPDF يمكن الوصول إليه يمكن أن يكون هائلًا. في هذا الدرس سنستعرض **كيفية وسم PDF لتسهيل الوصول**, ونظهر لك **كيفية إنشاء PDF موسوم** باستخدام Aspose PDF for Java، ونكشف الخطوات الدقيقة **لإضافة وسوم الوصول إلى PDF** حتى يحصل كل قارئ على نفس المعلومات.

سنغطي أيضًا **أفضل ممارسات تمكين وسم PDF**، والمشكلات الشائعة، ومثالًا كاملاً قابلًا للتنفيذ يمكنك إدراجه في مشروعك اليوم. لا مراجع غامضة—فقط كود ملموس، شروحات، وملف نهائي يمكنك فتحه في Adobe Acrobat للتحقق من الوسوم.

## ما ستتعلمه

- السبب وراء وسم PDF والامتثال لإمكانية الوصول.
- المتطلبات وإعداد المكتبة (Aspose PDF for Java 23.10 أو أحدث).
- **كيفية إنشاء PDF يمكن الوصول إليه** من الصفر، خطوة بخطوة.
- طرق **إضافة وسوم الوصول إلى PDF** بخلاف استدعاء `setTagDocumentStructure` الأساسي.
- نصائح لاختبار النتيجة وحل المشكلات الشائعة.

بنهاية هذا الدليل ستكون قادرًا على توليد ملفات PDF تجتاز فحوصات WCAG 2.1 AA وتبدو احترافية في الوقت نفسه.

---

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من وجود ما يلي:

| المتطلبات | السبب |
|-------------|--------|
| **Java 8+** | ميزات لغة حديثة وتعامل أفضل مع Unicode. |
| **Aspose PDF for Java** (v23.10 أو أحدث) | يوفر الفئة `PdfSaveOptions` ودعم الوسم. |
| **IDE** (IntelliJ IDEA, Eclipse, VS Code, إلخ) | لتسهيل التجميع وتصحيح الأخطاء. |
| **إذن كتابة** إلى مجلد سيتم حفظ PDF فيه | استدعاء `doc.save` يحتاج مسارًا قابلًا للكتابة. |

إذا لم تقم بعد بإضافة Aspose PDF إلى مشروعك، ضع تبعية Maven التالية في ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-pdf</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **نصيحة احترافية:** استخدم أحدث إصدار؛ الإصدارات الأحدث تحسن دقة الوسم وتضيف ميزات إمكانية وصول مخصصة للغة.

---

## الخطوة 1: إعداد هيكل المستند

أولاً، نقوم بإنشاء كائن `Document` جديد. فكر فيه كقماش فارغ سيحمل لاحقًا الوسوم التي نحتاجها لإمكانية الوصول.

```java
import com.aspose.pdf.*;

public class AccessiblePdfDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new PDF document – the foundation for create accessible pdf
        Document doc = new Document();

        // Add a single page – you can add more later if needed
        Page page = doc.getPages().add();

        // Insert some readable content
        TextFragment fragment = new TextFragment("Hello, accessible PDF!");
        page.getParagraphs().add(fragment);
```

**لماذا هذا مهم:** بدون أي محتوى، لا شيء يمكن وسمه. إضافة حتى `TextFragment` بسيط يمنح محرك الوسم شيئًا للعمل معه، وهو ينشئ تلقائيًا وسم `<P>` (فقرة) عندما نقوم بتمكين وسم الهيكل لاحقًا.

## الخطوة 2: إنشاء خيارات حفظ PDF (جوهر الوسم)

الآن نجهز الخيارات التي تخبر Aspose PDF بدمج شجرة هيكل منطقية داخل الملف.

```java
        // Step 1: Create PDF save options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();

        // Step 2: Enable document structure tagging for accessibility
        pdfOptions.setTagDocumentStructure(true);
```

الاستدعاء `setTagDocumentStructure(true)` هو مفتاح **تمكين وسم PDF**. عندما يكون true، تُنشئ المكتبة شجرة وسوم تعكس التخطيط البصري، مما يجعل PDF قابلًا للقراءة بواسطة تقنيات المساعدة.

> **ملاحظة:** هذه أبسط طريقة لـ **كيفية إنشاء PDF موسوم**. للحصول على تحكم أكثر تفصيلًا (مثل تعيين اللغة أو وسوم مخصصة)، يمكنك استكشاف `pdfOptions.setTagLanguage("en-US")` و `pdfOptions.setTagStructureTreeRoot(...)`.

## الخطوة 3: حفظ PDF القابل للوصول

أخيرًا، نكتب المستند إلى القرص باستخدام الخيارات التي أعددناها للتو.

```java
        // Step 3: Save the document as an accessible PDF
        doc.save("output/accessible.pdf", pdfOptions);
    }
}
```

عند انتهاء `doc.save`، ستجد الملف `accessible.pdf` في مجلد `output`. افتحه في Adobe Acrobat وانتقل إلى **File → Properties → Description → Tags** – يجب أن ترى شجرة وسوم مكتملة.

## كيفية وسم PDF لتسهيل الوصول – ما بعد الأساسيات

المقتطف المكوّن من ثلاث خطوات أعلاه يضيف بالفعل **وسوم الوصول إلى PDF**، لكن المستندات الواقعية غالبًا ما تحتاج إلى لمسة إضافية. إليك بعض التحسينات التي يمكنك إضافتها:

### 1. تعيين لغة المستند

تستخدم قارئات الشاشة سمة اللغة لنطق النص بشكل صحيح.

```java
pdfOptions.setTagLanguage("en-US");
```

### 2. توفير عنوان وموضوع

البيانات الوصفية تساعد الأدوات المساعدة على إعطاء سياق قبل أن يفتح المستخدم الملف.

```java
doc.setTitle("Welcome Letter");
doc.setSubject("Accessible PDF example");
```

### 3. وسم الصور بنص بديل

إذا أدرجت صورًا، تحتاج إلى أوصاف `alt`.

```java
Image image = new Image();
image.setFile("logo.png");
image.getAlternativeText().setValue("Company logo");
page.getParagraphs().add(image);
```

### 4. تعليم رؤوس الجداول

الجداول تميل إلى إرباك القارئات ما لم تُعلم صفوف الرؤوس.

```java
Table table = new Table();
table.setColumnWidths("100 100");
Row header = table.getRows().add();
header.getCells().add("Name");
header.getCells().add("Score");
header.getCells().get_Item(0).setIsHeader(true);
header.getCells().get_Item(1).setIsHeader(true);
```

هذه الخطوات الإضافية تجعل PDF الخاص بك ليس مجرد *موسوم* تقنيًا، بل **قابلًا للوصول** حقًا لجمهور متنوع.

## المشكلات الشائعة عند تمكين وسم PDF

| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| الوسوم مفقودة في Acrobat | ترك `setTagDocumentStructure` على `false` | تأكد من استدعاء `pdfOptions.setTagDocumentStructure(true)`. |
| ترتيب القراءة خاطئ | تخطيط معقد بدون وسوم صريحة | استخدم `pdfOptions.setTagStructureTreeRoot(...)` لتحديد ترتيب مخصص. |
| تُقرأ الصور كـ “image” بدون وصف | عدم تعيين نص بديل | استدعِ `image.getAlternativeText().setValue("...")`. |
| اللغة غير معترف بها | إغفال `setTagLanguage` أو تعيين locale غير صحيح | قدم رمز لغة BCP‑47 (`en-US`, `fr-FR`). |

الوعي بهذه القضايا سيوفر لك ساعات من التصحيح لاحقًا.

## التحقق من النتيجة – ما المتوقع

بعد تشغيل البرنامج، افتح `output/accessible.pdf` في Adobe Acrobat Reader:

1. **لوحة الوسوم** (`View → Show/Hide → Navigation Panes → Tags`) يجب أن تعرض تسلسلًا هرميًا مثل `/Document → /Part → /Sect → /Para`.  
2. **ترتيب القراءة** يجب أن يتبع التدفق البصري (النص أولًا، ثم الصور).  
3. **قارئ الشاشة** (NVDA, VoiceOver) سيقرأ “Hello, accessible PDF!” بدلاً من مجرد “Page 1”.

إذا كان أي من هذه العناصر مفقودًا، راجع الخطوات السابقة—خاصة استدعاء `setTagDocumentStructure`.

## مثال كامل جاهز للتنفيذ (انسخه‑الصق)



## دروس ذات صلة

- [إنشاء PDF يمكن الوصول إليه من Word – التحويل إلى PDF/UA](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-word-convert-to-pdf-ua/)
- [إنشاء PDF يمكن الوصول إليه من DOCX – دليل كامل](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-complete-guide/)
- [كيفية حفظ المستند كـ PDF باستخدام Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}