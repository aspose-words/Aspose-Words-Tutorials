---
date: 2026-01-16
description: Leer hoe je inches naar punten converteert, documentmetadata leest in
  Java, aangepaste eigenschappen toevoegt in Java en paginamarges instelt in Java
  met Aspose.Words voor Java.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: Inches omzetten naar punten – Documenteigenschappen gebruiken in Aspose.Words
  voor Java
url: /nl/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inches omzetten naar punten – Documenteigenschappen gebruiken in Aspose.Words voor Java

In deze tutorial ontdek je hoe je **inches omzetten naar punten** bij het instellen van paginamarges, documentmetadata in Java kunt lezen, aangepaste eigenschappen in Java kunt toevoegen, en kunt werken met ingebouwde documenteigenschappen met Aspose.Words voor Java. Of je nu rapporten, facturen of juridische documenten genereert, het beheersen van deze technieken geeft je fijne controle over het uiterlijk en de metadata van je Word‑bestanden.

## Snelle antwoorden
- **Hoe zet ik inches om naar punten?** Gebruik `ConvertUtil.inchToPoint(value)` van Aspose.Words.
- **Kan ik documentmetadata lezen in Java?** Ja – roep `doc.getBuiltInDocumentProperties()` of `doc.getCustomDocumentProperties()` aan.
- **Hoe voeg ik een aangepaste eigenschap toe in Java?** Gebruik `doc.getCustomDocumentProperties().add(name, value)`.
- **Welke methode stelt paginamarges in punten in?** `PageSetup.setTopMargin`, `setBottomMargin`, enz., accepteren puntwaarden.
- **Wordt koppelen aan een bladwijzer ondersteund?** Ja – gebruik `addLinkToContent` op de collectie van aangepaste eigenschappen.

## Introductie tot documenteigenschappen

Documenteigenschappen zijn een essentieel onderdeel van elk Word‑bestand. Ze slaan informatie op zoals titel, auteur, onderwerp, trefwoorden en eventuele aangepaste metadata die je nodig hebt voor downstream‑verwerking. In Aspose.Words voor Java kun je zowel ingebouwde als aangepaste documenteigenschappen manipuleren, en kun je ook lay‑outdetails zoals marges regelen door meeteenheden om te zetten (bijv. **inches omzetten naar punten**).

## Wat is “inches omzetten naar punten”?

In Word worden lay‑outmetingen uitgedrukt in punten (1 punt = 1/72 van een inch). Inches omzetten naar punten stelt je in staat marges, inspringingen en afstanden te definiëren met bekende imperiale eenheden, terwijl de API intern met punten werkt.

## Waarom documentmetadata beheren in Java?

Het insluiten van metadata maakt het gemakkelijker om te zoeken, te categoriseren en workflows te automatiseren. Bijvoorbeeld, je kunt een contract taggen met een “Authorized”‑vlag of een revisienummer opslaan voor audit‑trails. Het programmatisch lezen en schrijven van deze informatie zorgt voor consistentie over grote document‑batches.

## Voorvereisten
- Java 17+ (of een compatibele JDK)
- Aspose.Words for Java‑bibliotheek toegevoegd aan je project (Maven/Gradle)
- Een voorbeeld‑`.docx`‑bestand (bijv. `Properties.docx`) geplaatst in een toegankelijke map

## Stapsgewijze handleiding

### Enumereren van ingebouwde documenteigenschappen
Hieronder staat een eenvoudige test die een document opent en alle ingebouwde eigenschappen afdrukt, zoals Titel, Auteur en Trefwoorden.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **Pro tip:** Gebruik dit fragment om te verifiëren dat je metadata correct is geschreven tijdens eerdere stappen.

### Aangepaste documenteigenschappen toevoegen (add custom properties java)
Aangepaste eigenschappen stellen je in staat elk gewenst datatype op te slaan — boolean, string, datum, nummer, enz.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **Waarom dit belangrijk is:** Het toevoegen van een vlag zoals **Authorized** kan downstream‑goedkeuringsworkflows aandrijven zonder de documentinhoud te wijzigen.

