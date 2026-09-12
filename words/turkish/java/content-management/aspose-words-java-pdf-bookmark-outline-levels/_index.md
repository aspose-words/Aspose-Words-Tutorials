---
date: '2026-09-12'
description: Aspose.Words for Java kullanarak PDF yer imleri oluşturmayı, outline
  levels ayarlamayı ve iyi yapılandırılmış PDF'ler üretmeyi öğrenin.
keywords:
- how to create pdf bookmarks
- convert word to pdf java
- maven dependency aspose words
lastmod: '2026-09-12'
og_description: Aspose.Words for Java kullanarak PDF yer imleri oluşturmayı, outline
  levels ayarlamayı ve profesyonel PDF'leri hızlı bir şekilde oluşturmayı öğrenin.
og_image_alt: Developer guide showing PDF bookmark creation with Aspose.Words Java
og_title: Aspose.Words for Java ile PDF yer imleri nasıl oluşturulur
schemas:
- author: Aspose
  dateModified: '2026-09-12'
  description: Learn how to create PDF bookmarks using Aspose.Words for Java, set
    outline levels, and produce well‑structured PDFs.
  headline: How to create PDF bookmarks with Aspose.Words for Java
  type: TechArticle
- description: Learn how to create PDF bookmarks using Aspose.Words for Java, set
    outline levels, and produce well‑structured PDFs.
  name: How to create PDF bookmarks with Aspose.Words for Java
  steps:
  - name: initialize document and builder
    text: '`Document` represents the entire Word file in memory, while `DocumentBuilder`
      lets you insert text, tables, and bookmarks at the current cursor position.'
  - name: insert the outer (parent) bookmark
    text: Create the first bookmark that will act as a parent node in the PDF outline.
  - name: nest a child bookmark inside the parent
    text: '`startBookmark` and `endBookmark` define the range for the child bookmark,
      automatically becoming a child node under the parent when exported.'
  - name: close the outer bookmark
    text: Closing the outer bookmark finalizes the parent‑child relationship.
  - name: add an independent third bookmark
    text: You can add as many top‑level bookmarks as you need; each will appear as
      a separate entry in the PDF outline.
  - name: set up `PdfSaveOptions`
    text: '`PdfSaveOptions` lets you fine‑tune the PDF conversion, including bookmark
      handling.'
  - name: assign outline levels to each bookmark
    text: Use `PdfSaveOptions.getBookmarkExportMode()` and `PdfSaveOptions.setOutlineOptions()`
      to map your Word bookmarks to specific outline levels.
  - name: save the document as a PDF
    text: Calling `document.save("output.pdf", pdfSaveOptions)` writes the file with
      the defined bookmark hierarchy.
  type: HowTo
- questions:
  - answer: Add the Maven or Gradle dependency shown earlier, then place your license
      file in the classpath and load it with `License license = new License(); license.setLicense("Aspose.Words.lic");`.
    question: How do I install Aspose.Words for Java?
  - answer: Yes, but the PDF will show a flat list of bookmarks, making deep navigation
      harder.
    question: Can I create bookmarks without setting outline levels?
  - answer: Technically no strict limit, though keeping the hierarchy to 3‑5 levels
      maintains readability for end users.
    question: Is there a limit to how many bookmarks I can nest?
  - answer: It streams content and can process files over 1 GB without loading the
      entire document into memory, especially when you enable `PdfSaveOptions.setMemoryOptimization(true)`.
    question: How does Aspose.Words handle very large documents?
  - answer: Absolutely – use Aspose.PDF for Java to add, remove, or rename bookmarks
      in an existing PDF.
    question: Can I edit bookmarks after the PDF is created?
  type: FAQPage
tags:
- pdf bookmarks
- aspose.words
- java pdf generation
- document conversion
title: Aspose.Words for Java ile PDF yer imleri nasıl oluşturulur
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile PDF yer imleri nasıl oluşturulur

## Giriş
Okuyucuların bölümlere anında atlamasını sağlayan **PDF yer imleri oluşturmanız** gerekiyorsa, bu rehber Aspose.Words for Java ile bunu nasıl yapacağınızı adım adım gösterir. Kütüphaneyi kurmayı, iç içe yer imleri oluşturmayı, taslak seviyelerini atamayı ve profesyonel bir rapor gibi davranan şık bir PDF kaydetmeyi öğreneceksiniz.

**Öğrenecekleriniz**
- Aspose.Words for Java'ı kurma ve lisanslama  
- Word belgesinde iç içe yer imleri oluşturma  
- Hiyerarşik gezinme için yer imi taslak seviyelerini ayarlama  
- Belgeyi tam özellikli yer imleriyle PDF olarak dışa aktarma  

### Hızlı yanıtlar
- **Hangi kütüphane PDF yer imleri oluşturur?** Aspose.Words for Java.  
- **Bir lisansa ihtiyacım var mı?** Geliştirme için ücretsiz deneme sürümü çalışır; üretim için kalıcı bir lisans gereklidir.  
- **Maven kullanabilir miyim?** Evet – aşağıda gösterilen Maven bağımlılığını ekleyin.  
- **Hangi Java sürümü gerekiyor?** JDK 8 veya üzeri.  
- **Kaç yer imi seviyesi destekleniyor?** Sınırsız hiyerarşi, ancak okunabilirliği korumak için (genellikle 3‑5 seviye) tutun.

