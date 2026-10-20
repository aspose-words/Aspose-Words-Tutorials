---
date: '2026-10-02'
description: Aspose.Words for Java kullanarak iç içe yer imleri oluşturmayı ve Word
  PDF yer imlerini kaydetmeyi öğrenin, böylece PDF içinde verimli bir gezinme sağlayın.
keywords:
- how to create bookmarks
- convert word pdf bookmarks
- save word pdf bookmarks
lastmod: '2026-10-02'
og_description: Aspose.Words for Java kullanarak PDF'te yer imleri nasıl oluşturulur.
  İç içe yer imleri eklemeyi, anahat seviyelerini ayarlamayı ve Word PDF yer imlerini
  verimli bir şekilde kaydetmeyi öğrenin.
og_image_alt: Developer guide showing nested PDF bookmarks creation with Aspose.Words
  for Java
og_title: Aspose.Words for Java ile PDF'te yer imleri nasıl oluşturulur
schemas:
- author: Aspose
  dateModified: '2026-10-02'
  description: Learn how to create nested bookmarks and save Word PDF bookmarks using
    Aspose.Words for Java, enabling efficient PDF navigation.
  headline: How to create bookmarks in PDF with Aspose.Words for Java
  type: TechArticle
- description: Learn how to create nested bookmarks and save Word PDF bookmarks using
    Aspose.Words for Java, enabling efficient PDF navigation.
  name: How to create bookmarks in PDF with Aspose.Words for Java
  steps:
  - name: '**Free trial** – Download from [Aspose''s release page](https://releases.aspose.com/words/java/)
      to test full capabilities.'
    text: '**Free trial** – Download from [Aspose''s release page](https://releases.aspose.com/words/java/)
      to test full capabilities.'
  - name: '**Temporary license** – Apply at [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/)
      if you need a short‑term key.'
    text: '**Temporary license** – Apply at [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/)
      if you need a short‑term key.'
  - name: '**Purchase** – Obtain a permanent license from the [Aspose’s purchasing
      portal](https://purchase.aspose.com/buy).'
    text: '**Purchase** – Obtain a permanent license from the [Aspose’s purchasing
      portal](https://purchase.aspose.com/buy).'
  type: HowTo
- questions:
  - answer: Add the Maven or Gradle dependency shown above, then load your license
      file at runtime.
    question: How do I install Aspose.Words for Java?
  - answer: Yes, but without outline levels the PDF’s navigation pane will list all
      bookmarks at the same hierarchy, which can be confusing for readers.
    question: Can I use bookmarks without setting outline levels?
  - answer: Technically no, but for usability keep nesting to 3‑4 levels so users
      can easily scan the list.
    question: Is there a limit to how deep bookmarks can be nested?
  - answer: The library streams content and offers `optimizeResources()` to reduce
      memory footprint; monitoring JVM heap is still recommended for multi‑hundred‑page
      files.
    question: How does Aspose handle very large documents?
  - answer: Yes, you can use Aspose.PDF for Java to edit, add, or remove bookmarks
      in an existing PDF.
    question: Can I modify bookmarks after the PDF is created?
  type: FAQPage
tags:
- PDF bookmarks
- Aspose.Words
- Java PDF generation
- nested bookmarks
- document processing
title: Aspose.Words for Java ile PDF'te yer imleri nasıl oluşturulur
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile PDF'de Yer İmleri Nasıl Oluşturulur

## Giriş
Eğer bir Word belgesinden oluşturulan PDF'de **create nested bookmarks** oluşturmanız gerekiyorsa, doğru yerdesiniz. Bu öğreticide, Aspose.Words for Java kullanarak kütüphaneyi kurmaktan yer imi taslak seviyelerini yapılandırmaya ve nihayet **save Word PDF bookmarks** yapmaya kadar tam süreci adım adım göstereceğiz, böylece son PDF kolayca gezilebilir. Yer imlerinin neden önemli olduğunu anlayacak, kesin API çağrılarını görecek ve büyük belgelerle başa çıkma ipuçları alacaksınız.

**Öğrenecekleriniz**
- Aspose.Words for Java'ı nasıl kurulur
- Bir Word belgesi içinde **create nested bookmarks** nasıl oluşturulur
- PDF'de net bir gezinme için taslak seviyelerini nasıl atarsınız
- `PdfSaveOptions` kullanarak **save Word PDF bookmarks** nasıl kaydedilir

## Hızlı Yanıtlar
- **Ana hedef nedir?** Tek bir PDF dosyasında iç içe yer imleri oluşturmak ve Word PDF yer imlerini kaydetmek.  
- **Hangi kütüphane gereklidir?** Aspose.Words for Java (v25.3 veya daha yeni).  
- **Lisans gerekli mi?** Test için ücretsiz deneme çalışır; üretim için ticari bir lisans gereklidir.  
- **Taslak seviyelerini kontrol edebilir miyim?** Evet, `PdfSaveOptions` ve `BookmarksOutlineLevelCollection` kullanarak.  
- **Büyük belgeler için uygun mu?** Evet, uygun bellek yönetimi ve kaynak optimizasyonu ile.

## “create nested bookmarks” nedir?
İç içe yer imleri oluşturmak, bir yer imini başka bir yer iminin içine yerleştirmek anlamına gelir ve belgenizin mantıksal bölümlerini yansıtan hiyerarşik bir yapı oluşturur. Bu hiyerarşi PDF'nin gezinme bölmesinde gösterilir ve okuyucuların belirli bölümlere veya alt bölümlere doğrudan atlamasını sağlar.

## Word PDF yer imlerini kaydetmek için Aspose.Words for Java neden kullanılmalı?
Aspose.Words for Java **35+ input and output formats** (DOCX, ODT, RTF, PDF, HTML ve EPUB dahil) destekler ve tipik bir sunucuda 500 sayfalık belgeleri 3 saniyenin altında işleyebilir. Düşük seviyeli PDF işlemlerini soyutlayarak, stil, resim ve tablo gibi tüm Word özelliklerini korurken içerik yapısına odaklanmanızı sağlar.

## Önkoşullar
- **Kütüphaneler**: Aspose.Words for Java (v25.3+).  
- **Geliştirme ortamı**: JDK 8 veya daha yeni, IntelliJ IDEA veya Eclipse gibi IDE.  
- **Derleme aracı**: Maven veya Gradle (hangisini tercih ederseniz).  
- **Temel bilgi**: Java programlama, Maven/Gradle temelleri.

## Aspose.Words Kurulumu
Kütüphaneyi projenize aşağıdaki kod parçacıklarından birini kullanarak ekleyin.

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

### Lisans edinimi
Aspose.Words ticari bir üründür, ancak ücretsiz deneme ile başlayabilirsiniz:

1. **Free trial** – Tam özellikleri test etmek için [Aspose's release page](https://releases.aspose.com/words/java/) adresinden indirin.  
2. **Temporary license** – Kısa vadeli bir anahtara ihtiyacınız varsa [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/) adresinden başvurun.  
3. **Purchase** – Kalıcı bir lisansı [Aspose’s purchasing portal](https://purchase.aspose.com/buy) üzerinden edinin.

`.lic` dosyasını aldıktan sonra, tüm özelliklerin kilidini açmak için uygulama başlangıcında yükleyin.

## Uygulama rehberi
Aşağıda adım adım bir rehber bulunmaktadır. Her kod bloğu, işlevselliği korumak için orijinal öğreticiden değiştirilmemiştir.

### Word belgesinde iç içe yer imleri nasıl oluşturulur
#### Belge ve builder nasıl başlatılır
Başlamak için bir `Document` nesnesine ve bir `DocumentBuilder`'a ihtiyacınız var.  
`Document`, Aspose.Words'ın bellekte tek bir Word dosyasını temsil eden üst‑seviye nesnesidir.  
`DocumentBuilder`, metin, tablo, resim ve yer imleri eklemek için imleç‑tabanlı bir API sağlar.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```  

#### İlk (üst) yer imini nasıl eklenir
Bir yer imini `startBookmark` ile başlatır ve daha sonra `endBookmark` ile kapatırsınız.  
`startBookmark`, bir yer imi bölgesinin başlangıcını işaret eder; karşılık gelen `endBookmark` ise sonunu tanımlar.

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```  

#### İkinci yer imini birincisinin içine nasıl iç içe yerleştirirsiniz
Dış yer imini kapatmadan önce tekrar `startBookmark` çağırarak bir alt yer imi oluşturursunuz.  
İç içe yer imi, daha sonra açıkça farklı bir seviye ayarlamazsanız, üst yer iminin taslak seviyesini devralır.

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```  

#### Dış yer imini nasıl kapatırsınız
Dış yer imini kapatmak hiyerarşiyi tamamlar.  
Her `startBookmark`'ın eşleşen bir `endBookmark`'ı olduğundan emin olun; aksi takdirde PDF yer imini kaçırabilir veya hata gösterebilir.

```java
builder.endBookmark("Bookmark 1");
```  

#### Ayrı bir üçüncü yer imini nasıl eklersiniz
İç içe çiftin ardından ek üst‑seviye yer imleri ekleyebilirsiniz.  
Bunlar PDF gezinme panelinde kardeş girişler olarak görünecektir.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```  

## Word PDF yer imlerini kaydetme ve taslak seviyelerini ayarlama
### PdfSaveOptions nasıl yapılandırılır
`PdfSaveOptions`, yer imi taslak seviyeleri dahil olmak üzere PDF‑özel ayarları kontrol eder.

```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```  

### Her yer imine taslak seviyeleri nasıl atanır
`BookmarksOutlineLevelCollection`, her yer imi adını bir taslak seviyesine (1 = üst seviye) eşlemenizi sağlar.

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```  

### Belgeyi PDF olarak nasıl kaydedersiniz
Son olarak, yapılandırılmış seçeneklerle `save` metodunu çağırın.  
`save` metodu belgeyi belirtilen formata yazar; `PdfSaveOptions` kullanıldığında, yer imi hiyerarşisini PDF dosyasına da gömer.

```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```  

## Yaygın sorunlar ve çözümler
- **Yer imleri eksik** – Her `startBookmark`'ın eşleşen bir `endBookmark`'ı olduğundan emin olun.  
- **Yanlış hiyerarşi** – Taslak seviye numaralarının istenen üst‑alt ilişkiyi yansıttığından emin olun (düşük sayılar = daha yüksek seviye).  
- **Büyük dosya boyutu** – Kaydetmeden önce kullanılmayan stilleri veya resimleri kaldırın, ya da bellek kullanımını azaltmak için `doc.optimizeResources()` metodunu çağırın.

## Pratik uygulamalar
| Senaryo | İç içe yer imlerinin faydası |
|----------|----------------------------|
| Hukuki sözleşmeler | Maddelere ve alt maddelere hızlı geçiş |
| Teknik raporlar | Karmaşık bölümler ve ekleri gezme |
| E‑öğrenme materyalleri | Bölümlere, derslere ve sınavlara doğrudan erişim |

## Performans hususları
- **Memory usage** – Bellek kullanımı – Büyük belgeleri parçalara bölerek işleyin veya daha küçük parçaları birleştirmek için `DocumentBuilder.insertDocument` kullanın.  
- **File size** – Dosya boyutu – PDF dönüşümünden önce resimleri sıkıştırın ve gizli içeriği atın.  
- **Speed** – Hız – Aspose.Words, yerel render motoru sayesinde standart bir sunucuda 300 sayfalık bir belgeyi PDF'ye 2 saniyenin altında dönüştürebilir.

## Sonuç
Artık Aspose.Words for Java kullanarak **create nested bookmarks** oluşturmayı, taslak seviyelerini yapılandırmayı ve **save Word PDF bookmarks** kaydetmeyi biliyorsunuz. Bu teknik PDF gezinmesini büyük ölçüde iyileştirir, belgelerinizi daha profesyonel ve kullanıcı dostu hâle getirir.  

**Sonraki adımlar**: Daha derin yer imi hiyerarşileriyle denemeler yapın, bu mantığı toplu işleme hatlarına entegre edin veya PDF oluşturulduktan sonra yer imlerini düzenlemek için Aspose.PDF for Java ile birleştirin.

## Sıkça Sorulan Sorular
**S: Aspose.Words for Java nasıl kurulur?**  
Cevap: Yukarıda gösterilen Maven veya Gradle bağımlılığını ekleyin, ardından çalışma zamanında lisans dosyanızı yükleyin.

**S: Taslak seviyeleri ayarlamadan yer imlerini kullanabilir miyim?**  
Cevap: Evet, ancak taslak seviyeleri olmadan PDF'nin gezinme bölmesi tüm yer imlerini aynı hiyerarşide listeler, bu da okuyucular için kafa karıştırıcı olabilir.

**S: Yer imleri ne kadar derine iç içe yerleştirilebilir?**  
Cevap: Teknik olarak bir limit yok, ancak kullanılabilirlik açısından 3‑4 seviyeye kadar sınırlı tutun ki kullanıcılar listeyi kolayca tarayabilsin.

**S: Aspose çok büyük belgelerle nasıl başa çıkar?**  
Cevap: Kütüphane içeriği akış olarak işler ve bellek ayak izini azaltmak için `optimizeResources()` sunar; çok sayfalı dosyalar için JVM yığını izlenmesi hâlâ önerilir.

**S: PDF oluşturulduktan sonra yer imlerini değiştirebilir miyim?**  
Cevap: Evet, mevcut bir PDF'de yer imlerini düzenlemek, eklemek veya kaldırmak için Aspose.PDF for Java kullanabilirsiniz.

**Kaynaklar**  
- [Aspose.Words Dokümantasyonu](https://reference.aspose.com/words/java/)  
- [En Son Sürümleri İndir](https://releases.aspose.com/words/java/)  
- [Lisans Satın Al](https://purchase.aspose.com/buy)  
- [Ücretsiz Deneme](https://releases.aspose.com/words/java/)  
- [Geçici Lisans Başvurusu](https://purchase.aspose.com/temporary-license/)  
- [Aspose Destek Forumu](https://forum.aspose.com/c/words/10)

---

**Son Güncelleme:** 2026-10-02  
**Test Edilen Versiyon:** Aspose.Words 25.3 for Java  
**Yazar:** Aspose

## İlgili Öğreticiler

- [Aspose.Words for Java ile Word'e Yer İmleri Ekle – Ekle, Güncelle, Sil](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [Aspose Words ile Word'ü PDF Olarak Kaydet – Adım Adım Java Rehberi](/words/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [Aspose.Words for Java ile Word'ü PDF'ye Dönüştür](/words/java/document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}