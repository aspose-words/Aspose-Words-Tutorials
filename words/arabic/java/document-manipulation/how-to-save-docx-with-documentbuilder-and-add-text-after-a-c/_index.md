---
category: general
date: 2026-10-07
description: تعلم كيفية حفظ ملف docx باستخدام DocumentBuilder، وإدراج عنصر تحكم نص
  عادي، وإضافة نص بعد العنصر في دليل واحد.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx with DocumentBuilder
- add text after control
- insert plain text control
language: ar
lastmod: 2026-10-07
og_description: احفظ ملف docx باستخدام DocumentBuilder، أدرج عنصر تحكم نص عادي، وأضف
  نصًا بعد العنصر باستخدام Aspose.Words للـ Java في هذا الدرس خطوة بخطوة.
og_image_alt: Screenshot showing a DOCX file created with DocumentBuilder after inserting
  a plain text control
og_title: حفظ ملف docx باستخدام DocumentBuilder – إدراج عنصر تحكم نص عادي وإضافة نص
  بعد العنصر
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save docx with DocumentBuilder, insert plain text control,
    and add text after control in a single guide.
  headline: How to save docx with DocumentBuilder and add text after a control
  type: TechArticle
- description: Learn how to save docx with DocumentBuilder, insert plain text control,
    and add text after control in a single guide.
  name: How to save docx with DocumentBuilder and add text after a control
  steps:
  - name: Prerequisites
    text: '* Java 17 or newer installed. * Maven 3.6+ for dependency management. *
      Basic familiarity with Java syntax and object‑oriented programming.'
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for constructing Word documents
      programmatically. * `insertStructuredDocumentTag` creates a **plain text control**
      (also called an SDT) that appears as a content control in Word. * Setting `Title`
      and `PlaceholderName` provides metadata and a hint for the end‑u'
  - name: Expected output screenshot (alt text for accessibility)
    text: '*Alt text:* “Word document showing a plain text content control labeled
      CustomerName followed by the line ‘After the tag’.”'
  type: HowTo
tags:
- Aspose.Words
- Java
- DocumentBuilder
title: كيفية حفظ ملف docx باستخدام DocumentBuilder وإضافة نص بعد عنصر التحكم
url: /ar/java/document-manipulation/how-to-save-docx-with-documentbuilder-and-add-text-after-a-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية حفظ docx باستخدام DocumentBuilder وإضافة نص بعد عنصر التحكم

إذا كنت بحاجة إلى **حفظ docx باستخدام DocumentBuilder**، فإن هذا الدرس يوضح لك بالضبط كيفية القيام بذلك. سترى كيفية **إدراج عنصر تحكم نص عادي**، وتعيين عنوانه ومكانه النائب، ثم **إضافة نص بعد عنصر التحكم** بحيث يقرأ المستند النهائي بشكل طبيعي.

في الأقسام أدناه نغطي كل شيء من إعداد المشروع إلى معالجة الحالات الخاصة، بحيث يمكنك نسخ‑لصق مثال كامل وقابل للتنفيذ في مشروع Java الخاص بك. لا توجد مراجع خارجية مطلوبة—فقط الشيفرة والتوضيحات المتوفرة هنا.

## ما ستتعلمه

* كيفية تكوين Aspose.Words for Java في مشروع Maven.  
* كيفية **إدراج عنصر تحكم نص عادي** (Structured Document Tag) باستخدام `DocumentBuilder`.  
* كيفية **إضافة نص بعد عنصر التحكم** بحيث يتدفق المحتوى المحيط بشكل صحيح.  
* كيفية **حفظ docx باستخدام DocumentBuilder** إلى مجلد مختار.  
* نصائح لتخصيص مظهر العنصر، ومعالجة الأماكن النائبة الفارغة، وإعادة استخدام الـ builder لعدة وسوم.

### المتطلبات المسبقة

* تثبيت Java 17 أو أحدث.  
* Maven 3.6+ لإدارة التبعيات.  
* إلمام أساسي بصياغة Java والبرمجة الكائنية.

---

## الخطوة 1: إعداد مشروع Maven وإضافة Aspose.Words

