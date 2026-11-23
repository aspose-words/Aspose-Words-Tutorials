---
category: general
date: 2026-11-22
description: تعلم كيفية إضافة شكل إلى Word باستخدام Aspose.Words for Java – أدخل مستطيلًا
  وأخفِه برمجيًا.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: ar
lastmod: 2026-11-22
og_description: أضف شكلاً إلى Word باستخدام Aspose.Words للغة Java. يوضح هذا الدرس
  كيفية إدراج مستطيل، إخفاء الشكل، وحفظ المستند.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: إضافة شكل إلى Word باستخدام Aspose.Words – دليل Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: كيفية إضافة شكل إلى مستندات Word باستخدام Aspose.Words للـ Java
url: /ar/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة شكل إلى مستندات Word باستخدام Aspose.Words for Java

إذا كنت بحاجة إلى **إضافة شكل إلى مستندات Word** برمجياً، فإن Aspose.Words for Java يجعل ذلك بسيطًا. في هذا الدليل ستتعلم **كيفية إدراج شكل**، والتحكم في رؤيته، و**كيفية إخفاء الشكل** بحيث يبدو الملف النهائي تمامًا كما تتوقع.

ستستعرض مثالًا كاملاً وقابلًا للتنفيذ يقوم بتحميل ملف `.docx` موجود، وإدراج مستطيل، وإخفائه، ثم حفظ النتيجة. لا تحتاج إلى أي سكريبتات خارجية أو خطوات يدوية، ويغطي الدرس تنويعات شائعة مثل إنشاء مستند جديد من الصفر أو إخفاء الشكل فقط عند الطباعة.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود:

* Java 17 (أو أحدث) مثبت – الإصدارات السابقة تعمل لكن أحدث نسخة LTS توفر أداءً أفضل.  
* Maven 3.8+ لإدارة التبعيات.  
* رخصة صالحة لـ Aspose.Words for Java (التقييم المجاني يكفي للتعلم).  
* بيئة تطوير متكاملة أو محرر نصوص حسب اختيارك (مثل IntelliJ IDEA، VS Code).

## الخطوة 1: إضافة Aspose.Words إلى مشروع Maven الخاص بك

أضف التبعية التالية إلى ملف `pom.xml`. سيقوم هذا بجلب أحدث نسخة مستقرة (اعتبارًا من نوفمبر 2026).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **نصيحة احترافية:** استخدم جملة `<scope>provided</scope>` إذا كنت تخطط لتوزيع الـ JAR مع منطق الترخيص الخاص بك.

## إضافة شكل إلى Word – تهيئة المستند

الخطوة الوظيفية الأولى هي الحصول على كائن `Document`. يمكنك إما تحميل ملف موجود أو إنشاء مستند جديد.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*لماذا هذا مهم*: فئة `Document` هي نقطة الدخول لجميع عمليات تعديل Word. تحميل ملف موجود يحافظ على الأنماط، والرؤوس، والتذييلات، بينما يمنحك المستند الجديد صفحة فارغة.

## كيفية إدراج شكل في مستند Word

بعد ذلك، أنشئ كائن `DocumentBuilder` لتعديل محتوى المستند. يوفّر الـ builder طرقًا لإدراج النصوص، والجداول، و**الأشكال**.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

تُعيد استدعاء `insertShape` كائن `Shape` يمكنك تكوينه أكثر (اللون، الحدود، النص، إلخ). الأبعاد تُعبّر بالنقاط (1 pt = 1/72 in).

*لماذا قد تستخدم مستطيلًا*: المستطيلات هي الحاوية الأكثر شيوعًا للتعليقات، والعلامات المائية، أو العناصر النائبة. يمكنك استبدال `ShapeType.RECTANGLE` بـ `ShapeType.ELLIPSE` أو `ShapeType.LINE`، إلخ، لتلبية احتياجات بصرية مختلفة.

## كيفية إخفاء الشكل في Word

أحيانًا تحتاج إلى وجود شكل لحسابات التخطيط ولكن لا تريد ظهوره في العرض النهائي. توفر Aspose.Words طريقة `setHidden(true)` لتحقيق ذلك.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

علامة الإخفاء تعمل مثل خيار **Hidden** في تنسيق Microsoft Word: يُستبعد الشكل من التخطيط البصري لكنه لا يزال جزءًا من نموذج كائنات المستند. هذا مفيد لـ:

