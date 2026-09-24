---
date: 2025-12-14
description: Aspose.Words for Java ile **görüntü şekli eklemeyi** öğrenin. Bu kılavuz,
  şekiller eklemeyi, metin kutusu şekilleri oluşturmayı, şekilleri tablolara yerleştirmeyi,
  şekil en‑boy oranını ayarlamayı ve açıklama şekilleri eklemeyi gösterir.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java'da Belge Şekillerini Kullanma
url: /tr/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile **görüntü şekli ekleme** nasıl yapılır

Bu kapsamlı öğreticide, Aspose.Words for Java kullanarak Word belgelerine **görüntü şekli** nesnelerini nasıl ekleyeceğinizi keşfedeceksiniz. Raporlar, pazarlama materyalleri veya etkileşimli formlar oluşturuyor olun, şekiller sayesinde çağrı balonları, düğmeler, metin kutuları, filigranlar ve hatta SmartArt ekleyebilirsiniz. Her adımı adım adım inceleyecek, belirli bir şekli neden kullanmanız gerektiğini açıklayacak ve çalıştırmaya hazır kod parçacıkları sunacağız.

## Hızlı Yanıtlar
- **Şekil eklemenin temel yolu nedir?** `DocumentBuilder.insertShape` kullanın veya bir `Shape` örneği oluşturup belge ağacına ekleyin.  
- **Bir görüntüyü şekil olarak ekleyebilir miyim?** Evet – `builder.insertImage` çağırın ve dönen `Shape`ı diğerleri gibi kullanın.  
- **Bir şeklin en‑boy oranını nasıl korursunuz?** İhtiyacınıza göre `shape.setAspectRatioLocked(true)` veya `false` ayarlayın.  
- **Şekilleri gruplayabilir miyim?** Kesinlikle – onları bir `GroupShape` içinde sarın ve grubu tek bir düğüm olarak ekleyin.  
- **SmartArt diyagramları Aspose.Words ile çalışır mı?** Evet, SmartArt şekillerini programlı olarak tespit edip güncelleyebilirsiniz.

## **Görüntü şekli** nedir?
*Görüntü şekli*, bir Word belgesi içinde raster veya vektör grafiklerini tutan görsel bir öğedir. Aspose.Words'ta bir görüntü, `Shape` nesnesiyle temsil edilir ve boyut, konum, döndürme ve kaydırma üzerinde tam kontrol sağlar.

## Belgelerinizde Şekilleri Neden Kullanmalısınız?
- **Görsel etki:** Şekiller, önemli bilgilere çeker.  
- **Etkileşim:** Düğmeler ve çağrı balonları URL'lere veya yer imlerine bağlanabilir.  
- **Düzen esnekliği:** Grafiklerin konumunu mutlak veya göreceli koordinatlarla hassas bir şekilde ayarlayın.  
- **Otomasyon:** Manuel düzenleme yapmadan karmaşık düzenler oluşturun.

## Önkoşullar
- Java Development Kit (JDK 8 ve üzeri)  
- Aspose.Words for Java kütüphanesi (resmi siteden indirin)  
- Java ve nesne‑yönelimli programlama hakkında temel bilgi  

You can download the library here: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## **Şekil ekleme** – GroupShape ekleme
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

## **Metin kutusu şekli** oluşturma
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

## **Şekil en‑boy oranını** ayarlama
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## **Şekli tabloya yerleştirme**
Bir şekli tablo hücresine yerleştirmek, rapor düzenleri için kullanışlı olabilir. Aşağıdaki örnek bir tablo oluşturur ve ardından tüm sayfayı kaplayan bir filigran‑stili şekli ekler.
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

## **Çağrı balonu şekli** ekleme
Bir çağrı balonu şekli, notları veya uyarıları vurgulamak için mükemmeldir. Yukarıdaki kod zaten bir `ACCENT_BORDER_CALLOUT_1` gösteriyor, ancak `ShapeType`ı tasarımınıza uygun herhangi bir çağrı balonu çeşidine değiştirebilirsiniz.

## SmartArt Şekilleriyle Çalışma

### SmartArt Şekillerini Algılama
SmartArt diyagramları programlı olarak tespit edilebilir, böylece gerektiğinde işleyebilir veya değiştirebilirsiniz.
```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt Çizimlerini Güncelleme
Algılandıktan sonra, SmartArt grafiklerini veri değişikliklerini yansıtacak şekilde yenileyebilirsiniz.
```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Yaygın Sorunlar ve İpuçları
- **Şekil görünmüyor:** `builder.insertNode` kullanarak şeklin hedef düğümden sonra eklendiğinden emin olun.  
- **Beklenmeyen döndürme:** Döndürmenin şeklin merkezine göre uygulandığını unutmayın; gerekirse `setLeft`/`setTop` ayarlayın.  
- **En‑boy oranı kilitli:** Varsayılan olarak, birçok şekil en‑boy oranını kilitler; serbestçe uzatmak için `setAspectRatioLocked(false)` çağırın.  
- **SmartArt algılaması başarısız:** SmartArt'ı destekleyen bir Aspose.Words sürümü (v24+) kullandığınızdan emin olun.  

## Sık Sorulan Sorular

**S: Aspose.Words for Java nedir?**  
A: Aspose.Words for Java, geliştiricilerin Word belgelerini programlı olarak oluşturmasına, değiştirmesine ve dönüştürmesine olanak tanıyan bir Java kütüphanesidir. Çeşitli formatlarda belgelerle çalışmak için geniş özellik ve araç seti sunar.

**S: Aspose.Words for Java nasıl indirilebilir?**  
A: Aspose.Words for Java'ı Aspose web sitesinden şu bağlantıyı izleyerek indirebilirsiniz: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**S: Belge şekilleri kullanmanın faydaları nelerdir?**  
A: Belge şekilleri, belgelere görsel öğeler ve etkileşim ekleyerek daha çekici ve bilgilendirici olmalarını sağlar. Şekillerle çağrı balonları, düğmeler, görüntüler, filigranlar ve daha fazlasını oluşturabilir, genel kullanıcı deneyimini artırabilirsiniz.

**S: Şekillerin görünümünü özelleştirebilir miyim?**  
A: Evet, şekillerin boyut, konum, döndürme ve dolgu rengi gibi özelliklerini ayarlayarak görünümünü özelleştirebilirsiniz. Aspose.Words for Java, şekil özelleştirme için kapsamlı seçenekler sunar.

**S: Aspose.Words for Java SmartArt ile uyumlu mu?**  
A: Evet, Aspose.Words for Java SmartArt şekillerini destekler ve belgelerinizde karmaşık diyagramlar ve grafiklerle çalışmanıza olanak tanır.

---

**Son Güncelleme:** 2025-12-14  
**Test Edilen:** Aspose.Words for Java 24.12 (en son)  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}