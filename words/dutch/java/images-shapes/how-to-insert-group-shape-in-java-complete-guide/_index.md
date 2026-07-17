---
category: general
date: 2026-07-16
description: hoe een groepsvorm in Java invoegen met Aspose.Words – een rechthoekvorm
  toevoegen, vormafmetingen instellen, en een gekleurde rechthoek en cirkel maken
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: nl
lastmod: 2026-07-16
og_description: 'hoe een groepsvorm in Java in te voegen: een praktische gids om een
  rechthoekvorm toe te voegen, vormafmetingen in te stellen en gekleurde rechthoek
  en cirkel te maken met Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Groepsvorm invoegen in Java – Volledige Aspose.Words‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: Hoe een groepsvorm in Java in te voegen – Complete gids
url: /nl/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hoe een groepsvorm in Java in te voegen – Complete gids

Heb je je ooit afgevraagd **hoe je een groepsvorm** in een Word‑document kunt invoegen met Java? Je bent niet de enige. Of je nu een rapportgenerator of een dynamische flyer‑maker bouwt, het groeperen van vormen houdt je lay‑out netjes en je code beheersbaar.

In deze tutorial lopen we de exacte stappen door om **add rectangle shape**, **set shape dimensions**, en **create colored rectangle** en **create colored circle** te gebruiken met de Aspose.Words‑bibliotheek. Aan het einde heb je een uitvoerbaar programma dat een .docx‑bestand produceert met een blauwe rechthoek en een rode cirkel netjes verpakt binnen een groep.

## Vereisten

- Java 17 (of een recente JDK) geïnstalleerd en geconfigureerd.
- Maven of Gradle om afhankelijkheden te beheren.
- Aspose.Words for Java 23.9 of nieuwer – je kunt het ophalen van Maven Central.
- Een basisbegrip van Java‑syntaxis – niets ingewikkelds nodig.

Als je een van deze mist, haal dan de JDK van de Oracle‑site en voeg de Aspose.Words‑dependency toe aan je `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Nu de basis gelegd is, laten we de handen uit de mouwen steken.

## hoe een groepsvorm in te voegen – Overzicht

Het kernidee is simpel: maak een `Document`, open een `DocumentBuilder`, voeg een **group shape** in, en plaats vervolgens individuele vormen (een rechthoek en een cirkel) in die groep. De groep fungeert als een container, dus verplaats je deze later, verschuift alles erin – ideaal voor complexe lay‑outs.

Hieronder staat de volledige, kant‑klaar code. Voel je vrij om deze te kopiëren en plakken in een nieuwe Java‑klasse genaamd `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Pro tip:** De `setLeft`‑ en `setTop`‑waarden zijn relatief ten opzichte van de oorsprong van de groep, niet van de pagina. Dit maakt het later verplaatsen van de hele groep een fluitje van een cent.

### Wat is er net gebeurd?

1. **Document & Builder** – We maken een leeg Word‑bestand en een `DocumentBuilder` die ons in staat stelt inhoud in te voegen.
2. **Group Shape** – `builder.insertGroupShape()` maakt een container. Beschouw het als een map voor tekenobjecten.
3. **Blue Rectangle** – We maken een `Shape` van het type `RECTANGLE`, stellen de grootte en positie in, en vullen deze met blauw – dat is de **create colored rectangle** stap.
4. **Red Circle** – Zelfde patroon, maar met `ELLIPSE` voor een perfecte cirkel, vervolgens rood gevuld – dat is het **create colored circle** onderdeel.
5. **Saving** – Ten slotte slaan we alles op in `GroupShapeDemo.docx`.

Voer het programma uit (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) en open het resulterende bestand. Je zou een blauwe rechthoek aan de linkerkant en een rode cirkel aan de rechterkant moeten zien, beide vergrendeld binnen één groepsvak.

## Een rechthoekvorm toevoegen

Als je alleen een rechthoek nodig hebt zonder groeperen, kun je de `insertGroupShape()`‑aanroep overslaan en de rechthoek direct aan de body van het document toevoegen. Groeperen biedt echter de flexibiliteit om meerdere vormen in één keer te verplaatsen, roteren of verwijderen.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Let op hoe we hier de **add rectangle shape**‑logica hebben gebruikt. De rechthoek verschijnt op de pagina als een onafhankelijk object. In de meeste praktijksituaties wil je echter de groep, omdat die de relatieve positionering behoudt.

## Vormafmetingen instellen

Wanneer je methoden ziet zoals `setWidth` en `setHeight`, onthoud dan dat ze **points** (1/72 inch) accepteren. Als je millimeters verkiest, converteer dan eerst:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

Deze code laat **set shape dimensions** zien met een eenheidsconversie – handig wanneer je designspecificaties afkomstig zijn van een UI‑mockup die metrische eenheden gebruikt.

## Een gekleurde rechthoek maken

Een vorm kleuren is zo simpel als het aanroepen van `getFill().setForeColor()`. Je kunt elke `java.awt.Color` doorgeven. Wil je een verloop? Gebruik `setForeColor` voor de startkleur en `setBackColor` voor de eindkleur.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

Dat is een snelle manier om **create colored rectangle** te maken met een verloopvulling in plaats van een effen kleur.

## Een gekleurde cirkel maken

Cirkels zijn gewoon ellipsen met gelijke breedte en hoogte. Dezelfde kleurlogica is van toepassing:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

Als je een transparante vulling nodig hebt, stel dan het alfacanalen in:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Nu heb je de **create colored circle**‑techniek onder de knie.

## Het document opslaan

Aspose.Words stelt je in staat om naar veel formaten te exporteren: DOCX, PDF, HTML, PNG, wat je maar wilt. Voor deze demo blijven we bij DOCX omdat het de vectorvormen perfect behoudt.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

Het wijzigen van de `SaveFormat` is alles wat nodig is om een PDF‑versie van hetzelfde gegroepeerde kunstwerk te genereren.

## Veelvoorkomende valkuilen & hoe ze te vermijden

- **Vergeten de vorm aan de groep toe te voegen?** De vorm verschijnt op de pagina maar beweegt niet mee met de groep. Roep altijd `group.appendChild(yourShape)` aan.

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}