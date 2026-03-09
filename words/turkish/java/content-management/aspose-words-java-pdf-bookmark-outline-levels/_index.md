---
date: '2026-03-09'
description: Aspose.Words for Java ile Java’da iç içe yer imleri oluşturmayı ve Word/PDF
  yer imlerini kaydetmeyi öğrenin, PDF taslaklarını daha iyi gezinme için düzenleyin.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: PDF Outline Seviyeleri için Java’da İç İçe Yer İmleri Oluştur
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# PDF Taslak Düzeyleri için Java'da İç İçe Yer İşaretleri Oluşturma

## Giriş
Word belgelerini PDF'ye dönüştürürken yer işaretlerini yönetmekte zorlanıyor musunuz? Bu öğreticide Aspose.Words for Java kullanarak **create nested bookmarks java** oluşturacak, ardından **save word pdf bookmarks** net bir taslak hiyerarşisiyle kaydedeceksiniz. Sonunda, eklediğiniz bölüm sayısı ne olursa olsun, gezinmesi kolay, profesyonel görünümlü bir PDF elde edeceksiniz.

**Öğrenecekleriniz**
- Aspose.Words for Java'ı kurun
- **Create nested bookmarks java**'ı bir Word belgesinde oluşturun
- Yer işareti taslak düzeylerini yapılandırılmış gezinme için ayarlayın
- **Save word pdf bookmarks**'ı istenen hiyerarşiyle kaydedin

### Hızlı Yanıtlar
- **Belge oluşturmak için birincil sınıf nedir?** `DocumentBuilder`
- **Yer işareti hiyerarşisini kontrol eden seçenek hangisidir?** `BookmarksOutlineLevelCollection`
- **Maven veya Gradle kullanabilir miyim?** Evet, her ikisi de desteklenir
- **Üretim için lisansa ihtiyacım var mı?** Evet, geçerli bir Aspose.Words lisansı gereklidir
- **Önerilen Java sürümü nedir?** JDK 11 veya üzeri

## “create nested bookmarks java” nedir?
İç içe yer işaretleri oluşturmak, bir yer işaretini diğerinin içine yerleştirmek anlamına gelir, böylece PDF okuyucu katlanabilir bir taslak gösterebilir. Bu, büyük raporlar, yasal sözleşmeler veya okuyucuların belirli bölümlere hızlıca atlaması gereken e‑kitaplar için özellikle faydalıdır.

## PDF yer işareti taslak düzeyleri için Aspose.Words neden kullanılmalı?
Aspose.Words, Word‑PDF dönüşümünün zorluğunu üstlenirken yer işareti yapısını korur. Taslak düzeyleri üzerinde ayrıntılı kontrol sağlar, böylece manuel PDF düzenlemesi yapmadan ebeveyn‑çocuk ilişkilerini tanımlayabilirsiniz.

## Önkoşullar
- **Libraries and Dependencies**: Aspose.Words for Java (25.3 veya daha yeni).  
- **Environment**: JDK 11+ ve IntelliJ IDEA veya Eclipse gibi bir IDE.  
- **Knowledge**: Temel Java, Maven veya Gradle bilgisi.

## Aspose.Words Kurulumu
Başlamak için projenize gerekli bağımlılıkları ekleyin. İşte Maven ve Gradle kullanarak nasıl yapabileceğiniz:

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
Aspose.Words ticari bir üründür, ancak özelliklerini keşfetmek için ücretsiz deneme ile başlayabilirsiniz.

