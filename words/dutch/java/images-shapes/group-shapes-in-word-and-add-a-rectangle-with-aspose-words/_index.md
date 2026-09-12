---
category: general
date: 2026-09-11
description: Groeperen van vormen in Word en een rechthoekvorm toevoegen met Aspose.Words
  voor Java. Leer hoe u de vormgrootte instelt, objecten groepeert en het document
  opslaat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: nl
lastmod: 2026-09-11
og_description: Groep vormen in Word en voeg een rechthoekvorm toe met Aspose.Words
  for Java. Deze tutorial laat zien hoe je de vormgrootte instelt, vormen groepeert
  en het document exporteert.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Vormen groeperen in Word – voeg een rechthoek toe met Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Groep vormen in Word en voeg een rechthoek toe met Aspose.Words
url: /nl/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Groepvormen in Word en voeg een rechthoek toe met Aspose.Words

Als je **vormen wilt groeperen in Word** terwijl je programmatically een rechthoek toevoegt, biedt deze gids een complete, kant‑klaar oplossing. Je ziet precies hoe je een groepsvorm invoegt, een rechthoekvorm toevoegt, de vormgrootte instelt en uiteindelijk het document opslaat zodat je het resultaat direct kunt bekijken.

Werken met Word‑documenten betekent vaak dat je meerdere objecten—afbeeldingen, grafieken of eenvoudige geometrische vormen—samenvouwt tot één logische eenheid. Het groeperen van die objecten maakt het makkelijker om ze samen te verplaatsen, te roteren of te stijlen. In deze tutorial behandelen we ook **hoe je een rechthoek toevoegt** en **hoe je de vormgrootte instelt** voor perfecte lay-outcontrole.

## Wat je leert

* Hoe je een nieuw Word‑document maakt met Aspose.Words for Java.  
* **Hoe je vormen groepeert** zodat ze zich als één object gedragen.  
* **Rechthoekvorm toevoegen** aan een groep en een afbeelding in dezelfde groep invoegen.  
* **Vormgrootte instellen** voor zowel de rechthoek als de afbeelding.  
* Het document opslaan en openen in Microsoft Word om het resultaat te verifiëren.

### Vereisten

* Java 17 of later geïnstalleerd.  
* Maven of Gradle om afhankelijkheden te beheren.  
* Een geldige Aspose.Words for Java‑licentie (of een gratis evaluatiesleutel).  
* Een afbeeldingsbestand (`sample.png`) geplaatst in een bekende map (vervang `YOUR_DIRECTORY` door je eigen pad).

---

## Hoe je vormen groepeert in Word met Aspose.Words

De eerste stap is het maken van een `Document` en een `DocumentBuilder`. De builder biedt een handige API om vormen, tekst en andere elementen in te voegen.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Waarom dit belangrijk is:** `DocumentBuilder` werkt direct met het onderliggende `Document`‑object, waardoor je vormen kunt invoegen zonder handmatig low‑level node‑collecties te beheren.

### Een groepsvorm toevoegen

Een groepsvorm is een container die andere vormen kan bevatten. Beschouw het als een map voor tekenobjecten.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

De methode `insertGroupShape()` maakt een `GroupShape`‑node aan en retourneert deze zodat je later kindvormen kunt toevoegen.  

---

## Een rechthoekvorm toevoegen aan de groep

Nu **voegen we een rechthoekvorm toe** aan de eerder gemaakte groep. De rechthoek dient als achtergrond of rand voor de afbeelding.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **Tip:** Het instellen van `FillColor` en `StrokeColor` maakt de rechthoek zichtbaar in het uiteindelijke document. Als je deze eigenschappen weglaat, kan de vorm transparant verschijnen.

### Hoe je een rechthoek toevoegt

De bovenstaande code laat **zien hoe je een rechthoek toevoegt** door een `Shape`‑instantie te maken met `ShapeType.RECTANGLE` en deze vervolgens toe te voegen aan de `GroupShape`. Dit patroon werkt voor elk ander vormtype (bijv. `ELLIPSE`, `POLYLINE`).

---

## Vormgrootte instellen voor rechthoek en afbeelding

Een juiste afmeting zorgt ervoor dat de rechthoek en de afbeelding correct uitgelijnd zijn. Hier **stellen we ook de vormgrootte in** voor de afbeelding die we vervolgens invoegen.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

Zowel de rechthoek als de afbeelding delen nu dezelfde afmetingen (100 × 50 points). Omdat ze tot dezelfde groep behoren, beïnvloedt het verplaatsen of roteren van de groep beide vormen tegelijk.

> **Waarom afmetingen gelijk maken?** Het afstemmen van de dimensies garandeert dat de afbeelding netjes binnen de rechthoek past, waardoor een nette “ingelijste afbeelding” ontstaat.

---

## Het document opslaan en het resultaat bekijken

Tot slot schrijven we het document naar schijf. Het openen van het bestand in Microsoft Word toont de gegroepeerde vormen als één selecteerbaar object.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Wanneer je `output.docx` opent, zie je een rechthoek met de afbeelding erin. Door op de vorm te klikken, worden zowel de rechthoek als de afbeelding geselecteerd omdat ze **gegroepeerd** zijn.

![group shapes in word example](https://example.com/images/group-shapes-word.png "group shapes in word example")

*Afbeeldings‑alt‑tekst:* *group shapes in word example* – een Word‑document dat een gegroepeerde rechthoek en afbeelding toont.

---

## Veelgestelde vragen en edge‑case handling

| Vraag | Antwoord |
|----------|--------|
| **Wat als ik een andere grootte voor de afbeelding nodig heb?** | Pas `picture.setWidth()` en `picture.setHeight()` aan na het invoegen. De rechthoek kan zijn oorspronkelijke grootte behouden, of je kunt deze ook aanpassen om overeen te komen. |
| **Kan ik meer vormen aan dezelfde groep toevoegen?** | Ja. Roep `group.appendChild(newShape)` aan voor elk extra `Shape`‑object. |
| **Hoe roteer ik de hele groep?** | Gebruik `group.setRotationAngle(double angleInRadians)`. De rotatie wordt toegepast op elke kindvorm. |
| **Wat als het afbeeldingsbestand ontbreekt?** | `insertImage` gooit een `FileNotFoundException`. Plaats de aanroep in een try‑catch‑blok en bied een fallback‑placeholder‑vorm aan. |
| **Is het later mogelijk om te degroeperen?** | Roep `group.removeAllChildren()` aan om kinderen los te koppelen, en voeg ze vervolgens individueel weer in het document in. |

---

## Conclusie

Je hebt nu een compleet, uitvoerbaar voorbeeld dat laat zien **hoe je vormen groepeert in Word**, **een rechthoekvorm toevoegt**, **de vormgrootte instelt**, en **het document opslaat** met Aspose.Words for Java. Door de rechthoek en de afbeelding te groeperen, kun je ze verplaatsen, van grootte wijzigen of roteren als één eenheid—exact wat veel document‑automatiseringsscenario's vereisen.

Vanaf hier kun je verder gaan met:

* Tekstvakken toevoegen aan dezelfde groep (`how to add rectangle`‑style tekst).  
* Verschillende vullingspatronen of verlopen toepassen (`set shape size` gecombineerd met styling).  
* Dezelfde techniek gebruiken om grafieken, tabellen of SmartArt te groeperen (`how to group shapes` over andere objecttypen).  

Voel je vrij om te experimenteren met andere vormtypen, kleuren en lay‑outopties. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}