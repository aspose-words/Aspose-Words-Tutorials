---
category: general
date: 2026-08-01
description: Groep vormen in Word met Java met behulp van Aspose.Words. Leer hoe je
  vormen groepeert en snel een rechthoekvorm invoegt met een volledig codevoorbeeld.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- insert rectangle shape
- Aspose.Words Java
- shape grouping tutorial
- Word document automation
language: nl
lastmod: 2026-08-01
og_description: Groep vormen in Word met Java. Deze gids laat zien hoe je vormen groepeert,
  een rechthoekvorm invoegt en een DOCX opslaat met Aspose.Words.
og_image_alt: Screenshot of grouped shapes in a Word document created with Java
og_title: Groepvormen in Word met Java – Volledige programmeerhandleiding
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  headline: Group Shapes in Word with Java – Complete Step-by-Step Guide
  type: TechArticle
- description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  name: Group Shapes in Word with Java – Complete Step-by-Step Guide
  steps:
  - name: 1. Can I group more than two shapes?
    text: 'Absolutely. Just pass a larger array to `insertGroupShape`:'
  - name: 2. What if I need to change the group’s position after creation?
    text: 'Use the group’s `setLeft` and `setTop` methods, just like any other shape:'
  - name: 3. How do I apply a border or fill to the whole group?
    text: The group itself can have formatting, but it doesn’t affect the children
      directly. If you want a common border, wrap the shapes in a rectangle shape
      first, then group everything. Alternatively, iterate over each child shape and
      set the same `fillColor` or `strokeWeight`.
  - name: 4. Does `setHidden(true)` affect printing?
    text: Hidden shapes are **not** printed by default in Word, which can be useful
      for watermarks or template markers. If you need the shape to print but stay
      invisible on screen, you’ll have to use a different approach (e.g., set its
      opacity to 0%).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Groepvormen in Word met Java – Complete stapsgewijze handleiding
url: /nl/java/images-shapes/group-shapes-in-word-with-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Groepvormen in Word met Java – Complete stapsgewijze gids

Als je **vormen in Word** moet groeperen met Java, biedt deze gids alles wat je nodig hebt. Of je nu een rapportgenerator of een dynamische sjabloonengine bouwt, het groeperen van vormen zorgt ervoor dat je documenten er professioneel uitzien en gerelateerde grafieken bij elkaar houdt.

In de komende paar minuten zie je precies **hoe je vormen groepeert** en **rechthoekvormen** invoegt met Aspose.Words, plus een reeks praktische tips die je beschermen tegen veelvoorkomende valkuilen. Klaar om die losse rechthoeken en ellipsen om te vormen tot een nette groep? Laten we beginnen.

## Wat deze tutorial behandelt

* De minimale vereisten (Java 17+, Aspose.Words 24.10 of nieuwer).  
* Een complete, uitvoerbare Java‑programma dat een Word‑document maakt, een rechthoek en een ellips invoegt, ze groepeert, de groep verbergt indien gewenst, en het bestand opslaat.  
* Waarom elke API‑aanroep belangrijk is, niet alleen wat deze doet.  
* Afhandeling van randgevallen voor oudere Aspose.Words‑versies en voor het groeperen van meer dan twee vormen.  
* Verwachte output en een snelle manier om het resultaat te verifiëren.

Aan het einde kun je dit fragment in elk Java‑project plaatsen en direct vormen in Word gaan groeperen zonder door verspreide documentatie te zoeken.

---

## Vereisten

| Requirement | Why it matters |
|-------------|----------------|
| **Java 17+** | Moderne taalfeatures en betere prestaties. |
| **Aspose.Words for Java 24.10+** | De `setHidden`‑methode die later wordt gebruikt bestaat pas vanaf deze versie. |
| **A Maven or Gradle build** | Maakt afhankelijkheidsbeheer moeiteloos. |
| **An IDE (IntelliJ, Eclipse, VS Code)** | Handig voor snel testen, maar elke teksteditor werkt. |