1. **Free Trial**: Tam özellikleri test etmek için [Aspose'un sürüm sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Temporary License**: Gerekirse [Aspose'un geçici lisans sayfasından](https://purchase.aspose.com/temporary-license/) geçici lisans başvurusu yapın.  
3. **Purchase**: Sürekli kullanım için [Aspose'un satın alma portalından](https://purchase.aspose.com/buy) lisans satın alın.

Lisans dosyanızı aldıktan sonra tüm işlevselliği açmak için projenizde başlatın.

## Uygulama Kılavuzu
Kodları adım adım inceleyeceğiz. Her snippet orijinal öğreticiden değiştirilmemiştir, tam uyumluluk sağlar.

### İç İçe Yer İşaretleri Oluşturma (create nested bookmarks java)
**Adım 1: Belge ve Builder'ı Başlatma**  
Bu, içeriği ve yer işaretlerini doldurabileceğiniz yeni bir Word belgesi oluşturur.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Adım 2: İlk (ebeveyn) yer işaretini ekleyin**  
Dış yer işaretini başlatın ve biraz metin ekleyin.

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

**Adım 3: İkinci yer işaretini birincisinin içine iç içe yerleştirin**  
Şimdi ebeveynin içinde yaşayan bir çocuk yer işareti ekliyoruz.

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

**Adım 4: Dış yer işaretini kapatın**  

```java
builder.endBookmark("Bookmark 1");
```

**Adım 5: Ek üst‑seviye yer işaretleri ekleyin**  
İhtiyacınıza göre daha fazla yer işareti eklemeye devam edebilirsiniz.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Yer İşareti Taslak Düzeylerini Yapılandırma (save word pdf bookmarks)
**Adım 1: `PdfSaveOptions` ayarlayın**  
Bu seçenekler, yer işaretlerinin son PDF'de nasıl görüneceğini tanımlamanızı sağlar.

```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

**Adım 2: Her yer işaretine taslak düzeyleri atayın**  
Seviye 1 üst‑seviye bir girdi, seviye 2 seviye 1'in altında iç içe ve bu şekilde devam eder.

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

**Adım 3: Belgeyi PDF olarak kaydedin**  
PDF artık yapılandırılmış bir yer işareti bölmesi içerecek.

```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Yaygın Sorunlar ve Çözümler
- **Missing bookmarks** – Her `startBookmark`'ın eşleşen bir `endBookmark`'a sahip olduğundan emin olun.  
- **Incorrect hierarchy** – Atadığınız seviye numaralarını iki kez kontrol edin; bunlar iç içe sıralamayı belirler.  
- **License not applied** – Yer işaretleri kaybolursa, kaydetmeden önce lisans dosyanızın doğru yüklendiğinden emin olun.

## Pratik Uygulamalar
1. **Legal contracts** – Maddeler ve alt maddeler arasında hızlıca geçiş yapın.  
2. **Financial reports** – Bölümler, tablolar ve ekler arasında kolayca gezin.  
3. **Technical manuals** – Okuyuculara PDF içinde net, katlanabilir bir içindekiler tablosu sunun.

## Performans Düşünceleri
- **Document size** – PDF'i hafif tutmak için kaydetmeden önce kullanılmayan stilleri veya görselleri kaldırın.  
- **Memory usage** – Çok büyük belgeler için sayfaları toplu işleyerek veya `Document.optimizeResources()` kullanarak bellek kullanımını düşünün.

## Sonuç
Artık Aspose.Words for Java ile **create nested bookmarks java** ve **save word pdf bookmarks** nasıl yapılacağını biliyorsunuz. Bu yaklaşım, PDF gezinmesi üzerinde tam kontrol sağlar, belgelerinizi daha profesyonel ve kullanıcı dostu hâle getirir.

**Sonraki Adımlar**  
Yer işaretlerine özel simgeler eklemeyi deneyin veya bu iş akışını daha büyük bir toplu‑işlem uygulamasına entegre edin.

## SSS Bölümü
1. **Aspose.Words for Java nasıl kurulur?**  
   - Maven veya Gradle aracılığıyla bağımlılık olarak ekleyin, ardından lisans dosyanızı ayarlayın.  
2. **Taslak düzeyleri olmadan yer işaretleri kullanabilir miyim?**  
   - Evet, ancak taslak düzeyleri kullanmak PDF gezinmesini büyük ölçüde iyileştirir.  
3. **Yer işareti iç içeleme sınırları nelerdir?**  
   - Kesin bir sınır yoktur, ancak hiyerarşiyi okuyucular için mantıklı tutun.  
4. **Aspose büyük belgeleri nasıl yönetir?**  
   - Kaynakları verimli bir şekilde yönetir, ancak büyük dosyaları yine de optimize etmelisiniz.  
5. **PDF'i kaydettikten sonra yer işaretlerini değiştirebilir miyim?**  
   - Evet, dönüşüm sonrası yer işaretlerini düzenlemek için Aspose.PDF for Java kullanabilirsiniz.

## Kaynaklar
- [Aspose.Words Belgeleri](https://reference.aspose.com/words/java/)
- [En Son Sürümleri İndir](https://releases.aspose.com/words/java/)
- [Lisans Satın Al](https://purchase.aspose.com/buy)
- [Ücretsiz Deneme](https://releases.aspose.com/words/java/)
- [Geçici Lisans Başvurusu](https://purchase.aspose.com/temporary-license/)
- [Aspose Destek Forumu](https://forum.aspose.com/c/words/10)

---

**Last Updated:** 2026-03-09  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}