* تخزين بيانات تعريفية أو علامات يقرأها تطبيقك لاحقًا.  
* إنشاء عناصر نائبة تُزال قبل النشر مباشرة.  
* التحكم في الرؤية لتنسيقات إخراج مختلفة (مثلاً، إخفاء في HTML مع الإبقاء في PDF).

> **ملاحظة:** الأشكال المخفية لا تزال تُصدّر إلى PDF بشكل افتراضي. إذا كنت تريد إزالتها من PDF أيضًا، اضبط `rectangle.getWrapType( ) = WrapType.NONE` وعدّل خاصية `Hidden` وفقًا لذلك.

## الخطوة 4: حفظ المستند المعدل

أخيرًا، احفظ التغييرات في ملف جديد.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

عند فتح `output.docx` في Microsoft Word، لن يكون المستطيل مرئيًا، لكنه يظل جزءًا من شجرة المستند. يمكنك التحقق من وجوده برمجيًا بإعادة تحميل الملف وفحص `Shape.isHidden()`.

### النتيجة المتوقعة

* يفتح الملف `output.docx` دون أي أشكال مرئية.  
* إذا فحصت المستند باستخدام Aspose.Words (مثال: `doc.getChildNodes(NodeType.SHAPE, true).size()`)، سيكون عدد الأشكال **1**، مما يؤكد أن الشكل موجود لكنه مخفي.

## تنويعات متقدمة وحالات حافة

### 1. إنشاء شكل في مستند جديد

إذا بدأت من الصفر، استبدل سطر التحميل بـ:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. تموضع الشكل بدقة

بشكل افتراضي، يضع `insertShape` الشكل في موقع المؤشر الحالي. لتموضعه بشكل مطلق:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. التحكم في الرؤية حسب تنسيق الإخراج

إذا كنت تحتاج إلى ظهور الشكل في واجهة Word لكن إخفاؤه عند تصديره إلى PDF، استخدم `Shape.setWrapType(WrapType.NONE)` مع خاصية `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. إضافة نص داخل الشكل

يمكن للمستطيل أن يحتوي على إطار نصي:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

يمكنك بعد ذلك إخفاء صندوق النص بنفس استدعاء `setHidden(true)`.

## الأخطاء الشائعة وكيفية تجنبها

| العَرَض | السبب | الحل |
|---------|-------|-----|
| الشكل يظهر حتى بعد `setHidden(true)` | تم حفظ المستند قبل تعيين علامة الإخفاء. | تأكد من استدعاء `setHidden(true)` **قبل** `doc.save()`. |
| حجم الشكل مشوّه | خلط بين النقاط والبكسلات على شاشات عالية الدقة. | استخدم النقاط (72 pt = 1 in) للحصول على حجم ثابت عبر المنصات. |
| الشكل المخفي لا يزال يُطبع | بعض الطابعات تتجاهل علامة الإخفاء. | اضبط `Shape.setWrapType(WrapType.NONE)` وكذلك امسح `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`. |

## الخلاصة

أنت الآن تعرف كيف **تضيف شكلًا إلى مستندات Word** باستخدام Aspose.Words for Java، **كيف تُدرج شكلًا**، و**كيف تُخفي الشكل** بحيث يبقى غير مرئي للمستخدمين النهائيين ومع ذلك يكون جزءًا من بنية المستند. المثال الكامل أعلاه يقوم بتحميل ملف، وإدراج مستطيل، وإخفائه، ثم حفظ النتيجة، مع تغطية كل من حالات الاستخدام النموذجية وبعض حالات الحافة.

من هنا يمكنك استكشاف مواضيع ذات صلة مثل **كيفية إدراج شكل** بألوان تعبئة مخصصة، **كيفية إخفاء الشكل في Word** للطباعة الشرطية، أو أتمتة معالجة المستندات بالجملة باستخدام Aspose.Words. جرّب قيم `ShapeType` المختلفة، وخيارات التموضع، وعلامات الرؤية لتتناسب مع سير عملك الخاص.

برمجة سعيدة، واستمتع بالمرونة التي يوفرها التلاعب البرمجي بـ Word لتطبيقات Java الخاصة بك!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word برمجيًا، إضافة وإخفاء شكل في Java باستخدام Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [كيفية إخفاء شكل في مستند Word باستخدام Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [إنشاء مستند Word .docx فارغ وإضافة شكل مستطيل مخفي باستخدام Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}