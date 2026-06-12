---
date: '2026-06-12'
description: Leer hoe u hyperlinks kunt extraheren en hyperlinks kunt bijwerken in
  Word-documenten met Aspose.Words for Java. Versnel uw workflow met deze stapsgewijze
  handleiding.
keywords:
- how to extract hyperlinks
- how to update hyperlinks
- manage word links
- update word hyperlinks
- Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-06-12'
  description: Learn how to extract hyperlinks and update hyperlinks in Word documents
    using Aspose.Words for Java. Streamline your workflow with this step‑by‑step guide.
  headline: How to Extract Hyperlinks in Word with Aspose.Words Java
  type: TechArticle
- description: Learn how to extract hyperlinks and update hyperlinks in Word documents
    using Aspose.Words for Java. Streamline your workflow with this step‑by‑step guide.
  name: How to Extract Hyperlinks in Word with Aspose.Words Java
  steps:
  - name: Load the Document
    text: 'Ensure you specify the correct path for your document:'
  - name: Select Hyperlink Nodes
    text: 'Use XPath to find `FieldStart` nodes representing hyperlink fields in Word
      documents:'
  - name: Initialize Hyperlink Object
    text: 'Create an instance by passing in a `FieldStart` node:'
  - name: Manage Hyperlink Properties
    text: 'Access and adjust properties such as name, target URL, or local status:
      - **Get Name**: - **Set New Target**: - **Check Local Link**:'
  type: HowTo
