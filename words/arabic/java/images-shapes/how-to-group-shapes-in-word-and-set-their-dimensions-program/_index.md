---
category: general
date: 2026-11-25
description: كيفية تجميع الأشكال في Word باستخدام Java وكيفية ضبط أبعاد الشكل في ملف
  DOCX باستخدام Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: ar
lastmod: 2026-11-25
og_description: كيفية تجميع الأشكال في Word باستخدام Aspose.Words Java API وتعيين
  حجم الشكل بسرعة. اتبع الحل الكامل خطوة بخطوة.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: كيفية تجميع الأشكال في Word وتحديد أبعادها – دليل Java
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: كيفية تجميع الأشكال في Word وتحديد أبعادها برمجيًا
url: /ar/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تجميع الأشكال في Word وتعيين أبعادها برمجياً

إذا كنت بحاجة إلى **كيفية تجميع الأشكال في Word** والتحكم في حجمها الدقيق، يوضح لك هذا الدليل حلاً كاملاً وقابلاً للتنفيذ. باستخدام Aspose.Words for Java يمكنك إنشاء مستطيل، وإهليلج، وإضافتهما إلى `GroupShape`، ثم **كيفية تعيين أبعاد الشكل** مثل العرض والارتفاع في ملف DOCX واحد.

ستتعلم كيفية:

* إنشاء مستند Word جديد من الصفر.  
* إدراج `GroupShape` (API جديد في الإصدار 24.9).  
* إضافة مستطيل وإهليلج إلى المجموعة.  
* **تعيين حجم الشكل في Word** بدقة باستخدام `setWidth` و `setHeight`.  
* حفظ المستند إلى القرص.

لا يتطلب أي أدوات خارجية—فقط Java 17+، Maven، ومكتبة Aspose.Words for Java.

## المتطلبات المسبقة

* مجموعة تطوير جافا 17 أو أحدث.  
* Maven (أو Gradle) لإدارة الاعتماديات.  
* Aspose.Words for Java 24.9 أو أحدث (تم تقديم API `GroupShape` في 24.9).  
* إلمام أساسي بصياغة Java ومفاهيم البرمجة الكائنية.

إذا لم تقم بعد بإضافة Aspose.Words إلى مشروعك، أدرج الاعتماد التالي في Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## الخطوة 1: إنشاء مستند جديد وDocumentBuilder

تمثل الفئة `Document` الملف Word بالكامل، بينما يوفر `DocumentBuilder` طريقة مريحة لإضافة المحتوى.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*لماذا هذه الخطوة؟*  
إنشاء `Document` جديد يمنحك لوحة رسم نظيفة. `DocumentBuilder` هو المساعد عالي المستوى الذي يتيح لك إدراج فقرات، جداول، وفي هذه الحالة، أشكال.

## الخطوة 2: إدراج GroupShape (API جديد في الإصدار 24.9)

يعمل `GroupShape` كحاوية؛ أي شكل تضيفه يصبح جزءًا من نفس المجموعة البصرية.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*لماذا نستخدم `GroupShape`؟*  
تجميع الأشكال يبسط نقلها، تدويرها، أو تطبيق تنسيق عليها جميعًا مرة واحدة. تمت إضافة هذا الـ API في 24.9، لذا الإصدارات الأقدم لن تُترجم هذا السطر.

## الخطوة 3: إنشاء مستطيل، تعيين حجمه، وإضافته إلى المجموعة

هنا نوضح **كيفية تعيين أبعاد الشكل** لمستطيل.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*لماذا نحدد العرض والارتفاع صراحةً؟*  
يخزن Word حجم الشكل بالنقاط. باستدعاء `setWidth` و `setHeight` تتحكم في البصمة البصرية الدقيقة، وهو أمر أساسي عندما تحتاج إلى تخطيط دقيق أو عند التصدير إلى PDF.

## الخطوة 4: إنشاء إهليلج، تعيين حجمه، وإضافته إلى نفس المجموعة

