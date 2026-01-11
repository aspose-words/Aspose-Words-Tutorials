---
date: 2026-01-11
description: Aspose.Words for Java kullanarak yer imlerini gösterme/gizleme ve Java’da
  yer imi oluşturmayı öğrenin; böylece belge gezinmesi ve manipülasyonu daha verimli
  olur.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java ile Yer İmlerini Göster ve Gizle
url: /tr/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile Yer İmlerini Göster ve Gizle

## Aspose.Words for Java'da Yer İmlerini Kullanma Giriş

Yer imleri, Aspose.Words for Java'da **create bookmark java** oluşturmanıza, belirli içeriğe gitmenize ve farklı belge sürümleri oluşturmanız gerektiğinde **show hide bookmarks** yapmanıza olanak tanıyan güçlü bir özelliktir. Bu adım adım rehberde, yer imlerini oluşturma, erişme, güncelleme, kopyalama ve görünürlüğünü değiştirme konularını ele alacağız ve belge manipülasyonu üzerinde tam kontrol sağlayacağız.

## Hızlı Yanıtlar
- **Yer imlerinin temel amacı nedir?** Belgenin belirli bölümlerini işaretlemek ve daha sonra geri almak.  
- **Yer imi işaretçilerini son çıktıda gizleyebilir miyim?** Evet—görünürlüğünü değiştirmek için show/hide API'sini kullanın.  
- **Bir tablo hücresinin içinde nasıl bir yer imi oluştururum?** İşaretçi hücrenin içinde iken `DocumentBuilder` ile yer imini başlatıp sonlandırın.  
- **Yer işaretli metni başka bir belgeye kopyalamak mümkün mü?** Kesinlikle—biçimlendirmeyi korumak için `NodeImporter` kullanın.  
- **Hangi Aspose.Words sürümü gereklidir?** Herhangi bir son sürüm; kod en yeni 2026 yapısı ile çalışır.

## “show hide bookmarks” nedir?

**show hide bookmarks** özelliği, kaydedilen belgede yer imi sınırlayıcılarını programlı olarak göstermenizi veya gizlemenizi sağlar. Bu, son kullanıcılar için temiz bir çıktı üretmek isterken aynı zamanda iç işlem için yer imi verilerini korumak istediğinizde faydalıdır.

## Java belge otomasyonunda neden yer imleri kullanılır?

- **Verimli gezinme** – Tüm dosyayı taramadan doğrudan bölümlere atlayın.  
- **Dinamik içerik oluşturma** – Yer imine bağlı metni ekleyin, değiştirin veya kaldırın.  
- **Koşullu görünürlük** – Kullanıcı tercihine veya çıktı formatına göre yer imi işaretçilerini gösterin veya gizleyin.  
- **Yeniden kullanılabilirlik** – Stilleri koruyarak yer işaretli parçaları belgeler arasında kopyalayın.

## Önkoşullar
- Java Development Kit (JDK) 8 veya üzeri.  
- Projeye eklenmiş Aspose.Words for Java kütüphanesi (Maven/Gradle veya JAR).  
- `Document` ve `DocumentBuilder` sınıflarına temel aşinalık.

## Adım Adım Kılavuz

### Adım 1: Yer İmi Oluşturma (create bookmark java)

Bir yer imi eklemek için, onu başlatır, içeriği yazar ve ardından sonlandırırsınız. Bu örnek, **My Bookmark** adlı basit bir yer imi oluşturur.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Adım 2: Yer İmlerine Erişim (access bookmarks java)

Yer imleri, sıfır‑tabanlı indeksleriyle ya da isimleriyle alınabilir. Aşağıdaki kod her iki yaklaşımı da gösterir.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Adım 3: Yer İmi Verisini Güncelleme (update bookmark text)

Bir yer imini yeniden adlandırabilir veya metin içeriğini değiştirebilirsiniz. Bu, temel belge değiştiğinde kullanışlıdır.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Adım 4: Yer İşaretli Metinle Çalışma (copy bookmarked text)

Orijinal biçimlendirmeyi koruyarak bir yer işaretli parçayı başka bir belgeye kopyalamak, `NodeImporter` ile oldukça basittir.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Adım 5: Yer İmlerini Göster ve Gizle (show hide bookmarks)

Aşağıdaki kod parçacığı, kaydedilen dosyada bir yer iminin işaretçilerini nasıl gizleyeceğinizi gösterir. Gizlemek için `false`, göstermek için `true` gönderin.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Adım 6: Satır Yer İmlerini Çözümleme (bookmark table cell)

Yer imleri tablo satırlarını kapsadığında karışabilirler. Aşağıdaki yardımcı yöntemler bunları çözer ve yer imine göre belirli bir satırı silmenize olanak tanır.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Yaygın Sorunlar ve Çözümler

| Issue | Solution |
|-------|----------|
| **Yer imi bulunamadı** | Yer imi adının tam olarak (büyük/küçük harfe duyarlı) eşleştiğini ve belgenin oluşturulduktan sonra kaydedildiğini doğrulayın. |
| **Kopyalanan metnin biçimlendirmesi kaybolur** | Adım 4'te gösterildiği gibi `NodeImporter` ile `ImportFormatMode.KEEP_SOURCE_FORMATTING` kullanın. |
| **Göster/gizle çıktı üzerinde etkili değil** | `showHideBookmarkedContent` metodunu belgeyi kaydetmeden **önce** çağırdığınızdan emin olun. |
| **Tablo hücresi içindeki yer imi yoksayılır** | Başlatma/bitirme çağrılarını, builder imlecinin hedef hücrenin içinde olduğu sırada yapın. |

## Sıkça Sorulan Sorular

**S: Bir tablo hücresinde nasıl yer imi oluştururum?**  
C: `DocumentBuilder` ile imleci istediğiniz hücreye taşıyın, ardından hücre içeriği etrafında `startBookmark` ve `endBookmark` çağrılarını yapın.

**S: Yer imini başka bir belgeye kopyalayabilir miyim?**  
C: Evet—yer işaretli düğümü orijinal biçimlendirmesini koruyarak içe aktarmak için `NodeImporter` sınıfını (Adım 4'e bakın) kullanın.

**S: Yer imine göre bir satırı nasıl silebilirim?**  
C: Önce yer imini içeren satırı bulun, ardından satır düğümünde `remove` metodunu çağırın (Adım 6'da gösterildiği gibi).

**S: Yer imleri için yaygın kullanım senaryoları nelerdir?**  
C: İçindekiler tablosu oluşturma, raporlama için belirli bölümleri çıkarma ve kullanıcı seçimlerine göre belge montajını otomatikleştirme.

**S: Aspose.Words for Java hakkında daha fazla bilgiyi nereden bulabilirim?**  
C: Ayrıntılı dokümantasyon ve indirmeler için [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) adresini ziyaret edin.

**Son Güncelleme:** 2026-01-11  
**Test Edilen Sürüm:** Aspose.Words for Java 24.11 (2026)  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}