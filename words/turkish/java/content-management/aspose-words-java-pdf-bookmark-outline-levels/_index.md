---
date: '2026-04-07'
description: Aspose.Words for Java kullanarak iç içe PDF yer imleri oluşturmayı, yer
  imli PDF üretmeyi ve Word PDF yer imlerini kaydetmeyi öğrenin.
keywords:
- create nested pdf bookmarks
- generate pdf with bookmarks
- save word pdf bookmarks
title: Aspose.Words ile Java'da İç İçe PDF Yer İmleri Oluşturun
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java ile Aspose.Words'ta İç İçe PDF Yer İmleri Oluşturma

## Giriş
Bu öğreticide, Aspose.Words for Java kullanarak **iç içe PDF yer imleri oluşturmayı** öğrenecek, böylece yer imli PDF'ler oluşturabilecek ve Word PDF yer imlerini temiz bir taslak hiyerarşisiyle kaydedebileceksiniz. Kütüphaneyi kurma, iç içe yer imleri oluşturma, taslak seviyelerini atama ve son PDF'yi dışa aktarma adımlarını birlikte inceleyeceğiz.

**Öğrenecekleriniz**
- Aspose.Words for Java'ı kurun ve lisanslayın
- Bir Word belgesi içinde iç içe yer imleri oluşturun
- Yapılandırılmış gezinme için yer imi taslak seviyelerini yapılandırın
- Yer imi hiyerarşisini koruyan bir PDF olarak belgeyi kaydedin

### Önkoşullar
- **Kütüphaneler ve Bağımlılıklar**: Aspose.Words for Java (25.3 ve üzeri)  
- **Ortam**: JDK 8+ ve IntelliJ IDEA veya Eclipse gibi bir IDE  
- **Temel Beceriler**: Java, Maven veya Gradle ve PDF yer imleri kavramına aşinalık  

## Hızlı Yanıtlar
- **“iç içe pdf yer imleri oluşturma” ne anlama gelir?**  
  Bu, alt yer imlerinin üst yer imlerinin içinde yer aldığı, bir kitabın bölümleri ve alt bölümleri gibi bir yer imi hiyerarşisi oluşturmak anlamına gelir.  
- **PDF dönüşümünü hangi Aspose ürünü yönetir?**  
  Aspose.Words for Java, yer imi taslak seviyelerini koruyarak Word'ü PDF'ye dönüştürür.  
- **Geliştirme için lisansa ihtiyacım var mı?**  
  Ücretsiz deneme ile başlayabilirsiniz; kısa vadeli testler için geçici bir lisans mevcuttur.  
- **Özel taslak seviyeleri ayarlayabilir miyim?**  
  Evet – `BookmarksOutlineLevelCollection` her yer imine istediğiniz tam sayı seviyesini atamanızı sağlar.  
- **Bu yaklaşım büyük belgelerle uyumlu mu?**  
  Kesinlikle. Aspose.Words verileri verimli bir şekilde akıtır, ancak dosya boyutunu optimum tutmak için kullanılmayan içeriği kaldırmalısınız.

## “iç içe pdf yer imleri oluşturma” nedir?
İç içe PDF yer imleri, PDF görüntüleyicilerin gezinme bölmelerinde görülen ağaç benzeri bir yapıdır. Okuyucuların bölümlere, alt bölümlere veya belirli paragraflara doğrudan atlamasını sağlar, belge kullanılabilirliğini artırır—özellikle yasal sözleşmeler, teknik raporlar veya e‑kitaplar için.

## Yer imi taslak seviyeleri için neden Aspose.Words kullanmalı?
Aspose.Words, belgeyi oluştururken yer imlerini tanımlamanızı sağlayan akıcı bir API sunar ve ardından bu yer imlerini otomatik olarak PDF taslak girişlerine eşler. Bu, manuel son işlemeyi ortadan kaldırır ve PDF'nin gezinmesinin orijinal Word hiyerarşesini yansıtmasını garanti eder.

## Aspose.Words Kurulumu
Kütüphaneyi Maven veya Gradle kullanarak projenize ekleyin.

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
Aspose.Words ticari bir kütüphanedir, ancak ücretsiz olarak değerlendirebilirsiniz.

