---
date: 2025-12-18
description: تعلم كيفية إضافة علامة مائية إلى المستندات باستخدام Aspose.Words للغة
  Java، بما في ذلك مثال على علامة مائية بالصورة، تغيير لون العلامة المائية، ضبط شفافية
  العلامة المائية، وإزالة العلامة المائية من المستند.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: كيفية إضافة علامة مائية إلى المستندات باستخدام Aspose.Words للـ Java
url: /ar/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة علامة مائية إلى المستندات باستخدام Aspose.Words for Java

## مقدمة حول إضافة العلامات المائية إلى المستندات في Aspose.Words for Java

في هذا الدرس ستتعلم **كيفية إضافة علامة مائية** إلى مستندات Word باستخدام Aspose.Words for Java. العلامات المائية طريقة سريعة لتصنيف ملف على أنه سري أو مسودة أو معتمد، ويمكن أن تكون نصية أو صورة. سنستعرض إعداد المكتبة، إنشاء علامات مائية نصية وصورية، تخصيص مظهرها (بما في ذلك تغيير لون العلامة المائية وتعيين شفافية العلامة المائية)، وحتى إزالة علامة مائية من المستند عندما لا تكون بحاجة إليها بعد الآن.

## إجابات سريعة
- **ما هي العلامة المائية؟** طبقة نصف شفافة (نصية أو صورة) تظهر خلف محتوى المستند الرئيسي.  
- **هل يمكنني إضافة عدة علامات مائية؟** نعم – أنشئ عدة كائنات `Shape` وأضف كل واحدة إلى الأقسام المطلوبة.  
- **كيف يمكنني تغيير لون العلامة المائية؟** اضبط خاصية `Color` في `TextWatermarkOptions`.  
- **هل هناك مثال على علامة مائية صورة؟** راجع قسم “إضافة علامات مائية صورة” أدناه.  
- **هل أحتاج إلى ترخيص لإزالة العلامة المائية؟** يلزم وجود ترخيص Aspose.Words صالح للاستخدام في الإنتاج.

## إعداد Aspose.Words for Java

قبل أن نبدأ في إضافة العلامات المائية إلى المستندات، نحتاج إلى إعداد Aspose.Words for Java. اتبع الخطوات التالية للبدء:

1. قم بتنزيل Aspose.Words for Java من [هنا](https://releases.aspose.com/words/java/).  
2. أضف مكتبة Aspose.Words for Java إلى مشروع Java الخاص بك.  
3. استورد الفئات الضرورية في كود Java الخاص بك.

الآن بعد أن تم إعداد المكتبة، دعنا نغوص في إنشاء العلامة المائية الفعلية.

## إضافة علامات مائية نصية

العلامات المائية النصية خيار شائع عندما تريد إضافة معلومات نصية إلى مستنداتك. إليك كيفية إضافة علامة مائية نصية باستخدام Aspose.Words for Java:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

**لماذا هذا مهم:** من خلال تعديل `setFontFamily` و `setFontSize` و `setColor` يمكنك **تغيير لون العلامة المائية** ليتناسب مع هوية علامتك التجارية، و `setSemitransparent(true)` يتيح لك **تعيين شفافية العلامة المائية** لتأثير خفيف.

## إضافة علامات مائية صورة

بالإضافة إلى العلامات المائية النصية، يمكنك أيضًا إضافة علامات مائية صورة إلى مستنداتك. أدناه مثال **على علامة مائية صورة** يوضح كيفية تضمين شعار PNG أو ختم:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

يمكنك تكرار هذا الجزء باستخدام صور أو مواضع مختلفة **لإضافة عدة علامات مائية** إلى ملف واحد.

## تخصيص العلامات المائية

يمكنك تخصيص العلامات المائية عن طريق تعديل مظهرها وموقعها. بالنسبة للعلامات المائية النصية، يمكنك تغيير الخط والحجم واللون والتخطيط. بالنسبة للعلامات المائية الصورية، يمكنك تعديل الحجم والدوران والمحاذاة كما هو موضح في الأمثلة السابقة.

## إزالة العلامات المائية

إذا كنت بحاجة إلى **إزالة محتوى علامة مائية** من المستند، فإن الكود التالي يتنقل عبر جميع الأشكال ويحذف تلك التي تم التعرف عليها كعلامات مائية:

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## حالات الاستخدام الشائعة والنصائح

- **مسودات سرية:** تطبيق علامة مائية نصية نصف شفافة مثل “CONFIDENTIAL”.  
- **العلامة التجارية:** استخدم علامة مائية صورة تحتوي على شعار شركتك.  
- **علامات مائية خاصة بالأقسام:** قم بالتكرار عبر `doc.getSections()` وأضف علامة مائية فقط إلى الأقسام التي تختارها.  
- **نصيحة الأداء:** أعد استخدام نفس كائن `TextWatermarkOptions` عند تطبيق نفس العلامة المائية على العديد من المستندات.

## الأسئلة المتكررة

### كيف يمكنني تغيير خط العلامة المائية النصية؟

لتغيير خط العلامة المائية النصية، عدل خاصية `setFontFamily` في `TextWatermarkOptions`. على سبيل المثال:

```java
options.setFontFamily("Times New Roman");
```

### هل يمكنني إضافة عدة علامات مائية إلى مستند واحد؟

نعم، يمكنك إضافة عدة علامات مائية إلى مستند عن طريق إنشاء عدة كائنات `Shape` بإعدادات مختلفة وإضافتها إلى المستند.

### هل يمكن تدوير العلامة المائية؟

نعم، يمكنك تدوير العلامة المائية عن طريق ضبط خاصية `setRotation` في كائن `Shape`. القيم الموجبة تدور العلامة المائية في اتجاه عقارب الساعة، والقيم السالبة تدورها في الاتجاه المعاكس.

### كيف يمكنني جعل العلامة المائية نصف شفافة؟

لجعل العلامة المائية نصف شفافة، اضبط خاصية `setSemitransparent` إلى `true` في `TextWatermarkOptions`.

### هل يمكنني إضافة علامات مائية إلى أقسام محددة من المستند؟

نعم، يمكنك إضافة علامات مائية إلى أقسام محددة من المستند عن طريق التكرار عبر الأقسام وإضافة العلامة المائية إلى الأقسام المطلوبة.

**آخر تحديث:** 2025-12-18  
**تم الاختبار مع:** Aspose.Words for Java 24.12  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}