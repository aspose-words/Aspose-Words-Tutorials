---
date: '2026-03-20'
description: Aspose.Words for Java kullanarak iç içe yer imleri oluşturmayı ve yer
  imli PDF oluşturmayı öğrenin, okunabilirliği ve gezinmeyi artırın.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Aspose.Words Java ile PDF'lerde İç İçe Yer İşaretleri Oluşturun
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# PDF'lerde İç İçe Yer İşaretleri Oluşturma - Aspose.Words Java

## Giriş
Bir Word belgesini PDF'ye dönüştürdükten sonra PDF yer işaretlerini düzenli tutmakta zorlandıysanız, yalnız değilsiniz. Bu öğreticide **iç içe yer işaretleri oluşturacak** ve **yer işaretli PDF oluşturmayı** öğreneceksiniz. Aspose.Words kurulumunu, yer işaretleri hiyerarşisi oluşturmayı, anahat seviyelerini atamayı ve sonunda temiz bir PDF dışa aktarmayı adım adım göstereceğiz.

**Öğrenecekleriniz**
- Aspose.Words for Java nasıl kurulur
- Bir Word belgesi içinde **iç içe yer işaretleri nasıl oluşturulur**
- PDF gezinmesi için yer işareti anahat seviyeleri nasıl yapılandırılır
- Tanımladığınız hiyerarşiyi yansıtan **yer işaretli PDF nasıl oluşturulur**

### Hızlı Yanıtlar
- **Belge oluşturmak için birincil sınıf nedir?** `DocumentBuilder`
- **Hangi metot bir yer işareti ekler?** `startBookmark(String name)`
- **Bir yer işareti için anahat seviyesi nasıl ayarlanır?** `outlineLevels.add(name, level)`
- **Üretim ortamı için lisansa ihtiyacım var mı?** Evet, satın alınan lisans tam özellikleri açar.
- **Bunu Maven veya Gradle ile kullanabilir miyim?** Kesinlikle – her ikisi de desteklenir.

### Ön Koşullar
İlerlemeye başlamadan önce şunlara sahip olun:
- **Aspose.Words for Java** (sürüm 25.3 veya üzeri).  
- Yüklü bir JDK ve IntelliJ IDEA veya Eclipse gibi bir IDE.  
- Temel Java bilgisi ve Maven ya da Gradle hakkında bir miktar tecrübe.

## “İç içe yer işaretleri oluşturma” nedir?
İç içe yer işaretleri oluşturmak, bir yer işaretini başka bir yer işaretinin içinde konumlandırmak ve böylece bir üst‑alt hiyerarşi oluşturmak anlamına gelir. Belge PDF olarak kaydedildiğinde, bu ilişkiler PDF'in yer işareti panelinde katlanabilir girişler olarak görünür ve büyük belgelerin keşfini çok daha kolay hâle getirir.

## PDF'ye yer işaretleri eklerken neden anahat seviyeleri kullanmalısınız?
Anahat seviyeleri, PDF görüntüleyicide yer işaretlerinin görsel hiyerarşisini tanımlar. Seviye‑1 bir yer işareti üst‑seviye giriş olarak, seviye‑2 bir alt‑giriş olarak vb. görünür. Doğru anahat seviyeleri, düz bir yer işareti listesini yapılandırılmış bir içerik tablosuna dönüştürür; bu, özellikle yasal sözleşmeler, teknik raporlar ve e‑kitaplar için çok değerlidir.

## Aspose.Words Kurulumu
Kütüphaneyi projenize Maven ya da Gradle kullanarak ekleyin.

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

### Lisans Edinimi
Aspose.Words ticari bir üründür, ancak ücretsiz deneme sürümüyle başlayabilirsiniz.

