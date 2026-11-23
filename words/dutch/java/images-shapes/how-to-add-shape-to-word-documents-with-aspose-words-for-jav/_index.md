---
category: general
date: 2026-11-22
description: Leer hoe je een vorm aan Word kunt toevoegen met Aspose.Words voor Java
  – voeg een rechthoek in en verberg deze via code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: nl
lastmod: 2026-11-22
og_description: Voeg een vorm toe aan Word met Aspose.Words voor Java. Deze tutorial
  laat zien hoe je een rechthoek invoegt, de vorm verbergt en het document opslaat.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Vorm toevoegen aan Word met Aspose.Words – Java-gids
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Hoe een vorm toevoegen aan Word‑documenten met Aspose.Words voor Java
url: /nl/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een vorm toe te voegen aan Word‑documenten met Aspose.Words for Java

Als je **vormen aan Word** documenten programmatically wilt toevoegen, maakt Aspose.Words for Java het eenvoudig. In deze gids leer je **hoe je een vorm invoegt**, de zichtbaarheid ervan beheert, en **hoe je een vorm verbergt** zodat het uiteindelijke bestand er precies uitziet zoals je verwacht.

Je doorloopt een volledig, uitvoerbaar voorbeeld dat een bestaande `.docx` laadt, een rechthoek invoegt, deze verbergt en het resultaat opslaat. Er zijn geen externe scripts of handmatige stappen nodig, en de tutorial behandelt veelvoorkomende variaties zoals het maken van een nieuw document vanaf nul of een vorm alleen verbergen bij afdrukken.

## Vereisten

* Java 17 (of later) geïnstalleerd – eerdere versies werken, maar de nieuwste LTS biedt betere prestaties.  
* Maven 3.8+ voor dependency‑beheer.  
* Een geldige Aspose.Words for Java‑licentie (de gratis evaluatie werkt voor leren).  
* Een IDE of teksteditor naar keuze (bijv. IntelliJ IDEA, VS Code).

## Stap 1: Voeg Aspose.Words toe aan je Maven‑project

Voeg de volgende dependency toe aan je `pom.xml`. Hiermee haal je de nieuwste stabiele versie (vanaf november 2026).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Pro tip:** Gebruik een `<scope>provided</scope>` clausule als je van plan bent de JAR te leveren met je eigen licentie‑logica.

## Vorm toevoegen aan Word – het document initialiseren

De eerste functionele stap is het verkrijgen van een `Document`‑object. Je kunt een bestaand bestand laden of een nieuw document aanmaken.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Waarom dit belangrijk is*: De `Document`‑klasse is het toegangspunt voor alle Word‑manipulaties. Het laden van een bestaand bestand behoudt stijlen, kopteksten en voetteksten, terwijl een nieuw document je een schone lei geeft.

## Hoe een vorm in een Word‑document in te voegen

Maak vervolgens een `DocumentBuilder` aan om de inhoud van het document te wijzigen. De builder biedt methoden voor het invoegen van tekst, tabellen en **vormen**.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

De `insertShape`‑aanroep retourneert een `Shape`‑object dat je verder kunt configureren (kleur, rand, tekst, enz.). De afmetingen worden uitgedrukt in punten (1 pt = 1/72 in).

*Waarom je een rechthoek zou kunnen gebruiken*: Rechthoeken zijn de meest voorkomende container voor annotaties, watermerken of tijdelijke aanduidingen. Je kunt `ShapeType.RECTANGLE` vervangen door `ShapeType.ELLIPSE`, `ShapeType.LINE`, enz., om aan verschillende visuele behoeften te voldoen.

## Hoe een vorm te verbergen in Word

Soms moet een vorm bestaan voor lay‑outberekeningen, maar mag deze niet verschijnen in de uiteindelijke weergave. Aspose.Words biedt de methode `setHidden(true)` om dit te bereiken.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

De verborgen‑vlag werkt zoals de **Verborgen** opmaakoptie in Microsoft Word: de vorm wordt weggelaten uit de visuele lay‑out, maar blijft wel deel uitmaken van het objectmodel van het document. Dit is nuttig voor:

