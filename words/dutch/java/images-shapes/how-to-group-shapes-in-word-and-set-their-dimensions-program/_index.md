---
category: general
date: 2026-11-25
description: Hoe vormen te groeperen in Word met Java en hoe de afmetingen van vormen
  in te stellen in een DOCX‑bestand met Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: nl
lastmod: 2026-11-25
og_description: Hoe shapes in Word te groeperen met de Aspose.Words Java API en de
  grootte van een shape snel in te stellen. Volg de volledige stap‑voor‑stap oplossing.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Hoe vormen in Word groeperen en hun afmetingen instellen – Java-gids
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Hoe vormen in Word te groeperen en hun afmetingen via code in te stellen
url: /nl/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe vormen groeperen in Word en hun afmetingen programmatisch instellen

Als je **how to group shapes in Word** moet en hun exacte grootte wilt controleren, laat deze gids je een complete, uitvoerbare oplossing zien. Met Aspose.Words for Java kun je een rechthoek, een ellips maken, ze toevoegen aan een `GroupShape`, en vervolgens **how to set shape dimensions** zoals breedte en hoogte in één DOCX‑bestand.

U leert hoe u:

* Een nieuw Word‑document vanaf nul maken.  
* Een `GroupShape` invoegen (nieuwe API in versie 24.9).  
* Een rechthoek en een ellips aan de groep toevoegen.  
* **Set shape size Word** nauwkeurig instellen met `setWidth` en `setHeight`.  
* Het document opslaan op schijf.

Er is geen externe tooling vereist—alleen Java 17+, Maven en de Aspose.Words for Java‑bibliotheek.

## Vereisten

* Java Development Kit 17 of nieuwer.  
* Maven (of Gradle) voor afhankelijkheidsbeheer.  
* Aspose.Words for Java 24.9 of later (de `GroupShape`‑API werd geïntroduceerd in 24.9).  
* Basiskennis van Java‑syntaxis en object‑georiënteerde concepten.

Als je Aspose.Words nog niet aan je project hebt toegevoegd, voeg dan de volgende Maven‑afhankelijkheid toe:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Stap 1: Een nieuw document en een DocumentBuilder maken

De `Document`‑klasse vertegenwoordigt het volledige Word‑bestand, terwijl `DocumentBuilder` een handige manier biedt om inhoud toe te voegen.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Waarom deze stap?*  
Een nieuw `Document` geeft je een schoon canvas. `DocumentBuilder` is de high‑level helper waarmee je alinea’s, tabellen en, in dit geval, vormen kunt invoegen.

## Stap 2: Een GroupShape invoegen (nieuwe API in versie 24.9)

Een `GroupShape` werkt als een container; elke vorm die je toevoegt, wordt onderdeel van dezelfde visuele groep.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Waarom `GroupShape` gebruiken?*  
Vormen groeperen vereenvoudigt het verplaatsen, roteren of toepassen van opmaak op meerdere objecten tegelijk. De API werd toegevoegd in 24.9, dus oudere versies zullen deze regel niet compileren.

## Stap 3: Een rechthoek maken, de grootte instellen en toevoegen aan de groep

Hier demonstreren we **how to set shape dimensions** voor een rechthoek.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Waarom breedte en hoogte expliciet instellen?*  
Word slaat de vormgrootte op in points. Door `setWidth` en `setHeight` aan te roepen, beheer je de exacte visuele afmeting, wat essentieel is wanneer je een precieze lay-out nodig hebt of bij export naar PDF.

## Stap 4: Een ellips maken, de grootte instellen en toevoegen aan dezelfde groep

Dezelfde **set shape size word**‑techniek werkt voor elk type vorm.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Waarom de ellips aan dezelfde `GroupShape` toevoegen?*  
Beide vormen bewegen samen als één eenheid. Dit is handig voor het maken van iconen, logo’s of complexe diagrammen die uitgelijnd moeten blijven.

## Stap 5: Het document opslaan met de gegroepeerde vormen

Ten slotte persisteer je het DOCX‑bestand op schijf.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

Het uitvoeren van dit programma levert een bestand genaamd **GroupShape.docx** op dat een rechthoek en een ellips bevat die gegroepeerd zijn. Wanneer je het bestand opent in Microsoft Word, zie je dat de twee vormen zich gedragen als één object—je kunt ze samen slepen, van grootte veranderen of roteren.

### Verwachte output

* Een Word‑document (`GroupShape.docx`) met één pagina.  
* Een `GroupShape` met een rechthoek van 100 × 50 pt en een ellips van 80 × 80 pt.  
* Het selecteren van één vorm selecteert de hele groep.

## Veelgestelde vragen en randgevallen

### Hoe de positie van de gegroepeerde vormen wijzigen?

Nadat je de `GroupShape` hebt gemaakt, kun je de eigenschappen `left` en `top` instellen:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

Deze coördinaten worden ook gemeten in points.

### Wat als ik meer dan twee vormen wil toevoegen?

`GroupShape` werkt als elk ander container‑knooppunt. Roep `groupShape.appendChild(yourShape)` aan voor elke extra vorm. De API beperkt het aantal kinderen niet.

### Kan ik stijl (vulkleur, lijndikte) toepassen op individuele vormen?

Ja. Elk `Shape`‑object biedt opmaak‑eigenschappen:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Werkt de code met oudere Aspose.Words‑versies?

De `insertGroupShape`‑methode werd geïntroduceerd in versie 24.9. Als je een eerdere versie gebruikt, moet je een `GroupShape` handmatig via de knoopboom maken, wat ingewikkelder is. Upgraden wordt aanbevolen.

## Pro‑tips

* **Gebruik points voor consistentie** – de interne eenheid van Word is de point (1/72 inch). Omrekenen van pixels of centimeters kan onverwachte afmetingen opleveren.  
* **Groeperen vóór positioneren** – positioneer de `GroupShape` nadat je alle kinderen hebt toegevoegd; anders moet je mogelijk offsets opnieuw berekenen.  
* **Herbruik de DocumentBuilder** – je kunt meerdere groepen in hetzelfde document invoegen door de cursor van de builder (`builder.moveTo`) te verplaatsen vóór elke `insertGroupShape`‑aanroep.

## Conclusie

Je hebt nu een volledig, end‑to‑end voorbeeld van **how to group shapes in Word** en **how to set shape dimensions** met Aspose.Words for Java. De tutorial behandelde het maken van een document, het invoegen van een `GroupShape`, het toevoegen van een rechthoek en een ellips, het exact instellen van hun grootte, en het opslaan van het resultaat.  

Vanaf hier kun je verder gaan met:

* Tekstvakken of afbeeldingen aan dezelfde groep toevoegen.  
* Gegroepeerde vormen animeren met de smart‑art‑functies van Word (via de API).  
* De gegroepeerde vormen exporteren naar PDF of SVG voor webgebruik.

Voel je vrij om te experimenteren met verschillende vormtypen, afmetingen en posities—groeperen geeft je krachtige controle over complexe lay-outs in Word‑documenten.

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}