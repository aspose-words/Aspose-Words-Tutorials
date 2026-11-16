---
category: general
date: 2026-11-15
description: Maak een rechthoekvorm in Word met Java en leer hoe je vormen aan Word
  kunt toevoegen, de afmetingen van de vorm kunt instellen en het Word‑document efficiënt
  kunt opslaan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: nl
lastmod: 2026-11-15
og_description: Maak een rechthoekvorm in een Word‑document met Java. Leer vormen
  aan Word toe te voegen, de afmetingen van de vorm in te stellen en het Word‑document
  binnen enkele minuten op te slaan.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Rechthoekvorm maken in Word met Java – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Maak een rechthoekvorm in een Word‑document met Java
url: /nl/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm maken in een Word‑document met Java

Als je een **rechthoekvorm** in een Word‑bestand moet **maken**, laat deze gids je precies zien hoe je dat doet met Java. Je ziet hoe je **vormen aan Word kunt toevoegen**, de **vormafmetingen kunt instellen**, en uiteindelijk het **Word‑document kunt opslaan** zonder je IDE te verlaten.

In de volgende secties krijg je een volledig, uitvoerbaar voorbeeld, een uitleg van elke regel, en tips voor veelvoorkomende valkuilen zoals afmetingsproblemen en documentcompatibiliteit. Er zijn geen externe referenties nodig—alleen de Aspose.Words for Java‑bibliotheek.

## Wat je zult leren

* Hoe je een `Document` en een `DocumentBuilder` initialiseert.
* Hoe je een **groepsvorm** invoegt en daarin een rechthoek plaatst.
* Hoe je **vormgrootte definieert** met `setWidth` en `setHeight`.
* Hoe je een **Word‑document opslaat** in het `.docx`‑formaat.
* Afhandeling van randgevallen voor verschillende paginagroottes en DPI‑instellingen.

### Vereisten

* Java 17 of hoger (de code compileert ook met Java 8).
* Aspose.Words for Java 23.10 of nieuwer – te verkrijgen via Maven Central.
* Een basisbegrip van Java‑syntaxis en object‑georiënteerde concepten.

> **Pro tip:** Als je later meer vormen wilt toevoegen (bijv. cirkels of tekstvakken), houd ze dan binnen dezelfde `GroupShape`. Dit maakt het verplaatsen, roteren of opmaken van de hele collectie veel eenvoudiger.

## Stap 1: Initialiseer het document en de builder

De eerste stap is een leeg Word‑bestand maken en een `DocumentBuilder` die je in staat stelt inhoud te schrijven.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Waarom dit belangrijk is:* Een `Document` vertegenwoordigt het volledige bestand, terwijl `DocumentBuilder` hoog‑niveau methoden biedt voor het invoegen van tekst, tabellen en **vormen**. Zonder de builder zou je laag‑niveau knooppunten handmatig moeten manipuleren.

## Stap 2: Voeg een groepsvorm toe om meerdere vormen vast te houden

Een **groepsvorm** werkt als een container; je kunt verschillende vormen toevoegen en ze later als één object behandelen (bijv. samen verplaatsen of roteren).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Waarom een groepsvorm gebruiken?* Als je later pijlen, cirkels of labels rond de rechthoek wilt toevoegen, houdt de groep alles uitgelijnd. Het vereenvoudigt bovendien de **add shapes to Word**‑workflow omdat je slechts één aanroep van `appendChild` nodig hebt voor elke nieuwe vorm.

## Stap 3: Maak de rechthoekvorm

Nu maken we de daadwerkelijke rechthoek die binnen de groep zal staan. De `Shape`‑constructor heeft het eigenaar‑`Document` en het type vorm dat je wilt nodig.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Waarom een rechthoek?* `ShapeType.RECTANGLE` is de meest voorkomende primitive voor het markeren van secties, het maken van placeholders, of het tekenen van eenvoudige UI‑mock‑ups direct in Word.

## Stap 4: Definieer de grootte van de rechthoek

Het instellen van de afmetingen is waar **set shape dimensions** belangrijk wordt. Je kunt elke meeteenheid gebruiken die door Aspose.Words wordt ondersteund; de standaard is points (1 pt = 1/72 inch).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Opmerking:** Als je millimeters verkiest, roep dan `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` aan waar `1.39 in ≈ 35 mm`. Dit toont de flexibiliteit van **define shape size**.

## Stap 5: Voeg de rechthoek toe aan de groepsvorm

