---
title: Geavanceerde HTML-documenten opslaan opties met Aspose.Words Java
linktitle: HTML-documenten opslaan met
second_title: Aspose.Words Java Documentverwerkings-API
description: In deze tutorial hebben we verschillende geavanceerde HTML-documentopslagopties behandeld met Aspose.Words voor Java. Deze opties stellen u in staat om HTML van hoge kwaliteit te maken
weight: 16
url: /nl/java/document-loading-and-saving/advance-html-documents-saving-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Geavanceerde HTML-documenten opslaan opties met Aspose.Words Java


In deze tutorial verkennen we de geavanceerde HTML-documentopslagopties die Aspose.Words voor Java biedt. Aspose.Words is een krachtige Java API voor het werken met Word-documenten en biedt een breed scala aan functies voor documentmanipulatie en -conversie.

## 1. Inleiding
Met Aspose.Words voor Java kunt u programmatisch met Word-documenten werken. In deze tutorial richten we ons op geavanceerde opties voor het opslaan van HTML-documenten, waarmee u kunt bepalen hoe Word-documenten worden omgezet naar HTML.

## 2. Exporteer retourinformatie
 De`exportRoundtripInformation` methode kunt u Word-documenten exporteren naar HTML terwijl roundtrip-informatie behouden blijft. Deze informatie kan handig zijn wanneer u HTML terug wilt converteren naar Word-formaat zonder dat u documentspecifieke details verliest.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Lettertypen exporteren als Base64
 Met de`exportFontsAsBase64` methode, kunt u lettertypen die in het document worden gebruikt exporteren als Base64-gecodeerde gegevens in de HTML. Dit zorgt ervoor dat de HTML-weergave dezelfde lettertypestijlen behoudt als het originele Word-document.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Hulpbronnen exporteren
 De`exportResources` Met de methode kunt u het type CSS-stijlblad opgeven en lettertypebronnen exporteren. U kunt ook een bronmap en een alias voor bronnen in de HTML instellen.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://voorbeeld.com/resources");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

## 5. Metafiles converteren naar EMF of WMF
 De`convertMetafilesToEmfOrWmf`Met deze methode kunt u metabestanden in het document converteren naar EMF- of WMF-indeling, waardoor compatibiliteit en soepele weergave in HTML worden gegarandeerd.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Rode stip\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. Metafiles naar SVG converteren
 Gebruik de`convertMetafilesToSvg` methode om metafiles naar SVG-formaat te converteren. Dit formaat is ideaal voor het weergeven van vectorafbeeldingen in HTML-documenten.

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

## 7. Voeg CSS-klassenaamvoorvoegsel toe
 Met de`addCssClassNamePrefix` methode, kunt u een voorvoegsel toevoegen aan CSS-klassenamen in de geëxporteerde HTML. Dit helpt conflicten met bestaande stijlen te voorkomen.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. Exporteer CID-URL's voor MHTML-bronnen
 De`exportCidUrlsForMhtmlResources` methode wordt gebruikt bij het opslaan van documenten in MHTML-formaat. Hiermee kunnen Content-ID URL's voor bronnen worden geëxporteerd.

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

## 9. Lettertypenamen oplossen
 De`resolveFontNames` Met deze methode kunt u lettertypenamen omzetten bij het opslaan van documenten in HTML-formaat, waardoor een consistente weergave op verschillende platforms wordt gegarandeerd.

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

## 10. Exporteer tekstinvoerformulierveld als tekst
 De`exportTextInputFormFieldAsText`Met deze methode worden formuliervelden geëxporteerd als platte tekst in de HTML-code, waardoor ze gemakkelijk leesbaar en bewerkbaar zijn.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// De opgegeven map moet bestaan en mag leeg zijn.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Stel een optie in om formuliervelden te exporteren als platte tekst, niet als HTML-invoerelementen.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Conclusie
In deze tutorial hebben we de geavanceerde HTML-documentopslagopties van Aspose.Words voor Java onderzocht. Deze opties geven u nauwkeurige controle over het conversieproces, zodat u HTML-documenten kunt maken die sterk lijken op de originele Word-documenten.

## Veelgestelde vragen
Hier volgen enkele veelgestelde vragen over het werken met Aspose.Words voor Java- en HTML-documentopslagopties:

### V1: Hoe kan ik HTML terug converteren naar Word-formaat met Aspose.Words voor Java?
 Om HTML terug te converteren naar Word-formaat, kunt u de Aspose.Words API's gebruiken`load` Methode om het HTML-document te laden en vervolgens op te slaan in Word-formaat.

### V2: Kan ik de CSS-stijlen aanpassen bij het exporteren naar HTML?
Ja, u kunt CSS-stijlen aanpassen door de stylesheets die in de HTML worden gebruikt te wijzigen of door de`addCssClassNamePrefix` Methode om een voorvoegsel toe te voegen aan CSS-klassenamen.

### V3: Is er een manier om de HTML-uitvoer te optimaliseren voor weergave op internet?
Ja, u kunt de HTML-uitvoer optimaliseren voor weergave op het web door opties te configureren zoals het exporteren van lettertypen als Base64 en het converteren van metabestanden naar SVG.

### V4: Zijn er beperkingen bij het converteren van complexe Word-documenten naar HTML?
Hoewel Aspose.Words voor Java krachtige conversiemogelijkheden biedt, hebben complexe Word-documenten met een ingewikkelde lay-out mogelijk extra nabewerking nodig om de gewenste HTML-uitvoer te verkrijgen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
