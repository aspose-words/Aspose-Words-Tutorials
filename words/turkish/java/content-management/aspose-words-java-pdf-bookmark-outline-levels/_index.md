---
date: '2026-04-27'
description: Aspose.Words for Java kullanarak yer imleri nasıl ayarlanır ve yer imli
  PDF nasıl kaydedilir öğrenin. Bu kapsamlı rehberle okunabilirliği ve gezinmeyi artırın.
keywords:
- how to set bookmarks
- save pdf with bookmarks
- create nested bookmarks
- generate pdf with bookmarks
- convert word pdf bookmarks
title: Aspose.Words Java ile PDF'lerde Yer İmleri Nasıl Ayarlanır
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# PDF'lerde Yer İşaretleri Nasıl Ayarlanır Aspose.Words Java ile

## Giriş
Word belgelerini PDF'lere dönüştürürken **yer işaretlerinin nasıl ayarlanacağı** konusunda zorlanıyorsanız doğru yerdesiniz. Bu öğreticide Aspose.Words for Java kullanarak iç içe yer işaretleri oluşturma, ana hat seviyelerini yapılandırma ve son PDF'in temiz, profesyonel ve kolay gezilebilir olmasını sağlama sürecini adım adım göstereceğiz.

**Öğrenecekleriniz**
- Projenizde Aspose.Words for Java'ı kurun  
- **Word belgesi içinde iç içe yer işaretleri oluşturun**  
- **Yer işareti ana hat seviyelerini yapılandırın** yapılandırılmış bir PDF ana hatı için  
- **Belirlediğiniz hiyerarşiyi yansıtan yer işaretli PDF kaydedin**  

### Hızlı Yanıtlar
- **Belgeleri oluşturmak için birincil sınıf nedir?** `DocumentBuilder`  
- **Hangi seçenek yer işareti hiyerarşisini kontrol eder?** `PdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels()`  
- **Maven veya Gradle kullanabilir miyim?** Evet, ikisi de desteklenir (kod parçacıklarına bakın)  
- **Lisans gerekir mi?** Değerlendirme için bir deneme sürümü çalışır; üretim için kalıcı bir lisans gerekir  
- **PDF iç içe yer işaretlerini korur mu?** Kesinlikle, ana hat seviyeleri doğru ayarlandığında  

## PDF'de “yer işaretleri nasıl ayarlanır” nedir?
Yer işaretleri, PDF'in gezinme panelinde tıklanabilir girişler tanımlayarak belge içinde belirli bölümlere atlamayı sağlar. Yer işaretleri iç içe ve ana hat seviyeleri atandığında, katlanabilir bir ağaç şeklinde görünür ve büyük belgelerin keşfi çok daha kolay olur.

## Yer işareti ana hat seviyeleri için Aspose.Words neden kullanılmalı?
Aspose.Words, Word‑to‑PDF dönüşümünde tam programatik kontrol sunar; **yer işaretli PDF oluşturma** yeteneği sayesinde belgelerinizin yapısını yansıtan PDF'ler elde edersiniz. Bu, manuel sonrası işleme ihtiyacını ortadan kaldırır ve tüm oluşturulan PDF'lerde tutarlı bir kullanıcı deneyimi sağlar.

## Önkoşullar
- **Kütüphaneler ve Bağımlılıklar**: Aspose.Words for Java (sürüm 25.3 ve üzeri).  
- **Ortam**: JDK 8 veya daha yeni, IntelliJ IDEA veya Eclipse gibi IDE.  
- **Bilgi**: Temel Java, Maven veya Gradle bilgisi.

## Aspose.Words Kurulumu
Gerekli kütüphaneyi derleme sisteminize ekleyin.

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

### Lisans Edinme
Aspose.Words ticari bir üründür, ancak ücretsiz bir deneme ile başlayabilirsiniz.

