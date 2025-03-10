---
title: عرض الأشكال والرسومات في المستندات
linktitle: عرض الأشكال والرسومات في المستندات
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تعرف على كيفية تحسين مستنداتك باستخدام الأشكال والرسومات باستخدام Aspose.Words for Java. أنشئ محتوى مذهلاً بصريًا دون عناء.
weight: 12
url: /ar/java/document-rendering/rendering-shapes-graphics/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# عرض الأشكال والرسومات في المستندات

## مقدمة

في هذا العصر الرقمي، غالبًا ما تحتاج المستندات إلى أكثر من مجرد نص عادي. يمكن أن يؤدي إضافة الأشكال والرسومات إلى نقل المعلومات بشكل أكثر فعالية وجعل مستنداتك جذابة بصريًا. Aspose.Words for Java عبارة عن واجهة برمجة تطبيقات Java قوية تتيح لك التعامل مع مستندات Word، بما في ذلك إضافة الأشكال والرسومات وتخصيصها.

## البدء باستخدام Aspose.Words للغة Java

قبل أن نتعمق في إضافة الأشكال والرسومات، فلنبدأ باستخدام Aspose.Words for Java. ستحتاج إلى إعداد بيئة التطوير الخاصة بك وتضمين مكتبة Aspose.Words. فيما يلي الخطوات اللازمة للبدء:

```java
// أضف Aspose.Words إلى مشروع Maven الخاص بك
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>latest-version</version>
</dependency>

// تهيئة Aspose.Words
Document doc = new Document();
```

## إضافة الأشكال إلى المستندات

يمكن أن تتراوح الأشكال من المستطيلات البسيطة إلى المخططات المعقدة. يوفر Aspose.Words for Java مجموعة متنوعة من أنواع الأشكال، بما في ذلك الخطوط والمستطيلات والدوائر. لإضافة شكل إلى مستندك، استخدم الكود التالي:

```java
// إنشاء شكل جديد
Shape shape = new Shape(doc, ShapeType.RECTANGLE);

// تخصيص الشكل
shape.setWidth(100);
shape.setHeight(50);
shape.setStrokeColor(Color.RED);
shape.setFillColor(Color.YELLOW);

// أدخل الشكل في المستند
doc.getFirstSection().getBody().getFirstParagraph().appendChild(shape);
```

## إدراج الصور

يمكن للصور أن تعزز مستنداتك بشكل كبير. يتيح لك برنامج Aspose.Words for Java إدراج الصور بسهولة:

```java
// تحميل ملف الصورة
byte[] imageBytes = Files.readAllBytes(Paths.get("path/to/your/image.png"));
Shape imageShape = new Shape(doc, ShapeType.IMAGE);
imageShape.getImageData().setImage(imageBytes);
doc.getFirstSection().getBody().getFirstParagraph().appendChild(imageShape);
```

## تخصيص الأشكال

يمكنك تخصيص الأشكال بشكل أكبر عن طريق تغيير ألوانها وحدودها وخصائصها الأخرى. فيما يلي مثال لكيفية القيام بذلك:

```java
shape.setStrokeColor(Color.BLUE);
shape.setFillColor(Color.GREEN);
shape.getStroke().setWeight(2.0);
shape.setShadowEnabled(true);
```

## تحديد المواقع والحجم

يعد تحديد موضع وحجم الأشكال بدقة أمرًا بالغ الأهمية لتخطيط المستند. يوفر Aspose.Words for Java طرقًا لتعيين هذه الخصائص:

```java
shape.setLeft(100);
shape.setTop(200);
shape.setWidth(150);
shape.setHeight(75);
```

## العمل مع النص داخل الأشكال

يمكن أن تحتوي الأشكال أيضًا على نص. يمكنك إضافة نص وتنسيقه داخل الأشكال باستخدام Aspose.Words for Java:

```java
shape.getTextPath().setText("This is some text within the shape");
shape.getTextPath().setFontFamily("Arial");
shape.getTextPath().setFontSize(12);
```

## تجميع الأشكال

لإنشاء مخططات أو ترتيبات أكثر تعقيدًا، يمكنك تجميع الأشكال معًا:

```java
ShapeCollection group = new ShapeCollection(doc);
group.add(shape1);
group.add(shape2);
doc.getFirstSection().getBody().getFirstParagraph().appendChild(group);
```

## ترتيب الأشكال على شكل حرف Z

يمكنك التحكم في ترتيب عرض الأشكال باستخدام ترتيب Z:

```java
shape1.setZOrder(1); // إحضار إلى الأمام
shape2.setZOrder(0); // إرسال إلى الخلف
```

## حفظ المستند

بمجرد إضافة الأشكال والرسومات وتخصيصها، احفظ المستند:

```java
doc.save("output.docx");
```

## حالات الاستخدام الشائعة

يعد Aspose.Words for Java متعدد الاستخدامات ويمكن استخدامه في سيناريوهات مختلفة:

- إنشاء التقارير باستخدام المخططات والرسوم البيانية.
- إنشاء كتيبات تحتوي على رسومات جذابة للنظر.
- تصميم الشهادات والجوائز.
- إضافة التعليقات التوضيحية والتعليقات التوضيحية إلى المستندات.

## نصائح استكشاف الأخطاء وإصلاحها

إذا واجهت مشكلات أثناء العمل بالأشكال والرسومات، فراجع وثائق Aspose.Words for Java أو المنتديات المجتمعية للحصول على الحلول. تتضمن المشكلات الشائعة توافق تنسيق الصورة والمشكلات المتعلقة بالخطوط.

## خاتمة

إن تحسين مستنداتك باستخدام الأشكال والرسومات يمكن أن يحسن بشكل كبير من جاذبيتها البصرية وفعاليتها في نقل المعلومات. يوفر Aspose.Words for Java مجموعة قوية من الأدوات لإنجاز هذه المهمة بسلاسة. ابدأ في إنشاء مستندات مذهلة بصريًا اليوم!

## الأسئلة الشائعة

### كيف يمكنني تغيير حجم الشكل في مستندي؟

 لتغيير حجم الشكل، استخدم`setWidth` و`setHeight` الأساليب على كائن الشكل. على سبيل المثال، لجعل الشكل بعرض 150 بكسل وارتفاع 75 بكسل:

```java
shape.setWidth(150);
shape.setHeight(75);
```

### هل يمكنني إضافة أشكال متعددة إلى مستند؟

نعم، يمكنك إضافة أشكال متعددة إلى مستند. ما عليك سوى إنشاء أشكال متعددة وإضافتها إلى نص المستند أو فقرة محددة.

### كيف يمكنني تغيير لون الشكل؟

يمكنك تغيير لون الشكل عن طريق تعيين خصائص لون الحد ولون التعبئة لكائن الشكل. على سبيل المثال، لتعيين لون الحد إلى الأزرق ولون التعبئة إلى الأخضر:

```java
shape.setStrokeColor(Color.BLUE);
shape.setFillColor(Color.GREEN);
```

### هل يمكنني إضافة نص داخل الشكل؟

 نعم، يمكنك إضافة نص داخل الشكل. استخدم`getTextPath` خاصية الشكل لتعيين النص وتخصيص تنسيقه.

### كيف يمكنني ترتيب الأشكال بترتيب معين؟

 يمكنك التحكم في ترتيب الأشكال باستخدام خاصية ترتيب Z. اضبط`ZOrder` خاصية الشكل لتحديد موضعه في كومة الأشكال. يتم إرسال القيم المنخفضة إلى الخلف، بينما يتم إحضار القيم الأعلى إلى الأمام.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