1. **Ücretsiz Deneme** – Tüm özellikleri keşfetmek için [Aspose'un sürüm sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Geçici Lisans** – Kısa vadeli projeler için [Aspose'un geçici lisans sayfasına](https://purchase.aspose.com/temporary-license/) başvurun.  
3. **Satın Alma** – Tam bir lisansı [Aspose satın alma portalından](https://purchase.aspose.com/buy) edinin.

`.lic` dosyasını aldıktan sonra, tüm yetenekleri açmak için uygulama başlangıcında yükleyin.

## Uygulama Rehberi
Uygulamayı iki mantıksal bölüme ayıracağız: iç içe yer imleri oluşturma ve bunların taslak seviyelerini yapılandırma.

### İç İçe Yer İmleri Oluşturma
**Genel Bakış** – Bu bölüm, hiyerarşik yer imlerini doğrudan bir Word belgesine nasıl gömeceğinizi gösterir.

#### Adım 1: Belge ve Builder'ı Başlatma
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
`DocumentBuilder`, metin, tablo ve yer imleri eklemenizi sağlayan kullanışlı bir yol sunar.

#### Adım 2: Birincil ve İç İçe Yer İmleri Ekleme
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
Şimdi ilk yer iminin içinde bir alt yer imi ekleyin:

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

Dış yer imini kapatın:

```java
builder.endBookmark("Bookmark 1");
```

#### Adım 3: Ayrı Bir Üst‑Seviye Yer İmi Ekleme
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```
Gerekli derinlikte bir hiyerarşi oluşturmak için bu adımları tekrarlayabilirsiniz.

### Yer İmi Taslak Seviyelerini Yapılandırma
**Genel Bakış** – Yer imleri oluşturulduktan sonra, PDF görüntüleyicilerin doğru şekilde göstermesi için taslak seviyelerini tanımlayın.

#### Adım 1: PdfSaveOptions Ayarlama
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
`PdfSaveOptions`, Word belgesinin PDF olarak nasıl oluşturulacağını kontrol eder.

#### Adım 2: Her Yer İmine Seviyeler Atama
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```
Seviye 1 üst‑seviye bir giriş olarak, seviye 2 bir alt öğe olarak ve bu şekilde devam eder.

#### Adım 3: Belgeyi PDF Olarak Kaydetme
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
Oluşan PDF, tanımladığınız yapıyı yansıtan üç katmanlı bir yer imi bölmesi gösterecektir.

### Sorun Giderme İpuçları
- **Yer İmleri Eksik** – Her `startBookmark`'ın eşleşen bir `endBookmark`'a sahip olduğundan emin olun.  
- **Yanlış Hiyerarşi** – Taslak seviye sayılarını iki kez kontrol edin; bir alt öğe, üst öğesinden daha yüksek bir seviyeye sahip olmalıdır.  
- **Lisans Hataları** – Aspose API'lerini çağırmadan önce lisans dosyasının yüklendiğinden emin olun; aksi takdirde değerlendirme filigranları görürsünüz.

## Pratik Uygulamalar
1. **Yasal Sözleşmeler** – Maddelere, alt maddelere ve ek bölümlere hızlıca atlayın.  
2. **Teknik Raporlar** – Bölüm‑seviyesi yer imleriyle büyük teknik şartnamalarda gezin.  
3. **E‑Öğrenme Materyalleri** – Öğrencilere derslere ve sınavlara anında erişim sağlayın.

## Performans Düşünceleri
- **Belge Boyutu** – PDF'yi hafif tutmak için kaydetmeden önce kullanılmayan stilleri veya gizli bölümleri kaldırın.  
- **Bellek Yönetimi** – Çok büyük dosyalar için belgeyi akıtmeyi veya `Document.optimizeResources()` kullanmayı düşünün.

## Sonuç
Artık Aspose.Words for Java kullanarak **iç içe PDF yer imleri oluşturma**, **yer imli PDF üretme** ve **Word PDF yer imlerini kaydetme** için eksiksiz, üretim‑hazır bir yönteme sahipsiniz. Bu deseni raporlama veya belge‑oluşturma süreçlerinize entegre ederek şık ve gezinilebilir PDF'ler sunabilirsiniz.

## Sıkça Sorulan Sorular

**S: Aspose.Words for Java'yı nasıl kurarım?**  
A: Yukarıda gösterilen Maven veya Gradle bağımlılığını ekleyin, ardından çalışma zamanında lisans dosyanızı yükleyin.

**S: Taslak seviyeleri ayarlamadan yer imlerini kullanabilir miyim?**  
A: Evet, ancak PDF gezinmesi düz olacaktır, bu da okuyucuların belge hiyerarşisini anlamasını zorlaştırır.

**S: Yer imleri ne kadar derine iç içe yerleştirilebilir?**  
A: Teknik olarak hayır, ancak çoğu PDF görüntüleyicide okunabilirliği korumak için hiyerarşiyi makul (3‑5 seviye) tutun.

**S: Aspose.Words çok büyük belgeleri nasıl yönetir?**  
A: İçeriği akıtarak ve bellek tüketimini azaltmak için `optimizeResources()` sunarak çalışır, ancak yine de belirli dosya boyutlarınızla test etmelisiniz.

**S: PDF oluşturulduktan sonra yer imlerini düzenleyebilir miyim?**  
A: Kesinlikle—PDF oluşturulduktan sonra yer imi başlıklarını, hedeflerini veya taslak seviyelerini değiştirmek için Aspose.PDF for Java'yı kullanın.

## Kaynaklar
- [Aspose.Words Dokümantasyonu](https://reference.aspose.com/words/java/)
- [En Son Sürümleri İndir](https://releases.aspose.com/words/java/)
- [Lisans Satın Al](https://purchase.aspose.com/buy)
- [Ücretsiz Deneme](https://releases.aspose.com/words/java/)
- [Geçici Lisans Başvurusu](https://purchase.aspose.com/temporary-license/)
- [Aspose Destek Forumu](https://forum.aspose.com/c/words/10)

---

**Son Güncelleme:** 2026-04-07  
**Test Edilen Versiyon:** Aspose.Words 25.3 for Java  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}