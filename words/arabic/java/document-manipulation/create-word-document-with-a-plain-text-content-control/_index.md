---
category: general
date: 2026-10-04
description: إنشاء مستند Word باستخدام Java يتضمن عنصر تحكم نص عادي ومكان حامل. تعلم
  كيفية إضافة المكان الحامل إلى الوسم وكيفية إدراج sdt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- plain text content control
- docx with placeholder
- add placeholder to tag
- how to insert sdt
language: ar
lastmod: 2026-10-04
og_description: إنشاء مستند Word مع عنصر تحكم محتوى نص عادي وعنصر نائب. يوضح هذا البرنامج
  التعليمي كيفية إضافة العنصر النائب إلى الوسم وكيفية إدراج sdt باستخدام Aspose.Words
  for Java.
og_image_alt: Screenshot of a generated DOCX showing a plain text content control
  with placeholder
og_title: إنشاء مستند Word مع التحكم بالمحتوى – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  headline: Create word document with a plain text content control
  type: TechArticle
- description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  name: Create word document with a plain text content control
  steps:
  - name: Initialise the document and builder
    text: '```java import com.aspose.words.*;'
  - name: Insert a plain‑text Structured Document Tag (SDT)
    text: '```java private static void insertPlainTextControl(DocumentBuilder builder)
      throws Exception { // Step 2 – create a plain text content control (SDT) with
      a unique tag name StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
      StructuredDocumentTagType.PLAIN_TEXT, "MyTag");'
  - name: Add regular content after the SDT
    text: '```java private static void addTrailingContent(DocumentBuilder builder)
      throws Exception { // Step 3 – write a line after the SDT to prove the control
      is correctly positioned builder.writeln("After SDT"); } ```'
  - name: Save the resulting file
    text: '```java private static void saveDocument(Document doc) throws Exception
      { // Step 4 – persist the document as a DOCX with placeholder String outPath
      = "SdtDemo.docx"; doc.save(outPath); System.out.println("Document saved to "
      + outPath); } ```'
  - name: Expected output
    text: 'Running the program creates `SdtDemo.docx`. Opening the file in Word shows:'
  - name: Next steps
    text: '* Explore **how to insert sdt** inside tables for form‑like layouts. *
      Combine this technique with **docx with placeholder** merging to build automated
      report generators. * Experiment with other control types (`RICH_TEXT`, `CHECKBOX`)
      to create richer Word forms.'
  type: HowTo
tags:
- Word
- Java
- Aspose.Words
title: إنشاء مستند Word مع عنصر تحكم نص عادي
url: /ar/java/document-manipulation/create-word-document-with-a-plain-text-content-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word مع عنصر تحكم نص عادي

إذا كنت بحاجة إلى **إنشاء مستند Word** يحتوي على منطقة يمكن للمستخدم تحريرها، فإن عنصر تحكم النص العادي هو النهج الأكثر موثوقية. يوضح هذا الدرس بالضبط كيفية إدراج Structured Document Tag (SDT)، وتعيين عنصر نائب، وحفظ النتيجة كـ **docx مع عنصر نائب**. سترى مثال Java كامل قابل للتنفيذ يعمل مع Aspose.Words for Java 23.8.

الدليل يغطي جميع المتطلبات المسبقة، يشرح لماذا كل استدعاء API مهم، ويقدم نصائح للتعامل مع الحالات الخاصة مثل العناصر النائبة متعددة اللغات أو العلامات المتداخلة. في النهاية يمكنك إنشاء ملف Word يطلب من المستخدمين “Enter text…” مباشرة داخل المستند.

## المتطلبات المسبقة

* Java 17 (أو أحدث) مثبت ومُعد في PATH الخاص بك.  
* Maven 3.8+ لإدارة التبعيات.  
* ترخيص Aspose.Words for Java (التقييم يعمل للاختبار).  
* بيئة تطوير متكاملة (IntelliJ IDEA، Eclipse، أو VS Code).

أضف Aspose.Words إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.8</version>
</dependency>
```

## إنشاء مستند Word مع عنصر تحكم نص عادي

تتكون سير العمل الأساسي من أربع خطوات منطقية. كل خطوة محاطة بطريقة مسماة بوضوح حتى يمكنك إعادة استخدام المنطق في مشاريع أكبر.

