---
date: 2026-01-16
description: İnçleri puana dönüştürmeyi, Java’da belge meta verilerini okumayı, Java’da
  özel özellikler eklemeyi ve Aspose.Words for Java ile sayfa kenar boşluklarını ayarlamayı
  öğrenin.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: İnçleri Puanlara Dönüştür – Aspose.Words for Java'da Belge Özelliklerini Kullanarak
url: /tr/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# İnçleri Puana Dönüştür – Aspose.Words for Java'da Belge Özelliklerini Kullanma

Bu öğreticide, sayfa kenar boşluklarını ayarlarken **inçleri puana dönüştürmeyi**, Java'da belge meta verilerini okumayı, Java'da özel özellikler eklemeyi ve Aspose.Words for Java kullanarak yerleşik belge özellikleriyle çalışmayı öğreneceksiniz. Raporlar, faturalar veya yasal belgeler oluşturuyor olun, bu tekniklerde ustalaşmak Word dosyalarınızın görünümü ve meta verileri üzerinde ince ayar kontrolü sağlar.

## Hızlı Yanıtlar
- **İnçleri puana nasıl dönüştürürüm?** Aspose.Words'tan `ConvertUtil.inchToPoint(value)` kullanın.
- **Java'da belge meta verilerini okuyabilir miyim?** Evet – `doc.getBuiltInDocumentProperties()` veya `doc.getCustomDocumentProperties()` çağırın.
- **Java'da özel bir özellik nasıl eklerim?** `doc.getCustomDocumentProperties().add(name, value)` kullanın.
- **Sayfa kenar boşluklarını puan cinsinden ayarlayan yöntem hangisidir?** `PageSetup.setTopMargin`, `setBottomMargin` vb., puan değerlerini kabul eder.
- **Yer işaretine bağlama destekleniyor mu?** Evet – özel özellikler koleksiyonunda `addLinkToContent` kullanın.

## Belge Özelliklerine Giriş

Belge özellikleri, herhangi bir Word dosyasının hayati bir parçasıdır. Başlık, yazar, konu, anahtar kelimeler ve aşağı yönlü işleme ihtiyaç duyduğunuz herhangi bir özel meta veri gibi bilgileri depolarlar. Aspose.Words for Java'da yerleşik ve özel belge özelliklerini manipüle edebilir ve ölçü birimlerini dönüştürerek (ör. **inçleri puana dönüştür**) kenar boşlukları gibi düzen detaylarını da kontrol edebilirsiniz.

## “İnçleri puana dönüştür” nedir?

Word'de, düzen ölçüleri puan cinsinden ifade edilir (1 puan = bir inçin 1/72'si). İnçleri puana dönüştürmek, kenar boşlukları, girintiler ve boşlukları tanıdık imparatorluk birimleriyle tanımlamanıza olanak tanırken API dahili olarak puanlarla çalışır.

## Java'da belge meta verilerini yönetmek neden önemlidir?

Meta verileri gömmek, aramayı, sınıflandırmayı ve iş akışlarını otomatikleştirmeyi kolaylaştırır. Örneğin, bir sözleşmeye “Yetkili” bayrağı ekleyebilir veya denetim izleri için bir revizyon numarası depolayabilirsiniz. Bu bilgileri programlı olarak okumak ve yazmak, büyük belge toplulukları arasında tutarlılık sağlar.

## Önkoşullar
- Java 17+ (veya uyumlu JDK)
- Projenize eklenmiş Aspose.Words for Java kütüphanesi (Maven/Gradle)
- Erişilebilir bir dizine yerleştirilmiş örnek bir `.docx` dosyası (ör. `Properties.docx`)

## Adım‑Adım Kılavuz

### Yerleşik Belge Özelliklerini Listeleme
Aşağıda, bir belgeyi açan ve Başlık, Yazar ve Anahtar Kelimeler gibi tüm yerleşik özellikleri yazdıran basit bir test yer almaktadır.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **Pro tip:** Bu kod parçacığını, meta verilerinizin önceki adımlarda doğru yazıldığını doğrulamak için kullanın.

### Özel Belge Özellikleri Ekleme (add custom properties java)
Özel özellikler, ihtiyacınız olan herhangi bir veri tipini—boolean, string, tarih, sayı vb.—saklamanızı sağlar.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **Neden önemli:** **Authorized** gibi bir bayrak eklemek, belge içeriğini değiştirmeden sonraki onay iş akışlarını yönlendirebilir.

### Özel Bir Özelliği Kaldırma
Artık ihtiyaç duyulmayan bir özellik, temiz bir şekilde silinebilir.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### İçeriğe Bağlantı Yapılandırma (yer işareti bağlama)
Bir yer işareti oluşturabilir ve ardından bu yer işaretine işaret eden bir özel özellik ekleyerek dinamik çapraz referanslar sağlayabilirsiniz.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Ölçü Birimleri Arasında Dönüştürme (set page margins java)
İşte ana anahtar kelimenin parladığı yer. Kenar boşluklarını inç olarak ayarlıyoruz, ardından `ConvertUtil` kullanarak **inçleri puana dönüştürüyoruz**.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Not:** `ConvertUtil`, esnek düzen yönetimi için `pointToInch`, `mmToPoint` vb. yöntemleri de sunar.

