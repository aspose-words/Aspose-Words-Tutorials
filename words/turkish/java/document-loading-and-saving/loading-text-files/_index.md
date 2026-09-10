---
date: 2025-12-27
description: Aspose.Words for Java kullanarak yön ayarlamayı, txt dosyalarını yüklemeyi,
  boşlukları kırpmayı ve txt'yi docx'e dönüştürmeyi öğrenin.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java ile Yön Ayarlama ve Metin Dosyalarını Yükleme
url: /tr/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile Yön Ayarlama ve Metin Dosyalarını Yükleme

## Aspose.Words for Java ile Metin Dosyalarını Yüklemeye Giriş

Bu rehberde, düz‑metin belgelerini yüklerken **yönü nasıl ayarlayacağınızı** keşfedecek ve Aspose.Words for Java kullanarak **txt dosyalarını yükleme**, **boşlukları kırpma** ve **txt'yi docx'e dönüştürme** yollarını pratik örneklerle göreceksiniz. İster bir belge‑dönüştürme servisi oluşturuyor olun, ister liste algılaması üzerinde ince ayar yapmanız gereksin, bu öğretici her adımı açık açıklamalar ve çalıştırmaya hazır kodlarla size sunar.

## Hızlı Yanıtlar
- **Yüklenen bir TXT dosyası için metin yönünü nasıl ayarlarım?** `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` kullanın veya `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT` belirleyin.  
- **Aspose.Words düz metinde numaralı listeleri algılayabilir mi?** Evet – `TxtLoadOptions` içinde `DetectNumberingWithWhitespaces` özelliğini etkinleştirin.  
- **Baş ve son boşlukları nasıl kırparım?** `TxtLeadingSpacesOptions.TRIM` ve `TxtTrailingSpacesOptions.TRIM` ayarlayın.  
- **Bir TXT dosyasını tek satırda DOCX'e dönüştürmek mümkün mü?** `TxtLoadOptions` ile TXT'yi yükleyin ve `Document.save("output.docx")` çağırın.  
- **Hangi Java sürümü gerekiyor?** Aspose.Words 24.x için Java 8+ yeterlidir.

## Aspose.Words'ta “yön ayarlama” nedir?
Bir metin dosyası sağ‑dan‑sol scriptler (ör. İbranice veya Arapça) içerdiğinde, kütüphanenin okuma sırasını bilmesi gerekir. `DocumentDirection` enum'ı, **yönü** manuel olarak ayarlamanıza ya da Aspose'un otomatik algılamasına izin verir; böylece doğru yerleşim ve bidi biçimlendirme sağlanır.

## TXT dosyalarını yüklemek için Aspose.Words neden tercih edilmeli?
- **Doğru liste algılama** – numaralı, madde işaretli ve boşluk‑tabanlı listeleri işler.  
- **İnce boşluk kontrolü** – baştaki ve sondaki boşlukları kırpabilir veya koruyabilirsiniz.  
- **Otomatik metin‑yönü algılama** – çok dilli belgeler için idealdir.  
- **Tek adımda dönüşüm** – bir `.txt` dosyasını `.docx`, `.pdf` veya desteklenen diğer formatlara kaydedin.

## Ön Koşullar
- Java 8 veya daha yeni bir sürüm.  
- Aspose.Words for Java kütüphanesi (Maven/Gradle bağımlılığını ekleyin veya JAR dosyasını projenize dahil edin).  
- Java I/O akışları hakkında temel bilgi.

## Adım‑Adım Kılavuz

### Adım 1: Listeleri Algılama (txt nasıl yüklenir)
Bir metin belgesini yükleyip listeleri otomatik algılamak için bir `TxtLoadOptions` nesnesi oluşturun ve liste algılamayı etkinleştirin. Aşağıdaki kod, çeşitli liste stillerini gösterir ve boşluk‑duyarlı numaralandırmayı etkinleştirir.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
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
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Pro ipucu:** Yalnızca temel liste algılamasına ihtiyacınız varsa, boşluk seçeneğini atlayabilirsiniz – Aspose hâlâ standart `1.` ve `1)` kalıplarını tanıyacaktır.

### Adım 2: Boşluk Seçeneklerini Yönetme (boşlukları nasıl kırparım)
Baş ve son boşluklar genellikle biçimlendirme hatalarına yol açar. Bu davranışı kontrol etmek için `TxtLeadingSpacesOptions` ve `TxtTrailingSpacesOptions` kullanın.

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

> **Neden önemli:** Boşlukları kırpmak, ortaya çıkan DOCX'te istenmeyen girintileri önler ve belgeyi manuel post‑işlem yapmadan temiz bir görünüme kavuşturur.

### Adım 3: Metin Yönünü Kontrol Etme (yön nasıl ayarlanır)
Sağ‑dan‑sol diller için belge yönünü yüklemeden önce ayarlayın. Aşağıdaki örnek bir İbranice metin dosyasını yükler ve yönü doğrulamak için bidi bayrağını yazdırır.

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