## PDF yer imleri oluşturmak nedir?
PDF yer imleri oluşturmak, PDF dosyasının içinde adlandırılmış gezinme noktaları gömerek okuyucuların bir ağaç görünümünü genişletip doğrudan bölümlere atlamasını sağlamaktır. Aspose.Words for Java, PDF dönüşüm sürecinde bu yer imlerini yazar ve kaynak Word belgesinde tanımladığınız hiyerarşiyi korur.

## Aspose.Words for Java ile PDF yer imleri oluşturmak neden tercih edilmeli?
Aspose.Words **35+ giriş ve çıkış formatını** destekler ve tipik bir sunucuda 500 sayfalık bir belgeyi 3 saniyeden kısa sürede PDF’ye dönüştürebilir. Yer imi motoru, Word başlıklarını otomatik olarak PDF taslak girişlerine eşler, Microsoft Word yüklü olmadan kesin kontrol sağlar.

## Önkoşullar
- **Kütüphaneler ve bağımlılıklar** – Aspose.Words for Java 25.3 ve üzeri.  
- **Geliştirme ortamı** – JDK 8+, IntelliJ IDEA veya Eclipse.  
- **Derleme aracı** – Maven veya Gradle (aşağıdaki örnekler).  
- **Temel Java bilgisi** – sınıflar, metodlar ve Maven/Gradle yapılandırması konusunda rahat olmalısınız.

## Aspose.Words Kurulumu
Projeye Aspose.Words bağımlılığını ekleyin.

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
Aspose.Words ticari bir üründür, ancak ücretsiz deneme tüm özellikleri keşfetmenizi sağlar.

