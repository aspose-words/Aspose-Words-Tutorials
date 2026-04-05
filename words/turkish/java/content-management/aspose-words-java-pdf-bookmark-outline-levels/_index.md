---
date: '2026-04-05'
description: Aspose.Words for Java kullanarak yer imleriyle PDF kaydetmeyi öğrenin.
  İç içe yer imleri oluşturun, anahat seviyelerini ayarlayın ve profesyonel PDF'ler
  oluşturun.
keywords:
- save pdf with bookmarks
- Aspose.Words Java bookmarks
- PDF bookmark outline levels
title: Aspose.Words for Java Kullanarak Yer İmleriyle PDF Kaydet
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java Kullanarak Yer İmleriyle PDF Kaydetme

## Giriş
Word belgelerini PDF'ye dönüştürürken yer imlerini yönetmekte zorlanıyor musunuz? Bu öğreticide Aspose.Words for Java kullanarak **yer imleriyle PDF kaydetme** yöntemini öğrenecek ve bunları profesyonel bir gezinme için etkili bir şekilde düzenleyeceksiniz.

**Öğrenecekleriniz**
- Aspose.Words for Java'ı kurun
- Bir Word belgesinde iç içe yer imleri oluşturun
- Daha net PDF gezinmesi için yer imi anahat seviyelerini yapılandırın
- Belgeyi **yer imleriyle PDF kaydetme** özelliği doğru çalışan bir PDF olarak kaydedin

### Ön Koşullar
Başlamadan önce, şunların olduğundan emin olun:
- **Kütüphaneler ve Bağımlılıklar**: Aspose.Words for Java (sürüm 25.3 veya daha yeni).
- **Ortam Kurulumu**: Makinenizde kurulu bir JDK ve IntelliJ IDEA veya Eclipse gibi bir IDE.
- **Bilgi Ön Koşulları**: Temel Java programlama becerileri ve Maven veya Gradle hakkında bilgi.

## Hızlı Yanıtlar
- **“Yer İmleriyle PDF Kaydetme” ne anlama geliyor?**  
  Bu, yer imi bölmesinin belgenin mantıksal yapısını yansıttığı bir PDF oluşturmak anlamına gelir.
- **Hangi Aspose ürünü gereklidir?**  
  Aspose.Words for Java (PDF dönüştürme özellikleri dahildir).
- **Geliştirme için lisansa ihtiyacım var mı?**  
  Test için ücretsiz deneme sürümü yeterlidir; üretim için kalıcı bir lisans gereklidir.
- **Yer imleri için hiyerarşik seviyeler ayarlayabilir miyim?**  
  Evet – `BookmarksOutlineLevelCollection` kullanarak üst‑alt ilişkileri tanımlayabilirsiniz.
- **Bu yaklaşım büyük belgelerle uyumlu mu?**  
  Kesinlikle; Aspose.Words verileri verimli bir şekilde akıtır, ancak çok büyük dosyalar için kaynakları optimize etmeyi düşünün.

## “Yer İmleriyle PDF Kaydetme” nedir?
Bir Word belgesi PDF'ye dönüştürüldüğünde, başlıkları, bölümleri veya herhangi bir özel işareti yansıtacak şekilde yer imleri oluşturulabilir. Bu yer imleri PDF'nin gezinme bölmesinde görünür ve okuyucuların belge içindeki belirli bölümlere doğrudan atlamasını sağlar.

## Neden yer imi anahat seviyeleri kullanılır?
Anahat seviyeleri atamak, net bir hiyerarşi (bölümler, alt‑bölümler vb.) oluşturur. Bu, özellikle hızlı gezinmenin kritik olduğu yasal sözleşmeler, teknik raporlar veya e‑kitaplarda kullanıcı deneyimini iyileştirir.

## Aspose.Words Kurulumu
Kütüphaneyi projenize Maven veya Gradle ile ekleyin.

**Maven**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Lisans Alımı
Aspose.Words ticari bir üründür, ancak ücretsiz deneme sürümüyle başlayabilirsiniz.

