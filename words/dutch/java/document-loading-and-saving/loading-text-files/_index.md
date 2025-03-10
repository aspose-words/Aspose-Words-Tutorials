---
title: Tekstbestanden laden met Aspose.Words voor Java
linktitle: Tekstbestanden laden met
second_title: Aspose.Words Java Documentverwerkings-API
description: Ontgrendel de kracht van Aspose.Words voor Java. Leer hoe u tekstdocumenten laadt, lijsten beheert, spaties verwerkt en de tekstrichting bepaalt.
weight: 13
url: /nl/java/document-loading-and-saving/loading-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tekstbestanden laden met Aspose.Words voor Java


## Inleiding tot het laden van tekstbestanden met Aspose.Words voor Java

In deze gids gaan we onderzoeken hoe je tekstbestanden laadt met Aspose.Words voor Java en hoe je ze bewerkt als Word-documenten. We behandelen verschillende aspecten, zoals het detecteren van lijsten, het verwerken van spaties en het regelen van tekstrichting.

## Stap 1: Lijsten detecteren

Om een tekstdocument te laden en lijsten te detecteren, kunt u de volgende stappen volgen:

```java
// Maak een plattetekstdocument in de vorm van een tekenreeks met onderdelen die als lijsten kunnen worden geïnterpreteerd.
// Bij het laden worden de eerste drie lijsten altijd gedetecteerd door Aspose.Words,
// en er worden lijstobjecten voor hen gemaakt nadat ze zijn geladen.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
//De vierde lijst, met spaties tussen het lijstnummer en de inhoud van het lijstitem,
// wordt alleen gedetecteerd als een lijst als "DetectNumberingWithWhitespaces" in een LoadOptions-object is ingesteld op true,
// om te voorkomen dat alinea's die met getallen beginnen, ten onrechte als lijsten worden beschouwd.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Laad het document terwijl u LoadOptions als parameter toepast en controleer het resultaat.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

 Deze code laat zien hoe je een tekstdocument met verschillende lijstformaten laadt en de`DetectNumberingWithWhitespaces` Optie om lijsten correct te detecteren.

## Stap 2: Ruimteopties verwerken

Om de voorloop- en volgspaties te regelen bij het laden van een tekstdocument, kunt u de volgende code gebruiken:

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

 In dit voorbeeld laden we een tekstdocument en verwijderen we voorloop- en volgspaties met behulp van`TxtLeadingSpacesOptions.TRIM` En`TxtTrailingSpacesOptions.TRIM`.

## Stap 3: De tekstrichting bepalen

Om de tekstrichting op te geven bij het laden van een tekstdocument, kunt u de volgende code gebruiken:

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

Deze code stelt de documentrichting in op automatische detectie (`DocumentDirection.AUTO`en laadt een tekstdocument met Hebreeuwse tekst. U kunt de documentrichting naar wens aanpassen.

## Volledige broncode voor het laden van tekstbestanden met Aspose.Words voor Java

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Maak een plattetekstdocument in de vorm van een tekenreeks met onderdelen die als lijsten kunnen worden geïnterpreteerd.
	// Bij het laden worden de eerste drie lijsten altijd gedetecteerd door Aspose.Words,
	// en er worden lijstobjecten voor hen gemaakt nadat ze zijn geladen.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// De vierde lijst, met spaties tussen het lijstnummer en de inhoud van het lijstitem,
	// wordt alleen gedetecteerd als een lijst als "DetectNumberingWithWhitespaces" in een LoadOptions-object is ingesteld op true,
	// om te voorkomen dat alinea's die met getallen beginnen, ten onrechte als lijsten worden beschouwd.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Laad het document terwijl u LoadOptions als parameter toepast en controleer het resultaat.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Conclusie

In deze handleiding hebben we onderzocht hoe u tekstbestanden kunt laden met Aspose.Words voor Java, lijsten kunt detecteren, spaties kunt verwerken en tekstrichting kunt regelen. Met deze technieken kunt u tekstdocumenten effectief manipuleren in uw Java-toepassingen.

## Veelgestelde vragen

### Wat is Aspose.Words voor Java?

Aspose.Words voor Java is een krachtige bibliotheek voor documentverwerking waarmee ontwikkelaars Word-documenten programmatisch kunnen maken, bewerken en converteren in Java-applicaties. Het biedt een breed scala aan functies voor het werken met tekst, tabellen, afbeeldingen en andere documentelementen.

### Hoe kan ik aan de slag met Aspose.Words voor Java?

Volg deze stappen om aan de slag te gaan met Aspose.Words voor Java:
1. Download en installeer de Aspose.Words voor Java-bibliotheek.
2.  Raadpleeg de documentatie op[Aspose.Words voor Java API-referentie](https://reference.aspose.com/words/java/) voor gedetailleerde informatie en voorbeelden.
3. Bekijk de voorbeeldcode en tutorials om te leren hoe u de bibliotheek effectief kunt gebruiken.

### Hoe laad ik een tekstdocument met Aspose.Words voor Java?

 Om een tekstdocument te laden met Aspose.Words voor Java, kunt u de volgende opdracht gebruiken:`TxtLoadOptions` klasse en de`Document` klasse. Zorg ervoor dat u de juiste opties opgeeft voor het verwerken van spaties en tekstrichting indien nodig. Raadpleeg de stapsgewijze handleiding in dit artikel voor een gedetailleerd voorbeeld.

### Kan ik een geladen tekstdocument naar andere formaten converteren?

 Ja, Aspose.Words voor Java stelt u in staat om een geladen tekstdocument te converteren naar verschillende formaten, waaronder DOCX, PDF en meer. U kunt de`Document` klasse om conversies uit te voeren. Controleer de documentatie voor specifieke conversievoorbeelden.

### Hoe ga ik om met spaties in geladen tekstdocumenten?

 U kunt bepalen hoe voorloop- en volgspaties worden verwerkt in geladen tekstdocumenten met behulp van`TxtLoadOptions` . Opties zoals`TxtLeadingSpacesOptions` En`TxtTrailingSpacesOptions`kunt u spaties indien nodig bijsnijden of behouden. Raadpleeg de sectie "Opties voor spaties verwerken" in deze handleiding voor een voorbeeld.

### Wat is de betekenis van tekstrichting in Aspose.Words voor Java?

Tekstrichting is essentieel voor documenten met gemengde scripts of talen, zoals Hebreeuws of Arabisch. Aspose.Words voor Java biedt opties om de tekstrichting te specificeren, wat zorgt voor een correcte weergave en opmaak van tekst in deze talen. De sectie "Tekstrichting beheren" in deze handleiding laat zien hoe u de tekstrichting instelt.

### Waar kan ik meer bronnen en ondersteuning vinden voor Aspose.Words voor Java?

 Voor aanvullende bronnen, documentatie en ondersteuning, bezoek de[Aspose.Words voor Java-documentatie](https://reference.aspose.com/words/java/)U kunt ook deelnemen aan de Aspose.Words communityforums of contact opnemen met Aspose-ondersteuning voor hulp bij specifieke problemen of vragen.

### Is Aspose.Words voor Java geschikt voor commerciële projecten?

Ja, Aspose.Words voor Java is geschikt voor zowel persoonlijke als commerciële projecten. Het biedt licentieopties om verschillende gebruiksscenario's te accommoderen. Zorg ervoor dat u de licentievoorwaarden en prijzen op de Aspose-website bekijkt om de juiste licentie voor uw project te kiezen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
