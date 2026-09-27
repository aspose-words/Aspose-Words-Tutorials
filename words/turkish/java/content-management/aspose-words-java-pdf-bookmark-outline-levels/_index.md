---
date: '2026-09-27'
description: Aspose.Words for Java kullanarak iç içe PDF yer imleri oluşturmayı ve
  yer imli PDF üretmeyi öğrenin. Word belgelerini outline seviyeleriyle PDF'ye dönüştürmek
  için adım adım rehberi izleyin.
keywords:
- create nested PDF bookmarks
- generate PDF with bookmarks
- convert Word PDF bookmarks
lastmod: '2026-09-27'
og_description: Aspose.Words for Java kullanarak iç içe PDF yer imleri oluşturmayı
  ve yer imli PDF üretmeyi öğrenin. Word belgelerini outline seviyeleriyle PDF'ye
  dönüştürmek için adım adım rehberi izleyin.
og_image_alt: Guide showing how to create nested PDF bookmarks with Aspose.Words Java
og_title: Aspose.Words Java ile iç içe PDF yer imleri nasıl oluşturulur
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to create nested PDF bookmarks and generate PDF with bookmarks
    using Aspose.Words for Java. Follow a step‑by‑step guide to convert Word documents
    to PDFs with outline levels.
  headline: How to create nested PDF bookmarks with Aspose.Words Java
  type: TechArticle
- description: Learn how to create nested PDF bookmarks and generate PDF with bookmarks
    using Aspose.Words for Java. Follow a step‑by‑step guide to convert Word documents
    to PDFs with outline levels.
  name: How to create nested PDF bookmarks with Aspose.Words Java
  steps:
  - name: Initialize Document and Builder
    text: '`Document` represents a Word document in memory, while `DocumentBuilder`
      provides methods to construct and modify its contents.'
  - name: Insert nested bookmarks
    text: 'Start by creating a primary bookmark: Now, nest another bookmark within
      it: Complete the outer bookmark:'
  - name: Add additional bookmarks
    text: 'Continue adding bookmarks as needed. For example, a separate third bookmark:'
  - name: Set up PdfSaveOptions
    text: '`PdfSaveOptions` configures how a document is saved as PDF, including bookmark
      handling and image compression.'
  - name: Add outline levels
    text: 'Assign levels to each bookmark, which will determine their hierarchy:'
  - name: Save the document
    text: 'Finally, save your document as a PDF with these settings:'
  type: HowTo
- questions:
  - answer: Add the Maven or Gradle dependency shown above, then place your license
      file in the project resources folder.
    question: How do I install Aspose.Words for Java?
  - answer: Yes, but the bookmark pane will appear as a flat list, which reduces navigation
      efficiency.
    question: Can I generate PDF with bookmarks without setting outline levels?
  - answer: PDF specifications allow up to nine outline levels; Aspose.Words respects
      this limit.
    question: Is there a limit to how deep bookmark nesting can be?
  - answer: The library streams content and can process 500‑page files in under three
      seconds on typical hardware, while keeping memory usage under 200 MB.
    question: How does Aspose.Words handle very large documents?
  - answer: Yes, you can use Aspose.PDF for Java to edit, reorder, or delete bookmarks
      in an existing PDF.
    question: Can I modify bookmarks after the PDF is created?
  type: FAQPage
tags:
- create nested PDF bookmarks
- Aspose.Words Java
- PDF outline levels
- Java PDF generation
- document conversion
title: Aspose.Words Java ile iç içe PDF yer imleri nasıl oluşturulur
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java ile iç içe PDF yer imleri oluşturma

## Giriş
Aspose.Words for Java kullanarak iç içe PDF yer imleri oluşturun ve yer imli PDF oluşturun; bu sayede PDF'lerinize temiz, hiyerarşik bir gezinme bölmesi ekleyin. Bu öğretici, kütüphaneyi kurma, bir Word belgesinde iç içe yer imleri oluşturma, ana hat seviyelerini yapılandırma ve sonucu PDF olarak kaydetme adımlarını size gösterir.

**Öğrenecekleriniz**
- Aspose.Words for Java’yı kurma ve lisanslama  
- Bir Word belgesi içinde iç içe yer imleri oluşturma  
- PDF yer imi ağacının belge yapınızı yansıtması için ana hat seviyelerini atama  
- Tam özellikli bir yer imi ana hatı ile belgeyi PDF olarak dışa aktarma  

