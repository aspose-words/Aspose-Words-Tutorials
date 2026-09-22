---
date: '2026-09-22'
description: Aspose.Words for Java kullanarak PDF'lerde bookmark levels nasıl ayarlanacağını
  öğrenin ve Word'ü nested bookmarks ile PDF'ye verimli bir şekilde dönüştürmeyi keşfedin.
keywords:
- how to set bookmark
- convert word to pdf
- add bookmarks to pdf
- generate pdf with bookmarks
- java create pdf bookmarks
lastmod: '2026-09-22'
og_description: Aspose.Words for Java kullanarak PDF'lerde bookmark levels nasıl ayarlanacağını
  öğrenin ve Word'ü nested bookmarks ile PDF'ye verimli bir şekilde dönüştürmeyi keşfedin.
og_image_alt: Developer guide showing how to set PDF bookmark outline levels using
  Aspose.Words for Java
og_title: Aspose.Words Java ile PDF'lerde bookmark levels nasıl ayarlanır
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Learn how to set bookmark levels in PDFs using Aspose.Words for Java,
    and discover how to convert Word to PDF with nested bookmarks efficiently.
  headline: How to set bookmark levels in PDFs with Aspose.Words Java
  type: TechArticle
- description: Learn how to set bookmark levels in PDFs using Aspose.Words for Java,
    and discover how to convert Word to PDF with nested bookmarks efficiently.
  name: How to set bookmark levels in PDFs with Aspose.Words Java
  steps:
  - name: '**Free trial** – download from [Aspose''s release page](https://releases.aspose.com/words/java/)
      to evaluate the full feature set.'
    text: '**Free trial** – download from [Aspose''s release page](https://releases.aspose.com/words/java/)
      to evaluate the full feature set.'
  - name: '**Temporary license** – request one at [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/)
      for short‑term projects.'
    text: '**Temporary license** – request one at [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/)
      for short‑term projects.'
  - name: '**Purchase** – obtain a perpetual license via the [Aspose’s purchasing
      portal](https://purchase.aspose.com/buy).'
    text: '**Purchase** – obtain a perpetual license via the [Aspose’s purchasing
      portal](https://purchase.aspose.com/buy).'
  - name: '**Initialize Document and Builder**'
    text: '**Initialize Document and Builder**'
  - name: '**Insert the outer bookmark**'
    text: '**Insert the outer bookmark**'
  - name: '**Nest a second bookmark inside the first**'
    text: '**Nest a second bookmark inside the first**'
  - name: '**Close the outer bookmark**'
    text: '**Close the outer bookmark**'
  - name: '**Add a separate third bookmark**'
    text: '**Add a separate third bookmark**'
  - name: '**Set up `PdfSaveOptions`**'
    text: '**Set up `PdfSaveOptions`**'
  - name: '**Assign outline levels** – the `PdfBookmark` class (available through
      `document.getBookmarks()`) stores the level for each bookmark. Levels range
      from 0 (root) to 9 (maximum).'
    text: '**Assign outline levels** – the `PdfBookmark` class (available through
      `document.getBookmarks()`) stores the level for each bookmark. Levels range
      from 0 (root) to 9 (maximum).'
  type: HowTo
- questions:
  - answer: Add the Maven or Gradle dependency shown earlier, then place your license
      file in the classpath and initialize it with `License license = new License();
      license.setLicense("Aspose.Words.Java.lic");`.
    question: How do I install Aspose.Words for Java?
  - answer: Yes, but without levels the PDF viewer shows a flat list, making navigation
      harder for long documents.
    question: Can I add bookmarks without setting outline levels?
  - answer: Technically up to nine levels are supported by the PDF specification;
      deeper nesting is ignored by most viewers.
    question: Is there a limit to how deep bookmarks can be nested?
  - answer: It processes documents page‑by‑page and offers memory‑saving options,
      allowing you to convert files with hundreds of pages without exhausting RAM.
    question: How does Aspose.Words handle very large PDFs?
  - answer: Yes – use Aspose.PDF for Java to modify, reorder, or delete bookmarks
      in an existing PDF.
    question: Can I edit the bookmarks after the PDF is saved?
  type: FAQPage
tags:
- pdf bookmarks
- aspose.words
- java pdf generation
- document outline
title: Aspose.Words Java ile PDF'lerde bookmark levels nasıl ayarlanır
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# PDF'lerde Aspose.Words Java ile yer imi seviyelerini nasıl ayarlarsınız

## Giriş
Word belgelerini dönüştürdükten sonra PDF yer imlerini düzenli tutmakta zorlanıyorsanız, doğru yerdesiniz. Bu öğreticide Aspose.Words for Java kullanarak PDF'lerde **yer imi ayarlama** ana hat seviyelerini gösteriyoruz, böylece okuyucularınız sonsuz kaydırma yapmadan doğru bölüme doğrudan atlayabilir.

