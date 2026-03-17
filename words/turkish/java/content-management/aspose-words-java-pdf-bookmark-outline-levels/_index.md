---
date: '2026-03-17'
description: Aspose.Words for Java kullanarak yer imleri eklemeyi, anahat seviyelerini
  ayarlamayı ve yer imli PDF kaydetmeyi öğrenin.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: PDF'lerde Yer İmleri ve Seviyeler Nasıl Eklenir – Aspose.Words Java
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java Kullanarak PDF'lerde Yer İmi Taslak Seviyelerini Yönetme

## Giriş
Bu rehberde, Aspose.Words for Java kullanarak Word belgelerini PDF'ye dönüştürürken **yer imleri eklemeyi** ve taslak seviyelerini ayarlamayı öğreneceksiniz. Dönüştürme sırasında yer imlerini yönetmekte zorlanıyor musunuz? Bu öğretici, iç içe yer imleri oluşturmayı, hiyerarşilerini yapılandırmayı ve kolay gezilebilen bir PDF kaydetmeyi adım adım gösterir.

**Öğrenecekleriniz**
- Aspose.Words for Java'ı kurma ve kullanma
- Word belgelerinde iç içe yer imleri oluşturma
- Daha iyi organizasyon için yer imi taslak seviyelerini yapılandırma
- Belgeyi yapılandırılmış yer imleriyle PDF olarak kaydetme

### Önkoşullar
Başlamadan önce şunların olduğundan emin olun:
- **Kütüphaneler ve Bağımlılıklar**: Aspose.Words for Java (sürüm 25.3 veya daha yeni).
- **Ortam Kurulumu**: Makinenizde yüklü bir JDK ve IntelliJ IDEA veya Eclipse gibi uyumlu bir IDE.
- **Bilgi Önkoşulları**: Java programlamaya temel bir anlayış ve Maven ya da Gradle yapı sistemlerine aşinalık.

## Hızlı Yanıtlar
- **Yer imleri eklemenin temel yolu nedir?** `DocumentBuilder.startBookmark()` ve `endBookmark()` metodlarını kullanın.  
- **PDF yer imleri için hiyerarşi ayarlayabilir miyim?** Evet—`PdfSaveOptions` üzerinden `BookmarksOutlineLevelCollection` yapılandırın.  
- **Yer imli PDF oluşturmak için lisansa ihtiyacım var mı?** Test için ücretsiz deneme çalışır; üretim için kalıcı bir lisans gereklidir.  
- **Bu süreci en iyi tanımlayan anahtar kelime nedir?** *how to add bookmarks* (birincil).  
- **Eksik yer imleri için yerleşik bir sorun giderme var mı?** Evet—yer imi başlangıç/bitiş eşleşmesini ve taslak seviyesi atamalarını kontrol edin.

## PDF'lerde Yer İmi Eklemek
Aspose.Words ile yer imi oluşturmak oldukça basittir. Aşağıda uygulamayı net adımlara ayırıyoruz.

### Aspose.Words Kurulumu
Projeye gerekli bağımlılıkları ekleyerek başlayın.

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

