---
category: general
date: 2026-10-16
description: تعلم كيفية تجميع الأشكال في Word باستخدام Java. يوضح هذا الدرس كيفية
  إضافة شكل مستطيل، وتحديد حجم الأشكال وأبعادها، وحفظ المستند.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: ar
lastmod: 2026-10-16
og_description: تجميع الأشكال في Word باستخدام Java. إضافة شكل مستطيل، ضبط حجم الأشكال
  وأبعادها، وإنشاء مستندات احترافية برمجياً.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: تجميع الأشكال في Word باستخدام Java – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: كيفية تجميع الأشكال في Word باستخدام Java – دليل كامل
url: /ar/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تجميع الأشكال في Word باستخدام Java – دليل كامل

إذا كنت بحاجة إلى **تجميع الأشكال في Word** برمجياً، فإن هذا الدليل يقدم لك حلاً جاهزاً للتنفيذ. ستتعرف على كيفية **إضافة شكل مستطيل**، تعديل حجمه، ضبط أبعاد الشكل، وأخيراً حفظ ملف DOCX يحتوي على مستطيل مُجَمَّع وإهليلج.

يعد تجميع الأشكال في Word مفيداً لبناء مخططات معقدة، إنشاء مكونات رسومية قابلة لإعادة الاستخدام، أو ببساطة الحفاظ على الكائنات المرتبطة معاً عندما يتم تعديل المستند لاحقاً. يستخدم الكود مكتبة Aspose.Words for Java، التي تعمل مع أي JDK حديث ولا تتطلب تثبيت Microsoft Word.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

| المتطلب | السبب |
|-------------|--------|
| Java 17 (أو أحدث) | المكتبة تستهدف بيئات تشغيل Java الحديثة. |
| Aspose.Words for Java (أحدث إصدار) | توفر الفئات `Document`، `DocumentBuilder`، `GroupShape`، و`Shape` المستخدمة في المثال. |
| بيئة تطوير متكاملة أو أداة بناء (Maven/Gradle) | لترجمة وتشغيل العينة. |
| معرفة أساسية بتركيب Java | مطلوبة لفهم تدفق الكود. |

أضف تبعية Aspose.Words إلى مشروعك. لـ Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

أو لـ Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## نظرة عامة على الحل

يتبع الدليل نمط **المشكلة → الحل → الشرح** الواضح:

1. **إنشاء مستند Word جديد** والحصول على `DocumentBuilder`.  
2. **إدراج حاوية `GroupShape`** التي ستحمل عدة أشكال.  
3. **إضافة مستطيل**، ضبط عرضه/ارتفاعه (خطوة **set shape size**)، وإرفاقه بالمجموعة.  
4. **إضافة إهليلج**، وضعه داخل نفس المجموعة، وضبط أبعاده أيضاً.  
5. **حفظ** المستند على القرص.

كل خطوة تتضمن **السبب** وراء الكود، لتفهم ما تفعله الـ API وكيف يمكنك تعديلها لتناسب سيناريوهات أخرى.

## الخطوة 1: إنشاء المستند وDocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**لماذا هذا مهم:** `Document` تمثل ملف DOCX بالكامل، بينما `DocumentBuilder` أداة مساعدة تسمح لك بإدراج المحتوى دون التعامل مع إدارة العقد منخفضة المستوى. إن إنشائهما أولاً يمنحك لوحة نظيفة لجميع عمليات الأشكال اللاحقة.

## الخطوة 2: إدراج حاوية GroupShape

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

`GroupShape` يعمل كـ **مجلد** لكائنات الرسم. عندما تحرك أو تدور أو تحذف المجموعة، تتبع جميع الأشكال الفرعية ذلك تلقائياً. هذا هو جوهر **group shapes in word**.

