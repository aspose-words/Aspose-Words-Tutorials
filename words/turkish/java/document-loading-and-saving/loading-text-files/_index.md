---
"description": "Java için Aspose.Words'ün Gücünü Açın. Metin Belgelerini Yüklemeyi, Listeleri Yönetmeyi, Boşlukları Yönetmeyi ve Metin Yönünü Kontrol Etmeyi Öğrenin."
"linktitle": "Metin Dosyalarını Yükleme"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Java için Aspose.Words ile Metin Dosyalarını Yükleme"
"url": "/tr/java/document-loading-and-saving/loading-text-files/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words ile Metin Dosyalarını Yükleme


## Java için Aspose.Words ile Metin Dosyalarını Yüklemeye Giriş

Bu kılavuzda, Java için Aspose.Words kullanarak metin dosyalarının nasıl yükleneceğini ve Word belgeleri olarak nasıl işleneceğini inceleyeceğiz. Listeleri algılama, boşlukları yönetme ve metin yönünü kontrol etme gibi çeşitli yönleri ele alacağız.

## Adım 1: Listeleri Algılama

Bir metin belgesini yüklemek ve listeleri algılamak için şu adımları izleyebilirsiniz:

```java
// Liste olarak yorumlanabilecek parçalar içeren bir dize biçiminde düz metin belgesi oluşturun.
// Yükleme sırasında, ilk üç liste her zaman Aspose.Words tarafından algılanacaktır.
// ve yüklendikten sonra bunlar için Liste nesneleri oluşturulacaktır.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// Dördüncü liste, liste numarası ile liste öğesi içerikleri arasında boşluk bulunan,
// yalnızca bir LoadOptions nesnesindeki "DetectNumberingWithWhitespaces" true olarak ayarlandığında bir liste olarak algılanacaktır,
// sayılarla başlayan paragrafların yanlışlıkla liste olarak algılanmasını önlemek için.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// LoadOptions'ı parametre olarak uygulayarak belgeyi yükleyin ve sonucu doğrulayın.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

Bu kod, çeşitli liste biçimlerine sahip bir metin belgesinin nasıl yükleneceğini ve kullanılacağını gösterir. `DetectNumberingWithWhitespaces` Listeleri doğru bir şekilde algılama seçeneği.

## Adım 2: Alan Seçeneklerini İşleme

Bir metin belgesi yüklenirken öndeki ve arkadaki boşlukları kontrol etmek için aşağıdaki kodu kullanabilirsiniz:

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

Bu örnekte, bir metin belgesi yüklüyoruz ve öndeki ve arkadaki boşlukları kullanarak kırpıyoruz `TxtLeadingSpacesOptions.TRIM` Ve `TxtTrailingSpacesOptions.TRIM`.

## Adım 3: Metin Yönünü Kontrol Etme

Bir metin belgesini yüklerken metin yönünü belirtmek için aşağıdaki kodu kullanabilirsiniz:

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

Bu kod, belge yönünü otomatik algılamaya ayarlar (`DocumentDirection.AUTO`) ve İbranice metin içeren bir metin belgesi yükler. Belge yönünü gerektiği gibi ayarlayabilirsiniz.

## Java için Aspose.Words ile Metin Dosyalarını Yüklemek İçin Tam Kaynak Kodu

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Liste olarak yorumlanabilecek parçalar içeren bir dize biçiminde düz metin belgesi oluşturun.
	// Yükleme sırasında, ilk üç liste her zaman Aspose.Words tarafından algılanacaktır.
	// ve yüklendikten sonra bunlar için Liste nesneleri oluşturulacaktır.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// Dördüncü liste, liste numarası ile liste öğesi içerikleri arasında boşluk bulunan,
	// yalnızca bir LoadOptions nesnesindeki "DetectNumberingWithWhitespaces" true olarak ayarlandığında bir liste olarak algılanacaktır,
	// sayılarla başlayan paragrafların yanlışlıkla liste olarak algılanmasını önlemek için.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// LoadOptions'ı parametre olarak uygulayarak belgeyi yükleyin ve sonucu doğrulayın.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Çözüm

Bu kılavuzda, Java için Aspose.Words kullanarak metin dosyalarının nasıl yükleneceğini, listelerin nasıl algılanacağını, boşlukların nasıl işleneceğini ve metin yönünün nasıl kontrol edileceğini inceledik. Bu teknikler, Java uygulamalarınızda metin belgelerini etkili bir şekilde düzenlemenize olanak tanır.

## SSS

### Java için Aspose.Words nedir?

Aspose.Words for Java, geliştiricilerin Java uygulamalarında Word belgelerini programatik olarak oluşturmalarına, düzenlemelerine ve dönüştürmelerine olanak tanıyan güçlü bir belge işleme kütüphanesidir. Metin, tablo, resim ve diğer belge öğeleriyle çalışmak için çok çeşitli özellikler sunar.

### Aspose.Words for Java'yı nasıl kullanmaya başlayabilirim?

Aspose.Words for Java'yı kullanmaya başlamak için şu adımları izleyin:
1. Aspose.Words for Java kütüphanesini indirin ve kurun.
2. Belgelere şu adresten bakın: [Aspose.Words for Java API Referansı](https://reference.aspose.com/words/java/) Detaylı bilgi ve örnekler için.
3. Kütüphaneyi etkili bir şekilde nasıl kullanacağınızı öğrenmek için örnek kodları ve eğitimleri inceleyin.

### Aspose.Words for Java kullanarak bir metin belgesini nasıl yüklerim?

Java için Aspose.Words kullanarak bir metin belgesi yüklemek için şunu kullanabilirsiniz: `TxtLoadOptions` sınıf ve `Document` sınıf. Gerektiğinde boşlukları ve metin yönünü işlemek için uygun seçenekleri belirttiğinizden emin olun. Ayrıntılı bir örnek için bu makaledeki adım adım kılavuza bakın.

### Yüklenen bir metin belgesini başka biçimlere dönüştürebilir miyim?

Evet, Java için Aspose.Words, yüklenen bir metin belgesini DOCX, PDF ve daha fazlası dahil olmak üzere çeşitli biçimlere dönüştürmenize olanak tanır. `Document` dönüştürmeleri gerçekleştirmek için sınıf. Belirli dönüştürme örnekleri için belgelere bakın.

### Yüklenen metin belgelerindeki boşlukları nasıl hallederim?

Yüklenen metin belgelerinde öndeki ve arkadaki boşlukların nasıl işleneceğini kontrol edebilirsiniz. `TxtLoadOptions`. Gibi seçenekler `TxtLeadingSpacesOptions` Ve `TxtTrailingSpacesOptions` ihtiyaç duyduğunuzda alanları kırpmanıza veya korumanıza olanak tanır. Bir örnek için bu kılavuzdaki "Alanları Yönetme Seçenekleri" bölümüne bakın.

### Aspose.Words for Java'da metin yönünün önemi nedir?

İbranice veya Arapça gibi karma yazılar veya diller içeren belgeler için metin yönü önemlidir. Java için Aspose.Words, metin yönünü belirtmek için seçenekler sunar ve bu dillerde metnin düzgün bir şekilde işlenmesini ve biçimlendirilmesini sağlar. Bu kılavuzdaki "Metin Yönünü Kontrol Etme" bölümü, metin yönünün nasıl ayarlanacağını gösterir.

### Aspose.Words for Java için daha fazla kaynak ve desteği nerede bulabilirim?

Ek kaynaklar, belgeler ve destek için şu adresi ziyaret edin: [Java Belgeleri için Aspose.Words](https://reference.aspose.com/words/java/)Ayrıca Aspose.Words topluluk forumlarına katılabilir veya belirli sorunlar veya sorularınızla ilgili yardım almak için Aspose destek ekibiyle iletişime geçebilirsiniz.

### Aspose.Words for Java ticari projeler için uygun mudur?

Evet, Aspose.Words for Java hem kişisel hem de ticari projeler için uygundur. Çeşitli kullanım senaryolarına uyum sağlamak için lisanslama seçenekleri sunar. Projeniz için uygun lisansı seçmek üzere Aspose web sitesindeki lisanslama koşullarını ve fiyatlandırmayı incelediğinizden emin olun.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}