### Lisans Alımı
Aspose.Words ticari bir üründür, ancak özelliklerini keşfetmek için ücretsiz bir deneme ile başlayabilirsiniz. İşte adımlar:
1. **Ücretsiz Deneme**: Tam yetenekleri test etmek için [Aspose'un sürüm sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Geçici Lisans**: Gerekirse [Aspose'un geçici lisans sayfasından](https://purchase.aspose.com/temporary-license/) geçici bir lisans başvurusu yapın.  
3. **Satın Alma**: Sürekli kullanım için [Aspose'un satın alma portalından](https://purchase.aspose.com/buy) lisans satın alın.

Lisans dosyanızı aldıktan sonra Aspose.Words'un tüm özelliklerini açmak için projenizde başlatın.

## İç İçe Yer İmleri Oluşturma
**Genel Bakış**: Aspose.Words for Java kullanarak bir Word belgesi içinde iç içe yer imleri oluşturmayı öğrenin.

### Adım 1: Belge ve Builder'ı Başlatma
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Bu, içerik eklemeye başlayabileceğiniz Word belge ortamını ayarlar.

### Adım 2: İç İçe Yer İmleri Eklemek
Öncelikle bir birincil yer imi oluşturun:
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

Şimdi, onun içinde başka bir yer imi iç içe yerleştirin:
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

Dış yer imi tamamlayın:
```java
builder.endBookmark("Bookmark 1");
```

### Adım 3: Ek Yer İmleri Eklemek
Gerektikçe yer imleri eklemeye devam edin. Örneğin, ayrı bir üçüncü yer imi:
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## Yer İmi Taslak Seviyelerini Yapılandırma
**Genel Bakış**: PDF içinde daha iyi gezinme için yer imlerinin taslak seviyelerini ayarlayarak düzenleyin.

### Adım 1: PdfSaveOptions'ı Ayarlama
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
Bu kod parçacığı, belgeyi düzenli yer imleriyle PDF olarak kaydetmek için kullanacağınız seçenekleri başlatır.

### Adım 2: Taslak Seviyelerini Eklemek
Her yer imi için seviyeler atayın; bu, hiyerarşilerini belirleyecektir:
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

### Adım 3: Belgeyi Kaydetme
Son olarak, bu ayarlarla belgenizi PDF olarak kaydedin:
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Sorun Giderme İpuçları
- **Eksik Yer İmleri**: Her `startBookmark`'ın karşılık gelen bir `endBookmark`'ı olduğundan emin olun.  
- **Yanlış Seviyeler**: Kodunuzdaki ebeveyn‑çocuk ilişkilerini kontrol ederek hiyerarşiyi doğrulayın.  
- **pdf bookmark troubleshooting**: Yer imleri oluşturulan PDF'de görünmüyorsa, `PdfSaveOptions`'ın `doc.save()`'e doğru şekilde geçirildiğini iki kez kontrol edin.

## Pratik Uygulamalar
Bu bilgiyi uygulayabileceğiniz bazı senaryolar:
1. **Hukuki Belgeler** – Hızlı referans için bölümleri ve alt bölümleri düzenleyin.  
2. **Raporlar** – Karmaşık veri yapılarında gezinmek için iç içe yer imleri kullanın.  
3. **Eğitim Materyalleri** – Bölümleri, alt‑bölümleri ve önemli noktaları verimli bir şekilde yapılandırın.  

## Performans Düşünceleri
- Kaydetmeden önce gereksiz içeriği kaldırarak belge boyutunu optimize edin.  
- Özellikle **word to pdf bookmarks** dönüşümleri için büyük belgelerle çalışırken bellek kullanımını etkili bir şekilde yönetin.

## Sonuç
Artık Aspose.Words for Java kullanarak **yer imleri eklemeyi** ve taslak seviyelerini yapılandırmayı öğrendiniz. Bu beceri, PDF'lerinizin gezinilebilirliğini büyük ölçüde artırır, onları daha kullanıcı‑dostu ve profesyonel hâle getirir.

**Sonraki Adımlar**: Farklı belge yapılarıyla denemeler yapın veya bu işlevi daha büyük bir uygulamaya entegre ederek faydalarını gerçek ortamda görün.

## SSS Bölümü
1. **Aspose.Words for Java nasıl kurulur?**  
   - Maven veya Gradle aracılığıyla bağımlılık olarak ekleyin, ardından lisans dosyanızı ayarlayın.  
2. **Yer imlerini taslak seviyeleri olmadan kullanabilir miyim?**  
   - Evet, ancak taslak seviyeleri PDF'lerde gezinmeyi iyileştirir.  
3. **Yer imi iç içeleme sınırları nelerdir?**  
   - Kesin bir sınır yoktur, ancak kullanıcıların okunabilirliğini ve yapıyı göz önünde bulundurun.  
4. **Aspose büyük belgeleri nasıl yönetir?**  
   - Kaynakları verimli bir şekilde yönetir, ancak çok büyük dosyalar için optimizasyon önerilir.  
5. **PDF kaydedildikten sonra yer imlerini değiştirebilir miyim?**  
   - Evet, dönüşüm sonrası yer imlerini düzenlemek için Aspose.PDF for Java kullanılabilir.  

**Ek Soru‑Cevap**
- **S: Bu yöntem Word‑to‑PDF yer imleri için de çalışır mı?**  
  C: Kesinlikle – Word'ü PDF'ye dönüştürürken aynı yer imi oluşturma mantığı uygulanır.  
- **S: Tek bir kod satırıyla yer imli PDF nasıl oluşturulur?**  
  C: `DocumentBuilder` çağrılarını zincirleyip yapılandırılmış `PdfSaveOptions`'ı `doc.save()`'e geçirerek.

## Kaynaklar
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)
- [Download Latest Releases](https://releases.aspose.com/words/java/)
- [Purchase a License](https://purchase.aspose.com/buy)
- [Free Trial](https://releases.aspose.com/words/java/)
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

---

**Son Güncelleme:** 2026-03-17  
**Test Edilen Versiyon:** Aspose.Words 25.3 for Java  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}