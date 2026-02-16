---
date: 2026-02-16
description: تعرّف على كيفية إنشاء مربع نص، وإضافة كلمة كعلامة مائية، وتجميع أشكال
  متعددة، وتعيين نسبة أبعاد الشكل، ووضع الشكل في خلية جدول باستخدام Aspose.Words for
  Java.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: كيفية إنشاء مربع نص واستخدام أشكال المستند في Aspose.Words for Java
url: /ar/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

" keep same.

"**Tested With:** Aspose.Words for Java 24.12" keep.

"**Author:** Aspose" keep.

Then closing shortcodes.

Also there is a backtop button shortcode at end.

Make sure to keep all shortcodes exactly.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# استخدام أشكال المستند في Aspose.Words for Java

## مقدمة حول استخدام أشكال المستند في Aspose.Words for Java

في هذا الدليل الشامل، **ستتعلم كيفية إنشاء text box** كائنات وغيرها من الأشكال القوية باستخدام Aspose.Words for Java. تتيح لك الأشكال إثراء مستندات Word بإشارات توضيحية، أزرار، علامات مائية، SmartArt، وأكثر—مما يجعلها جذابة بصريًا وتفاعلية. سنستعرض أمثلة واقعية، بدءًا من إدراج مربع نص بسيط إلى تجميع عدة أشكال، ضبط نسب الأبعاد، ووضع الأشكال داخل خلايا الجداول.

## إجابات سريعة
- **ما هي الطريقة الأساسية لإضافة text box؟** استخدم `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **هل يمكنني تجميع الأشكال معًا؟** نعم – أنشئ `GroupShape` وأضف الأشكال الفرعية.
- **كيف أقفل أو أفتح نسبة أبعاد الشكل؟** استدعِ `shape.setAspectRatioLocked(true/false)`.
- **هل يمكن إضافة علامة مائية باستخدام شكل؟** بالتأكيد – أدخل `Shape` مع `TEXT_PLAIN_TEXT` واضبط التعبئة/الحد.
- **هل تعمل مخططات SmartArt مع Aspose.Words؟** نعم – اكتشف باستخدام `shape.hasSmartArt()` وحدث عبر `shape.updateSmartArtDrawing()`.

## ما هو text box ولماذا إنشاء أشكال text box؟

text box هو حاوية يمكنها احتواء نص منسق، صور، أو أشكال أخرى. استخدام **create text box** في أتمتتك يتيح لك وضع محتوى عائم في أي مكان على الصفحة، وهو مثالي للتعليقات التوضيحية، الإشارات، أو العناصر الزخرفية دون تعديل تدفق المستند الرئيسي.

## كيفية إضافة شكل

قبل أن نغوص في الكود، تأكد من أن Aspose.Words for Java مضمّن في مشروعك. إذا لم تقم بإضافته بعد، قم بتحميل المكتبة من الموقع الرسمي:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### إضافة أشكال إلى المستندات

## كيفية تجميع عدة أشكال

`GroupShape` يتيح لك التعامل مع عدة أشكال فردية كوحدة واحدة—مفيد لتحريكها أو تدويرها معًا.

### إدراج GroupShape

فيما يلي مثال كامل ينشئ مجموعة، يضيف شكلين مختلفين، ويُدرج المجموعة في المستند.

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

## كيفية إنشاء text box (create text box)

### إدراج شكل Text Box

طريقة `insertShape` تجعل إضافة text box سهلة. يوضح المثال أدناه طريقتين لتحديد موضع وتدوير text box.

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

## كيفية ضبط نسبة أبعاد الشكل

### إدارة نسبة الأبعاد

أحيانًا تحتاج إلى تمديد الشكل دون الحفاظ على نسبه الأصلية. يوضح المقتطف التالي كيفية فتح قفل نسبة أبعاد شكل صورة.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## كيفية وضع شكل داخل خلية جدول

### وضع شكل داخل خلية جدول

فيما يلي مثال خطوة بخطوة يبني جدولًا، ثم يُدرج شكل علامة مائية يتموضع بالنسبة للصفحة ولكنه يمكن أيضًا وضعه داخل خلية.

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

## العمل مع أشكال SmartArt

### اكتشاف أشكال SmartArt

يمكنك برمجيًا العثور على كائنات SmartArt في مستند باستخدام طريقة `hasSmartArt()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### تحديث رسومات SmartArt

