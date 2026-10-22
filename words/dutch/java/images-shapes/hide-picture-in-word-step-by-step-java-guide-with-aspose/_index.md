---
category: general
date: 2026-08-14
description: Afbeelding verbergen in Word met Java. Leer hoe je een afbeelding verbergt,
  een afbeelding verbergt, de verborgen eigenschap instelt en een vorm verbergt in
  Word met Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide picture in word
- how to hide picture
- how to hide image
- set hidden property
- hide shape in word
language: nl
lastmod: 2026-08-14
og_description: Verberg afbeelding in Word met Java en Aspose.Words. Deze tutorial
  laat zien hoe je de verborgen eigenschap op een afbeelding instelt, een vorm in
  Word verbergt en het document in enkele seconden opslaat.
og_image_alt: Screenshot of Java code hiding a picture in a Word document
og_title: Afbeelding verbergen in Word – stapsgewijze Java‑gids met Aspose
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Hide picture in Word using Java. Learn how to hide picture, hide image,
    set hidden property, and hide shape in Word with Aspose.Words.
  headline: Hide picture in Word – step‑by‑step Java guide with Aspose
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Afbeelding verbergen in Word – stapsgewijze Java‑gids met Aspose
url: /nl/java/images-shapes/hide-picture-in-word-step-by-step-java-guide-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Afbeelding verbergen in Word – stapsgewijze Java‑gids met Aspose

Als je programmatically **afbeelding verbergen in Word** moet, toont deze gids de volledige oplossing. Je ziet hoe je een afbeelding kunt vinden, de verborgen‑vlag toepast en het bijgewerkte bestand terug naar schijf schrijft.

Een afbeelding verbergen is een veelvoorkomende eis wanneer je rapporten genereert, sjablonen maakt of documenten voorbereidt voor een compliance‑review. Het onderstaande voorbeeld toont **hoe je een afbeelding kunt verbergen** met Aspose.Words for Java, maar dezelfde concepten gelden voor elke tekstverwerkingsbibliotheek die een shape’s `setHidden`‑methode beschikbaar stelt.

## Wat je zult bereiken

* Laad een `.docx`‑bestand met Aspose.Words.
* Zoek de eerste afbeelding‑shape in het document.
* **Stel de verborgen eigenschap in** voor die shape zodat deze niet verschijnt wanneer het bestand wordt geopend in Microsoft Word.
* Sla het gewijzigde document op zonder andere inhoud te wijzigen.

De enige voorwaarde is een Java‑ontwikkelomgeving (JDK 8 of nieuwer) en een geldige Aspose.Words for Java‑licentie. Er zijn geen extra Maven‑plugins nodig naast de kernbibliotheek.

## Afbeelding verbergen in Word met Aspose.Words

De eerste stap is het aanmaken van een `Document`‑object dat het bronbestand vertegenwoordigt. Aspose.Words leest het volledige Word‑pakket in het geheugen, waardoor het eenvoudig is om door knooppunten zoals shapes, alinea’s en tabellen te navigeren.

```java
// Step 1: Load the Word document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Het aanmaken van de `Document`‑instantie valideert het bestandsformaat en bouwt een interne knooppuntboom. Deze boom vormt de basis voor alle volgende bewerkingen, inclusief **hoe je afbeeldingobjecten verbergt**.

## Hoe je een afbeelding verbergt met de set hidden‑eigenschap

Een afbeelding in een Word‑bestand wordt opgeslagen als een `Shape`‑knooppunt met `ShapeType.IMAGE`. De bibliotheek biedt de `setHidden(boolean)`‑methode om de zichtbaarheid van de shape te regelen. De volgende stream filtert de knooppuntcollectie om de eerste afbeelding‑shape te vinden.

```java
// Step 2: Locate the first picture shape in the document
Shape picture = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getShapeType() == ShapeType.IMAGE)
        .findFirst()
        .orElse(null);
