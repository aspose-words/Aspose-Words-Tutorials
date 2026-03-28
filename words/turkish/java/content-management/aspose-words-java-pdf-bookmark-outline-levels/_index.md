---
date: '2026-03-28'
description: Aspose.Words for Java kullanarak PDF'e yer imi eklemeyi ve iç içe yer
  imlerini yönetmeyi öğrenin. Belge gezinmesini net taslak seviyeleriyle artırın.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Aspose.Words Java ile PDF yer imleri ve anahat seviyeleri ekleyin
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java ile PDF yer imleri ve ana hat seviyeleri ekleme

## Giriş
Word belgelerini PDF'ye dönüştürürken düzenli kalan **PDF yer imleri ekleme** konusunda zorlanıyorsanız, doğru yerdesiniz. Bu öğreticide Aspose.Words for Java'yı kullanarak **PDF içinde iç içe yer imleri** oluşturmayı, ana hat seviyelerini atamayı ve temiz, gezilebilir bir PDF dosyası üretmeyi adım adım göstereceğiz.

**Öğrenecekleriniz**
- Projenizde Aspose.Words for Java'ı kurun  
- Bir Word belgesinden doğrudan **PDF içinde iç içe yer imleri** oluşturun  
- Yer imi ana hat seviyelerini hiyerarşik bir görünüm için yapılandırın  
- Son belgeyi düzgün yapılandırılmış yer imleriyle PDF olarak kaydedin  

### Hızlı Yanıtlar
- **PDF yer imleri eklemenin temel faydası nedir?** Büyük belgelerde gezinmeyi ve kullanıcı deneyimini iyileştirir.  
- **Java'da kolay PDF yer imi oluşturmayı sağlayan kütüphane hangisidir?** Aspose.Words for Java.  
- **Yer imi özelliklerini kullanmak için lisansa ihtiyacım var mı?** Değerlendirme için ücretsiz deneme çalışır; üretim için lisans gereklidir.  
- **Her yer imi için farklı ana hat seviyeleri ayarlayabilir miyim?** Evet, `PdfSaveOptions` içinde `BookmarksOutlineLevelCollection` kullanarak.  
- **Bu yöntem en son Aspose.Words sürümüyle uyumlu mu?** Kesinlikle – 25.3 ve üzeri sürümlerle çalışır.  

## “PDF yer imleri ekleme” nedir?
PDF yer imleri eklemek, PDF'nin gezinme bölmesinde belge içindeki belirli bölümlere yönlendiren tıklanabilir girişler eklemek anlamına gelir. Ana hat seviyeleriyle birleştirildiğinde, bu yer imleri belgenizin hiyerarşisini yansıtan ağaç benzeri bir yapı oluşturur.

## PDF'de iç içe yer imleri neden kullanılır?
İç içe yer imleri, okuyucuların yüksek seviyeli bölümlerden ayrıntılı alt bölümlere sayfaları kaydırmadan geçmesini sağlar. Bu, **hukuki sözleşmeler**, **teknik raporlar** ve **e‑öğrenme kılavuzları** gibi hızlı referansın kritik olduğu durumlarda özellikle değerlidir.

## Önkoşullar
- **Kütüphaneler ve Bağımlılıklar**: Aspose.Words for Java (versiyon 25.3 veya üzeri).  
- **Ortam**: JDK 8+ ve IntelliJ IDEA veya Eclipse gibi bir IDE.  
- **Bilgi**: Temel Java, Maven veya Gradle bilgisi.  

## Aspose.Words Kurulumu
Başlamak için, projenize gerekli bağımlılıkları ekleyin. İşte Maven ve Gradle ile nasıl yapılacağı:

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
Aspose.Words ticari bir üründür, ancak ücretsiz deneme ile başlayabilirsiniz:

