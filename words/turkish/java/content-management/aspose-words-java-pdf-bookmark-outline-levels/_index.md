---
date: '2026-04-11'
description: Aspose.Words kullanarak Java'da yer imleri ve anahat seviyeleriyle PDF
  kaydetmeyi öğrenin. Dönüştürme ipuçları, kod örnekleri ve sorun giderme içerir.
keywords:
- save pdf with bookmarks
- convert word pdf java
- aspose words java pdf
title: Aspose.Words Java Kullanarak Yer İmleriyle PDF Kaydet
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java Kullanarak Yer İmleriyle PDF Kaydet

## Giriş
Eğer net bir hiyerarşi yansıtan **yer imleriyle PDF kaydetmek** istiyorsanız, doğru yerdesiniz. Bu öğreticide bir Word belgesini PDF'ye dönüştürürken yer imi anahat seviyelerini yapılandıracağız, böylece ortaya çıkan PDF okuyucular ve gözden geçirenler için gezinmesi kolay olacaktır.  

**Öğrenecekleriniz**
- Aspose.Words for Java'ı nasıl kuracağınızı  
- Word belgesinde iç içe yer imleri nasıl oluşturacağınızı  
- PDF yer imlerinin mantıklı bir ağaçta görünmesi için anahat seviyelerini nasıl atayacağınızı  
- En son Aspose.Words API'sını kullanarak **yer imleriyle PDF kaydetmeyi** nasıl yapacağınızı  

### Hızlı Yanıtlar
- **Word'ı PDF'ye dönüştürürken yer imi ekleyebilir miyim?** Evet, Aspose.Words kaydetmeden önce tanımlamanıza izin verir.  
- **Bu özelliği kullanmak için lisansa ihtiyacım var mı?** Ücretsiz deneme değerlendirme için çalışır; bir lisans tam işlevselliği açar.  
- **Hangi Java sürümü gerekiyor?** Java 8 veya üzeri.  
- **Anahat seviyesi yapılandırması isteğe bağlı mı?** İsteğe bağlıdır ancak daha iyi gezinme için şiddetle tavsiye edilir.  
- **PDF yer imi hiyerarşisini koruyacak mı?** Kesinlikle – ayarladığınız seviyeler PDF'nin yer imi ağacını oluşturur.

### Ön Koşullar
Başlamadan önce, şunların olduğundan emin olun:

- **Kütüphaneler ve Bağımlılıklar**: Aspose.Words for Java (25.3 veya sonrası).  
- **Ortam**: JDK 8+ ve IntelliJ IDEA veya Eclipse gibi bir IDE.  
- **Temel Bilgi**: Java, Maven veya Gradle ve Word'deki yer imleri kavramına aşinalık.  

## Yer İmleri ve Anahat Seviyeleriyle PDF Nasıl Kaydedilir

### Aspose.Words Kurulumu
Projeye Maven veya Gradle kullanarak Aspose.Words kütüphanesini ekleyin.

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

#### Lisans Edinme
Aspose.Words ticari bir üründür, ancak ücretsiz deneme ile başlayabilirsiniz.

