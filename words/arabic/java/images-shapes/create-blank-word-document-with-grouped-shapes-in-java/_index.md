---
category: general
date: 2026-08-07
description: إنشاء مستند Word فارغ مع أشكال مجمعة في Java باستخدام Aspose.Words. تعلم
  كيفية تجميع الشكل، ضبط حجم الشكل، وإضافة الأشكال إلى Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: ar
lastmod: 2026-08-07
og_description: إنشاء مستند Word فارغ مع أشكال مجمعة في Java. اتبع هذا الدليل لتحديد
  حجم الشكل، وإضافة الأشكال إلى Word، وإتقان كيفية تجميع الشكل.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: إنشاء مستند Word فارغ مع أشكال مجمعة – دليل Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: إنشاء مستند Word فارغ مع أشكال مجمعة في Java
url: /ar/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ مع أشكال مجمعة في Java

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** يحتوي على عدة أشكال مرتبة كوحدة واحدة، فإن هذا الدليل يوضح لك بالضبط كيفية ذلك. سترى مثالًا كاملاً قابلاً للتنفيذ يوضح **كيفية تجميع الشكل** وتعديل أبعاده، و**إضافة أشكال إلى Word** باستخدام Aspose.Words for Java.

الدليل يمر بكل خطوة — من إعداد المشروع إلى حفظ ملف .docx النهائي — حتى تتمكن من نسخ الشيفرة مباشرةً إلى تطبيقك الخاص. لا توجد مراجع خارجية مطلوبة، والحل يعمل مع Aspose.Words 23.9 أو أحدث.

## المتطلبات المسبقة

* Java 17 (أو أي JDK مدعوم)
* Maven أو Gradle لإدارة التبعيات
* رخصة Aspose.Words for Java (أو مفتاح تقييم مؤقت)
* ملف صورة تجريبي (مثال: `sample.jpg`) موجود في دليل معروف

إذا كان أي من هذه العناصر مفقودًا، فقم بتثبيتها أولاً؛ باقي الدليل يفترض أن البيئة جاهزة.

## الخطوة 1: إضافة Aspose.Words إلى مشروعك

أضف تبعية Aspose.Words إلى ملف `pom.xml` (Maven) أو `build.gradle` (Gradle). هذه المكتبة توفر الفئات `Document` و `DocumentBuilder` و `GroupShape` و `Shape` المستخدمة لاحقًا.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**لماذا هذا مهم:** بدون المكتبة، لا تتوفر أي من واجهات برمجة تطبيقات معالجة Word، ولا يمكنك **إنشاء مستند Word فارغ** برمجيًا.

## الخطوة 2: إنشاء مستند Word فارغ

الإجراء الأول الملموس هو إنشاء كائن `Document`، الذي يمثل **مستند Word فارغ** في الذاكرة.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* ينشئ **مستند Word فارغ** بإعدادات افتراضية (صفحة A4، هوامش افتراضية). يتيح لك `DocumentBuilder` المرافق إدراج المحتوى عند موضع المؤشر الحالي.

## الخطوة 3: إدراج شكل مجموعة (كيفية تجميع الشكل)

*group shape* يعمل كحاوية لأشكال أخرى. في هذه الخطوة ستتعلم **كيفية تجميع الشكل** بحيث تتحرك الكائنات معًا.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

طريقة `insertGroupShape` تضع الحاوية عند موقع مؤشر الـ builder. التجميع ضروري عندما تريد التعامل مع رسومات متعددة ككيان واحد — هذا هو جوهر وظيفة **group shapes word**.

## الخطوة 4: إنشاء مستطيل وتحديد حجمه

الآن أضف مستطيلًا إلى المجموعة. هذا يوضح **set shape size**، وهو ضروري لتخطيط دقيق.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*لماذا تحديد الأبعاد؟* استدعاء `setWidth` و `setHeight` صراحةً يضمن أن يظهر المستطيل بالضبط كما هو مقصود، بغض النظر عن أنماط الأشكال الافتراضية في المستند.

