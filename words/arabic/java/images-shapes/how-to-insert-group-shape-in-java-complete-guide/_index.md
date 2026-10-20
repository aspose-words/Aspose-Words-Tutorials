---
category: general
date: 2026-07-16
description: كيفية إدراج مجموعة أشكال في Java باستخدام Aspose.Words – إضافة شكل مستطيل،
  ضبط أبعاد الشكل، وإنشاء مستطيل ودائرة ملونين.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: ar
lastmod: 2026-07-16
og_description: 'كيفية إدراج مجموعة أشكال في Java: دليل عملي لإضافة شكل مستطيل، ضبط
  أبعاد الشكل، وإنشاء مستطيل ودائرة ملونين باستخدام Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: إدراج مجموعة أشكال في جافا – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: كيفية إدراج مجموعة أشكال في جافا – دليل كامل
url: /ar/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إدراج شكل مجموعة في Java – دليل كامل

هل تساءلت يومًا **كيفية إدراج شكل مجموعة** في مستند Word باستخدام Java؟ لست وحدك. سواء كنت تبني مولد تقارير أو منشئ منشورات ديناميكي، فإن تجميع الأشكال يحافظ على ترتيب التخطيط ويسهل إدارة الكود.

في هذا الدرس سنستعرض الخطوات الدقيقة لـ **إضافة شكل مستطيل**، **تحديد أبعاد الشكل**، و**إنشاء مستطيل ملون** و**إنشاء دائرة ملونة** باستخدام مكتبة Aspose.Words. في النهاية ستحصل على برنامج قابل للتنفيذ ينتج ملف .docx يحتوي على مستطيل أزرق ودائرة حمراء ملفوفة بدقة داخل مجموعة.

## المتطلبات المسبقة

- Java 17 (أو أي JDK حديث) مثبت ومُكوَّن.
- Maven أو Gradle لإدارة التبعيات.
- Aspose.Words for Java 23.9 أو أحدث – يمكنك الحصول عليه من Maven Central.
- فهم أساسي لصياغة Java – لا حاجة لأي شيء معقد.

إذا كنت تفتقد أيًا من هذه المتطلبات، احصل على JDK من موقع Oracle وأضف تبعية Aspose.Words إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

الآن بعد أن تم إعداد الأساس، دعنا نبدأ العمل.

## كيفية إدراج شكل مجموعة – نظرة عامة

الفكرة الأساسية بسيطة: إنشاء `Document`، فتح `DocumentBuilder`، إدراج **شكل مجموعة**، ثم إضافة الأشكال الفردية (مستطيل ودائرة) إلى تلك المجموعة. تعمل المجموعة كحاوية، لذا فإن نقلها لاحقًا سيؤدي إلى تحريك كل ما بداخلها – وهو مثالي للتصاميم المعقدة.

فيما يلي الكود الكامل الجاهز للتنفيذ. لا تتردد في نسخه ولصقه في فئة Java جديدة تسمى `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **نصيحة احترافية:** قيم `setLeft` و `setTop` نسبية إلى أصل المجموعة، وليس إلى الصفحة. هذا يجعل إعادة تموضع المجموعة بالكامل أمرًا سهلاً لاحقًا.

### ماذا حدث؟

1. **Document & Builder** – نقوم بإنشاء ملف Word فارغ و`DocumentBuilder` يتيح لنا إدراج المحتوى.
2. **Group Shape** – `builder.insertGroupShape()` ينشئ حاوية. فكر فيها كملف لمجموعة كائنات الرسم.
3. **Blue Rectangle** – ننشئ كائن `Shape` من النوع `RECTANGLE`، نحدده بالحجم والموقع، ونملأه باللون الأزرق – هذه هي خطوة **إنشاء مستطيل ملون**.
4. **Red Circle** – نفس النمط، لكن باستخدام `ELLIPSE` للحصول على دائرة مثالية، ثم ملئها باللون الأحمر – هذه هي جزء **إنشاء دائرة ملونة**.
5. **Saving** – أخيرًا نحفظ كل شيء إلى `GroupShapeDemo.docx`.

شغّل البرنامج (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) وافتح الملف الناتج. يجب أن ترى مستطيلًا أزرق على اليسار ودائرة حمراء على اليمين، كلاهما محصور داخل صندوق مجموعة واحد.

## إضافة شكل مستطيل

إذا كنت تحتاج فقط إلى مستطيل دون تجميع، يمكنك تخطي استدعاء `insertGroupShape()` وإضافة المستطيل مباشرة إلى جسم المستند. ومع ذلك، يوفر التجميع لك مرونة نقل، تدوير، أو حذف عدة أشكال دفعة واحدة.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

لاحظ كيف استخدمنا منطق **إضافة شكل مستطيل** هنا. يظهر المستطيل على الصفحة ككائن مستقل. في معظم السيناريوهات الواقعية ستفضل المجموعة، لأنها تحافظ على التموضع النسبي.

## تحديد أبعاد الشكل

عند رؤية طرق مثل `setWidth` و `setHeight`، تذكر أنها تقبل **نقاط** (1/72 بوصة). إذا كنت تفضل المليمترات، قم بالتحويل أولاً:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

هذا المقتطف يوضح **تحديد أبعاد الشكل** مع تحويل الوحدات – مفيد عندما تكون مواصفات التصميم لديك من نموذج UI يستخدم الوحدات المترية.

## إنشاء مستطيل ملون

تلوين الشكل سهل مثل استدعاء `getFill().setForeColor()`. يمكنك تمرير أي `java.awt.Color`. هل تريد تدرجًا لونيًا؟ استخدم `setForeColor` للون البداية و `setBackColor` للون النهاية.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

هذه طريقة سريعة لـ **إنشاء مستطيل ملون** بملء متدرج بدلاً من لون صلب.

## إنشاء دائرة ملونة

الدائر هي مجرد إهليلجات ذات عرض وارتفاع متساويين. نفس منطق اللون ينطبق:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

إذا كنت تحتاج إلى ملء شفاف، اضبط قناة ألفا:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

الآن أصبحت متمكنًا من تقنية **إنشاء دائرة ملونة**.

## حفظ المستند

تتيح لك Aspose.Words تصدير المستند إلى صيغ متعددة: DOCX، PDF، HTML، PNG، وما إلى ذلك. في هذا العرض نستخدم DOCX لأنه يحافظ على الأشكال المتجهية بشكل مثالي.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

تغيير `SaveFormat` هو كل ما يلزم لإنشاء نسخة PDF من نفس العمل المجمّع.

## الأخطاء الشائعة وكيفية تجنّبها

- **نسيت إضافة الشكل إلى المجموعة؟** سيظهر الشكل على الصفحة لكنه لن يتحرك مع المجموعة. احرص دائمًا على استدعاء `group.appendChild(yourShape)`.

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [إنشاء مستند Word باستخدام Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}