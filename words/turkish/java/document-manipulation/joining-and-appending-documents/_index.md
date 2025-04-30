---
"description": "Aspose.Words for Java kullanarak belgeleri zahmetsizce nasıl birleştireceğinizi ve ekleyeceğinizi öğrenin. Biçimlendirmeyi koruyun, üstbilgileri ve altbilgileri yönetin ve daha fazlasını yapın."
"linktitle": "Belgeleri Birleştirme ve Ekleme"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Java için Aspose.Words'de Belgeleri Birleştirme ve Ekleme"
"url": "/tr/java/document-manipulation/joining-and-appending-documents/"
"weight": 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Belgeleri Birleştirme ve Ekleme


## Java için Aspose.Words'de Belgeleri Birleştirme ve Eklemeye Giriş

Bu eğitimde, Aspose.Words for Java kütüphanesini kullanarak belgeleri nasıl birleştireceğinizi ve ekleyeceğinizi inceleyeceğiz. Biçimlendirme ve yapıyı korurken birden fazla belgeyi sorunsuz bir şekilde nasıl birleştireceğinizi öğreneceksiniz.

## Ön koşullar

Başlamadan önce, Java projenizde Aspose.Words for Java API'sinin kurulu olduğundan emin olun.

## Belge Birleştirme Seçenekleri

### Basit Ekleme

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### İçe Aktarma Biçimi Seçenekleriyle Ekle

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Boş Belgeye Ekle

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Sayfa Numarası Dönüşümü ile Ekle

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // NUMPAGES alanını dönüştür
dstDoc.updatePageLayout(); // Doğru numaralandırma için sayfa düzenini güncelleyin
```

## Farklı Sayfa Kurulumlarını Yönetme

Farklı sayfa düzenlerine sahip belgeleri eklerken:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Sayfa düzeni ayarlarının hedef belgeyle eşleştiğinden emin olun
```

## Farklı Stillerdeki Belgeleri Birleştirme

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

## Kaynak Numaralandırmayı Tutma

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Metin Kutularını Kullanma

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Başlıkları ve Altbilgileri Yönetme

### Başlıklar ve Altbilgileri Bağlama

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Başlıklar ve Altbilgilerin Bağlantısını Kaldırma

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Çözüm

Java için Aspose.Words, biçimlendirmeyi korumanız, farklı sayfa kurulumlarını yönetmeniz veya başlıkları ve altbilgileri yönetmeniz gerekip gerekmediğine bakılmaksızın belgeleri birleştirmek ve eklemek için esnek ve güçlü araçlar sağlar. Belirli belge işleme ihtiyaçlarınızı karşılamak için bu teknikleri deneyin.

## SSS

### Farklı stillere sahip belgeleri sorunsuz bir şekilde nasıl birleştirebilirim?

Farklı stillere sahip belgeleri birleştirmek için şunu kullanın: `ImportFormatMode.USE_DESTINATION_STYLES` eklerken.

### Belge eklerken sayfa numaralandırmasını koruyabilir miyim?

Evet, sayfa numaralandırmasını kullanarak koruyabilirsiniz. `convertNumPageFieldsToPageRef` yöntem ve sayfa düzenini güncelleme.

### Akıllı Stil Davranışı Nedir?

Akıllı Stil Davranışı, belgeler eklerken tutarlı stilleri korumaya yardımcı olur. Bunu şununla kullanın: `ImportFormatOptions` Daha iyi sonuçlar için.

### Belge eklerken metin kutularını nasıl kullanabilirim?

Ayarlamak `importFormatOptions.setIgnoreTextBoxes(false)` Ekleme sırasında metin kutuları eklemek için.

### Belgeler arasındaki üstbilgi ve altbilgileri birbirine bağlamak/bağlantısını kaldırmak istersem ne olur?

Başlıkları ve altbilgileri şu şekilde bağlayabilirsiniz: `linkToPrevious(true)` veya onları bağlantısını kes `linkToPrevious(false)` ihtiyaç duyulduğu takdirde.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}