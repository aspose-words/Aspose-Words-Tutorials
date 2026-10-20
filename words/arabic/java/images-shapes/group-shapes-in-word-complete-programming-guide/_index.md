---
category: general
date: 2026-08-14
description: تجميع الأشكال في Word باستخدام Java و Aspose.Words. تعلّم كيفية إنشاء
  شكل مستطيل، ضبط أبعاد الشكل، وتجميع عدة أشكال في مستند Word فارغ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: ar
lastmod: 2026-08-14
og_description: تجميع الأشكال في Word باستخدام Aspose.Words للغة Java. أنشئ مستند
  Word فارغ، أنشئ شكلًا مستطيلًا، اضبط أبعاد الشكل، وقم بتجميع عدة أشكال في دقائق.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: تجميع الأشكال في Word – مثال جافا للمطورين
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: تجميع الأشكال في Word – دليل برمجي كامل
url: /ar/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تجميع الأشكال في Word – دليل برمجة كامل

إذا كنت بحاجة إلى **تجميع الأشكال في Word**، فإن هذا الدرس يشرح لك العملية بالكامل باستخدام Java و Aspose.Words. ستتعلم كيفية **إنشاء مستند Word فارغ**، **إنشاء شكل مستطيل**، **تحديد أبعاد الشكل**، وأخيرًا **تجميع عدة أشكال** بحيث تتصرف ككائن واحد.

التعامل مع الأشكال في ملف Word غالبًا ما يشبه الرسم على لوحة دون فرشاة. بحلول نهاية هذا الدليل ستحصل على مقتطف كود قابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع Java، سواء كنت تولد تقارير أو فواتير أو قوالب مخصصة.

## ما ستحتاجه

- Java 8 أو أحدث
- Aspose.Words for Java (أحدث نسخة، مثال: 24.9)
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse
- إلمام أساسي بالبرمجة الكائنية التوجه

جميع هذه المتطلبات مجانية للتثبيت، والكود أدناه يُترجم باستخدام تبعية Maven واحدة:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## الخطوة 1: إنشاء مستند Word فارغ وتهيئة الـ builder

أول شيء يجب عليك القيام به هو **إنشاء مستند Word فارغ**. هذا يمنحك لوحة نظيفة يمكنك لاحقًا إدراج الأشكال عليها.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` يمثل ملف *.docx* بالكامل، بينما `DocumentBuilder` هو المساعد الذي يُدرج الفقرات والجداول والأشكال. تهيئة كلا الكائنين هي الأساس لأي مهمة أتمتة Word.

## الخطوة 2: إدراج حاوية مجموعة الأشكال

`**مجموعة الأشكال**` تعمل كالمجلد الذي يمكنه احتواء أشكال أخرى. أولاً نقوم بإنشاء الحاوية بحجم ثابت 400 pt × 200 pt.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

طريقة `insertGroupShape` تُعيد كائن `GroupShape`. يجب إلحاق جميع الأشكال اللاحقة التي تريد معالجتها كوحدة واحدة بهذا الكائن.

## الخطوة 3: إنشاء أشكال مستطيلة وتحديد أبعاد الشكل

الآن نقوم **بإنشاء كائنات شكل مستطيل**، ضبط حجمها، وتحديد موقعها داخل المجموعة. تُظهر هذه الخطوة أيضًا كيفية **تحديد أبعاد الشكل** بدقة.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

كلا المستطيلين يشتركان في نفس الأبعاد، لكن خاصية `left` تختلف، لذا يظهران جنبًا إلى جنب. يمكنك تعديل `setTop` و `setLeft` لترتيب أي تخطيط تحتاجه.

## الخطوة 4: حفظ المستند الذي يحتوي على المستطيلات المجمعة

بعد وضع الأشكال داخل المجموعة، ببساطة احفظ الـ `Document`. سيظهر الملف الناتج مستطيلين يتحركان معًا عند تحديدهما.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

تشغيل البرنامج يُنشئ ملف `GroupShape.docx` في دليل العمل. افتحه في Microsoft Word، حدد أحد المستطيلات، وستلاحظ أن المجموعة بأكملها تتحرك كوحدة—وهو بالضبط ما يُقصد بـ **تجميع الأشكال في Word**.

![مثال على تجميع الأشكال في Word](group-shapes.png){alt="مثال على تجميع الأشكال في Word"}

*الشكل: شكلان مستطيلان مجمّعان معًا في مستند Word.*

## نصيحة احترافية: إعادة استخدام نفس مجموعة الأشكال

إذا كنت بحاجة لإضافة المزيد من الأشكال لاحقًا (مثل الدوائر أو مربعات النص)، احتفظ بمرجع إلى `groupShape` واستمر في استدعاء `appendChild`. هذا يتجنب إعادة إنشاء الحاوية ويضمن بقاء جميع الأعضاء متزامنين.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## الحالات الخاصة والأسئلة الشائعة

- **ماذا لو تداخلت الأشكال؟** يُسمح بالتداخل؛ سيعرض Word الأشكال بالترتيب الذي أضيفت به. استخدم `setZOrder` إذا كنت بحاجة إلى ترتيب صريح.
- **هل يمكنني تجميع الأشكال عبر صفحات مختلفة؟** لا. `GroupShape` محصورة في صفحة واحدة لأن نظام إحداثياتها نسبي للصفحة.
- **هل ترث الأشكال المجمعة التنسيق؟** كل عنصر فرعي يحتفظ بتنسيقه الخاص (لون التعبئة، نمط الخط). لتطبيق نمط موحد، قم بالتكرار على `groupShape.getChildNodes()` واضبط الخصائص برمجيًا.

## الكود الكامل للمصدر للرجوع إليه

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

تشغيل البرنامج ينتج ملف DOCX حيث يكون المستطيلان **مجمّعين**. اختيار أي مستطيل يحرك كليهما، مما يؤكد أنك نجحت في **تجميع عدة أشكال**.

## الخلاصة

أنت الآن تعرف كيف **تجميع الأشكال في Word** باستخدام Java، بدءًا من **إنشاء مستند Word فارغ** إلى **إنشاء شكل مستطيل**، **تحديد أبعاد الشكل**، وأخيرًا **تجميع عدة أشكال** في كائن واحد قابل للتحريك. هذا النمط يمكن توسيعه لأي عدد من الأشكال ويمكن دمجه مع النصوص أو الصور أو المخططات لإنشاء مستندات غنية ومبرمجة.

### ما التالي؟

- استكشف **تجميع عدة أشكال** بأنواع مختلفة (إهليلجات، أسهم، مربعات نص).
- طبق ألوان التعبئة أو الحدود باستدعاء `shape.getFillColor()` و `shape.getLine().setColor()`.
- أدخل مجموعة الأشكال داخل خلية جدول لتقارير منظمة.
- جمع هذا النهج مع دمج البريد لإنشاء عقود مخصصة تشمل رسومات ذات علامة تجارية.

لا تتردد في التجربة، تعديل الأبعاد، أو تضمين محتوى إضافي. عندما تتقن التجميع، تصبح سكريبتات أتمتة Word أكثر مرونة وسهولة في الصيانة. برمجة سعيدة!

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [استخدام أشكال المستند في Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [إنشاء مستند Word باستخدام Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}