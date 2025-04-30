---
"description": "اكتشف قوة أشكال المستندات في Aspose.Words لجافا. تعلم كيفية إنشاء مستندات جذابة بصريًا من خلال أمثلة خطوة بخطوة."
"linktitle": "استخدام أشكال المستندات"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "استخدام أشكال المستندات في Aspose.Words للغة Java"
"url": "/ar/java/document-conversion-and-export/using-document-shapes/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# استخدام أشكال المستندات في Aspose.Words للغة Java


## مقدمة لاستخدام أشكال المستندات في Aspose.Words لـ Java

في هذا الدليل الشامل، سنتعمق في عالم أشكال المستندات في Aspose.Words لجافا. تُعد الأشكال عناصر أساسية لإنشاء مستندات جذابة بصريًا وتفاعلية. سواءً كنت بحاجة إلى إضافة تعليقات توضيحية أو أزرار أو صور أو علامات مائية، يوفر Aspose.Words لجافا الأدوات اللازمة للقيام بذلك بكفاءة. لنستكشف كيفية استخدام هذه الأشكال خطوة بخطوة مع أمثلة من الكود المصدري.

## البدء باستخدام أشكال المستندات

قبل البدء بالشرح، لنبدأ بإعداد بيئة العمل. تأكد من دمج Aspose.Words for Java في مشروعك. إذا لم تكن قد قمت بذلك بالفعل، يمكنك تنزيله من موقع Aspose الإلكتروني. [تنزيل Aspose.Words لـ Java](https://releases.aspose.com/words/java/)

## إضافة الأشكال إلى المستندات

### إدراج شكل المجموعة

أ `GroupShape` يسمح لك بتجميع أشكال متعددة معًا. إليك كيفية إنشاء وإدراج `GroupShape`:

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

### إدراج شكل مربع نص

لإدراج شكل مربع نص، يمكنك استخدام `insertShape` الطريقة كما هو موضح في المثال أدناه:

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

## التلاعب بخصائص الشكل

### إدارة نسبة العرض إلى الارتفاع

يمكنك التحكم في تثبيت نسبة العرض إلى الارتفاع لشكل ما. إليك كيفية إلغاء قفل نسبة العرض إلى الارتفاع لشكل ما:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### وضع شكل في خلية جدول

إذا كنت بحاجة إلى وضع شكل داخل خلية جدول، فيمكنك تحقيق ذلك باستخدام الكود التالي:

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
watermark.isLayoutInCell(true); // عرض الشكل خارج خلية الجدول إذا كان سيتم وضعه داخل خلية.
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

## العمل مع أشكال SmartArt

### اكتشاف أشكال SmartArt

يمكنك اكتشاف أشكال SmartArt في مستند باستخدام الكود التالي:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### تحديث رسومات SmartArt

لتحديث رسومات SmartArt داخل مستند، استخدم الكود التالي:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## خاتمة

في هذا الدليل، استكشفنا عالم أشكال المستندات في Aspose.Words لجافا. تعلمت كيفية إضافة أشكال متنوعة إلى مستنداتك، والتعامل مع خصائصها، والعمل مع أشكال SmartArt. بفضل هذه المعرفة، يمكنك إنشاء مستندات جذابة بصريًا وتفاعلية بسهولة.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ Java؟

Aspose.Words for Java هي مكتبة جافا تُمكّن المطورين من إنشاء مستندات Word وتعديلها وتحويلها برمجيًا. تُوفر مجموعة واسعة من الميزات والأدوات للعمل مع المستندات بتنسيقات مُختلفة.

### كيف يمكنني تنزيل Aspose.Words لـ Java؟

يمكنك تنزيل Aspose.Words for Java من موقع Aspose الإلكتروني باتباع هذا الرابط: [تنزيل Aspose.Words لـ Java](https://releases.aspose.com/words/java/)

### ما هي فوائد استخدام أشكال المستندات؟

تُضفي أشكال المستندات عناصر بصرية وتفاعلية على مستنداتك، مما يجعلها أكثر جاذبية وإثراءً بالمعلومات. باستخدام الأشكال، يمكنك إنشاء تعليقات توضيحية وأزرار وصور وعلامات مائية وغيرها، مما يُحسّن تجربة المستخدم بشكل عام.

### هل يمكنني تخصيص مظهر الأشكال؟

نعم، يمكنك تخصيص مظهر الأشكال بتعديل خصائصها، مثل الحجم والموضع والدوران ولون التعبئة. يوفر Aspose.Words لجافا خيارات واسعة لتخصيص الأشكال.

### هل Aspose.Words for Java متوافق مع SmartArt؟

نعم، يدعم Aspose.Words for Java أشكال SmartArt، مما يسمح لك بالعمل مع المخططات والرسومات المعقدة في مستنداتك.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}