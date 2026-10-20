---
date: 2025-12-27
description: Leer hoe je de richting instelt, txt‑bestanden laadt, spaties verwijdert
  en txt naar docx converteert met Aspose.Words voor Java.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Hoe de richting instellen en tekstbestanden laden met Aspose.Words voor Java
url: /nl/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hoe de Richting in te Stellen en Tekstbestanden te Laden met Aspose.Words voor Java

## Introductie tot het Laden van Tekstbestanden met Aspose.Words voor Java

In deze gids ontdek je **hoe je de richting instelt** bij het laden van platte‑tekstdocumenten en zie je praktische manieren om **txt te laden**, **spaties te trimmen**, en **txt naar docx te converteren** met Aspose.Words voor Java. Of je nu een document‑conversieservice bouwt of fijne controle nodig hebt over lijstdetectie, deze tutorial leidt je stap voor stap met duidelijke uitleg en kant‑klaar code.

## Snelle Antwoorden
- **Hoe stel ik de tekstrichting in voor een geladen TXT‑bestand?** Gebruik `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` of specificeer `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`.
- **Kan Aspose.Words genummerde lijsten in platte tekst detecteren?** Ja – schakel `DetectNumberingWithWhitespaces` in via `TxtLoadOptions`.
- **Hoe kan ik voor‑ en achtervoegsels van spaties trimmen?** Stel `TxtLeadingSpacesOptions.TRIM` en `TxtTrailingSpacesOptions.TRIM` in.
- **Is het mogelijk om een TXT‑bestand in één regel naar DOCX te converteren?** Laad de TXT met `TxtLoadOptions` en roep `Document.save("output.docx")` aan.
- **Welke Java‑versie is vereist?** Java 8+ is voldoende voor Aspose.Words 24.x.

## Wat betekent “hoe de richting in te stellen” in Aspose.Words?
Wanneer een tekstbestand rechts‑naar‑links‑scripts bevat (bijv. Hebreeuws of Arabisch), moet de bibliotheek de leesvolgorde kennen. De `DocumentDirection`‑enum laat je **de richting handmatig instellen** of Aspose automatisch laten detecteren, zodat de lay‑out en bidi‑opmaak correct zijn.

## Waarom Aspose.Words gebruiken voor het laden van TXT‑bestanden?
- **Nauwkeurige lijstdetectie** – verwerkt genummerde, opsommingstekens en door witruimte gescheiden lijsten.
- **Fijne controle over spaties** – trimmen of behouden van voor‑ en achtervoegsels.
- **Automatische detectie van tekstrichting** – ideaal voor meertalige documenten.
- **Eén‑staps conversie** – laad een `.txt` en sla op als `.docx`, `.pdf` of elk ondersteund formaat.

## Vereisten
- Java 8 of nieuwer.
- Aspose.Words voor Java‑bibliotheek (voeg de Maven/Gradle‑dependency toe of de JAR aan je project).
- Basiskennis van Java‑I/O‑streams.

## Stapsgewijze Gids

### Stap 1: Lijsten Detecteren (hoe txt te laden)
Om een tekstdocument te laden en automatisch lijsten te detecteren, maak je een `TxtLoadOptions`‑instantie aan en schakel je lijstdetectie in. De code hieronder toont verschillende lijststijlen en activeert witruimte‑bewuste nummering.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
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
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Pro tip:** Als je alleen basislijstdetectie nodig hebt, kun je de witruimte‑optie overslaan – Aspose herkent nog steeds standaard `1.` en `1)` patronen.

### Stap 2: Spatie‑opties Behandelen (hoe spaties te trimmen)
Voor‑ en achtervoegsels veroorzaken vaak opmaakproblemen. Gebruik `TxtLeadingSpacesOptions` en `TxtTrailingSpacesOptions` om dit gedrag te regelen.

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

> **Waarom het belangrijk is:** Het trimmen van spaties voorkomt ongewenste inspringing in de resulterende DOCX, waardoor het document er netjes uitziet zonder handmatige nabewerking.

### Stap 3: Tekstrichting Beheren (hoe de richting in te stellen)
Voor rechts‑naar‑links‑talen stel je de documentrichting in vóór het laden. Het voorbeeld hieronder laadt een Hebreeuws tekstbestand en print de bidi‑vlag om de richting te bevestigen.

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

> **Veelvoorkomende valkuil:** Het vergeten van `DocumentDirection` kan leiden tot onleesbare Arabische/Hebreeuwse tekst waarbij tekens in de verkeerde volgorde staan.

