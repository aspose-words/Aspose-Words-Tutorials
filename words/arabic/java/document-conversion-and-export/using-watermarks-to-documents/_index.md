---
"description": "تعرّف على كيفية إضافة علامات مائية إلى المستندات في Aspose.Words لجافا. خصّص علامات مائية للنصوص والصور لمستندات احترافية."
"linktitle": "استخدام العلامات المائية على المستندات"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "استخدام العلامات المائية في المستندات في Aspose.Words لـ Java"
"url": "/ar/java/document-conversion-and-export/using-watermarks-to-documents/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# استخدام العلامات المائية في المستندات في Aspose.Words لـ Java


## مقدمة حول إضافة العلامات المائية إلى المستندات في Aspose.Words لـ Java

في هذا البرنامج التعليمي، سنستكشف كيفية إضافة علامات مائية إلى المستندات باستخدام واجهة برمجة تطبيقات Aspose.Words لجافا. تُعد العلامات المائية وسيلة مفيدة لتمييز المستندات التي تحتوي على نصوص أو رسومات للإشارة إلى حالتها أو سريتها أو أي معلومات أخرى ذات صلة. سنتناول في هذا الدليل كلاً من العلامات المائية النصية والصورية.

## إعداد Aspose.Words لـ Java

قبل البدء بإضافة العلامات المائية إلى المستندات، علينا إعداد Aspose.Words لجافا. اتبع الخطوات التالية للبدء:

1. تنزيل Aspose.Words لـ Java من [هنا](https://releases.aspose.com/words/java/).
2. أضف مكتبة Aspose.Words for Java إلى مشروع Java الخاص بك.
3. استيراد الفئات اللازمة في الكود Java الخاص بك.

الآن بعد أن قمنا بإعداد المكتبة، فلننتقل إلى إضافة العلامات المائية.

## إضافة علامات مائية نصية

تُعد العلامات المائية النصية خيارًا شائعًا لإضافة معلومات نصية إلى مستنداتك. إليك كيفية إضافة علامة مائية نصية باستخدام Aspose.Words لجافا:

```java
// إنشاء مثيل مستند
Document doc = new Document("Document.docx");

// تحديد خيارات العلامة المائية النصية
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// تعيين نص العلامة المائية والخيارات
doc.getWatermark().setText("Test", options);

// احفظ المستند بالعلامة المائية
doc.save("DocumentWithWatermark.docx");
```

## إضافة العلامات المائية للصور

بالإضافة إلى العلامات المائية النصية، يمكنك أيضًا إضافة علامات مائية للصور إلى مستنداتك. إليك كيفية إضافة علامة مائية للصور:

```java
// إنشاء مثيل مستند
Document doc = new Document("Document.docx");

// تحميل الصورة للعلامة المائية
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// تعيين حجم العلامة المائية وموضعها
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// إضافة العلامة المائية إلى المستند
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// احفظ المستند بالعلامة المائية
doc.save("DocumentWithImageWatermark.docx");
```

## تخصيص العلامات المائية

يمكنك تخصيص العلامات المائية بتعديل مظهرها وموقعها. بالنسبة للعلامات المائية النصية، يمكنك تغيير الخط والحجم واللون والتخطيط. أما بالنسبة للعلامات المائية للصور، فيمكنك تعديل حجمها وموقعها كما هو موضح في الأمثلة السابقة.

## إزالة العلامات المائية

لإزالة العلامات المائية من مستند، يمكنك استخدام الكود التالي:

```java
// إنشاء مثيل مستند
Document doc = new Document("DocumentWithWatermark.docx");

// إزالة العلامة المائية
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// احفظ المستند بدون العلامة المائية
doc.save("DocumentWithoutWatermark.docx");
```


## خاتمة

في هذا البرنامج التعليمي، تعلمنا كيفية إضافة علامات مائية إلى المستندات باستخدام Aspose.Words لجافا. سواءً كنت ترغب في إضافة علامات مائية نصية أو صورية، يوفر Aspose.Words الأدوات اللازمة لتخصيصها وإدارتها بكفاءة. كما يمكنك إزالة العلامات المائية عند عدم الحاجة إليها، مما يضمن نظافة مستنداتك واحترافيتها.

## الأسئلة الشائعة

### كيف يمكنني تغيير خط العلامة المائية النصية؟

لتغيير خط العلامة المائية النصية، قم بتعديل `setFontFamily` الممتلكات في `TextWatermarkOptions`. على سبيل المثال:

```java
options.setFontFamily("Times New Roman");
```

### هل يمكنني إضافة علامات مائية متعددة إلى مستند واحد؟

نعم، يمكنك إضافة علامات مائية متعددة إلى مستند عن طريق إنشاء علامات مائية متعددة `Shape` الكائنات ذات الإعدادات المختلفة وإضافتها إلى المستند.

### هل من الممكن تدوير العلامة المائية؟

نعم، يمكنك تدوير العلامة المائية عن طريق ضبط `setRotation` الممتلكات في `Shape` القيم الإيجابية تدور العلامة المائية في اتجاه عقارب الساعة، والقيم السلبية تدورها عكس اتجاه عقارب الساعة.

### كيف يمكنني جعل العلامة المائية شفافة جزئيًا؟

لجعل العلامة المائية شفافة جزئيًا، اضبط `setSemitransparent` الممتلكات إلى `true` في `TextWatermarkOptions`.

### هل يمكنني إضافة علامات مائية إلى أقسام معينة من المستند؟

نعم، يمكنك إضافة علامات مائية إلى أقسام محددة من المستند عن طريق التكرار عبر الأقسام وإضافة العلامة المائية إلى الأقسام المطلوبة.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}