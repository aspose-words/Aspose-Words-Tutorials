---
date: 2026-02-24
description: Aspose.Words for Java kullanarak Word belgesini markdown’a nasıl dönüştüreceğinizi
  öğrenin. Bu rehber, tablo hizalamasını, resim işleme yöntemlerini ve belgenin markdown
  olarak nasıl kaydedileceğini kapsar.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java ile Word'ü Markdown'a Dönüştür
url: /tr/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile Word'ü Markdown'a Dönüştürme

## Aspose.Words for Java ile Word'ü Markdown'a Dönüştürmeye Giriş

Bu adım adım öğreticide, güçlü Aspose.Words for Java API'sini kullanarak **Word'ü Markdown'a nasıl dönüştüreceğinizi** öğreneceksiniz. Markdown, birçok geliştirici ve içerik platformunun temiz, okunabilir belgeler için güvendiği hafif bir işaretleme dilidir. Bu rehberin sonunda herhangi bir `.docx` dosyasını alabilecek, tabloları, resimleri ve biçimlendirmeyi koruyabilecek ve bunu statik site jeneratörleri, GitHub README'ları veya herhangi bir markdown‑uyumlu iş akışı için hazır bir `.md` dosyası olarak dışa aktarabileceksiniz.

## Hızlı Yanıtlar
- **Hangi kütüphaneye ihtiyacım var?** Aspose.Words for Java (`aspose-words.jar`).
- **Tablo hizalamasını özelleştirebilir miyim?** Evet – `MarkdownSaveOptions` içinde `TableContentAlignment` kullanın.
- **Resimler nasıl işlenir?** `setImagesFolder()` ile bir resim klasörü ayarlayın; kütüphane göreceli bağlantılar oluşturur.
- **Üretim için lisansa ihtiyacım var mı?** Deneme dışı kullanım için ticari lisans gereklidir.
- **Bu, Java 17 ile uyumlu mu?** Evet, kütüphane Java 8 ve üzerini destekler.

## Word'ü Markdown'a Dönüştürmek Ne Demektir?

Word'ü Markdown'a dönüştürmek, bir Microsoft Word belgesinin zengin biçimlendirmesini düz metin markdown sözdizimine çevirmek anlamına gelir. Bu süreç başlıkları, listeleri, tabloları ve resim referanslarını korurken ikili biçimlendirmeyi kaldırır, içeriği taşınabilir ve sürüm kontrolüne uygun hâle getirir.

## Neden Aspose.Words for Java'ı belgeyi markdown olarak kaydetmek için kullanmalıyım?

* **Tam sadakat** – tablolar, resimler ve karmaşık düzenler korunur.
* **İnce ayarlı kontrol** – tablo hizalamasını, resim yollarını ve daha fazlasını özelleştirebilirsiniz.
* **Harici bağımlılık yok** – kütüphane, Office kurulumu gerektirmeden kutudan çıkar çıkmaz çalışır.
* **Çapraz platform** – Windows, Linux ve macOS üzerinde herhangi bir Java çalışma zamanı ile çalışır.

## Ön Koşullar

Başlamadan önce, aşağıdakilere sahip olduğunuzdan emin olun:

