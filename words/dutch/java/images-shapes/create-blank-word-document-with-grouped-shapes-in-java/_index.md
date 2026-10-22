---
category: general
date: 2026-08-07
description: Maak een leeg Word‑document met gegroepeerde vormen in Java met Aspose.Words.
  Leer hoe je vormen groepeert, de grootte van een vorm instelt en vormen toevoegt
  aan Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: nl
lastmod: 2026-08-07
og_description: Maak een leeg Word‑document met gegroepeerde vormen in Java. Volg
  deze gids om de vormgrootte in te stellen, vormen toe te voegen aan Word en leer
  hoe je vormen groepeert.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Maak een leeg Word‑document met gegroepeerde vormen – Java‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Maak een leeg Word‑document met gegroepeerde vormen in Java
url: /nl/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word-document met gegroepeerde vormen in Java

Als je een **blank Word document** moet maken dat verschillende vormen bevat die als één eenheid zijn gerangschikt, laat deze tutorial je precies zien hoe. Je ziet een volledig, uitvoerbaar voorbeeld dat **hoe je vormen groepeert** objecten, hun afmetingen aanpast, en **vormen toevoegt aan Word** met Aspose.Words for Java.

De gids doorloopt elke stap—van projectconfiguratie tot het opslaan van het uiteindelijke .docx‑bestand—zodat je de code direct kunt kopiëren naar je eigen applicatie. Er zijn geen externe referenties nodig, en de oplossing werkt met Aspose.Words 23.9 of later.

## Vereisten

* Java 17 (of een ondersteunde JDK)
* Maven of Gradle voor afhankelijkheidsbeheer
* Een Aspose.Words for Java‑licentie (of een tijdelijke evaluatiesleutel)
* Een voorbeeld‑afbeeldingsbestand (bijv. `sample.jpg`) geplaatst in een bekende map

Als een van deze items ontbreekt, installeer deze dan eerst; de rest van de tutorial gaat ervan uit dat de omgeving klaar is.

## Stap 1: Voeg Aspose.Words toe aan je project

Voeg de Aspose.Words‑dependency toe aan je `pom.xml` (Maven) of `build.gradle` (Gradle). Deze bibliotheek levert de `Document`, `DocumentBuilder`, `GroupShape` en `Shape` klassen die later worden gebruikt.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Waarom dit belangrijk is:** Zonder de bibliotheek zijn geen van de Word‑processing API's beschikbaar, en kun je niet programmatically **create blank Word document** maken.

## Stap 2: Maak een leeg Word-document

De eerste concrete actie is het instantieren van een `Document`‑object, dat een **blank Word document** in het geheugen vertegenwoordigt.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* maakt een **blank Word document** met standaardinstellingen (A4‑pagina, standaardmarges). De bijbehorende `DocumentBuilder` stelt je in staat om inhoud in te voegen op de huidige cursorpositie.

## Stap 3: Voeg een groepsvorm in (hoe je vormen groepeert)

Een *group shape* fungeert als een container voor andere vormen. In deze stap leer je **hoe je vormen groepeert** objecten zodat ze samen bewegen.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

De `insertGroupShape`‑methode plaatst de container op de cursorlocatie van de builder. Groeperen is essentieel wanneer je meerdere tekeningen als één entiteit wilt behandelen—dit is de kern van de **group shapes word** functionaliteit.

## Stap 4: Maak een rechthoek en stel de grootte in

Voeg nu een rechthoek toe aan de groep. Dit toont **set shape size**, wat nodig is voor een precieze lay-out.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Waarom afmetingen instellen?* Het expliciet aanroepen van `setWidth` en `setHeight` garandeert dat de rechthoek precies verschijnt zoals bedoeld, ongeacht de standaardvormstijlen van het document.

## Stap 5: Voeg een afbeelding in en voeg deze toe aan de groep

Het toevoegen van een afbeelding toont een andere veelvoorkomende gebruikssituatie voor **add shapes to word**. De afbeelding wordt onderdeel van dezelfde groep en beweegt mee met de rechthoek.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

Als het afbeeldingsbestand ontbreekt, gooit Aspose.Words een uitzondering. Een praktische tip is om het pad vooraf te controleren:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## Stap 6: Sla het document op dat de gegroepeerde vormen bevat

Sla tenslotte het **blank Word document** (nu gevuld met een gegroepeerde vorm) op schijf op.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Wanneer je `GroupShapeDemo.docx` opent in Microsoft Word, zie je één gegroepeerd object dat een rechthoek en een afbeelding bevat. Het selecteren van een deel van de groep verplaatst de hele container, wat bevestigt dat de vormen correct **grouped** zijn.

### Verwachte output

* Een bestand genaamd `GroupShapeDemo.docx` in de opgegeven map.
* Het openen van het bestand toont een container van 300 × 200 punt met:
  * Een rechthoek van 100 × 50 punt gepositioneerd op (20, 20).
  * Een afbeelding gepositioneerd op (150, 30) binnen dezelfde container.

## Randgevallen en variaties

| Situatie | Hoe aan te pakken |
|-----------|-----------------|
| **Verschillende paginagrootte** | Roep `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` aan vóór het invoegen van de groep. |
| **Meerdere groepen** | Herhaal stappen 3‑5 met een nieuwe `GroupShape`‑instantie; elke groep kan onafhankelijk worden gepositioneerd. |
| **Vormen roteren** | Gebruik `shape.setRotationAngle(45.0);` om een rechthoek of afbeelding te roteren voordat je deze aan de groep toevoegt. |
| **Niet‑afbeeldingsvormen** | Maak `Shape`‑objecten van type `ShapeType.ELLIPSE`, `ShapeType.LINE`, enz., en voeg ze toe net als de rechthoek. |
| **Grote afbeeldingen** | Schaald de afbeelding met `picture.setWidth(80.0); picture.setHeight(60.0);` om de groep binnen de oorspronkelijke grenzen te houden. |

## Praktische tips uit ervaring

* **Pro tip:** Stel de `RelativeHorizontalPosition` en `RelativeVerticalPosition` van de groep in op `RelativeHorizontalPosition.PAGE` en `RelativeVerticalPosition.PAGE` als je wilt dat de groep verankerd blijft aan de pagina in plaats van aan de cursor.
* **Let op:** Het toevoegen van een vorm die de afmetingen van de groep overschrijdt; de vorm wordt in Word bijgesneden. Pas de groepsgrootte aan met `group.setWidth()` en `group.setHeight()`.
* **Prestatienota:** Als je veel documenten in een lus genereert, hergebruik dan een enkele `DocumentBuilder`‑instantie en roep `doc.clone()` aan om de overhead van objectcreatie te verminderen.

## Conclusie

Je weet nu hoe je een **create blank Word document** kunt maken dat een gegroepeerde verzameling vormen bevat met Aspose.Words for Java. De tutorial besloeg de volledige workflow: het instellen van de bibliotheek, het maken van het document, het invoegen van een groep, **set shape size**, **add shapes to word**, en het opslaan van het resultaat.

Vanaf hier kun je meer geavanceerde functies verkennen, zoals het groeperen van grafieken, het toepassen van stijlen op individuele vormen, of het exporteren van het document naar PDF. Elk van deze onderwerpen bouwt voort op dezelfde principes die in deze gids worden gedemonstreerd.

---

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Groepvorm maken in Word-document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Word-document maken Java – Rechthoekvorm toevoegen met schaduweffect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Vormen invoegen in Word-documenten met Aspose.Words voor .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}