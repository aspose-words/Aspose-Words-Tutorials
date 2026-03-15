---
date: '2026-03-15'
description: Aspose.Words for Java kullanarak PDF yer imleri eklemeyi ve taslak seviyelerini
  ayarlamayı öğrenin, PDF gezinmesini ve okunabilirliğini artırın.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Aspose.Words Java ile PDF yer imleri ve anahat seviyeleri ekleyin
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

 "---" line.

Then "**Last Updated:** 2026-03-15" keep date.

"**Tested With:** Aspose.Words for Java 25.3" keep.

"**Author:** Aspose" keep.

Now produce final content.

Be careful to preserve markdown formatting exactly.

Let's craft translation.

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java ile PDF yer imleri ve anahat seviyeleri ekleme

## Giriş
Bu öğreticide **PDF yer imlerini nasıl ekleyeceğinizi** ve **Aspose.Words for Java** kullanarak anahat seviyelerini nasıl yapılandıracağınızı öğreneceksiniz. İyi düzenlenmiş yer imleri, büyük PDF'leri kolayca gezilebilir kılar; ister yasal sözleşmeler, detaylı raporlar ya da e‑öğrenme materyalleriyle çalışıyor olun.

**Neler Öğreneceksiniz**
- **Aspose.Words for Java**'ı kurma ve kullanma
- Bir Word belgesinde **iç içe yer imleri oluşturma**
- Temiz bir hiyerarşi için **yer imi anahat seviyelerini ayarlama**
- **PDF olarak kaydetme** ve yapılandırılmış bir yer imi ağacı oluşturma

İlerlemeye başlamadan önce her şeyin elinizde olduğundan emin olun.

### Önkoşullar
Başlamadan önce şunların mevcut olduğunu doğrulayın:
- **Kütüphaneler ve Bağımlılıklar**: Aspose.Words for Java (sürüm 25.3 veya daha yeni).  
- **Ortam Kurulumu**: JDK yüklü ve IntelliJ IDEA veya Eclipse gibi bir IDE.  
- **Bilgi Önkoşulları**: Temel Java programlama becerileri ve Maven ya da Gradle hakkında bilgi.

## Hızlı Yanıtlar
- **Birincil hedef nedir?** PDF yer imleri eklemek ve anahat seviyelerini tanımlamak.  
- **Hangi kütüphane gereklidir?** Aspose.Words for Java (v25.3+).  
- **Lisans gerekir mi?** Test için ücretsiz deneme yeterlidir; üretim için ticari lisans gereklidir.  
- **Yer imli PDF tek adımda üretilebilir mi?** Evet—`PdfSaveOptions` yapılandırın ve `doc.save` çağırın.  
- **İç içe yer imleri destekleniyor mu?** Kesinlikle, sınırsız seviyede iç içe yer imleri oluşturabilirsiniz.

## Aspose.Words Kurulumu
Projeye gerekli bağımlılıkları ekleyerek başlayın. Maven ve Gradle örnekleri aşağıdadır:

**Maven:**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Lisans Edinme
Aspose.Words ticari bir üründür, ancak özelliklerini keşfetmek için ücretsiz bir deneme ile başlayabilirsiniz.