### Volledige Broncode voor het Laden van Tekstbestanden met Aspose.Words voor Java
Hieronder staat de volledige, kant‑klaar broncode die lijstdetectie, spatie‑beheer en richtingscontrole combineert. Je kunt deze kopiëren‑plakken in één klasse en de drie testmethoden afzonderlijk uitvoeren.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
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
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
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

## Veelvoorkomende Problemen en Oplossingen
| Probleem | Oorzaak | Oplossing |
|----------|---------|-----------|
| Lijsten worden niet gedetecteerd | `DetectNumberingWithWhitespaces` staat op `false` voor door witruimte gescheiden lijsten | Schakel `loadOptions.setDetectNumberingWithWhitespaces(true)` in |
| Extra inspringing na laden | Voor‑spaties werden behouden | Stel `TxtLeadingSpacesOptions.TRIM` in |
| Hebreeuwse tekst verschijnt omgekeerd | Documentrichting niet ingesteld of ingesteld op `LEFT_TO_RIGHT` | Gebruik `DocumentDirection.AUTO` of `RIGHT_TO_LEFT` |
| Uitvoer‑DOCX is leeg | Invoerstroom werd niet gereset vóór de tweede laadactie | Maak een nieuwe `ByteArrayInputStream` aan voor elke laadaanroep |

## Veelgestelde Vragen

### Q: Wat is Aspose.Words voor Java?
A: Aspose.Words voor Java is een krachtige documentverwerkingsbibliotheek die ontwikkelaars in staat stelt Word‑documenten programmatisch te maken, te bewerken en te converteren in Java‑applicaties. Het ondersteunt een breed scala aan functies, van eenvoudig tekstladen tot complexe opmaak en conversie.

### Q: Hoe kan ik aan de slag met Aspose.Words voor Java?
A: 1. Download en installeer de Aspose.Words voor Java‑bibliotheek. 2. Raadpleeg de documentatie op [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) voor gedetailleerde informatie en voorbeelden. 3. Verken de voorbeeldcode en tutorials om de bibliotheek effectief te leren gebruiken.

### Q: Hoe laad ik een tekstdocument met Aspose.Words voor Java?
A: Gebruik de `TxtLoadOptions`‑klasse samen met de `Document`‑constructor. Specificeer opties zoals lijstdetectie, spatie‑beheer of tekstrichting zoals gedemonstreerd in de stap‑voor‑stap‑secties hierboven.

### Q: Kan ik een geladen tekstdocument naar andere formaten converteren?
A: Ja. Nadat je het TXT‑bestand in een `Document`‑object hebt geladen, roep je `doc.save("output.pdf")`, `doc.save("output.docx")` of een ander ondersteund formaat aan.

### Q: Hoe ga ik om met spaties in geladen tekstdocumenten?
A: Beheer voor‑ en achtervoegsels met `TxtLeadingSpacesOptions` en `TxtTrailingSpacesOptions`. Stel ze in op `TRIM` om ongewenste witruimte te verwijderen, of op `PRESERVE` als je de oorspronkelijke spatiëring wilt behouden.

### Q: Wat is het belang van tekstrichting in Aspose.Words voor Java?
A: Tekstrichting zorgt voor correcte weergave van rechts‑naar‑links‑scripts (Hebreeuws, Arabisch, enz.). Door `DocumentDirection` in te stellen, garandeer je dat bidi‑tekst juist wordt weergegeven in het uiteindelijke document.

### Q: Waar vind ik meer bronnen en ondersteuning voor Aspose.Words voor Java?
A: Bezoek de [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) voor API‑referenties, code‑samples en uitgebreide handleidingen. Je kunt ook deelnemen aan de Aspose‑communityforums of contact opnemen met de Aspose‑ondersteuning voor specifieke vragen.

### Q: Is Aspose.Words voor Java geschikt voor commerciële projecten?
A: Ja. Het biedt licentie‑opties voor zowel persoonlijk als commercieel gebruik. Bekijk de licentievoorwaarden op de Aspose‑website om het juiste plan voor jouw project te kiezen.

## Conclusie
Je beschikt nu over een complete toolkit om **txt‑bestanden te laden**, **lijsten te detecteren**, **spaties te trimmen** en **richting in te stellen** bij het omzetten van platte tekst naar rijke Word‑documenten met Aspose.Words voor Java. Pas deze patronen toe om document‑workflows te automatiseren, meertalige ondersteuning te verbeteren en elke keer een nette, professionele output te garanderen.

---

**Laatst bijgewerkt:** 2025-12-27  
**Getest met:** Aspose.Words voor Java 24.12  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}