---
"description": "Aspose.Words for Java'da Belge Şekillerinin Gücünü Açın. Adım Adım Örneklerle Görsel Olarak İlgi Çekici Belgeler Oluşturmayı Öğrenin."
"linktitle": "Belge Şekillerini Kullanma"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Java için Aspose.Words'de Belge Şekillerini Kullanma"
"url": "/tr/java/document-conversion-and-export/using-document-shapes/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Belge Şekillerini Kullanma


## Java için Aspose.Words'de Belge Şekillerinin Kullanımına Giriş

Bu kapsamlı kılavuzda, Java için Aspose.Words'deki belge şekillerinin dünyasına dalacağız. Şekiller, görsel olarak çekici ve etkileşimli belgeler oluşturma konusunda olmazsa olmaz unsurlardır. Açıklamalar, düğmeler, resimler veya filigranlar eklemeniz gerekip gerekmediğine bakılmaksızın, Java için Aspose.Words bunu verimli bir şekilde yapmanız için gereken araçları sağlar. Kaynak kod örnekleriyle bu şekillerin nasıl kullanılacağını adım adım inceleyelim.

## Belge Şekillerine Başlarken

Koda geçmeden önce ortamımızı ayarlayalım. Projenize Aspose.Words for Java'nın entegre olduğundan emin olun. Eğer henüz entegre etmediyseniz, Aspose web sitesinden indirebilirsiniz [Java için Aspose.Words'ü indirin](https://releases.aspose.com/words/java/)

## Belgelere Şekil Ekleme

### Bir GroupShape Ekleme

A `GroupShape` birden fazla şekli bir arada gruplamanıza olanak tanır. İşte bir şekli nasıl oluşturabileceğiniz ve ekleyebileceğiniz `GroupShape`:

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

### Bir Metin Kutusu Şekli Ekleme

Bir metin kutusu şekli eklemek için şunu kullanabilirsiniz: `insertShape` Aşağıdaki örnekte gösterildiği gibi bir yöntem:

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

## Şekil Özelliklerini Düzenleme

### En Boy Oranını Yönetme

Bir şeklin en boy oranının kilitli olup olmadığını kontrol edebilirsiniz. Bir şeklin en boy oranının kilidini açma yöntemi şöyledir:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Bir Tablo Hücresine Şekil Yerleştirme

Bir tablo hücresinin içine bir şekil yerleştirmeniz gerekiyorsa, bunu aşağıdaki kodla yapabilirsiniz:

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
watermark.isLayoutInCell(true); // Şekil bir hücreye yerleştirilecekse, onu tablo hücresinin dışında görüntüle.
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

## SmartArt Şekilleriyle Çalışma

### SmartArt Şekillerini Algılama

Aşağıdaki kodu kullanarak bir belgedeki SmartArt şekillerini tespit edebilirsiniz:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt Çizimlerini Güncelleme

Bir belgedeki SmartArt çizimlerini güncellemek için aşağıdaki kodu kullanın:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Çözüm

Bu kılavuzda, Java için Aspose.Words'deki belge şekillerinin dünyasını keşfettik. Belgelerinize çeşitli şekiller eklemeyi, özelliklerini düzenlemeyi ve SmartArt şekilleriyle çalışmayı öğrendiniz. Bu bilgiyle, görsel olarak çekici ve etkileşimli belgeleri kolaylıkla oluşturabilirsiniz.

## SSS

### Java için Aspose.Words nedir?

Aspose.Words for Java, geliştiricilerin Word belgelerini programatik olarak oluşturmasına, değiştirmesine ve dönüştürmesine olanak tanıyan bir Java kütüphanesidir. Çeşitli formatlardaki belgelerle çalışmak için geniş bir yelpazede özellikler ve araçlar sunar.

### Aspose.Words for Java'yı nasıl indirebilirim?

Aspose.Words for Java'yı Aspose web sitesinden şu bağlantıyı takip ederek indirebilirsiniz: [Java için Aspose.Words'ü indirin](https://releases.aspose.com/words/java/)

### Belge şekillerini kullanmanın faydaları nelerdir?

Belge şekilleri belgelerinize görsel öğeler ve etkileşim ekleyerek onları daha ilgi çekici ve bilgilendirici hale getirir. Şekillerle açıklamalar, düğmeler, resimler, filigranlar ve daha fazlasını oluşturarak genel kullanıcı deneyimini geliştirebilirsiniz.

### Şekillerin görünümünü özelleştirebilir miyim?

Evet, şekillerin boyut, konum, dönüş ve dolgu rengi gibi özelliklerini ayarlayarak görünümlerini özelleştirebilirsiniz. Java için Aspose.Words, şekil özelleştirme için kapsamlı seçenekler sunar.

### Aspose.Words for Java SmartArt ile uyumlu mudur?

Evet, Aspose.Words for Java SmartArt şekillerini destekler ve belgelerinizde karmaşık diyagramlar ve grafiklerle çalışmanıza olanak tanır.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}