> **Yaygın tuzak:** `DocumentDirection` ayarlamayı unutmak, Arapça/İbranice karakterlerin yanlış sırada görünmesine neden olur.

### Aspose.Words for Java ile Metin Dosyalarını Yüklemek için Tam Kaynak Kodu
Aşağıda, liste algılamayı, boşluk yönetimini ve yön kontrolünü birleştiren, çalıştırmaya hazır tam kaynak kodu yer alıyor. Tek bir sınıfa kopyalayıp üç test metodunu ayrı ayrı çalıştırabilirsiniz.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
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
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
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

## Yaygın Sorunlar ve Çözümler
| Sorun | Neden | Çözüm |
|-------|-------|------|
| Listeler algılanmıyor | `DetectNumberingWithWhitespaces` boş bırakıldı | `loadOptions.setDetectNumberingWithWhitespaces(true)` etkinleştirin |
| Yüklemeden sonra ekstra girinti | Baştaki boşluklar korundu | `TxtLeadingSpacesOptions.TRIM` ayarlayın |
| İbranice metin ters görünüyor | Belge yönü ayarlanmamış veya `LEFT_TO_RIGHT` olarak ayarlanmış | `DocumentDirection.AUTO` veya `RIGHT_TO_LEFT` kullanın |
| Çıktı DOCX boş | Giriş akışı ikinci yüklemeden önce sıfırlanmadı | Her yükleme çağrısı için yeni `ByteArrayInputStream` oluşturun |

## Sıkça Sorulan Sorular

### S: Aspose.Words for Java nedir?
C: Aspose.Words for Java, geliştiricilerin Java uygulamalarında Word belgelerini programatik olarak oluşturmasına, düzenlemesine ve dönüştürmesine olanak tanıyan güçlü bir belge işleme kütüphanesidir. Basit metin yüklemeden karmaşık biçimlendirme ve dönüşüm özelliklerine kadar geniş bir yelpazeyi destekler.

### S: Aspose.Words for Java ile nasıl başlayabilirim?
C: 1. Aspose.Words for Java kütüphanesini indirin ve kurun. 2. Ayrıntılı bilgi ve örnekler için [Aspose.Words for Java API Referansı](https://reference.aspose.com/words/java/) sayfasına bakın. 3. Kütüphaneyi etkili bir şekilde kullanmayı öğrenmek için örnek kodları ve öğreticileri inceleyin.

### S: Aspose.Words for Java ile bir metin belgesi nasıl yüklenir?
C: `TxtLoadOptions` sınıfını `Document` yapıcısı ile birlikte kullanın. Liste algılama, boşluk yönetimi veya metin yönü gibi seçenekleri, yukarıdaki adım‑adım bölümlerinde gösterildiği gibi belirtin.

### S: Yüklenen bir metin belgesini başka formatlara dönüştürebilir miyim?
C: Evet. TXT dosyasını bir `Document` nesnesine yükledikten sonra `doc.save("output.pdf")`, `doc.save("output.docx")` veya desteklenen diğer formatlardan birini çağırın.

### S: Yüklenen metin belgelerinde boşlukları nasıl yönetirim?
C: `TxtLeadingSpacesOptions` ve `TxtTrailingSpacesOptions` ile baştaki ve sondaki boşlukları kontrol edin. İstenmeyen boşlukları kaldırmak için `TRIM`, orijinal boşlukları korumak için `PRESERVE` ayarlayın.

### S: Aspose.Words for Java’da metin yönünün önemi nedir?
C: Metin yönü, sağ‑dan‑sol scriptlerin (İbranice, Arapça vb.) doğru şekilde render edilmesini sağlar. `DocumentDirection` ayarlayarak, bidi metnin sonuç belgesinde düzgün görüntülenmesini garantilersiniz.

### S: Aspose.Words for Java için daha fazla kaynak ve destek nerede bulunur?
C: API referansları, kod örnekleri ve ayrıntılı kılavuzlar için [Aspose.Words for Java Dokümantasyonu](https://reference.aspose.com/words/java/) sayfasını ziyaret edin. Aspose topluluk forumlarına katılabilir veya belirli sorular için Aspose desteğiyle iletişime geçebilirsiniz.

### S: Aspose.Words for Java ticari projeler için uygun mu?
C: Evet. Kişisel ve ticari kullanım için lisans seçenekleri sunar. Projeniz için uygun planı seçmek üzere Aspose web sitesindeki lisans koşullarını inceleyin.

## Sonuç
Artık **txt dosyalarını yükleme**, **listeleri algılama**, **boşlukları kırpma** ve **yön ayarlama** konularında tam bir araç setine sahipsiniz; bu sayede Aspose.Words for Java ile düz‑metni zengin Word belgelerine dönüştürürken belge iş akışlarını otomatikleştirebilir, çok dilli desteği artırabilir ve her seferinde temiz, profesyonel çıktılar elde edebilirsiniz.

---

**Son Güncelleme:** 2025-12-27  
**Test Edilen Versiyon:** Aspose.Words for Java 24.12  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}