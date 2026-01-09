---
date: 2026-01-09
description: Aspose.Words for Java ile belgeleri birleştirirken biçimlendirmeyi koruma,
  başlık ve altbilgileri bağlama ve daha fazlasını öğrenin.
linktitle: Joining and Appending Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java Kullanarak Belgeleri Birleştirme
url: /tr/java/document-manipulation/joining-and-appending-documents/
weight: 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile Belgeleri Birleştirme

Word dosyalarını programlı olarak birleştirmek baş ağrısı olabilir—özellikle stilleri, sayfa numaralarını ve üstbilgi/altbilgileri aynı tutmanız gerektiğinde. Bu öğreticide Aspose.Words for Java kütüphanesini kullanarak **belgeleri nasıl birleştireceğinizi** adım adım keşfedeceksiniz. Basit eklemeler, gelişmiş içe aktarma seçenekleri, farklı sayfa düzenlerinin ele alınması ve gerçek dünya senaryolarında **biçimlendirmeyi koruyan birleştirme** sonuçları elde etmek için gereken ipuçlarını ele alacağız.

## Hızlı Yanıtlar
- **Word belgelerini birleştirmenin en kolay yolu nedir?** `Document.appendDocument` metodunu `ImportFormatMode.KEEP_SOURCE_FORMATTING` ile kullanın.  
- **Her kaynak dosyanın orijinal stillerini koruyabilir miyim?** Evet—`ImportFormatMode.USE_DESTINATION_STYLES` ayarlayın veya Smart Style Behavior'ı etkinleştirin.  
- **Birleştirmeden sonra sayfa numaralarını doğru tutmak nasıl yapılır?** `NUMPAGES` alanlarını sayfa referanslarına dönüştürün ve `updatePageLayout()` çağırın.  
- **Üstbilgi ve altbilgiler otomatik olarak bağlı kalır mı?** `linkToPrevious(true/false)` ile bağlayabilir veya bağını kesebilirsiniz.  
- **Başlamadan önce neye ihtiyacım var?** Projenize Aspose.Words for Java ekleyin ve kaynak `.docx` dosyalarınızı hazır bulundurun.

## Aspose.Words for Java'da Belgeleri Birleştirme ve Eklemeye Giriş

Bu öğreticide Aspose.Words for Java kütüphanesini kullanarak belgeleri nasıl birleştireceğimizi ve ekleyeceğimizi keşfedeceğiz. Birden fazla belgeyi biçimlendirmeyi ve yapıyı koruyarak sorunsuz bir şekilde birleştirmeyi öğreneceksiniz.

## Önkoşullar

Başlamadan önce, Java projenizde Aspose.Words for Java API'sinin kurulu olduğundan emin olun.

## Belge Birleştirme Seçenekleri

### Basit Ekleme

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### İçe Aktarma Biçim Seçenekleriyle Ekleme

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Boş Belgeye Ekleme

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Sayfa Numarası Dönüştürmesiyle Ekleme

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Convert NUMPAGES fields
dstDoc.updatePageLayout(); // Update page layout for correct numbering
```

## Farklı Sayfa Düzenlerini Ele Alma

Farklı sayfa düzenlerine sahip belgeler eklendiğinde:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Ensure page setup settings match the destination document
```

## Farklı Stillerle Belgeleri Birleştirme

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Akıllı Stil Davranışı

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## DocumentBuilder ile Belgeleri Ekleme

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Kaynak Numaralandırmayı Koruma

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Metin Kutularını Ele Alma

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Üstbilgi ve Altbilgileri Yönetme

### Üstbilgi ve Altbilgileri Bağlama

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Üstbilgi ve Altbilgileri Bağlantısını Kesme

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Bu, “merge word documents java” Projeleri İçin Neden Önemlidir

**merge word documents java** tarzında belgeleri birleştirmeniz gerektiğinde, her dosyanın görünüm ve hissini korumak, hukuk, yayıncılık veya raporlama iş akışları için hayati öneme sahiptir. Yukarıdaki teknikleri kullanmak şunları sağlar:

* Her kaynağın stilleri aynı kalır (veya tercihinize bağlı olarak birleştirilir).  
* Sayfa numaralandırması ve bölüm sonları öngörülebilir şekilde davranır.  
* Üstbilgi ve altbilgiler tek bir kod satırıyla bağlanabilir veya bağımsız tutulabilir.  

## Yaygın Tuzaklar ve İpuçları

| Sorun | Neden Oluşur | Nasıl Çözülür |
|-------|----------------|------------|
| Birleştirme sonrası numaralandırma kayboldu | `NUMPAGES` alanları hâlâ orijinal bölümlere işaret ediyor | `convertNumPageFieldsToPageRef` ve `updatePageLayout()` çağırın |
| Stil çakışması | Çakışan stillerle `KEEP_SOURCE_FORMATTING` kullanmak | `USE_DESTINATION_STYLES`'a geçin veya Akıllı Stil Davranışını etkinleştirin |
| Boş sayfalar ortaya çıkıyor | Farklı `SectionStart` değerleri | Eklemeden önce kaynak bölümlerde `SectionStart.CONTINUOUS` ayarlayın |

## Sıkça Sorulan Sorular

**S: Farklı stillere sahip belgeleri sorunsuz bir şekilde nasıl birleştirebilirim?**  
C: Ekleme sırasında `ImportFormatMode.USE_DESTINATION_STYLES` kullanın veya daha akıllı birleştirme için `SmartStyleBehavior`'ı etkinleştirin.

**S: Belgeleri eklerken sayfa numaralandırmasını koruyabilir miyim?**  
C: Evet, `NUMPAGES` alanlarını `convertNumPageFieldsToPageRef` ile sayfa referanslarına dönüştürün ve ardından `updatePageLayout()` çağırın.

**S: Akıllı Stil Davranışı nedir?**  
C: Mümkün olduğunda kaynak stilleri hedef stillere otomatik olarak eşler, birleştirilmiş içerikte tutarlı bir görünüm sağlamaya yardımcı olur.

**S: Belgeleri eklerken metin kutularını nasıl ele alırım?**  
C: Birleştirme sırasında metin kutularının korunması için `importFormatOptions.setIgnoreTextBoxes(false)` ayarlayın.

**S: Belgeler arasında üstbilgi ve altbilgileri bağlamak veya bağını kesmek istersem ne yapmalıyım?**  
C: Bağlamak için `linkToPrevious(true)`, ayrı tutmak için `linkToPrevious(false)` kullanın, ardından `appendDocument` çağırın.

## Sonuç

Aspose.Words for Java, **belgeleri nasıl birleştireceğiniz** konusunda esnek ve güçlü araçlar sunar; tam biçimlendirmeyi korumanız, çeşitli sayfa düzenlerini ele almanız veya üstbilgi/altbilgi bağlamasını kontrol etmeniz gerektiğinde. Yukarıdaki kod parçacıklarıyla denemeler yaparak kendi belge işleme iş akışınıza uyarlayın ve **merge word documents java** tarzında birleştirme konusunda güvenle ilerleyin.

---

**Son Güncelleme:** 2026-01-09  
**Test Edilen Versiyon:** Aspose.Words for Java 24.12  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}