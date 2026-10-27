---
category: general
date: 2026-10-26
description: Leer hoe je een Word‑document programmatically maakt, een vorm toevoegt
  en een object verbergt in Word met Aspose.Words for Java – stap‑voor‑stap gids.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: nl
lastmod: 2026-10-26
og_description: Maak een Word‑document programmatisch, leer hoe je een vorm toevoegt
  en een object verbergt in Word met Aspose.Words voor Java. Volledig, uitvoerbaar
  voorbeeld.
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: Maak een Word-document programmatisch – voeg vormen toe en verberg ze in
  Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Maak een Word‑document programmatisch aan en voeg een vorm toe in Java
url: /nl/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-document programmatisch maken en een vorm toevoegen in Java

Als je **een Word-document programmatisch wilt maken**, laat deze tutorial je precies zien hoe je dat doet, een vorm toevoegt en vervolgens het object verbergt in Word. Of je nu een rapportgenerator of een geautomatiseerd contract‑systeem bouwt, je krijgt een complete, kant‑klaar werkende oplossing in slechts een paar minuten.

Je leert hoe je:

* Een Word‑document initialiseert met Aspose.Words for Java.  
* Een ellips (of een andere vorm) invoegt met de **how to add shape**‑techniek.  
* Die vorm verbergt zodat deze nooit verschijnt wanneer het bestand wordt geopend, waarmee je de **how to hide shape**‑vraag beantwoordt.  

Er zijn geen externe tools nodig buiten de Aspose.Words‑bibliotheek, en de code werkt met Java 17 en hoger.

## Prerequisites

Voordat je begint, zorg dat je het volgende hebt:

* Java Development Kit (JDK) 17 of nieuwer geïnstalleerd.  
* Maven of Gradle om afhankelijkheden te beheren (het voorbeeld gebruikt Maven).  
* Een geldige Aspose.Words for Java‑licentie (de gratis evaluatie werkt voor testen).  

Als je nieuw bent met Aspose.Words, raadpleeg dan de officiële Getting Started‑gids, maar je hoeft die niet te lezen om deze tutorial te volgen.

## Maven dependency

Voeg de volgende afhankelijkheid toe aan je `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **Pro tip:** Houd het versienummer up‑to‑date; nieuwere releases bevatten bugfixes voor shape‑handling.

## Step 1: Create Word document programmatically – initializing the document

Het eerste wat je doet wanneer je **een Word-document programmatisch maakt**, is een `Document`‑object instantieren. Dit object vertegenwoordigt het volledige .docx‑bestand in het geheugen.

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom deze stap belangrijk is*: De `Document`‑klasse is het toegangspunt voor alle Word‑verwerkingsoperaties. Zonder dit kun je geen pagina's, alinea's of vormen toevoegen.

## Step 2: How to add shape – inserting an ellipse

Nu behandelen we het **how to add shape**‑deel van de tutorial. Aspose.Words ondersteunt veel vormtypen (Ellipse, Rectangle, TextBox, enz.). Hieronder voegen we een ellips in met een breedte en hoogte van 50 punten.

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

De `insertShape`‑methode retourneert een `Shape`‑object dat je verder kunt aanpassen — kleur, lijntype, rotatie en meer. De coördinaten worden gemeten in punten (1/72 inch).

*Waarom je een vorm zou willen toevoegen*: Vormen zijn handig voor watermerken, decoratieve elementen of tijdelijke aanduidingen die je later verbergt of vervangt.

## Step 3: How to hide shape – making the object invisible in Word

Om de **how to hide shape**‑vraag te beantwoorden, stel je simpelweg de `Hidden`‑eigenschap van de vorm in op `true`. Dit vertelt Word de vorm als een verborgen object te behandelen, zodat deze nooit wordt weergegeven in de documentweergave of afdruk.

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

Als je **object in Word wilt verbergen** voor een specifieke gebruiker of conditie, kun je deze eigenschap tijdens runtime toggelen op basis van je bedrijfslogica.

> **Note:** Verborgen vormen maken nog steeds deel uit van de XML‑structuur van het document. Ze kunnen later worden onthuld door `setHidden(false)` aan te roepen.

## Step 4: Save the document

Na het toevoegen en verbergen van de vorm, schrijf je het document naar schijf.

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

Wanneer je `HiddenShapeDemo.docx` opent in Microsoft Word, zie je een lege pagina omdat de ellips verborgen is. Het document gedraagt zich verder als elk normaal Word‑bestand.

## Full working example

Alle onderdelen samengevoegd, hier is het complete, uitvoerbare programma:

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**Expected output**

```
Document created successfully.
```

Het openen van `HiddenShapeDemo.docx` toont een lege pagina; de verborgen ellips wordt niet gerenderd, wat bevestigt dat de **hide object in Word**‑operatie geslaagd is.

## Edge cases and variations

| Situation | What to change | Why |
|-----------|----------------|-----|
| Hide a rectangle instead of an ellipse | Use `ShapeType.RECTANGLE` in `insertShape` | Different visual placeholder |
| Hide multiple shapes at once | Loop through `doc.getChildNodes(NodeType.SHAPE, true)` and set `setHidden(true)` | Useful for bulk processing |
| Show the shape only in print view | Set `shape.setVisible(false)` and `shape.setPrint(true)` | Word distinguishes between screen and print visibility |
| Use a different measurement unit | Call `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` | Aligns with your layout requirements |

## Common pitfalls

* **Vergeten `setHidden(true)` aan te roepen** – de vorm verschijnt normaal.  
* **Het document opslaan vóór het verbergen van de vorm** – de volgorde is belangrijk; eerst verbergen, dan opslaan.  
* **Een verouderde Aspose.Words‑versie gebruiken** – oudere releases kunnen de `setHidden`‑API missen.  

Test altijd het gegenereerde bestand in de doel‑versie van Microsoft Word om te verzekeren dat de verborgen status zich gedraagt zoals verwacht.

## Conclusion

In deze gids heb je geleerd hoe je **een Word-document programmatisch maakt**, **een vorm toevoegt**, en **een object in Word verbergt** met Aspose.Words for Java. Het volledige voorbeeld toont de exacte stappen, van het initialiseren van het document tot het opslaan van een bestand waarin de vorm nooit verschijnt.  

Vanaf hier kun je:

* Experimenteren met andere vormtypen (`ShapeType.LINE`, `ShapeType.TEXT_BOX`).  
* Verborgen vormen combineren met bladwijzers om dynamische sjablonen te maken.  
* De `setVisible`‑ en `setPrint`‑eigenschappen verkennen voor fijnmazigere controle over de zichtbaarheid van objecten.

Happy coding, and enjoy automating your Word documents!

## What Should You Learn Next?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [How to create blank word document with Aspose.Words for Java](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}