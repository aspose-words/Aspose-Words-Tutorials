---
title: Java için Aspose.Words'de Başlıklar ve Altbilgiler Kullanımı
linktitle: Başlıklar ve Altbilgileri Kullanma
second_title: Aspose.Words Java Belge İşleme API'si
description: Aspose.Words for Java'da başlık ve altbilgilerin nasıl kullanılacağını adım adım öğrenin. Zahmetsizce profesyonel belgeler oluşturun.
weight: 16
url: /tr/java/using-document-elements/using-headers-and-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Başlıklar ve Altbilgiler Kullanımı


Bu kapsamlı kılavuzda, Aspose.Words for Java'da başlıklar ve altbilgilerle çalışma sürecinde size yol göstereceğiz. Başlıklar ve altbilgiler belge biçimlendirmede temel öğelerdir ve Aspose.Words bunları ihtiyaçlarınıza göre oluşturmanız ve özelleştirmeniz için güçlü araçlar sunar.

Şimdi bu adımların her birini detaylı olarak inceleyelim.

## 1. Aspose.Words'e Giriş

Aspose.Words, Word belgelerini programatik olarak oluşturmanıza, düzenlemenize ve işlemenize olanak tanıyan güçlü bir Java API'sidir. Başlıklar ve altbilgiler dahil olmak üzere belge biçimlendirme için kapsamlı özellikler sağlar.

## 2. Java Ortamınızı Kurma

 Aspose.Words'ü kullanmaya başlamadan önce, Java geliştirme ortamınızın doğru şekilde ayarlandığından emin olun. Gerekli kurulum talimatlarını Aspose.Words dokümantasyon sayfasında bulabilirsiniz:[Aspose.Words Java Belgeleri](https://reference.aspose.com/words/java/).

## 3. Yeni Bir Belge Oluşturma

Başlıklar ve altbilgilerle çalışmak için Aspose.Words kullanarak yeni bir belge oluşturmanız gerekir. Aşağıdaki kod bunu nasıl yapacağınızı gösterir:

```java
// Yeni bir belge oluşturmak için Java kodu
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. Sayfa Düzenini Anlamak

 Sayfa düzeni, belgenizin düzenini kontrol etmek için çok önemlidir. Başlıklar ve altbilgilerle ilgili çeşitli özellikleri kullanarak belirtebilirsiniz.`PageSetup` sınıf. Örneğin:

```java
// Sayfa özelliklerini ayarlama
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. Farklı İlk Sayfa Üstbilgisi/Altbilgisi

Aspose.Words, belgenizin ilk sayfası için farklı üstbilgiler ve altbilgiler kullanmanıza olanak tanır.`pageSetup.setDifferentFirstPageHeaderFooter(true);` Bu özelliği etkinleştirmek için.

## 6. Başlıklarla Çalışma

### 6.1. Başlıklara Metin Ekleme

 Başlıklara metin eklemek için şunu kullanabilirsiniz:`DocumentBuilder`İşte bir örnek:

```java
// İlk sayfa başlığına metin ekleme
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. Başlıklara Resim Ekleme

 Başlıklara resim eklemek için şunu kullanabilirsiniz:`insertImage` yöntem. İşte bir örnek:

```java
// Başlığa bir resim ekleme
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. Başlık Stillerini Özelleştirme

Yukarıdaki örneklerde gösterildiği gibi, yazı tipi, hizalama ve daha fazlası gibi çeşitli özellikleri ayarlayarak başlık stillerini özelleştirebilirsiniz.

## 7. Altbilgilerle Çalışma

### 7.1. Altbilgilere Metin Ekleme

 Başlıklara benzer şekilde, altbilgilere de metin ekleyebilirsiniz.`DocumentBuilder`İşte bir örnek:

```java
// Birincil alt bilgiye metin ekleme
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// Gerektiği gibi metin ve alanlar ekleyin
```

### 7.2. Altbilgilere Resim Ekleme

 Altbilgilere resim eklemek için şunu kullanın:`insertImage` Başlıklarda olduğu gibi yöntem.

### 7.3. Altbilgi Stillerini Özelleştirme

 Altbilgi stillerini özelleştirmek için şunu kullanın:`DocumentBuilder`başlıkları özelleştirmeye benzer.

## 8. Sayfa Numaralandırması

 Başlık ve altbilgilerinize şu alanları kullanarak sayfa numaraları ekleyebilirsiniz:`PAGE` Ve`NUMPAGES`. Sayfa ekledikçe veya kaldırdıkça bu alanlar otomatik olarak güncellenir.

## 9. Altbilgilerdeki Telif Hakkı Bilgileri

Belgenizin altbilgisine telif hakkı bilgisi eklemek için, kod parçacığında gösterildiği gibi, biri sola, diğeri sağa hizalanmış iki hücreden oluşan bir tablo kullanabilirsiniz.

## 10. Birden Fazla Bölümle Çalışma

Aspose.Words, bir belge içinde birden fazla bölümle çalışmanıza olanak tanır. Her bölüm için farklı sayfa düzenleri ve üstbilgiler/altbilgiler ayarlayabilirsiniz.

