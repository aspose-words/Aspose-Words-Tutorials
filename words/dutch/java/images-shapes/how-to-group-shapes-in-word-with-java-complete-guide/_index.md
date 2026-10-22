---
category: general
date: 2026-10-16
description: Leer hoe je vormen groepeert in Word met Java. Deze tutorial laat zien
  hoe je een rechthoekvorm toevoegt, de grootte en afmetingen van de vorm instelt
  en het document opslaat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: nl
lastmod: 2026-10-16
og_description: Groepeer vormen in Word met Java. Voeg een rechthoekvorm toe, stel
  de grootte en afmetingen van de vorm in, en maak professionele documenten via code.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Vormen groeperen in Word met Java – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Hoe vormen groeperen in Word met Java – volledige gids
url: /nl/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe vormen groeperen in Word met Java – volledige gids

Als je **vormen in Word** programmatisch moet **groeperen**, biedt deze tutorial een kant‑klaar werkende oplossing. Je ziet hoe je een **rechthoekige vorm toevoegt**, de grootte aanpast, vormafmetingen instelt en uiteindelijk een DOCX‑bestand opslaat dat een gegroepeerde rechthoek en een ellips bevat.

Vormen groeperen in Word is handig voor het bouwen van complexe diagrammen, het maken van herbruikbare grafische componenten, of simpelweg om gerelateerde objecten bij elkaar te houden wanneer het document later wordt bewerkt. De code maakt gebruik van de Aspose.Words for Java‑bibliotheek, die werkt met elke recente JDK en geen Microsoft Word vereist.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

| Vereiste | Reden |
|----------|-------|
| Java 17 (of later) | De bibliotheek richt zich op moderne Java‑runtime‑omgevingen. |
| Aspose.Words for Java (nieuwste versie) | Biedt de `Document`, `DocumentBuilder`, `GroupShape` en `Shape`‑klassen die in het voorbeeld worden gebruikt. |
| Een IDE of build‑tool (Maven/Gradle) | Om het voorbeeld te compileren en uit te voeren. |
| Basiskennis van Java‑syntaxis | Nodig om de code‑stroom te begrijpen. |

Voeg de Aspose.Words‑dependency toe aan je project. Voor Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

Of voor Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## Overzicht van de oplossing

De tutorial volgt een duidelijk **probleem → oplossing → uitleg**‑patroon:

1. **Maak een nieuw Word‑document** en verkrijg een `DocumentBuilder`.  
2. **Voeg een `GroupShape`‑container toe** die meerdere vormen zal bevatten.  
3. **Voeg een rechthoek toe**, stel de breedte/hoogte in (de **set shape size**‑stap), en koppel deze aan de groep.  
4. **Voeg een ellips toe**, positioneer deze binnen dezelfde groep, en stel ook de afmetingen in.  
5. **Sla** het document op schijf.

Elke stap bevat het **waarom** achter de code, zodat je begrijpt wat de API doet en hoe je deze kunt aanpassen voor andere scenario's.

## Stap 1: Maak het document en een DocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Waarom dit belangrijk is:** `Document` vertegenwoordigt het volledige DOCX‑bestand, terwijl `DocumentBuilder` een helper is die je inhoud laat invoegen zonder low‑level node‑beheer. Ze eerst aanmaken geeft je een schoon canvas voor alle volgende vorm‑bewerkingen.

## Stap 2: Voeg een GroupShape‑container toe

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

Een `GroupShape` werkt als een **map** voor tekenobjecten. Wanneer je de groep verplaatst, roteert of verwijdert, volgen alle onderliggende vormen automatisch. Dit is de kern van **group shapes in word**.

## Stap 3: Voeg een rechthoekige vorm toe – de rectangle shape code

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – De `Shape`‑constructor ontvangt `ShapeType.RECTANGLE`, wat Aspose.Words vertelt een rechthoekige omtrek te renderen.  
- **set shape size** – `setWidth` en `setHeight` definiëren de **shape dimensions** in points (1 pt = 1/72 in). Dit is de meest gebruikelijke manier om de visuele grootte te bepalen.  
- **Why we use `appendChild`** – Het koppelt de rechthoek aan de `GroupShape` zodat hij samen met de groep beweegt.

## Stap 4: Voeg een ellips toe en positioneer deze binnen de groep

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

De ellips demonstreert **set shape dimensions** buiten een eenvoudige rechthoek. Door `setLeft` aan te roepen, beheer je de horizontale offset binnen de groep, wat handig is bij het rangschikken van meerdere objecten.

## Stap 5: Sla het document op

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Wanneer je *GroupShapeDemo.docx* opent in Microsoft Word, zie je een rechthoek en een ellips die samen in één groep zijn vergrendeld. Het selecteren van één van de vormen selecteert de hele groep — precies wat je verwacht bij **group shapes in word**.

## Volledig, uitvoerbaar voorbeeld

Alle onderdelen samengevoegd, hier is het complete bronbestand dat je in je IDE kunt plakken:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### Verwachte output

- Een bestand met de naam **GroupShapeDemo.docx** verschijnt in de projectmap.  
- Het openen van het bestand in Word toont twee vormen (een rechthoek en een ellips) die gegroepeerd zijn.  
- Het slepen van één van de vormen verplaatst de hele groep, wat bevestigt dat **group shapes in word** werkt zoals bedoeld.

## Veelvoorkomende variaties en randgevallen

| Scenario | Wat te wijzigen | Waarom |
|----------|----------------|--------|
| **Andere vormtypen** (bijv. driehoek) | Gebruik `ShapeType.TRIANGLE` of een andere enum‑waarde bij het construeren van `Shape`. | Hiermee kun je complexere diagrammen bouwen. |
| **Vulkleur instellen** | Roep `shape.getFillColor().setColor(Color.BLUE);` aan na het aanmaken van de vorm. | Verbetert het uiterlijk zonder de groepering te beïnvloeden. |
| **Groep roteren** | `groupShape.setRotationAngle(45);` | Roteert alle onderliggende vormen tegelijk, handig voor iconen. |
| **Tekst in een vorm plaatsen** | `shape.appendChild(new Paragraph(document));` en voeg daarna een `Run` met tekst toe. | Laat de vorm fungeren als label of bijschrift. |
| **Opslaan naar een stream** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Handig voor webservices die het document direct retourneren. |

### Pro‑tip

Wanneer je **set shape dimensions** moet baseren op dynamische data (bijv. een barcode‑lengte), bereken dan eerst de breedte/hoogte in points:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

Dit voorkomt hard‑gecodeerde waarden en houdt je code flexibel.

## Conclusie

Je weet nu hoe je **group shapes in Word** kunt gebruiken met Java, hoe je **add rectangle shape** toevoegt, en hoe je **set shape size** en **set shape dimensions** instelt met beknopte, productie‑klare code. Door de bovenstaande stappen te volgen, kun je herbruikbare grafische groepen maken, ze in geautomatiseerde rapporten embedden, of aangepaste diagramtools bouwen zonder ooit Word handmatig te openen.

### Wat is de volgende stap?

- Verken variaties op **add rectangle shape**, zoals afgeronde hoeken (`ShapeType.RECTANGLE` met `setCornerRadius`).  
- Combineer **group shapes in word** met tabellen of grafieken voor rijkere documenten.  
- Bekijk de Aspose.Words‑API voor **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) om te bepalen hoe omringende tekst met je gegroepeerde graphics omgaat.

Voel je vrij om te experimenteren, de **rectangle shape code** aan te passen, en je resultaten te delen.


## Wat moet je hierna leren?


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}