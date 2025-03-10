---
title: إضافة علامة مائية إلى المستندات وإعداد الصفحة
linktitle: إضافة علامة مائية إلى المستندات وإعداد الصفحة
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تعرف على كيفية إضافة العلامات المائية وإعداد تكوينات الصفحات باستخدام Aspose.Words for Java. دليل شامل مع الكود المصدر.
weight: 13
url: /ar/java/document-styling/document-watermarking-page-setup/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة علامة مائية إلى المستندات وإعداد الصفحة

## مقدمة

في مجال معالجة المستندات، يعد Aspose.Words for Java أداة قوية تتيح للمطورين التحكم في كل جانب من جوانب معالجة المستندات. في هذا الدليل الشامل، سنتعمق في تعقيدات وضع العلامات المائية على المستندات وإعداد الصفحات باستخدام Aspose.Words for Java. سواء كنت مطورًا متمرسًا أو كنت قد دخلت للتو عالم معالجة المستندات بلغة Java، فإن هذا الدليل التفصيلي سيزودك بالمعرفة وكود المصدر الذي تحتاج إليه.

## وضع علامة مائية على المستندات

### إضافة العلامات المائية

قد يكون إضافة العلامات المائية إلى المستندات أمرًا بالغ الأهمية لإضفاء العلامة التجارية على المحتوى أو تأمينه. يجعل Aspose.Words for Java هذه المهمة سهلة. إليك الطريقة:

```java
// تحميل المستند
Document doc = new Document("document.docx");

// إنشاء علامة مائية
Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.getTextPath().setText("Confidential");
watermark.setWidth(300);
watermark.setHeight(100);

// وضع العلامة المائية
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.setWrapType(WrapType.NONE);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);

// أدخل العلامة المائية
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// حفظ المستند
doc.save("document_with_watermark.docx");
```

### تخصيص العلامات المائية

يمكنك تخصيص العلامات المائية بشكل أكبر عن طريق ضبط الخط والحجم واللون والتدوير. تضمن هذه المرونة أن تتوافق العلامة المائية مع نمط المستند بسلاسة.

## إعداد الصفحة

### حجم الصفحة واتجاهها

يعد إعداد الصفحة أمرًا بالغ الأهمية في تنسيق المستندات. يوفر Aspose.Words for Java التحكم الكامل في حجم الصفحة واتجاهها:

```java
// تحميل المستند
Document doc = new Document("document.docx");

// ضبط حجم الصفحة إلى A4
doc.getFirstSection().getPageSetup().setPageWidth(595.0);
doc.getFirstSection().getPageSetup().setPageHeight(842.0);

// تغيير اتجاه الصفحة إلى الوضع الأفقي
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);

// حفظ المستند المعدل
doc.save("formatted_document.docx");
```

### الهوامش وترقيم الصفحات

يعد التحكم الدقيق في الهوامش وترقيم الصفحات أمرًا ضروريًا للمستندات الاحترافية. يمكنك تحقيق ذلك باستخدام Aspose.Words for Java:

```java
// تحميل المستند
Document doc = new Document("document.docx");

// تعيين الهوامش
doc.getFirstSection().getPageSetup().setLeftMargin(72.0);
doc.getFirstSection().getPageSetup().setRightMargin(72.0);
doc.getFirstSection().getPageSetup().setTopMargin(72.0);
doc.getFirstSection().getPageSetup().setBottomMargin(72.0);

// تمكين ترقيم الصفحات
doc.getFirstSection().getPageSetup().setDifferentFirstPageHeaderFooter(true);
HeaderFooter firstPageHeader = doc.getFirstSection().getHeadersFooters().getByHeaderFooterType(HeaderFooterType.HEADER_FIRST);
firstPageHeader.appendParagraph("First Page Header");

// حفظ المستند المنسق
doc.save("formatted_document.docx");
```

## الأسئلة الشائعة

### كيف يمكنني إزالة العلامة المائية من مستند؟

لإزالة علامة مائية من مستند، يمكنك تكرار الأشكال الموجودة في المستند وإزالة الأشكال التي تمثل العلامات المائية. فيما يلي مقتطف:

```java
Document doc = new Document("document_with_watermark.docx");

for (Shape shape : doc.getChildNodes(NodeType.SHAPE, true).<Shape>toArray()) {
    if (shape.getText().contains("Confidential")) {
        shape.remove();
    }
}

doc.save("document_without_watermark.docx");
```

### هل يمكنني إضافة علامات مائية متعددة إلى مستند واحد؟

نعم، يمكنك إضافة علامات مائية متعددة إلى مستند عن طريق إنشاء كائنات شكل إضافية وتحديد موضعها حسب الحاجة.

### كيف أقوم بتغيير حجم الصفحة إلى الحجم القانوني في الاتجاه الأفقي؟

لتعيين حجم الصفحة ليكون قانونيًا في الاتجاه الأفقي، قم بتعديل عرض الصفحة وارتفاعها على النحو التالي:

```java
doc.getFirstSection().getPageSetup().setPageWidth(842.0);
doc.getFirstSection().getPageSetup().setPageHeight(595.0);
```

### ما هو الخط الافتراضي للعلامات المائية؟

الخط الافتراضي للعلامات المائية هو Calibri بحجم خط 36.

### كيف يمكنني إضافة أرقام الصفحات بدءًا من صفحة معينة؟

يمكنك تحقيق ذلك عن طريق تعيين رقم الصفحة الأولية في مستندك على النحو التالي:

```java
doc.getFirstSection().getPageSetup().setPageStartingNumber(5);
```

### كيف أقوم بمحاذاة النص في منتصف الرأس أو التذييل؟

يمكنك محاذاة النص في منتصف الرأس أو التذييل باستخدام طريقة setAlignment على كائن الفقرة داخل الرأس أو التذييل.

## خاتمة

في هذا الدليل الشامل، استكشفنا فن وضع العلامات المائية على المستندات وإعداد الصفحات باستخدام Aspose.Words for Java. وبفضل مقتطفات التعليمات البرمجية المصدرية والرؤى المقدمة، أصبحت تمتلك الآن الأدوات اللازمة للتعامل مع مستنداتك وتنسيقها ببراعة. يمكّنك Aspose.Words for Java من إنشاء مستندات احترافية تحمل علامتك التجارية ومصممة وفقًا لمواصفاتك الدقيقة.

إن إتقان التعامل مع المستندات مهارة قيمة للمطورين، وبرنامج Aspose.Words for Java هو رفيقك الموثوق في هذه الرحلة. ابدأ في إنشاء مستندات مذهلة اليوم!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
