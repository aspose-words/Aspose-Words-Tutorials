---
category: general
date: 2026-09-24
description: تعرّف على كيفية إنشاء مستند Word فارغ في Java وتجميع الأشكال مثل المستطيلات
  والخطوط باستخدام Aspose.Words. يتضمن كودًا خطوة بخطوة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: ar
lastmod: 2026-09-24
og_description: إنشاء مستند Word فارغ في Java وتعلم كيفية تجميع الأشكال، إضافة شكل
  مستطيل، وتحديد حجم الشكل باستخدام Aspose.Words.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: إنشاء مستند Word فارغ وتجميع الأشكال في Java – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: كيفية إنشاء مستند Word فارغ وتجميع الأشكال في Java
url: /ar/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word فارغ وتجميع الأشكال في Java

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** ثم تنظيم عدة كائنات رسم، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. باستخدام Aspose.Words for Java يمكنك إدراج شكل مجموعة، إضافة شكل مستطيل، رسم خط، والتحكم في حجم كل شكل وموقعه—كل ذلك في برنامج واحد قابل للتنفيذ.

ستتبع كل خطوة، من تهيئة المستند إلى حفظ ملف `.docx` النهائي. في النهاية ستفهم **كيفية تجميع الأشكال**، **إضافة شكل مستطيل**، و**تحديد حجم الشكل** بحيث تبدو ملفات Word الخاصة بك كما هو مقصود.

## المتطلبات المسبقة

- Java 17 أو أحدث (الكود يُترجم مع أي JDK حديث)
- مكتبة Aspose.Words for Java (قم بتنزيلها من [موقع Aspose](https://products.aspose.com/words/java))
- بيئة تطوير متكاملة أو أداة بناء (Maven/Gradle) يمكنها إضافة ملف JAR الخاص بـ Aspose.Words إلى مسار الفئة
- معرفة أساسية بصياغة Java

> **نصيحة احترافية:** استخدم Maven لإدارة الاعتمادات؛ أضف `com.aspose:aspose-words:23.12` (أو أحدث نسخة) إلى ملف `pom.xml` الخاص بك.

## الخطوة 1: إنشاء مستند Word فارغ

المهمة الأولى هي **إنشاء مستند Word فارغ**. هذا يمنحك لوحة رسم نظيفة يمكنك لاحقًا إدراج الأشكال عليها.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*لماذا هذا مهم:* كائن `Document` يمثل الملف `.docx` بالكامل. البدء بمستند فارغ يضمن عدم وجود تنسيقات مخفية تتداخل مع الأشكال التي ستضيفها.

## الخطوة 2: إدراج شكل مجموعة – الحاوية لعدة كائنات

**شكل المجموعة** يعمل كحاوية تسمح لك بتحريك، تغيير حجم، أو تدوير عدة أشكال معًا. هذا هو جوهر **كيفية تجميع الأشكال** في Word.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*شرح:* طريقة `insertGroupShape` تنشئ كائن `GroupShape` وتضعه في موقع المؤشر الحالي. جميع الأشكال اللاحقة التي تقوم بـ `appendChild` إلى هذه المجموعة ستُعامل كوحدة واحدة.

## الخطوة 3: إضافة شكل مستطيل وتحديد حجمه

الآن نقوم **بإضافة شكل مستطيل** إلى المجموعة و**تحديد حجم الشكل** بدقة.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*لماذا تحتاج إلى تحديد حجم الشكل:* العرض والارتفاع يتحكمان في كيفية ظهور المستطيل على الصفحة. طريقتا `setLeft` و `setTop` تحددان موقع المستطيل بالنسبة لأصل المجموعة، مما يمنحك تحكمًا دقيقًا في التخطيط.

## الخطوة 4: إضافة شكل خط وتكوين أبعاده

الخط هو كائن رسم شائع آخر. سنطبق منطق **إضافة شكل مستطيل** على الخط، لإظهار أن نفس مبادئ الحجم تنطبق.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*نقطة رئيسية:* رغم أن الخط لا يمتلك ارتفاعًا، لا يزال عليك استخدام `setWidth` لتحديد طوله. التحديد (`setLeft`، `setTop`) يتبع نفس نظام الإحداثيات كما في الأشكال الأخرى.

## الخطوة 5: حفظ المستند مع الأشكال المجمعة

أخيرًا، احفظ التغييرات عن طريق حفظ المستند. هذا ينتج ملف `.docx` يمكنك فتحه في Microsoft Word للتحقق من النتيجة.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**الناتج المتوقع:** عند فتح `GroupShapeDemo.docx` يظهر صفحة فارغة تحتوي على مستطيل وخط مجمّعين. اختيار أي شكل يحدد المجموعة بأكملها، مما يتيح لك تحريكهما معًا.

## الأسئلة الشائعة ومعالجة الحالات الخاصة

| السؤال | الجواب |
|----------|--------|
| *هل يمكنني إضافة أكثر من شكلين إلى المجموعة؟* | نعم. استدعِ `group.appendChild(yourShape)` لكل شكل إضافي. |
| *ماذا لو احتجت إلى وحدة مختلفة (مثل السنتيمترات) للحجم؟* | Aspose.Words يستخدم النقاط (1 نقطة = 1/72 بوصة). حوِّل باستخدام `Points = centimeters * 28.3465`. |
| *هل ستحافظ المجموعة على تخطيطها عند فتح المستند على جهاز آخر؟* | بالطبع. جميع بيانات الحجم والموقع مخزنة في ملف `.docx`، مما يجعل التخطيط قابلًا للنقل. |
| *كيف يمكنني فك تجميع الأشكال لاحقًا؟* | استرجع كائن `GroupShape`، ثم تكرّر عبر `group.getChildNodes(NodeType.SHAPE, true)` وانقل كل طفل خارج المجموعة. |
| *ماذا لو احتجت إلى تدوير المجموعة بأكملها؟* | استخدم `group.setRotationAngle(double angleInDegrees)` قبل الحفظ. |

## مثال كامل وقابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في بيئة التطوير المتكاملة الخاصة بك. يتضمن جميع الاستيرادات الضرورية والتعليقات.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

شغّل البرنامج، افتح `GroupShapeDemo.docx` في Microsoft Word، وسترى الأشكال المجمعة كما هو موضح.

## الخلاصة

أنت الآن تعرف كيف **تنشئ مستند Word فارغ**، **تجميع الأشكال في Word**، **إضافة شكل مستطيل**، و**تحديد حجم الشكل** باستخدام Aspose.Words for Java. من خلال وضع الأشكال داخل `GroupShape`، تحصل على تحكم كامل في التحديد الجماعي، التحجيم، والدوران—مناسب للمخططات، الرسوم البيانية، أو الرسومات المخصصة المدمجة في التقارير الآلية.

**الخطوات التالية:**  
- استكشف **كيفية تجميع الأشكال** مع كائنات أكثر تعقيدًا مثل الصور أو مربعات النص.  
- جرّب `setRotationAngle` لتدوير المجموعة بأكملها.  
- اجمع هذه التقنية مع دمج البريد لإنشاء مستندات مخصصة تتضمن رسومات ذات علامة تجارية.

لا تتردد في تعديل الكود لمشاريعك الخاصة، وشارك نتائجك في التعليقات!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء شكل مستطيل في Word باستخدام Java – دليل كامل](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [إنشاء مستند Word Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}