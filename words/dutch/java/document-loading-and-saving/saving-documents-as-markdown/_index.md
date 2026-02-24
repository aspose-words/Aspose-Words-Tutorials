---
date: 2026-02-24
description: Leer hoe je Word naar markdown kunt converteren met Aspose.Words voor
  Java. Deze gids behandelt tabeluitlijning, beeldverwerking en hoe je een document
  als markdown opslaat.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Converteer Word naar Markdown met Aspose.Words voor Java
url: /nl/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word naar Markdown converteren met Aspose.Words voor Java

## Introductie tot Word naar Markdown converteren met Aspose.Words voor Java

In deze stap‑voor‑stap‑handleiding leer je **hoe je Word naar Markdown kunt converteren** met de krachtige Aspose.Words voor Java API. Markdown is een lichtgewicht opmaaktaal die veel ontwikkelaars en contentplatforms gebruiken voor schone, leesbare documentatie. Aan het einde van deze gids kun je elk `.docx`‑bestand nemen, tabellen, afbeeldingen en opmaak behouden, en exporteren als een `.md`‑bestand dat klaar is voor static‑site generators, GitHub‑README’s of elke markdown‑vriendelijke workflow.

## Snelle antwoorden
- **Welke bibliotheek heb ik nodig?** Aspose.Words voor Java (`aspose-words.jar`).
- **Kan ik de uitlijning van tabellen aanpassen?** Ja – gebruik `TableContentAlignment` in `MarkdownSaveOptions`.
- **Hoe worden afbeeldingen afgehandeld?** Stel een afbeeldingenmap in met `setImagesFolder()`; de bibliotheek maakt relatieve links.
- **Heb ik een licentie nodig voor productie?** Een commerciële licentie is vereist voor niet‑trial gebruik.
- **Is dit compatibel met Java 17?** Ja, de bibliotheek ondersteunt Java 8 en hoger.

## Wat is Word naar Markdown converteren?

Word naar Markdown converteren betekent dat je de rijke opmaak van een Microsoft Word‑document vertaalt naar platte‑tekst markdown‑syntaxis. Dit proces behoudt koppen, lijsten, tabellen en afbeeldingsverwijzingen terwijl binaire opmaak wordt verwijderd, waardoor de inhoud draagbaar en versie‑control‑vriendelijk wordt.

## Waarom Aspose.Words voor Java gebruiken om een document als markdown op te slaan?

* **Volledige getrouwheid** – tabellen, afbeeldingen en complexe lay-outs worden behouden.
* **Fijne controle** – je kunt de uitlijning van tabellen, afbeeldingspaden en meer aanpassen.
* **Geen externe afhankelijkheden** – de bibliotheek werkt out‑of‑the‑box zonder dat Office geïnstalleerd hoeft te zijn.
* **Cross‑platform** – werkt op Windows, Linux en macOS met elke Java‑runtime.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