### Hızlı cevaplar
- **Ana hedef?** Ana hat seviyeleriyle iç içe PDF yer imleri oluşturma.  
- **Gerekli kütüphane?** Aspose.Words for Java v25.3 veya daha yeni bir sürüm.  
- **Ana sınıf?** Yer imleri eklemek için `DocumentBuilder`.  
- **Kaç ana hat seviyesi destekleniyor?** PDF spesifikasyonlarına uygun olarak en fazla 9 seviye.  
- **Tipik çalışma süresi?** Standart bir dizüstü bilgisayarda 50 sayfalık belge için bir saniyeden az.

## İç içe PDF yer imleri oluşturma nedir?
İç içe PDF yer imleri oluşturma, PDF dosyası içinde hiyerarşik gezinme noktaları ekleyerek okuyucuların yer imleri bölmesinde bölümleri genişletip daraltabilmesini sağlar. Aspose.Words, bu yer imlerini kaynak belge hâlâ bir Word dosyası iken tanımlamanıza izin verir ve PDF’ye kaydederken hiyerarşiyi korur.

## Bu görev için Aspose.Words neden kullanılmalı?
Aspose.Words **35+** giriş ve çıkış formatını destekler—DOCX, ODT ve PDF dahil—ve tipik sunucu donanımında **500‑sayfalık** belgeleri **3 saniyenin** altında işleyebilir. Kütüphane, karmaşık düzenleri, yazı tiplerini ve görselleri Microsoft Word kurulumu gerektirmeden işler, bu da otomatik PDF üretim hatları için idealdir.

## Önkoşullar
- **Kütüphaneler ve bağımlılıklar**: Aspose.Words for Java v25.3 veya daha yenisi.  
- **Ortam**: JDK 8 veya daha yenisi, IntelliJ IDEA veya Eclipse gibi bir IDE.  
- **Bilgi**: Temel Java, Maven veya Gradle bilgisi.

## Aspose.Words Kurulumu
Projeye gerekli bağımlılıkları ekleyerek başlayın. Maven ve Gradle kullanarak nasıl yapacağınızı aşağıda bulabilirsiniz:

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

### Lisans edinme
Aspose.Words ticari bir üründür, ancak özelliklerini keşfetmek için ücretsiz bir deneme sürümüyle başlayabilirsiniz.

