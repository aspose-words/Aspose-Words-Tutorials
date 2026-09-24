---
category: general
date: 2026-09-24
description: Leer hoe je een leeg Word‑document maakt in Java en vormen zoals rechthoeken
  en lijnen groepeert met Aspose.Words. Inclusief stapsgewijze code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: nl
lastmod: 2026-09-24
og_description: Maak een leeg Word‑document in Java en leer hoe je vormen groepeert,
  een rechthoekvorm toevoegt en de vormgrootte instelt met Aspose.Words.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Maak een leeg Word‑document en groepeer vormen in Java – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Hoe maak je een leeg Word‑document en groepeer je vormen in Java
url: /nl/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe maak je een leeg Word‑document en groepeer je vormen in Java

Als je een **leeg Word‑document wilt maken** en vervolgens meerdere tekenobjecten wilt organiseren, laat deze gids je precies zien hoe. Met Aspose.Words for Java kun je een groepsvorm invoegen, een rechthoekvorm toevoegen, een lijn tekenen en de grootte en positie van elke vorm regelen — allemaal in één uitvoerbaar programma.

Je doorloopt elke stap, van het initialiseren van het document tot het opslaan van de uiteindelijke `.docx`. Aan het einde begrijp je **hoe je vormen groepeert**, **een rechthoekvorm toevoegt** en **de vormgrootte instelt**, zodat je Word‑bestanden er precies uitzien zoals bedoeld.

## Vereisten

- Java 17 of later (de code compileert met elke recente JDK)
- Aspose.Words for Java‑bibliotheek (download van de [Aspose‑website](https://products.aspose.com/words/java))
- Een IDE of build‑tool (Maven/Gradle) die de Aspose.Words‑JAR aan het classpath kan toevoegen
- Basiskennis van Java‑syntaxis

> **Pro tip:** Gebruik Maven voor afhankelijkheidsbeheer; voeg `com.aspose:aspose-words:23.12` (of de nieuwste versie) toe aan je `pom.xml`.

## Stap 1: Maak een leeg Word‑document

De eerste taak is om een **leeg Word‑document te maken**. Dit geeft je een schoon canvas waarop je later vormen kunt invoegen.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Waarom dit belangrijk is:* Een `Document`‑object vertegenwoordigt het volledige `.docx`‑bestand. Beginnen met een leeg document zorgt ervoor dat er geen verborgen opmaak interfereert met de vormen die je gaat toevoegen.

## Stap 2: Voeg een groepsvorm in – de container voor meerdere objecten

Een **groepsvorm** werkt als een container waarmee je meerdere vormen tegelijk kunt verplaatsen, van grootte kunt wijzigen of roteren. Dit is de kern van **hoe je vormen groepeert** in Word.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Uitleg:* De `insertGroupShape`‑methode maakt een `GroupShape`‑object aan en plaatst het op de huidige cursorpositie. Alle daaropvolgende vormen die je `appendChild` aan deze groep toevoegt, worden behandeld als één enkele eenheid.

## Stap 3: Voeg een rechthoekvorm toe en stel de grootte in

Nu **voegen we een rechthoekvorm toe** aan de groep en **stellen we de vormgrootte** nauwkeurig in.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Waarom je de vormgrootte moet instellen:* Breedte en hoogte bepalen hoe de rechthoek op de pagina verschijnt. De `setLeft`‑ en `setTop`‑methoden positioneren de rechthoek relatief ten opzichte van de oorsprong van de groep, waardoor je pixel‑perfecte lay-outcontrole krijgt.

## Stap 4: Voeg een lijnvorm toe en configureer de afmetingen

Een lijn is een ander veelvoorkomend tekenobject. We zullen **logica vergelijkbaar met het toevoegen van een rechthoekvorm** toepassen op een lijn, om te laten zien dat dezelfde dimensioneringsprincipes gelden.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Belangrijk punt:* Hoewel een lijn geen hoogte heeft, gebruik je nog steeds `setWidth` om de lengte te definiëren. Positionering (`setLeft`, `setTop`) volgt hetzelfde coördinatensysteem als andere vormen.

## Stap 5: Sla het document op met gegroepeerde vormen

Sla tenslotte de wijzigingen op door het document op te slaan. Dit genereert een `.docx`‑bestand dat je in Microsoft Word kunt openen om het resultaat te verifiëren.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Verwacht resultaat:** Het openen van `GroupShapeDemo.docx` toont een lege pagina met een gegroepeerde rechthoek en lijn. Het selecteren van een van beide vormen selecteert de hele groep, waardoor je ze samen kunt verplaatsen.

## Veelgestelde vragen en afhandeling van randgevallen

| Vraag | Antwoord |
|----------|--------|
| *Kan ik meer dan twee vormen aan de groep toevoegen?* | Ja. Roep `group.appendChild(yourShape)` aan voor elke extra vorm. |
| *Wat als ik een andere eenheid (bijv. centimeters) voor de grootte nodig heb?* | Aspose.Words gebruikt punten (1 punt = 1/72 inch). Converteer met `Points = centimeters * 28.3465`. |
| *Behoudt de groep zijn lay-out wanneer het document op een andere computer wordt geopend?* | Absoluut. Alle grootte‑ en positiedata worden opgeslagen in het `.docx`‑bestand, waardoor de lay-out draagbaar is. |
| *Hoe kan ik later vormen degroeperen?* | Haal het `GroupShape`‑object op, loop vervolgens over `group.getChildNodes(NodeType.SHAPE, true)` en verplaats elk kind uit de groep. |
| *Wat als ik de hele groep wil roteren?* | Gebruik `group.setRotationAngle(double angleInDegrees)` vóór het opslaan. |

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑en‑plakken in je IDE. Het bevat alle benodigde imports en commentaren.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Voer het programma uit, open `GroupShapeDemo.docx` in Microsoft Word, en je zult de gegroepeerde vormen precies zien zoals beschreven.

## Conclusie

Je weet nu hoe je een **leeg Word‑document maakt**, **vormen groepeert in Word**, een **rechthoekvorm toevoegt**, en **de vormgrootte instelt** met Aspose.Words for Java. Door vormen in een `GroupShape` te plaatsen, krijg je volledige controle over collectieve positionering, schaling en rotatie — perfect voor diagrammen, stroomdiagrammen of aangepaste grafische elementen die in geautomatiseerde rapporten zijn ingebed.

**Volgende stappen:**  
- Verken **hoe je vormen groepeert** met complexere objecten zoals afbeeldingen of tekstvakken.  
- Experimenteer met `setRotationAngle` om de hele groep te roteren.  
- Combineer deze techniek met mail‑merge om gepersonaliseerde documenten te genereren die merk‑graphics bevatten.

Voel je vrij om de code aan te passen voor je eigen projecten, en deel je resultaten in de reacties!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Rechthoekvorm maken in Word met Java – Volledige gids](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Word‑document maken Java – Rechthoekvorm toevoegen met schaduweffect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Groepsvorm maken in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}