Voeg de Aspose.Words Maven‑dependency toe aan je `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

Als je de voorkeur geeft aan Gradle, is het equivalent:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

---

## Stap 1: Maak een nieuw document en builder

Eerst maken we een leeg `Document` en een `DocumentBuilder`. De builder is de werkpaard die ons in staat stelt vormen, tekst en meer in te voegen.

```java
// Step 1: Create a new empty document and a builder to work with it.
Document doc = new Document();                     // The container for all Word content.
DocumentBuilder builder = new DocumentBuilder(doc); // Fluent API to add elements.
```

*Waarom deze stap?*  
`Document` vertegenwoordigt het volledige DOCX‑bestand, terwijl `DocumentBuilder` een handige cursor‑gebaseerde API biedt. Zonder een builder zou je laag‑niveau node‑collecties handmatig moeten manipuleren — iets dat gemakkelijk fout kan gaan.

---

## Stap 2: Voeg een rechthoekvorm toe (en een ellips)

Nu voegen we de twee basisvormen toe die we willen groeperen. Let op de **insert rectangle shape**‑aanroep — dit is precies het secundaire trefwoord dat je zoekt.

```java
// Step 2: Insert two simple shapes – a rectangle and an ellipse.
Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);
```

Een paar dingen om in gedachten te houden:

* De breedte (`100`) en hoogte (`50`) worden gemeten in punten (1 pt ≈ 1/72 in). Pas ze aan om in je lay‑out te passen.  
* De rechthoek wordt eerst getekend, dus staat standaard achter de ellips. Als je de omgekeerde volgorde nodig hebt, voeg dan eerst de ellips toe.  
* Beide vormen erven de huidige opmaak van de builder (kleur, lijntype). Je kunt ze aanpassen vóór het groeperen als je wilt.

---

## Stap 3: Hoe vormen te groeperen met Aspose.Words

Hier is de kern van de tutorial — **hoe je vormen groepeert**. De `insertGroupShape` API neemt een array van bestaande vormen en retourneert een nieuwe `Shape` die de groep vertegenwoordigt.

```java
// Step 3: Group the two shapes together using the InsertGroupShape API.
Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });
```

Waarom een groep gebruiken?  

* Een groep beweegt als één geheel, waardoor de relatieve positionering behouden blijft.  
* Je kunt transformaties (rotatie, schalen) op de hele set toepassen met één aanroep.  
* Groeperen vereenvoudigt latere bewerking — ontgroepeer later als je individuele elementen wilt aanpassen.

---

## Stap 4 (optioneel): Verberg de groep in de documentweergave

Als je niet wilt dat de groep verschijnt wanneer de gebruiker het document in Word opent, kun je deze verbergen. Deze stap is optioneel maar handig voor achtergrondgrafieken of watermerken.

```java
// Step 4: (Optional) Hide the group so it does not appear in the document view.
groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later
```

**Wat als je een oudere Aspose.Words‑versie gebruikt?**  
De `setHidden`‑methode compileert niet. In dat geval kun je een vergelijkbaar effect bereiken door de `WrapType` van de vorm op `NONE` te zetten en deze achter de tekstlaag te plaatsen:

```java
groupShape.setWrapType(WrapType.NONE);
groupShape.getParagraph().getParagraphFormat().setStyleIdentifier(StyleIdentifier.BACKGROUND);
```

Het is iets uitgebreider, maar houdt de groep nog steeds uit het zicht van de lezer.

---

## Stap 5: Sla het document op

Tot slot schrijf je het document naar schijf. Pas het pad aan naar de locatie waar je het bestand wilt opslaan.

```java
// Step 5: Save the document with the grouped shapes.
doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
```

Wanneer je `GroupShapeResult.docx` opent in Microsoft Word, zie je een rechthoek en een ellips netjes samengevoegd. Als je `setHidden(true)` instelt, is de groep onzichtbaar in de editor maar nog wel aanwezig in het bestand (handig voor later programmatisch verwerken).

---

## Volledig werkend voorbeeld

Hier is de complete, zelf‑behorende Java‑klasse die je kunt copy‑paste in je project:

```java
import com.aspose.words.*;

public class GroupShapeTutorial {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert two simple shapes – a rectangle and an ellipse.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);

        // Step 3: Group the two shapes together using the InsertGroupShape API.
        Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });

        // Step 4: (Optional) Hide the group so it does not appear in the document view.
        groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later

        // Step 5: Save the document with the grouped shapes.
        doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
    }
}
```

**Verwachte output:** Een bestand genaamd `GroupShapeResult.docx` dat een enkele groep bevat met een blauw‑gevulde rechthoek en een rood‑omrande ellips (standaardkleuren). Als je het document opent, de groep selecteert en rechtsklikt → **Group → Ungroup**, zie je de twee oorspronkelijke vormen terugkeren.

---

## Veelgestelde vragen & randgevallen

### 1. Kan ik meer dan twee vormen groeperen?

Absoluut. Geef gewoon een grotere array door aan `insertGroupShape`:

```java
Shape triangle = builder.insertShape(ShapeType.TRIANGLE, 80, 80);
Shape[] manyShapes = new Shape[] { rectangleShape, ellipseShape, triangle };
Shape bigGroup = builder.insertGroupShape(manyShapes);
```

De API schaalt lineair; de enige beperking is het geheugen voor extreem grote groepen.

### 2. Wat als ik de positie van de groep moet wijzigen na creatie?

Gebruik de `setLeft`‑ en `setTop`‑methoden van de groep, net als bij elke andere vorm:

```java
groupShape.setLeft(150);
groupShape.setTop(200);
```

Omdat de groep zich gedraagt als één enkele vorm, bewegen alle onderliggende vormen samen.

### 3. Hoe pas ik een rand of vulling toe op de hele groep?

De groep zelf kan opmaak hebben, maar dit beïnvloedt de kinderen niet direct. Als je een gemeenschappelijke rand wilt, plaats de vormen eerst in een rechthoekvorm en groepeer vervolgens alles. Alternatief kun je over elke kindvorm itereren en dezelfde `fillColor` of `strokeWeight` instellen.

### 4. Heeft `setHidden(true)` invloed op afdrukken?

Verborgen vormen worden standaard **niet** afgedrukt in Word, wat handig kan zijn voor watermerken of sjabloonmarkeringen. Als je wilt dat de vorm wordt afgedrukt maar onzichtbaar blijft op het scherm, moet je een andere aanpak gebruiken (bijv. de doorzichtigheid op 0 % zetten).

---

## Pro‑tips uit de praktijk

* **Geef je vormen een naam** – `groupShape.setName("HeaderGraphics");` maakt debugging makkelijker wanneer je later vormen op naam opvraagt.  
* **Herbruik de builder** – Na het invoegen van een groep blijft de cursor van de builder op de plaats van de groep, zodat je direct daarna al paragrafen kunt toevoegen zonder de positie te resetten.  
* **Versie‑guard** – Als je een bibliotheek levert die mogelijk op oudere Aspose.Words‑versies draait, wikkel de `setHidden`‑aanroep in een try‑catch voor `NoSuchMethodError` en val terug op de `WrapType.NONE`‑truc die eerder werd getoond.  
* **Prestatie‑tip** – Bij het genereren van duizenden ...

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Documentvormen gebruiken in Aspose.Words voor Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Word‑document maken met Java – Rechthoekvorm toevoegen met schaduweffect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Vormen renderen in Aspose.Words voor Java](/words/english/java/rendering-documents/rendering-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}