1. **Ücretsiz deneme** – Tam yetenekleri test etmek için [Aspose'un sürüm sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Geçici lisans** – Gerekiyorsa [Aspose'un geçici lisans sayfasından](https://purchase.aspose.com/temporary-license/) geçici bir lisans başvurusu yapın.  
3. **Satın alma** – Sürekli kullanım için [Aspose'un satın alma portalından](https://purchase.aspose.com/buy) lisans satın alın.

Lisans dosyanızı aldıktan sonra tüm özellikleri açmak için projenizde başlatın.

## Uygulama rehberi
Uygulamayı yönetilebilir bölümlere ayıralım.

### İç içe yer imleri oluşturma
**Genel bakış:** Aspose.Words for Java kullanarak bir Word belgesinde iç içe yer imleri oluşturmayı öğrenin.

#### Adım 1: Document ve Builder'ı Başlatma
`Document` bellekte bir Word belgesini temsil eder, `DocumentBuilder` ise içeriğini oluşturmak ve değiştirmek için yöntemler sunar.  
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```  

#### Adım 2: İç içe yer imleri ekleme
Öncelikle bir ana yer imi oluşturun:  
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```  
Şimdi onun içinde başka bir yer imi iç içe yerleştirin:  
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```  
Dış yer imi tamamlayın:  
```java
builder.endBookmark("Bookmark 1");
```  

#### Adım 3: Ek yer imleri ekleme
Gerektiği gibi yer imleri eklemeye devam edin. Örneğin, ayrı bir üçüncü yer imi:  
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```  

### Yer imi ana hat seviyelerini yapılandırma
**Genel bakış:** PDF’de daha iyi bir gezinme için yer imlerinize ana hat seviyeleri atayarak düzenleyin.

#### Adım 1: PdfSaveOptions'ı ayarlama
`PdfSaveOptions`, bir belgenin PDF olarak kaydedilme şeklini, yer imi işleme ve görsel sıkıştırma dahil olmak üzere yapılandırır.  
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```  

#### Adım 2: Ana hat seviyeleri ekleme
Her yer imine seviyeler atayın; bu, hiyerarşilerini belirleyecektir:  
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```  

#### Adım 3: Belgeyi kaydetme
Son olarak, bu ayarlarla belgeyi PDF olarak kaydedin:  
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```  

## Yaygın sorunlar ve çözümler
- **Yer imleri eksik** – Her `startBookmark` için eşleşen bir `endBookmark` olduğundan emin olun.  
- **Yanlış ana hat seviyeleri** – Kaydetmeden önce yer imi ağacını yazdırarak ebeveyn‑çocuk ilişkilerini doğrulayın.  
- **Büyük belge bellek kullanımı** – Ağır değişikliklerden sonra geçici kaynakları serbest bırakmak için `Document.updatePageLayout()` çağırın.

## Pratik uygulamalar
İç içe PDF yer imlerinin öne çıktığı gerçek dünya senaryoları:

1. **Hukuki sözleşmeler** – Maddelere, alt maddelere ve eklerine hızlıca atlayın.  
2. **Finansal raporlar** – Bölümler, tablolar ve grafikler arasında kaydırmadan gezinme.  
3. **E‑öğrenme modülleri** – Bölümler ve dersler için tıklanabilir bir içerik tablosu sağlayın.

## Performans hususları
- PDF boyutunu küçük tutmak için kaydetmeden önce kullanılmayan stilleri ve boş paragrafları kaldırın.  
- 200 sayfadan büyük belgeler işlenirken bellek baskısını azaltmak için `PdfSaveOptions.setCompressImages(true)` etkinleştirin.

## Ek kaynaklar
- **Dokümantasyon:** Tam API referansını [Aspose.Words Documentation](https://reference.aspose.com/words/java/) adresinde keşfedin.  
- **İndirilenler:** En yeni ikili dosyaları [Download Latest Releases](https://releases.aspose.com/words/java/) üzerinden alın.  
- **Lisanslama:** [Purchase a License](https://purchase.aspose.com/buy) ile lisans satın alın veya bir [Free Trial](https://releases.aspose.com/words/java/) ile başlayın.  
- **Geçici lisans:** [Temporary License Application](https://purchase.aspose.com/temporary-license/) üzerinden başvurun.  
- **Destek:** Sorularınızı [Aspose Support Forum](https://forum.aspose.com/c/words/10) üzerinden sorabilirsiniz.

## Sonuç
**İç içe PDF yer imleri** oluşturmayı, ana hat seviyeleri atamayı ve Aspose.Words for Java kullanarak Word belgesini iyi yapılandırılmış bir PDF’ye dışa aktarmayı öğrendiniz. Bu teknikleri uyguladığınızda PDF’leriniz çok daha kullanıcı dostu ve profesyonel olacaktır.

**Sonraki adımlar** – Özel yer imi simgeleriyle deney yapın, PDF meta verileri ekleyin veya iş akışını toplu‑işleme hizmetine entegre edin.

## Sıkça sorulan sorular

**S: Aspose.Words for Java’yı nasıl kurarım?**  
C: Yukarıda gösterilen Maven veya Gradle bağımlılığını ekleyin, ardından lisans dosyanızı proje kaynak klasörüne yerleştirin.

**S: Ana hat seviyeleri ayarlamadan yer imli PDF oluşturabilir miyim?**  
C: Evet, ancak yer imi bölmesi düz bir liste olarak görünecek ve gezinme verimliliği azalacaktır.

**S: Yer imi iç içeleme derinliği için bir sınırlama var mı?**  
C: PDF spesifikasyonları en fazla dokuz ana hat seviyesine izin verir; Aspose.Words bu sınırlamayı uygular.

**S: Aspose.Words çok büyük belgelerle nasıl başa çıkar?**  
C: Kütüphane içeriği akış olarak işler ve tipik donanımda 500‑sayfalık dosyaları üç saniyenin altında işleyebilir, bellek kullanımı 200 MB’nin altında tutulur.

**S: PDF oluşturulduktan sonra yer imlerini değiştirebilir miyim?**  
C: Evet, mevcut bir PDF’de yer imlerini düzenlemek, yeniden sıralamak veya silmek için Aspose.PDF for Java’yı kullanabilirsiniz.

**Last Updated:** 2026-09-27  
**Tested With:** Aspose.Words for Java v25.3  
**Author:** Aspose

## İlgili Eğitimler

- [Master Aspose.Words for Java: How to Insert and Manage Bookmarks in Word Documents](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [Hyperlink Management in Word Using Aspose.Words Java: A Comprehensive Guide](/words/java/content-management/master-hyperlink-management-word-aspose-words-java/)
- [Saving Documents as PDF in Aspose.Words for Java](/words/java/document-loading-and-saving/saving-documents-as-pdf/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}