1. **Ücretsiz Deneme** – Tam yetenekleri test etmek için [Aspose'un sürüm sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Geçici Lisans** – Kısa vadeli bir anahtara ihtiyacınız varsa [Aspose'un geçici lisans sayfasına](https://purchase.aspose.com/temporary-license/) başvurun.  
3. **Satın Alma** – Kalıcı bir lisansı [Aspose'un satın alma portalından](https://purchase.aspose.com/buy) edinin.

Lisans dosyasını edindikten sonra, tüm özelliklerin kilidini açmak için kodunuzda yükleyin.

## Uygulama Kılavuzu
Uygulamayı net, numaralı adımlara bölelim.

### Adım 1: Belge ve Builder'ı Başlatma
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Bu, içeriği ve yer imlerini dolduracağımız yeni bir Word belgesi oluşturur.

### Adım 2: İç İçe Yer İmleri Ekleme
#### İlk (üst) yer imini oluşturma
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### Üst yer iminin içine bir alt yer imi ekleme
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### Üst yer imini kapatma
```java
builder.endBookmark("Bookmark 1");
```

#### Üçüncü, bağımsız bir yer imi ekleme
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Adım 3: Yer İmi Ana Hat Seviyelerini Yapılandırma
#### `PdfSaveOptions` ayarlama
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### Hiyerarşi seviyelerini atama
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Belgeyi PDF olarak kaydetme
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

### Yaygın Sorunlar ve Çözümler
- **Yer imleri eksik** – Her `startBookmark`'ın eşleşen bir `endBookmark`'a sahip olduğundan emin olun.  
- **Yanlış ana hat hiyerarşisi** – Seviye numaralarını iki kez kontrol edin; daha düşük bir sayı, gezinme bölmesinde daha yüksek bir seviyeyi ifade eder.  
- **Büyük belgeler** – Bellek tüketimini azaltmak için kaydetmeden önce `doc.optimizeResources()` çağırın.

## Pratik Uygulamalar
1. **Hukuki Belgeler** – Maddelere ve alt maddelere hızlıca atlayın.  
2. **Yıllık Raporlar** – Bölümler, kısımlar ve içindekiler tabloları arasında gezin.  
3. **Eğitim Materyalleri** – Öğrencilere PDF içinde tıklanabilir bir müfredat sunun.

## Performans Düşünceleri
- Dönüştürmeden önce gereksiz görüntüleri veya gizli bölümleri kaldırın.  
- Bellek kullanımını düşük tutmak için çok büyük dosyalar için akış API'lerini kullanın.

## Sonuç
Artık **PDF yer imleri ekleme**, ana hat seviyelerini yapılandırma ve Aspose.Words for Java kullanarak iyi yapılandırılmış bir PDF oluşturma konusunda eksiksiz, üretime hazır bir yönteme sahipsiniz. Bu teknik, belge kullanılabilirliğini büyük ölçüde artırır ve PDF gezinmesi üzerinde ayrıntılı kontrol sağlar.

**Sonraki Adımlar** – PDF oluşturulduktan sonra ek yer imleri eklemek veya düzenlemek için bu yaklaşımı Aspose.PDF for Java ile birleştirmeyi deneyin.

## SSS Bölümü
1. **Aspose.Words for Java'ı nasıl kurarım?**  
   Maven veya Gradle bağımlılığı olarak ekleyin ve çalışma zamanında lisans dosyanızı yükleyin.  
2. **Yer imlerini ana hat seviyeleri olmadan kullanabilir miyim?**  
   Evet, ancak ana hat seviyeleri, gezinmeyi çok daha kolay hale getiren hiyerarşik bir görünüm sağlar.  
3. **Yer imi iç içeleme sınırları nelerdir?**  
   Katı bir sınır yoktur, ancak en iyi kullanıcı deneyimi için hiyerarşiyi mantıklı tutun.  
4. **Aspose büyük belgeleri nasıl yönetir?**  
   Kaynakları verimli bir şekilde akıtır; ancak çok büyük dosyalar için `optimizeResources()` çağırmalısınız.  
5. **PDF'yi kaydettikten sonra yer imlerini değiştirebilir miyim?**  
   Kesinlikle – dönüştürme sonrası yer imlerini düzenlemek için Aspose.PDF for Java'yı kullanın.

## Ek Sık Sorulan Sorular
**S: Bu teknik DOCX'ten PDF'ye dönüştürürken çalışır mı?**  
C: Evet, kaynak Word formatı ne olursa olsun aynı yer imi oluşturma adımları uygulanır.

**S: Yer imi için özel renkler veya simgeler ayarlamak mümkün mü?**  
C: Yer imi görünümü PDF görüntüleyici tarafından kontrol edilir; Aspose.Words hiyerarşi ve adlandırmaya odaklanır.

**S: Ana hat seviyeleri tüm PDF okuyucularda görünecek mi?**  
C: Çoğu modern okuyucu (Adobe Acrobat, Foxit, Chrome) Aspose.Words tarafından tanımlanan ana hat hiyerarşisine saygı gösterir.

## Kaynaklar
- [Aspose.Words Belgeleri](https://reference.aspose.com/words/java/)  
- [En Son Sürümleri İndir](https://releases.aspose.com/words/java/)  
- [Lisans Satın Al](https://purchase.aspose.com/buy)  
- [Ücretsiz Deneme](https://releases.aspose.com/words/java/)  
- [Geçici Lisans Başvurusu](https://purchase.aspose.com/temporary-license/)  
- [Aspose Destek Forumu](https://forum.aspose.com/c/words/10)

---

**Son Güncelleme:** 2026-03-28  
**Test Edilen:** Aspose.Words 25.3 for Java  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}