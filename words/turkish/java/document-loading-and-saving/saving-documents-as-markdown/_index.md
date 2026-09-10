---
date: 2025-12-22
description: Aspose.Words for Java ile Word belgelerini Markdown’a dönüştürerek markdown
  dışa aktarmayı öğrenin. Bu adım adım kılavuz, tablo hizalaması, resim işleme ve
  daha fazlasını kapsar.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java ile Markdown Nasıl Dışa Aktarılır
url: /tr/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile Markdown Nasıl Dışa Aktarılır

## Aspose.Words for Java’da Markdown Dışa Aktarmaya Giriş

Bu adım‑adım öğreticide, **Word belgelerinden markdown dışa aktarmayı** Aspose.Words for Java kullanarak öğreneceksiniz. Markdown, dokümantasyon, statik site üreticileri ve birçok yayın platformu için mükemmel bir hafif işaretleme dilidir. Bu rehberin sonunda **Word’ü markdown’a dönüştürebilecek**, tablo hizalamasını özelleştirebilecek ve **markdown’da görüntüleri sorunsuz bir şekilde yönetebileceksiniz**.

## Hızlı Yanıtlar
- **Markdown olarak kaydetmek için birincil sınıf nedir?** `MarkdownSaveOptions`
- **Görseller otomatik olarak gömülebilir mi?** Evet – `setImagesFolder` ile görsel klasörünü ayarlayın.
- **Tablo hizalamasını nasıl kontrol ederim?** `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO) kullanın.
- **Minimum gereksinimler nelerdir?** JDK 8+ ve Aspose.Words for Java kütüphanesi.
- **Deneme sürümü mevcut mu?** Evet, Aspose web sitesinden indirebilirsiniz.

## “markdown dışa aktarma” nedir?
Markdown dışa aktarma, zengin‑metin bir Word belgesi (`.docx`) alıp başlıkları, tabloları ve görselleri Markdown sözdiziminde koruyan düz‑metin bir `.md` dosyası üretmek anlamına gelir.

## Görsellerle docx’i dönüştürmek için Aspose.Words for Java neden kullanılmalı?
Aspose.Words, karmaşık düzenleri, gömülü resimleri ve tablo yapılarını kalite kaybı olmadan işler. Ayrıca tablo hizalaması ve görsel klasör yönetimi gibi Markdown çıktısı üzerinde ince ayar yapmanıza olanak tanır.

## Ön Koşullar

- Sisteminizde yüklü Java Development Kit (JDK).
- Aspose.Words for Java kütüphanesi. İndirmek için [buraya](https://releases.aspose.com/words/java/) tıklayın.

## Adım 1: Basit bir Word belgesi oluşturun

İlk olarak içinde bir tablo bulunan küçük bir belge oluşturacağız. Bu, **tablo hizalamasını özelleştirme** konusunu daha sonra gösterebilmemizi sağlayacak.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

Yukarıdaki kodda:

1. Yeni bir `Document` oluşturuyoruz.
2. `DocumentBuilder` kullanarak iki hücreli bir tablo ekliyoruz.
3. Her hücrede **sağ** ve **ortalanmış** paragraf hizalaması uyguluyoruz.
4. Dosyayı `MarkdownSaveOptions` ile Markdown olarak kaydediyoruz.

## Adım 2: Tablo içeriği hizalamasını özelleştirin

Aspose.Words, tablo hücrelerinin son Markdown’da nasıl render edileceğini belirlemenize izin verir. `TableContentAlignment` özelliğini kullanarak sola, sağa, ortaya hizalamayı zorlayabilir veya kütüphanenin her sütunun ilk paragrafına göre otomatik karar vermesini sağlayabilirsiniz.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

`TableContentAlignment` özelliğini değiştirerek **Markdown çıktısı için tablo hizalamasını özelleştirebilirsiniz**.

## Adım 3: Markdown’a dışa aktarırken görselleri yönetin

Belge resimler içeriyorsa, bu görsellerin oluşturulan `.md` dosyasında doğru şekilde görünmesini istersiniz. Aspose.Words’un çıkarılan görselleri koyacağı klasörü ayarlayın.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

`"document_with_images.docx"` ifadesini kaynak dosyanızın yolu ile, `"images_folder/"` ifadesini ise görsellerin saklanmasını istediğiniz konumla değiştirin. Oluşan Markdown, bu klasöre işaret eden görsel bağlantılarını içerecek ve **markdown’da görselleri sorunsuz bir şekilde yönetmenizi** sağlayacaktır.

## Aspose.Words for Java’da Belgeleri Markdown Olarak Kaydetmek İçin Tam Kaynak Kodu

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
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
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

## Yaygın Sorunlar ve Çözümleri

| Sorun | Çözüm |
|-------|----------|
| Görseller `.md` dosyasında görünmüyor | `setImagesFolder`'ın yazılabilir bir dizine işaret ettiğinden ve klasörün oluşturulan Markdown’da doğru şekilde referans verildiğinden emin olun. |
| Tablo hizalaması bozuk | `TableContentAlignment.AUTO` kullanarak Aspose.Words’un her sütunun ilk paragrafına göre en uygun hizalamayı seçmesine izin verin. |
| Çıktı dosyası boş | `save` metodunu çağırmadan önce `Document` nesnesinin gerçekten içerik içerdiğini kontrol edin. |

## Sık Sorulan Sorular

**S: Aspose.Words for Java nasıl kurulur?**  
C: Aspose.Words for Java, projenize kütüphaneyi ekleyerek kurulabilir. Kütüphaneyi [buradan](https://releases.aspose.com/words/java/) indirebilir ve dokümantasyonda verilen kurulum talimatlarını izleyebilirsiniz.

**S: Karmaşık tablolar ve görseller içeren Word belgelerini Markdown’a dönüştürebilir miyim?**  
C: Evet, Aspose.Words for Java, tablolar, görseller ve çeşitli biçimlendirme öğeleri içeren karmaşık Word belgelerinin Markdown’a dönüştürülmesini destekler. Markdown çıktısını belgenizin karmaşıklığına göre özelleştirebilirsiniz.

**S: Markdown dosyalarında görselleri nasıl yönetirim?**  
C: `MarkdownSaveOptions` içinde `setImagesFolder` metodunu kullanarak görsel klasör yolunu belirleyin. Görsel dosyalarının belirtilen klasörde saklandığından emin olun; Aspose.Words uygun Markdown görsel bağlantılarını oluşturacaktır.

**S: Aspose.Words for Java için bir deneme sürümü var mı?**  
C: Evet, Aspose web sitesinden Aspose.Words for Java için bir deneme sürümü alabilirsiniz. Deneme sürümü, lisans satın almadan kütüphanenin yeteneklerini değerlendirmenize olanak tanır.

**S: Daha fazla örnek ve dokümantasyona nereden ulaşabilirim?**  
C: Daha fazla örnek, dokümantasyon ve Aspose.Words for Java hakkında detaylı bilgi için lütfen [dokümantasyon](https://reference.aspose.com/words/java/) sayfasını ziyaret edin.

---

**Son Güncelleme:** 2025-12-22  
**Test Edilen Sürüm:** Aspose.Words for Java 24.12 (yazım anındaki en son sürüm)  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}