Door de rechthoek toe te voegen aan de eerder gemaakte groep, verschijnt hij in het document.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

Op dit moment staat de rechthoek in de linkerbovenhoek van de groep. Je kunt hem later verplaatsen met `rectangle.setLeft(...)` en `rectangle.setTop(...)` als je een precieze plaatsing nodig hebt.

## Stap 6: (Optioneel) Sla het document op om het resultaat te zien

Tot slot schrijf je het document naar schijf. Dit is de **save Word document**‑stap die een `.docx`‑bestand produceert dat je kunt openen in Microsoft Word, LibreOffice of Google Docs.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

Het uitvoeren van het programma maakt `RectangleShapeDemo.docx` aan met een enkele rechthoek binnen een groepsvorm. Het openen van het bestand toont een eenvoudige witte rechthoek—exact de grootte die je hebt gedefinieerd.

### Verwachte output

* Een Word‑bestand met de naam `RectangleShapeDemo.docx`.
* In de eerste alinea een groepsvorm die een rechthoek van 100 pt × 50 pt bevat.
* Er wordt geen tekst toegevoegd, dus de rechthoek verschijnt op een lege pagina.

## Veelvoorkomende variaties en randgevallen

| Situatie | Hoe de code aan te passen |
|-----------|---------------------------|
| **Andere paginagrootte** (bijv. A4) | Roep `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` aan vóór het invoegen van de vorm. |
| **Hogere DPI voor afdrukken** | Vermenigvuldig breedte/hoogte met de gewenste DPI‑factor, bv. `rectangle.setWidth(200 * 2);` voor dubbele resolutie. |
| **Een tekstlabel toevoegen binnen de rechthoek** | Maak een `Shape` van type `TEXT_BOX`, stel `setWidth`/`setHeight` gelijk aan de rechthoek, en voeg deze toe aan dezelfde `GroupShape`. |
| **De rechthoek roteren** | Gebruik `rectangle.setRotationAngle(45);` om 45 graden met de klok mee te draaien. |
| **Opslaan als PDF in plaats van DOCX** | Vervang `document.save("output.docx");` door `document.save("output.pdf");` – dezelfde API werkt voor PDF en behoudt de rechthoek. |

## Pro tips voor een robuuste implementatie

1. **Hergebruik de builder** – na het invoegen van de groepsvorm kun je blijven paragrafen of tabellen toevoegen zonder een nieuwe builder‑instantie te maken.
2. **Resources vrijgeven** – hoewel de Java‑garbage‑collector de meeste objecten afhandelt, voorkomt een expliciete aanroep van `document.close();` (bij gebruik van streams) lekken van bestands‑handles.
3. **Afmetingen valideren** – controleer vóór het aanroepen van `setWidth`/`setHeight` of de waarden positief zijn; negatieve waarden veroorzaken een `IllegalArgumentException`.
4. **Versie‑compatibiliteit** – de code werkt met Aspose.Words 23.x en later. Oudere versies kunnen `Shape.setSize(width, height)` vereisen in plaats van afzonderlijke setters.

## Volledig, uitvoerbaar voorbeeld

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Resultaatverificatie:** Open `output/RectangleShapeDemo.docx` in Microsoft Word. Je zou een rechthoek van de opgegeven grootte moeten zien, gecentreerd bovenaan de eerste pagina. Als de rechthoek te klein lijkt, pas dan de waarden die aan `setWidth` en `setHeight` worden doorgegeven aan.

## Conclusie

Je weet nu hoe je een **rechthoekvorm** in een Word‑bestand maakt met Java, hoe je **vormen aan Word kunt toevoegen** via een `GroupShape`, hoe je **vormafmetingen** instelt en **vormgrootte definieert**, en uiteindelijk hoe je het **Word‑document opslaat** voor verdere distributie. Hetzelfde patroon werkt voor andere vormtypen, zodat je programmatisch complexe diagrammen kunt bouwen.

### Wat is het volgende?

* Verken **add shapes to Word** door cirkels, pijlen of tekstvakken in te voegen.
* Combineer meerdere vormen tot één `GroupShape` en pas transformaties toe (roteren, spiegelen).
* Genereer rapporten die grafieken als vormen insluiten en **save Word document** vervolgens als PDF voor deling.

Voel je vrij om te experimenteren met de afmetingen, kleuren en positionering om aan jouw specifieke scenario te voldoen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Create word document java – hide shape and set fill color](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}