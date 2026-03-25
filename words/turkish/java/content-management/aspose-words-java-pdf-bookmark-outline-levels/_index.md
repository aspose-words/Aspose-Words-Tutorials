---
date: '2026-03-25'
description: Aspose.Words for Java kullanarak yer imleri oluşturmayı ve yer imli PDF
  üretmeyi öğrenin. Bu adım adım kılavuz, iç içe yer imleri, anahat seviyeleri ve
  PDF dışa aktarmayı kapsar.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Aspose.Words for Java ile PDF'lerde Yer İmleri Nasıl Oluşturulur
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# PDF'lerde Aspose.Words Java Kullanarak Yer İmi Taslak Seviyelerini Yönetme

## Giriş
PDF'lerinizi kolayca gezilebilir hâle getirecek **how to create bookmarks** ihtiyacınız varsa doğru yerdesiniz. Bu öğreticide Aspose.Words for Java kurulumunu, iç içe yer imleri oluşturmayı, taslak seviyelerini atamayı ve sonunda **generating PDF with bookmarks** profesyonel ve kullanıcı dostu bir şekilde nasıl yapılacağını adım adım göstereceğiz. Sonunda, herhangi bir Java projesine ekleyebileceğiniz yeniden kullanılabilir bir desen elde edeceksiniz.

**Öğrenecekleriniz**
- Aspose.Words for Java'ı kurun ve lisanslayın  
- Bir Word belgesinde iç içe yer imleri oluşturun  
- Yer imi taslak seviyelerini hiyerarşik gezinme için yapılandırın  
- Belgeyi düzgün yapılandırılmış yer imleriyle PDF olarak kaydedin  

### Hızlı Yanıtlar
- **Belge oluşturmak için birincil sınıf nedir?** `DocumentBuilder`  
- **Yer imlerini iç içe yerleştirebilir miyim?** Evet, üst öğeyi sonlandırmadan önce yeni bir yer imi başlatmanız yeterlidir.  
- **Taslak seviyelerini nasıl ayarlarsınız?** `PdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels()` kullanın.  
- **PDF dışa aktarımı için lisansa ihtiyacım var mı?** Deneme sürümü çalışır, ancak lisans değerlendirme sınırlamalarını kaldırır.  
- **Bu öğreticinin hedeflediği anahtar kelime ifadesi nedir?** *how to create bookmarks*  

## Aspose.Words'da “how to create bookmarks” nedir?
Yer imleri, bir Word belgesi içinde adlandırılmış konumlardır ve PDF taslak bölmesinde tıklanabilir girişler haline gelir. Okuyucuların bölümlere, tablolara veya şekillere kaydırma yapmadan doğrudan atlamasını sağlar.

## Neden PDF'yi yer imleriyle oluşturmalısınız?
PDF oluşturulurken yer imlerini gömmek, sonradan işleme adımını ortadan kaldırır, erişilebilirliği artırır ve yasal ya da teknik belgeler için temiz, aranabilir bir yapı sunar.

## Önkoşullar
- **Kütüphaneler ve Bağımlılıklar**: Aspose.Words for Java (versiyon 25.3 veya üzeri).  
- **Ortam**: JDK 8 veya daha yenisi, IntelliJ IDEA/Eclipse, ve Maven veya Gradle.  
- **Bilgi**: Temel Java, Maven/Gradle yapı dosyaları ve PDF kavramlarına aşinalık.  

## Aspose.Words Kurulumu
Başlamak için projenize gerekli bağımlılıkları ekleyin. Maven ve Gradle kullanarak nasıl yapacağınız aşağıdadır:

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
Aspose.Words ticari bir üründür, ancak özelliklerini keşfetmek için ücretsiz bir deneme ile başlayabilirsiniz. Aşağıdaki adımları izleyin:

