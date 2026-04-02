---
date: '2026-04-02'
description: Aspose.Words for Java ile iç içe yer imleri oluşturmayı, yer imi anahat
  seviyelerini ayarlamayı ve Word belgelerini PDF olarak kaydetmeyi öğrenin.
keywords:
- create nested bookmarks
- how to set bookmark
- save word pdf bookmarks
title: Aspose.Words for Java Kullanarak PDF'lerde İç İçe Yer İşaretleri Oluşturun
  ve Taslak Düzeylerini Ayarlayın
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# PDF'lerde Aspose.Words for Java Kullanarak İç İçe Yer İşaretleri Oluşturma ve Taslak Düzeylerini Ayarlama

## Giriş
Word belgelerini PDF'lere dönüştürürken yer işaretlerini yönetmekte zorlanıyor musunuz? **Bu öğreticide iç içe yer işaretleri oluşturmayı**, taslak düzeylerini yapılandırmayı ve sonucu temiz, gezilebilir bir PDF olarak Aspose.Words for Java kullanarak kaydetmeyi öğreneceksiniz. Bu rehberin sonunda okuyucuların ihtiyaç duydukları bölümlere doğrudan atlayabilecekleri profesyonel görünümlü bir PDF elde edeceksiniz.

**Öğrenecekleriniz**
- Projenizde Aspose.Words for Java'ı kurun  
- **İç içe yer işaretleri oluşturun** bir Word belgesinde  
- **Yer işareti** taslak düzeylerini net bir hiyerarşi için nasıl ayarlayacağınızı  
- **Word PDF yer işaretlerini** doğru yapı ile kaydedin  

### Hızlı Yanıtlar
- **Belgeleri oluşturmak için birincil sınıf nedir?** `DocumentBuilder`  
- **Hangi yöntem bir yer işareti taslak düzeyi ekler?** `BookmarksOutlineLevels.add()`  
- **PDF'leri dışa aktarmak için lisansa ihtiyacım var mı?** Üretim için bir lisans gereklidir; ücretsiz deneme değerlendirme için çalışır.  
- **Yer işaretlerini rastgele derinliğe kadar iç içe yerleştirebilir miyim?** Evet, ancak hiyerarşiyi son kullanıcılar için okunabilir tutun.  
- **Hangi Aspose.Words sürümü gereklidir?** Sürüm 25.3 veya üzeri.

## “İç içe yer işaretleri oluşturma” nedir?
İç içe yer işaretleri, diğer yer işaretlerinin içinde bulunan ve bir üst‑alt hiyerarşi oluşturan yer işaretleridir. Bir PDF'de bunlar, okuyucuların bölümleri gerektiğinde daraltıp genişletebileceği yer işareti panelinde genişletilebilir öğeler olarak görünür.

## Neden yer işareti taslak düzeyleri ayarlamalıyız?
Taslak düzeyleri, PDF'in yer işareti panelindeki görsel iç içe sıralamayı tanımlar. Doğru düzeyler, özellikle uzun hukuki sözleşmeler, teknik raporlar veya e‑kitaplarda kullanıcıların bilgiyi hızlıca bulmasını sağlayarak gezinmeyi iyileştirir.

## Ön Koşullar
- **Kütüphaneler ve Bağımlılıklar**: Aspose.Words for Java (sürüm 25.3 veya üzeri).  
- **Ortam**: JDK 8+ ve IntelliJ IDEA veya Eclipse gibi bir IDE.  
- **Bilgi**: Temel Java, Maven veya Gradle bilgisi.

### Aspose.Words Kurulumu
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
Aspose.Words ticari bir üründür, ancak ücretsiz bir deneme ile başlayabilirsiniz.