- Java Development Kit (JDK) geïnstalleerd op je systeem.
- Aspose.Words voor Java bibliotheek. Je kunt deze downloaden van [hier](https://releases.aspose.com/words/java/).

## Stapsgewijze handleiding

### Stap 1: Maak een Word‑document dat wordt geconverteerd

Eerst bouwen we een eenvoudig Word‑document met een tabel van twee cellen. Dit voorbeeld laat zien hoe alinea‑uitlijning binnen tabelcellen wordt gerespecteerd wanneer we later **het document als markdown opslaan**.

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

### Stap 2: Pas de uitlijning van tabelinhoud aan

Aspose.Words voor Java stelt je in staat te bepalen hoe tabelcellen worden uitgelijnd in de gegenereerde markdown. Gebruik de eigenschap `TableContentAlignment` om **tabeluitlijning aan te passen** naar links, rechts, gecentreerd, of laat de bibliotheek automatisch beslissen op basis van de eerste alinea in elke kolom.

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

Door deze instelling te wijzigen kun je **Word‑tabellen naar markdown exporteren** met de exacte uitlijning die je nodig hebt voor downstream render‑engines.

### Stap 3: Afbeeldingen afhandelen tijdens conversie

Wanneer je bron‑Word‑document afbeeldingen bevat, moet je Aspose.Words vertellen waar de geëxporteerde afbeeldingsbestanden moeten worden geplaatst. De methode `setImagesFolder` op `MarkdownSaveOptions` definieert de map die de afbeeldingsassets bevat, en de markdown bevat relatieve links naar die bestanden.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Vervang `"document_with_images.docx"` door het pad naar je bronbestand en `"images_folder/"` door de gewenste uitvoermap voor de afbeeldingen.

### Complete broncode voor alle scenario's

Hieronder staat een geconsolideerd voorbeeld dat laat zien hoe je **automatische tabeluitlijning**, **aangepaste uitlijning** en **een afbeeldingenmap instelt** in één methode. Deze snippet spiegelt de oorspronkelijke tutorialcode en werkt ongewijzigd.

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

## Veelvoorkomende problemen en oplossingen

| Probleem | Reden | Oplossing |
|----------|-------|-----------|
| Afbeeldingen verschijnen als kapotte links | `setImagesFolder` niet ingesteld of mappad onjuist | Controleer of het mappad correct is en of de map schrijfbaar is |
| Tabeluitlijning ziet er verkeerd uit | Verkeerde `TableContentAlignment`‑waarde | Gebruik `TableContentAlignment.AUTO` om de eerste alinea te laten bepalen, of stel expliciet LEFT/RIGHT/CENTER in |
| Uitvoerbestand is leeg | Opslagopties niet doorgegeven aan `doc.save()` | Zorg ervoor dat je de `MarkdownSaveOptions`‑instantie doorgeeft aan de `save`‑methode |
| Niet‑ondersteunde Word‑functies (bijv. SmartArt) | Markdown kan sommige complexe objecten niet weergeven | Converteer die elementen naar afbeeldingen vóór het opslaan, of vereenvoudig het bron‑document |

## Veelgestelde vragen

**V: Hoe installeer ik Aspose.Words voor Java?**  
A: Aspose.Words voor Java kan worden geïnstalleerd door de bibliotheek op te nemen in je Java‑project. Je kunt de bibliotheek downloaden van [hier](https://releases.aspose.com/words/java/) en de installatie‑instructies volgen die in de documentatie staan.

**V: Kan ik complexe Word‑documenten met tabellen en afbeeldingen naar Markdown converteren?**  
A: Ja, Aspose.Words voor Java ondersteunt de conversie van complexe Word‑documenten met tabellen, afbeeldingen en diverse opmaak‑elementen naar Markdown. Je kunt de Markdown‑output aanpassen aan de complexiteit van je document.

**V: Hoe kan ik afbeeldingen in Markdown‑bestanden verwerken?**  
A: Stel het pad van de afbeeldingenmap in met de `setImagesFolder`‑methode in `MarkdownSaveOptions`. Zorg ervoor dat de afbeeldingsbestanden in de opgegeven map worden opgeslagen, en Aspose.Words voor Java regelt de afbeeldingsverwijzingen.

**V: Is er een proefversie van Aspose.Words voor Java beschikbaar?**  
A: Ja, je kunt een proefversie van Aspose.Words voor Java verkrijgen via de Aspose‑website. De proefversie stelt je in staat de mogelijkheden van de bibliotheek te evalueren voordat je een licentie aanschaft.

**V: Waar vind ik meer voorbeelden en documentatie?**  
A: Voor meer voorbeelden, documentatie en gedetailleerde informatie over Aspose.Words voor Java, bezoek de [documentatie](https://reference.aspose.com/words/java/).

## Conclusie

In deze gids hebben we alles behandeld wat je nodig hebt om **Word naar Markdown te converteren** met Aspose.Words voor Java: het maken van een bron‑document, **tabeluitlijning aanpassen**, en afbeeldingen verwerken met de juiste mapconfiguratie. Met deze technieken kun je betrouwbaar Word‑inhoud exporteren naar markdown voor blogs, documentatiesites of elk platform dat markdown ondersteunt.

---

**Laatst bijgewerkt:** 2026-02-24  
**Getest met:** Aspose.Words voor Java 24.12 (latest at time of writing)  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}