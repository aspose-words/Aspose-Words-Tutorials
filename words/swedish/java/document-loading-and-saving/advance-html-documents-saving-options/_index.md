---
date: 2025-12-19
description: Lär dig hur du exporterar HTML med Aspose.Words Java, inklusive avancerade
  alternativ för att spara Word som HTML och konvertera Word till HTML på ett effektivt
  sätt.
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Hur man exporterar HTML med Aspose.Words Java: Avancerade alternativ'
url: /sv/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hur man exporterar HTML med Aspose.Words Java: Avancerade alternativ

I den här handledningen kommer du att upptäcka **hur man exporterar HTML** från Word‑dokument med Aspose.Words för Java. Oavsett om du behöver **spara Word som HTML** för webbpublicering eller **konvertera Word till HTML** för vidare bearbetning, ger de avancerade sparalternativen dig fin‑granulär kontroll över resultatet. Vi går igenom varje alternativ steg‑för‑steg, förklarar när du ska använda det och visar verkliga scenarier där dessa inställningar gör skillnad.

## Snabba svar
- **Vad är den primära klassen för HTML‑export?** `HtmlSaveOptions`  
- **Kan teckensnitt bäddas in direkt i HTML?** Ja, sätt `exportFontsAsBase64` till `true`.  
- **Hur behåller jag Word‑specifik round‑trip‑data?** Aktivera `exportRoundtripInformation`.  
- **Vilket format är bäst för vektorgrafik?** Använd `convertMetafilesToSvg` för SVG‑utdata.  
- **Är det möjligt att undvika kollisioner av CSS‑klassnamn?** Ja, använd `addCssClassNamePrefix`.

## 1. Introduktion
Aspose.Words för Java är ett robust API som låter utvecklare manipulera Word‑dokument programatiskt. Denna guide fokuserar på de avancerade HTML‑dokument‑sparalternativen som låter dig anpassa konverteringsprocessen för att möta specifika webb‑ eller integrationskrav.

## 2. Exportera round‑trip‑information
Att bevara round‑trip‑information gör att du kan konvertera HTML tillbaka till ett Word‑dokument utan att förlora layout‑ eller formateringsdetaljer.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### När du ska använda
- När du behöver en reversibel konverteringspipeline (HTML → Word → HTML).  
- Idealiskt för samarbetsredigeringsscenarier där den ursprungliga Word‑strukturen måste behållas.

## 3. Exportera teckensnitt som Base64
Att bädda in teckensnitt direkt i HTML eliminerar externa teckensnittsberoenden och säkerställer visuell trohet i alla webbläsare.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### Pro‑tips
Använd detta alternativ när målmiljön har begränsad åtkomst till externa resurser (t.ex. e‑postnyhetsbrev).

## 4. Exportera resurser
Styr hur CSS‑ och teckensnittsresurser skrivs ut, och ange en anpassad mapp eller URL‑alias för dessa tillgångar.

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

### Varför det är viktigt
Att separera CSS i en extern fil minskar HTML‑storleken och möjliggör cachning för snabbare sidladdning.

## 5. Konvertera metafiler till EMF eller WMF
Metafiler (t.ex. EMF/WMF) konverteras till ett format som webbläsare kan rendera på ett pålitligt sätt.

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

### Användningsfall
Välj EMF/WMF när målwebbläsarna stödjer dessa vektorformat och du behöver förlustfri skalning.

## 6. Konvertera metafiler till SVG
SVG ger bästa skalbarhet och stöds brett i moderna webbläsare.

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

### Fördel
SVG‑filer är lätta och håller dokumentet upplösningsoberoende, perfekt för responsiv webbdesign.

## 7. Lägg till prefix för CSS‑klassnamn
Förhindra stilkrockar genom att lägga till ett prefix framför alla genererade CSS‑klassnamn.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### Praktisk tip
Använd ett unikt prefix (t.ex. ditt projektnamn) när du bäddar in HTML i befintliga sidor för att undvika CSS‑konflikter.

## 8. Exportera CID‑URL:er för MHTML‑resurser
När du sparar som MHTML kan du exportera resurser med Content‑ID‑URL:er för bättre e‑postkompatibilitet.

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

### När du ska använda
Perfekt för att generera en enda, självständig HTML‑fil som kan bifogas till e‑postmeddelanden.

## 9. Lös upp teckensnittsnamn
Säkerställer att HTML refererar till rätt teckensnittsfamiljer, vilket förbättrar plattformsöverskridande konsistens.

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

### Varför det hjälper
Om det ursprungliga dokumentet använder teckensnitt som inte är installerade på klientens maskin, ersätter detta alternativ dem med webbsäkra alternativ.

## 10. Exportera textinmatningsformulärfält som text
Rendera formulärfält som vanlig text istället för interaktiva HTML‑inmatningselement.

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

### Användningsfall
När du behöver en skrivskyddad representation av ett formulär för arkivering eller utskrift.

## Vanliga fallgropar & felsökning
| Problem | Typisk orsak | Åtgärd |
|-------|---------------|-----|
| Teckensnitt saknas i resultatet | `exportFontsAsBase64` inte aktiverat | Sätt `setExportFontsAsBase64(true)` |
| CSS går sönder efter inbäddning | Använder `EXTERNAL` utan att tillhandahålla CSS‑filen | Säkerställ att CSS‑filen är distribuerad på angivet `resourceFolderAlias` |
| Stor HTML‑fil | Inbäddar många bilder som Base64 | Byt till externa bildresurser via `setExportFontResources(true)` och konfigurera `resourceFolder` |
| SVG renderas inte i äldre webbläsare | Webbläsaren saknar SVG‑stöd | Tillhandahåll fallback‑PNG genom att också exportera som EMF/WMF |

## Vanliga frågor

**Q: Kan jag både bädda in teckensnitt som Base64 och behålla extern CSS?**  
A: Ja. Sätt `exportFontsAsBase64(true)` samtidigt som du använder `CssStyleSheetType.EXTERNAL` för att separera teckensnittsdata från stilregler.

**Q: Hur konverterar jag en befintlig HTML tillbaka till ett Word‑dokument?**  
A: Läs in HTML med `Document doc = new Document("input.html");` och spara sedan med `doc.save("output.docx");`. Bevara round‑trip‑data med `exportRoundtripInformation` under den initiala exporten.

**Q: Påverkar SVG‑konverteringen prestandan?**  
A: Att konvertera stora metafiler till SVG kan öka bearbetningstiden, men den resulterande HTML‑filen är vanligtvis mindre och renderas snabbare i webbläsare.

**Q: Fungerar dessa alternativ även med Aspose.Words för .NET?**  
A: Samma koncept finns i .NET‑API‑et, även om metodnamnen kan skilja sig något (t.ex. `HtmlSaveOptions` är gemensamt för plattformarna).

**Q: Vilket alternativ bör jag välja för e‑post‑vänlig HTML?**  
A: Använd `SaveFormat.MHTML` med `exportCidUrlsForMhtmlResources` för att bädda in alla resurser direkt i e‑postens kropp.

---

**Senast uppdaterad:** 2025-12-19  
**Testat med:** Aspose.Words för Java 24.12  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}