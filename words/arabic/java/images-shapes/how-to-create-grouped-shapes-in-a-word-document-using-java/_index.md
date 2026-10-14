---
category: general
date: 2026-10-13
description: تعلم كيفية إنشاء أشكال مجمعة في Word باستخدام Java. يوضح لك هذا الدليل
  كيفية إدراج شكل مجموعة، إضافة خط إلى المجموعة، وتجميع عدة أشكال عبر المستند.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: ar
lastmod: 2026-10-13
og_description: إنشاء أشكال مجمعة في Word باستخدام Java. اتبع هذا الدرس الكامل لإدراج
  شكل مجموعة، وإضافة خط إلى المجموعة، وتجميع أشكال متعددة في مستندات Word.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: إنشاء أشكال مجمعة في Word باستخدام Java – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: كيفية إنشاء أشكال مجمعة في مستند Word باستخدام Java
url: /ar/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء أشكال مجمعة في مستند Word باستخدام Java

إذا كنت بحاجة إلى **إنشاء أشكال مجمعة** في ملف Microsoft Word من خلال Java، فإن هذا الدليل سيقودك خلال العملية بالكامل. ستتعرف على كيفية **إدراج شكل مجموعة**، وضع مستطيل وخط داخل نفس الحاوية، وأخيرًا حفظ المستند مع الرسومات المجمعة.

تجميع الأشكال يجعل من السهل نقلها أو تغيير حجمها أو تنسيقها ككائن واحد—مثالي للمخططات، المخططات الانسيابية، أو الزخارف المخصصة للصفحات. بنهاية هذا الدليل ستتمكن من **إضافة خط إلى المجموعة**، **تجميع أشكال متعددة في مستندات Word**، وإعادة استخدام نفس التقنية لأي عدد من الأشكال.

## المتطلبات المسبقة

- Java 17 أو أحدث مثبت على جهاز التطوير الخاص بك.  
- رخصة Aspose.Words for Java (أو نسخة تجريبية مجانية).  
- مشروع Maven أو Gradle حيث يمكنك إضافة تبعية Aspose.Words:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

لا توجد مكتبات إضافية مطلوبة.

## الخطوة 1: إدراج حاوية شكل المجموعة

الخطوة الأولى هي **إدراج شكل مجموعة** في المستند. هذه الحاوية ستحمل كل شكل لاحق.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` ينشئ كائن `Shape` فارغ من النوع `GROUPSHAPE`. فكر فيه كقماش شفاف يمكنه احتواء كائنات رسم أخرى.

## الخطوة 2: إضافة مستطيل إلى المجموعة

غالبًا ما يُستخدم المستطيل كخلفية بصرية لمجموعة من الأشكال.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

ضبط `Left` و `Top` إلى `0` يضع المستطيل في الزاوية العليا اليسرى للمجموعة. يمكنك تغيير هذه القيم لإزاحة الشكل داخل المجموعة.

## الخطوة 3: **إضافة خط إلى المجموعة** – إنشاء شكل خط

الآن نقوم **بإضافة خط إلى المجموعة**. سيظهر الخط تحت المستطيل.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

خاصية `Top` تحرك الخط 60 نقطة أسفل المستطيل، مما يخلق تخطيطًا مكدسًا بسيطًا. يمكنك أيضًا ضبط `Left` إذا كنت بحاجة إلى إزاحة أفقية.

## الخطوة 4: حفظ المستند مع الأشكال المجمعة

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

عند فتح `GroupShapeDemo.docx` في Microsoft Word، سترى مجموعة واحدة تحتوي على كل من المستطيل والخط. اختيار المجموعة يتيح لك نقل الشكلين معًا، مما يثبت أنك نجحت في **تجميع أشكال متعددة في Word**.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل مع جميع الاستيرادات ومعالجة الأخطاء. انسخه إلى بيئة التطوير المتكاملة (IDE) الخاصة بك، استبدل `YOUR_DIRECTORY` بمسار مجلد موجود، ثم شغّله.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### النتيجة المتوقعة

- ملف باسم `GroupShapeDemo.docx` يظهر في المجلد المستهدف.  
- فتح الملف في Word يظهر كائنًا مجمعًا واحدًا يحتوي على مستطيل في الأعلى وخط أسفله.  
- سحب المجموعة ينقل الشكلين معًا، مؤكدًا أنك **أنشأت أشكالًا مجمعة** بنجاح.

## نصائح ومشكلات شائعة

- **نصيحة احترافية:** إذا كنت بحاجة إلى تدوير أو تنسيق الأشكال الفردية داخل المجموعة، استدعِ الدوال المناسبة (`setRotation`, `getFill().setForeColor`, إلخ) قبل إلحاقها بالمجموعة. ستحافظ المجموعة على تلك الخصائص البصرية.  
- **احذر من:** نسيان ضبط خاصية `Top` للخط قد يتسبب في تداخل الخط مع المستطيل، مما يجعل المجموعة تبدو فوضوية.  
- **حالة خاصة:** عند إضافة أكثر من شكلين، تذكر أن إحداثيات كل عنصر فرعي تكون نسبية إلى أصل المجموعة (0,0). خطط للتخطيط وفقًا لذلك.  
- **ملاحظة أداء:** تجميع عدد كبير من الأشكال (مئات) قد يزيد حجم الملف قليلًا، لكنه يبسط التعديل لاحقًا في Word.

## كيفية **تجميع أشكال متعددة في مستندات Word** برمجيًا

النمط الموضح أعلاه—إنشاء حاوية مجموعة، تكوين كل شكل فرعي، وإلحاقه—يعمل لأي عدد من الأشكال: دوائر، صور، مربعات نص، إلخ. ببساطة كرّر خطوات “إنشاء الشكل → ضبط الخصائص → الإلحاق” قبل استدعاء `doc.save()`.

إذا كنت بحاجة إلى **إضافة خط إلى المجموعة** بعد أن تحتوي المجموعة بالفعل على أشكال أخرى، يمكنك استرجاع المجموعة الحالية باستخدام:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

هذا يوضح أنه يمكنك تعديل مجموعة في أي مرحلة من دورة حياة المستند.

## الخلاصة

أنت الآن تعرف كيف **تنشئ أشكالًا مجمعة** في مستند Word باستخدام Java و Aspose.Words. من خلال **إدراج شكل مجموعة**، **إضافة خط إلى المجموعة**، و **تجميع أشكال متعددة في Word**، يمكنك بناء رسومات معقدة تتصرف ككائن واحد—مثالية للمخططات، القوالب، وتوليد التقارير الآلية.

بعد ذلك، استكشف هذه المواضيع ذات الصلة:

- **تطبيق الأنماط على الأشكال المجمعة** – تعلم كيفية ضبط ألوان التعبئة، الحدود، والتأثيرات لجميع العناصر الفرعية مرة واحدة.  
- **تصدير الأشكال المجمعة إلى PDF** – شاهد كيف يبقى نفس التجميع عند تحويل المستند.  
- **تحريك الأشكال باستخدام VBA** – دمج المجموعات التي تم إنشاؤها بـ Java مع ماكروات Word لإنشاء مستندات تفاعلية.

لا تتردد في تجربة أنواع مختلفة من الأشكال، الأحجام، والمواضع. التجميع يمنحك المرونة للتعامل مع العديد من الكائنات ككائن واحد، مما يبسط كلًا من الشيفرة وتفاعل المستخدم. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}