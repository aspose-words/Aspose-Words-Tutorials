---
category: general
date: 2026-08-23
description: إنشاء مستند Word فارغ باستخدام Aspose.Words للغة Java، وتعلم كيفية تجميع
  الأشكال، وتلوين شكل المستطيل، وحفظ المستند بصيغة docx في دقائق.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: ar
lastmod: 2026-08-23
og_description: إنشاء مستند Word فارغ باستخدام Aspose.Words for Java، ثم معرفة كيفية
  تجميع الأشكال، وتلوين شكل المستطيل، وحفظ المستند بصيغة docx بكفاءة.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: إنشاء مستند Word فارغ وتجميع الأشكال في Java – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: إنشاء مستند Word فارغ وتجميع الأشكال في Java
url: /ar/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ وتجميع الأشكال في Java

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** برمجياً، فإن Aspose.Words for Java يجعل ذلك بسيطًا. يوضح لك هذا الدليل بالضبط كيفية **إنشاء مستند Word فارغ**، وإدراج **تجميع الأشكال في Word**، وتطبيق **شكل مستطيل ملون**، وأخيرًا **حفظ المستند كملف docx**. في النهاية ستحصل على قطعة كود قابلة لإعادة الاستخدام يمكنك وضعها في أي مشروع Java.

ستتعلم:

* التبعية المطلوبة لـ Maven/Gradle لـ Aspose.Words.
* كيفية إنشاء مستند فارغ و`DocumentBuilder`.
* الخطوات الدقيقة لـ **كيفية تجميع الأشكال** داخل `GroupShape`.
* كيفية تعيين ألوان التعبئة لأشكال المستطيل.
* أفضل الممارسات لـ **حفظ المستند كملف docx** وأين يمكنك العثور على ملف الإخراج.

لا يُفترض أن لديك خبرة سابقة مع Aspose.Words، لكن يجب أن تكون مرتاحًا مع تطوير Java الأساسي وأن يكون لديك JDK 8 أو أحدث مثبتًا.

---

## المتطلبات المسبقة

| المتطلب | الإصدار / التفاصيل |
|---------|----------------------|
| مجموعة تطوير جافا | 8 أو أعلى |
| أداة البناء | Maven 3+ أو Gradle 6+ |
| Aspose.Words for Java | 23.12 أو أحدث (أحدث نسخة وقت الكتابة) |
| بيئة التطوير المتكاملة (اختياري) | IntelliJ IDEA, Eclipse, VS Code, أو أي محرر متوافق مع Java |

---

## الخطوة 1: إضافة Aspose.Words إلى مشروعك

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **نصيحة احترافية:** إذا كنت تستخدم بروكسيً مؤسسيًا، قم بتهيئة Maven/Gradle لسحب الحزمة من مستودع Aspose كما هو موضح في الوثائق الرسمية.

---

## الخطوة 2: **إنشاء مستند Word فارغ** باستخدام منشئ

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

منشئ `Document` ينشئ حاوية `.docx` فارغة في الذاكرة. يوفر لك `DocumentBuilder` واجهة برمجة تطبيقات سلسة لإضافة المحتوى، بما في ذلك الأشكال.

---

## الخطوة 3: إدراج حاوية **تجميع الأشكال في Word**

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

`GroupShape` يعمل كقماش صغير. جميع الأشكال المضافة إليه تتحرك معًا، وهذا بالضبط **كيفية تجميع الأشكال** لتحقيق اتساق التخطيط.

---

## الخطوة 4: إضافة أول **شكل مستطيل ملون** (أحمر)

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

الثابت `ShapeType.RECTANGLE` ينشئ مستطيلًا بسيطًا. عبر استدعاء `getFill().setForeColor(...)` يمكنك التحكم في **شكل المستطيل الملون**. يمكنك استبدال `java.awt.Color.RED` بأي ثابت `java.awt.Color` أو قيمة RGB مخصصة.

---

## الخطوة 5: إضافة ثاني **شكل مستطيل ملون** (أخضر) وتحديد موقعه

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