## الخطوة 5: إدراج صورة وإضافتها إلى المجموعة

إضافة صورة تُظهر حالة استخدام شائعة أخرى لـ **add shapes to word**. تصبح الصورة جزءًا من نفس المجموعة، وتتحرك مع المستطيل.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

إذا كان ملف الصورة مفقودًا، فإن Aspose.Words يطرح استثناء. نصيحة عملية هي التحقق من المسار مسبقًا:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## الخطوة 6: حفظ المستند الذي يحتوي على الأشكال المجمعة

أخيرًا، احفظ **مستند Word فارغ** (الذي تم ملؤه الآن بشكل مجموعة) على القرص.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

عند فتح `GroupShapeDemo.docx` في Microsoft Word، سترى كائنًا مجمعًا واحدًا يحتوي على مستطيل وصورة. اختيار أي جزء من المجموعة يحرك الحاوية بالكامل، مما يؤكد أن الأشكال تم **تجميعها** بشكل صحيح.

### النتيجة المتوقعة

* ملف باسم `GroupShapeDemo.docx` في الدليل المحدد.
* فتح الملف يظهر حاوية بحجم 300 × 200 نقطة مع:
  * مستطيل بحجم 100 × 50 نقطة موضعه (20, 20).
  * صورة موضوعة عند (150, 30) داخل نفس الحاوية.

## حالات الحافة والاختلافات

| الحالة | طريقة التعامل |
|-----------|-----------------|
| **Different page size** | استدعِ `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` قبل إدراج المجموعة. |
| **Multiple groups** | كرّر الخطوات 3‑5 مع كائن `GroupShape` جديد؛ يمكن وضع كل مجموعة بشكل مستقل. |
| **Rotating shapes** | استخدم `shape.setRotationAngle(45.0);` لتدوير مستطيل أو صورة قبل إلحاقها بالمجموعة. |
| **Non‑image shapes** | أنشئ كائنات `Shape` من النوع `ShapeType.ELLIPSE`، `ShapeType.LINE`، إلخ، وألحقها كما تفعل مع المستطيل. |
| **Large images** | قم بتغيير حجم الصورة باستخدام `picture.setWidth(80.0); picture.setHeight(60.0);` للحفاظ على المجموعة ضمن حدودها الأصلية. |

## نصائح عملية من الخبرة

* **نصيحة احترافية:** اضبط `RelativeHorizontalPosition` و `RelativeVerticalPosition` للمجموعة إلى `RelativeHorizontalPosition.PAGE` و `RelativeVerticalPosition.PAGE` إذا كنت تريد أن تبقى المجموعة مثبتة على الصفحة بدلاً من المؤشر.
* **احذر من:** إضافة شكل يتجاوز أبعاد المجموعة؛ سيُقص الشكل في Word. عدّل حجم المجموعة باستخدام `group.setWidth()` و `group.setHeight()` وفقًا لذلك.
* **ملاحظة أداء:** إذا كنت تُنشئ العديد من المستندات في حلقة، أعد استخدام كائن `DocumentBuilder` واحد واستدعِ `doc.clone()` لتقليل عبء إنشاء الكائنات.

## الخلاصة

أنت الآن تعرف كيف **تنشئ مستند Word فارغ** يحتوي على مجموعة مجمعة من الأشكال باستخدام Aspose.Words for Java. غطى الدليل سير العمل الكامل: إعداد المكتبة، إنشاء المستند، إدراج مجموعة، **set shape size**، **add shapes to word**، وحفظ النتيجة.

من هنا يمكنك استكشاف ميزات أكثر تقدمًا مثل تجميع المخططات، تطبيق الأنماط على الأشكال الفردية، أو تصدير المستند إلى PDF. كل من هذه المواضيع يبني على نفس المبادئ التي تم توضيحها في هذا الدليل.

---

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء مستند Word Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [إدراج أشكال في مستندات Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}