---
date: 2026-02-16
description: Aspose.Words for Java kullanarak metin kutusu oluşturmayı, filigran kelime
  eklemeyi, birden fazla şekli gruplamayı, şekil en‑boy oranını ayarlamayı ve şekli
  bir tablo hücresine yerleştirmeyi öğrenin.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java'da Metin Kutusu Oluşturma ve Belge Şekillerini Kullanma
url: /tr/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java’da Belge Şekillerinin Kullanımı

## Aspose.Words for Java’da Belge Şekillerinin Kullanımına Giriş

Bu kapsamlı rehberde, **metin kutusu oluşturma** nesnelerini ve Aspose.Words for Java ile diğer güçlü şekilleri nasıl oluşturacağınızı öğreneceksiniz. Şekiller, Word belgelerinizi açıklama balonları, düğmeler, filigranlar, SmartArt ve daha fazlası ile zenginleştirmenizi sağlar—belgeleri görsel olarak çekici ve etkileşimli hâle getirir. Basit bir metin kutusu eklemekten, birden fazla şekli gruplamaya, en boy oranlarını ayarlamaya ve şekilleri tablo hücrelerine yerleştirmeye kadar gerçek dünya örnekleri üzerinden ilerleyeceğiz.

## Hızlı Yanıtlar
- **Metin kutusu eklemenin temel yolu nedir?** `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)` kullanın.
- **Şekilleri bir arada gruplayabilir miyim?** Evet – bir `GroupShape` oluşturun ve alt şekilleri ekleyin.
- **Bir şeklin en boy oranını nasıl kilitleyip kilidini açarım?** `shape.setAspectRatioLocked(true/false)` çağırın.
- **Şekil ile bir filigran eklemek mümkün mü?** Kesinlikle – `TEXT_PLAIN_TEXT` tipinde bir `Shape` ekleyin ve doldurma/çizgi ayarlarını yapın.
- **SmartArt diyagramları Aspose.Words ile çalışıyor mu?** Evet – `shape.hasSmartArt()` ile tespit edin ve `shape.updateSmartArtDrawing()` ile güncelleyin.

## Metin kutusu nedir ve neden metin kutusu şekilleri oluşturmalıyız?

Metin kutusu, biçimlendirilmiş metin, resim veya diğer şekilleri tutabilen bir kapsayıcıdır. Otomasyonunuzda **metin kutusu oluşturma** kullanmak, sayfa üzerinde yüzen içerik yerleştirmenizi sağlar; açıklamalar, balonlar veya dekoratif öğeler için mükemmeldir ve ana belge akışını etkilemez.

## Şekil nasıl eklenir

Kodlamaya geçmeden önce, projenizde Aspose.Words for Java’nın referans edildiğinden emin olun. Henüz eklemediyseniz, resmi siteden kütüphaneyi indirin:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Belgelere Şekil Ekleme

## Birden fazla şekli nasıl gruplayabilirsiniz

`GroupShape`, birden fazla ayrı şekli tek bir birim olarak ele almanızı sağlar—bunları birlikte taşıma veya döndürme işlemleri için kullanışlıdır.

### GroupShape Ekleme

Aşağıda bir grup oluşturan, iki farklı şekil ekleyen ve grubu belgeye yerleştiren tam bir örnek bulunmaktadır.

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

## Metin kutusu (create text box) nasıl oluşturulur

### Metin Kutusu Şekli Ekleme

`insertShape` yöntemi, bir metin kutusu eklemeyi oldukça basitleştirir. Aşağıdaki örnek, bir metin kutusunu konumlandırma ve döndürme için iki farklı yolu gösterir.

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

## Şeklin en boy oranı nasıl ayarlanır

### En Boy Oranı Yönetimi

Bazen bir şeklin orijinal oranlarını korumadan uzamasına ihtiyaç duyabilirsiniz. Aşağıdaki kod parçacığı, bir resim şeklinin en boy oranının kilidini açmayı gösterir.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Şekil bir tablo hücresine nasıl yerleştirilir

### Şekli Bir Tablo Hücresine Yerleştirme