## 11. Manzara Yönü

İhtiyaç duyduğunuzda belirli bölümlerin yönünü yatay moda değiştirebilirsiniz.

## 12. Önceki Bölümlerden Başlıkları/Altbilgileri Kopyalama

Karmaşık belgeler oluştururken önceki bölümlerden üstbilgi ve altbilgileri kopyalamak zaman kazandırabilir.

## 13. Belgenizi Kaydetme

Belgenizi oluşturup özelleştirdikten sonra, onu kullanarak kaydetmeyi unutmayın.`doc.save()` yöntem.

## Tam Kaynak Kodu
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // İlk sayfanın üstbilgilerinin/altbilgilerinin diğer sayfalardan farklı olmasını isteyip istemediğimizi belirtin.
        // Ayrıca, belirtmek için PageSetup.OddAndEvenPagesHeaderFooter özelliğini de kullanabilirsiniz.
        // tek ve çift sayfalar için farklı üstbilgiler/altbilgiler.
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        // Başlığın üst/sol köşesine konumlandırılmış bir resim ekleyin.
        // Sayfanın üst/sol kenarlarından uzaklık 10 punto olarak ayarlanmıştır.
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // Satırdaki metnin bir kısmını (sayfa numaralandırmasıyla) oluşturmak için iki hücreli bir tablo kullanıyoruz.
        // Sola hizalanacak, metnin diğer kısmı (telif hakkı olan) ise sağa hizalanacak.
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // Mevcut sayfa numarasını ve sayfa sayısını otomatik olarak hesaplamak için PAGE ve NUMPAGES alanlarını kullanır.
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        // Birincil üstbilgilerin/altbilgilerin görüleceği ikinci bir sayfa oluşturmak için sayfa sonu oluşturun.
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // Bu bölümün ayrı bir ilk sayfa üstbilgisi/altbilgisine ihtiyacı yoktur, belgede yalnızca bir başlık sayfasına ihtiyacımız vardır.
        //ve bu sayfanın üstbilgisi/altbilgisi daha önceki bölümde tanımlanmıştır.
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // Bu bölüm, önceki bölümden başlıkları/altbilgileri görüntüler
        // varsayılan olarak bu sayfa genişliğini iptal etmek için currentSection.HeadersFooters.LinkToPrevious(false) çağırın
        // yeni bölüm için farklıdır ve bu nedenle altbilgi tablosu için farklı hücre genişlikleri ayarlamamız gerekir.
        currentSection.getHeadersFooters().linkToPrevious(false);
        // Bu bölüm için halihazırda var olan header/footer setini kullanmak istiyorsak.
        // Ancak bazı küçük değişikliklerle, başlıkları/altbilgileri kopyalamak uygun olabilir
        // Önceki bölümden gerekli değişiklikleri yapıp istediğimiz yere uygulayabiliriz.
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
copyHeadersFootersFromPreviousSection yönteminin kaynak kodu
```java
    /// <özet>
    /// Önceki bölümdeki üstbilgileri/altbilgileri belirtilen bölüme kopyalar ve klonlar.
    /// </özet>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## Çözüm

Bu eğitimde, Java için Aspose.Words'de başlıklar ve altbilgilerle çalışmanın temellerini ele aldık. Başlıklar ve altbilgileri nasıl oluşturacağınızı, özelleştireceğinizi ve biçimlendireceğinizi ve diğer temel belge biçimlendirme tekniklerini öğrendiniz.

 Daha fazla ayrıntı ve gelişmiş özellikler için şuraya bakın:[Aspose.Words Java Belgeleri](https://reference.aspose.com/words/java/).

## SSS

### 1. Belgemin alt bilgisine sayfa numaraları nasıl ekleyebilirim?
 Sayfa numaralarını ekleyerek sayfa numaraları ekleyebilirsiniz.`PAGE` Aspose.Words kullanarak alanı alt bilgiye ekleyin.

### 2. Aspose.Words Java geliştirme ortamlarıyla uyumlu mudur?
Evet, Aspose.Words Java geliştirme desteği sağlar. Gerekli kurulumunuzun yerinde olduğundan emin olun.

### 3. Üstbilgi ve altbilgilerin yazı tipini ve stilini özelleştirebilir miyim?
Elbette, başlıklarınız ve altbilgilerinizin görsel olarak çekici olmasını sağlamak için yazı tiplerini, hizalamayı ve diğer stilleri özelleştirebilirsiniz.

### 4. Tek ve çift sayfalar için farklı başlıklar kullanmak mümkün müdür?
 Evet, kullanabilirsiniz`PageSetup.OddAndEvenPagesHeaderFooter` tek ve çift sayfalar için farklı başlıklar belirtmek.

### 5. Aspose.Words for Java'yı kullanmaya nasıl başlarım?
 Başlamak için, şu adresi ziyaret edin:[Aspose.Words Java Belgeleri](https://reference.aspose.com/words/java/) API'yi kullanma konusunda kapsamlı rehberlik için.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
