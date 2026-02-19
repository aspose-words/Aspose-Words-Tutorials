---
date: 2026-02-19
description: Aspose.Words for Java kullanarak filigranlı belge oluşturmayı ve profesyonel
  görünümlü belgeler için Java ile görüntü filigranı eklemeyi öğrenin.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java kullanarak filigranlı belge oluşturma
url: /tr/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

ords for Java 24.12 (latest)"

**Author:** Aspose -> "**Yazar:** Aspose"

Make sure markdown bold.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java kullanarak filigranlı belge oluşturma

Bu öğreticide **filigranlı belge oluşturma** işlemini Aspose.Words for Java API'si ile yapacaksınız. Filigranlar—metin ya da resim olsun—belgeyi gizli, taslak veya onaylı olarak etiketlemenize yardımcı olur ve programlı olarak herhangi bir Word belgesine uygulanabilir. Kütüphaneyi kurma, hem metin hem de resim filigranları ekleme, görünümünü özelleştirme ve artık gerekmediğinde kaldırma adımlarını birlikte inceleyeceğiz.

## Hızlı Yanıtlar
- **Bir filigran ne işe yarar?** Her sayfaya metin ya da resim ekleyerek durum veya marka bilgisi verir.  
- **Java'da filigran ekleyen kütüphane hangisidir?** Aspose.Words for Java yerleşik filigran desteği sağlar.  
- **Resim filigranı ekleyebilir miyim?** Evet—`Shape` sınıfını ve `add image watermark java` yaklaşımını kullanın.  
- **Filigran yarı saydam mı?** Metin filigranları için `setSemitransparent` ile opaklığı kontrol edebilirsiniz.  
- **Lisans gerekir mi?** Test için ücretsiz deneme çalışır; üretim için ticari lisans gereklidir.

## Filigran nedir ve neden kullanılır?

Filigran, bir belgenin her sayfasına eklenen hafif bir kaplamadır—metinsel ya da grafiksel. Genellikle **gizlilik**, **taslak durumu** veya **marka** göstermek için kullanılır ve temel içeriği değiştirmez. Filigranları programlı olarak eklemek, büyük dosya gruplarında tutarlılık sağlar ve manuel düzenlemeye göre zaman tasarrufu sağlar.

## Aspose.Words for Java Kurulumu

Filigran eklemeye başlamadan önce kütüphanenin projenizde hazır olduğundan emin olun:

1. Aspose.Words for Java'ı [buradan](https://releases.aspose.com/words/java/) indirin.  
2. İndirilen JAR'ı (veya Maven/Gradle bağımlılığını) projenizin sınıf yoluna ekleyin.  
3. Java kaynak dosyanıza gerekli sınıfları içe aktarın:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

Kütüphane kurulduğuna göre, gerçek filigran koduna geçelim.

## Metin filigranı ekleme

Metin filigranları, belgeyi “CONFIDENTIAL” veya “DRAFT” gibi etiketlemek için idealdir. Aşağıdaki kod parçacığı, `TextWatermarkOptions` kullanarak **filigranlı belge oluşturma** işlemini gösterir.

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

### Metin filigranını özelleştirme
- **Yazı tipi ailesi ve boyutu** – `setFontFamily` ve `setFontSize` değerlerini değiştirin.  
- **Renk** – herhangi bir `java.awt.Color` kullanın.  
- **Düzen** – `HORIZONTAL`, `DIAGONAL` vb. seçin.  
- **Şeffaflık** – daha hafif bir görünüm için `setSemitransparent(true)` ayarlayın.

## Görüntü filigranı ekleme (add image watermark java)

Görüntü filigranları, logo veya özel grafikler için mükemmeldir. Aşağıdaki **add image watermark java** örneği, bir PNG dosyasını her sayfanın ortasına ekler.

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

### Görüntü filigranları için ipuçları
- **Yeniden boyutlandırma** – sayfaya sığdırmak için `setWidth` / `setHeight` kullanın.  
- **Pozisyon** – `RelativeHorizontalPosition` / `RelativeVerticalPosition` kullanarak ortalanabilir veya herhangi bir kenara hizalanabilir.  
- **Şeffaflık** – yüklemeden önce görüntünün alfa kanalını ayarlayarak uygulanabilir.

## Filigranları kaldırma

Bir belge artık filigran gerektirmiyorsa, programlı olarak silebilirsiniz. Aşağıdaki kod, tüm şekilleri dolaşır ve adında “Watermark” geçenleri kaldırır.

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

## Yaygın hatalar ve sorun giderme

- **Kaydetme sonrası filigran eksik** – filigranı ayarladıktan sonra `doc.save()` çağırdığınızdan emin olun.  
- **Görüntü görünmüyor** – görüntü yolunun doğru olduğunu ve dosyanın desteklenen bir formatta (PNG, JPEG, BMP) olduğunu kontrol edin.  
- **Şeffaflık uygulanmadı** – `setSemitransparent(true)` yalnızca metin filigranları için çalışır; görüntüler için PNG'nin alfa kanalını düzenleyin.  
- **Birden fazla bölüm** – belgenizde birden fazla bölüm varsa, filigranı her bölümün gövdesine ekleyin veya global olarak uygulamak için `doc.getWatermark().setText(...)` kullanın.

## Sıkça Sorulan Sorular

**S: Metin filigranının yazı tipini nasıl değiştirebilirim?**  
C: `TextWatermarkOptions` içinde `setFontFamily` özelliğini değiştirin, örn. `options.setFontFamily("Times New Roman");`.

**S: Tek bir belgeye birden fazla filigran ekleyebilir miyim?**  
C: Evet. Birden fazla `Shape` nesnesi (görüntüler için) oluşturabilir veya her filigran için farklı seçeneklerle `doc.getWatermark().setText(...)` çağırabilirsiniz.

**S: Filigranı döndürebilir miyim?**  
C: Görüntü filigranları için `Shape` nesnesinde `watermark.setRotation(angle)` ile döndürme yapın. Metin filigranları için `setLayout` özelliğini (örn. `WatermarkLayout.DIAGONAL`) kullanın.

**S: Filigranı yarı saydam nasıl yaparım?**  
C: `TextWatermarkOptions` içinde `options.setSemitransparent(true)` ayarlayın. Görüntüler için yüklemeden önce opaklığı ayarlayın.

**S: Belgenin belirli bölümlerine filigran ekleyebilir miyim?**  
C: Evet. `doc.getSections()` üzerinden döngü kurarak istediğiniz bölümlere sadece filigran ekleyin.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Son Güncelleme:** 2026-02-19  
**Test Edilen:** Aspose.Words for Java 24.12 (latest)  
**Yazar:** Aspose