1. **Ücretsiz Deneme** – Tam özellikleri test etmek için [Aspose'un sürüm sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Geçici Lisans** – Kısa vadeli bir anahtara ihtiyacınız varsa [Aspose'un geçici lisans sayfasına](https://purchase.aspose.com/temporary-license/) başvurun.  
3. **Satın Alma** – Kalıcı bir lisansı [Aspose'un satın alma portalından](https://purchase.aspose.com/buy) edinin.

PDF'leri kaydetmeden önce tüm özellikleri açmak için lisansı kodunuzda (burada gösterilmemiştir) başlatın.

## İç İçe Yer İmleri Nasıl Oluşturulur
### Adım 1: Belge ve Builder'ı Başlatma
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Bu, içeriği ve yer imlerini ekleyebileceğiniz yeni bir Word belgesi oluşturur.

### Adım 2: Birincil Yer İmi Ekleme
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

### Adım 3: İç İçe Yer İmi Ekleme
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

### Adım 4: Birincil Yer İmini Kapatma
```java
builder.endBookmark("Bookmark 1");
```

### Adım 5: Ek Bağımsız Yer İmleri Ekleme (isteğe bağlı)
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## Yer İmi Anahat Seviyeleri Nasıl Yapılandırılır
### Adım 1: PDF Kaydetme Seçeneklerini Hazırlama
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

### Adım 2: Hiyerarşik Seviyeleri Atama
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```
Sayısal değer, PDF'nin yer imi ağacındaki derinliği tanımlar.

### Adım 3: Belgeyi PDF Olarak Kaydetme
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
Ortaya çıkan PDF, tamamen yapılandırılmış bir yer imi bölmesi içerir ve **yer imleriyle PDF kaydetme** gereksinimini karşılar.

## Sorun Giderme İpuçları
- **Yer İmleri Eksik** – Her `startBookmark`'ın eşleşen bir `endBookmark`'a sahip olduğundan emin olun.  
- **Yanlış Hiyerarşi** – Atadığınız seviye sayılarını iki kez kontrol edin; daha düşük bir sayı, ağaçta daha üst bir seviyeyi ifade eder.  
- **Büyük Dosyalar** – Bellek tüketimini azaltmak için kaydetmeden önce `doc.optimizeResources()` çağırın.

## Pratik Uygulamalar
1. **Yasal Sözleşmeler** – Maddelere, ek belgelere ve ek bölümlere hızlıca atlayın.  
2. **Teknik Raporlar** – Bölümleri, alt bölümleri ve veri tablolarını gezin.  
3. **E‑Öğrenme Materyalleri** – Okuyuculara PDF içinde tıklanabilir bir içindekiler tablosu sunun.

## Performans Hususları
- Dönüştürmeden önce kullanılmayan stilleri veya görselleri kaldırarak PDF'yi hafif tutun.  
- Çok büyük belgeler işlenirken, çıktıyı `PdfSaveOptions.setSaveFormat(SaveFormat.Pdf)` ile akıtarak ve bellek kullanımını izleyerek düşünün.

## Sonuç
Artık Aspose.Words for Java kullanarak **yer imleriyle PDF kaydetme** ve anahat seviyelerini kontrol etme konusunda bilgi sahibisiniz. Bu teknik, PDF'lerinizi, ister yasal özetler, teknik kılavuzlar, ister öğretici rehberler olsun, çok daha kolay keşfedilebilir hâle getirir.

### Sonraki Adımlar
- Belge başlıklarına dayalı dinamik yer imi adları deneyin.  
- Gerekirse bu yaklaşımı Aspose.PDF ile birleştirerek dönüştürme sonrası yer imi düzenlemesi yapın.  
- Köprüler, açıklamalar ve güvenlik gibi diğer PDF özelliklerini keşfedin.

## Sık Sorulan Sorular
**S: Aspose.Words for Java'ı nasıl kurarım?**  
C: Yukarıda gösterilen Maven veya Gradle bağımlılığını ekleyin, ardından lisans dosyanızı projenin resources klasörüne yerleştirin.

**S: Anahat seviyeleri ayarlamadan yer imleri oluşturabilir miyim?**  
C: Evet, ancak anahat seviyeleri olmadan yer imi bölmesi düz görünecek ve derin gezinmeyi zorlaştıracaktır.

**S: Kaç yer imi seviyesi oluşturabileceğim konusunda bir sınırlama var mı?**  
C: Teknik olarak yok, ancak okunabilirlik için hiyerarşiyi makul bir derinlikte (genellikle 3‑5 seviye) tutun.

**S: Aspose çok büyük Word dosyalarını nasıl yönetir?**  
C: İçeriği akıtarak ve dönüşüm sırasında bellek kullanımını düşük tutmak için `optimizeResources()` sunar.

**S: PDF kaydedildikten sonra yer imlerini düzenleyebilir miyim?**  
C: Evet – mevcut bir PDF'de yer imlerini değiştirmek veya eklemek için Aspose.PDF for Java kullanın.

## Kaynaklar
- [Aspose.Words Dokümantasyonu](https://reference.aspose.com/words/java/)
- [En Son Sürümleri İndir](https://releases.aspose.com/words/java/)
- [Lisans Satın Al](https://purchase.aspose.com/buy)
- [Ücretsiz Deneme](https://releases.aspose.com/words/java/)
- [Geçici Lisans Başvurusu](https://purchase.aspose.com/temporary-license/)
- [Aspose Destek Forumu](https://forum.aspose.com/c/words/10)

---

**Son Güncelleme:** 2026-04-05  
**Test Edilen Versiyon:** Aspose.Words 25.3 for Java  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}