---
date: 2025-12-22
description: Leer hoe je Markdown exporteert door Word‑documenten naar Markdown te
  converteren met Aspose.Words for Java. Deze stapsgewijze gids behandelt tabeluitlijning,
  afbeeldingverwerking en meer.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Hoe Markdown te exporteren met Aspose.Words voor Java
url: /nl/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hoe Markdown Exporteren met Aspose.Words voor Java

## Introductie tot het Exporteren van Markdown in Aspose.Words voor Java

In deze stapsgewijze tutorial leer je **hoe je markdown kunt exporteren** vanuit Word‑documenten met Aspose.Words voor Java. Markdown is een lichtgewicht opmaaktaal die perfect is voor documentatie, statische site‑generatoren en vele publicatieplatformen. Aan het einde van deze gids kun je **Word naar markdown converteren**, de uitlijning van tabellen aanpassen en **afbeeldingen in markdown** moeiteloos verwerken.

## Snelle Antwoorden
- **Wat is de primaire klasse voor opslaan als Markdown?** `MarkdownSaveOptions`
- **Kunnen afbeeldingen automatisch worden ingebed?** Ja – stel de afbeeldingsmap in via `setImagesFolder`.
- **Hoe kan ik de uitlijning van tabellen regelen?** Gebruik `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **Wat zijn de minimale vereisten?** JDK 8+ en de Aspose.Words voor Java‑bibliotheek.
- **Is er een proefversie beschikbaar?** Ja, download deze van de Aspose‑website.

## Wat betekent “hoe markdown exporteren”?
Markdown exporteren betekent dat je een rijk‑tekst Word‑document (`.docx`) neemt en een platte‑tekst `.md`‑bestand genereert dat koppen, tabellen en afbeeldingen behoudt in Markdown‑syntaxis.

## Waarom Aspose.Words voor Java gebruiken om docx met afbeeldingen te converteren?
Aspose.Words verwerkt complexe lay‑outs, ingebedde afbeeldingen en tabelstructuren zonder verlies van kwaliteit. Het biedt ook fijne controle over de Markdown‑output, zoals tabeluitlijning en beheer van de afbeeldingsmap.

## Vereisten

- Java Development Kit (JDK) geïnstalleerd op je systeem.
- Aspose.Words voor Java‑bibliotheek. Je kunt deze downloaden van [hier](https://releases.aspose.com/words/java/).

## Stap 1: Maak een eenvoudig Word‑document

Eerst maken we een klein document dat een tabel bevat. Hiermee kunnen we later **de uitlijning van tabellen aanpassen** demonstreren.

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

In het bovenstaande fragment doen we:

1. Maak een nieuw `Document` aan.
2. Gebruik `DocumentBuilder` om een tabel met twee cellen in te voegen.
3. Pas **rechts** en **centraal** alinea‑uitlijning toe binnen elke cel.
4. Sla het bestand op als Markdown met `MarkdownSaveOptions`.

## Stap 2: Pas de uitlijning van tabelinhoud aan

Aspose.Words stelt je in staat te bepalen hoe tabelcellen worden weergegeven in de uiteindelijke Markdown. Je kunt links, rechts of gecentreerd forceren, of de bibliotheek automatisch laten beslissen op basis van de eerste alinea in elke kolom.

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

Door de eigenschap `TableContentAlignment` te wijzigen, beheer je **het aanpassen van de tabeluitlijning** voor de Markdown‑output.

## Stap 3: Afbeeldingen verwerken bij het exporteren naar markdown

Wanneer een document afbeeldingen bevat, wil je dat die afbeeldingen correct verschijnen in het gegenereerde `.md`‑bestand. Stel de map in waar Aspose.Words de geëxtraheerde afbeeldingen moet plaatsen.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Vervang `"document_with_images.docx"` door het pad naar je bronbestand en `"images_folder/"` door de locatie waar je de afbeeldingen wilt opslaan. De resulterende Markdown zal afbeeldingslinks bevatten die naar deze map wijzen, waardoor je **afbeeldingen in markdown** moeiteloos kunt verwerken.

## Complete Broncode voor het Opslaan van Documenten als Markdown in Aspose.Words voor Java

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

## Veelvoorkomende Problemen en Oplossingen

| Probleem | Oplossing |
|----------|-----------|
| Afbeeldingen verschijnen niet in het `.md`‑bestand | Controleer of `setImagesFolder` naar een beschrijfbare map wijst en of de map correct wordt gerefereerd in de gegenereerde Markdown. |
| Tabeluitlijning ziet er verkeerd uit | Gebruik `TableContentAlignment.AUTO` zodat Aspose.Words de beste uitlijning kan afleiden op basis van de eerste alinea van elke kolom. |
| Uitvoerbestand is leeg | Zorg ervoor dat het `Document`‑object daadwerkelijk inhoud bevat voordat je `save` aanroept. |

## Veelgestelde Vragen

**Q: Hoe installeer ik Aspose.Words voor Java?**  
A: Aspose.Words voor Java kan worden geïnstalleerd door de bibliotheek op te nemen in je Java‑project. Je kunt de bibliotheek downloaden van [hier](https://releases.aspose.com/words/java/) en de installatie‑instructies volgen die in de documentatie worden gegeven.

**Q: Kan ik complexe Word‑documenten met tabellen en afbeeldingen naar Markdown converteren?**  
A: Ja, Aspose.Words voor Java ondersteunt de conversie van complexe Word‑documenten met tabellen, afbeeldingen en diverse opmaak‑elementen naar Markdown. Je kunt de Markdown‑output aanpassen aan de complexiteit van je document.

**Q: Hoe kan ik afbeeldingen in Markdown‑bestanden verwerken?**  
A: Stel het pad van de afbeeldingsmap in met de `setImagesFolder`‑methode in `MarkdownSaveOptions`. Zorg ervoor dat de afbeeldingsbestanden in de opgegeven map worden opgeslagen; Aspose.Words genereert de juiste Markdown‑afbeeldingslinks.

**Q: Is er een proefversie van Aspose.Words voor Java beschikbaar?**  
A: Ja, je kunt een proefversie van Aspose.Words voor Java verkrijgen via de Aspose‑website. De proefversie stelt je in staat de mogelijkheden van de bibliotheek te evalueren voordat je een licentie aanschaft.

**Q: Waar kan ik meer voorbeelden en documentatie vinden?**  
A: Voor meer voorbeelden, documentatie en gedetailleerde informatie over Aspose.Words voor Java, bezoek de [documentatie](https://reference.aspose.com/words/java/).

---

**Laatst bijgewerkt:** 2025-12-22  
**Getest met:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}