- Sisteminizde Java Development Kit (JDK) kurulu.
- Aspose.Words for Java kütüphanesi. Bunu [buradan](https://releases.aspose.com/words/java/) indirebilirsiniz.

## Adım Adım Kılavuz

### Adım 1: Dönüştürülecek bir Word belgesi oluşturun

İlk olarak, iki hücreli bir tablo içeren basit bir Word belgesi oluşturuyoruz. Bu örnek, tablo hücreleri içindeki paragraf hizalamasının, daha sonra **belgeyi markdown olarak kaydettiğimizde** nasıl korunduğunu gösterir.

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

### Adım 2: Tablo içeriği hizalamasını özelleştirin

Aspose.Words for Java, oluşturulan markdown'da tablo hücrelerinin nasıl hizalanacağını kontrol etmenizi sağlar. `TableContentAlignment` özelliğini kullanarak tablo hizalamasını sola, sağa, ortaya ayarlayabilir veya kütüphanenin her sütundaki ilk paragraf temelinde otomatik olarak karar vermesine izin verebilirsiniz.

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

Bu ayarı değiştirerek, aşağı yönlü render motorları için ihtiyaç duyduğunuz tam hizalama ile **Word tablolarını markdown olarak dışa aktarabilirsiniz**.

### Adım 3: Dönüşüm sırasında resimleri işleyin

Kaynak Word belgenizde resimler bulunduğunda, Aspose.Words'a dışa aktarılan resim dosyalarının nereye yerleştirileceğini belirtmelisiniz. `MarkdownSaveOptions` üzerindeki `setImagesFolder` yöntemi, resim varlıklarını tutacak klasörü tanımlar ve markdown bu dosyalara göreceli bağlantılar içerir.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

`"document_with_images.docx"` ifadesini kaynak dosyanızın yolu ile, `"images_folder/"` ifadesini ise resimler için istediğiniz çıktı klasörüyle değiştirin.

### Tüm senaryolar için tam kaynak kodu

Aşağıda, bir yöntemde **otomatik tablo hizalaması**, **hizalamanın özelleştirilmesi** ve **bir resim klasörünün ayarlanması** nasıl yapılır gösteren birleştirilmiş bir örnek bulunmaktadır. Bu kod parçacığı orijinal öğretici kodunu yansıtır ve değişiklik yapılmadan çalışır.

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

## Yaygın Sorunlar ve Çözümler

| Sorun | Sebep | Çözüm |
|-------|--------|-----|
| Resimler kırık bağlantı olarak görünüyor | `setImagesFolder` ayarlanmamış veya klasör yolu hatalı | Klasör yolunun doğru ve klasörün yazılabilir olduğundan emin olun |
| Tablo hizalaması bozuk görünüyor | `TableContentAlignment` değeri yanlış | `TableContentAlignment.AUTO` kullanarak ilk paragrafın karar vermesine izin verin veya LEFT/RIGHT/CENTER değerlerini açıkça ayarlayın |
| Çıktı dosyası boş | Kaydetme seçenekleri `doc.save()`'e geçirilmemiş | `MarkdownSaveOptions` örneğini `save` metoduna geçirdiğinizden emin olun |
| Desteklenmeyen Word özellikleri (ör. SmartArt) | Markdown bazı karmaşık nesneleri temsil edemez | Bu öğeleri kaydetmeden önce resimlere dönüştürün veya kaynak belgeyi sadeleştirin |

## Sıkça Sorulan Sorular

**Q: Aspose.Words for Java'ı nasıl kurarım?**  
A: Aspose.Words for Java, Java projenize kütüphaneyi ekleyerek kurulabilir. Kütüphaneyi [buradan](https://releases.aspose.com/words/java/) indirebilir ve belgelerde sağlanan kurulum talimatlarını izleyebilirsiniz.

**Q: Tablolar ve resimler içeren karmaşık Word belgelerini Markdown'a dönüştürebilir miyim?**  
A: Evet, Aspose.Words for Java, tablolar, resimler ve çeşitli biçimlendirme öğeleri içeren karmaşık Word belgelerinin Markdown'a dönüştürülmesini destekler. Markdown çıktısını belgenizin karmaşıklığına göre özelleştirebilirsiniz.

**Q: Markdown dosyalarında resimleri nasıl yönetebilirim?**  
A: Markdown dosyalarına resim eklemek için `MarkdownSaveOptions` içinde `setImagesFolder` yöntemini kullanarak resim klasörü yolunu ayarlayın. Resim dosyalarının belirtilen klasörde saklandığından emin olun, Aspose.Words for Java resim referanslarını buna göre yönetecektir.

**Q: Aspose.Words for Java için bir deneme sürümü mevcut mu?**  
A: Evet, Aspose web sitesinden Aspose.Words for Java için bir deneme sürümü edinebilirsiniz. Deneme sürümü, lisans satın almadan önce kütüphanenin yeteneklerini değerlendirmenizi sağlar.

**Q: Daha fazla örnek ve belgeyi nerede bulabilirim?**  
A: Daha fazla örnek, belge ve Aspose.Words for Java hakkında ayrıntılı bilgi için lütfen [belgelere](https://reference.aspose.com/words/java/) göz atın.

## Sonuç

Bu rehberde, Aspose.Words for Java kullanarak **Word'ü markdown'a dönüştürmek** için ihtiyacınız olan her şeyi ele aldık: bir kaynak belge oluşturma, **tablo hizalamasını özelleştirme** ve resimleri uygun klasör yapılandırmasıyla işleme. Bu tekniklerle Word içeriğini bloglar, belge siteleri veya markdown tüketen herhangi bir platform için güvenilir bir şekilde markdown'a dışa aktarabilirsiniz.

---

**Son Güncelleme:** 2026-02-24  
**Test Edildiği Sürüm:** Aspose.Words for Java 24.12 (yazım zamanındaki en yeni sürüm)  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}