1. **Ücretsiz Deneme** – Tam yetenekleri test etmek için [Aspose'un sürüm sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Geçici Lisans** – Kısa vadeli değerlendirme için [Aspose'un geçici lisans sayfasına](https://purchase.aspose.com/temporary-license/) başvurun.  
3. **Satın Alma** – Kalıcı bir lisansı [Aspose satın alma portalından](https://purchase.aspose.com/buy) edinin.  

`.lic` dosyasını edindikten sonra, tüm özellikleri açmak için uygulama başlangıcında yükleyin.

### İç İçe Yer İmleri Oluşturma (Adım 1)
İlk olarak, bir Word belgesi oluşturun ve istediğiniz hiyerarşiyi yansıtan yer imlerini ekleyin.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

```java
builder.endBookmark("Bookmark 1");
```

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Yer İmi Anahat Seviyelerini Yapılandırma (Adım 2)
Şimdi Aspose.Words'a bu yer imlerinin PDF'nin yer imi bölmesinde nasıl görüneceğini söyleyin.

```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

Oluşturulan PDF'yi açtığınızda, Word belgesinde tanımladığınız yapıyı yansıtan üç seviyeli bir yer imi ağacı göreceksiniz.

## Java'da Word'ı PDF'ye dönüştürmek için Aspose.Words Neden Kullanılır?
- **Yüksek doğruluk**: Düzen, yazı tipleri ve karmaşık öğeler korunur.  
- **Programatik kontrol**: Yer imlerini, anahat seviyelerini ve birçok diğer PDF özelliğini doğrudan Java'dan ekleyebilir veya değiştirebilirsiniz.  
- **Performans**: Büyük belgeleri verimli bir şekilde işler, özellikle aşağıdaki performans ipuçlarını izlerseniz.  

## Pratik Uygulamalar
1. **Hukuki sözleşmeler** – Maddeleri ve alt maddeleri hızlıca gezinin.  
2. **Yıllık raporlar** – Okuyuculara tıklanabilir bir içindekiler tablosu sunun.  
3. **E‑öğrenme modülleri** – Bölümleri, alt bölümleri ve sınavları tek bir PDF'de düzenleyin.  

## Performans Düşünceleri
- Kaydetmeden önce kullanılmayan stilleri veya gizli bölümleri kaldırarak PDF'yi hafif tutun.  
- Çok büyük belgeler için bellek tüketimini azaltmak amacıyla `doc.optimizeResources()` kullanın.  

## Yaygın Sorunlar ve Çözümler
- **Yer imleri eksik** – Her `startBookmark`'ın eşleşen bir `endBookmark`'a sahip olduğunu doğrulayın.  
- **Yanlış hiyerarşi** – Anahat seviyesi sayıların ebeveyn‑çocuk ilişkisini yansıttığından emin olun (düşük sayı = üst seviye).  
- **Lisans uygulanmadı** – Herhangi bir Aspose.Words API çağrısından önce lisans dosyasını yükleyin; aksi takdirde deneme filigranı alırsınız.  

## SSS

**S: Aspose.Words for Java'ı nasıl kurarım?**  
C: Yukarıda gösterilen Maven veya Gradle bağımlılığını ekleyin, ardından lisans dosyanızı çalışma zamanında yükleyin.

**S: Anahat seviyeleri ayarlamadan yer imleri oluşturabilir miyim?**  
C: Evet, ancak PDF düz bir yer imi listesi gösterir ve gezinmeyi zorlaştırır.

**S: Yer imleri ne kadar derine iç içe yerleştirilebilir?**  
C: Teknik olarak hayır, ancak hiyerarşiyi okunabilir tutun—genellikle üç ila dört seviye en iyisidir.

**S: Aspose.Words büyük Word dosyalarını verimli bir şekilde işler mi?**  
C: İçeriği akış olarak işler ve optimizasyon yöntemleri sunar; ancak çok büyük belgeleri bölmeyi düşünün.

**S: PDF kaydedildikten sonra yer imlerini düzenleyebilir miyim?**  
C: Evet, dönüşüm sonrası yer imlerini değiştirmek için Aspose.PDF for Java kullanabilirsiniz.

## Kaynaklar
- [Aspose.Words Dokümantasyonu](https://reference.aspose.com/words/java/)  
- [En Son Sürümleri İndir](https://releases.aspose.com/words/java/)  
- [Lisans Satın Al](https://purchase.aspose.com/buy)  
- [Ücretsiz Deneme](https://releases.aspose.com/words/java/)  
- [Geçici Lisans Başvurusu](https://purchase.aspose.com/temporary-license/)  
- [Aspose Destek Forumu](https://forum.aspose.com/c/words/10)

---

**Son Güncelleme:** 2026-04-11  
**Test Edilen Versiyon:** Aspose.Words 25.3 for Java  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}