1. **Ücretsiz Deneme** – Tam özellikleri test etmek için [Aspose'un sürüm sayfası](https://releases.aspose.com/words/java/) üzerinden indirin.  
2. **Geçici Lisans** – Kısa vadeli değerlendirme için [Aspose’un geçici lisans sayfası](https://purchase.aspose.com/temporary-license/) üzerinden başvurun.  
3. **Satın Alma** – Kalıcı bir lisans almak için [Aspose’un satın alma portalı](https://purchase.aspose.com/buy) adresini ziyaret edin.

`.lic` dosyasını edindikten sonra, tüm özellikleri açmak için kodunuzda yükleyin.

## Uygulama Kılavuzu
Aşağıda bir belge oluşturma, iç içe yer işaretleri ekleme, anahat seviyeleri atama ve sonucu PDF olarak kaydetme adımlarını bulacaksınız.

### Adım 1: Belge ve Builder'ı Başlatma
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Bu kod, boş bir Word belgesi ve metin ile yer işaretleri eklemek için kullanacağınız bir builder nesnesi oluşturur.

### Adım 2: İlk (Üst) Yer İşaretini Oluşturma
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
`startBookmark` çağrısı **Bookmark 1** adlı yeni bir yer işareti açar. Bu çağrının ardından yazdığınız her şey, yer işareti kapanana kadar o yer işaretine ait olur.

### Adım 3: İkinci Yer İşaretini İlkinin İçine İç İçe Yerleştirme
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
Bu yer işareti, birincisinin **sonra** başlatılıp **önce** kapatıldığı için **Bookmark 1**'in bir çocuğu haline gelir.

### Adım 4: Üst Yer İşaretini Kapatma
```java
builder.endBookmark("Bookmark 1");
```
Artık hiyerarşi şu şekilde görünür:

- Bookmark 1 (seviye 1)  
  - Bookmark 2 (seviye 2)

### Adım 5: Bağımsız Üçüncü Yer İşareti Ekleme
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```
Bu yer işareti, ilk iki yer işaretinden ayrı olarak üst seviyede yer alır.

### Adım 6: PDF Dışa Aktarma için Anahat Seviyelerini Yapılandırma
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
`PdfSaveOptions` nesnesi, yer işaretlerinin nihai PDF'te nasıl görüneceğini kontrol etmenizi sağlar.

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 1);
```
Burada üst‑seviye yer işaretlerine seviye 1, iç içe yer işaretine ise seviye 2 atıyoruz.

### Adım 7: Belgeyi PDF Olarak Kaydetme
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
Oluşan PDF, tanımladığınız hiyerarşiyi yansıtan temiz ve katlanabilir bir yer işareti paneli gösterir.

## Yaygın Sorunlar ve Çözümler
- **Yer İşaretleri Eksik** – Her `startBookmark` için eşleşen bir `endBookmark` olmalıdır. Birini atlamak, yer işaretinin PDF'te gözükmemesine neden olur.  
- **Yanlış Anahat Seviyeleri** – `outlineLevels.add` içine gönderdiğiniz isimleri iki kez kontrol edin. Yazım hatası seviyenin uygulanmamasına yol açar.  
- **Büyük Belgeler** – Çok büyük dosyalar için `doc.removeMacros()` çağırın ya da kullanılmayan stilleri temizleyin; bu PDF boyutunu makul tutar.

## Pratik Uygulamalar
1. **Yasal Sözleşmeler** – Madde ve alt‑madde arasında hızlı geçiş.  
2. **Teknik Raporlar** – Bölümler, tablolar ve şekiller arasında kaydırma yapmadan gezinme.  
3. **E‑Öğrenme Materyalleri** – Öğrenciler için tıklanabilir bir içerik tablosu sağlama.

## Performans İpuçları
- Kaydetmeden önce kullanılmayan kaynakları (görseller, stiller) kaldırın.  
- 100 MB'den büyük PDF'ler işliyorsanız, bellek kullanımını düşük tutmak için akış (streaming) API'lerini kullanın.

## Sonuç
Artık **iç içe yer işaretleri oluşturma**, anahat seviyeleri atama ve **yer işaretli PDF oluşturma** konularında bilgi sahibisiniz. Daha derin hiyerarşiler deneyebilir ya da bu mantığı belge‑oluşturma hattınıza entegre ederek otomasyonu artırabilirsiniz.

## Sık Sorulan Sorular

**S: Aspose.Words for Java nasıl kurulur?**  
C: Yukarıda gösterilen Maven ya da Gradle bağımlılığını ekleyin, ardından çalışma zamanında lisans dosyanızı yükleyin.

**S: Anahat seviyeleri ayarlamadan yer işaretleri kullanılabilir mi?**  
C: Evet, ancak PDF düz bir liste gösterecek ve karmaşık belgelerde gezinme zorlaşacaktır.

**S: Yer işareti iç içeleme derinliği için bir sınırlama var mı?**  
C: Teknik olarak yok, ancak okunabilirliği korumak için hiyerarşiyi 3‑4 seviye ile sınırlamak önerilir.

**S: Aspose çok büyük belgeleri nasıl yönetir?**  
C: İçeriği akış (stream) olarak işler ve bellek yönetimi araçları sunar; yine de kullanılmayan öğeleri temizlemek faydalıdır.

**S: PDF oluşturulduktan sonra yer işaretlerini düzenleyebilir miyim?**  
C: Kesinlikle – PDF sonrası düzenlemeler için Aspose.PDF for Java kullanarak başlıkları, hedefleri veya anahat seviyelerini değiştirebilirsiniz.

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

---

**Last Updated:** 2026-03-20  
**Tested With:** Aspose.Words for Java 25.3  
**Author:** Aspose