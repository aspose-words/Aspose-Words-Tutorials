---
date: '2025-12-10'
description: Aspose.Words for Java kullanarak iç içe yer imleri oluşturmayı ve Word
  PDF yer imlerini kaydetmeyi öğrenin, PDF gezinmesini verimli bir şekilde düzenleyin.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Aspose.Words Java ile PDF'de iç içe yer imleri oluşturun
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# PDF'de Aspose.Words Java ile iç içe yer imleri oluşturma

## Giriş
Eğer bir Word belgesinden oluşturulan PDF içinde **iç içe yer imleri** oluşturmanız gerekiyorsa, doğru yerdesiniz. Bu öğreticide Aspose.Words for Java kullanarak kütüphaneyi kurmaktan yer imi taslak seviyelerini yapılandırmaya ve son olarak **Word PDF yer imlerini kaydetmeye** kadar tüm süreci adım adım inceleyeceğiz, böylece ortaya çıkan PDF kolayca gezilebilir.

**Öğrenecekleriniz**
- Aspose.Words for Java nasıl kurulur
- Bir Word belgesi içinde **iç içe yer imleri** nasıl oluşturulur
- PDF gezinmesi için taslak seviyeleri nasıl atanır
- PdfSaveOptions kullanarak **Word PDF yer imleri** nasıl kaydedilir

## Hızlı Yanıtlar
- **Ana hedef nedir?** Tek bir PDF dosyasında iç içe yer imleri oluşturmak ve Word PDF yer imlerini kaydetmek.  
- **Hangi kütüphane gereklidir?** Aspose.Words for Java (v25.3 veya daha yeni).  
- **Lisans gerekli mi?** Test için ücretsiz deneme sürümü yeterlidir; üretim için ticari lisans gerekir.  
- **Taslak seviyelerini kontrol edebilir miyim?** Evet, `PdfSaveOptions` ve `BookmarksOutlineLevelCollection` kullanarak.  
- **Büyük belgeler için uygun mu?** Evet, doğru bellek yönetimi ve kaynak optimizasyonu ile.

## “İç içe yer imleri oluşturma” nedir?
İç içe yer imleri oluşturmak, bir yer imini başka bir yer iminin içinde konumlandırmak anlamına gelir; bu, belgenizin mantıksal bölümlerini yansıtan hiyerarşik bir yapı oluşturur. Bu hiyerarşi, PDF'nin gezinme panelinde gösterilir ve okuyucuların belirli bölümlere veya alt bölümlere doğrudan atlamasını sağlar.

## Aspose.Words for Java ile Word PDF yer imlerini kaydetmek neden tercih edilmeli?
Aspose.Words, düşük seviyeli PDF işlemlerini soyutlayan yüksek seviyeli bir API sunar; böylece dosya formatı detaylarıyla uğraşmadan içerik yapısına odaklanabilirsiniz. Ayrıca tüm Word özelliklerini (stil, resim, tablo vb.) korurken yer imi hiyerarşisi üzerinde tam kontrol sağlar.

## Önkoşullar
- **Kütüphaneler**: Aspose.Words for Java (v25.3+).  
- **Geliştirme Ortamı**: JDK 8 veya üzeri, IntelliJ IDEA veya Eclipse gibi bir IDE.  
- **Derleme Aracı**: Maven veya Gradle (hangisini tercih ederseniz).  
- **Temel Bilgi**: Java programlama, Maven/Gradle temelleri.

## Aspose.Words Kurulumu
Kütüphaneyi projenize aşağıdaki snippet'lerden birini kullanarak ekleyin.

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
Aspose.Words ticari bir üründür, ancak ücretsiz deneme sürümüyle başlayabilirsiniz:

