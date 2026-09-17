---
date: '2026-09-17'
description: Aspose.Words for Java kullanarak yer imli PDF oluşturmayı ve çizelge
  seviyelerini ayarlamayı öğrenin. Word'den PDF'ye yer imleri oluşturmak için adım
  adım kılavuz ve verimli bir yöntem.
keywords:
- word to pdf bookmarks
- generate pdf with bookmarks
- Aspose.Words Java bookmarks
lastmod: '2026-09-17'
og_description: Aspose.Words for Java kullanarak yer imli PDF oluşturmayı ve çizelge
  seviyelerini ayarlamayı öğrenin. Word'den PDF'ye yer imleri oluşturmak için adım
  adım kılavuz ve verimli bir yöntem.
og_image_alt: Guide showing how to add word to pdf bookmarks using Aspose.Words Java
og_title: Aspose.Words for Java ile PDF yer imlerine Word ekleme
schemas:
- author: Aspose
  dateModified: '2026-09-17'
  description: Learn how to generate pdf with bookmarks and set outline levels using
    Aspose.Words for Java. Step‑by‑step guide for creating word to pdf bookmarks efficiently.
  headline: How to add word to PDF bookmarks with Aspose.Words for Java
  type: TechArticle
- description: Learn how to generate pdf with bookmarks and set outline levels using
    Aspose.Words for Java. Step‑by‑step guide for creating word to pdf bookmarks efficiently.
  name: How to add word to PDF bookmarks with Aspose.Words for Java
  steps:
  - name: initialize the document and builder
    text: '`Document` is Aspose.Words'' top‑level object that represents a single
      Word file in memory.'
  - name: insert nested bookmarks
    text: '`DocumentBuilder` is Aspose.Words'' cursor‑based API for inserting text,
      tables, images, and bookmarks programmatically. Start a primary bookmark: Now
      nest a secondary bookmark inside the first one: Close the outer bookmark:'
  - name: add additional independent bookmarks
    text: 'You can create as many top‑level bookmarks as needed. Example of a third
      bookmark:'
  - name: set up PdfSaveOptions
    text: '`PdfSaveOptions` is the configuration object that controls how a Word document
      is rendered to PDF, including bookmark handling.'
  - name: assign outline levels
    text: '`OutlineOptions` is a property of `PdfSaveOptions` that lets you define
      the hierarchy of bookmarks in the PDF. Use the `OutlineOptions` property to
      map each bookmark name to an integer level (1 = top‑level, 2 = child, etc.).'
  - name: save the document as PDF
    text: The final call writes the PDF with the structured bookmark tree.
  type: HowTo
- questions:
  - answer: Add the Maven or Gradle dependency shown earlier, then place your license
      file on the classpath and load it with the `License` class.
    question: How do I install Aspose.Words for Java?
  - answer: Yes, but the PDF will display a flat list of bookmarks, which can be harder
      to navigate in large documents.
    question: Can I add bookmarks without setting outline levels?
  - answer: Technically no, but keeping the hierarchy to 3‑4 levels maintains readability
      for most users.
    question: Is there a limit to how deep bookmark nesting can be?
  - answer: It streams content and can process 500‑page files in under 3 seconds;
      for larger files, enable memory‑optimisation options as described.
    question: How does Aspose.Words handle very large documents?
  - answer: Absolutely—use Aspose.PDF for Java to edit, reorder, or delete bookmarks
      in an existing PDF.
    question: Can I modify bookmarks after the PDF is created?
  type: FAQPage
tags:
- pdf bookmarks
- Aspose.Words
- java document processing
title: Aspose.Words for Java ile PDF yer imlerine Word ekleme
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile PDF yer imlerine kelime ekleme

## Giriş
**Word to pdf bookmarks** dönüştürülmüş bir PDF içinde okuyucuların bölümler arasında hızlıca atlamasını sağlamak için gereklidir. Bu öğreticide, Aspose.Words for Java kullanarak yer imli PDF oluşturmayı, anahat seviyelerini atamayı ve temiz bir gezinme ağacı üretmeyi öğreneceksiniz. Sonunda, yasal sözleşmeler, teknik kılavuzlar ve çok bölümlü herhangi bir belge için çalışan yeniden kullanılabilir bir desen elde edeceksiniz.

### Hızlı cevaplar
- **Yer imi eklemenin en basit yolu nedir?** `DocumentBuilder` aralığını oluşturun, `startBookmark(name)` ve `endBookmark(name)` metodlarını çağırın.
- **Yer imi desteği için lisansa ihtiyacım var mı?** Hayır, ücretsiz deneme tam yer imi işlevselliğini içerir.
- **Hiyerarşik seviyeler ayarlayabilir miyim?** Evet, `PdfSaveOptions.getOutlineOptions().setOutlineLevel(bookmark, level)` kullanın.
- **Büyük belgeler performansı etkiler mi?** Aspose.Words standart bir sunucuda 500 sayfalık dosyaları 3 saniyeden kısa sürede işler.
- **Bu yaklaşım Maven ve Gradle ile uyumlu mu?** Kesinlikle – aynı API her iki yapı aracında da çalışır.