بعد تحديد أشكال SmartArt، يمكنك تحديث بيانات الرسم الداخلية باستخدام `updateSmartArtDrawing()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## الخلاصة

في هذا الدليل، غطينا كيفية **create text box** كائنات، تجميع عدة أشكال، ضبط نسب الأبعاد، تضمين الأشكال داخل خلايا الجداول، إضافة علامات مائية، والعمل مع مخططات SmartArt باستخدام Aspose.Words for Java. تمكّنك هذه التقنيات من إنشاء مستندات Word مُنسقة بشكل غني وتفاعلية برمجيًا.

## الأسئلة الشائعة

### ما هو Aspose.Words for Java؟

Aspose.Words for Java هي مكتبة Java تتيح للمطورين إنشاء وتعديل وتحويل مستندات Word برمجيًا. توفر مجموعة واسعة من الميزات والأدوات للعمل مع المستندات بمختلف الصيغ.

### كيف يمكنني تحميل Aspose.Words for Java؟

يمكنك تحميل Aspose.Words for Java من موقع Aspose عبر الرابط التالي: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### ما هي فوائد استخدام أشكال المستند؟

تضيف أشكال المستند عناصر بصرية وتفاعلية إلى مستنداتك، مما يجعلها أكثر جاذبية وإفادة. باستخدام الأشكال، يمكنك إنشاء إشارات توضيحية، أزرار، صور، علامات مائية، وأكثر، مما يعزز تجربة المستخدم العامة.

### هل يمكنني تخصيص مظهر الأشكال؟

نعم، يمكنك تخصيص مظهر الأشكال عن طريق تعديل خصائصها مثل الحجم، الموضع، الدوران، ولون التعبئة. توفر Aspose.Words for Java خيارات واسعة لتخصيص الأشكال.

### هل Aspose.Words for Java متوافق مع SmartArt؟

نعم، يدعم Aspose.Words for Java أشكال SmartArt، مما يتيح لك العمل مع مخططات ورسومات معقدة في مستنداتك.

## الأسئلة المتكررة

**س: هل يمكنني دمج text box مع صورة داخل نفس الشكل؟**  
ج: نعم. أدخل صورة داخل شكل text box باستخدام `builder.insertImage()` بعد إنشاء الشكل، ثم اضبط تخطيطها حسب الحاجة.

**س: كيف أضمن أن تظهر العلامة المائية خلف جميع محتوى المستند؟**  
ج: اضبط `WrapType` للشكل إلى `NONE` واضبط `RelativeHorizontalPosition` و `RelativeVerticalPosition` إلى `PAGE`. هذا يضع العلامة المائية خلف التدفق الرئيسي.

**س: هل يمكن تحريك شكل مجموعة في Word؟**  
ج: رغم أن Aspose.Words يمكنه إنشاء وتجميع الأشكال، إلا أن ميزات التحريك غير مدعومة لأنها تعتمد على قدرات واجهة المستخدم في Word.

**س: ما هو إصدار Aspose.Words المطلوب لدعم SmartArt؟**  
ج: اكتشاف وتحديث SmartArt متاحان بدءًا من Aspose.Words 20.9 لـ Java وما بعده.

**س: هل تتعامل المكتبة بكفاءة مع مستندات كبيرة تحتوي على العديد من الأشكال؟**  
ج: نعم. استخدم `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` أو أعلى لتحسين الأداء في المستندات التي تحتوي على العديد من الأشكال.

---

**Last Updated:** 2026-02-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}