---
category: general
date: 2026-07-26
description: إدراج شكل مستطيل في Java باستخدام Aspose.Words. تعلم كيفية ضبط حجم الشكل،
  وتحديد موضع الشكل، وكيفية تجميع الأشكال في ملف DOCX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: ar
lastmod: 2026-07-26
og_description: أدرج شكلًا مستطيلًا في Java لإنشاء رسومات DOCX غنية. اتبع هذا الدليل
  خطوة بخطوة لضبط حجم الشكل، وتحديد موضعه، وتجميع الأشكال بسهولة.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: إدراج شكل مستطيل في جافا – إتقان التجميع وتحديد المواقع
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: إدراج شكل مستطيل في جافا – تجميع وتحديد موضع الأشكال
url: /ar/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج شكل مستطيل في جافا – تجميع وتحديد موضع الأشكال

هل احتجت يومًا إلى **insert rectangle shape** داخل مستند Word أثناء كتابة كود جافا؟ لست وحدك—المطورون الذين يبنون تقارير، فواتير، أو قوالب مخصصة يواجهون هذه المشكلة كثيرًا. الخبر السار هو أنه ببضع أسطر من Aspose.Words for Java يمكنك **insert rectangle shape**، **set shape size**، **position shape**، وحتى **how to group shapes** بحيث تتحرك كوحدة واحدة.

في هذا الدليل سنستعرض العملية بالكامل من إنشاء مستند فارغ إلى حفظ ملف `.docx` يحتوي على مستطيلين مجمّعين بشكل أنيق. بنهاية القراءة ستعرف **how to add rectangle**، كيفية التحكم بأبعادها، وضعها بدقة، وتجميعها في مجموعة قابلة لإعادة الاستخدام. لا تحتاج إلى مكتبات خارجية غير Aspose.Words، والكود يعمل مع Java 8‑plus.

## المتطلبات المسبقة

- تثبيت Java 8 أو أحدث (أستخدم JDK 17، لكن أي نسخة تدعم Maven تعمل)
- Aspose.Words for Java 23.9 أو أحدث – أضف الاعتماد إلى ملف `pom.xml` أو حمّل ملف JAR
- فهم أساسي لصياغة Java (إذا يمكنك كتابة طريقة `main` فأنت جاهز)
- بيئة تطوير أو محرر نصوص من اختيارك (IntelliJ IDEA، Eclipse، VS Code…)

> **نصيحة احترافية:** إذا كنت تستخدم Maven، فإن الاعتماد يبدو هكذا:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

الآن بعد أن وضعنا الأساس، دعنا نغوص في الكود.

## Insert Rectangle Shape and Set Its Size

أول شيء ستفعله هو إنشاء كائن `Document` جديد و`DocumentBuilder`. الـ builder هو “القلم” الذي يرسم الأشكال على الصفحة. أدناه نـ **insert rectangle shape** ونحدد فورًا **set shape size** إلى 100 × 80 نقطة.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

لاحظ كيف أن استدعاءات `setWidth`/`setHeight` **set shape size** بالنقاط (1 pt ≈ 1/72 inch). يمكنك أيضًا استخدام `setSize` إذا فضلت طريقة واحدة، لكن الاستدعاءات الصريحة تجعل النية واضحة تمامًا.

## Position Shape on the Page

بعد أن حصلنا على المستطيل الأول، نحتاج إلى **position shape** للمستطيل الثاني حتى لا يتداخل مع الأول. يعمل التحديد بنفس الطريقة: تقوم بتعيين خصائص `Left` و`Top` نسبةً إلى أصل المجموعة.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

إذا كنت تتساءل لماذا نستخدم `setLeft` بدلاً من `setX`، فذلك لأن Aspose.Words يتبع نظام إحداثيات Windows GDI التقليدي—`Left` هو الإزاحة الأفقية، `Top` هو الإزاحة العمودية. تعديل هذه القيم يتيح لك ضبط التخطيط بدقة دون الحاجة إلى الجداول أو الفقرات.

## How to Group Shapes

قد تتساءل، “لماذا نهتم بالمجموعة أصلاً؟” التجميع يكون منطقيًا عندما تريد أن تتحرك الأشكال معًا، أو تدور كوحدة، أو تشترك في نمط موحد. في المقتطف أعلاه أنشأنا بالفعل `GroupShape` عبر `builder.insertGroupShape`. هذا الكائن هو في الأساس حاوية—فكر فيه كمجلد يحتوي على ملفات أشكال أخرى.

