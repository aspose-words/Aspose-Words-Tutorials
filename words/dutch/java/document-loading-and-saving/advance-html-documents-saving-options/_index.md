---
date: 2025-12-19
description: Leer hoe u HTML kunt exporteren met Aspose.Words Java, met geavanceerde
  opties om Word op te slaan als HTML en Word efficiënt naar HTML te converteren.
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Hoe HTML exporteren met Aspose.Words Java: Geavanceerde opties'
url: /nl/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hoe HTML te exporteren met Aspose.Words Java: Geavanceerde opties

In deze tutorial ontdek je **hoe je HTML kunt exporteren** vanuit Word‑documenten met Aspose.Words voor Java. Of je nu **Word als HTML wilt opslaan** voor webpublicatie of **Word naar HTML wilt converteren** voor verdere verwerking, de geavanceerde opslaan‑opties geven je fijnmazige controle over de uitvoer. We lopen elke optie stap‑voor‑stap door, leggen uit wanneer je deze moet gebruiken, en tonen praktijkvoorbeelden waarin deze instellingen een verschil maken.

## Snelle antwoorden
- **Wat is de primaire klasse voor HTML‑export?** `HtmlSaveOptions`  
- **Kunnen lettertypen direct in de HTML worden ingebed?** Ja, stel `exportFontsAsBase64` in op `true`.  
- **Hoe houd ik Word‑specifieke round‑trip‑gegevens behouden?** Schakel `exportRoundtripInformation` in.  
- **Welk formaat is het beste voor vectorafbeeldingen?** Gebruik `convertMetafilesToSvg` voor SVG‑output.  
- **Is het mogelijk om CSS‑klassenaam‑conflicten te voorkomen?** Ja, gebruik `addCssClassNamePrefix`.

## 1. Introductie
Aspose.Words voor Java is een robuuste API waarmee ontwikkelaars Word‑documenten programmatisch kunnen manipuleren. Deze gids richt zich op de geavanceerde HTML‑document‑opslaan‑opties waarmee je het conversieproces kunt afstemmen op specifieke web‑ of integratie‑vereisten.

## 2. Round‑trip‑informatie exporteren
Het behouden van round‑trip‑informatie maakt het mogelijk om de HTML terug te converteren naar een Word‑document zonder verlies van lay‑out‑ of opmaakdetails.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### Wanneer te gebruiken
- Wanneer je een omkeerbare conversiepijplijn nodig hebt (HTML → Word → HTML).  
- Ideaal voor scenario's met collaboratieve bewerking waarbij de oorspronkelijke Word‑structuur behouden moet blijven.

## 3. Lettertypen exporteren als Base64
Lettertypen direct in de HTML insluiten elimineert externe font‑afhankelijkheden en zorgt voor visuele getrouwheid in alle browsers.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### Pro‑tip
Gebruik deze optie wanneer de doelomgeving beperkte toegang heeft tot externe bronnen (bijv. e‑mail‑nieuwsbrieven).

## 4. Resources exporteren
Beheer hoe CSS‑ en font‑resources worden uitgegeven, en geef een aangepaste map of URL‑alias op voor die assets.

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

### Waarom het belangrijk is
Het scheiden van CSS in een extern bestand verkleint de HTML‑grootte en maakt caching mogelijk voor snellere paginalading.

## 5. Metabestanden converteren naar EMF of WMF
Metabestanden (bijv. EMF/WMF) worden geconverteerd naar een formaat dat browsers betrouwbaar kunnen weergeven.

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

### Gebruikssituatie
Kies EMF/WMF wanneer de doelbrowsers deze vectorformaten ondersteunen en je verliesloze schaalbaarheid nodig hebt.

## 6. Metabestanden converteren naar SVG
SVG biedt de beste schaalbaarheid en wordt breed ondersteund door moderne browsers.

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

