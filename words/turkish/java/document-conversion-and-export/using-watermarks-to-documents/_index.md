---
date: 2025-12-18
description: Aspose.Words for Java ile belgelere filigran eklemeyi öğrenin; görüntü
  filigranı örneği, filigran rengini değiştirme, filigran şeffaflığını ayarlama ve
  filigranı belgeden kaldırma dahil.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java ile Belgeler'e Filigran Ekleme
url: /tr/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java Kullanarak Belgelerde Filigran Ekleme

## Aspose.Words for Java'da Belgelerde Filigran Eklemeye Giriş

Bu öğreticide Aspose.Words for Java ile Word belgelerine **filigran eklemeyi** öğreneceksiniz. Filigranlar, bir dosyayı gizli, taslak veya onaylı olarak etiketlemenin hızlı bir yoludur ve metin‑tabanlı ya da görüntü‑tabanlı olabilir. Kütüphaneyi kurma, metin ve görüntü filigranları oluşturma, görünümünü özelleştirme (filigran rengini değiştirme ve filigran şeffaflığını ayarlama dahil) ve artık gerekmediğinde bir filigranı belgeden kaldırma adımlarını göstereceğiz.

## Hızlı Cevaplar
- **Filigran nedir?** Ana belge içeriğinin arkasında görünen yarı‑şeffaf bir kaplama (metin veya görüntü).  
- **Birden fazla filigran ekleyebilir miyim?** Evet – birkaç `Shape` nesnesi oluşturup her birini istediğiniz bölümlere ekleyin.  
- **Filigran rengini nasıl değiştiririm?** `TextWatermarkOptions` içindeki `Color` özelliğini ayarlayın.  
- **Görüntü filigranı örneği var mı?** Aşağıdaki “Görüntü Filigranları Ekleme” bölümüne bakın.  
- **Filigranı kaldırmak için lisans gerekir mi?** Üretim kullanımında geçerli bir Aspose.Words lisansı gereklidir.

## Aspose.Words for Java'ı Kurma

Belgelere filigran eklemeye başlamadan önce Aspose.Words for Java'ı kurmamız gerekir. Başlamak için aşağıdaki adımları izleyin:

1. Aspose.Words for Java'ı [buradan](https://releases.aspose.com/words/java/) indirin.  
2. Aspose.Words for Java kütüphanesini Java projenize ekleyin.  
3. Java kodunuzda gerekli sınıfları içe aktarın.

Artık kütüphane kurulduğuna göre, gerçek filigran oluşturma işlemine dalalım.

## Metin Filigranları Ekleme

Metin filigranları, belgelere metinsel bilgi eklemek istediğinizde yaygın bir tercihtir. Aspose.Words for Java kullanarak bir metin filigranı eklemenin yolu aşağıdadır:

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

**Neden önemli:** `setFontFamily`, `setFontSize` ve `setColor` ayarlarını değiştirerek **filigran rengini** markanıza uygun şekilde **değiştirebilir**, `setSemitransparent(true)` ise **filigran şeffaflığını** ince bir etki için **ayarlamanıza** olanak tanır.

## Görüntü Filigranları Ekleme

Metin filigranlarına ek olarak, belgelere görüntü filigranları da ekleyebilirsiniz. Aşağıda, bir PNG logo veya damga nasıl gömülür gösteren **görüntü filigranı örneği** yer almaktadır:

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

Bu bloğu farklı görüntüler veya konumlarla tekrarlayarak tek bir dosyaya **birden fazla filigran ekleyebilirsiniz**.

## Filigranları Özelleştirme

Filigranların görünümünü ve konumunu ayarlayarak özelleştirebilirsiniz. Metin filigranları için yazı tipini, boyutu, rengi ve yerleşimi değiştirebilirsiniz. Görüntü filigranları için ise önceki örneklerde gösterildiği gibi boyut, dönüş ve hizalamayı değiştirebilirsiniz.

## Filigranları Kaldırma

**Filigran içeren belge** içeriğini kaldırmanız gerekiyorsa, aşağıdaki kod tüm şekilleri dolaşır ve filigran olarak tanımlananları siler:

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

## Yaygın Kullanım Durumları ve İpuçları

- **Gizli taslaklar:** “CONFIDENTIAL” gibi yarı‑şeffaf bir metin filigranı uygulayın.  
- **Markalaşma:** Şirket logonuzu içeren bir görüntü filigranı kullanın.  
- **Bölüm‑özel filigranlar:** `doc.getSections()` üzerinden döngü yaparak sadece seçtiğiniz bölümlere filigran ekleyin.  
- **Performans ipucu:** Aynı filigranı birçok belgeye uygularken aynı `TextWatermarkOptions` örneğini yeniden kullanın.

## Sıkça Sorulan Sorular

### Metin filigranının yazı tipini nasıl değiştirebilirim?

Metin filigranının yazı tipini değiştirmek için `TextWatermarkOptions` içindeki `setFontFamily` özelliğini değiştirin. Örneğin:

```java
options.setFontFamily("Times New Roman");
```

### Tek bir belgeye birden fazla filigran ekleyebilir miyim?

Evet, farklı ayarlara sahip birden fazla `Shape` nesnesi oluşturarak ve bunları belgeye ekleyerek bir belgeye birden fazla filigran ekleyebilirsiniz.

### Bir filigranı döndürmek mümkün mü?

Evet, `Shape` nesnesindeki `setRotation` özelliğini ayarlayarak bir filigranı döndürebilirsiniz. Pozitif değerler filigranı saat yönünde, negatif değerler ise saat yönünün tersine döndürür.

### Bir filigranı yarı‑şeffaf nasıl yapabilirim?

Bir filigranı yarı‑şeffaf yapmak için `TextWatermarkOptions` içinde `setSemitransparent` özelliğini `true` olarak ayarlayın.

### Bir belgenin belirli bölümlerine filigran ekleyebilir miyim?

Evet, bölümler arasında döngü yaparak ve istediğiniz bölümlere filigran ekleyerek bir belgenin belirli bölümlerine filigran ekleyebilirsiniz.

---

**Son Güncelleme:** 2025-12-18  
**Test Edilen:** Aspose.Words for Java 24.12  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}