> **لماذا هذا مهم:** إذا قررت لاحقًا إضافة تسمية توضيحية أو تدوير المخطط بالكامل، تحتاج فقط لتعديل المجموعة، وليس كل مستطيل على حدة.

## How to Add Rectangle to a Group

طريقة **how to add rectangle** إلى المجموعة هي ببساطة استدعاء `group.appendChild(rectangle)`. في الخلفية، تقوم Aspose.Words بتحديث مجموعة العناصر الداخلية وإعادة حساب الصندوق المحيط تلقائيًا بحيث لا تزال المجموعة تتناسب مع العرض والارتفاع المحددين.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

يمكنك تجربة `ShapeType`s أخرى—`ShapeType.ELLIPSE`، `ShapeType.TRIANGLE`، إلخ—ونمط `appendChild` يظل هو نفسه.

## Save the Document

أخيرًا، نقوم بحفظ المستند على القرص. يمكن أن يكون المسار مطلقًا أو نسبيًا؛ فقط تأكد من وجود المجلد.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

عند فتح `GroupShape.docx` في Microsoft Word، سترى مستطيلين جنبًا إلى جنب، كلاهما محاط داخل صندوق رمادي فاتح. تحديد الصندوق الرمادي سيُظهر كلا المستطيلين معًا—دليل على أن **how to group shapes** يعمل فعليًا.

![مستطيلات مجمّعة في مستند Word](placeholder-image.png){: .center-image alt="مثال على إدراج شكل مستطيل يظهر مستطيلين مجمّعين في ملف DOCX تم إنشاؤه بجافا"}

*نص بديل للصورة (SEO):* **مثال على إدراج شكل مستطيل يظهر مستطيلين مجمّعين في ملف DOCX تم إنشاؤه بجافا**.

## Expected Output

- ملف `GroupShape.docx` موجود في مجلد `output`.
- داخل المستند: مجموعة بحجم 400 × 200 pt تحتوي على مستطيلين (100 × 80 pt و120 × 60 pt) موضعين عند (20, 30) و(150, 50) على التوالي.
- للمجموعة حد أسود رفيع وتعبئة رمادية فاتحة، مما يجعل التجميع واضحًا بصريًا.

افتح الملف وجرب سحب الصندوق الرمادي—يجب أن يتحرك المستطيلان معًا. إذا لم يحدث ذلك، تحقق من أنك استدعيت `group.appendChild` لكل شكل.

## Common Pitfalls & Edge Cases

| المشكلة | سبب حدوثها | الحل |
|-------|----------------|-----|
| **المستطيلات تظهر خارج الصفحة** | قيم `Left`/`Top` تتجاوز أبعاد المجموعة | زيادة حجم المجموعة (`insertGroupShape(width, height)`) أو تقليل الإزاحات |
| **المجموعة تختفي بعد الحفظ** | تم ضبط `Width`/`Height` للمجموعة إلى 0 | توفير أبعاد غير صفرية عند استدعاء `insertGroupShape` |
| **ألوان الشكل تبدو خاطئة** | التعبئة الافتراضية شفافة؛ قد يعرض Word ذلك كأبيض | تعيين `setFillColor` صراحةً أو استخدام `ShapeStyle` |
| **استثناء `ArgumentOutOfRangeException`** | استخدام إحداثيات سلبية | الحفاظ على قيم `Left` و`Top` غير سلبية |

معالجة هذه المشكلات مبكرًا سيوفر عليك صداع “لماذا اختفى شكلي؟” الذي يواجهه الكثير من المبتدئين.

## Recap & Next Steps

غطينا دورة حياة **insert rectangle shape** بالكامل في جافا: إنشاء مستند، **set shape size**، **position shape**، **how to group shapes**، و**how to add rectangle** إلى تلك المجموعة. المثال الكامل القابل للتنفيذ موجود في المقتطف أعلاه، ويمكنك لصقه مباشرةً في مشروع Maven لرؤية النتيجة.

ما الخطوة التالية؟ فكر في تجربة:

- إضافة نص داخل كل مستطيل عبر

## What Should You Learn Next?

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي استعرضناها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}