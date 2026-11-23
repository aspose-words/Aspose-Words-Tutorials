---
category: general
date: 2026-11-22
description: إضافة شكل مستطيل في مستند Word باستخدام Java، ضبط حجم الشكل، تجميع عدة
  أشكال، وإلحاق الشكل بالمجموعة بكفاءة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: ar
lastmod: 2026-11-22
og_description: أضف شكل مستطيل في مستند Word باستخدام Java، ثم حدد حجم الشكل، وجمع
  عدة أشكال في مجموعة، وأضف الشكل إلى المجموعة في سير عمل واحد.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: إضافة شكل مستطيل وتجميع الأشكال في جافا – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: إضافة شكل مستطيل وتجميع الأشكال في جافا
url: /ar/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة شكل مستطيل وتجميع الأشكال في Java

إذا كنت بحاجة إلى **إضافة شكل مستطيل** إلى مستند Word باستخدام Java، فإن هذا الدليل يوضح لك الخطوات الدقيقة. ستتعلم أيضًا كيفية **تحديد حجم الشكل**، **تجميع عدة أشكال**، و**إلحاق الشكل بالمجموعة** دون مغادرة بيئة التطوير المتكاملة.

العمل مع الرسومات المتجهة داخل ملف DOCX غالبًا ما يشعر وكأنه التعامل مع عدة واجهات برمجة تطبيقات منفصلة. بنهاية هذا الدرس ستحصل على برنامج واحد متكامل يقوم بإنشاء مستطيل، إهليلج، وأي أشكال إضافية قد تحتاجها، ثم يجمعها بحيث تتحرك ككائن واحد. لا تحتاج إلى أدوات خارجية بخلاف Aspose.Words for Java.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* Java 17 أو أحدث مثبتة.
* Maven 3.8+ (أو Gradle) لإدارة التبعيات.
* رخصة صالحة لـ Aspose.Words for Java (التقييم يعمل للاختبار).
* بيئة تطوير متكاملة مثل IntelliJ IDEA أو VS Code، رغم أن أي محرر نصوص سيكفي.

هذه المتطلبات تضمن أن الكود يُجمَّع ويُنفَّذ على أي بيئة تطوير حديثة.

## الخطوة 1: إعداد مشروع Maven

أنشئ مشروع Maven جديد أو أضف تبعية Aspose.Words إلى ملف `pom.xml` الموجود:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

التبعية تجلب جميع الفئات المطلوبة لمعالجة المستندات، بما في ذلك `Document`، `DocumentBuilder`، `Shape`، و`GroupShape`. سيقوم Maven بتحميل ملفات JAR تلقائيًا عند تشغيل `mvn compile`.

## الخطوة 2: تحميل المستند وإنشاء DocumentBuilder

يوفر `DocumentBuilder` واجهة برمجة تطبيقات سلسة لإدراج المحتوى. حمّل مستند DOCX موجود أو ابدأ من مستند فارغ:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

إنشاء الـ builder مبكرًا يمنحك مؤشرًا موضعه في بداية المستند، جاهزًا لإدراج الأشكال.

## إضافة شكل مستطيل إلى مستند Word

### الخطوة 3: إدراج شكل المستطيل

المستطيل هو العنصر البصري الأول الذي نريد وضعه داخل المستند. باستخدام مُنشئ `Shape` مع `ShapeType.RECTANGLE`، ستحصل على كائن قابل للتحرير بالكامل.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

إضافة المستطيل في هذه المرحلة لا تؤثر على التخطيط حتى يتم تحديد حجمه وإلحاقه بحاوية.

### تحديد حجم الشكل وأبعاده

#### الخطوة 4: تعريف العرض والارتفاع

