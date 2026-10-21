---
category: general
date: 2026-10-04
description: Leer hoe je een vorm in Word kunt verbergen met Java. Deze stapsgewijze
  handleiding laat zien hoe je een vorm in Word kunt verbergen, een vorm onzichtbaar
  maakt in Word, en een vorm in Microsoft Word programmeermatig kunt verbergen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- make shape invisible word
- hide shape microsoft word
language: nl
lastmod: 2026-10-04
og_description: Hoe je een vorm in Word verbergt met Java. Volg deze gids om een vorm
  in Word te verbergen, een vorm onzichtbaar te maken in Word, en een vorm in Microsoft
  Word te verbergen in een paar regels code.
og_image_alt: Screenshot showing a Word document with a hidden shape after applying
  the how to hide shape code
og_title: Hoe een vorm te verbergen in een Word‑document met Java – volledige gids
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to hide shape in Word with Java. This step‑by‑step guide
    shows you how to hide shape in Word, make shape invisible Word, and hide shape
    Microsoft Word programmatically.
  headline: How to hide shape in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Microsoft Word
- Document Automation
title: Hoe een vorm te verbergen in een Word‑document met Java
url: /nl/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een vorm te verbergen in een Word‑document met Java

Als je een vorm in een Word‑bestand moet verbergen, laat deze gids je precies zien **hoe je een vorm kunt verbergen** programmatically. Of je nu rapporten genereert, sjablonen opruimt, of documenten voorbereidt voor compliance, je kunt een vorm onzichtbaar maken zonder deze uit de bestandsstructuur te verwijderen.

In de onderstaande secties leer je hoe je een vorm in Word kunt verbergen, een vorm onzichtbaar maakt in Word, en een vorm verbergt in Microsoft Word met behulp van de Aspose.Words for Java‑bibliotheek. De tutorial gaat ervan uit dat je basiskennis van Java hebt en een werkende Java‑ontwikkelomgeving.

## Vereisten

* Java Development Kit (JDK) 8 of nieuwer  
* Maven of Gradle voor afhankelijkheidsbeheer  
* Aspose.Words for Java (versie 23.9 of later) – voeg de Maven‑coördinaat `com.aspose:aspose-words:23.9` toe  
* Een Word‑document (`input.docx`) dat minstens één vorm bevat (bijv. een afbeelding, tekstvak of SmartArt)

## Stap 1: Het project opzetten en Aspose.Words importeren

Maak een nieuw Maven‑project aan of voeg de Aspose.Words‑afhankelijkheid toe aan een bestaand project.

```xml
<!-- pom.xml snippet -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier> <!-- adjust classifier for your JDK -->
</dependency>
```

De bibliotheek levert de `Document`, `NodeType` en `Shape` klassen die in de volgende stappen worden gebruikt. Importeer ze bovenaan je Java‑bronbestand:

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;
```

## Stap 2: Het Word‑document laden

Het laden van het document is de eerste stap in elke Word‑verwerkingsworkflow. De `Document`‑constructor leest het bestand in het geheugen in, waarbij alle knooppunten, inclusief verborgen vormen, behouden blijven.

```java
// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Waarom dit belangrijk is*: Het laden van het bestand creëert een DOM (Document Object Model) waarmee je individuele knooppunten zoals vormen, alinea's of tabellen kunt navigeren, opvragen en wijzigen.

## Stap 3: De doelvorm ophalen

Als het document meerdere vormen bevat, kun je een specifieke vinden op basis van index, naam of andere criteria. Voor een snelle demonstratie haalt het voorbeeld de eerste vorm in de documenthiërarchie op, inclusief vormen die genest zijn in tabellen of groepen.

```java
// Retrieve the first shape (including descendants)
Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
```

*Waarom dit belangrijk is*: De `getChild`‑methode met `true` voor de `isDeep`‑vlag doorloopt de volledige knooppuntboom, zodat je vormen kunt vastleggen die geen directe kinderen van het documentlichaam zijn.

## Stap 4: De vorm verbergen

Door de `Hidden`‑eigenschap op `true` te zetten, vertel je Microsoft Word de vorm uit de lay-outweergave te verwijderen terwijl deze in de documentstructuur blijft. De vorm zal niet zichtbaar zijn wanneer het bestand in Word wordt geopend, maar blijft toegankelijk voor latere verwerking.

```java
// Hide the shape so it does not appear in the layout
shape.setHidden(true);
```

*Waarom dit belangrijk is*: Het verbergen van een vorm is handig wanneer je de vorm wilt behouden voor latere activering (bijv. conditionele inhoud, versiebeheer) zonder deze aan de eindgebruiker te tonen.

## Stap 5: Het gewijzigde document opslaan

Na het wijzigen van de zichtbaarheid van de vorm, schrijf je het document terug naar schijf. Je kunt het oorspronkelijke bestand overschrijven of een nieuw bestand maken; het voorbeeld schrijft naar `HiddenShape.docx`.

```java
// Save the document with the hidden shape
doc.save("YOUR_DIRECTORY/HiddenShape.docx");
```

Wanneer je `HiddenShape.docx` opent in Microsoft Word, zal de vorm onzichtbaar zijn, maar de lay-out van het document zal de verborgen status weergeven (geen extra witruimte).

