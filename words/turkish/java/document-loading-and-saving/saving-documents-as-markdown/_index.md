---
"description": "Word belgelerini Aspose.Words for Java ile Markdown'a nasıl dönüştüreceğinizi öğrenin. Bu adım adım kılavuz tablo hizalamasını, görüntü işlemeyi ve daha fazlasını kapsar."
"linktitle": "Belgeleri Markdown Olarak Kaydetme"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Java için Aspose.Words'de Belgeleri Markdown Olarak Kaydetme"
"url": "/tr/java/document-loading-and-saving/saving-documents-as-markdown/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Belgeleri Markdown Olarak Kaydetme


## Aspose.Words for Java'da Belgeleri Markdown Olarak Kaydetmeye Giriş

Bu adım adım kılavuzda, Aspose.Words for Java kullanarak belgeleri Markdown olarak nasıl kaydedeceğinizi göstereceğiz. Markdown, genellikle metin belgelerini biçimlendirmek için kullanılan hafif bir işaretleme dilidir. Aspose.Words for Java ile Word belgelerinizi kolayca Markdown biçimine dönüştürebilirsiniz. Tablo içerik hizalaması ve görselleri işleme dahil olmak üzere Markdown dosyalarını kaydetmenin farklı yönlerini ele alacağız.

## Ön koşullar

Başlamadan önce aşağıdaki ön koşullara sahip olduğunuzdan emin olun:

- Sisteminizde Java Development Kit (JDK) yüklü.
- Aspose.Words for Java kütüphanesi. Buradan indirebilirsiniz [Burada](https://releases.aspose.com/words/java/).

## Adım 1: Bir Word Belgesi Oluşturma

Daha sonra Markdown formatına dönüştüreceğimiz bir Word belgesi oluşturarak başlayalım. Bu belgeyi ihtiyaçlarınıza göre özelleştirebilirsiniz.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// İki hücreli bir tablo ekle
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Belgeyi Markdown olarak kaydedin
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

Bu örnekte, iki hücreli basit bir tablo oluşturuyoruz ve bu hücrelerdeki paragrafların hizalamasını ayarlıyoruz. Ardından, belgeyi Markdown olarak kaydediyoruz `MarkdownSaveOptions`.

## Adım 2: Tablo İçeriği Hizalamasını Özelleştirin

Java için Aspose.Words, Markdown olarak kaydederken tablo içeriğinin hizalamasını özelleştirmenize olanak tanır. Tablo içeriğini sola, sağa, ortaya hizalayabilir veya her tablo sütunundaki ilk paragrafa göre otomatik olarak belirlenmesine izin verebilirsiniz.

Tablo içeriği hizalamasını özelleştirme yöntemi:

```java
// Tablo içeriğinin hizalamasını sola ayarlayın
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Tablo içeriğinin hizalamasını sağa ayarla
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Tablo içeriği hizalamasını ortaya ayarlayın
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Tablo içerik hizalamasını otomatik olarak ayarlayın (ilk paragraf tarafından belirlenir)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Değiştirerek `TableContentAlignment` özelliğiyle, Markdown'a dönüştürülürken tabloların içindeki içeriğin nasıl hizalanacağını kontrol edebilirsiniz.

## Adım 3: Görüntülerin İşlenmesi

Markdown belgenize resimler eklemek için resimlerin bulunduğu klasörü belirtmeniz gerekir. Java için Aspose.Words, resimler klasörünü `MarkdownSaveOptions`.

İşte images klasörünü nasıl ayarlayacağınız ve belgeyi images ile nasıl kaydedeceğiniz:

```java
// Görüntüler içeren bir belge yükleyin
Document doc = new Document("document_with_images.docx");

// Görüntüler klasör yolunu ayarlayın
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Belgeyi resimlerle birlikte kaydedin
doc.save("document_with_images.md", saveOptions);
```

Değiştirdiğinizden emin olun `"document_with_images.docx"` resim ve dosyaları içeren Word belgenize giden yol ile `"images_folder/"` Resimlerinizin saklandığı klasörün gerçek yolunu belirtin.

## Java için Aspose.Words'de Belgeleri Markdown Olarak Kaydetmek İçin Tam Kaynak Kodu

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Tablonun içindeki tüm paragrafların hizalanmasını sağlar.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// Bu durumda hizalama, ilgili tablo sütunundaki ilk paragraftan alınacaktır.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Çözüm

Bu kılavuzda, Java için Aspose.Words kullanarak belgeleri Markdown olarak nasıl kaydedeceğinizi inceledik. Bir Word belgesinin oluşturulmasını, tablo içeriği hizalamasını özelleştirmeyi ve Markdown dosyalarındaki resimleri işlemeyi ele aldık. Artık Word belgelerinizi Markdown biçimine verimli bir şekilde dönüştürebilir, bunları çeşitli yayın platformları ve belge gereksinimleri için uygun hale getirebilirsiniz.

## SSS

### Java için Aspose.Words'ü nasıl yüklerim?

Java için Aspose.Words, Java projenize kütüphaneyi ekleyerek yüklenebilir. Kütüphaneyi şu adresten indirebilirsiniz: [Burada](https://releases.aspose.com/words/java/) ve dokümanlarda verilen kurulum talimatlarını izleyin.

### Tablo ve resim içeren karmaşık Word belgelerini Markdown'a dönüştürebilir miyim?

Evet, Aspose.Words for Java, tablolar, resimler ve çeşitli biçimlendirme öğeleri içeren karmaşık Word belgelerinin Markdown'a dönüştürülmesini destekler. Markdown çıktısını belgenizin karmaşıklığına göre özelleştirebilirsiniz.

### Markdown dosyalarındaki görselleri nasıl işleyebilirim?

Markdown dosyalarına resim eklemek için, resim klasör yolunu kullanarak ayarlayın `setImagesFolder` yöntem `MarkdownSaveOptions`Görüntü dosyalarının belirtilen klasörde saklandığından emin olun; Aspose.Words for Java, görüntü referanslarını buna göre işleyecektir.

### Aspose.Words for Java'nın deneme sürümü mevcut mu?

Evet, Aspose.Words for Java'nın deneme sürümünü Aspose web sitesinden edinebilirsiniz. Deneme sürümü, lisans satın almadan önce kütüphanenin yeteneklerini değerlendirmenize olanak tanır.

### Daha fazla örnek ve dokümanı nerede bulabilirim?

Aspose.Words for Java hakkında daha fazla örnek, belge ve ayrıntılı bilgi için lütfen şu adresi ziyaret edin: [belgeleme](https://reference.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}