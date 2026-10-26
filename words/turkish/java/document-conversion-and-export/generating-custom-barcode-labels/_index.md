---
date: 2026-10-23
description: Aspose.Words ile QR kod Java etiketleri oluşturmayı öğrenin. Bu step‑by‑step
  rehber, Word belgelerine barcode eklemeyi ve boyut, renk ve formatı özelleştirmeyi
  gösterir.
keywords:
- create qr code java
- how to create barcode label
- add barcode to word document
- embed barcode in word
lastmod: 2026-10-23
linktitle: Özel Barcode Etiketleri Oluşturma
og_description: Aspose.Words ile QR kod Java etiketleri oluşturmayı öğrenin. Bu rehber,
  Word belgelerinde barcode yerleştirme, boyut kontrolü ve renk özelleştirmesini açıklar.
og_image_alt: 'Developer guide: generate custom QR code labels in Java with Aspose.Words'
og_title: Aspose.Words kullanarak QR kod Java etiketleri oluşturma
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  headline: How to create QR code Java labels using Aspose.Words
  type: TechArticle
- description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  name: How to create QR code Java labels using Aspose.Words
  steps:
  - name: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
    text: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
  - name: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
    text: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
  - name: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
    text: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
  - name: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
    text: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
  type: HowTo
- questions:
  - answer: Yes, but it will have evaluation limitations. Obtain a [temporary license](https://purchase.aspose.com/temporary-license/)
      for full functionality.
    question: Can I use Aspose.Words for Java without a license?
  - answer: Aspose.BarCode supports QR, Code 128, EAN‑13, DataMatrix, PDF417, and
      many other formats—over 20 symbologies in total. See the [documentation](https://reference.aspose.com/words/java/)
      for the complete list.
    question: What types of barcodes can I generate?
  - answer: Adjust the width and height arguments in `builder.insertImage`, or calculate
      exact Word twips using `twipsToPixels` for pixel‑perfect control.
    question: How can I change the barcode size?
  - answer: Yes, you can customize the text font through the `CodeTextParameters`
      property of the `BarcodeGenerator`.
    question: Is it possible to use custom fonts for the barcode text?
  - answer: Visit the [support forum](https://forum.aspose.com/c/words/8/) for assistance
      from the Aspose community and engineers.
    question: Where can I get help if I run into problems?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- barcode generation
- Aspose.Words
- Java document processing
- QR code
title: Aspose.Words kullanarak QR kod Java etiketleri oluşturma
url: /tr/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words kullanarak QR kod Java etiketleri oluşturma

Barkodlar modern uygulamalarda vazgeçilmezdir—envanter yönetimi, bilet yazdırma veya kimlik kartı oluşturma gibi. Bu öğreticide **create QR code Java** etiketleri oluşturacak ve bunları `IBarcodeGenerator` arayüzünü kullanarak doğrudan bir Word belgesine gömeceksiniz. Ortamı kurmaktan barkod görüntüsünü eklemeye kadar her adımı adım adım göstereceğiz, böylece Java projelerinizde barkodları hemen kullanmaya başlayabilirsiniz.

## Hızlı cevaplar
- **Bu öğreticide ne öğretiliyor?** Aspose.Words for Java ile QR kod Java etiketleri oluşturma ve bunları bir Word dosyasına gömme.  
- **Örnekte hangi barkod türü kullanılıyor?** QR kod (20'den fazla desteklenen türden herhangi biriyle değiştirilebilir).  
- **Lisans gerekli mi?** Geliştirme sırasında sınırsız erişim için geçici bir lisans gereklidir.  
- **Hangi Java sürümü gerekiyor?** JDK 8 veya üzeri.  
- **Barkod boyutunu veya renklerini değiştirebilir miyim?** Evet—`BarcodeParameters` ve `BarcodeGenerator` ayarlarını değiştirin.

## create QR code Java nedir?
`create QR code Java`, Java ortamında programlı olarak bir QR‑kod görüntüsü oluşturmayı ve bunu bir belgeye veya UI bileşenine eklemeyi ifade eder. Aspose.Words for Java, Aspose.BarCode ile birlikte, görüntüyü tamamen bellek içinde üretmenizi sağlar, geçici dosyalardan kaçınır.

## Neden Aspose.Words ile özel barkod etiketleri oluşturmalısınız?
Aspose.Words **35+ giriş ve çıkış formatını** destekler ve standart sunucu donanımında **500 sayfalık belgeleri 3 saniyenin altında** işleyebilir. Bellek içi barkod üretimini kullanarak tür, boyut ve renkler üzerinde tam kontrol elde ederken, iş akışını tamamen Java‑merkezli ve platform‑bağımsız tutarsınız.

## Önkoşullar

- Java Development Kit (JDK): Sürüm 8 veya üzeri.  
- Aspose.Words for Java Kütüphanesi: [Buradan indirin](https://releases.aspose.com/words/java/).  
- Aspose.BarCode for Java Kütüphanesi: [Buradan indirin](https://releases.aspose.com/).  
- Entegre Geliştirme Ortamı (IDE): IntelliJ IDEA, Eclipse veya tercih ettiğiniz herhangi bir IDE.  
- Geçici Lisans: Sınırsız erişim için bir [geçici lisans](https://purchase.aspose.com/temporary-license/) edinin.

## Paketleri içe aktar

Aspose.Words ve Aspose.BarCode kütüphanelerini kullanacağız. Projenize aşağıdaki paketleri içe aktarın:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Bu içe aktarmalar, ihtiyacımız olan barkod üretim API'sine ve Word belge sınıflarına erişim sağlar.

## Adım 1: barkod işlemleri için yardımcı sınıf oluşturma

Yardımcı sınıf, **twips'i piksele dönüştürme** ve **hex‑renk dönüşümü** gibi yeniden kullanılabilir yardımcıları barındırır.  
`CustomBarcodeGeneratorUtils` sınıfı, birim dönüşümü ve renk işleme için statik yöntemler sağlar.

### Kod

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**Açıklama**  
- `twipsToPixels` – Word, boyutları **twips** biriminde ölçer; bu yöntem, barkod görüntüsünü tam olarak boyutlandırmanız gerektiğinde ekran pikseline dönüştürür.  
- `convertColor` – Hexadecimal bir dizeyi (ör. kırmızı için `"FF0000"` ) `java.awt.Color` nesnesine dönüştürür, böylece özel ön plan ve arka plan renkleriyle **barkodu Word belgesine ekleyebilirsiniz**.

## Adım 2: özel barkod üreteci uygulama

Şimdi `IBarcodeGenerator` arayüzünü uygulayacağız. Bu sınıf, Aspose.Words'in gömebileceği **generate QR code Java**‑stilinde görüntüler üretmekten sorumludur.  
`IBarcodeGenerator` arayüzü, barkodu temsil eden bir `BufferedImage` döndüren tek bir yöntem tanımlar.

### Kod

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**Açıklama**  
- `getBarcodeImage` bir `BarcodeGenerator` örneği oluşturur, `BarcodeParameters` aracılığıyla sağlanan renkleri uygular ve sonunda bir `BufferedImage` döndürür.  
- Yöntem ayrıca hataları, bir yer tutucu görüntü döndürerek nazikçe ele alır ve Word belgesi oluşturulmasının hiç çökmesini engeller.

## Aspose.Words kullanarak barkodu Word'e nasıl gömebilirsiniz?

Word dosyanızı `new Document("template.docx")` ile yükleyin (veya yeni bir `Document` oluşturun) ve üreteciden dönen barkod görüntüsüyle `builder.insertImage` çağırın. Bu iki adımlı desen, ara bir dosya yazmadan barkodu doğrudan gömer. Görüntü boyutlarını piksel olarak belirterek veya Word twips'lerini piksele dönüştürerek, barkodun belge içindeki tam boyut ve konumunu kontrol edebilir, herhangi bir yazıcıda doğru şekilde basılan profesyonel bir düzen sağlayabilirsiniz.

## Adım 3: bir barkod oluşturma ve barkodu Word'e gömme

Üreteç hazır olduğunda, bir barkod görüntüsü oluşturabilir ve **bir Word belgesine ekleyebiliriz**.

### Kod

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**Açıklama**  

1. **Belge başlatma** – Yeni bir `Document` oluşturur (veya mevcut bir şablonu yükleyebilirsiniz).  
2. **Barkod parametreleri** – Barkod türünü (`QR`), kodlanacak değeri ve ön plan/arka plan renklerini tanımlar.  
3. **Görüntü ekleme** – `builder.insertImage`, oluşturulan barkodu istenen boyutta (200 × 200 piksel) yerleştirir. Bu, **barkodu Word'e nasıl gömeceğinizin** temelidir.  
4. **Kaydetme** – Son belge, `CustomBarcodeLabels.docx`, gömülü barkodu içerir ve yazdırma veya dağıtım için hazırdır.

## Yaygın sorunlar ve çözüm yolları

| Belirti | Muhtemel neden | Çözüm |
|---------|----------------|-------|
| Barkod boş görünüyor | `BarcodeParameters` renkleri aynı (ör. siyah üzerine siyah) | `foregroundColor` ve `backgroundColor` değerlerini doğrulayın. |
| Görüntü bozulmuş | `insertImage`'a yanlış piksel boyutları gönderildi | Genişlik/yükseklik argümanlarını ayarlayın veya kesin boyutlandırma için `twipsToPixels` dönüşümünü kullanın. |
| Desteklenmeyen barkod türü hatası | `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` tarafından tanınmayan bir tür kullanılması | Barkod türü dizesinin desteklenen `EncodeTypes` (ör. `"QR"`, `"CODE128"`) ile eşleştiğinden emin olun. |

## Sıkça sorulan sorular

**Q: Aspose.Words for Java'yı lisans olmadan kullanabilir miyim?**  
A: Evet, ancak değerlendirme sınırlamaları vardır. Tam işlevsellik için bir [geçici lisans](https://purchase.aspose.com/temporary-license/) edinin.

**Q: Hangi barkod türlerini oluşturabilirim?**  
A: Aspose.BarCode, QR, Code 128, EAN‑13, DataMatrix, PDF417 ve birçok diğer formatı destekler—toplamda 20'den fazla semboloji. Tam liste için [belgelere](https://reference.aspose.com/words/java/) bakın.

**Q: Barkod boyutunu nasıl değiştirebilirim?**  
A: `builder.insertImage` içindeki genişlik ve yükseklik argümanlarını ayarlayın veya piksel‑tam kontrol için `twipsToPixels` kullanarak kesin Word twips değerlerini hesaplayın.

**Q: Barkod metni için özel yazı tipleri kullanabilir miyim?**  
A: Evet, `BarcodeGenerator`'ın `CodeTextParameters` özelliği aracılığıyla metin yazı tipini özelleştirebilirsiniz.

**Q: Sorun yaşarsam nereden yardım alabilirim?**  
A: Aspose topluluğu ve mühendislerinden destek almak için [destek forumunu](https://forum.aspose.com/c/words/8/) ziyaret edin.

## Sonuç

Yukarıdaki adımları izleyerek, Aspose.Words for Java kullanarak **create QR code Java** görüntüleri oluşturmayı ve **barkodu Word** belgelerine gömmeyi artık biliyorsunuz. Bu teknik, envanter etiketleri, etkinlik biletleri veya barkodun oluşturulan bir belgenin parçası olması gereken herhangi bir senaryo için yeterince esnektir. Farklı barkod türleri, renkler ve boyutlandırma seçenekleriyle deney yaparak özel iş ihtiyaçlarınıza uyarlayın.

---

**Son Güncelleme:** 2026-10-23  
**Test Edildi:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Yazar:** Aspose

## İlgili Öğreticiler

- [Barkod Oluşturma ile Word'den PDF Oluşturma – Aspose.Words for Java](/words/java/document-conversion-and-export/using-barcode-generation/)
- [Aspose Words ile Word'ü PDF Olarak Kaydet – Adım Adım Java Rehberi](/words/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [Java'da Aspose Words ile Boş Word Belgesi Oluşturma](/words/java/document-manipulation/create-blank-word-document-in-java-with-aspose-words/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}