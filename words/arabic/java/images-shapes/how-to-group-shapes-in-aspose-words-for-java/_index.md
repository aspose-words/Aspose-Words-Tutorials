---
category: general
date: 2026-10-20
description: كيفية تجميع الأشكال في Aspose.Words للغة Java – تعلم كيفية إدراج شكل
  مستطيل، تجميعها، وحفظ المستند في دليل واحد.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: ar
lastmod: 2026-10-20
og_description: كيفية تجميع الأشكال في Aspose.Words for Java. يوضح هذا البرنامج التعليمي
  كيفية إدراج شكل مستطيل، تجميعها، وتصدير النتيجة.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: كيفية تجميع الأشكال في Aspose.Words للغة Java – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: كيفية تجميع الأشكال في Aspose.Words للـ Java
url: /ar/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تجميع الأشكال في Aspose.Words for Java

إذا كنت بحاجة إلى **how to group shapes** في مستند Word باستخدام Aspose.Words for Java، فإن هذا الدليل يوضح لك سير العمل الكامل. ستتعلم كيفية **insert rectangle shape**، إضافة مستطيل ثانٍ، تجميع الشكلين، وأخيرًا حفظ الملف—كل ذلك باستخدام كود واضح وقابل للتنفيذ.

تجميع الأشكال مفيد عندما تريد نقل أو تدوير أو تنسيق عدة رسومات كوحدة واحدة. سواءً كنت تبني قالب تقرير، أو مخططًا، أو نشرة مخصصة، فإن إتقان تجميع الأشكال يوفر لك الوقت ويحافظ على تناسق التصميم.

في هذا الدرس سوف:

* إنشاء `Document` جديد و `DocumentBuilder`.
* **How to insert rectangle** أشكال بأبعاد دقيقة.
* تجميع المستطيلات داخل `GroupShape`.
* حفظ المستند والتحقق من النتيجة.

> **Prerequisite** – يجب أن تكون قد أضفت Aspose.Words for Java (الإصدار v23.12 أو أحدث) إلى مشروعك. يمكن لمستخدمي Maven تضمين الاعتماد الموضح أدناه.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## ما ستحتاجه

| العنصر | السبب |
|------|--------|
| Java 17+ | ميزات لغة حديثة وأداء أفضل |
| Aspose.Words for Java | يوفر واجهات `DocumentBuilder` و `Shape` و `GroupShape` |
| بيئة تطوير (IntelliJ IDEA, Eclipse, VS Code, إلخ) | لتجميع وتشغيل المثال |
| صلاحية كتابة إلى مجلد | سيتم حفظ المستند على القرص |

---

## كيفية إدراج شكل مستطيل

الخطوة الأولى هي إنشاء `Document` و `DocumentBuilder`. يوفر الـ builder طرقًا مثل `insertShape` لوضع كائنات الرسم.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Why this matters** – استخدام `insertShape` هو الطريقة القياسية **how to insert rectangle** للكائنات في Aspose.Words. يضيف الشكل تلقائيًا إلى الفقرة الحالية في المستند، لذا لا تحتاج إلى إدارة OpenXML منخفض المستوى.

## تعديل مواضع المستطيل (اختياري)

إذا كان المستطيل الثاني يحتاج إلى موقع مخصص بالنسبة للأول، يمكنك تعديل خصائص `left` و `top`. هذه الخطوة اختيارية ولكنها غالبًا ما تكون مطلوبة لتخطيط مخطط دقيق.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Pro tip:** جميع القياسات بوحدات النقاط (1 pt ≈ 1/72 in). استخدم `convertPointsToPixels` إذا كنت بحاجة إلى قيم بكسل لحسابات واجهة المستخدم.

## كيفية تجميع الأشكال

الآن بعد أن تم إنشاء المستطيلات، يمكنك وضعها داخل `GroupShape`. يجعل التجميع المستطيلين يتصرفان ككائن واحد—نقل، تدوير أو تنسيق المجموعة سيؤثر على الشكلين.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Why grouping works** – `GroupShape` يرث من `Shape`، لذا يمكنك التعامل مع المجموعة كما تتعامل مع أي كائن رسم آخر. عند استدعاء `appendChild`، يتم إزالة الأشكال من موقعها الأصلي وتصبح أبناء للمجموعة.

## حفظ المستند الذي يحتوي على الأشكال المجمعة

أخيرًا، احفظ المستند على القرص. سيحتوي الملف على `GroupShape` واحد يحتوي على مستطيلين داخله.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### النتيجة المتوقعة

افتح `GroupShape.docx` في Microsoft Word:

* سترى مستطيلين (أزرق وأخضر) موضوعة جنبًا إلى جنب.
* اختيار أي من المستطيلين يحدد المجموعة بأكملها—سحبها يحركهما معًا.
* للمجموعة حدّ أحمر رفيع، مما يؤكد تطبيق خصائص `GroupShape`.

إذا نقرت بزر الماوس الأيمن على المجموعة واخترت **Group → Ungroup**، ستعود المستطيلات إلى أشكال مستقلة، مما يوضح أن عملية التجميع قابلة للعكس.

---

## الاختلافات الشائعة وحالات الحافة

| الحالة | كيفية التعامل |
|-----------|------------------|
| **أكثر من شكلين** | أدخل كل شكل، ثم أضف جميعها إلى نفس `GroupShape`. |
| **أنواع أشكال مختلفة** (مثلًا، إهليلج، صورة) | استخدم `builder.insertShape(ShapeType.ELLIPSE, …)` أو `builder.insertImage(...)` قبل الإضافة. |
| **تحجيم المجموعة** | استدعِ `group.setWidth(newWidth)` أو `group.setHeight(newHeight)`؛ يتم تحجيم الأطفال بنسبة متناسبة. |
| **تدوير المجموعة** | `group.setRotationAngle(45);` يدور المجموعة بأكملها حول مركزها. |
| **الحفاظ على المواقع الأصلية** | احفظ قيم `left`/`top` لكل شكل قبل التجميع وأعدها بعد إلغاء التجميع إذا لزم الأمر. |

---

## مثال كامل قابل للتنفيذ

فيما يلي الفئة الكاملة في Java التي يمكنك نسخها ولصقها في بيئة التطوير المتكاملة الخاصة بك. تتضمن جميع الاستيرادات، ومعالجة الأخطاء، وتعليقات لتوضيح الكود.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

شغّل البرنامج، افتح ملف `GroupShape.docx` الناتج، وسترى المستطيلات المجمعة تمامًا كما هو موضح.

---

## الخلاصة

أنت الآن تعرف **how to group shapes** في Aspose.Words for Java، من إنشاء مستند إلى إدراج أشكال مستطيلة، تعديل مواضعها، وأخيرًا تجميعها باستخدام `GroupShape`. تسمح لك هذه التقنية بمعاملة عدة رسومات ككيان واحد، مما يبسط تعديل التخطيط ويحافظ على التناسق البصري.

**Next steps**

* استكشف **how to insert rectangle** أشكال بأنماط تعبئة أو حدود مختلفة.
* اجمع **insert rectangle shape** مع مربعات النص لإنشاء مخططات معنونة.
* جرّب تدوير أو تحجيم المجموعة لإنتاج رسومات أكثر تعقيدًا.

لا تتردد في تعديل الكود لأنواع أشكال أخرى، مجموعات أكبر، أو سيناريوهات توليد مستندات ديناميكية. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إدراج شكل مستطيل في Java – تجميع وتحديد مواضع الأشكال](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [كيفية إدراج شكل مجموعة في Java – دليل كامل](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [كيفية تعيين ظل على شكل في Aspose.Words – دليل كامل](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}