* Het opslaan van metadata of markeringen die je applicatie later leest.  
* Het maken van tijdelijke aanduidingen die net voor publicatie worden verwijderd.  
* Het regelen van zichtbaarheid voor verschillende uitvoerformaten (bijv. verbergen in HTML maar behouden in PDF).

> **Opmerking:** Verborgen vormen worden standaard nog steeds geëxporteerd naar PDF. Als je ze ook uit PDF wilt weglaten, stel dan `rectangle.getWrapType( ) = WrapType.NONE` in en pas de `Hidden`‑eigenschap dienovereenkomstig aan.

## Stap 4: Sla het gewijzigde document op

Sla tenslotte de wijzigingen op in een nieuw bestand.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

Wanneer je `output.docx` opent in Microsoft Word, zal de rechthoek niet zichtbaar zijn, maar blijft hij deel van de documentboom. Je kunt de aanwezigheid programmatisch verifiëren door het bestand opnieuw te laden en `Shape.isHidden()` te controleren.

### Verwachte output

* Het bestand `output.docx` opent zonder zichtbare vormen.  
* Als je het document inspecteert met Aspose.Words (bijv. `doc.getChildNodes(NodeType.SHAPE, true).size()`), zal het aantal vormen **1** zijn, wat bevestigt dat de vorm bestaat maar verborgen is.

## Geavanceerde variaties en randgevallen

### 1. Een vorm maken in een nieuw document

Als je vanaf nul begint, vervang je de laadregel door:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. De vorm nauwkeurig positioneren

Standaard plaatst `insertShape` de vorm op de huidige cursorpositie. Om deze absoluut te positioneren:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Zichtbaarheid per uitvoerformaat regelen

Als je de vorm zichtbaar wilt in de Word‑UI maar verborgen bij export naar PDF, gebruik dan `Shape.setWrapType(WrapType.NONE)` samen met `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Tekst toevoegen binnen de vorm

Een rechthoek kan een tekstframe bevatten:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

Je kunt vervolgens het tekstvak verbergen met dezelfde `setHidden(true)`‑aanroep.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Symptoom | Oorzaak | Oplossing |
|----------|---------|-----------|
| Vorm verschijnt zelfs na `setHidden(true)` | Het document werd opgeslagen voordat de verborgen‑vlag werd ingesteld. | Zorg ervoor dat je `setHidden(true)` **vóór** `doc.save()` aanroept. |
| Vormgrootte ziet er vervormd uit | Verwarring tussen punten en pixels op schermen met hoge DPI. | Gebruik punten (72 pt = 1 in) voor consistente afmetingen op alle platformen. |
| Verborgen vorm wordt toch afgedrukt | Sommige printers negeren de verborgen‑vlag. | Stel `Shape.setWrapType(WrapType.NONE)` in en maak ook de `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)` leeg. |

## Conclusie

Je weet nu hoe je **vormen aan Word** documenten kunt toevoegen met Aspose.Words for Java, **hoe je een vorm invoegt**, en **hoe je een vorm verbergt** zodat deze onzichtbaar blijft voor eindgebruikers maar wel deel uitmaakt van de documentstructuur. Het volledige voorbeeld hierboven laadt een bestand, voegt een rechthoek toe, verbergt deze en slaat het resultaat op, en behandelt zowel typische gebruikssituaties als diverse randgevallen.

Vanaf hier kun je gerelateerde onderwerpen verkennen, zoals **hoe je een vorm invoegt** met aangepaste vulkleuren, **hoe je een vorm verbergt in Word** voor voorwaardelijke afdrukken, of het automatiseren van bulk‑documentverwerking met Aspose.Words. Experimenteer met verschillende `ShapeType`‑waarden, positioneringsopties en zichtbaarheidsvlaggen om ze aan te passen aan jouw specifieke workflow.

Veel programmeerplezier, en geniet van de flexibiliteit die programmatische Word‑manipulatie biedt voor je Java‑applicaties!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak een Word‑document programmatically, voeg een vorm toe en verberg deze in Java met Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Hoe een vorm te verbergen in een Word‑document met Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Maak een leeg .docx Word‑document en voeg een verborgen rechthoekige vorm toe met Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}