1. **Ücretsiz Deneme**: Tam özellikleri test etmek için [Aspose'un sürüm sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Geçici Lisans**: Daha uzun bir değerlendirme süresi gerekiyorsa [Aspose'un geçici lisans sayfasından](https://purchase.aspose.com/temporary-license/) başvurun.  
3. **Satın Alma**: Sürekli kullanım için [Aspose'un satın alma portalından](https://purchase.aspose.com/buy) lisans alın.

Lisans dosyanızı aldıktan sonra, tüm özelliklerin kilidini açmak için projede başlatın.

## Uygulama Kılavuzu
Uygulamayı adım adım inceleyecek, her bölümü küçük parçalara ayıracağız.

### İç İçe Yer İmleri Oluşturma
**Genel Bakış**: Aspose.Words for Java kullanarak bir Word belgesinde **iç içe yer imleri oluşturmayı** öğrenin.

#### Adım 1: Belge ve Builder'ı Başlatma
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Bu kod yeni bir Word belgesi ve içerik ile yer imleri eklemenizi sağlayan bir builder nesnesi oluşturur.

#### Adım 2: İç İçe Yer İmleri Ekleme
Öncelikle bir ana yer imi oluşturun:
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
Şimdi, onun içine başka bir yer imi yerleştirin:
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
Dış yer imini tamamlayın:
```java
builder.endBookmark("Bookmark 1");
```

#### Adım 3: Ek Yer İmleri Ekleme
İhtiyacınıza göre yer imleri eklemeye devam edebilirsiniz. Örneğin, ayrı bir üçüncü yer imi:
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Yer İmi Anahat Seviyelerini Yapılandırma
**Genel Bakış**: Yer imlerinizi anahat seviyelerini ayarlayarak düzenleyin; bu, PDF görüntüleyicilerinde göreceğiniz hiyerarşiyi belirler.

#### Adım 1: PdfSaveOptions'ı Ayarlama
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
Bu seçenekler **belgeyi PDF olarak kaydettiğinizde** uygulanacaktır.

#### Adım 2: Anahat Seviyeleri Ekleme
Her yer imine bir seviye atayın; düşük sayılar anahat ağacında daha üstte görünür:
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Adım 3: Belgeyi Kaydetme
Son olarak, yapılandırılmış yer imi hiyerarşisiyle PDF'i oluşturun:
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

### Sorun Giderme İpuçları
- **Yer İmleri Eksik**: Her `startBookmark`'in eşleşen bir `endBookmark`'i olduğundan emin olun.  
- **Yanlış Seviyeler**: Anahat seviyelerini ekleme sırasını iki kez kontrol edin; hiyerarşi atadığınız sayısal seviyeye göre oluşur.  
- **Büyük Belgeler**: PDF boyutunu küçültmek için kaydetmeden önce `doc.removeUnusedResources()` kullanın.

## Pratik Uygulamalar
**PDF yer imleri eklemenin** öne çıktığı birkaç gerçek dünya senaryosu:

1. **Yasal Belgeler** – Maddelere, eklere veya ek belgelere hızlıca atlayın.  
2. **Finansal Raporlar** – Bölümler, tablolar ve grafikler arasında gezinmeyi kolaylaştırın.  
3. **E‑Öğrenme Materyalleri** – Okuyuculara tıklanabilir bir içindekiler tablosu sunun.  

## Performans Düşünceleri
- **Bellek Yönetimi**: Çok büyük Word dosyalarını işlerken, kaydetme sonrası `System.gc()` çağırarak belleği serbest bırakın.  
- **Belge Boyutu**: Gereksiz resimleri veya gizli metinleri yer imleri oluşturmadan önce kaldırarak son PDF'i hafif tutun.

## Sonuç
Artık **PDF yer imleri ekleme**, anahat seviyelerini yapılandırma ve **Aspose.Words for Java** ile **yer imli PDF üretme** konusunda tam üretim‑hazır bir yönteme sahipsiniz. Bu yaklaşım PDF kullanılabilirliğini büyük ölçüde artırır ve son kullanıcılarınıza profesyonel bir gezinme deneyimi sunar.

**Sonraki Adımlar**: Bu tekniği, PDF oluşturulduktan sonra yer imlerini düzenlemek için Aspose.PDF for Java ile birleştirmeyi deneyin veya her raporunuza otomatik olarak bir içindekiler tablosu ekleyen toplu‑işlem hizmetine entegre edin.

## Sıkça Sorulan Sorular

**S: Aspose.Words for Java nasıl kurulur?**  
C: Yukarıda gösterilen Maven ya da Gradle bağımlılığını ekleyin, lisans dosyasını projenin `resources` klasörüne koyun ve başlangıçta başlatın.

**S: Yer imlerini anahat seviyeleri olmadan kullanabilir miyim?**  
C: Evet, ancak anahat seviyeleri olmadan PDF görüntüleyici tüm yer imlerini aynı hiyerarşide listeler, bu da gezinmeyi zorlaştırır.

**S: Yer imi iç içeleme sınırı nedir?**  
C: Teknik olarak sabit bir sınır yoktur, ancak okunabilirliği korumak için hiyerarşiyi 3‑5 seviye arasında tutmanız önerilir.

**S: Aspose büyük belgeleri nasıl yönetir?**  
C: İçeriği akış (stream) olarak işler ve bellek kullanımını düşük tutmak için `Document.optimizeResources()` gibi yöntemler sunar.

**S: PDF kaydedildikten sonra yer imlerini değiştirebilir miyim?**  
C: Kesinlikle—kaydedilen PDF'i düzenlemek, yeniden sıralamak veya silmek için Aspose.PDF for Java kullanabilirsiniz.

## Kaynaklar
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)
- [Download Latest Releases](https://releases.aspose.com/words/java/)
- [Purchase a License](https://purchase.aspose.com/buy)
- [Free Trial](https://releases.aspose.com/words/java/)
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Last Updated:** 2026-03-15  
**Tested With:** Aspose.Words for Java 25.3  
**Author:** Aspose