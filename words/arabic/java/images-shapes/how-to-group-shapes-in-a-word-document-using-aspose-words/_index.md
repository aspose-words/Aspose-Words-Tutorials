---
category: general
date: 2026-08-20
description: تعلم كيفية تجميع الأشكال، ضبط حجم الشكل، إدراج صورة في المستند، إضافة
  صورة إلى المجموعة، وإنشاء شكل مستطيل باستخدام Aspose.Words في Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: ar
lastmod: 2026-08-20
og_description: كيفية تجميع الأشكال في مستند Word باستخدام Aspose.Words. اتبع هذا
  الدليل خطوة بخطوة بلغة Java لتحديد حجم الشكل، وإدراج صورة في المستند، وإضافة صورة
  إلى المجموعة، وإنشاء شكل مستطيل.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: كيفية تجميع الأشكال في مستند Word باستخدام Aspose.Words – دليل Java
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: كيفية تجميع الأشكال في مستند Word باستخدام Aspose.Words
url: /ar/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تجميع الأشكال في مستند Word باستخدام Aspose.Words

إذا كنت بحاجة إلى **كيفية تجميع الأشكال** في ملف Word، فإن هذا الدرس يوضح الحل الكامل بلغة Java. ستتعرف على كيفية **تحديد حجم الشكل**، **إدراج صورة في المستند**، **إضافة صورة إلى مجموعة**، و**إنشاء شكل مستطيل**—كل ذلك مع شروحات واضحة وعينة كود قابلة للتنفيذ.

تجميع الأشكال يبسط إدارة التخطيط، ويسمح لك بنقل أو تدوير عدة كائنات كوحدة واحدة، ويحافظ على نظافة المستند. في الخطوات أدناه ستُنشئ مجموعة تحتوي على مستطيل وصورة، ثم تضع المجموعة على الصفحة.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* Java 17 أو أحدث مثبتة.
* Aspose.Words for Java (الإصدار 23.9 أو أحدث) مضاف إلى مسار الفئة (classpath) في مشروعك.
* صورة JPEG تجريبية في `YOUR_DIRECTORY/sample.jpg` (استبدل `YOUR_DIRECTORY` بالمسار الفعلي).

يمكنك إضافة Aspose.Words عبر Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## كيفية تجميع الأشكال باستخدام Aspose.Words

الأقسام التالية تستعرض كل عملية مطلوبة لـ **كيفية تجميع الأشكال**. يحتوي عنوان H2 الأساسي على الكلمة المفتاحية الأساسية، مما يحقق قواعد SEO.

### الخطوة 1: إنشاء مستند جديد و`DocumentBuilder`

`Document` يمثل ملف Word، بينما `DocumentBuilder` يوفر طرقًا مريحة لإدراج المحتوى.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*لماذا هذا مهم*: بدءًا بـ `Document` جديد يضمن أن المجموعة التي تنشئها لن تتداخل مع العناصر الموجودة.

### الخطوة 2: إدراج شكل مجموعة سيحتوي على أشكال فرعية متعددة

شكل المجموعة يعمل كحاوية. أبعاده تحدد الصندوق المحيط لجميع الأشكال الفرعية.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*نصيحة*: العرض (`300`) والارتفاع (`200`) بوحدات النقاط (1 pt = 1/72 inch). عدّلهما بناءً على حجم الأشكال التي تخطط لإضافتها.

### الخطوة 3: إنشاء شكل مستطيل، تحديد حجمه، وإضافته إلى المجموعة

تحديد الحجم الدقيق للشكل أمر أساسي عندما تريد تحكمًا دقيقًا في التخطيط.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*لماذا نحدد حجم الشكل*: طُرُق `setWidth` و `setHeight` تتطابق مع الكلمة المفتاحية الثانوية **set shape size**، مما يمنحك تحكمًا بكسل‑بكسل في مظهر المستطيل.

### الخطوة 4: إدراج صورة، ثم إضافة شكل الصورة إلى نفس المجموعة

إدراج صورة هو جوهر متطلب **insert image into document**. الشكل `Shape` المرتجع هو شكل صورة يمكن تجميعه مثل أي شكل آخر.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*نصيحة احترافية*: إذا كنت بحاجة للحفاظ على نسبة العرض إلى الارتفاع الأصلية، حدد بعدًا واحدًا فقط (`setWidth` أو `setHeight`). يقوم Aspose.Words تلقائيًا بتعديل البعد الآخر.

### الخطوة 5: وضع المجموعة بالكامل على الصفحة

بعد إضافة جميع الأشكال الفرعية، يمكنك نقل، تدوير، أو إخفاء المجموعة بأكملها. يستخدم التموضع مفهوم **add picture to group** بشكل غير مباشر، لأن المجموعة الآن تحتوي على الصورة.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*شرح*: `setLeft` و `setTop` يضعان المجموعة نسبةً إلى هوامش الصفحة. تدوير المجموعة يوضح أن جميع الأشكال الفرعية ترث التحويل.