تحديد أبعاد الشكل يحدد كيف سيظهر على الصفحة. قيم العرض والارتفاع تُقاس بالنقاط (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

يمكنك تعديل هذه الأرقام لتتناسب مع متطلبات التصميم الخاصة بك. نفس الأساليب تنطبق على أي كائن `Shape`، لذا يمكنك إعادة استخدامها للدوائر، الأسهم، أو الرسومات المخصصة.

#### الخطوة 5: إدراج المستطيل في المستند

الآن بعد أن تم تحديد حجم المستطيل، ضعّه على الصفحة. طريقة `insertShape` في `DocumentBuilder` تضيف الشكل في موضع المؤشر الحالي.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

في هذه المرحلة يظهر المستطيل بمفرده على الصفحة. الخطوات التالية توضح كيفية دمجه مع أشكال أخرى.

## تجميع عدة أشكال معًا

تجميع الأشكال يتيح لك تحريكها، تدويرها، أو تغيير حجمها كوحدة واحدة. هذا مفيد بشكل خاص لإنشاء مخططات معقدة.

### الخطوة 6: إنشاء حاوية مجموعة الأشكال

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

استدعاء `insertGroupShape` يضيف حاوية فارغة إلى المستند. أي شكل يُلحق بهذه الحاوية يصبح جزءًا من المجموعة.

### إلحاق الشكل بالمجموعة

#### الخطوة 7: إضافة المستطيل إلى المجموعة

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

الإلحاق ينقل المستطيل من جسم المستند إلى مجموعة داخلية. الآن يحترم المستطيل تحويلات المجموعة.

#### الخطوة 8: إضافة إهليلج للتوضيح

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

الإهليلج يشترك في نفس مساحة الإحداثيات مع المستطيل، لذا يمكنك محاذاته بصريًا عن طريق تعديل خصائص `setLeft` و `setTop` إذا لزم الأمر.

### الخطوة 9: حفظ المستند

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

تشغيل البرنامج يولد `output.docx`. افتح الملف في Microsoft Word أو LibreOffice؛ سترى مستطيلًا وإهليلجًا مجمّعين معًا. اختيار أي من الشكلين يبرز المجموعة بأكملها، مما يؤكد نجاح **إلحاق الشكل بالمجموعة**.

![Add rectangle shape example in Java](image.png){alt="مثال على إضافة شكل مستطيل في Java"}

*تُظهر لقطة الشاشة المستطيل والإهليلج داخل مجموعة واحدة، جاهزين للتعامل المشترك.*

## لماذا هذه الطريقة مهمة

* **مصدر واحد للحقائق** – جميع خصائص الشكل تُحدد قبل إنشاء المجموعة، مما يمنع حدوث مشكلات في التخطيط.
* **إعادة الاستخدام** – نفس طُرُق `setWidth`/`setHeight` تعمل مع أي شكل، لذا يمكنك توسيع المثال ليشمل أسهم، نجوم، أو SVG مخصص.
* **الأداء** – التجميع يقلل عدد كائنات الرسم التي يجب على محرك Word معالجتها، مما يحسن سرعة الفتح للمستندات الكبيرة.
* **الصيانة** – من خلال إبقاء منطق إنشاء الشكل وتجمّعه معًا، يمكن للمطورين المستقبليين تعديل الأبعاد أو إضافة أشكال جديدة دون البحث في شيفرة غير ذات صلة.

## الاختلافات الشائعة والحالات الخاصة

| السيناريو | التعديل |
|----------|------------|
| **وحدات مختلفة** | استخدم تحويل `PointsToPixels` أو عيّن `Shape.setWrapType(WrapType.INLINE)` للتموضع داخل السطر. |
| **تدوير المجموعة** | استدعِ `groupShape.setRotation(45);` لتدوير جميع الأشكال الفرعية بزاوية 45°. |
| **إضافة نص إلى الشكل** | استخدم `Shape.setText("Label");` بعد تحديد الحجم. |
| **تحديد حجم ديناميكي** | احصل على أبعاد الصفحة عبر `doc.getFirstSection().getPageSetup().getPageWidth()` واحسب أحجام الأشكال نسبياً. |

هذه الاختلافات توضح كيف يتكيف النمط الأساسي—**إضافة شكل مستطيل**، **تحديد حجم الشكل**، **تجميع عدة أشكال**، **إلحاق الشكل بالمجموعة**—مع العديد من المتطلبات الواقعية.

## الخلاصة

أنت الآن تعرف كيف **تضيف شكل مستطيل** إلى مستند Word باستخدام Java، **تحدد حجم الشكل**، **تجمع عدة أشكال**، و**تلحق الشكل بالمجموعة** بطريقة نظيفة وقابلة للصيانة. المثال الكامل يُجمَّع في فئة واحدة قابلة للتنفيذ، والملف DOCX الناتج يُظهر النتيجة المتوقعة.

من هنا يمكنك استكشاف:

* إضافة تسميات نصية أو روابط تشعبية إلى كل شكل.
* تعشيق المجموعات لبناء مخططات هرمية.
* تصدير المستند إلى PDF مع الحفاظ على مجموعات الأشكال.

لا تتردد في تجربة أبعاد، ألوان، وأنواع أشكال إضافية مختلفة. إتقان معالجة الأشكال يفتح الباب أمام إنشاء تقارير آلية، مخططات ديناميكية، وتجارب مستندات غنية—all directly from Java code.

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Create rectangle shape in a Word document using Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}