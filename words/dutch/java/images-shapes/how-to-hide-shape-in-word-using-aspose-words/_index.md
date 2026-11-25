---
category: general
date: 2026-11-25
description: Verberg een vorm in Word met Aspose.Words en leer een Word‑document te
  maken met Aspose terwijl je een rechthoekige vorm in Word invoegt in slechts een
  paar regels code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide shape in word
- create word document aspose
- insert rectangle shape word
- Aspose.Words shape handling
- hide Word objects programmatically
language: nl
lastmod: 2026-11-25
og_description: Vorm verbergen in Word met Aspose.Words. Deze tutorial laat zien hoe
  je een Word‑document maakt met Aspose, een rechthoekige vorm in Word invoegt en
  deze via code verbergt.
og_image_alt: Screenshot of a hidden rectangle shape inside a Word document created
  with Aspose.Words
og_title: Vorm verbergen in Word met Aspose.Words – snelle stap‑voor‑stap gids
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  headline: How to hide shape in Word using Aspose.Words
  type: TechArticle
- description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  name: How to hide shape in Word using Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17+ (or .NET 6+ if you prefer C#—the API calls are analogous). *
      Aspose.Words for Java 24.x (the latest version at the time of writing). * An
      IDE such as IntelliJ IDEA, Eclipse, or VS Code.'
  - name: Create a Word document aspose
    text: First, instantiate a blank `Document` and a `DocumentBuilder`. The builder
      provides a fluent API for adding content, including shapes.
  - name: Insert rectangle shape word
    text: Now we add a rectangle shape. The `insertShape` method requires the shape
      type and its dimensions in points (1 point = 1/72 inch).
  - name: Hide the shape so it does not appear in the layout
    text: Aspose.Words mirrors the Microsoft Word *Hidden* attribute. Setting it to
      `true` tells Word to omit the shape from rendering, while keeping the object
      in the document structure.
  - name: Save and verify the result
    text: Finally, write the document to disk. Open the file in Microsoft Word to
      confirm that the rectangle is not visible. You can also inspect the underlying
      XML to see the hidden flag.
  - name: (Optional) Unhide the shape later
    text: If you need to make the shape visible again, load the document, locate the
      shape, and set `hidden` to `false`.
  - name: What the output files contain
    text: '* **HideShapeResult.docx** – the rectangle is hidden; the page looks empty.
      * **UnhiddenShape.docx** – the same rectangle is visible, showing a red box
      with a black outline.'
  - name: Next steps
    text: '* Explore **conditional content** by combining hidden shapes with mail‑merge
      fields. * Learn how to **hide text runs** (`Run.setHidden(true)`) for more granular
      control. * Check the Aspose.Words documentation on **document protection** to
      prevent users from accidentally unhiding shapes.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape manipulation
title: Hoe een vorm verbergen in Word met Aspose.Words
url: /nl/java/images-shapes/how-to-hide-shape-in-word-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een vorm verbergen in Word met Aspose.Words

Als je **een vorm in Word wilt verbergen** tijdens het programmatisch genereren van documenten, maakt Aspose.Words het moeiteloos. In deze gids zie je precies hoe je een Word‑document aspose maakt, een rechthoekige vorm word invoegt, en vervolgens die vorm verbergt zodat deze niet in de lay-out verschijnt. Het volledige, uitvoerbare voorbeeld wordt geleverd zodat je het kunt copy‑pasten in je IDE en het resultaat meteen kunt zien.

Je eindigt deze tutorial met een Word‑bestand dat een verborgen rechthoek bevat — handig voor tijdelijke aanduidingen, conditionele inhoud, of metadata die onzichtbaar moet blijven voor de lezer. Er zijn geen externe tools nodig, behalve de Aspose.Words for Java (of .NET) bibliotheek.

## Wat je zult leren

* Hoe je **een Word‑document aspose** vanaf nul maakt.  
* Hoe je **een rechthoekige vorm word** invoegt met behulp van de `DocumentBuilder`.  
* Hoe je de `hidden`‑eigenschap van de vorm instelt zodat deze niet wordt gerenderd in de uiteindelijke lay‑out.  
* Hoe je verifieert dat de vorm verborgen is en hoe je deze indien nodig weer zichtbaar maakt.  

### Vereisten

* Java 17+ (of .NET 6+ als je C# verkiest — de API‑aanroepen zijn analoog).  
* Aspose.Words for Java 24.x (de nieuwste versie op het moment van schrijven).  
* Een IDE zoals IntelliJ IDEA, Eclipse of VS Code.  

> **Pro tip:** Gebruik de gratis tijdelijke licentie van Aspose als je nog geen commerciële licentie hebt. De bibliotheek werkt zonder licentie voor evaluatie, maar een licentie verwijdert de evaluatiewatermerken.

## Vorm verbergen in Word met Aspose.Words

De kernstappen zijn:

1. **Maak een nieuw `Document`.**  
2. **Voeg een rechthoekige vorm toe** met `DocumentBuilder`.  
3. **Markeer de vorm als verborgen** zodat deze niet verschijnt wanneer het bestand wordt geopend.  

### Stap 1: Een Word‑document aspose maken

Eerst maak je een lege `Document` en een `DocumentBuilder` aan. De builder biedt een fluente API voor het toevoegen van inhoud, inclusief vormen.

```java
// Step 1: Create a new document and a DocumentBuilder to work with it
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // Load a free evaluation license (optional for production)
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Create an empty Word document
        Document doc = new Document();

        // DocumentBuilder lets us add text, tables, shapes, etc.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Waarom dit belangrijk is:**  
Het maken van een nieuw `Document` geeft je een schoon canvas. De `DocumentBuilder` is de aanbevolen manier om het document te wijzigen omdat deze automatisch het huidige invoegpunt bijhoudt en sectie-/paginabeheer voor je afhandelt.

### Stap 2: Een rechthoekige vorm word invoegen

Nu voegen we een rechthoekige vorm toe. De `insertShape`‑methode vereist het vormtype en de afmetingen in punten (1 punt = 1/72 inch).

```java
        // Step 2: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

        // Optional: give the shape a visible fill and outline so you can see it before hiding
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);
```

**Waarom dit belangrijk is:**  
`insertShape` maakt een tekenobject dat zich bevindt in het *drawing*-deel van het document. Door de grootte op te geven, bepaal je hoeveel ruimte de vorm zou innemen als deze zichtbaar was. De optionele opmaak helpt je de vorm te verifiëren voordat je deze verbergt.

### Stap 3: De vorm verbergen zodat deze niet in de lay‑out verschijnt

Aspose.Words spiegelt het Microsoft Word *Hidden*‑attribuut. Het instellen op `true` vertelt Word de vorm niet te renderen, terwijl het object in de documentstructuur behouden blijft.

```java
        // Step 3: Hide the shape so it does not appear in the layout
        rectangle.setHidden(true);
```

**Waarom dit belangrijk is:**  
Een verborgen vorm kan nog steeds programmatisch worden benaderd (bijv. voor conditionele verwerking) en later weer zichtbaar worden gemaakt door de eigenschap te toggelen. Dit is ideaal voor scenario's zoals **conditionele tijdelijke aanduidingen** die alleen voor bepaalde doelgroepen moeten verschijnen.

### Stap 4: Opslaan en het resultaat verifiëren

Tot slot schrijf je het document naar schijf. Open het bestand in Microsoft Word om te bevestigen dat de rechthoek niet zichtbaar is. Je kunt ook de onderliggende XML inspecteren om de verborgen‑vlag te zien.

```java
        // Save the document
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**Verwachte output:**  
Het uitvoeren van het programma geeft:

```
Document saved to HideShapeResult.docx
```

Wanneer je *HideShapeResult.docx* opent in Word, lijkt de pagina leeg (of bevat eventuele andere inhoud die je vóór de vorm hebt toegevoegd). De rechthoek is aanwezig in de XML van het bestand (`<w:hidden>`‑attribuut) maar wordt niet gerenderd.

### Stap 5: (Optioneel) De vorm later weer zichtbaar maken

Als je de vorm weer zichtbaar wilt maken, laad je het document, zoek je de vorm, en stel je `hidden` in op `false`.

```java
        // Load the document again
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
```

**Waarom dit belangrijk is:**  
Het kunnen toggelen van de verborgen‑vlag geeft je volledige controle over dynamische documentgeneratie — bijvoorbeeld je kunt een master‑document genereren met alle optionele elementen verborgen, en ze vervolgens selectief zichtbaar maken op basis van gebruikersvoorkeuren.

## Volledig, uitvoerbaar voorbeeld (create word document aspose, insert rectangle shape word, hide shape)

Hieronder staat het volledige programma dat je direct kunt compileren en uitvoeren.

```java
// HideShapeExample.java
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // ---- License (optional for evaluation) ----
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // ---- Step 1: Create a new document ----
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // ---- Step 2: Insert rectangle shape ----
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill for visual check
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);

        // ---- Step 3: Hide the shape ----
        rectangle.setHidden(true);

        // ---- Step 4: Save the document ----
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);

        // ---- Optional Step 5: Unhide and save a second file ----
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
        System.out.println("Unhidden document saved to UnhiddenShape.docx");
    }
}
```

**De code uitvoeren**

```bash
javac -cp "aspose-words-24.10.jar" HideShapeExample.java
java -cp ".:aspose-words-24.10.jar" HideShapeExample
```

Vervang `aspose-words-24.10.jar` door de daadwerkelijke versie die je hebt gedownload.

### Wat de uitvoerbestanden bevatten

* **HideShapeResult.docx** – de rechthoek is verborgen; de pagina lijkt leeg.  
* **UnhiddenShape.docx** – dezelfde rechthoek is zichtbaar, met een rode doos en een zwarte omlijning.

## Veelgestelde vragen & edge‑case handling

| Question | Answer |
|----------|--------|
| *Zal de verborgen vorm de paginering beïnvloeden?* | Nee. Verborgen objecten worden genegeerd door de layout‑engine, dus ze duwen geen tekst naar een nieuwe pagina. |
| *Kan ik andere Word‑objecten verbergen (bijv. afbeeldingen, tabellen)?* | Ja. De meeste `Node`‑subklassen (inclusief `Shape`, `Paragraph`, `Run`) bieden een `setHidden(boolean)`‑methode. |
| *Wat als het document al vormen bevat?* | Gebruik `doc.getChildNodes(NodeType.SHAPE, true)` om te itereren en alleen de vormen die je wilt verbergen. |
| *Verhoogt het verbergen van een vorm de bestandsgrootte?* | Een beetje, omdat de vorm‑XML behouden blijft. De impact is verwaarloosbaar voor typische documenten. |
| *Blijft de verborgen‑vlag behouden wanneer het document als PDF wordt opgeslagen?* | Bij het converteren naar PDF worden verborgen vormen standaard weggelaten. Je kunt dit regelen met `PdfSaveOptions` indien nodig. |

## Best practices bij het werken met verborgen objecten

* **Geef je vormen een naam** met `setName("MyPlaceholder")`. Dit maakt het later makkelijker om ze te vinden.  
* **Groep gerelateerde verborgen objecten** binnen een `GroupShape` als je de zichtbaarheid van meerdere elementen tegelijk wilt toggelen.  
* **Documenteer het doel** van verborgen elementen in commentaren of een apart specificatie‑bestand — toekomstige maintainers zullen de context waarderen.  
* **Vermijd overmatig gebruik van verborgen objecten**; ze verhogen de documentcomplexiteit en kunnen eindgebruikers die de XML handmatig inspecteren verwarren.

## Conclusie

Je weet nu hoe je **een vorm in Word kunt verbergen** met Aspose.Words, hoe je **een Word‑document aspose maakt**, en hoe je **een rechthoekige vorm word invoegt** voordat je deze verbergt. Het voorbeeld toont de volledige levenscyclus: maken, invoegen, verbergen, opslaan en eventueel weer zichtbaar maken. Pas deze technieken toe om dynamische rapporten, conditionele sjablonen of elke geautomatiseerde Word‑workflow te bouwen waarbij onzichtbare tijdelijke aanduidingen nodig zijn.

### Volgende stappen

* Verken **conditionele inhoud** door verborgen vormen te combineren met mail‑merge‑velden.  
* Leer hoe je **tekst‑runs kunt verbergen** (`Run.setHidden(true)`) voor meer gedetailleerde controle.  
* Bekijk de Aspose.Words‑documentatie over **documentbeveiliging** om te voorkomen dat gebruikers per ongeluk vormen zichtbaar maken.

Veel programmeerplezier, en laat je gegenereerde Word‑bestanden schoon blijven terwijl ze toch de verborgen gegevens bevatten die je nodig hebt!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak een Word‑document programmatisch, voeg een vorm toe en verberg deze in Java met Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Hoe een vorm te verbergen in een Word‑document met Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Maak een leeg .docx Word‑document en voeg een verborgen rechthoekige vorm toe met Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}