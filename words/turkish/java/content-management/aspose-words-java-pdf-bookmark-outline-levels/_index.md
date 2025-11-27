---
date: '2025-11-27'
description: Java'da Aspose.Words kullanarak yer imleri oluşturmayı, yer imli PDF
  oluşturmayı ve Word'ü PDF'ye dönüştürmeyi öğrenin. Bu kılavuz, iç içe yer imleri
  ve anahat seviyelerini kapsar.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
language: tr
title: Aspose.Words Java ile PDF'lerde Yer İmleri Oluşturma ve Taslak Seviyelerini
  Ayarlama
url: /java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java Kullanarak PDF'lerde Yer İmleri Oluşturma ve Ana Hat Seviyelerini Ayarlama

## Giriş
Word belgesini PDF'ye dönüştürürken **yer imleri oluşturma** konusunda zorlandığınız olduysa, doğru yerdesiniz. Bu öğreticide, yer imleriyle bir PDF oluşturma, bunları iç içe yerleştirme ve ana hat seviyelerini atama sürecini adım adım inceleyeceğiz, böylece son PDF kolayca gezilebilir. Sonunda, **Word PDF Java**'ı dönüştürme‑stilinde temiz bir yer imi hiyerarşisiyle herhangi bir PDF görüntüleyicide çalışan bir PDF oluşturabileceksiniz.

### Öğrenecekleriniz
- Aspose.Words for Java'ı geliştirme ortamınıza kurun.  
- **Yer imleri oluşturma**'ı programlı olarak ve iç içe yerleştirmeyi.  
- Belge yapısını yansıtan yer imleriyle PDF oluşturmak için yer imi ana hat seviyelerini yapılandırın.  
- Yer imi hiyerarşisini koruyarak Word dosyasını PDF olarak kaydedin.

## Hızlı Yanıtlar
- **Belge oluşturmak için birincil sınıf nedir?** `DocumentBuilder`.  
- **Yer imi hiyerarşisini kontrol eden seçenek hangisidir?** `PdfSaveOptions` içinde `BookmarksOutlineLevelCollection`.  
- **Maven veya Gradle kullanabilir miyim?** Evet – ikisi de aşağıda gösterilmiştir.  
- **Lisans gerekli mi?** Test için ücretsiz deneme çalışır; üretim için kalıcı bir lisans gereklidir.  
- **Bu yaklaşım büyük belgeler için uygun mu?** Evet, ancak bellek optimizasyon tekniklerini (ör. kullanılmayan kaynakları kaldırma) göz önünde bulundurun.  

### Önkoşullar
Başlamadan önce şunların olduğundan emin olun:

- **Kütüphaneler ve Bağımlılıklar** – Aspose.Words for Java (25.3 ve üzeri).  
- **Ortam** – JDK 8 ve üzeri, ve IntelliJ IDEA veya Eclipse gibi bir IDE.  
- **Temel Bilgi** – Java programlama temelleri ve Maven veya Gradle hakkında bilgi.  

## Aspose.Words Kurulumu
Başlamak için, projenize gerekli bağımlılıkları ekleyin. Aspose.Words'ı Maven veya Gradle kullanarak nasıl ekleyebileceğiniz aşağıdadır:

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
Aspose.Words ticari bir kütüphanedir, ancak ücretsiz deneme ile başlayabilirsiniz:

