---
date: 2025-12-19
description: Aspose.Words Java ile HTML dışa aktarmayı öğrenin; Word'ü HTML olarak
  kaydetmek ve Word'ü verimli bir şekilde HTML'ye dönüştürmek için gelişmiş seçenekleri
  kapsar.
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Aspose.Words Java ile HTML Nasıl Dışa Aktarılır: Gelişmiş Seçenekler'
url: /tr/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java ile HTML Dışa Aktarma: Gelişmiş Seçenekler

Bu öğreticide Aspose.Words for Java kullanarak Word belgelerinden **HTML dışa aktarmayı** keşfedeceksiniz. Web yayıncılığı için **Word'ü HTML olarak kaydetmeniz** ya da **Word'ü HTML'ye dönüştürmeniz** gerektiğinde, gelişmiş kaydetme seçenekleri çıktıyı ince ayarlarla kontrol etmenizi sağlar. Her seçeneği adım adım inceleyecek, ne zaman kullanılacağını açıklayacak ve bu ayarların fark yarattığı gerçek dünya senaryolarını göstereceğiz.

## Quick Answers
- **HTML dışa aktarma için birincil sınıf nedir?** `HtmlSaveOptions`  
- **Yazı tipleri doğrudan HTML içinde gömülebilir mi?** Evet, `exportFontsAsBase64` özelliğini `true` olarak ayarlayın.  
- **Word‑özel round‑trip verilerini nasıl korurum?** `exportRoundtripInformation` özelliğini etkinleştirin.  
- **Vektör grafikler için en iyi format hangisidir?** SVG çıktısı için `convertMetafilesToSvg` kullanın.  
- **CSS sınıf adı çakışmalarından kaçınmak mümkün mü?** Evet, `addCssClassNamePrefix` kullanın.

## 1. Introduction
Aspose.Words for Java, geliştiricilerin Word belgelerini programlı olarak manipüle etmelerini sağlayan güçlü bir API'dir. Bu kılavuz, belirli web veya entegrasyon gereksinimlerini karşılamak için dönüşüm sürecini özelleştirmenize olanak tanıyan gelişmiş HTML belge kaydetme seçeneklerine odaklanmaktadır.

## 2. Export Roundtrip Information
Round‑trip bilgilerini korumak, HTML'yi Word belgesine geri dönüştürürken düzen veya biçimlendirme detaylarını kaybetmemenizi sağlar.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### When to use
- HTML → Word → HTML gibi tersine dönüştürülebilir bir işlem hattına ihtiyaç duyduğunuzda.  
- Orijinal Word yapısının korunması gereken işbirlikli düzenleme senaryoları için ideal.

## 3. Export Fonts as Base64
Yazı tiplerini doğrudan HTML içine gömmek, dış kaynak bağımlılıklarını ortadan kaldırır ve tarayıcılar arasında görsel tutarlılığı sağlar.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### Pro tip
Hedef ortamın dış kaynaklara sınırlı erişimi olduğu durumlarda (ör. e‑posta bültenleri) bu seçeneği kullanın.

## 4. Export Resources
CSS ve yazı tipi kaynaklarının nasıl yayımlanacağını kontrol eder ve bu varlıklar için özel bir klasör ya da URL takma adı belirlemenizi sağlar.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/resources");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

### Why it matters
CSS'i harici bir dosyaya ayırmak, HTML boyutunu küçültür ve önbellekleme sayesinde sayfa yüklemelerini hızlandırır.

## 5. Convert Metafiles to EMF or WMF
Metafile'lar (ör. EMF/WMF) tarayıcıların güvenilir bir şekilde render edebileceği bir formata dönüştürülür.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n                    vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Red dot\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

### Use case
Hedef tarayıcılar bu vektör formatlarını destekliyorsa ve kayıpsız ölçekleme ihtiyacınız varsa EMF/WMF seçin.

## 6. Convert Metafiles to SVG
SVG, en iyi ölçeklenebilirliği sunar ve modern tarayıcılar tarafından geniş çapta desteklenir.

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

