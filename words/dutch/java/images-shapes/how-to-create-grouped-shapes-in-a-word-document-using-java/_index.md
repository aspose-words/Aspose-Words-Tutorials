---
category: general
date: 2026-10-13
description: Leer hoe je gegroepeerde vormen in Word maakt met Java. Deze gids laat
  zien hoe je een groepsvorm invoegt, een lijn aan de groep toevoegt en meerdere vormen
  door het hele document groepeert.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: nl
lastmod: 2026-10-13
og_description: Maak gegroepeerde vormen in Word met Java. Volg deze volledige tutorial
  om een groepsvorm in te voegen, een lijn aan de groep toe te voegen en meerdere
  vormen in Word‑documenten te groeperen.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Gegroepeerde vormen maken in Word met Java – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Hoe maak je gegroepeerde vormen in een Word‑document met Java
url: /nl/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe gegroepeerde vormen te maken in een Word-document met Java

Als je **gegroepeerde vormen** moet maken in een Microsoft Word‑bestand vanuit Java, leidt deze tutorial je door het hele proces. Je ziet hoe je **insert group shape** gebruikt, een rechthoek en een lijn in dezelfde container plaatst, en uiteindelijk het document opslaat met de gegroepeerde grafische elementen.

Het groeperen van vormen maakt het eenvoudig om meerdere tekenobjecten als één eenheid te verplaatsen, van grootte te wijzigen of op te maken—perfect voor diagrammen, stroomdiagrammen of aangepaste paginadecoraties. Aan het einde van deze gids kun je **add line to group**, **group multiple shapes word** documenten, en dezelfde techniek hergebruiken voor een willekeurig aantal vormen.

## Vereisten

- Java 17 of hoger geïnstalleerd op je ontwikkelmachine.  
- Een Aspose.Words for Java‑licentie (of een gratis evaluatie).  
- Een Maven‑ of Gradle‑project waarin je de Aspose.Words‑dependency kunt toevoegen:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

Er zijn geen extra bibliotheken nodig.

## Stap 1: De group shape‑container invoegen

De eerste stap is om **insert group shape** in het document te plaatsen. Deze container zal elke volgende vorm bevatten.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` maakt een leeg `Shape`‑object van het type `GROUPSHAPE`. Beschouw het als een transparant canvas dat andere tekenobjecten kan bevatten.

## Stap 2: Een rechthoek aan de groep toevoegen

Een rechthoek dient vaak als visuele achtergrond voor een groep vormen.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

Door `Left` en `Top` op `0` te zetten, wordt de rechthoek gepositioneerd in de linkerbovenhoek van de groep. Je kunt deze waarden aanpassen om de vorm binnen de groep te verschuiven.

## Stap 3: **Add line to group** – een lijnvorm maken

Nu **add line to group**. De lijn verschijnt onder de rechthoek.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

De `Top`‑eigenschap verplaatst de lijn 60 points onder de rechthoek, waardoor een eenvoudige gestapelde lay-out ontstaat. Je kunt ook `Left` instellen als je een horizontale verschuiving nodig hebt.

## Stap 4: Het document opslaan met de gegroepeerde vormen

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Wanneer je `GroupShapeDemo.docx` opent in Microsoft Word, zie je één groep die zowel de rechthoek als de lijn bevat. Het selecteren van de groep laat je beide vormen samen verplaatsen, wat aantoont dat je succesvol **group multiple shapes word** hebt uitgevoerd.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma met alle imports en foutafhandeling. Kopieer het naar je IDE, vervang `YOUR_DIRECTORY` door een bestaand mappad, en voer het uit.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Verwachte output

- Een bestand genaamd `GroupShapeDemo.docx` verschijnt in de doelmap.  
- Het openen van het bestand in Word toont één gegroepeerd object met een rechthoek bovenaan en een lijn eronder.  
- Het slepen van de groep verplaatst beide vormen samen, wat bevestigt dat je **created grouped shapes** succesvol hebt gemaakt.

## Tips en veelvoorkomende valkuilen

- **Pro tip:** Als je individuele vormen binnen de groep moet roteren of opmaken, roep dan de respectieve setters (`setRotation`, `getFill().setForeColor`, etc.) aan voordat je ze aan de groep toevoegt. De groep behoudt die visuele eigenschappen.
- **Let op:** Het vergeten om de `Top`‑eigenschap voor de lijn in te stellen kan ervoor zorgen dat deze overlapt met de rechthoek, waardoor de groep er rommelig uitziet.
- **Randgeval:** Wanneer je meer dan twee vormen toevoegt, onthoud dan dat de coördinaten van elk kind relatief zijn ten opzichte van de oorsprong (0,0) van de groep. Plan de lay-out dienovereenkomstig.
- **Prestatie‑opmerking:** Het groeperen van een groot aantal vormen (honderden) kan de bestandsgrootte iets vergroten, maar het vereenvoudigt later bewerken in Word.

## Hoe **group multiple shapes word** documenten programmatically

Het patroon hierboven—een groepscontainer maken, elke kindvorm configureren en toevoegen—werkt voor elk aantal vormen: cirkels, afbeeldingen, tekstvakken, enz. Herhaal eenvoudig de stappen “create shape → set properties → append” voordat je `doc.save()` aanroept.

Als je **add line to group** moet uitvoeren nadat de groep al andere vormen bevat, kun je de bestaande groep ophalen met:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

Dit toont aan dat je een groep op elk moment in de levenscyclus van het document kunt aanpassen.

## Conclusie

Je weet nu hoe je **create grouped shapes** kunt maken in een Word‑document met Java en Aspose.Words. Door **inserting group shape**, **adding line to group**, en **group multiple shapes word** kun je complexe tekeningen bouwen die zich gedragen als één object—ideaal voor diagrammen, sjablonen en geautomatiseerde rapportgeneratie.

Bekijk vervolgens deze gerelateerde onderwerpen:

- **Applying styles to grouped shapes** – leer hoe je vulkleuren, randen en effecten voor alle kinderen in één keer kunt instellen.  
- **Exporting grouped shapes to PDF** – zie hoe dezelfde groep behouden blijft bij het converteren van het document.  
- **Animating shapes with VBA** – combineer Java‑gegenereerde groepen met Word‑macro's voor interactieve documenten.

Voel je vrij om te experimenteren met verschillende vormtypen, -groottes en -posities. Groeperen geeft je de flexibiliteit om veel objecten als één te behandelen, waardoor zowel code als gebruikersinteractie wordt vereenvoudigd. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Word-document maken met Java – Rechthoekvorm toevoegen met schaduweffect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Rechthoekvorm maken in Word met Java – volledige gids](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Groepsvorm maken in Word-document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}