## الخطوة 3: إضافة شكل مستطيل – كود شكل المستطيل

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – يتلقى مُنشئ `Shape` القيمة `ShapeType.RECTANGLE`، مما يخبر Aspose.Words برسم حدود مستطيلة.  
- **set shape size** – `setWidth` و `setHeight` يحددان **shape dimensions** بالنقاط (1 pt = 1/72 in). هذه هي الطريقة الأكثر شيوعاً للتحكم في الحجم البصري.  
- **Why we use `appendChild`** – يربط المستطيل بـ `GroupShape` بحيث يتحرك مع المجموعة.

## الخطوة 4: إضافة إهليلج وتحديد موقعه داخل المجموعة

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

يوضح الإهليلج **set shape dimensions** بما يتجاوز المستطيل البسيط. عبر استدعاء `setLeft`، نتحكم في الإزاحة الأفقية داخل المجموعة، وهو مفيد عند ترتيب عدة كائنات.

## الخطوة 5: حفظ المستند

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

عند فتح *GroupShapeDemo.docx* في Microsoft Word، ستظهر لك مستطيل وإهليلج مقفلين معاً داخل مجموعة واحدة. اختيار أي من الشكلين سيختار المجموعة بالكامل—تماماً ما تتوقعه عند **group shapes in word**.

## مثال كامل قابل للتنفيذ

بدمج جميع الأجزاء معاً، إليك ملف المصدر الكامل الذي يمكنك نسخه إلى IDE الخاص بك:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### النتيجة المتوقعة

- يظهر ملف باسم **GroupShapeDemo.docx** في مجلد المشروع.  
- فتح الملف في Word يُظهر شكلين (مستطيل وإهليلج) تم تجميعهما معاً.  
- سحب أي من الشكلين ينقل المجموعة بأكملها، مؤكدًا أن **group shapes in word** يعمل كما هو متوقع.

## تنويعات شائعة وحالات حافة

| السيناريو | ما الذي يجب تغييره | السبب |
|----------|----------------|-----|
| **أنواع أشكال مختلفة** (مثل المثلث) | استخدم `ShapeType.TRIANGLE` أو أي قيمة enum أخرى عند إنشاء `Shape`. | يتيح لك بناء مخططات أكثر تعقيداً. |
| **تعيين لون التعبئة** | استدعِ `shape.getFillColor().setColor(Color.BLUE);` بعد إنشاء الشكل. | يحسن المظهر البصري دون التأثير على التجميع. |
| **دوران المجموعة** | `groupShape.setRotationAngle(45);` | يدور جميع الأشكال الفرعية معاً، مفيد للأيقونات. |
| **إضافة نص داخل الشكل** | `shape.appendChild(new Paragraph(document));` ثم أضف `Run` يحتوي على النص. | يجعل الشكل يعمل كعلامة أو توضيح. |
| **الحفظ إلى تدفق** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | مفيد لخدمات الويب التي تُعيد المستند مباشرة. |

### نصيحة احترافية

عندما تحتاج إلى **set shape dimensions** بناءً على بيانات ديناميكية (مثل طول الباركود)، احسب العرض/الارتفاع بالنقاط أولاً:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

هذا يتجنب الترميز الصلب للقيم ويحافظ على قابلية تعديل الكود.

## الخلاصة

أنت الآن تعرف كيف **تجميع الأشكال في Word** باستخدام Java، وكيف **إضافة شكل مستطيل**، وكيف **ضبط حجم الشكل** و**ضبط أبعاد الشكل** بكود مختصر وجاهز للإنتاج. باتباع الخطوات أعلاه، يمكنك إنشاء مجموعات رسومية قابلة لإعادة الاستخدام، دمجها في تقارير آلية، أو بناء أدوات تخطيط مخصصة دون الحاجة إلى فتح Word يدوياً.

### ما التالي؟

- استكشف تنويعات **add rectangle shape** مثل الزوايا المستديرة (`ShapeType.RECTANGLE` مع `setCornerRadius`).  
- اجمع **group shapes in word** مع الجداول أو المخططات للحصول على مستندات أغنى.  
- اطلع على Aspose.Words API لـ **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) للتحكم في كيفية تفاعل النص المحيط مع الرسومات المجمعة.

لا تتردد في التجربة، تعديل **rectangle shape code**، ومشاركة نتائجك.

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}