ضبط `setLeft` (أو `setTop`) ينقل الشكل بالنسبة إلى الزاوية العلوية اليسرى لحاوية **تجميع الأشكال في Word**. هذا يوضح **كيفية تجميع الأشكال** مع تحديد موقع دقيق.

---

## الخطوة 6: **حفظ المستند كملف docx** والتحقق من النتيجة

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

طريقة `save` تكتب تلقائيًا ملف `.docx` لأن امتداد الملف هو `.docx`. إذا كنت بحاجة إلى تنسيق مختلف (مثل PDF)، مرّر التعداد المناسب `SaveFormat`.

> **نصيحة:** تأكد من وجود دليل الهدف (`output/` في هذا المثال) أو أنشئه برمجيًا باستخدام `new File("output").mkdirs();`.

---

## الكود الكامل للنسخ السريع

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**الناتج المتوقع:** عند فتح `GroupShapeDemo.docx` في Microsoft Word يظهر صفحة واحدة تحتوي على مستطيلين ملونين (أحمر على اليسار، أخضر على اليمين) يتحركان معًا عندما تختار المجموعة.

---

## الأسئلة الشائعة ومعالجة الحالات الخاصة

| السؤال | الجواب |
|--------|--------|
| *هل يمكنني إضافة أكثر من شكلين إلى نفس المجموعة؟* | نعم. استدعِ `groupShape.appendChild(yourShape)` لكل شكل إضافي. ستقوم المجموعة تلقائيًا بتغيير حجمها لتناسب أبعد الامتدادات، أو يمكنك تعديل العرض/الارتفاع يدويًا. |
| *ماذا لو احتجت إلى نوع شكل مختلف (مثل إهليلج)؟* | استبدل `ShapeType.RECTANGLE` بـ `ShapeType.ELLIPSE`. منطق تعبئة اللون يبقى نفسه. |
| *هل يجب علي التخلص من كائن `Document`؟* | Aspose.Words يدير الموارد الأصلية داخليًا. عند خروج JVM، يتم تحرير الموارد. للتطبيقات طويلة التشغيل، استدعِ `doc.dispose();` إذا كنت تستخدم نسخة **Aspose.Words for Java (Native)**. |
| *كيف أغيّر ترتيب Z بحيث يظهر أحد المستطيلات في الأعلى؟* | استخدم `groupShape.insertAfter(shape, referenceShape);` أو `groupShape.insertBefore(shape, referenceShape);` لإعادة ترتيب الأطفال داخل المجموعة. |
| *هل يمكنني تجميع الأشكال عبر أقسام مختلفة؟* | لا. يجب أن يكون `GroupShape` داخل فقرة واحدة أو حاوية شكل واحدة. لتجميع عبر الأقسام، أنشئ مجموعات منفصلة في كل قسم. |

---

## الخلاصة

أنت الآن تعرف كيفية **إنشاء مستند Word فارغ** باستخدام Aspose.Words for Java، **تجميع الأشكال في Word**، تطبيق تنسيق **شكل المستطيل الملون**، و**حفظ المستند كملف docx**. يمكن توسيع هذا النمط إلى تخطيطات أكثر تعقيدًا—فقط أضف أشكالًا إضافية، اضبط الإزاحات، واختياريًا ضع نصًا أو صورًا أو روابط داخل المجموعة.

**الخطوات التالية** التي قد تستكشفها:

* استخدم **تجميع الأشكال في Word** لبناء مخططات تدفق أو نماذج واجهة المستخدم.
* جرّب **حفظ المستند كملف docx** مع تحويل إلى PDF (`doc.save("out.pdf")`).
* طبق تدرجات أو أنماط على **شكل المستطيل الملون** للحصول على تصميم بصري أغنى.
* اجمع الأشكال المجمعة مع الجداول أو المخططات لإنشاء مستندات تقارير متقدمة.

لا تتردد في تعديل الأبعاد أو الألوان أو أنواع الأشكال لتتناسب مع هوية مشروعك. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [كيفية حفظ المستند كملف PDF باستخدام Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [استخدام أشكال المستند في Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}