تقنية **تعيين حجم الشكل في Word** نفسها تعمل مع أي نوع من الأشكال.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*لماذا نضيف الإهليلج إلى نفس `GroupShape`؟*  
كلا الشكلين سيتحركان معًا كوحدة واحدة. هذا مفيد لإنشاء أيقونات، شعارات، أو مخططات معقدة يجب أن تبقى محاذية.

## الخطوة 5: حفظ المستند مع الأشكال المجمعة

أخيرًا، احفظ ملف DOCX إلى القرص.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

تشغيل هذا البرنامج ينتج ملفًا باسم **GroupShape.docx** يحتوي على مستطيل وإهليلج مجمّعين معًا. عند فتح الملف في Microsoft Word، ستلاحظ أن الشكلين يتصرفان ككائن واحد—يمكنك سحبهما، تغيير حجمهما، أو تدويرهما معًا.

### النتيجة المتوقعة

* مستند Word (`GroupShape.docx`) بصفحة واحدة.  
* `GroupShape` يحتوي على مستطيل بحجم 100 × 50 نقطة وإهليلج بحجم 80 × 80 نقطة.  
* اختيار أي من الشكلين يختار المجموعة بأكملها.

## أسئلة شائعة وحالات خاصة

### كيفية تغيير موضع الأشكال المجمعة؟

بعد إنشاء `GroupShape`، يمكنك تعيين خصائص `left` و `top` الخاصة به:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

هذه الإحداثيات تُقاس أيضًا بالنقاط.

### ماذا لو أردت إضافة أكثر من شكلين؟

يعمل `GroupShape` كأي عقدة حاوية أخرى. استدعِ `groupShape.appendChild(yourShape)` لكل شكل إضافي. الـ API لا يحد من عدد الأطفال.

### هل يمكن تطبيق نمط (لون التعبئة، وزن الخط) على الأشكال الفردية؟

نعم. كل كائن `Shape` يتيح خصائص تنسيق:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### هل يعمل الكود مع إصدارات Aspose.Words القديمة؟

تم تقديم طريقة `insertGroupShape` في الإصدار 24.9. إذا كنت تستخدم إصدارًا أقدم، سيتعين عليك إنشاء `GroupShape` يدويًا عبر شجرة العقد، وهو أمر أكثر تعقيدًا. التحديث هو المسار الموصى به.

## نصائح احترافية

* **استخدم النقاط للاتساق** – الوحدة الداخلية في Word هي النقطة (1/72 إنش). التحويل من البيكسل أو السنتيمتر قد يؤدي إلى أحجام غير متوقعة.  
* **اجمع قبل تحديد الموضع** – حدد موضع `GroupShape` بعد إضافة جميع أطفاله؛ وإلا قد تحتاج إلى إعادة حساب الإزاحات.  
* **أعد استخدام DocumentBuilder** – يمكنك إدراج مجموعات متعددة في نفس المستند بنقل مؤشر الباني (`builder.moveTo`) قبل كل استدعاء `insertGroupShape`.

## الخلاصة

أصبح لديك الآن مثال كامل من البداية إلى النهاية حول **كيفية تجميع الأشكال في Word** و**كيفية تعيين أبعاد الشكل** باستخدام Aspose.Words for Java. غطى الدرس إنشاء مستند، إدراج `GroupShape`، إضافة مستطيل وإهليلج، تعيين حجمهما الدقيق، وحفظ النتيجة.

من هنا يمكنك استكشاف:

* إضافة صناديق نص أو صور إلى نفس المجموعة.  
* تحريك الأشكال المجمعة باستخدام ميزات SmartArt في Word (عبر الـ API).  
* تصدير الأشكال المجمعة إلى PDF أو SVG للاستخدام على الويب.

لا تتردد في تجربة أنواع أشكال، أحجام، ومواقع مختلفة—التجميع يمنحك سيطرة قوية على تخطيطات معقدة في مستندات Word.

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم استعراضها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}