**Neler öğreneceksiniz**
- Aspose.Words for Java'yı kurun ve lisanslayın
- Bir Word dosyası içinde iç içe yer imleri oluşturun
- Temiz PDF gezinmesi için yer imi ana hat seviyelerini yapılandırın
- Tam yapılandırılmış bir yer imi ağacıyla son PDF'yi kaydedin

### Hızlı cevaplar
- **İç içe yer imleri ekleyebilir miyim?** Evet – Aspose.Words, yer imlerini istediğiniz derinliğe kadar iç içe yerleştirmenize izin verir.
- **PDF çıktısı için lisansa ihtiyacım var mı?** Geçici veya satın alınmış bir lisans, tam PDF özelliklerini açar.
- **Hangi Java sürümü gereklidir?** Java 8 veya üzeri; kütüphane ayrıca Java 17 ile de uyumludur.
- **Kaç ana hat seviyesi destekleniyor?** PDF spesifikasyonuna uygun olarak en fazla 9 seviye.
- **Kaydetmeden sonra seviyeleri değiştirmek mümkün mü?** Kaydetmeden önce değiştirebilirsiniz, ancak PDF oluşturulduktan sonra değiştirilemez.

## Önkoşullar
- **Kütüphaneler**: Aspose.Words for Java ≥ 25.3.
- **Geliştirme ortamı**: JDK 8+ ve IntelliJ IDEA veya Eclipse gibi bir IDE.
- **Temel bilgi**: Java programlama temelleri ve Maven veya Gradle yapı araçları.

## Yer imi ayarlama nedir?
*Yer imi ayarlama*, her yer imine bir ana hat seviyesi atama sürecine denir, böylece PDF görüntüleyicileri onları hiyerarşik bir ağaçta gösterir. Bu seviyeleri tanımlayarak, düz bir bağlantı listesini sezgisel, daraltılabilir bir gezinme paneline dönüştürürsünüz.

## Yer imi ana hat seviyeleri için Aspose.Words neden kullanılmalı?
Aspose.Words, **35+ giriş formatını** (DOCX, ODT, RTF dahil) işleyebilir ve **PDF, XPS, HTML, EPUB ve daha fazlasına** dışa aktarabilir. Tipik bir sunucuda **500 sayfaya** kadar belgeleri **3 saniyenin** altında işleyerek, karmaşık düzenleri ve iç içe yer imi yapılarını Microsoft Word gerektirmeden korur.

## Aspose.Words kurulumu
Başlamak için, kütüphaneyi projenize ekleyin. Aşağıda, orijinal öğreticide zaten bulunan bağımlılık kod parçacıkları yer alıyor.

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
Aspose.Words ticari bir üründür, ancak ücretsiz deneme ile başlayabilirsiniz.