1. **Ücretsiz Deneme**: Tam özellikleri test etmek için [Aspose'un sürüm sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Geçici Lisans**: Gerekiyorsa [Aspose'un geçici lisans sayfasından](https://purchase.aspose.com/temporary-license/) geçici lisans başvurusu yapın.  
3. **Satın Alma**: Sürekli kullanım için [Aspose'un satın alma portalından](https://purchase.aspose.com/buy) lisans satın alın.

Lisans dosyanızı aldıktan sonra, Aspose.Words'un tüm özelliklerini açmak için projenizde başlatın.

## Uygulama Kılavuzu
Uygulamayı iki mantıksal bölüme ayıracağız: iç içe yer imleri oluşturma ve taslak seviyelerini yapılandırma.

### Word Belgesinde Yer İmleri Nasıl Oluşturulur
**Genel Bakış** – Bu bölüm, daha sonra PDF hiyerarşisi olarak dışa aktarılabilecek **how to create bookmarks** için gereken tam kodu gösterir.

#### Adım 1: Belge ve Builder'ı Başlatma
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
`Document` nesnesi Word dosyasını temsil eder, `DocumentBuilder` ise metin, resim ve yer imleri eklemenizi sağlar.

#### Adım 2: İç İçe Yer İmleri Ekleme
İlk olarak bir birincil yer imi oluşturun:
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
Şimdi ilk yer iminin içine başka bir yer imi ekleyin:
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
Dış yer imi kapatın:
```java
builder.endBookmark("Bookmark 1");
```

#### Adım 3: Ek Bağımsız Yer İmleri Ekleyin
İhtiyacınız kadar ekleyebilirsiniz. Örneğin, ayrı bir üçüncü yer imi:
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Yer İmleri ve Taslak Seviyeleriyle PDF Nasıl Oluşturulur
**Genel Bakış** – Word belgesinde yer imleri oluşturulduktan sonra, PDF olarak kaydetmeden önce taslak hiyerarşisini yapılandırıyoruz.

#### Adım 1: PdfSaveOptions Ayarlama
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
Bu seçenekler, Aspose.Words'un Word yer imlerini PDF taslak girişlerine nasıl dönüştüreceğini belirler.

#### Adım 2: Taslak Seviyelerini Atama
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```
Tam sayı derinliği tanımlar – `1` üst‑seviye, `2` alt‑seviye vb.

#### Adım 3: Belgeyi PDF Olarak Kaydetme
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
Oluşturulan PDF, tanımladığınız hiyerarşiyi yansıtan düzenli bir yer imi bölmesi gösterecektir.

### Sorun Giderme İpuçları
- **Yer İmleri Eksik** – Her `startBookmark`'ın eşleşen bir `endBookmark`'a sahip olduğundan emin olun.  
- **Yanlış Seviyeler** – Seviye numaralarının istenen üst‑alt ilişkisine uygun olduğunu doğrulayın.  
- **Lisans Sorunları** – Değerlendirme filigranları görürseniz, lisans dosyasının herhangi bir belge işleminden önce doğru yüklendiğinden emin olun.

## Pratik Uygulamalar
**how to create bookmarks** ve **generate PDF with bookmarks** özellikle aşağıdaki senaryolarda çok değerlidir:

1. **Hukuki Sözleşmeler** – Maddelere, tanımlara veya eklerine hızlıca atlayın.  
2. **Finansal Raporlar** – Bölümler, tablolar ve grafikler arasında kaydırmadan gezin.  
3. **E‑Öğrenme Materyalleri** – Bölüm ve alt bölümler için tıklanabilir bir içindekiler tablosu sağlayın.  

## Performans Düşünceleri
- **Belge Boyutu** – PDF'i hafif tutmak için kaydetmeden önce kullanılmayan stilleri veya görselleri kaldırın.  
- **Bellek Yönetimi** – Çok büyük dosyalar için, büyük düzenlemelerden sonra `doc.updatePageLayout()` çağırarak kaynakları serbest bırakmayı düşünün.  

## Sonuç
Artık **how to create bookmarks**, taslak seviyelerini atama ve Aspose.Words for Java kullanarak **generate PDF with bookmarks** için eksiksiz, üretim‑hazır bir yönteme sahipsiniz. Bu deseni belge iş akışlarınıza entegre ederek her seferinde şık, gezilebilir PDF'ler sunabilirsiniz.

**Sonraki Adımlar**: Yer imlerine özel simgeler eklemeyi deneyin veya bu yaklaşımı Aspose.PDF ile birleştirerek dijital imzalar gibi son‑işlem görevlerini ekleyin.

## SSS Bölümü
1. **Aspose.Words for Java'ı nasıl kurarım?**  
   - Maven veya Gradle aracılığıyla bağımlılık olarak ekleyin, ardından lisans dosyanızı ayarlayın.  
2. **Taslak seviyeleri olmadan yer imlerini kullanabilir miyim?**  
   - Evet, ancak taslak seviyeleri PDF'lerde gezinmeyi iyileştirir.  
3. **Yer imi iç içeleme sınırları nelerdir?**  
   - Katı bir sınır yoktur, ancak hiyerarşiyi son kullanıcı için mantıklı tutun.  
4. **Aspose büyük belgeleri nasıl yönetir?**  
   - Kaynakları verimli yönetir, ancak çok büyük dosyalar için optimizasyon önerilir.  
5. **PDF'yi kaydettikten sonra yer imlerini değiştirebilir miyim?**  
   - Evet, PDF'yi sonradan düzenlemek için Aspose.PDF for Java kullanılabilir.  

## Kaynaklar
- [Aspose.Words Dokümantasyonu](https://reference.aspose.com/words/java/)
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

**Son Güncelleme:** 2026-03-25  
**Test Edilen Versiyon:** Aspose.Words 25.3 for Java  
**Yazar:** Aspose