## Volledig uitvoerbaar voorbeeld

Alle stappen samenvoegen levert een zelfstandig programma op dat je direct kunt compileren en uitvoeren.

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

/**
 * Demonstrates how to hide shape in a Word document using Aspose.Words for Java.
 */
public class HideShapeExample {
    public static void main(String[] args) {
        // Verify that the input path is provided
        if (args.length != 1) {
            System.out.println("Usage: java HideShapeExample <input-docx-path>");
            return;
        }

        String inputPath = args[0];
        String outputPath = "HiddenShape.docx";

        try {
            // Step 1: Load the Word document
            Document doc = new Document(inputPath);

            // Step 2: Retrieve the first shape (including descendants)
            Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
            if (shape == null) {
                System.out.println("No shape found in the document.");
                return;
            }

            // Step 3: Hide the shape
            shape.setHidden(true);

            // Step 4: Save the modified document
            doc.save(outputPath);
            System.out.println("Shape hidden successfully. Output saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error processing document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Verwacht resultaat**  
Het uitvoeren van het programma genereert `HiddenShape.docx`. Het openen van dat bestand in Microsoft Word toont de oorspronkelijke inhoud, maar de vorm die aanwezig was in `input.docx` is niet langer zichtbaar. De documentstructuur bevat nog steeds het vormknooppunt, dat later kan worden onthuld door `shape.setHidden(false)` in te stellen.

## Waarom een vorm verbergen in plaats van verwijderen?

* **Metadata behouden** – Vormen bevatten vaak alternatieve tekst, hyperlinks of aangepaste gegevens die je later nodig kunt hebben.  
* **Conditionele weergave** – In mail‑merge‑ of rapportgeneratiescenario's kun je de vorm alleen tonen aan specifieke ontvangers.  
* **Versiebeheer** – Een vorm verborgen houden stelt je in staat één sjabloon te behouden terwijl je de zichtbaarheid programmatically schakelt.

## Veelvoorkomende variaties en randgevallen

| Situatie | Aanbevolen aanpassing |
|-----------|------------------------|
| Meerdere vormen, een specifieke nodig | Gebruik `doc.getChild(NodeType.SHAPE, index, true)` met de juiste index, of itereren door `doc.getChildNodes(NodeType.SHAPE, true)` en matchen op `shape.getName()` of `shape.getAlternativeText()`. |
| Vorm bevindt zich binnen een GroupShape | De diepe zoekopdracht (`true`) bereikt al groepen, maar je moet mogelijk eerst casten naar `GroupShape` als je alleen een lid van de groep wilt verbergen. |
| Je wilt alle vormen verbergen | Loop over alle vormknooppunten en roep `setHidden(true)` aan binnen de lus. |
| Compatibiliteit met oudere Word‑versies | De `Hidden`‑vlag wordt ondersteund sinds Word 2000. Oudere formaten (`.doc`) respecteren deze ook, maar test op de doelformaat als je onverwachte lay-outwijzigingen tegenkomt. |

**Pro tip:** Na het verbergen van een vorm kun je `doc.updatePageLayout()` aanroepen als je wilt dat de paginalay-out opnieuw wordt berekend vóór het opslaan. Dit is zelden nodig omdat Word de inhoud automatisch opnieuw doorloopt bij openen, maar het kan nuttig zijn voor server‑side preview‑generatie.

## Het resultaat programmatically testen

Als je wilt bevestigen dat de vorm verborgen is zonder Word te openen, kun je de eigenschap na het opslaan opvragen:

```java
Document checkDoc = new Document(outputPath);
Shape hiddenShape = (Shape) checkDoc.getChild(NodeType.SHAPE, 0, true);
System.out.println("Shape hidden flag: " + hiddenShape.isHidden()); // prints true
```

## Volgende stappen

Nu je weet hoe je een vorm in Word kunt verbergen, overweeg deze gerelateerde onderwerpen:

* **Vorm verbergen in Word op basis van aangepaste voorwaarden** – Combineer de `Hidden`‑vlag met mail‑merge‑velden om de zichtbaarheid per ontvanger te schakelen.  
* **Vorm onzichtbaar maken in Word met VBA** – Voor automatisering op het apparaat kan dezelfde eigenschap via VBA worden ingesteld (`Shape.Visible = msoFalse`).  
* **Vorm verbergen in Microsoft Word in bulk** – Verwerk een map met documenten met een lus die dezelfde code op elk bestand toepast.  

Het verkennen van deze uitbreidingen vergroot je controle over Word‑documentautomatisering en houdt je gegenereerde bestanden schoon en professioneel.

--- 

*Deze tutorial volgt de Google Developer Documentation Style Guide, gebruikt de actieve vorm, de tweede‑persoonsperspectief, en biedt een volledige, citeerbare oplossing voor zowel zoekmachines als AI‑assistenten.*

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Rechthoekvorm maken in Word met Java – Volledige gids](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Schaduw toevoegen aan vorm in Word – Complete Aspose.Words‑gids](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Word‑document maken met Java – Rechthoekvorm toevoegen met schaduweffect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}