1. **Ücretsiz deneme** – tam yetenekleri test etmek için [Aspose'un sürüm sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Geçici lisans** – kısa vadeli değerlendirme için [Aspose'un geçici lisans sayfasından](https://purchase.aspose.com/temporary-license/) talep edin.  
3. **Satın alma** – üretim kullanımı için kalıcı lisansı [Aspose'un satın alma portalından](https://purchase.aspose.com/buy) edinin.  

`.lic` dosyasını aldıktan sonra uygulama başlangıcında yükleyerek tüm özelliklerin kilidini açın.

## Uygulama rehberi
Aşağıda her adımı açıklayan kısa notlar ve yer tutucular bulunur. Yer tutucular, zaten sahip olduğunuz tam kod bloklarını temsil eder; değiştirmeyin.

### Word belgesinde iç içe yer imleri nasıl oluşturulur?
`Document` nesnesini yükleyin ve `DocumentBuilder` ile yer imleri ekleyin. Bu yöntem, yer imi hiyerarşisi üzerinde tam kontrol sağlar.

`Document`, bellek içindeki bir Word dosyasını temsil eder, `DocumentBuilder` ise içeriği oluşturmak ve değiştirmek için metodlar sunar.

#### Adım 1: belge ve oluşturucuyu başlatma
`Document` bellek içindeki tüm Word dosyasını temsil eder, `DocumentBuilder` ise geçerli imleç konumunda metin, tablo ve yer imleri eklemenizi sağlar.  
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```  

#### Adım 2: dış (üst) yer imini ekleme
PDF taslağında bir üst düğüm olarak davranacak ilk yer imini oluşturun.  
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```  

#### Adım 3: üst yer iminin içine alt yer imi ekleme
`startBookmark` ve `endBookmark` alt yer iminin aralığını tanımlar; dışa aktarımda otomatik olarak üst düğümün çocuğu olur.  
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```  

#### Adım 4: dış yer imini kapatma
Dış yer imini kapatmak, üst‑alt ilişkisinin tamamlanmasını sağlar.  
```java
builder.endBookmark("Bookmark 1");
```  

#### Adım 5: bağımsız üçüncü bir yer imi ekleme
İhtiyacınız kadar üst‑seviye yer imi ekleyebilirsiniz; her biri PDF taslağında ayrı bir giriş olarak görünür.  
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```  

### PDF dışa aktarımı için yer imi taslak seviyeleri nasıl yapılandırılır?
Taslak seviyeleri, PDF gezinme bölmesinde her yer iminin derinliğini belirler. Doğru ayarlamak, temiz ve katlanabilir bir ağaç oluşturur.

`PdfSaveOptions`, PDF dışa aktarım ayarlarını yapılandırır; yer imlerinin nasıl yazılacağını da içerir.

#### Adım 1: `PdfSaveOptions` ayarlama
`PdfSaveOptions`, PDF dönüşümünü ince ayar yapmanıza olanak tanır, yer imi işleme dahil.  
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```  

#### Adım 2: her yer imine taslak seviyeleri atama
`PdfSaveOptions.getBookmarkExportMode()` ve `PdfSaveOptions.setOutlineOptions()` kullanarak Word yer imlerinizi belirli taslak seviyelerine eşleyin.  
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```  

#### Adım 3: belgeyi PDF olarak kaydetme
`document.save("output.pdf", pdfSaveOptions)` çağrısı, tanımlı yer imi hiyerarşisiyle dosyayı yazar.  
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```  

### Yaygın sorunlar ve çözümler
- **Yer imleri eksik** – her `startBookmark` için eşleşen bir `endBookmark` olduğundan emin olun.  
- **Hiyerarşi hatalı** – alt yer imlerinin, üst yer iminin başlangıcından sonra ancak sonundan önce eklendiğini kontrol edin.  
- **Büyük dosyalarda performans düşüşü** – kaydetmeden önce `document.removeUnusedResources()` çağırarak bellek kullanımını azaltın.

## Pratik uygulamalar
PDF yer imlerini birçok gerçek dünya senaryosunda kullanabilirsiniz:

1. **Hukuki sözleşmeler** – maddelere, ek bölümlere ve eklerine anında atlama.  
2. **Yıllık raporlar** – finansal tablolar, yönetim tartışması ve dipnotlar gibi bölümlere paydaşların kolayca erişmesi.  
3. **E‑öğrenme materyalleri** – bölümler ve alt bölümler için tıklanabilir bir içerik tablosu oluşturma.  

## Performans değerlendirmeleri
- **Belge boyutu** – dışa aktarmadan önce `document.removeUnusedResources()` ile kullanılmayan stil ve görselleri temizleyin.  
- **Bellek yönetimi** – büyük dosyaları parçalara bölerek işleyin veya `Document.save(OutputStream, pdfSaveOptions)` ile PDF'yi akış olarak kaydedip yığını düşük tutun.  

## Kaynaklar
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/) – kapsamlı API referansı.  
- [Download Latest Releases](https://releases.aspose.com/words/java/) – en yeni kütüphane sürümlerini edinin.  
- [Purchase a License](https://purchase.aspose.com/buy) – üretim kullanımı için kalıcı lisans alın.  
- [Free Trial](https://releases.aspose.com/words/java/) – ürünü maliyetsiz değerlendirin.  
- [Temporary License Application](https://purchase.aspose.com/temporary-license/) – kısa vadeli lisans talep edin.  
- [Aspose Support Forum](https://forum.aspose.com/c/words/10) – topluluktan soru sorup yardım alın.  

## Sonuç
Artık Aspose.Words for Java kullanarak **PDF yer imleri oluşturma** ve taslak seviyelerini yapılandırma konusunda eksiksiz, üretim‑hazır bir yönteme sahipsiniz. Bu teknik, PDF'lerinizi gezinmesi kolay hâle getirir, kullanıcı deneyimini artırır ve profesyonel dokümantasyon standartlarını karşılar.

**Sonraki adımlar** – PDF API'si aracılığıyla yer imlerine özel simgeler eklemeyi deneyin veya bu iş akışını, gecelik olarak yüzlerce Word dosyasını dönüştüren bir toplu iş hizmetine entegre edin.

## Sıkça Sorulan Sorular

**S: Aspose.Words for Java nasıl kurulur?**  
C: Yukarıda gösterilen Maven veya Gradle bağımlılığını ekleyin, lisans dosyanızı sınıf yoluna yerleştirin ve `License license = new License(); license.setLicense("Aspose.Words.lic");` ile yükleyin.

**S: Taslak seviyeleri ayarlamadan yer imleri oluşturabilir miyim?**  
C: Evet, ancak PDF düz bir yer imi listesi gösterir ve derin gezinme zorlaşır.

**S: Kaç yer imi iç içe yerleştirilebilir?**  
C: Teknik olarak katı bir limit yoktur; ancak kullanıcı okunabilirliğini korumak için genellikle 3‑5 seviye önerilir.

**S: Aspose.Words çok büyük belgelerle nasıl başa çıkar?**  
C: İçeriği akış olarak işler ve 1 GB üzerindeki dosyaları tüm belgeyi belleğe yüklemeden işleyebilir; özellikle `PdfSaveOptions.setMemoryOptimization(true)` etkinleştirildiğinde.

**S: PDF oluşturulduktan sonra yer imlerini düzenleyebilir miyim?**  
C: Kesinlikle – mevcut bir PDF'de yer imlerini eklemek, kaldırmak veya yeniden adlandırmak için Aspose.PDF for Java kullanabilirsiniz.

---

**Son Güncelleme:** 2026-09-12  
**Test Edilen Versiyon:** Aspose.Words for Java 25.3  
**Yazar:** Aspose

## İlgili Eğitimler

- [Master Aspose.Words for Java: How to Insert and Manage Bookmarks in Word Documents](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [Using Bookmarks in Aspose.Words for Java](/words/java/document-manipulation/using-bookmarks/)
- [Saving Documents as PDF in Aspose.Words for Java](/words/java/document-loading-and-saving/saving-documents-as-pdf/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}