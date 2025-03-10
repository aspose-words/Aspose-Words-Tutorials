---
title: Avancera alternativ för att spara HTML-dokument med Aspose.Words Java
linktitle: Spara HTML-dokument med
second_title: Aspose.Words Java Document Processing API
description: I den här handledningen har vi täckt olika avancerade alternativ för att spara HTML-dokument med Aspose.Words för Java. Dessa alternativ ger dig möjlighet att skapa HTML av hög kvalitet
weight: 16
url: /sv/java/document-loading-and-saving/advance-html-documents-saving-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Avancera alternativ för att spara HTML-dokument med Aspose.Words Java


I den här handledningen kommer vi att utforska de avancerade alternativen för att spara HTML-dokument som tillhandahålls av Aspose.Words för Java. Aspose.Words är ett kraftfullt Java API för att arbeta med Word-dokument, och det erbjuder ett brett utbud av funktioner för dokumentmanipulation och konvertering.

## 1. Introduktion
Aspose.Words för Java låter dig arbeta med Word-dokument programmatiskt. I den här handledningen kommer vi att fokusera på avancerade alternativ för att spara HTML-dokument, som gör att du kan kontrollera hur Word-dokument konverteras till HTML.

## 2. Exportera information om tur och retur
 De`exportRoundtripInformation` metoden låter dig exportera Word-dokument till HTML samtidigt som du bevarar information om tur och retur. Denna information kan vara användbar när du vill konvertera HTML tillbaka till Word-format utan att förlora några dokumentspecifika detaljer.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Exportera teckensnitt som Base64
 Med`exportFontsAsBase64` metod kan du exportera teckensnitt som används i dokumentet som Base64-kodade data i HTML. Detta säkerställer att HTML-representationen behåller samma teckensnittsstil som det ursprungliga Word-dokumentet.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Exportera resurser
 De`exportResources` metoden låter dig ange typen av CSS-formatmall och exportera teckensnittsresurser. Du kan också ställa in en resursmapp och ett alias för resurser i HTML.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/resurser");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

## 5. Konvertera metafiler till EMF eller WMF
 De`convertMetafilesToEmfOrWmf`metoden låter dig konvertera metafiler i dokumentet till antingen EMF- eller WMF-format, vilket säkerställer kompatibilitet och smidig rendering i HTML.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Röd prick\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. Konvertera metafiler till SVG
 Använd`convertMetafilesToSvg` metod för att konvertera metafiler till SVG-format. Detta format är idealiskt för att visa vektorgrafik i HTML-dokument.

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

## 7. Lägg till prefix för CSS-klassnamn
 Med`addCssClassNamePrefix` metod kan du lägga till ett prefix till CSS-klassnamn i den exporterade HTML-koden. Detta hjälper till att förhindra konflikter med befintliga stilar.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. Exportera CID-URL:er för MHTML-resurser
 De`exportCidUrlsForMhtmlResources` metod används när du sparar dokument i MHTML-format. Det tillåter export av Content-ID-webbadresser för resurser.

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

## 9. Lös teckensnittsnamn
 De`resolveFontNames` metod hjälper till att lösa teckensnittsnamn när du sparar dokument i HTML-format, vilket säkerställer konsekvent rendering på olika plattformar.

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

## 10. Exportera textinmatningsformulärfält som text
 De`exportTextInputFormFieldAsText`metod exporterar formulärfält som vanlig text i HTML, vilket gör dem lätta att läsa och redigera.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// Den angivna mappen måste finnas och bör vara tom.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Ställ in ett alternativ för att exportera formulärfält som vanlig text, inte som HTML-inmatningselement.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Slutsats
I den här handledningen utforskade vi de avancerade alternativen för att spara HTML-dokument som tillhandahålls av Aspose.Words för Java. Dessa alternativ ger dig finkornig kontroll över konverteringsprocessen, så att du kan skapa HTML-dokument som liknar de ursprungliga Word-dokumenten.

## FAQ's
Här är några vanliga frågor om att arbeta med Aspose.Words för Java och alternativ för att spara HTML-dokument:

### F1: Hur kan jag konvertera HTML tillbaka till Word-format med Aspose.Words för Java?
 För att konvertera HTML tillbaka till Word-format kan du använda Aspose.Words API:er`load` metod för att ladda HTML-dokumentet och sedan spara det i Word-format.

### F2: Kan jag anpassa CSS-stilarna när jag exporterar till HTML?
Ja, du kan anpassa CSS-stilar genom att modifiera stilmallarna som används i HTML eller genom att använda`addCssClassNamePrefix` metod för att lägga till ett prefix till CSS-klassnamn.

### F3: Finns det något sätt att optimera HTML-utdata för webbvisning?
Ja, du kan optimera HTML-utdata för webbvisning genom att konfigurera alternativ som att exportera teckensnitt som Base64 och konvertera metafiler till SVG.

### F4: Finns det några begränsningar vid konvertering av komplexa Word-dokument till HTML?
Medan Aspose.Words för Java ger kraftfulla konverteringsmöjligheter, kan komplexa Word-dokument med invecklade layouter kräva ytterligare efterbearbetning för att uppnå önskad HTML-utdata.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