1. **Ücretsiz Deneme** – Tam özellikleri test etmek için [Aspose'un yayın sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Geçici Lisans** – Kısa vadeli bir anahtara ihtiyacınız varsa [Aspose'un geçici lisans sayfasına](https://purchase.aspose.com/temporary-license/) başvurun.  
3. **Satın Alma** – Kalıcı bir lisans için [Aspose'un satın alma portalına](https://purchase.aspose.com/buy) gidin.

`.lic` dosyasını edindikten sonra uygulama başlangıcında yükleyerek tüm özelliklerin kilidini açın.

## Uygulama Kılavuzu
Aşağıda adım adım bir yürütme bulacaksınız. Her kod bloğu, işlevselliği korumak için orijinal öğreticiden değiştirilmemiştir.

### Word belgesinde iç içe yer imleri nasıl oluşturulur
#### Adım 1: Document ve Builder'ı başlatma
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Bu, boş bir Word belgesi ve içerik eklemek için bir builder nesnesi oluşturur.

#### Adım 2: İlk (ebeveyn) yer imini ekleme
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### Adım 3: İkinci yer imini birincisinin içine yerleştirme
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### Adım 4: Dış yer imini kapatma
```java
builder.endBookmark("Bookmark 1");
```

#### Adım 5: Ayrı bir üçüncü yer imi ekleme
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Word PDF yer imlerini kaydetme ve taslak seviyelerini ayarlama
#### Adım 1: PdfSaveOptions yapılandırma
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### Adım 2: Her yer imine taslak seviyeleri atama
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Adım 3: Belgeyi PDF olarak kaydetme
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Yaygın Sorunlar ve Çözümleri
- **Yer imleri eksik** – Her `startBookmark` için eşleşen bir `endBookmark` olduğundan emin olun.  
- **Hiyerarşi hatalı** – Taslak seviyesi sayılarının istenen ebeveyn‑çocuk ilişkisini yansıttığını (düşük sayı = üst seviye) kontrol edin.  
- **Dosya boyutu büyük** – Kaydetmeden önce kullanılmayan stilleri veya resimleri kaldırın veya gerekirse `doc.optimizeResources()` çağrısını yapın.

## Pratik Uygulamalar
| Senaryo | İç içe Yer İmlerinin Faydası |
|----------|----------------------------|
| Hukuki sözleşmeler | Maddelere ve alt maddelere hızlı geçiş |
| Teknik raporlar | Karmaşık bölümler ve ekler arasında gezinme |
| E‑öğrenme materyalleri | Bölümler, dersler ve sınavlara doğrudan erişim |

## Performans Düşünceleri
- **Bellek kullanımı** – Büyük belgeleri parçalara bölerek işleyin veya daha küçük parçaları birleştirmek için `DocumentBuilder.insertDocument` kullanın.  
- **Dosya boyutu** – PDF dönüşümünden önce resimleri sıkıştırın ve gizli içeriği atın.

## Sonuç
Artık **iç içe yer imleri** oluşturmayı, taslak seviyelerini yapılandırmayı ve Aspose.Words for Java kullanarak **Word PDF yer imlerini** kaydetmeyi biliyorsunuz. Bu teknik, PDF gezinmesini büyük ölçüde iyileştirir, belgelerinizi daha profesyonel ve kullanıcı‑dostu hâle getirir.

**Sonraki Adımlar**: Daha derin yer imi hiyerarşileriyle deney yapın, bu mantığı toplu işleme hatlarına entegre edin veya PDF oluşturma sonrası yer imi düzenleme için Aspose.PDF ile birleştirin.

## Sıkça Sorulan Sorular
**S: Aspose.Words for Java nasıl kurulur?**  
C: Yukarıda gösterilen Maven veya Gradle bağımlılığını ekleyin, ardından çalışma zamanında lisans dosyanızı yükleyin.

**S: Taslak seviyeleri ayarlamadan yer imleri kullanılabilir mi?**  
C: Evet, ancak taslak seviyeleri olmadan PDF'nin gezinme paneli tüm yer imlerini aynı hiyerarşide listeler, bu da okuyucular için kafa karıştırıcı olabilir.

**S: Yer imleri ne kadar derin iç içe olabilir?**  
C: Teknik olarak bir sınırlama yoktur, ancak kullanılabilirliği artırmak için 3‑4 seviye gibi makul bir derinlikte tutmanız önerilir.

**S: Aspose çok büyük belgeleri nasıl yönetir?**  
C: Kütüphane içeriği akış olarak işler ve bellek ayak izini azaltmak için `optimizeResources()` sunar; yine de çok sayfalı dosyalar için JVM heap izlenmelidir.

**S: PDF oluşturulduktan sonra yer imleri değiştirilebilir mi?**  
C: Evet, mevcut bir PDF'de yer imlerini düzenlemek, eklemek veya kaldırmak için Aspose.PDF for Java kullanılabilir.

---

**Son Güncelleme:** 2025-12-10  
**Test Edilen Sürüm:** Aspose.Words 25.3 for Java  
**Yazar:** Aspose  

**Kaynaklar**
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