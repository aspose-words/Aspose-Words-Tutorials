---
category: general
date: 2026-09-21
description: إنشاء مستند Word برمجيًا باستخدام Java. تعلم كيفية تجميع الأشكال في Word،
  وإدراج شكل مستطيل، وتحديد حجم الشكل، وإضافة الأشكال إلى مستند Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: ar
lastmod: 2026-09-21
og_description: 'إنشاء مستند Word برمجيًا باستخدام Java: يوضح هذا الدليل كيفية تجميع
  الأشكال في Word، وإدراج أشكال مستطيلة، وتحديد حجم الشكل، وإضافة الأشكال إلى مستند
  Word.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: إنشاء مستند Word برمجيًا، تجميع الأشكال في Java
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: إنشاء مستند Word برمجيًا، تجميع الأشكال في جافا
url: /ar/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word برمجياً، تجميع الأشكال في Java

إذا كنت بحاجة إلى **إنشاء مستند Word برمجياً**، فإن هذا الدليل يشرح لك حلًا كاملاً. ستتعرف على كيفية **تجميع الأشكال في Word**، وإدراج مستطيل، وتحديد حجمه، وإضافة أشكال أخرى—كل ذلك باستخدام Java ومكتبة Aspose.Words for Java.

يغطي الدليل كل خطوة من إعداد المشروع إلى حفظ ملف .docx النهائي. في النهاية ستتمكن من توليد مستند Word يحتوي على مستطيل وصورة مُلفَفتين داخل مجموعة واحدة، مما يسهل تحريكهما أو تغيير حجمهما معًا. لا تحتاج إلى خبرة سابقة في Aspose.Words API، لكن يجب أن يكون لديك بيئة تطوير Java أساسية.

## المتطلبات المسبقة

* Java Development Kit (JDK) 8 أو أحدث  
* Maven أو Gradle لإدارة التبعيات  
* Aspose.Words for Java 23.9 (أو أحدث نسخة) – المكتبة مجانية للتقييم  
* ملف صورة (مثال: `sample.jpg`) موجود في دليل معروف  

وجود هذه العناصر جاهزة يضمن تشغيل الكود دون إعدادات إضافية.

## الخطوة 1: إعداد المشروع واستيراد Aspose.Words

إنشاء مشروع Maven (أو إضافة التبعيات إلى ملف `pom.xml` الحالي الخاص بك):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

إذا كنت تفضل Gradle، أضف ما يلي إلى `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

بعد حل التبعيات، استورد الفئات المطلوبة في ملف Java الخاص بك:

```java
import com.aspose.words.*;
import java.io.File;
```

## الخطوة 2: إنشاء مستند Word برمجياً

العملية الأولى في أي سيناريو أتمتة هي إنشاء كائن `Document` و `DocumentBuilder`. يبسط الـ builder إدراج النصوص، الصور، والأشكال.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

في هذه المرحلة المستند موجود فقط في الذاكرة. يمكنك الآن البدء في إضافة الأشكال.

## الخطوة 3: إدراج شكل مستطيل – كيفية إدراج شكل مستطيل

المستطيل هو `Shape` أساسي من النوع `ShapeType.RECTANGLE`. تتحكم في أبعاده باستخدام `setWidth` و `setHeight` وتحدد موقعه باستخدام `setTop` و `setLeft`.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**لماذا هذا مهم:** ضبط الحجم والموقع صراحةً (`set shape size word`) يضمن ظهور المستطيل بالضبط حيث تتوقع، بغض النظر عن تخطيط المستند الافتراضي.

## الخطوة 4: إدراج صورة – إضافة أشكال إلى مستند Word

يمكن لـ `DocumentBuilder` إدراج صورة مباشرةً من مسار ملف. بعد الإدراج، يمكنك إعادة تموضع الصورة مثل أي شكل آخر.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

كل من المستطيل والصورة الآن أشكال مستقلة داخل المستند.

## الخطوة 5: تجميع الأشكال – كيفية تجميع الأشكال في Word

تجميع الأشكال مفيد عندما تريد تحريكها أو تغيير حجمها كوحدة واحدة. توفر Aspose.Words حاوية `GroupShape` لهذا الغرض.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

عند حفظ المجموعة، يتعامل Word مع الطفلين ككائن منطقي واحد. يمكنك لاحقًا تحديد المجموعة وسحبها، وسيتبع كل من المستطيل والصورة ذلك.

## الخطوة 6: حفظ المستند

أخيرًا، اكتب المستند إلى القرص. يجب أن يكون المسار قابلًا للكتابة من قبل عملية Java.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

تشغيل طريقة `main` ينتج ملفًا باسم **GroupShapeExample.docx**. افتحه في Microsoft Word لترى مستطيلًا وصورةً مقفلين معًا داخل مجموعة. تحديد المجموعة يتيح لك تحريك الكائنين معًا، مما يؤكد نجاح التجميع.

## النتيجة المتوقعة

* ملف Word (`GroupShapeExample.docx`) موجود في الدليل الذي حددته.  
* داخل الملف، يظهر مستطيل (ملء رمادي فاتح) في الزاوية العليا اليسرى، وتجلس الصورة مباشرةً تحته.  
* كلا الكائنين جزء من مجموعة واحدة، لذا سحب أحدهما يحرك الآخر.

## الاختلافات الشائعة وحالات الحافة

| الحالة | التوصية |
|-----------|----------------|
| **تنسيقات الصور المختلفة** | Aspose.Words يدعم PNG و BMP و GIF و TIFF. استخدم الامتداد المناسب في `insertImage`. |
| **أبعاد سلبية** | API يطرح `ArgumentException`. تحقق دائمًا من صحة العرض والارتفاع قبل استدعاء `setWidth` / `setHeight`. |
| **مستندات كبيرة** | تجميع العديد من الأشكال قد يزيد من حجم الملف. فكر في دمج الأشكال في صورة واحدة عندما تكون الأداء مهمًا. |
| **توافق إصدارات Word** | `GroupShape` يعمل مع Word 2007 (`.docx`) وما بعده. بالنسبة للملفات `.doc` القديمة، سيتم تسطيح المجموعة. |
| **تموضع ديناميكي** | استخدم حسابات تعتمد على حجم الصفحة (`doc.getFirstSection().getPageSetup().getPageWidth()`) إذا كنت بحاجة إلى تموضع متكيف. |

**نصيحة احترافية:** بعد إنشاء المجموعة، يمكنك تغيير

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شاملة من الكود مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [إنشاء مستند Word Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [إنشاء شكل مستطيل في Word باستخدام Java – دليل كامل](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}