### Een aangepaste eigenschap verwijderen
Als een eigenschap niet meer nodig is, kun je deze netjes verwijderen.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### Een koppeling naar inhoud configureren (bookmark linking)
Je kunt een bladwijzer maken en vervolgens een aangepaste eigenschap toevoegen die naar die bladwijzer verwijst, waardoor dynamische kruisverwijzingen mogelijk worden.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Eenheden omzetten (set page margins java)
Hier komt het belangrijkste trefwoord tot zijn recht. We stellen marges in inches in en vervolgens **inches omzetten naar punten** met `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Opmerking:** `ConvertUtil` biedt ook `pointToInch`, `mmToPoint`, enz. voor flexibele lay‑outafhandeling.

### Controle‑tekens gebruiken (read document metadata java)
Controle‑tekens helpen je tekststromen op te schonen. Dit voorbeeld vervangt een carriage‑return (`\r`) door de Windows‑regeleinde‑sequentie (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Veelvoorkomende problemen & oplossingen

| Probleem | Oorzaak | Oplossing |
|----------|---------|-----------|
| Marges zien er verkeerd uit na conversie | Verkeerde eenheid gebruikt (bijv. cm in plaats van inches) | Controleer of je `ConvertUtil.inchToPoint` aanroept voor inch‑waarden |
| Aangepaste eigenschap verschijnt niet | Eigenschap toegevoegd na het opslaan van het document | Roep `doc.save(...)` aan na het toevoegen van eigenschappen |
| Bladwijzer‑koppeling kapot | Typfout in bladwijzernaam | Zorg ervoor dat de bladwijzernaam exact overeenkomt in `addLinkToContent` |

## Veelgestelde vragen

### Hoe krijg ik toegang tot ingebouwde documenteigenschappen?

Om ingebouwde documenteigenschappen te benaderen in Aspose.Words voor Java, kun je de `getBuiltInDocumentProperties`‑methode op het `Document`‑object gebruiken. Deze methode retourneert een collectie van ingebouwde eigenschappen die je kunt itereren.

### Kan ik aangepaste documenteigenschappen aan een document toevoegen?

Ja, je kunt aangepaste documenteigenschappen aan een document toevoegen via de collectie `CustomDocumentProperties`. Je kunt aangepaste eigenschappen definiëren met verschillende datatypes, waaronder strings, booleans, datums en numerieke waarden.

### Hoe kan ik een specifieke aangepaste documenteigenschap verwijderen?

Om een specifieke aangepaste documenteigenschap te verwijderen, kun je de `remove`‑methode op de collectie `CustomDocumentProperties` gebruiken, waarbij je de naam van de te verwijderen eigenschap als parameter doorgeeft.

### Wat is het doel van koppelen naar inhoud binnen een document?

Koppelen naar inhoud binnen een document stelt je in staat dynamische verwijzingen naar specifieke delen van het document te maken. Dit kan handig zijn voor het creëren van interactieve documenten of kruisverwijzingen tussen secties.

### Hoe kan ik tussen verschillende meeteenheden converteren in Aspose.Words voor Java?

Je kunt tussen verschillende meeteenheden converteren in Aspose.Words voor Java door de `ConvertUtil`‑klasse te gebruiken. Deze biedt methoden om eenheden zoals inches naar punten, punten naar centimeters, enz. te converteren.

## Veelgestelde vragen

**V: Hoe lees ik documentmetadata Java zonder het hele bestand te laden?**  
A: Gebruik `DocumentInfo` om kern‑eigenschappen op te halen zonder de volledige documentinhoud te laden.

**V: Kan ik paginamarges in Java programmatisch instellen voor bestaande documenten?**  
A: Ja — open het document, wijzig de `PageSetup`‑marges (converteer inches naar punten indien nodig), en sla op.

**V: Is het mogelijk om aangepaste eigenschappen te exporteren naar PDF‑metadata?**  
A: Bij het opslaan naar PDF map Aspose.Words automatisch aangepaste documenteigenschappen naar aangepaste PDF‑metadata.

**V: Hebben controle‑tekens invloed op PDF‑conversie?**  
A: Ze worden behouden tijdens de conversie; echter, je wilt mogelijk regeleinden normaliseren voor consistentie.

**V: Welke Aspose.Words‑versie is vereist voor `ConvertUtil`?**  
A: `ConvertUtil` is beschikbaar sinds Aspose.Words 16.5; elke recente versie ondersteunt het.

## Conclusie

Door **inches omzetten naar punten** te beheersen, documentmetadata in Java te lezen en aangepaste eigenschappen in Java toe te voegen, krijg je volledige controle over zowel de visuele lay‑out als de verborgen data van je Word‑bestanden. Deze mogelijkheden stellen je in staat geautomatiseerde document‑pijplijnen te bouwen, naleving af te dwingen en rijk opgemaakte rapporten te maken — allemaal met Aspose.Words voor Java.

---

**Laatst bijgewerkt:** 2026-01-16  
**Getest met:** Aspose.Words for Java 24.11  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}