### Voordeel
SVG‑bestanden zijn lichtgewicht en houden het document resolutie‑onafhankelijk, perfect voor responsief webdesign.

## 7. CSS‑klassenaam‑prefix toevoegen
Voorkom stijlconflicten door alle gegenereerde CSS‑klassennamen te prefixen.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### Praktische tip
Gebruik een unieke prefix (bijv. de naam van je project) bij het insluiten van de HTML in bestaande pagina's om CSS‑conflicten te vermijden.

## 8. CID‑URL's exporteren voor MHTML‑resources
Bij het opslaan als MHTML kun je resources exporteren met Content‑ID‑URL's voor betere e‑mail‑compatibiliteit.

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

### Wanneer te gebruiken
Ideaal voor het genereren van één enkel, zelf‑voorzienend HTML‑bestand dat aan e‑mails kan worden toegevoegd.

## 9. Lettertype‑namen oplossen
Zorgt ervoor dat de HTML naar de juiste lettertype‑families verwijst, wat de consistentie over platformen heen verbetert.

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

### Waarom het helpt
Als het oorspronkelijke document lettertypen gebruikt die niet op de clientmachine zijn geïnstalleerd, vervangt deze optie ze door web‑veilige alternatieven.

## 10. Tekstinvoerveld exporteren als tekst
Render formulier‑velden als platte tekst in plaats van interactieve HTML‑invoerelementen.

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

### Gebruikssituatie
Wanneer je een alleen‑lezen weergave van een formulier nodig hebt voor archivering of afdrukdoeleinden.

## Veelvoorkomende valkuilen & probleemoplossing
| Probleem | Typische oorzaak | Oplossing |
|----------|-------------------|-----------|
| Ontbrekende lettertypen in de output | `exportFontsAsBase64` niet ingeschakeld | Stel `setExportFontsAsBase64(true)` in |
| Defecte CSS na insluiten | `EXTERNAL` gebruiken zonder het CSS‑bestand te leveren | Zorg ervoor dat het CSS‑bestand is gedeployed op de opgegeven `resourceFolderAlias` |
| Grote HTML‑grootte | Veel afbeeldingen insluiten als Base64 | Schakel over naar externe afbeeldingsresources via `setExportFontResources(true)` en configureer `resourceFolder` |
| SVG wordt niet weergegeven in oudere browsers | Browser ondersteunt geen SVG | Voorzie een fallback‑PNG door ook te exporteren als EMF/WMF |

## Veelgestelde vragen

**Q: Kan ik zowel lettertypen als Base64 insluiten als externe CSS behouden?**  
A: Ja. Stel `exportFontsAsBase64(true)` in terwijl je `CssStyleSheetType.EXTERNAL` behoudt om font‑data te scheiden van stijlregels.

**Q: Hoe converteer ik een bestaande HTML terug naar een Word‑document?**  
A: Laad de HTML met `Document doc = new Document("input.html");` en vervolgens `doc.save("output.docx");`. Behoud round‑trip‑gegevens met `exportRoundtripInformation` tijdens de eerste export.

**Q: Heeft het gebruik van SVG‑conversie invloed op de prestaties?**  
A: Het converteren van grote metafiles naar SVG kan de verwerkingstijd verhogen, maar de resulterende HTML is doorgaans kleiner en rendert sneller in browsers.

**Q: Werken deze opties ook met Aspose.Words voor .NET?**  
A: Dezelfde concepten bestaan in de .NET‑API, hoewel methodenamen enigszins kunnen afwijken (bijv. `HtmlSaveOptions` wordt gedeeld over platforms).

**Q: Welke optie moet ik kiezen voor e‑mail‑vriendelijke HTML?**  
A: Gebruik `SaveFormat.MHTML` met `exportCidUrlsForMhtmlResources` om alle resources direct in de e‑mail‑body in te sluiten.

---

**Laatst bijgewerkt:** 2025-12-19  
**Getest met:** Aspose.Words for Java 24.12  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}