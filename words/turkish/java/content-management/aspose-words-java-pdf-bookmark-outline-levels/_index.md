---
date: '2026-03-31'
description: Java'da iç içe yer imleri oluşturmayı ve Aspose.Words kullanarak yer
  imli PDF oluşturmayı öğrenin. Java'da Word'ü PDF'ye dönüştürmek için adım adım rehber.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Java ile Aspose.Words PDF Seviyeleri Kullanarak İç İçe Yer İmleri Oluşturma
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words PDF Düzeyleriyle Java'da İç İçe Yer İşaretleri Oluşturma

## Giriş
If you need to **create nested bookmarks Java**‑style while converting Word documents to PDFs, you’re in the right place. In this tutorial we’ll walk through using Aspose.Words for Java to generate PDF with bookmarks that are neatly organized with outline levels. By the end you’ll have a professional‑looking PDF where readers can jump to any section instantly.

**Neler Öğreneceksiniz**
- Aspose.Words for Java'ı nasıl kurulur  
- Bir Word belgesinde iç içe yer işaretleri nasıl oluşturulur  
- Yer işareti taslak düzeylerini net bir hiyerarşi için nasıl yapılandırılır  
- Belgeyi yapılandırılmış yer işaretleriyle PDF olarak nasıl dışa aktarılır  

### Hızlı Yanıtlar
- **Belge oluşturmak için birincil sınıf nedir?** `DocumentBuilder`  
- **Hangi yöntem bir taslak düzeyi ekler?** `outlineLevels.add(bookmarkName, level)`  
- **Maven veya Gradle kullanabilir miyim?** Evet, her ikisi de desteklenir (kod parçacıklarına bakın)  
- **PDF taslak düzeyleri için lisansa ihtiyacım var mı?** Bir lisans tam işlevselliği açar; ücretsiz deneme değerlendirme için çalışır  
- **Bu yaklaşım büyük raporlar için uygun mu?** Evet, ancak performans bölümündeki bellek‑optimizasyon ipuçlarını göz önünde bulundurun  

## “create nested bookmarks java” nedir?
İç içe yer işaretleri oluşturmak, bir yer işaretini başka birinin içine yerleştirerek ebeveyn‑çocuk hiyerarşisi oluşturmak anlamına gelir. Belge PDF olarak kaydedildiğinde, bu hiyerarşiler PDF'in yer işareti bölmesinde katlanabilir girişler haline gelir ve okuyucular için gezinmeyi sezgisel kılar.

## Neden PDF'ye yer işaretleri ekleyerek oluşturmalıyız?
PDF'lere yer işaretleri eklemek kullanıcı deneyimini artırır, özellikle yasal sözleşmeler, uzun raporlar veya e‑kitaplar için. Okuyucular sayfaları kaydırmadan bölümlere, alt bölümlere veya belirli maddelere anında atlayabilir.

## Önkoşullar
- **Kütüphaneler ve Bağımlılıklar**: Aspose.Words for Java (sürüm 25.3 ve üzeri).  
- **Ortam**: JDK 8 ve üzeri, IntelliJ IDEA veya Eclipse gibi IDE.  
- **Beceriler**: Temel Java, Maven veya Gradle hakkında bilgi.  

### Aspose.Words Kurulumu
Kütüphaneyi projenize Maven veya Gradle kullanarak ekleyin.

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

#### Lisans Alımı
Aspose.Words ticari bir üründür, ancak ücretsiz deneme ile başlayabilirsiniz.