Aşağıda adım adım bir tablo oluşturup, sayfaya göre konumlandırılmış bir filigran şekli ekleyen ve aynı zamanda bir hücre içine de yerleştirilebilen bir örnek yer almaktadır.

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

## SmartArt Şekilleri ile Çalışma

### SmartArt Şekillerini Tespit Etme

`hasSmartArt()` yöntemiyle bir belgede SmartArt nesnelerini programlı olarak bulabilirsiniz.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt Çizimlerini Güncelleme

SmartArt şekillerini bulduktan sonra, `updateSmartArtDrawing()` ile iç çizim verilerini yenileyebilirsiniz.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Sonuç

Bu rehberde, **metin kutusu oluşturma** nesnelerini, birden fazla şekli gruplamayı, en boy oranlarını ayarlamayı, şekilleri tablo hücrelerine yerleştirmeyi, filigran eklemeyi ve Aspose.Words for Java ile SmartArt diyagramlarıyla çalışmayı ele aldık. Bu teknikler, programlı olarak zengin biçimlendirilmiş ve etkileşimli Word belgeleri oluşturmanızı sağlar.

## SSS

### Aspose.Words for Java nedir?

Aspose.Words for Java, geliştiricilerin Word belgelerini programlı olarak oluşturmasına, değiştirmesine ve dönüştürmesine olanak tanıyan bir Java kütüphanesidir. Çeşitli formatlarda belgeyle çalışmak için geniş bir özellik ve araç yelpazesi sunar.

### Aspose.Words for Java nasıl indirilir?

Aspose.Words for Java’yı Aspose web sitesinden şu bağlantıyı izleyerek indirebilirsiniz: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Belge şekilleri kullanmanın faydaları nelerdir?

Belge şekilleri, belgelere görsel öğeler ve etkileşim ekleyerek daha çekici ve bilgilendirici hâle getirir. Şekillerle açıklama balonları, düğmeler, resimler, filigranlar ve daha fazlasını oluşturabilir, genel kullanıcı deneyimini artırabilirsiniz.

### Şekillerin görünümü özelleştirilebilir mi?

Evet, şekillerin boyut, konum, döndürme ve dolgu rengi gibi özelliklerini ayarlayarak görünümünü özelleştirebilirsiniz. Aspose.Words for Java, şekil özelleştirmesi için kapsamlı seçenekler sunar.

### Aspose.Words for Java SmartArt ile uyumlu mu?

Evet, Aspose.Words for Java SmartArt şekillerini destekler; böylece belgelerinizde karmaşık diyagram ve grafiklerle çalışabilirsiniz.

## Sıkça Sorulan Sorular

**S: Metin kutusunu aynı şekil içinde bir resimle birleştirebilir miyim?**  
C: Evet. Şekli oluşturduktan sonra `builder.insertImage()` ile metin kutusu şekline bir resim ekleyin ve düzenini gerektiği gibi ayarlayın.

**S: Filigranın tüm belge içeriğinin arkasında görünmesini nasıl sağlarım?**  
C: Şeklin `WrapType` özelliğini `NONE` olarak ayarlayın ve `RelativeHorizontalPosition` ile `RelativeVerticalPosition` değerlerini `PAGE` olarak belirleyin. Bu, filigranı ana akışın arkasına konumlandırır.

**S: Word’de gruplanmış bir şekli animasyonlu hale getirmek mümkün mü?**  
C: Aspose.Words şekil oluşturma ve gruplama yapabilir, ancak animasyon özellikleri Word’ün UI yeteneklerine bağlı olduğundan desteklenmez.

**S: SmartArt desteği için hangi Aspose.Words sürümü gerekir?**  
C: SmartArt tespiti ve güncellemesi, Aspose.Words 20.9 for Java ve sonraki sürümlerinde mevcuttur.

**S: Kütüphane çok sayıda şekil içeren büyük belgeleri verimli bir şekilde işleyebilir mi?**  
C: Evet. `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` veya daha yüksek bir sürüm kullanarak çok sayıda şekil içeren belgelerde performansı artırabilirsiniz.

---

**Son Güncelleme:** 2026-02-16  
**Test Edilen Versiyon:** Aspose.Words for Java 24.12  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}