## Word to pdf yer imleri nedir?
Word to pdf yer imleri, PDF içinde gömülü olan ve kaynak Word dosyasındaki adlandırılmış konumlara karşılık gelen gezinme girişleridir. Bir PDF görüntüleyici belgeyi gösterdiğinde, bu girişler yer imi bölmesinde görünür ve bölümlere, tablolara veya şekillere anında atlamayı sağlar.

## Aspose.Words kullanarak yer imli PDF neden oluşturmalısınız?
Aspose.Words **35+ giriş ve çıkış formatını**—DOCX, ODT, HTML ve PDF dahil—destekler ve tipik sunucu donanımında Microsoft Word gerektirmeden **500 sayfalık belgeleri 3 saniyeden kısa sürede** işleyebilir. Bu hız ve format çeşitliliği, zengin gezinme yapılarıyla otomatik PDF oluşturma için sektörde standart çözüm olmasını sağlar.

## Önkoşullar
- **Aspose.Words for Java** sürüm 25.3 ve üzeri.
- JDK 11 veya daha yeni bir sürüm ve IntelliJ IDEA veya Eclipse gibi bir IDE.
- Temel Java bilgisi ve Maven veya Gradle ile aşinalık.
- Geçerli bir Aspose.Words lisans dosyası (deneme için isteğe bağlı).

## Aspose.Words kurulumu
Kütüphaneyi projenize eklemek için, yapı sisteminize uygun bağımlılığı ekleyin.

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

### Lisans edinimi
Aspose.Words ticari bir üründür, ancak ücretsiz deneme tam erişim sağlar.