1. **Ücretsiz Deneme**: Tam yetenekleri test etmek için [Aspose's release page](https://releases.aspose.com/words/java/) adresinden indirin.  
2. **Geçici Lisans**: Gerekiyorsa [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/) üzerinden geçici lisans başvurusu yapın.  
3. **Satın Alma**: Sürekli kullanım için [Aspose’s purchasing portal](https://purchase.aspose.com/buy) üzerinden lisans satın alın.

Lisansı kodunuzda başlatarak tüm özelliklerin kilidini açın.

## Uygulama Kılavuzu
Çözümü net, numaralı adımlara böleceğiz.

### Adım 1: Bir Belge ve Builder Oluşturma
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Bu, içeriği ve yer işaretlerini eklemek için kullanacağınız boş bir Word belgesi ve bir builder nesnesi oluşturur.

### Adım 2: İç İçe Yer İşaretleri Ekleme
#### Birincil yer işareti
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### Birincil yer işaretinin içindeki iç içe yer işareti
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### Dış yer işaretini kapatma
```java
builder.endBookmark("Bookmark 1");
```

#### Ek bağımsız yer işareti
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Adım 3: Yer İşareti Taslak Düzeylerini Yapılandırma
#### PDF kaydetme seçeneklerini ayarlama
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### Hiyerarşi düzeylerini atama
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Tanımlı taslakla PDF olarak kaydetme
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

### Yaygın Sorunlar ve Çözümler
- **Yer İşaretleri Eksik** – Her `startBookmark` bir eşleşen `endBookmark` içermelidir.  
- **Yanlış Düzeyler** – Düzey numaralarını iki kez kontrol edin; PDF'deki ebeveyn‑çocuk ilişkisini tanımlar.  
- **Büyük Belgeler** – Bellek tüketimini azaltmak için kaydetmeden önce `Document.optimizeResources()` kullanın.  

## Pratik Uygulamalar
1. **Yasal Sözleşmeler** – Maddelere ve alt maddelere hızlıca atlayın.  
2. **Finansal Raporlar** – Bölümler, tablolar ve grafikler arasında gezin.  
3. **Eğitim Materyalleri** – e‑kitaplar için tıklanabilir bir içindekiler tablosu sağlayın.  

## Performans Düşünceleri
- Kaydetmeden önce kullanılmayan stilleri veya bölümleri kaldırın.  
- Çok büyük dosyalar için, yüksek bellek kullanımını önlemek amacıyla PDF çıktısını akış olarak üretmeyi düşünün.  

## Sonuç
Artık **create nested bookmarks Java** nasıl oluşturulur ve Aspose.Words kullanarak taslak düzeylerini nasıl yapılandırılır biliyorsunuz. Bu teknik, sade bir PDF'i kullanıcı dostu, gezilebilir bir belgeye dönüştürür—profesyonel raporlar, sözleşmeler ve e‑kitaplar için mükemmeldir.

**Sonraki Adımlar**: Yer işaretlerine özel simgeler eklemeyi deneyin veya bu iş akışını birden fazla Word dosyasını aynı anda dönüştüren toplu‑işlem hizmetine entegre edin.

## Sıkça Sorulan Sorular

**S: Aspose.Words for Java nasıl kurulur?**  
C: Daha önce gösterilen Maven veya Gradle bağımlılığını ekleyin, ardından lisans dosyanızı proje kaynaklarına yerleştirin.

**S: Taslak düzeyleri olmadan PDF oluşturabilir miyim?**  
C: Evet, ancak PDF düz yer işaretleri içerir ve bunlar gezinmesi daha zordur.

**S: Yer işaretleri ne kadar derine iç içe yerleştirilebilir?**  
C: Teknik olarak bir sınırlama yok, ancak okunabilirlik için hiyerarşiyi makul tutun.

**S: Aspose.Words çok büyük belgeleri verimli bir şekilde yönetir mi?**  
C: Belleği iyi yönetir, özellikle kaydetmeden önce `optimizeResources()` çağırdığınızda.

**S: PDF oluşturulduktan sonra yer işaretlerini düzenleyebilir miyim?**  
C: Evet, Aspose.PDF for Java kullanarak yer işareti başlıklarını veya hiyerarşisini oluşturma sonrası değiştirebilirsiniz.

## Kaynaklar
- [Aspose.Words Dokümantasyonu](https://reference.aspose.com/words/java/)
- [En Son Sürümleri İndir](https://releases.aspose.com/words/java/)
- [Lisans Satın Al](https://purchase.aspose.com/buy)
- [Ücretsiz Deneme](https://releases.aspose.com/words/java/)
- [Geçici Lisans Başvurusu](https://purchase.aspose.com/temporary-license/)
- [Aspose Destek Forumu](https://forum.aspose.com/c/words/10)

---

**Son Güncelleme:** 2026-03-31  
**Test Edilen Sürüm:** Aspose.Words 25.3 for Java  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}