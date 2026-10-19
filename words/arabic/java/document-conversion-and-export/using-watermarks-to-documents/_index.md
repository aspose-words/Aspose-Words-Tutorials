---
date: 2026-02-19
description: تعلم كيفية إنشاء مستند مع علامة مائية باستخدام Aspose.Words للغة Java
  وإضافة علامة مائية صورة في Java للحصول على مستندات ذات مظهر احترافي.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: إنشاء مستند بعلامة مائية باستخدام Aspose.Words للـ Java
url: /ar/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند بعلامة مائية باستخدام Aspose.Words for Java

في هذا البرنامج التعليمي ستقوم **بإنشاء مستند بعلامة مائية** باستخدام واجهة برمجة تطبيقات Aspose.Words for Java. تساعد العلامات المائية—سواء كانت نصية أو صورًا—في تصنيف الملف على أنه سري، مسودة، أو معتمد، ويمكن تطبيقها برمجيًا على أي مستند Word. سنستعرض إعداد المكتبة، إضافة كل من العلامات المائية النصية والصورية، تخصيص مظهرها، وحتى إزالتها عندما لا تكون بحاجة إليها بعد الآن.

## الإجابات السريعة
- **ماذا تفعل العلامة المائية؟** تُضيف نصًا أو صورة فوق كل صفحة لتوضيح الحالة أو العلامة التجارية.  
- **أي مكتبة تضيف علامات مائية في Java؟** توفر Aspose.Words for Java دعمًا مدمجًا للعلامات المائية.  
- **هل يمكنني إضافة علامة مائية صورية؟** نعم—استخدم الفئة `Shape` وطريقة `add image watermark java`.  
- **هل العلامة المائية شبه شفافة؟** يمكنك التحكم في الشفافية عبر `setSemitransparent` للعلامات المائية النصية.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تعمل للاختبار؛ الترخيص التجاري مطلوب للإنتاج.

## ما هي العلامة المائية ولماذا نستخدمها؟

العلامة المائية هي تغطية خفيفة—نصية أو رسومية—تُضاف إلى كل صفحة من المستند. تُستخدم عادةً للإشارة إلى **السرية**، **حالة المسودة**، أو **العلامة التجارية** دون تعديل المحتوى الأساسي. يضمن إضافة العلامات المائية برمجيًا التناسق عبر دفعات كبيرة من الملفات ويوفر الوقت مقارنةً بالتحرير اليدوي.

## إعداد Aspose.Words for Java

قبل أن نبدأ بإضافة العلامات المائية، تأكد من أن المكتبة جاهزة في مشروعك:

1. حمّل Aspose.Words for Java من [هنا](https://releases.aspose.com/words/java/).  
2. أضف ملف JAR الذي تم تنزيله (أو الاعتماديات عبر Maven/Gradle) إلى مسار الفئات في مشروعك.  
3. استورد الفئات المطلوبة في ملف المصدر Java الخاص بك:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

الآن بعد أن تم إعداد المكتبة، دعنا ننتقل إلى كود العلامة المائية الفعلي.

## كيفية إضافة علامة مائية نصية

العلامات المائية النصية مثالية لتصنيف المستند كـ “CONFIDENTIAL” أو “DRAFT”. يُظهر المقتطف التالي طريقة نظيفة **لإنشاء مستند بعلامة مائية** باستخدام `TextWatermarkOptions`.

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

### تخصيص العلامة المائية النصية
- **عائلة الخط والحجم** – غيّر `setFontFamily` و `setFontSize`.  
- **اللون** – استخدم أي `java.awt.Color`.  
- **التخطيط** – اختر `HORIZONTAL`، `DIAGONAL`، إلخ.  
- **الشفافية** – فعّل `setSemitransparent(true)` للحصول على مظهر أخف.

## كيفية إضافة علامة مائية صورية (add image watermark java)

العلامات المائية الصورية مثالية للشعارات أو الرسومات المخصصة. أدناه مثال **add image watermark java** يدرج ملف PNG في وسط كل صفحة.

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

### نصائح للعلامات المائية الصورية
- **إعادة التحجيم** باستخدام `setWidth` / `setHeight` لتناسب الصفحة.  
- **الموضع** يمكن أن يكون مركزيًا أو محاذيًا لأي هامش باستخدام `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **الشفافية** يمكن تطبيقها عن طريق تعديل قناة ألفا للصورة قبل تحميلها.

## كيفية إزالة العلامات المائية

عندما لا يعود المستند بحاجة إلى علامة مائية، يمكنك حذفها برمجيًا. الكود أدناه يتنقل عبر جميع الأشكال ويزيل أي منها يحتوي على كلمة “Watermark” في اسمها.

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

## المشكلات الشائعة واستكشاف الأخطاء

- **العلامة المائية مفقودة بعد الحفظ** – تأكد من استدعاء `doc.save()` بعد ضبط العلامة المائية.  
- **الصورة لا تظهر** – تحقق من صحة مسار الصورة وأن الملف بصيغة مدعومة (PNG، JPEG، BMP).  
- **الشفافية غير مطبقة** – `setSemitransparent(true)` يعمل فقط للعلامات المائية النصية؛ بالنسبة للصور، عدّل قناة ألفا للـ PNG.  
- **وجود أقسام متعددة** – إذا كان المستند يحتوي على عدة أقسام، أضف العلامة المائية إلى جسم كل قسم أو استخدم `doc.getWatermark().setText(...)` لتطبيقها عالميًا.

## الأسئلة المتكررة

**س: كيف يمكنني تغيير خط العلامة المائية النصية؟**  
ج: عدّل خاصية `setFontFamily` في `TextWatermarkOptions`، مثال: `options.setFontFamily("Times New Roman");`.

**س: هل يمكنني إضافة عدة علامات مائية إلى مستند واحد؟**  
ج: نعم. أنشئ عدة كائنات `Shape` (للصور) أو استدعِ `doc.getWatermark().setText(...)` مع خيارات مختلفة لكل علامة مائية.

**س: هل يمكن تدوير العلامة المائية؟**  
ج: بالنسبة للعلامات المائية الصورية، اضبط الدوران على كائن `Shape` باستخدام `watermark.setRotation(angle)`. بالنسبة للعلامات المائية النصية، استخدم خاصية `setLayout` (مثلًا `WatermarkLayout.DIAGONAL`).

**س: كيف أجعل العلامة المائية شبه شفافة؟**  
ج: اضبط `options.setSemitransparent(true)` في `TextWatermarkOptions`. بالنسبة للصور، عدّل شفافية الصورة قبل تحميلها.

**س: هل يمكنني إضافة علامات مائية إلى أقسام محددة من المستند؟**  
ج: نعم. تنقّ عبر `doc.getSections()` وأضف العلامة المائية فقط إلى الأقسام المطلوبة.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**آخر تحديث:** 2026-02-19  
**تم الاختبار مع:** Aspose.Words for Java 24.12 (latest)  
**المؤلف:** Aspose