### الخطوة 1: تهيئة المستند والباني

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Step 1 – create an empty Document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        insertPlainTextControl(builder);
        addTrailingContent(builder);
        saveDocument(doc);
    }
}
```

**لماذا هذا مهم:** `Document` تمثل ملف Word في الذاكرة. `DocumentBuilder` هو API سلس يتيح لك إدراج فقرات وجداول وSDTs. البدء بمستند فارغ يضمن ظهور العنصر النائب في البداية تمامًا، وهو مفيد للقوالب.

### الخطوة 2: إدراج Structured Document Tag (SDT) نص عادي

```java
private static void insertPlainTextControl(DocumentBuilder builder) throws Exception {
    // Step 2 – create a plain text content control (SDT) with a unique tag name
    StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, "MyTag");

    // Step 2.1 – add a placeholder that appears when the tag is empty
    sdt.setPlaceholderName("Enter text…");   // add placeholder to tag
}
```

**لماذا هذا مهم:** `StructuredDocumentTagType.PLAIN_TEXT` ينشئ عنصر تحكم يقبل فقط أحرفًا عادية، مما يمنع التنسيق العرضي. استدعاء `setPlaceholderName` يملأ نص التلميح الرمادي الذي يراه المستخدمون قبل الكتابة—هذا هو عملية **إضافة عنصر نائب إلى العلامة** التي تجعل المستند يبدو كاستمارة.

### الخطوة 3: إضافة محتوى عادي بعد الـ SDT

```java
private static void addTrailingContent(DocumentBuilder builder) throws Exception {
    // Step 3 – write a line after the SDT to prove the control is correctly positioned
    builder.writeln("After SDT");
}
```

**لماذا هذا مهم:** إضافة محتوى بعد عنصر التحكم يتحقق من أن الـ SDT لا يستهلك تدفق المستند بالكامل. كما يوضح كيفية دمج العلامات المهيكلة مع الفقرات العادية، وهو مطلب شائع عند بناء القوالب.

### الخطوة 4: حفظ الملف الناتج

```java
private static void saveDocument(Document doc) throws Exception {
    // Step 4 – persist the document as a DOCX with placeholder
    String outPath = "SdtDemo.docx";
    doc.save(outPath);
    System.out.println("Document saved to " + outPath);
}
```

**لماذا هذا مهم:** طريقة `save` تكتب النموذج الموجود في الذاكرة إلى ملف فعلي **docx مع عنصر نائب**. يمكن فتح الملف الناتج في Microsoft Word أو LibreOffice أو أي مكتبة تدعم صيغة OpenXML.

## الكود المصدر الكامل

جمع الأجزاء معًا يمنحك برنامجًا مستقلًا يمكنك تجميعه وتشغيله:

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Initialise document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert plain‑text content control and set placeholder
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, "MyTag");
        sdt.setPlaceholderName("Enter text…");   // add placeholder to tag

        // Add normal text after the control
        builder.writeln("After SDT");

        // Save the file
        String outPath = "SdtDemo.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### النتيجة المتوقعة

تشغيل البرنامج ينشئ `SdtDemo.docx`. فتح الملف في Word يظهر:

* عنصر نائب رمادي “Enter text…” داخل عنصر تحكم نص عادي يحمل التسمية **MyTag**.  
* السطر **After SDT** مباشرةً أسفل عنصر التحكم.

يختفي العنصر النائب بمجرد أن يبدأ المستخدم بالكتابة، مع الحفاظ على التنسيق الأصلي.

## الاختلافات الشائعة والحالات الخاصة

| السيناريو | التغيير الموصى به |
|----------|--------------------|
| **Multilingual placeholder** | استخدم أحرف Unicode في `setPlaceholderName`، على سبيل المثال `sdt.setPlaceholderName("Введите текст…");`. |
| **Nested content controls** | أدخل SDT ثاني داخل الأول عن طريق استدعاء `builder.moveTo(sdt.getParagraph());` قبل `insertStructuredDocumentTag` الثاني. |
| **Read‑only control** | استدعِ `sdt.setLockContentControl(true);` لمنع المستخدمين من حذف العلامة. |
| **Rich‑text instead of plain text** | استبدل `StructuredDocumentTagType.PLAIN_TEXT` بـ `StructuredDocumentTagType.RICH_TEXT`. |
| **Saving to a stream** | استخدم `doc.save(OutputStream, SaveFormat.DOCX);` عندما تحتاج لإرسال الملف عبر HTTP. |

## نصائح احترافية

* **إعادة استخدام معرفات العلامات** – إذا قمت بإنشاء العديد من المستندات من نفس القالب، حافظ على اسم العلامة (`"MyTag"`) ثابتًا حتى يتمكن المعالجة اللاحقة (مثل دمج البريد) من العثور عليها بشكل موثوق.  
* **الأداء** – بالنسبة للقوالب الكبيرة، أنشئ `DocumentBuilder` مرة واحدة وأعد استخدامها؛ إدراج العديد من الـ SDTs داخل حلقة أسرع من إعادة إنشاء الباني في كل تكرار.  
* **الاختبار** – بعد إنشاء ملف DOCX، تحقق برمجيًا من وجود العنصر النائب باستخدام `doc.getRange().getStructuredDocumentTags().getCount()`.

## الخلاصة

أنت الآن تعرف كيف **إنشاء مستند Word** يحتوي على **عنصر تحكم نص عادي** مع عنصر نائب مخصص، مما ينتج فعليًا **docx مع عنصر نائب** جاهز لإدخال المستخدم. يوضح المثال الدورة الكاملة من تهيئة المستند، **كيفية إدراج sdt**، **إضافة عنصر نائب إلى العلامة**، إضافة محتوى عادي، وأخيرًا حفظ الملف.

### الخطوات التالية

* استكشف **كيفية إدراج sdt** داخل الجداول لتصميمات شبيهة بالنماذج.  
* اجمع هذه التقنية مع دمج **docx مع عنصر نائب** لبناء مولدات تقارير آلية.  
* جرب أنواع عناصر تحكم أخرى (`RICH_TEXT`، `CHECKBOX`) لإنشاء نماذج Word أغنى.

لا تتردد في تعديل الكود ليناسب محرك القوالب الخاص بك، وشارك نتائجك في التعليقات!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [إنشاء مستند Word Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [كيفية إنشاء مستندات PDF باستخدام Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}