---
date: 2025-12-14
description: تعلم كيفية **إدراج شكل صورة** باستخدام Aspose.Words for Java. يوضح هذا
  الدليل كيفية إضافة الأشكال، إنشاء أشكال صندوق النص، وضع الأشكال في الجداول، ضبط
  نسبة أبعاد الشكل، وإضافة أشكال التعليق.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: استخدام أشكال المستند في Aspose.Words للـ Java
url: /ar/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية **insert image shape** باستخدام Aspose.Words for Java

في هذا الدرس الشامل ستكتشف كيفية **insert image shape** داخل مستندات Word باستخدام Aspose.Words for Java. سواءً كنت تُنشئ تقارير أو مواد تسويقية أو نماذج تفاعلية، تتيح لك الأشكال إضافة توضيحات، أزرار، مربعات نص، علامات مائية، وحتى SmartArt. سنستعرض كل خطوة، نشرح لماذا قد تستخدم شكلًا معينًا، ونوفر مقتطفات كود جاهزة للتنفيذ.

## إجابات سريعة
- **ما هي الطريقة الأساسية لإضافة شكل؟** استخدم `DocumentBuilder.insertShape` أو أنشئ كائن `Shape` وأضفه إلى شجرة المستند.  
- **هل يمكنني إدراج صورة كشكل؟** نعم – استدعِ `builder.insertImage` ثم عالج الـ `Shape` المُرجع كأي شكل آخر.  
- **كيف أحافظ على نسبة أبعاد الشكل؟** اضبط `shape.setAspectRatioLocked(true)` أو `false` حسب احتياجاتك.  
- **هل يمكن تجميع الأشكال؟** بالتأكيد – ضعها داخل `GroupShape` وأدرج المجموعة كعقدة واحدة.  
- **هل تعمل مخططات SmartArt مع Aspose.Words؟** نعم، يمكنك اكتشاف وتحديث أشكال SmartArt برمجيًا.

## ما هو **insert image shape**؟
‏*شكل الصورة* هو عنصر بصري يحتوي على رسومات نقطية أو متجهة داخل مستند Word. في Aspose.Words، تُمثَّل الصورة ككائن `Shape`، مما يمنحك تحكمًا كاملاً في الحجم، الموضع، الدوران، والالتفاف.

## لماذا تستخدم الأشكال في مستنداتك؟
- **التأثير البصري:** الأشكال تجذب الانتباه إلى المعلومات الرئيسية.  
- **التفاعلية:** يمكن ربط الأزرار والتوضيحات بـ URLs أو إشارات مرجعية.  
- **مرونة التخطيط:** وضع الرسومات بدقة باستخدام إحداثيات مطلقة أو نسبية.  
- **الأتمتة:** إنشاء تخطيطات معقدة دون تحرير يدوي.

## المتطلبات المسبقة
- Java Development Kit (JDK 8 أو أعلى)  
- مكتبة Aspose.Words for Java (حمّلها من الموقع الرسمي)  
- معرفة أساسية بـ Java والبرمجة الكائنية التوجه  

يمكنك تحميل المكتبة من هنا: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## كيفية **add shape** – إدراج GroupShape
‏`GroupShape` يتيح لك التعامل مع عدة أشكال كوحدة واحدة. هذا مفيد لنقل أو تنسيق عدة عناصر معًا.

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

## إنشاء **text box shape**
مربع النص هو حاوية يمكنها احتواء نص منسق. يمكنك أيضًا تدويره للحصول على مظهر ديناميكي.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## ضبط **shape aspect ratio**
أحيانًا تحتاج إلى أن يتمدد الشكل بحرية، وأحيانًا أخرى تريد الحفاظ على نسبه الأصلية. التحكم في نسبة الأبعاد سهل.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## وضع **shape in table**
إدراج شكل داخل خلية جدول يمكن أن يكون مفيدًا لتخطيطات التقارير. المثال أدناه ينشئ جدولًا ثم يدرج شكلًا بنمط العلامة المائية يمتد عبر الصفحة بأكملها.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## إضافة **callout shape**
شكل التوضيح مثالي لتسليط الضوء على الملاحظات أو التحذيرات. بينما يوضح الكود أعلاه بالفعل `ACCENT_BORDER_CALLOUT_1`، يمكنك استبدال `ShapeType` بأي نوع توضيح آخر ليناسب تصميمك.

## العمل مع أشكال SmartArt

### اكتشاف أشكال SmartArt
يمكن التعرف على مخططات SmartArt برمجيًا، مما يتيح لك معالجتها أو استبدالها حسب الحاجة.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### تحديث رسومات SmartArt
بعد اكتشافها، يمكنك تحديث رسومات SmartArt لتعكس أي تغييرات في البيانات.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## المشكلات الشائعة والنصائح
- **عدم ظهور الشكل:** تأكد من إدراج الشكل بعد العقدة المستهدفة باستخدام `builder.insertNode`.  
- **دوران غير متوقع:** تذكر أن الدوران يُطبق حول مركز الشكل؛ عدل `setLeft`/`setTop` إذا لزم الأمر.  
- **قفل نسبة الأبعاد:** بشكل افتراضي، كثير من الأشكال تقفل نسبة أبعادها؛ استدعِ `setAspectRatioLocked(false)` للتمدد بحرية.  
- **فشل اكتشاف SmartArt:** تأكد من أنك تستخدم نسخة Aspose.Words التي تدعم SmartArt (v24+).

## الأسئلة المتكررة

**س: ما هو Aspose.Words for Java؟**  
ج: Aspose.Words for Java هي مكتبة Java تتيح للمطورين إنشاء وتعديل وتحويل مستندات Word برمجيًا. توفر مجموعة واسعة من الميزات والأدوات للعمل مع المستندات بمختلف الصيغ.

**س: كيف يمكنني تحميل Aspose.Words for Java؟**  
ج: يمكنك تحميل Aspose.Words for Java من موقع Aspose عبر الرابط التالي: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**س: ما هي فوائد استخدام أشكال المستند؟**  
ج: تضيف أشكال المستند عناصر بصرية وتفاعلية إلى مستنداتك، مما يجعلها أكثر جاذبية وإفادة. باستخدام الأشكال، يمكنك إنشاء توضيحات، أزرار، صور، علامات مائية، وأكثر، مما يحسن تجربة المستخدم العامة.

**س: هل يمكنني تخصيص مظهر الأشكال؟**  
ج: نعم، يمكنك تخصيص مظهر الأشكال عن طريق تعديل خصائصها مثل الحجم، الموضع، الدوران، ولون التعبئة. توفر Aspose.Words for Java خيارات واسعة لتخصيص الأشكال.

**س: هل Aspose.Words for Java متوافق مع SmartArt؟**  
ج: نعم، تدعم Aspose.Words for Java أشكال SmartArt، مما يتيح لك العمل مع مخططات ورسومات معقدة في مستنداتك.

---

**آخر تحديث:** 2025-12-14  
**تم الاختبار مع:** Aspose.Words for Java 24.12 (latest)  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}