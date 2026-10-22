---
category: general
date: 2026-09-27
description: Maak een leeg Word‑document in Java en groepeer vormen met Aspose.Words.
  Leer hoe je de vormgrootte instelt, de vulkleur van de vorm instelt en een kind
  toevoegt aan de groep.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: nl
lastmod: 2026-09-27
og_description: Maak een leeg Word‑document in Java met Aspose.Words. Deze tutorial
  laat zien hoe je vormen groepeert in Word, de vormgrootte instelt, de vulkleur van
  de vorm instelt en een kind aan de groep toevoegt.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Maak een leeg Word‑document en groepeer vormen in Java – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Hoe een leeg Word‑document te maken en vormen te groeperen in Java
url: /nl/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een leeg Word‑document maken en vormen groeperen in Java

Als je **een leeg Word‑document** programmatically wilt **aanmaken**, laat deze gids je precies zien hoe je dat doet met Aspose.Words for Java. Je leert ook hoe je **vormen in Word groepeert**, de grootte van elke vorm instelt, een vulkleur toepast en **een kind toevoegt aan de groep** zodat de objecten zich als één geheel gedragen.

Werken met Word‑bestanden vanuit code bespaart handmatig opmaken en stelt je in staat om rapporten, contracten of marketingbrochures automatisch te genereren. Aan het einde van deze tutorial heb je een uitvoerbaar Java‑programma dat een `.docx`‑bestand produceert met een blauwe rechthoek en een afbeelding, beide gegroepeerd.

## Vereisten

Zorg ervoor dat je het volgende hebt:

- Java 17 (of een recente JDK) geïnstalleerd.
- Maven of Gradle om afhankelijkheden te beheren.
- Een Aspose.Words for Java‑licentie (de gratis evaluatieversie werkt voor testen).
- Een voorbeeld‑afbeeldingsbestand (bijv. `sample.jpg`) in een map die je vanuit de code kunt refereren.

> **Pro tip:** Plaats je afbeeldingsbestanden in een `resources`‑directory en laad ze met `ClassLoader.getResourceAsStream` om hard‑gecodeerde absolute paden te vermijden.

## Stap 1: Een leeg Word‑document maken en een GroupShape toevoegen

De eerste stap is het instantieren van een nieuw `Document`‑object, dat een leeg Word‑bestand voorstelt, en vervolgens een `GroupShape` in te voegen. De groep fungeert als container voor alle vormen die je later toevoegt.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Waarom dit belangrijk is:* Een `GroupShape` laat je meerdere vormen tegelijk verplaatsen, roteren of opmaken, wat essentieel is voor complexe lay‑outs zoals diagrammen of watermerken.

## Stap 2: Een rechthoek invoegen en **vormgrootte instellen**

Maak nu een rechthoek, definieer de afmetingen en voeg deze toe aan de groep. Dit demonstreert de **set shape size**‑bewerking.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Uitleg:* `setWidth` en `setHeight` bepalen de exacte grootte van de vorm in points (1 point = 1/72 inch). Pas deze waarden aan om aan je lay‑outvereisten te voldoen.

## Stap 3: **Vulkleur van de vorm** voor de rechthoek instellen

De achtergrond van de rechthoek wordt blauw ingesteld met `setFillColor`. Je kunt elke `java.awt.Color`‑constante gebruiken of een aangepaste RGB‑kleur maken.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Waarom het handig is:* Vulkleur helpt objecten visueel te onderscheiden, vooral wanneer je later het document exporteert naar PDF of afdrukt.

## Stap 4: Een afbeelding invoegen en **kind toevoegen aan de groep**

Voeg nu een afbeelding toe aan dezelfde `GroupShape`. De afbeelding wordt ingevoegd via `DocumentBuilder.insertImage` en vervolgens aan de groep toegevoegd zodat deze samen met de rechthoek beweegt.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Randgeval:* Als het afbeeldingspad onjuist is, gooit Aspose.Words een `FileNotFoundException`. Gebruik een relatief pad of laad de afbeelding vanuit resources om dit probleem te voorkomen.

## Stap 5: **Het document opslaan met de gegroepeerde vormen**

Schrijf tenslotte het document naar schijf. Het resulterende bestand bevat de rechthoek en de afbeelding gegroepeerd.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Verwachte output

- Een bestand met de naam `GroupShape.docx` verschijnt in de opgegeven map.
- Het openen van het bestand in Microsoft Word toont een lege pagina met een blauwe rechthoek en de gekozen afbeelding, beide geselecteerd als één object (je kunt ze samen verplaatsen of van grootte veranderen).

![maak leeg word document met gegroepeerde vormen](/images/grouped-shapes.png "maak leeg word document met gegroepeerde vormen")

*De bovenstaande schermafbeelding toont de uiteindelijke gegroepeerde vormen binnen het nieuw aangemaakte Word‑document.*

## Veelvoorkomende variaties en extra tips

| Situatie | Hoe je het aanpakt |
|-----------|--------------------|
| **Meerdere afbeeldingen** | Voeg elke afbeelding toe met `builder.insertImage` en roep `group.appendChild(picture)` aan voor elk van hen. |
| **Verschillende vormtypen** | Gebruik `ShapeType.OVAL`, `ShapeType.LINE`, enz., bij het construeren van het `Shape`‑object. |
| **Positie van de groep wijzigen** | Nadat alle kinderen zijn toegevoegd, stel `group.setLeft(x)` en `group.setTop(y)` in om de hele groep te verplaatsen. |
| **Exporteren naar PDF** | Roep `doc.save("output.pdf")` aan na het groeperen; de PDF behoudt de groepering. |
| **Licentie‑handhaving** | Als je de evaluatieversie gebruikt, verschijnt er een watermerk. Installeer een geldige licentie om dit te verwijderen. |

## Conclusie

Je weet nu hoe je een **leeg Word‑document** maakt, een **GroupShape** invoegt, **vormgrootte** instelt, **vulkleur** van een vorm bepaalt en **een kind toevoegt aan de groep** met Aspose.Words for Java. Dit patroon stelt je in staat om complexe, programmatische lay‑outs te bouwen die later in Word bewerkt of naar andere formaten geëxporteerd kunnen worden.

Verken vervolgens hoe je **vormen in Word groepeert** met tekstvakken, hyperlinks aan vormen toevoegt, of de generatie van meer‑pagina‑rapporten automatiseert. Dezelfde principes gelden — maak gewoon extra vormen, configureer hun eigenschappen en voeg ze toe aan dezelfde groep.

Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}