1. **Ücretsiz deneme** – tam özellik setini değerlendirmek için [Aspose'un sürüm sayfasından](https://releases.aspose.com/words/java/) indirin.  
2. **Geçici lisans** – kısa vadeli projeler için [Aspose'un geçici lisans sayfasından](https://purchase.aspose.com/temporary-license/) bir lisans isteyin.  
3. **Satın al** – [Aspose'un satın alma portalı](https://purchase.aspose.com/buy) üzerinden kalıcı bir lisans edinin.

`.lic` dosyasını edindikten sonra, uygulama başlangıcında yükleyerek tüm PDF‑ile ilgili yeteneklerin kilidini açın.

## Yer imi ana hat seviyelerini nasıl ayarlarsınız?
Word belgenizi yükleyin, iç içe yer imleri oluşturun, ana hat seviyelerini atayın ve sonunda PDF olarak kaydedin. Direkt cevap şu şekildedir:

> Bir `Document` nesnesi başlatın, `DocumentBuilder` kullanarak başlangıç/bitiş yer imlerini ekleyin, her yer iminin `OutlineLevel` değerini `PdfSaveOptions.getBookmarksOutlineLevel()` ile ayarlayın ve `document.save("output.pdf", saveOptions)` metodunu çağırın. Bu sıralama, yer imlerinin tam olarak tanımladığınız gibi hiyerarşik bir ağaçta göründüğü bir PDF oluşturur.

### Adım adım uygulama

#### İç içe yer imleri oluşturma
`DocumentBuilder`, Aspose.Words'ün bir belgeye programlı olarak metin, tablo, resim ve yer imleri eklemek için imleç tabanlı API'sidir.

1. **Document ve Builder'ı başlat**  
   ```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```  

2. **Dış yer imini ekle**  
   ```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```  

3. **İkinci yer imini birincinin içine iç içe ekle**  
   ```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```  

4. **Dış yer imini kapat**  
   ```java
builder.endBookmark("Bookmark 1");
```  

5. **Ayrı bir üçüncü yer imi ekle**  
   ```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```  

#### Yer imi ana hat seviyelerini yapılandırma
`PdfSaveOptions`, yer imlerinin PDF'ye nasıl yazıldığını, ana hat hiyerarşisini de kontrol etmenizi sağlar.

1. **`PdfSaveOptions`'ı ayarla**  
   ```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```  

2. **Ana hat seviyelerini ata** – `PdfBookmark` sınıfı (`document.getBookmarks()` üzerinden erişilebilir) her yer iminin seviyesini saklar. Seviyeler 0 (kök) ile 9 (maksimum) arasında değişir.  
   ```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```  

3. **PDF'yi kaydet**  
   ```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```  

## Yaygın sorunlar ve hata ayıklama
- **Eksik yer imleri** – her `startBookmark` bir `endBookmark` ile eşleşmelidir. Denge bozuksa builder bir istisna fırlatır.
- **Yanlış hiyerarşi** – alt yer imlerinin, ebeveyninin başlangıç etiketinden sonra ancak ebeveyninin bitiş etiketinden önce eklendiğini doğrulayın.
- **Büyük belgeler** – bellek kullanımını azaltmak için kaydetmeden önce `document.removeUnusedResources()` metodunu çağırın.

## Pratik uygulamalar
1. **Hukuki sözleşmeler** – maddelere, eklerine ve takvimlere hızlıca atlayın.
2. **Yıllık raporlar** – paydaşların bölümler, tablolar ve grafikler arasında tek bir tıklama ile gezinmesini sağlayın.
3. **E‑öğrenme modülleri** – bölümleri, dersleri ve sınavları sorunsuz bir öğrenme deneyimi için yapılandırın.

## Performans değerlendirmeleri
- **Kullanılmayan içeriği temizle** – PDF boyutunu minimumda tutmak için `document.removeUnusedResources()` kullanın.
- **Akış halinde kaydetme** – 200 MB'den büyük dosyalar için, tüm belgeyi RAM'e yüklememek amacıyla `PdfSaveOptions.setUseMemorySaving(true)` kullanın.

## Sıkça sorulan sorular

**S: Aspose.Words for Java nasıl kurulur?**  
**C:** Daha önce gösterilen Maven veya Gradle bağımlılığını ekleyin, ardından lisans dosyanızı sınıf yoluna koyun ve `License license = new License(); license.setLicense("Aspose.Words.Java.lic");` ile başlatın.

**S: Yer imlerini ana hat seviyeleri ayarlamadan ekleyebilir miyim?**  
**C:** Evet, ancak seviyeler olmadan PDF görüntüleyici düz bir liste gösterir, uzun belgelerde gezinmeyi zorlaştırır.

**S: Yer imleri ne kadar derine kadar iç içe yerleştirilebilir?**  
**C:** Teknik olarak PDF spesifikasyonu en fazla dokuz seviyeyi destekler; daha derin iç içe yerleştirmeler çoğu görüntüleyici tarafından göz ardı edilir.

**S: Aspose.Words çok büyük PDF'leri nasıl işler?**  
**C:** Belgeleri sayfa sayfa işler ve bellek‑tasarruf seçenekleri sunar, bu sayede yüzlerce sayfalık dosyaları RAM'i tüketmeden dönüştürebilirsiniz.

**S: PDF kaydedildikten sonra yer imlerini düzenleyebilir miyim?**  
**C:** Evet – mevcut bir PDF'deki yer imlerini değiştirmek, yeniden sıralamak veya silmek için Aspose.PDF for Java kullanın.

## Sonuç
Artık Aspose.Words for Java kullanarak PDF'lerde **yer imi ayarlama** ana hat seviyelerini nasıl ayarlayacağınızı biliyorsunuz. İç içe yer imleri oluşturarak ve hiyerarşik seviyeler atayarak, düz bir PDF'yi profesyonel, kullanıcı‑dostu bir belgeye dönüştürürsünüz. Farklı yapılarla deney yapın, bu tekniği diğer Aspose özellikleri (örneğin dijital imzalar veya filigranlar) ile birleştirin ve en yüksek etki için belge‑oluşturma süreçlerinize entegre edin.

---

**Son Güncelleme:** 2026-09-22  
**Test Edilen:** Aspose.Words for Java 25.3  
**Yazar:** Aspose  

**İlgili kaynaklar:** [Aspose.Words Documentation](https://reference.aspose.com/words/java/) | [Download Latest Releases](https://releases.aspose.com/words/java/) | [Purchase a License](https://purchase.aspose.com/buy) | [Free Trial](https://releases.aspose.com/words/java/) | [Temporary License Application](https://purchase.aspose.com/temporary-license/) | [Aspose Support Forum](https://forum.aspose.com/c/words/10)

## İlgili Öğreticiler

- [Aspose.Words for Java'da Ustalaşın: Word Belgelerinde Yer İmlerini Ekleme ve Yönetme](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [Aspose.Words for Java'da Yer İmlerini Kullanma](/words/java/document-manipulation/using-bookmarks/)
- [Aspose.Words for Java'da Belgeleri PDF Olarak Kaydetme](/words/java/document-loading-and-saving/saving-documents-as-pdf/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}