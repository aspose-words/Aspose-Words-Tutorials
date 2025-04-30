---
"description": "Leer hoe u Word-documenten naar Markdown converteert met Aspose.Words voor Java. Deze stapsgewijze handleiding behandelt tabeluitlijning, afbeeldingsverwerking en meer."
"linktitle": "Documenten opslaan als Markdown"
"second_title": "Aspose.Words Java Documentverwerking API"
"title": "Documenten opslaan als Markdown in Aspose.Words voor Java"
"url": "/nl/java/document-loading-and-saving/saving-documents-as-markdown/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Documenten opslaan als Markdown in Aspose.Words voor Java


## Inleiding tot het opslaan van documenten als Markdown in Aspose.Words voor Java

In deze stapsgewijze handleiding laten we zien hoe u documenten kunt opslaan als Markdown met Aspose.Words voor Java. Markdown is een lichtgewicht opmaaktaal die veel wordt gebruikt voor het opmaken van tekstdocumenten. Met Aspose.Words voor Java kunt u uw Word-documenten eenvoudig converteren naar Markdown-formaat. We behandelen verschillende aspecten van het opslaan van Markdown-bestanden, waaronder het uitlijnen van tabelinhoud en het verwerken van afbeeldingen.

## Vereisten

Voordat u begint, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:

- Java Development Kit (JDK) op uw systeem geïnstalleerd.
- Aspose.Words voor Java-bibliotheek. Je kunt het downloaden van [hier](https://releases.aspose.com/words/java/).

## Stap 1: Een Word-document maken

Laten we beginnen met het maken van een Word-document dat we later naar Markdown-formaat converteren. Je kunt dit document naar eigen wens aanpassen.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Een tabel met twee cellen invoegen
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Sla het document op als Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

In dit voorbeeld maken we een eenvoudige tabel met twee cellen en stellen we de uitlijning van de alinea's in deze cellen in. Vervolgens slaan we het document op als Markdown met behulp van de `MarkdownSaveOptions`.

## Stap 2: Pas de uitlijning van de tabelinhoud aan

Met Aspose.Words voor Java kunt u de uitlijning van de tabelinhoud aanpassen bij het opslaan als Markdown. U kunt de tabelinhoud links, rechts of gecentreerd uitlijnen, of dit automatisch laten bepalen op basis van de eerste alinea in elke tabelkolom.

Zo past u de uitlijning van de tabelinhoud aan:

```java
// Stel de uitlijning van de tabelinhoud in op links
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Stel de uitlijning van de tabelinhoud in op rechts
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Stel de uitlijning van de tabelinhoud in op gecentreerd
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Stel de uitlijning van de tabelinhoud in op automatisch (bepaald door de eerste alinea)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Door het veranderen van de `TableContentAlignment` Met deze eigenschap kunt u bepalen hoe de inhoud in tabellen wordt uitgelijnd bij het converteren naar Markdown.

## Stap 3: Afbeeldingen verwerken

Om afbeeldingen in uw Markdown-document op te nemen, moet u de map opgeven waar de afbeeldingen zich bevinden. Met Aspose.Words voor Java kunt u de map met afbeeldingen in de `MarkdownSaveOptions`.

Hier leest u hoe u de map met afbeeldingen instelt en het document met afbeeldingen opslaat:

```java
// Laad een document met afbeeldingen
Document doc = new Document("document_with_images.docx");

// Stel het pad naar de afbeeldingenmap in
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Sla het document op met afbeeldingen
doc.save("document_with_images.md", saveOptions);
```

Zorg ervoor dat u vervangt `"document_with_images.docx"` met het pad naar uw Word-document met afbeeldingen en `"images_folder/"` met het daadwerkelijke pad naar de map waar uw afbeeldingen zijn opgeslagen.

## Volledige broncode voor het opslaan van documenten als Markdown in Aspose.Words voor Java

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
	// Zorgt ervoor dat alle alinea's in de tabel worden uitgelijnd.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// In dit geval wordt de uitlijning overgenomen uit de eerste alinea in de overeenkomstige tabelkolom.
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

## Conclusie

In deze handleiding hebben we besproken hoe je documenten als Markdown kunt opslaan met Aspose.Words voor Java. We hebben het maken van een Word-document, het aanpassen van de uitlijning van tabelinhoud en het verwerken van afbeeldingen in Markdown-bestanden behandeld. Je kunt nu je Word-documenten efficiënt converteren naar Markdown-formaat, waardoor ze geschikt zijn voor diverse publicatieplatforms en documentatiebehoeften.

## Veelgestelde vragen

### Hoe installeer ik Aspose.Words voor Java?

Aspose.Words voor Java kan worden geïnstalleerd door de bibliotheek in uw Java-project op te nemen. U kunt de bibliotheek downloaden van [hier](https://releases.aspose.com/words/java/) en volg de installatie-instructies in de documentatie.

### Kan ik complexe Word-documenten met tabellen en afbeeldingen naar Markdown converteren?

Ja, Aspose.Words voor Java ondersteunt de conversie van complexe Word-documenten met tabellen, afbeeldingen en diverse opmaakelementen naar Markdown. U kunt de Markdown-uitvoer aanpassen aan de complexiteit van uw document.

### Hoe kan ik afbeeldingen in Markdown-bestanden verwerken?

Om afbeeldingen in Markdown-bestanden op te nemen, stelt u het pad naar de afbeeldingenmap in met behulp van de `setImagesFolder` methode in `MarkdownSaveOptions`Zorg ervoor dat de afbeeldingsbestanden in de opgegeven map worden opgeslagen, zodat Aspose.Words voor Java de afbeeldingsverwijzingen dienovereenkomstig verwerkt.

### Is er een proefversie van Aspose.Words voor Java beschikbaar?

Ja, u kunt een proefversie van Aspose.Words voor Java downloaden van de Aspose-website. Met de proefversie kunt u de mogelijkheden van de bibliotheek uitproberen voordat u een licentie aanschaft.

### Waar kan ik meer voorbeelden en documentatie vinden?

Voor meer voorbeelden, documentatie en gedetailleerde informatie over Aspose.Words voor Java kunt u terecht op de [documentatie](https://reference.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}