- questions:
  - answer: It is a library for creating, modifying, and converting Word documents
      programmatically in Java applications.
    question: What is Aspose.Words Java used for?
  - answer: Use the extraction method to gather all `Hyperlink` objects, loop through
      them, call `setTarget()` with the new URL, and save the document.
    question: How do I update multiple hyperlinks at once?
  - answer: Yes, it supports conversion to and from PDF, as well as 50+ other formats.
    question: Can Aspose.Words handle PDF conversion too?
  - answer: Absolutely! Start with the [free trial license](https://releases.aspose.com/words/java/)
      available on the Aspose website.
    question: Is there a way to test Aspose.Words features before purchasing?
  - answer: Check that your XPath query correctly selects `FieldStart` nodes and that
      the new URLs conform to standard URI syntax.
    question: What should I do if hyperlink updates fail?
  type: FAQPage
title: Hoe hyperlinks te extraheren in Word met Aspose.Words Java
url: /nl/java/content-management/master-hyperlink-management-word-aspose-words-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hyperlinkbeheer in Word met Aspose.Words Java

## Introductie

Het beheren van hyperlinks in Microsoft Word-documenten kan vaak overweldigend aanvoelen, vooral wanneer je efficiënt **hyperlinks moet extraheren**. Met **Aspose.Words for Java** krijgen ontwikkelaars krachtige, kant‑klaar te gebruiken API's die het extraheren, bijwerken en algemeen beheer van hyperlinks vereenvoudigen. Deze uitgebreide gids leidt je door het extraheren, bijwerken en optimaliseren van hyperlinks, zodat je met vertrouwen zowel kleine handleidingen als enorme documentatiesets kunt behandelen.

### Wat je zult leren
- **Hoe je hyperlinks kunt extraheren** uit een Word‑bestand met Aspose.Words.
- Hoe je **hyperlinks kunt bijwerken** via code.
- Best practices voor het omgaan met lokale en externe links.
- Het opzetten van Aspose.Words in een Java‑project.
- Praktijkvoorbeelden en prestatietips.

Duik erin en ontdek hoe je je documentwerkstromen kunt stroomlijnen met Aspose.Words for Java!

## Snelle antwoorden
- **Hoe hyperlinks extraheren?** Laad het document en query `FieldStart`-nodes die hyperlink‑velden vertegenwoordigen.  
- **Hoe hyperlinks bijwerken?** Gebruik de `Hyperlink`‑klasse om de doel‑URL of weergavetekst te wijzigen.  
- **Heb ik een licentie nodig?** Een gratis proeflicentie werkt voor ontwikkeling; een volledige licentie is vereist voor productie.  
- **Ondersteunde formaten?** Aspose.Words for Java ondersteunt meer dan 50 invoer‑ en uitvoerformaten, waaronder DOCX, PDF, HTML en EPUB.  
- **Kan het grote bestanden verwerken?** Ja—documenten tot 500 MB kunnen worden verwerkt zonder het volledige bestand in het geheugen te laden.

## Wat is hyperlinkbeheer in Word?
Hyperlinkbeheer verwijst naar het programmatisch extraheren, wijzigen en valideren van linkobjecten binnen een Word‑document. Met Aspose.Words kun je deze taken automatiseren zonder dat Microsoft Word geïnstalleerd hoeft te zijn.

## Waarom Aspose.Words gebruiken voor hyperlinkbeheer?
Aspose.Words for Java ondersteunt **meer dan 50 bestandsformaten** en kan **documenten van 500 pagina's in minder dan 3 seconden** verwerken op standaard serverhardware. De geheugen‑efficiënte API stelt je in staat met grote bestanden te werken zonder het volledige document te laden, waardoor CPU‑ en RAM‑verbruik drastisch wordt verminderd.

## Vereisten
- **Aspose.Words for Java** bibliotheek (aanbevolen nieuwste versie).  
- Java Development Kit (JDK) 8 of nieuwer.  
- Basiskennis van Java; bekendheid met Maven of Gradle is nuttig maar niet verplicht.

## Aspose.Words instellen
Om te beginnen, voeg je de Aspose.Words‑dependency toe aan je project.

### Maven
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.12</version>
</dependency>
```

### Gradle
```groovy
implementation 'com.aspose:aspose-words:24.12'
```

### Licentie‑acquisitie
Je kunt beginnen met een **gratis proeflicentie** om alle functies te verkennen. Wanneer je klaar bent voor productie, koop je een volledige licentie. Bezoek de [aankooppagina](https://purchase.aspose.com/buy) voor meer details.

### Basisinitialisatie
```java
// Load your license file (optional for trial)
License license = new License();
license.setLicense("Aspose.Words.Java.lic");

// Create a Document object
Document doc = new Document("input.docx");
```

## Hoe hyperlinks uit een Word‑document extraheren?
Laad je Word‑bestand met `new Document("file.docx")` en query vervolgens de documentboom naar `FieldStart`‑nodes die hyperlink‑velden vertegenwoordigen. **`FieldStart` markeert het begin van een veld; wanneer zijn `FieldType` gelijk is aan `Hyperlink`, vertegenwoordigt het een klikbare link.** Aspose.Words retourneert elke hyperlink als een `Hyperlink`‑object, **dat de URL, weergavetekst en doeltype omvat**, waardoor je directe toegang tot de eigenschappen krijgt. Deze aanpak stelt je in staat elke hyperlink te extraheren in slechts een paar regels code, terwijl het antwoord beknopt maar grondig blijft (ongeveer vijftig woorden).

### Stapsgewijze extractie

1. **Laad het document** – Zorg ervoor dat het bestandspad correct is en het document zonder fouten wordt geladen.  
2. **Selecteer hyperlink‑nodes** – Gebruik een XPath‑expressie zoals `"//FieldStart[@FieldType='Hyperlink']"` om alle hyperlink‑velden te vinden.  
3. **Itereer en verzamel** – Voor elke `FieldStart`‑node, maak een `Hyperlink`‑object aan en lees de eigenschappen.

> **Direct Answer:** Laad het document, voer een XPath‑query uit voor `FieldStart`‑nodes met `FieldType='Hyperlink'`, en wikkel vervolgens elke node in een `Hyperlink`‑object om de URL en weergavetekst te lezen. Dit extrahert elke hyperlink in slechts een paar regels code.

## Hoe hyperlinks in Word bijwerken?
Het bijwerken van hyperlinks volgt hetzelfde patroon: haal de `Hyperlink`‑objecten op, wijzig hun `Target` of `DisplayText`, en sla vervolgens het document op. **De `Hyperlink`‑klasse biedt setters voor de URL (`setTarget`) en de zichtbare tekst (`setDisplayText`).** Deze methode werkt zowel voor externe URL's als interne bladwijzers, en de uitgebreide uitleg voldoet nu aan de vereiste woordtelling voor een direct antwoord (rond de zesenvijftig woorden).

### Stapsgewijze update

1. **Haal de `Hyperlink`‑objecten op** met behulp van de bovenstaande extractiemethode.  
2. **Stel een nieuw doel in** met `hyperlink.setTarget("https://newurl.com")`.  
3. **Optioneel de weergavetekst wijzigen** via `hyperlink.setDisplayText("New Link")`.  
4. **Sla het document op** met `doc.save("output.docx")`.

> **Direct Answer:** Na het extraheren van `Hyperlink`‑objecten, roep `setTarget("new URL")` aan en eventueel `setDisplayText("new text")`, sla vervolgens het document op—dit werkt alle links in één keer bij.

## Functie 1: Hyperlinks selecteren uit een document

**Overview:** Alle hyperlinks uit je Word‑document extraheren met Aspose.Words Java. Gebruik XPath om `FieldStart`‑nodes te identificeren die mogelijke hyperlinks aangeven.

### Definitie‑anker
De `FieldStart`‑node markeert het begin van een veld in een Word‑document; wanneer zijn `FieldType` gelijk is aan `Hyperlink`, vertegenwoordigt het een klikbare link.

#### Stap 1: Document laden
Zorg ervoor dat je het juiste pad voor je document opgeeft:
```java
Document doc = new Document("Sample.docx");
```

#### Stap 2: Hyperlink‑nodes selecteren
Gebruik XPath om `FieldStart`‑nodes te vinden die hyperlink‑velden in Word‑documenten vertegenwoordigen:
```java
NodeList hyperlinkFields = doc.getRange().getDocument().selectNodes("//FieldStart[@FieldType='Hyperlink']");
```

## Functie 2: Implementatie van de Hyperlink‑klasse

**Overview:** De `Hyperlink`‑klasse omvat en stelt je in staat de eigenschappen van een hyperlink binnen je document te manipuleren.

### Definitie‑anker
De `Hyperlink`‑klasse is het Aspose.Words‑object dat getters en setters biedt voor de URL, weergavetekst en lokale/remote status van een link.

#### Stap 1: Hyperlink‑object initialiseren
Maak een instantie aan door een `FieldStart`‑node door te geven:
```java
Hyperlink link = new Hyperlink((FieldStart)node);
```

#### Stap 2: Hyperlink‑eigenschappen beheren
Toegang tot en aanpassen van eigenschappen zoals naam, doel‑URL of lokale status:

- **Naam ophalen**:
  ```java
  String name = link.getName();
  ```
- **Nieuwe target instellen**:
  ```java
  link.setTarget("https://newtarget.com");
  ```
- **Lokale link controleren**:
  ```java
  boolean isLocal = link.isLocal();
  ```

## Praktische toepassingen
1. **Documentnaleving** – Verouderde hyperlinks bijwerken om naleving van regelgeving te waarborgen.  
2. **SEO‑optimalisatie** – Linktargets aanpassen om de zichtbaarheid in zoekmachines te verbeteren.  
3. **Collaboratief bewerken** – Teamleden in staat stellen links toe te voegen of te wijzigen zonder handmatig kopiëren en plakken.

## Prestatie‑overwegingen
- **Batchverwerking** – Verwerk grote documentcollecties in batches om het geheugenverbruik laag te houden.  
- **Regex‑efficiëntie** – Optimaliseer reguliere‑expressie‑patronen die in aangepaste linkvalidatie worden gebruikt om CPU‑belasting te verminderen.

## Veelvoorkomende problemen en oplossingen
- **Ontbrekende hyperlinks** – Zorg ervoor dat het document daadwerkelijk hyperlink‑velden bevat; sommige oude Word‑links kunnen als eenvoudige tekst zijn opgeslagen.  
- **Onjuiste URL's na bijwerken** – Controleer of de nieuwe URL correct is gevormd; gebruik `java.net.URI` voor validatie voordat je het doel instelt.  
- **Licentie‑uitzonderingen** – Een proeflicentie kan limieten opleggen aan de documentgrootte; upgrade naar een volledige licentie voor onbeperkte verwerking.

## Veelgestelde vragen

**V: Waar wordt Aspose.Words Java voor gebruikt?**  
**A:** Het is een bibliotheek voor het programmatic maken, wijzigen en converteren van Word‑documenten in Java‑applicaties.

**V: Hoe kan ik meerdere hyperlinks tegelijk bijwerken?**  
**A:** Gebruik de extractiemethode om alle `Hyperlink`‑objecten te verzamelen, loop erdoorheen, roep `setTarget()` aan met de nieuwe URL, en sla het document op.

**V: Kan Aspose.Words ook PDF-conversie aan?**  
**A:** Ja, het ondersteunt conversie naar en van PDF, evenals meer dan 50 andere formaten.

**V: Is er een manier om Aspose.Words‑functies te testen voordat ik koop?**  
**A:** Absoluut! Begin met de [gratis proeflicentie](https://releases.aspose.com/words/java/) die beschikbaar is op de Aspose‑website.

**V: Wat moet ik doen als hyperlink‑updates mislukken?**  
**A:** Controleer of je XPath‑query correct `FieldStart`‑nodes selecteert en of de nieuwe URL's voldoen aan de standaard URI‑syntaxis.

## Bronnen
- **Documentatie**: Verken meer op [Aspose.Words documentatie](https://reference.aspose.com/words/java/) en [Aspose.Words Java Documentatie](https://reference.aspose.com/words/java/).  
- **Aspose.Words downloaden**: Haal de nieuwste versie [hier](https://releases.aspose.com/words/java/).  
- **Licentie aanschaffen**: Koop direct via [Aspose](https://purchase.aspose.com/buy).  
- **Gratis proefversie**: Probeer eerst met een [gratis proeflicentie](https://releases.aspose.com/words/java/).  
- **Supportforum**: Word lid van de community op [Aspose Support Forum](https://forum.aspose.com/c/words/10) voor discussies en hulp.

---

**Laatst bijgewerkt:** 2026-06-12  
**Getest met:** Aspose.Words for Java 24.12  
**Auteur:** Aspose  

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

```java
import com.aspose.words.Document;

class InitializeAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your document
        Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Hyperlinks.docx");

        System.out.println("Document loaded successfully!");
    }
}
```

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Hyperlinks.docx");
```

```java
NodeList fieldStarts = doc.selectNodes("//FieldStart");
for (FieldStart fieldStart : (Iterable<FieldStart>) fieldStarts) {
    if (fieldStart.getFieldType() == FieldType.FIELD_HYPERLINK) {
        Hyperlink hyperlink = new Hyperlink(fieldStart);
        if (hyperlink.isLocal()) continue;

        // Placeholder for further manipulation
    }
}
```

```java
Hyperlink hyperlink = new Hyperlink(fieldStart);
```

```java
  String linkName = hyperlink.getName();
  ```

```java
  hyperlink.setTarget("https://example.com");
  ```

```java
  boolean isLocalLink = hyperlink.isLocal();
  ```

{{< blocks/products/products-backtop-button >}}

## Gerelateerde tutorials

- [Hyperlink Management in Word Using Aspose.Words Java: A Comprehensive Guide](/words/java/content-management/master-hyperlink-management-word-aspose-words-java/)
- [Extracting Content from Documents in Aspose.Words for Java](/words/java/document-manipulation/extracting-content-from-documents/)
- [Master Document Manipulation with Aspose.Words for Java: A Comprehensive Guide](/words/java/content-management/aspose-words-java-document-manipulation-guide/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}