أولاً، أنشئ مشروع Maven جديد (أو أضف إلى مشروع موجود). أدرج تبعية Aspose.Words for Java في ملف `pom.xml` الخاص بك:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version at the time of writing -->
    </dependency>
</dependencies>
```

> **Pro tip:** Aspose.Words مكتبة تجارية، لكن رخصة التقييم المجانية تعمل للتطوير. سجّل على موقع Aspose للحصول على ملف الترخيص وحمّله وقت التشغيل لتجنب العلامات المائية.

## الخطوة 2: إنشاء فئة Java واستيراد الأنواع المطلوبة

أنشئ فئة باسم `DocxBuilderDemo`. استورد الفئات اللازمة للعمل مع `DocumentBuilder` و `StructuredDocumentTag` وتعداد المظهر.

```java
package com.example.docx;

import com.aspose.words.*;

public class DocxBuilderDemo {

    public static void main(String[] args) throws Exception {
        // Initialize the license if you have one (optional)
        // License license = new License();
        // license.setLicense("Aspose.Words.Java.lic");

        // Step 3: Build the document and insert the plain text control
        buildDocument();
    }

    private static void buildDocument() throws Exception {
        // Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text Structured Document Tag (SDT) with default appearance
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, SdtAppearanceTags.DEFAULT);

        // Set the tag's title and placeholder text to guide the user
        sdt.setTitle("CustomerName");
        sdt.setPlaceholderName("Enter name");

        // Step 4: Add regular content after the SDT
        builder.writeln("After the tag");