### Benefit
SVG dosyaları hafiftir ve belgeyi çözünürlükten bağımsız tutar; responsive web tasarımı için mükemmeldir.

## 7. Add CSS Class Name Prefix
Oluşturulan tüm CSS sınıf adlarına ön ek ekleyerek stil çakışmalarını önleyin.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### Practical tip
HTML'i mevcut sayfalara gömerken CSS çakışmalarını önlemek için benzersiz bir ön ek (ör. proje adınız) kullanın.

## 8. Export CID URLs for MHTML Resources
MHTML olarak kaydederken, kaynakları e‑posta uyumluluğunu artırmak için Content‑ID URL'leriyle dışa aktarabilirsiniz.

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

### When to use
Tek bir, kendine ait HTML dosyası oluşturup bunu e‑postalara eklemek istediğinizde idealdir.

## 9. Resolve Font Names
HTML'in doğru yazı tipi ailelerine referans vermesini sağlayarak platformlar arası tutarlılığı artırır.

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

### Why it helps
Orijinal belgede istemci makinede yüklü olmayan yazı tipleri kullanılmışsa, bu seçenek web‑güvenli alternatiflerle değiştirir.

## 10. Export Text Input Form Field as Text
Form alanlarını etkileşimli HTML giriş elemanları yerine düz metin olarak dışa aktarın.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// The folder specified needs to exist and should be empty.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Set an option to export form fields as plain text, not as HTML input elements.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

### Use case
Arşivleme veya baskı amaçlı, formun yalnızca okunabilir bir temsiline ihtiyacınız olduğunda.

## Common Pitfalls & Troubleshooting
| Issue | Typical Cause | Fix |
|-------|---------------|-----|
| Çıktıda eksik yazı tipleri | `exportFontsAsBase64` etkin değil | `setExportFontsAsBase64(true)` olarak ayarlayın |
| Gömme sonrası bozuk CSS | `EXTERNAL` kullanırken CSS dosyası sağlanmamış | Belirtilen `resourceFolderAlias` konumunda CSS dosyasının dağıtıldığından emin olun |
| Büyük HTML boyutu | Çok sayıda resmi Base64 olarak gömmek | `setExportFontResources(true)` ile harici resim kaynaklarına geçin ve `resourceFolder` yapılandırın |
| SVG eski tarayıcılarda render olmuyor | Tarayıcı SVG desteğine sahip değil | EMF/WMF olarak da dışa aktararak yedek PNG sağlayın |

## Frequently Asked Questions

**S: Yazı tiplerini Base64 olarak gömerken dış CSS'i de tutabilir miyim?**  
C: Evet. `exportFontsAsBase64(true)` ayarlarken `CssStyleSheetType.EXTERNAL` tutarak yazı tipi verilerini stil kurallarından ayırabilirsiniz.

**S: Mevcut bir HTML dosyasını tekrar Word belgesine nasıl dönüştürürüm?**  
C: `Document doc = new Document("input.html");` ile HTML'i yükleyin ve ardından `doc.save("output.docx");` ile kaydedin. İlk dışa aktarmada `exportRoundtripInformation` kullanarak round‑trip verisini koruyun.

**S: SVG dönüşümü performansı etkiler mi?**  
C: Büyük metafile'ları SVG'ye dönüştürmek işlem süresini artırabilir, ancak ortaya çıkan HTML genellikle daha küçüktür ve tarayıcılarda daha hızlı render olur.

**S: Bu seçenekler Aspose.Words for .NET'te de çalışıyor mu?**  
C: Aynı kavramlar .NET API'sinde de mevcuttur, ancak metod isimleri biraz farklı olabilir (ör. `HtmlSaveOptions` her iki platformda da ortak).

**S: E‑posta dostu HTML için hangi seçeneği tercih etmeliyim?**  
C: Tüm kaynakları doğrudan e‑posta gövdesine gömmek için `SaveFormat.MHTML` ve `exportCidUrlsForMhtmlResources` kullanın.

**Last Updated:** 2025-12-19  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}