1. **Ücretsiz deneme:** Tüm özellikleri test etmek için [Aspose'un sürüm sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Geçici lisans:** Kısa vadeli bir anahtar için [Aspose'un geçici lisans sayfasına](https://purchase.aspose.com/temporary-license/) başvurun.  
3. **Satın alma:** Kalıcı bir lisans almak için [Aspose'un satın alma portalından](https://purchase.aspose.com/buy) faydalanın.

`.lic` dosyasını indirdikten sonra, kodunuzda `License license = new License(); license.setLicense("Aspose.Words.Java.lic");` ile yükleyin.

## Uygulama rehberi
Aşağıda, iç içe yer imleri oluşturmayı, anahat seviyelerini atamayı ve son PDF'yi kaydetmeyi gösteren adım adım bir rehber bulunmaktadır.

### Java'da word to pdf yer imleri nasıl oluşturulur?
Kaynak belgenizi yükleyin, `DocumentBuilder` ile yer imleri ekleyin, `PdfSaveOptions` aracılığıyla anahat seviyelerini ayarlayın ve sonunda PDF olarak kaydedin. Bu desen, yüklediğiniz herhangi bir Word dosyası için çalışır.

#### Adım 1: belgeyi ve oluşturucuyu başlatın
`Document` Aspose.Words'in bellek içinde tek bir Word dosyasını temsil eden üst‑seviye nesnesidir.  
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```  

#### Adım 2: iç içe yer imleri ekleyin
`DocumentBuilder`, Aspose.Words'in metin, tablo, resim ve yer imlerini programlı olarak eklemek için imleç‑tabanlı API'sidir.  
Birincil bir yer imi başlatın:  
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```  

Şimdi, birincil yer iminin içine ikincil bir yer imi ekleyin:  
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```  

Dış yer imi kapatın:  
```java
builder.endBookmark("Bookmark 1");
```  

#### Adım 3: ek bağımsız yer imleri ekleyin
İhtiyacınıza göre istediğiniz sayıda üst‑seviye yer imi oluşturabilirsiniz. Üçüncü bir yer imi örneği:  
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```  

### PDF çıktısı için yer imi anahat seviyeleri nasıl yapılandırılır?
Anahat seviyeleri, PDF görüntüleyicinin yer imi bölmesinde gösterilen hiyerarşiyi belirler ve okuyuculara net bir ağaç görünümü sunar.

#### Adım 1: PdfSaveOptions ayarlayın
`PdfSaveOptions`, bir Word belgesinin PDF'ye nasıl dönüştürüleceğini kontrol eden, yer imi işleme dahil yapılandırma nesnesidir.  
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```  

#### Adım 2: anahat seviyelerini atayın
`OutlineOptions`, `PdfSaveOptions`'ın PDF'deki yer imlerinin hiyerarşisini tanımlamanızı sağlayan bir özelliğidir.  
`OutlineOptions` özelliğini kullanarak her yer imi adını bir tam sayı seviyesine (1 = üst‑seviye, 2 = alt‑seviye, vb.) eşleyin.  
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```  

#### Adım 3: belgeyi PDF olarak kaydedin
Son çağrı, yapılandırılmış yer imi ağacıyla PDF'yi yazar.  
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```  

## Yaygın sorunlar ve çözümler
- **Eksik yer imleri:** Her `startBookmark`'ın eşleşen bir `endBookmark`'a sahip olduğundan emin olun.
- **Yanlış hiyerarşi:** Atadığınız seviye numaralarını kontrol edin; alt yer imleri, üst yer imlerinden daha büyük bir sayıya sahip olmalıdır.
- **Büyük dosyalarda performans düşüşü:** Bellek kullanımını azaltmak için `document.removeUnusedResources()` metodunu çağırın.

## Pratik uygulamalar
1. **Hukuki sözleşmeler:** Maddelere, ek belgelere ve imzalara hızlı gezinme sağlar.
2. **Teknik raporlar:** Okuyucuların bölümler, ekler ve veri tabloları arasında atlamasını mümkün kılar.
3. **E‑öğrenme materyalleri:** Kursları bölümler ve alt bölümlerle yapılandırarak sezgisel bir öğrenme yolu sunar.

## Performans hususları
- Kullanılmayan stilleri ve resimleri kaldırarak PDF'yi hafif tutun.
- 1.000 sayfayı aşan belgeler için, `PdfSaveOptions.setMemoryOptimization(true)` ayarını yaparak çıktıyı akış olarak alın.
- Çok çekirdekli işleme iyileştirmelerinden faydalanmak için en yeni Aspose.Words sürümünü kullanın.

## Sonuç
Artık Aspose.Words for Java kullanarak yer imli PDF oluşturmak ve anahat seviyelerini kontrol etmek için eksiksiz, üretime hazır bir yaklaşıma sahipsiniz. Bu deseni belge‑oluşturma süreçlerinize entegre ederek kullanıcıların sorunsuzca gezinebileceği profesyonel kalitede PDF'ler sunabilirsiniz.

**Sonraki adımlar:** Belge içeriğine göre koşullu yer imi oluşturmayı deneyin veya iş akışını, kullanıcıların yüklediği Word dosyalarını anında dönüştüren bir web servisine entegre edin.

## Sıkça sorulan sorular

**S: Aspose.Words for Java nasıl kurulur?**  
C: Önceden gösterilen Maven veya Gradle bağımlılığını ekleyin, ardından lisans dosyanızı sınıf yoluna yerleştirin ve `License` sınıfı ile yükleyin.

**S: Anahat seviyeleri ayarlamadan yer imleri ekleyebilir miyim?**  
C: Evet, ancak PDF, büyük belgelerde gezinmesi daha zor olabilecek düz bir yer imi listesi gösterir.

**S: Yer imi iç içeleme derinliği için bir sınırlama var mı?**  
C: Teknik olarak hayır, ancak hiyerarşiyi 3‑4 seviyede tutmak çoğu kullanıcı için okunabilirliği korur.

**S: Aspose.Words çok büyük belgelerle nasıl başa çıkar?**  
C: İçeriği akış olarak işler ve 500 sayfalık dosyaları 3 saniyeden kısa sürede işleyebilir; daha büyük dosyalar için, açıklanan bellek‑optimizasyon seçeneklerini etkinleştirin.

**S: PDF oluşturulduktan sonra yer imlerini değiştirebilir miyim?**  
C: Kesinlikle—varolan bir PDF'de yer imlerini düzenlemek, yeniden sıralamak veya silmek için Aspose.PDF for Java kullanın.

## Kaynaklar
- [Aspose.Words Dokümantasyonu](https://reference.aspose.com/words/java/)
- [En Son Sürümleri İndir](https://releases.aspose.com/words/java/)
- [Lisans Satın Al](https://purchase.aspose.com/buy)
- [Ücretsiz Deneme](https://releases.aspose.com/words/java/)
- [Geçici Lisans Başvurusu](https://purchase.aspose.com/temporary-license/)
- [Aspose Destek Forumu](https://forum.aspose.com/c/words/10)

---

**Son Güncelleme:** 2026-09-17  
**Test Edilen Versiyon:** Aspose.Words for Java 25.3  
**Yazar:** Aspose

## İlgili Eğitimler

- [Aspose.Words for Java'ı Ustalaştırın: Word Belgelerinde Yer İmleri Ekleme ve Yönetme](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [Aspose.Words for Java'da Yer İmleri Kullanma](/words/java/document-manipulation/using-bookmarks/)
- [Aspose.Words for Java'da Belgeleri PDF Olarak Kaydetme](/words/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}