        // Step 5: Save the resulting document – this is where we **save docx with DocumentBuilder**
        String outputPath = "output/SDT.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### لماذا يعمل هذا

* `DocumentBuilder` هو الـ API الأساسي لإنشاء مستندات Word برمجيًا.  
* `insertStructuredDocumentTag` ينشئ **عنصر تحكم نص عادي** (يسمى أيضًا SDT) يظهر كعنصر تحكم محتوى في Word.  
* ضبط `Title` و `PlaceholderName` يضيف بيانات وصفية وتلميح للمستخدم النهائي.  
* `writeln` يضيف فقرة جديدة **بعد العنصر**، مما يلبي متطلب **إضافة نص بعد عنصر التحكم**.  
* أخيرًا، `doc.save` **يحفظ docx باستخدام DocumentBuilder** إلى نظام الملفات.

## الخطوة 3: تشغيل المثال والتحقق من النتيجة

1. قم بترجمة المشروع باستخدام `mvn clean compile`.  
2. نفّذ الفئة `DocxBuilderDemo` (`mvn exec:java -Dexec.mainClass="com.example.docx.DocxBuilderDemo"`).  
3. افتح `output/SDT.docx` في Microsoft Word أو LibreOffice.

يجب أن ترى مستندًا يحتوي على:

* عنصر تحكم محتوى بعنوان **CustomerName** مع المكان النائب “Enter name”.  
* النص **After the tag** في السطر التالي.

### لقطة الشاشة المتوقعة (نص بديل لسهولة الوصول)

*نص بديل:* “مستند Word يظهر عنصر تحكم نص عادي مسمى CustomerName يتبعه السطر ‘After the tag’.”

## الخطوة 4: تخصيص مظهر العنصر (اختياري)

إذا أردت أن يبدو العنصر مختلفًا—مثل صندوق حدود أو خلفية مظللة—استخدم تعداد `SdtAppearanceTags`:

```java
// Insert a plain‑text control with a bounding box appearance
StructuredDocumentTag sdtBox = builder.insertStructuredDocumentTag(
        StructuredDocumentTagType.PLAIN_TEXT, SdtAppearanceTags.BOUNDING_BOX);
sdtBox.setTitle("OrderNumber");
sdtBox.setPlaceholderName("Enter order #");
```

يمكنك تكرار نمط **إضافة نص بعد عنصر التحكم** لكل وسم تقوم بإدراجه:

```java
builder.writeln("First line after first tag");
builder.writeln("Second line after second tag");
```

## الخطوة 5: معالجة عدة عناصر تحكم وإعادة استخدام الـ builder

عند إنشاء نماذج، غالبًا ما تحتاج إلى عدة عناصر تحكم. يمكن لنفس نسخة `DocumentBuilder` إدراج العديد من الوسوم بشكل متتابع:

```java
String[] titles = {"FirstName", "LastName", "Email"};
for (String title : titles) {
    StructuredDocumentTag tag = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, SdtAppearanceTags.DEFAULT);
    tag.setTitle(title);
    tag.setPlaceholderName("Enter " + title.toLowerCase());
    builder.writeln(" "); // Add a space so the next tag starts on a new line
}
builder.writeln("All fields added above.");
```

تُظهر الحلقة كيفية **حفظ docx باستخدام DocumentBuilder** بعد مجموعة من عمليات **إضافة نص بعد عنصر التحكم**، مع الحفاظ على شفرة مختصرة.

## الحالات الخاصة واستكشاف الأخطاء وإصلاحها

| الحالة | ما يجب مراقبته | الحل المقترح |
|-----------|-------------------|-----------------|
| **دليل الإخراج غير موجود** | `doc.save` يرمي `FileNotFoundException` | تأكد من وجود الدليل (`new File("output").mkdirs();`) قبل استدعاء `save`. |
| **العنصر يظهر فارغًا في Word** | المكان النائب غير معروض | تحقق من ضبط `setPlaceholderName` **بعد** إدراج الوسم. |
| **لم يتم تحميل الترخيص** | ظهور العلامة المائية “Aspose.Words Evaluation” | حمّل ملف ترخيص صالح كما هو موضح في الخطوة 2. |
| **حروف Unicode مشوهة** | نص غير ASCII يظهر كـ � | احفظ المستند باستخدام `SaveFormat.DOCX` (الإعداد الافتراضي) وتأكد من أن ملفات المصدر مشفرة بـ UTF‑8. |

## مثال كامل جاهز للتنفيذ (نسخ‑لصق)

```java
package com.example.docx;

import com.aspose.words.*;

import java.io.File;

public class DocxBuilderDemo {

    public static void main(String[] args) throws Exception {
        // Optional: load license to remove evaluation watermark
        // License license = new License();
        // license.setLicense("Aspose.Words.Java.lic");

        // Ensure the output folder exists
        File outDir = new File("output");
        if (!outDir.exists()) outDir.mkdirs();

        // Build the document
        buildDocument(outDir.getAbsolutePath() + "/SDT.docx");
    }

    private static void buildDocument(String outputPath) throws Exception {
        // 1️⃣ Create a new document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a plain‑text Structured Document Tag (SDT)
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, SdtAppearanceTags.DEFAULT);
        sdt.setTitle("CustomerName");
        sdt.setPlaceholderName("Enter name");

        // 3️⃣ Add regular content after the SDT – this satisfies **add text after control**
        builder.writeln("After the tag");

        // 4️⃣ Save the resulting document – this is the core **save docx with DocumentBuilder** step
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

تشغيل هذه الفئة ينتج نفس ملف `SDT.docx` المذكور سابقًا.

---

## الخلاصة

الآن تعرف كيف **تحفظ docx باستخدام DocumentBuilder**، **تدرج عنصر تحكم نص عادي**، وت **ضيف نص بعد عنصر التحكم** باستخدام Aspose.Words for Java. يوضح مثال الشيفرة الكامل إعداد المشروع، إنشاء العنصر، إدراج المحتوى، وحفظ الملف في سير عمل موحد ومتكامل.

من هنا يمكنك:

* تجربة قيم أخرى لـ `StructuredDocumentTagType` (مثل `RICH_TEXT` أو `DATE`).  
* دمج عدة عناصر تحكم لبناء نماذج معقدة.  
* تطبيق تنسيقات مخصصة على الفقرات المحيطة للحصول على مظهر مصقول.

لا تتردد في تعديل النمط لاحتياجات توليد المستندات الخاصة بك، ومشاركة نتائجك في التعليقات أو على GitHub. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة‑بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Save docx as pdf with Java – Complete Step‑by‑Step Guide](/words/english/java/document-conversion-and-export/save-docx-as-pdf-with-java-complete-step-by-step-guide/)
- [Save docx as markdown in Java – Complete Step‑by‑Step Guide](/words/english/java/document-conversion-and-export/save-docx-as-markdown-in-java-complete-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}