1. **Ücretsiz Deneme**: Tam özellikleri test etmek için [Aspose'un sürüm sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Geçici Lisans**: Gerekiyorsa [Aspose'un geçici lisans sayfasından](https://purchase.aspose.com/temporary-license/) geçici lisans başvurusu yapın.  
3. **Satın Alma**: Sürekli kullanım için [Aspose'un satın alma portalından](https://purchase.aspose.com/buy) lisans satın alın.

Lisans dosyasını kodunuzda başlatarak tüm özelliklerin kilidini açın.

## Uygulama Kılavuzu
Aşağıda **iç içe yer işaretleri oluşturma**, ana hat seviyelerini ayarlama ve sonunda **yer işaretli PDF kaydetme** konularını kapsayan adım adım bir rehber bulunmaktadır.

### İç İçe Yer İşaretleri Oluşturma
**Genel Bakış**: Bir Word belgesi oluşturun ve hiyerarşiyi yansıtan yer işaretleri ekleyin.

#### Adım 1: Belge ve Builder'ı Başlat
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Bu, içerik eklemeye hazır yeni bir belge oluşturur.

#### Adım 2: İç İçe Yer İşaretleri Ekle
Önce bir birincil yer işareti oluşturun, ardından içine ikinci bir yer işareti iç içe yerleştirin.

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

#### Adım 3: Ek Yer İşaretleri Ekle
Gerektikçe bağımsız yer işaretleri eklemeye devam edebilirsiniz.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Yer İşareti Ana Hat Seviyelerini Yapılandırma
**Genel Bakış**: PDF'in yer işareti bölmesinin istenen hiyerarşiyi yansıtması için ana hat seviyeleri atayın.

#### Adım 1: PdfSaveOptions'ı Ayarla
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
Bu seçenekler belge PDF olarak kaydedilirken kullanılacak.

#### Adım 2: Ana Hat Seviyeleri Ekle
Her yer işareti adını bir ana hat seviyesine eşleyin (1 = üst‑seviye, 2 = alt‑seviye, vb.).

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Adım 3: Belgeyi Kaydet
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
Ortaya çıkan PDF artık yapılandırılmış bir yer işareti ağacına sahiptir.

## Yaygın Sorunlar ve Çözümler
- **Eksik yer işaretleri** – Her `startBookmark`'ın eşleşen bir `endBookmark`'ı olduğundan emin olun.  
- **Yanlış hiyerarşi** – Ana hat seviyesi sayılarını kontrol edin; bir alt‑seviye, üst‑seviyesinden daha yüksek bir sayıya sahip olmalı.  
- **Büyük belgeler** – Dosya boyutunu azaltmak için kaydetmeden önce `doc.removeUnusedResources()` çağırın.

## Pratik Uygulamalar
1. **Hukuki sözleşmeler** – Maddelere ve alt maddelere hızlıca atlayın.  
2. **Yıllık raporlar** – Bölümler, tablolar ve grafikler arasında kolayca gezin.  
3. **E‑öğrenme materyali** – Öğrenciler için tıklanabilir bir içerik tablosu sağlayın.

## Performans Düşünceleri
- Dönüştürmeden önce gereksiz düğümleri kaldırarak PDF'i hafif tutun.  
- Çok büyük dosyalar için belgenin akışını (streaming) düşünerek yüksek bellek tüketimini önleyin.

## Sonuç
Artık **yer işaretlerinin nasıl ayarlanacağını**, ana hat seviyelerinin nasıl yapılandırılacağını ve Aspose.Words for Java kullanarak **yer işaretli PDF kaydetmeyi** biliyorsunuz. Bu teknik PDF gezinmesini büyük ölçüde iyileştirir ve belgelerinize profesyonel bir dokunuş kazandırır.

**Sonraki Adımlar**: Yer işaretlerine özel simgeler eklemeyi deneyin veya bu iş akışını toplu‑işlem hizmetine entegre edin.

## Sıkça Sorulan Sorular

**S: Aspose.Words for Java nasıl kurulur?**  
C: Yukarıda gösterilen Maven veya Gradle bağımlılığını ekleyin, ardından lisans dosyanızı projenin resources klasörüne yerleştirin.

**S: Ana hat seviyeleri olmadan yer işaretleri oluşturabilir miyim?**  
C: Evet, ancak ana hat seviyeleri olmadan PDF'in gezinme bölmesi tüm yer işaretlerini aynı seviyede listeler, bu da büyük belgelerin taranmasını zorlaştırır.

**S: Yer işaretleri ne kadar derine iç içe yerleştirilebilir?**  
C: Teknik olarak bir limit yok, ancak hiyerarşiyi son kullanıcılar için okunabilir tutun—genellikle 3‑4 seviye yeterlidir.

**S: Aspose çok büyük Word dosyalarını nasıl yönetir?**  
C: İçeriği akış (stream) olarak işler ve bellek kullanımını düşük tutmak için `Document.optimizeResources()` gibi yöntemler sunar.

**S: PDF oluşturulduktan sonra yer işaretlerini düzenleyebilir miyim?**  
C: Evet, Aspose.PDF for Java kullanarak yer işareti başlıklarını, hedeflerini veya hiyerarşisini dönüşüm sonrası değiştirebilirsiniz.

---

**Last Updated:** 2026-04-27  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose  

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