1. **Ücretsiz Deneme** – [Aspose sürüm sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Geçici Lisans** – Kısa vadeli bir anahtara ihtiyacınız varsa [geçici‑lisans sayfasına](https://purchase.aspose.com/temporary-license/) başvurun.  
3. **Tam Lisans** – Üretim kullanımı için [Aspose satın alma portalından](https://purchase.aspose.com/buy) satın alın.  

Lisans dosyasını edindikten sonra, tüm özellikleri açmak için uygulama başlangıcında yükleyin.

## Aspose.Words Java ile PDF'lerde Yer İmleri Oluşturma
Aşağıda uygulamayı net, numaralı adımlara bölüyoruz. Her adım kısa bir açıklama ve ardından (değiştirilmemiş) orijinal kod bloğunu içerir.

### Adım 1: Bir Document ve DocumentBuilder Başlatma
Yeni bir `Document` örneği ve içerik ve yer imleri eklememizi sağlayan bir `DocumentBuilder` ile başlarız.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Adım 2: İlk (Üst) Yer İmini Ekleme
Daha sonra bir alt yer imi içerecek üst‑seviye bir yer imi oluşturun.

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

### Adım 3: Üst Yer İmi İçine Bir Alt Yer İmi İç İçe Yerleştirme
Şimdi, birincisinin içinde yer alan ikinci bir yer imi ekleyerek iç içe yerleştirmeyi gösteriyoruz.

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

### Adım 4: Üst Yer İmini Kapatma
İç içe içeriğin ardından dış yer imi tamamlanır.

```java
builder.endBookmark("Bookmark 1");
```

### Adım 5: Bağımsız Üçüncü Bir Yer İmi Ekleme
Her zaman iç içe olmayan daha fazla yer imi ekleyebilirsiniz.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## Yer İmi Ana Hat Seviyelerini Yapılandırma
Yer imleri yerleştirildikten sonra, Aspose.Words'a bu yer imlerinin PDF'in ana hatında (sol taraftaki gezinme panelinde) nasıl görüneceğini söyleriz.

### Adım 6: PdfSaveOptions Hazırlama
`PdfSaveOptions` bize ana hat ayarlarına erişim sağlar.

```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

### Adım 7: Hiyerarşi Seviyelerini Atama
Her yer imi bir tam sayı seviyesi alır; daha düşük sayılar hiyerarşide daha üstte olur.

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

### Adım 8: Belgeyi PDF Olarak Kaydetme
Son olarak, yer imi ana hatını koruyarak Word belgesini PDF olarak dışa aktarın.

```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Neden Bu Yaklaşımı Kullanarak Yer İmleriyle PDF Oluşturmalısınız?
- **Profesyonel Navigasyon** – Okuyucular bölümlere doğrudan atlayabilir, büyük raporlar veya yasal sözleşmelerde kullanılabilirliği artırır.  
- **Tam Kontrol** – Hiyerarşiyi PDF görüntüleyici değil, siz belirlersiniz.  
- **Çapraz Platform** – Saf Java olduğu için Windows, Linux ve macOS'ta aynı şekilde çalışır.  

## Yaygın Sorunlar ve Çözümler
| Belirti | Muhtemel Neden | Çözüm |
|---|---|---|
| PDF'de eksik yer imleri | Eşleşen `endBookmark` olmadan bir `startBookmark` | Her `startBookmark`'ın karşılık gelen bir `endBookmark`'a sahip olduğundan emin olun. |
| Yanlış hiyerarşi | Ana hat seviyeleri sırasız atanmış | Üst yer imlerinin, alt yer imlerinden daha düşük seviye numaralarına sahip olduğundan emin olun. |
| Lisans uygulanmadı | Belge oluşturulmadan önce lisans dosyası yüklenmemiş | Lisansı uygulamanızın çok başında yükleyin (`License license = new License(); license.setLicense("Aspose.Words.lic");`). |

## Pratik Uygulamalar
1. **Hukuki Belgeler** – Maddelere, eklere ve ek bölümlere hızlıca geçiş.  
2. **Finansal Raporlar** – Gelir Tablosu, Bilanço ve Notlar gibi bölümler arasında atlama.  
3. **E‑Öğrenme Materyalleri** – PDF ana hatını yansıtan bir içindekiler tablosu sağlayın.  

## Performans Düşünceleri
- **Bellek Yönetimi** – Çok büyük Word dosyaları için, kaydetmeden önce `doc.cleanup()` çağırmayı düşünün.  
- **Kaynak Optimizasyonu** – PDF boyutunu küçük tutmak için kullanılmayan resimleri veya stilleri kaldırın.  

## Sık Sorulan Sorular

**S: Aspose.Words for Java'ı nasıl kurarım?**  
C: Yukarıda gösterilen Maven veya Gradle bağımlılığını ekleyin, ardından lisans dosyanızı sınıf yoluna koyun ve çalışma zamanında yükleyin.

**S: Ana hat seviyeleri ayarlamadan yer imleri oluşturabilir miyim?**  
C: Evet, ancak PDF görüntüleyici onları düz bir liste olarak gösterir, bu da karmaşık belgelerde gezinmeyi zorlaştırabilir.

**S: Yer imleri ne kadar derin iç içe yerleştirilebilir?**  
C: Teknik olarak bir limit yok, ancak çoğu PDF görüntüleyici rahatlıkla 9 seviyeye kadar destekler. Hiyerarşiyi okuyucular için mantıklı tutun.

**S: Aspose çok büyük Word dosyalarını nasıl yönetir?**  
C: Kütüphane içeriği akış olarak işler ve bellek kullanımını azaltmak için `Document.optimizeResources()` gibi yöntemler sunar.

**S: PDF oluşturulduktan sonra yer imlerini düzenleyebilirim?**  
C: Kesinlikle – mevcut bir PDF'de yer imlerini eklemek, kaldırmak veya yeniden adlandırmak için Aspose.PDF for Java kullanabilirsiniz.

## Kaynaklar
- [Aspose.Words Belgeleri](https://reference.aspose.com/words/java/)  
- [En Son Sürümleri İndir](https://releases.aspose.com/words/java/)  
- [Lisans Satın Al](https://purchase.aspose.com/buy)  
- [Ücretsiz Deneme](https://releases.aspose.com/words/java/)  
- [Geçici Lisans Başvurusu](https://purchase.aspose.com/temporary-license/)  
- [Aspose Destek Forumu](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Son Güncelleme:** 2025-11-27  
**Test Edilen:** Aspose.Words 25.3 for Java  
**Yazar:** Aspose