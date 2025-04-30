---
"description": "Aspose.Words for Java'da belgelere filigran eklemeyi öğrenin. Profesyonel görünümlü belgeler için metin ve resim filigranlarını özelleştirin."
"linktitle": "Belgelerde Filigran Kullanımı"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Java için Aspose.Words'de Belgelere Filigran Kullanma"
"url": "/tr/java/document-conversion-and-export/using-watermarks-to-documents/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Belgelere Filigran Kullanma


## Aspose.Words for Java'da Belgelere Filigran Eklemeye Giriş

Bu eğitimde, Aspose.Words for Java API'sini kullanarak belgelere filigran eklemeyi inceleyeceğiz. Filigranlar, belgelerin durumunu, gizliliğini veya diğer ilgili bilgileri belirtmek için belgeleri metin veya grafiklerle etiketlemenin kullanışlı bir yoludur. Bu kılavuzda hem metin hem de resim filigranlarını ele alacağız.

## Java için Aspose.Words Kurulumu

Belgelere filigran eklemeye başlamadan önce, Java için Aspose.Words'ü kurmamız gerekiyor. Başlamak için şu adımları izleyin:

1. Java için Aspose.Words'ü şuradan indirin: [Burada](https://releases.aspose.com/words/java/).
2. Java projenize Aspose.Words for Java kütüphanesini ekleyin.
3. Gerekli sınıfları Java kodunuza aktarın.

Artık kütüphaneyi kurduğumuza göre filigran eklemeye geçebiliriz.

## Metin Filigranları Ekleme

Belgelerinize metinsel bilgi eklemek istediğinizde metin filigranları yaygın bir tercihtir. Java için Aspose.Words kullanarak bir metin filigranı nasıl ekleyebileceğiniz aşağıda açıklanmıştır:

```java
// Bir Belge örneği oluşturun
Document doc = new Document("Document.docx");

// TextWatermarkOptions'ı tanımlayın
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Filigran metnini ve seçeneklerini ayarlayın
doc.getWatermark().setText("Test", options);

// Belgeyi filigranla birlikte kaydedin
doc.save("DocumentWithWatermark.docx");
```

## Görüntü Filigranları Ekleme

Belgelerinize metin filigranlarına ek olarak resim filigranları da ekleyebilirsiniz. Resim filigranı ekleme yöntemi şöyledir:

```java
// Bir Belge örneği oluşturun
Document doc = new Document("Document.docx");

// Filigran için görseli yükleyin
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Filigran boyutunu ve konumunu ayarlayın
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Belgeye filigran ekleyin
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Belgeyi filigranla birlikte kaydedin
doc.save("DocumentWithImageWatermark.docx");
```

## Filigranları Özelleştirme

Filigranları görünümlerini ve konumlarını ayarlayarak özelleştirebilirsiniz. Metin filigranları için yazı tipini, boyutunu, rengini ve düzenini değiştirebilirsiniz. Resim filigranları için boyutlarını ve konumlarını önceki örneklerde gösterildiği gibi değiştirebilirsiniz.

## Filigranları Kaldırma

Bir belgeden filigranları kaldırmak için aşağıdaki kodu kullanabilirsiniz:

```java
// Bir Belge örneği oluşturun
Document doc = new Document("DocumentWithWatermark.docx");

// Filigranı kaldırın
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Belgeyi filigran olmadan kaydet
doc.save("DocumentWithoutWatermark.docx");
```


## Çözüm

Bu eğitimde, Java için Aspose.Words kullanarak belgelere filigran eklemeyi öğrendik. Metin veya resim filigranları eklemeniz gerekip gerekmediğine bakılmaksızın, Aspose.Words bunları etkili bir şekilde özelleştirmek ve yönetmek için araçlar sunar. Ayrıca, artık ihtiyaç duyulmadığında filigranları kaldırabilir, belgelerinizin temiz ve profesyonel olmasını sağlayabilirsiniz.

## SSS

### Bir metin filigranının yazı tipini nasıl değiştirebilirim?

Bir metin filigranının yazı tipini değiştirmek için, `setFontFamily` mülk `TextWatermarkOptions`. Örneğin:

```java
options.setFontFamily("Times New Roman");
```

### Tek bir belgeye birden fazla filigran ekleyebilir miyim?

Evet, birden fazla filigran oluşturarak bir belgeye birden fazla filigran ekleyebilirsiniz. `Shape` Farklı ayarlara sahip nesneleri seçip belgeye eklemek.

### Filigranı döndürmek mümkün müdür?

Evet, filigranı döndürebilirsiniz. `setRotation` mülk `Shape` nesne. Pozitif değerler filigranı saat yönünde döndürür ve negatif değerler saat yönünün tersine döndürür.

### Filigranı yarı saydam nasıl yapabilirim?

Bir filigranı yarı saydam yapmak için, `setSemitransparent` mülk `true` içinde `TextWatermarkOptions`.

### Belgenin belirli bölümlerine filigran ekleyebilir miyim?

Evet, bölümler arasında gezinerek ve filigranı istediğiniz bölümlere ekleyerek belgenin belirli bölümlerine filigran ekleyebilirsiniz.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}