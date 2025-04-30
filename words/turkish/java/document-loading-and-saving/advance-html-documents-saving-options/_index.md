---
"description": "Bu eğitimde, Aspose.Words for Java ile çeşitli gelişmiş HTML belge kaydetme seçeneklerini ele aldık. Bu seçenekler, yüksek kaliteli HTML oluşturmanıza olanak tanır"
"linktitle": "HTML Belgelerini Kaydetme"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Aspose.Words Java ile Gelişmiş HTML Belgeleri Kaydetme Seçenekleri"
"url": "/tr/java/document-loading-and-saving/advance-html-documents-saving-options/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java ile Gelişmiş HTML Belgeleri Kaydetme Seçenekleri


Bu eğitimde, Aspose.Words for Java tarafından sağlanan gelişmiş HTML belge kaydetme seçeneklerini inceleyeceğiz. Aspose.Words, Word belgeleriyle çalışmak için güçlü bir Java API'sidir ve belge düzenleme ve dönüştürme için çok çeşitli özellikler sunar.

## 1. Giriş
Java için Aspose.Words, Word belgeleriyle programatik olarak çalışmanıza olanak tanır. Bu eğitimde, Word belgelerinin HTML'ye nasıl dönüştürüleceğini kontrol etmenizi sağlayan gelişmiş HTML belge kaydetme seçeneklerine odaklanacağız.

## 2. Gidiş-Dönüş Bilgilerini Dışa Aktar
The `exportRoundtripInformation` yöntem, gidiş-dönüş bilgilerini koruyarak Word belgelerini HTML'ye aktarmanıza olanak tanır. Bu bilgiler, belgeye özgü hiçbir ayrıntıyı kaybetmeden HTML'yi Word biçimine geri dönüştürmek istediğinizde yararlı olabilir.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Yazı Tiplerini Base64 Olarak Dışa Aktar
İle `exportFontsAsBase64` yöntemiyle, belgede kullanılan yazı tiplerini HTML'de Base64 kodlu veri olarak dışa aktarabilirsiniz. Bu, HTML gösteriminin orijinal Word belgesiyle aynı yazı tipi stillerini korumasını sağlar.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Kaynakları İhracat Etmek
The `exportResources` yöntemi, CSS stil sayfasının türünü belirtmenize ve yazı tipi kaynaklarını dışa aktarmanıza olanak tanır. Ayrıca HTML'de kaynaklar için bir kaynak klasörü ve bir takma ad da ayarlayabilirsiniz.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://ornek.com/kaynaklar");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

## 5. Meta Dosyalarını EMF veya WMF'ye Dönüştürün
The `convertMetafilesToEmfOrWmf` Bu yöntem, belgedeki meta dosyalarını EMF veya WMF biçimine dönüştürmenize olanak tanır ve HTML'de uyumluluğu ve düzgün işlemeyi garanti eder.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Kırmızı nokta\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. Meta Dosyalarını SVG'ye Dönüştürün
Kullanın `convertMetafilesToSvg` meta dosyalarını SVG formatına dönüştürme yöntemi. Bu format, HTML belgelerinde vektör grafiklerini görüntülemek için idealdir.

```java

public void convertMetafilesToSvg() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	
	builder.write("Here is an SVG image: ");
	builder.insertHtml(
		"<svg height='210' width='500'>\r\n                <polygon points='100,10 40,198 190,78 10,78 160,198' \r\n                    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />\r\n            </svg> ");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.SVG); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
}
```

## 7. CSS Sınıf Adı Önekini Ekleyin
İle `addCssClassNamePrefix` yöntemi, dışa aktarılan HTML'deki CSS sınıf adlarına bir önek ekleyebilirsiniz. Bu, mevcut stillerle çakışmaları önlemeye yardımcı olur.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. MHTML Kaynakları için CID URL'lerini dışa aktarın
The `exportCidUrlsForMhtmlResources` yöntem, belgeleri MHTML biçiminde kaydederken kullanılır. Kaynaklar için İçerik Kimliği URL'lerinin dışa aktarılmasına izin verir.

```java

public void exportCidUrlsForMhtmlResources() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document(dataDir + "Content-ID.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.MHTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setExportCidUrlsForMhtmlResources(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
}
```

## 9. Yazı Tipi Adlarını Çöz
The `resolveFontNames` Bu yöntem, belgeleri HTML formatında kaydederken yazı tipi adlarının çözümlenmesine yardımcı olur ve farklı platformlarda tutarlı bir görüntüleme sağlar.

```java

public void resolveFontNames() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Missing font.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setResolveFontNames(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
}
```

## 10. Metin Giriş Formu Alanını Metin Olarak Dışa Aktar
The `exportTextInputFormFieldAsText` method form alanlarını HTML'de düz metin olarak dışa aktarır, böylece kolayca okunabilir ve düzenlenebilir hale gelir.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// Belirtilen klasörün mevcut olması ve boş olması gerekiyor.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Form alanlarını HTML giriş öğeleri olarak değil, düz metin olarak dışa aktarmak için bir seçenek belirleyin.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Çözüm
Bu eğitimde, Aspose.Words for Java tarafından sağlanan gelişmiş HTML belge kaydetme seçeneklerini inceledik. Bu seçenekler, dönüştürme süreci üzerinde ayrıntılı kontrol sağlayarak orijinal Word belgelerine oldukça benzeyen HTML belgeleri oluşturmanıza olanak tanır.

## SSS
Aspose.Words for Java ve HTML belge kaydetme seçenekleriyle ilgili sık sorulan sorulardan bazıları şunlardır:

### S1: Aspose.Words for Java kullanarak HTML'yi Word formatına nasıl geri dönüştürebilirim?
HTML'yi Word biçimine geri dönüştürmek için Aspose.Words API'lerini kullanabilirsiniz `load` HTML belgesini yükleme ve ardından Word formatında kaydetme yöntemi.

### S2: HTML'e aktarırken CSS stillerini özelleştirebilir miyim?
Evet, HTML'de kullanılan stil sayfalarını değiştirerek veya CSS stillerini özelleştirebilirsiniz. `addCssClassNamePrefix` CSS sınıf adlarına önek ekleme yöntemi.

### S3: HTML çıktısını web gösterimi için optimize etmenin bir yolu var mı?
Evet, fontları Base64 olarak dışa aktarma ve meta dosyalarını SVG'ye dönüştürme gibi seçenekleri yapılandırarak HTML çıktısını web gösterimi için optimize edebilirsiniz.

### S4: Karmaşık Word belgelerini HTML'ye dönüştürürken herhangi bir sınırlama var mı?
Aspose.Words for Java güçlü dönüştürme yetenekleri sağlasa da, karmaşık düzenlere sahip karmaşık Word belgelerinin istenen HTML çıktısını elde etmek için ek son işleme tabi tutulması gerekebilir.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}