### Kontrol Karakterlerini Kullanma (read document metadata java)
Kontrol karakterleri, metin akışlarını temizlemenize yardımcı olur. Bu örnek, bir satır sonu (`\r`) karakterini Windows satır sonu dizisi (`\r\n`) ile değiştirir.

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Yaygın Sorunlar ve Çözümler
| Sorun | Neden | Çözüm |
|-------|-------|-----|
| Kenar boşlukları dönüşüm sonrası yanlış görünüyor | Yanlış birim kullanımı (ör. inç yerine cm) | İnç değerleri için `ConvertUtil.inchToPoint` çağırdığınızı doğrulayın |
| Özel özellik görünmüyor | Özellik belge kaydedildikten sonra eklendi | Özellikleri ekledikten sonra `doc.save(...)` çağırın |
| Yer işareti bağlantısı kırık | Yer işareti adı yazım hatası | `addLinkToContent` içinde yer işareti adının tam olarak eşleştiğinden emin olun |

## SSS'ler

### Yerleşik belge özelliklerine nasıl erişilir?

Aspose.Words for Java'da yerleşik belge özelliklerine erişmek için `Document` nesnesindeki `getBuiltInDocumentProperties` yöntemini kullanabilirsiniz. Bu yöntem, üzerinden döngü kurabileceğiniz bir yerleşik özellik koleksiyonu döndürür.

### Bir belgeye özel belge özellikleri ekleyebilir miyim?

Evet, `CustomDocumentProperties` koleksiyonunu kullanarak bir belgeye özel belge özellikleri ekleyebilirsiniz. Özel özellikleri string, boolean, tarih ve sayısal değerler gibi çeşitli veri tipleriyle tanımlayabilirsiniz.

### Belirli bir özel belge özelliğini nasıl kaldırabilirim?

Belirli bir özel belge özelliğini kaldırmak için `CustomDocumentProperties` koleksiyonundaki `remove` yöntemini kullanabilir ve kaldırmak istediğiniz özelliğin adını parametre olarak geçebilirsiniz.

### Bir belge içinde içeriğe bağlamanın amacı nedir?

Bir belge içinde içeriğe bağlamak, belgenin belirli bölümlerine dinamik referanslar oluşturmanıza olanak tanır. Bu, etkileşimli belgeler veya bölümler arası çapraz referanslar oluşturmak için faydalı olabilir.

### Aspose.Words for Java'da farklı ölçü birimleri arasında nasıl dönüşüm yapılır?

Aspose.Words for Java'da farklı ölçü birimleri arasında dönüşüm yapmak için `ConvertUtil` sınıfını kullanabilirsiniz. Bu sınıf, inçten puana, puandan santimetreye ve daha fazlasına dönüşüm sağlayan yöntemler sunar.

## Sıkça Sorulan Sorular

**S: Tüm dosyayı yüklemeden Java'da belge meta verilerini nasıl okurum?**  
C: Belge içeriğini tamamen yüklemeden temel özellikleri almak için `DocumentInfo` kullanın.

**S: Mevcut belgeler için Java'da programlı olarak sayfa kenar boşluklarını ayarlayabilir miyim?**  
C: Evet—belgeyi açın, `PageSetup` kenar boşluklarını (gerekirse inçleri puana dönüştürerek) değiştirin ve kaydedin.

**S: Özel özellikleri PDF meta verilerine aktarabilir miyim?**  
C: PDF olarak kaydederken, Aspose.Words özel belge özelliklerini otomatik olarak PDF özel meta verilerine eşler.

**S: Kontrol karakterleri PDF dönüşümünü etkiler mi?**  
C: Dönüşüm sırasında korunurlar; ancak tutarlılık için satır sonlarını normalleştirmek isteyebilirsiniz.

**S: `ConvertUtil` için hangi Aspose.Words sürümü gereklidir?**  
C: `ConvertUtil`, Aspose.Words 16.5'ten beri mevcuttur; herhangi bir yeni sürüm bunu destekler.

## Sonuç

**İnçleri puana dönüştür**ü, Java'da belge meta verilerini okumayı ve Java'da özel özellikler eklemeyi ustalaşarak, Word dosyalarınızın görsel düzeni ve gizli verileri üzerinde tam kontrol elde edersiniz. Bu yetenekler, otomatik belge iş akışları oluşturmanıza, uyumluluğu sağlamanıza ve zengin biçimlendirilmiş raporlar üretmenize olanak tanır—hepsi Aspose.Words for Java ile.

---

**Son Güncelleme:** 2026-01-16  
**Test Edilen:** Aspose.Words for Java 24.11  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}