### الخطوة 6: حفظ المستند

أخيرًا، اكتب الملف إلى القرص. يمكنك فتح ملف `.docx` الناتج في Word للتحقق من التجميع.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

تشغيل البرنامج ينتج **GroupShapesDemo.docx** يحتوي على مستطيل وصورة مُجمّعين معًا. تحديد أي من الشكلين في Word سيحدد الآخر أيضًا، مؤكدًا أنك تعلمت بنجاح **كيفية تجميع الأشكال**.

---

## النتيجة المتوقعة

عند فتح *GroupShapesDemo.docx* في Microsoft Word:

* يظهر مستطيل (تعبئة ذهبية) على الجانب الأيسر من المجموعة.
* الصورة التي قدمتها تظهر على يمين المستطيل.
* يتحرك الكائنان معًا عند سحب المجموعة.
* تُوضع المجموعة على بعد 50 pt من الهامش الأيسر و100 pt من الهامش العلوي، وتدويرها 15°.

إذا لم تظهر الصورة، تحقق مرة أخرى من مسار الملف في `insertImage`. يقوم Aspose.Words بإلقاء استثناء `IOException` عندما لا يمكن العثور على الملف.

---

## أسئلة شائعة ومعالجة الحالات الخاصة

| السؤال | الجواب |
|----------|--------|
| **هل يمكنني إضافة أكثر من شكلين؟** | نعم. استدعِ `groupShape.appendChild(otherShape)` لكل شكل إضافي. |
| **ماذا لو احتجت خلفية شفافة للمستطيل؟** | استخدم `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **هل يدعم التجميع صيغ Word القديمة (مثل `.doc` )؟** | يعمل التجميع مع `.docx` و`.doc` لكن بعض عارضات الإصدارات القديمة قد تتجاهل بيانات التجميع. احفظ كـ `.docx` للحصول على دقة كاملة. |
| **كيف أقوم بفك التجميع لاحقًا؟** | استرجع العقد الفرعية عبر `groupShape.getChildNodes(NodeType.ANY, true)` وانقلها إلى جسم المستند، ثم احذف المجموعة. |
| **هل يمكنني تجميع أشكال عبر أقسام مختلفة؟** | لا. يجب أن تكون `GroupShape` داخل `Story` واحدة (عادةً جسم المستند الرئيسي). |

---

## نصائح احترافية للتعامل القوي مع الأشكال

* **استخدام التموضع المطلق بحذر** – التموضع النسبي (`builder.moveToDocumentEnd()`) غالبًا ما ينتج تخطيطات أكثر استجابة.
* **تخزين `DocumentBuilder` مؤقتًا** – إنشاء بنّاء جديد لكل عملية قد يضعف الأداء في المستندات الكبيرة.
* **تعيين `PictureFillMode`** عندما تحتاج إلى تمديد أو تكرار الصورة داخل الشكل: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **التحقق من أبعاد الصورة** قبل الإدراج لتجنب التحجيم غير المتوقع الذي قد يؤثر على صندوق حدود المجموعة.

---

## الخطوات التالية

الآن بعد أن عرفت **كيفية تجميع الأشكال**، يمكنك استكشاف:

* **إدراج صورة في المستند** مع خيارات متقدمة مثل القص (`pictureShape.setCropTop(...)`).
* **تحديد حجم الشكل** بشكل ديناميكي بناءً على أبعاد الصفحة (`doc.getFirstSection().getPageSetup().getPageWidth()`).
* **إضافة صورة إلى مجموعة** مع صناديق نصية لتوفير رسومات توضيحية مع عناوين.
* **إنشاء شكل مستطيل** بزوايا مستديرة (`rectangleShape.setCornerRadius(5);`).

هذه المواضيع تبني على نفس سطح الـ API وتساعدك على إنشاء تقارير Word برمجية متقدمة.

---

## الخلاصة

في هذا الدرس تعلمت **كيفية تجميع الأشكال** في مستند Word باستخدام Aspose.Words for Java. باتباع الخطوات الستة—إنشاء مستند، إدراج مجموعة، **إنشاء شكل مستطيل**، **تحديد حجم الشكل**، **إدراج صورة في المستند**، **إضافة صورة إلى مجموعة**، وتموضع المجموعة—أصبحت تمتلك نمطًا قابلاً لإعادة الاستخدام لسيناريوهات تخطيط معقدة. لا تتردد في تجربة أشكال فرعية إضافية، تدويرات مختلفة، أو منطق تجميع شرطي لتلبية احتياجات تطبيقك.

برمجة ممتعة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك الخاصة.

- [إنشاء مستند Word باستخدام Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [استخدام أشكال المستند في Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}