1. **Ücretsiz Deneme** – Tam yetenekleri test etmek için [Aspose'un sürüm sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Geçici Lisans** – Kısa vadeli bir anahtara ihtiyacınız varsa [Aspose'un geçici lisans sayfasına](https://purchase.aspose.com/temporary-license/) başvurun.  
3. **Satın Alma** – Kalıcı bir lisansı [Aspose'un satın alma portalı](https://purchase.aspose.com/buy) üzerinden satın alın.

Aspose API'lerini kullanmadan önce kodunuzda lisans dosyasını başlatın, böylece tüm özelliklerin kilidi açılır.

## Uygulama Kılavuzu

### Bir Word belgesinde iç içe yer işaretleri nasıl oluşturulur
Basit bir belge oluşturacağız ve üç yer işareti ekleyeceğiz; bunlardan biri başka bir yer işareti içeriyor.

#### Adım 1: Belgeyi ve oluşturucuyu başlatma
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### Adım 2: İlk (üst) yer işaretini ekleme
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### Adım 3: İkinci yer işaretini birincisinin içine iç içe yerleştirme
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### Adım 4: Dış yer işaretini kapatma
```java
builder.endBookmark("Bookmark 1");
```

#### Adım 5: Bağımsız üçüncü bir yer işareti ekleme
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### PDF dışa aktarımı için yer işareti taslak düzeylerini nasıl ayarlarsınız
Şimdi son PDF'de görünecek taslak hiyerarşisini yapılandıracağız.

#### Adım 1: `PdfSaveOptions` hazırlama
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### Adım 2: Her yer işaretine taslak düzeyleri atama
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Adım 3: Belgeyi yapılandırılmış yer işaretleriyle PDF olarak kaydetme
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Yaygın Sorunlar ve Çözümler
- **Eksik yer işaretleri** – Her `startBookmark`'ın eşleşen bir `endBookmark`'a sahip olduğundan emin olun.  
- **Yanlış hiyerarşi** – Atadığınız seviye sayılarını iki kez kontrol edin; daha düşük bir sayı daha yüksek (üst) seviyeyi ifade eder.  
- **Lisans uygulanmadı** – Yer işaretleri kaybolursa, lisans dosyasının herhangi bir belge işleme işleminden önce yüklendiğinden emin olun.  

## Pratik Uygulamalar
1. **Hukuki sözleşmeler** – Maddelere, alt maddelere ve eklerine hızlıca atlayın.  
2. **Teknik raporlar** – Bölümlere, tablolara ve şekillere kaydırmadan gidin.  
3. **E‑öğrenme materyali** – Öğrencilerin bölümleri genişletip örnekleri gerektiğinde daraltmasına izin verin.

## Performans İpuçları
- Kaydetmeden önce kullanılmayan bölümleri veya görselleri kaldırarak PDF boyutunu küçük tutun.  
- Çok büyük belgeler için `doc.cleanup()` çağırın veya dosyayı parçalar halinde işleyerek bellek baskısını azaltın.

## Sıkça Sorulan Sorular

**S: Aspose.Words for Java'ı nasıl kurarım?**  
C: Yukarıda gösterilen Maven veya Gradle bağımlılığını ekleyin, ardından lisans dosyanızı projeye koyun ve kodda başlatın.

**S: Taslak düzeyleri ayarlamadan yer işaretlerini kullanabilir miyim?**  
C: Evet, ancak taslak düzeyleri olmadan PDF'in yer işareti bölmesi düz bir liste gösterir, bu da gezinmeyi zorlaştırır.

**S: Yer işaretleri ne kadar derine iç içe yerleştirilebilir?**  
C: Teknik olarak bir limit yok, ancak hiyerarşiyi kullanıcı okunabilirliği için makul (3‑4 seviye) tutun.

**S: Aspose çok büyük Word dosyalarını nasıl yönetir?**  
C: Kütüphane içeriği akış olarak işler ve bellek kullanımını düşük tutmak için `Document.optimizeResources()` gibi yöntemler sunar.

**S: PDF oluşturulduktan sonra yer işaretlerini düzenleyebilir miyim?**  
C: Evet, Aspose.PDF for Java kullanarak yer işareti başlıklarını, hedeflerini veya hiyerarşisini oluşturma sonrası değiştirebilirsiniz.

## Kaynaklar
- [Aspose.Words Dokümantasyonu](https://reference.aspose.com/words/java/)
- [En Son Sürümleri İndir](https://releases.aspose.com/words/java/)
- [Lisans Satın Al](https://purchase.aspose.com/buy)
- [Ücretsiz Deneme](https://releases.aspose.com/words/java/)
- [Geçici Lisans Başvurusu](https://purchase.aspose.com/temporary-license/)
- [Aspose Destek Forumu](https://forum.aspose.com/c/words/10)

---

**Last Updated:** 2026-04-02  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}