```

De `getChildNodes`‑aanroep doorloopt de volledige documentboom (`true` schakelt diepe zoekopdracht in). De lambda‑expressie controleert de `ShapeType` van elk knooppunt. Dit patroon is de aanbevolen manier om **hoe je een afbeelding verbergt** wanneer je precieze controle over knooppuntselectie nodig hebt.

## Hoe je een afbeelding verbergt in een Word‑document

Zodra de doel‑shape is geïdentificeerd, pas je de verborgen‑vlag toe. Het instellen van deze eigenschap verwijdert de afbeelding niet; het instrueert Word alleen om de shape als verborgen te behandelen tijdens het renderen.

```java
// Step 3: Hide the picture if it was found
if (picture != null) {
    picture.setHidden(true);
}
```

De `setHidden(true)`‑aanroep wordt direct vertaald naar het onderliggende XML‑attribuut `w:hidden="true"`. Word respecteert dit attribuut zowel in de desktop‑ als online‑editors, waardoor de afbeelding onzichtbaar blijft voor alle lezers.

## Shape verbergen in Word – aanvullende overwegingen

Hoewel het voorbeeld alleen de eerste afbeelding verbergt, kun je de logica uitbreiden om meerdere shapes te verwerken:

```java
// Hide all picture shapes
for (Node node : doc.getChildNodes(NodeType.SHAPE, true)) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.IMAGE) {
        shape.setHidden(true);
    }
}
```

* **Prestaties** – Het doorlopen van de knooppuntboom is O(n); bij zeer grote documenten kun je overwegen de zoekopdracht te beperken tot specifieke secties.
* **Compatibiliteit** – De verborgen‑vlag werkt met Word 2007+ (`.docx`) en Word 97‑2003 (`.doc`) bestanden.
* **Zichtbaarheid schakelen** – Om een verborgen afbeelding weer zichtbaar te maken, roep je `shape.setHidden(false)` aan.

Deze tips helpen je om **shape verbergen in Word** scenario's te beheersen, verder dan het basisgeval.

## Het gewijzigde document opslaan

Na het bijwerken van de verborgen‑vlag, schrijf je het document terug naar de opslag. Aspose.Words behoudt automatisch alle andere documentonderdelen, zoals stijlen, kopteksten en voetteksten.

```java
// Step 4: Save the modified document
doc.save("YOUR_DIRECTORY/output.docx");
```

De `save`‑methode ondersteunt een breed scala aan formaten (PDF, HTML, ODT). In deze tutorial houden we de uitvoer als een Word‑bestand om het verborgen‑afbeelding‑effect direct te demonstreren.

## Volledig uitvoerbaar voorbeeld

Alle stappen samenvoegen levert een zelfstandig programma op dat je direct kunt compileren en uitvoeren.

```java
import com.aspose.words.*;

public class HidePictureExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Locate the first picture shape in the document
        Shape picture = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                .stream()
                .filter(node -> ((Shape) node).getShapeType() == ShapeType.IMAGE)
                .findFirst()
                .orElse(null);

        // Hide the picture if it was found
        if (picture != null) {
            picture.setHidden(true);
        }

        // Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Verwacht resultaat:** Open `output.docx` in Microsoft Word. De oorspronkelijke afbeelding wordt niet weergegeven, maar de rest van het document (tekst, tabellen, andere grafische elementen) blijft ongewijzigd. Als je de XML (`document.xml`) inspecteert, zie je het attribuut `w:hidden="true"` op het `<w:pict>`‑element dat overeenkomt met de verborgen afbeelding.

## Conclusie

Je weet nu hoe je **een afbeelding kunt verbergen in Word** met Java, Aspose.Words en de `setHidden`‑eigenschap. De tutorial behandelde het vinden van een afbeelding‑shape, het toepassen van de verborgen‑vlag en het opslaan van de wijzigingen. Met deze basis kun je ook **shapes verbergen in Word**, meerdere afbeeldingen verwerken, of de zichtbaarheid schakelen op basis van bedrijfsregels.

**Volgende stappen**

* Verken **hoe je een afbeelding conditioneel kunt verbergen** op basis van metadata (bijv. gebruikersrol).
* Combineer deze techniek met mail‑merge om gepersonaliseerde, privacy‑bewuste documenten te genereren.
* Bekijk de Aspose.Words API‑referentie voor geavanceerde shape‑manipulatie, zoals het wijzigen van rotatie of het toepassen van watermerken.

Voel je vrij om te experimenteren met variaties, zoals het verbergen van grafieken of SmartArt‑objecten, en deel je bevindingen met de ontwikkelaarscommunity. Veel plezier met coderen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Grafiekas verbergen in een Word‑document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Geboekte inhoud tonen/verbergen in Word‑document](/words/english/net/programming-with-bookmarks/show-hide-bookmarked-content/)
- [Inline‑afbeelding invoegen in Word‑document met Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}