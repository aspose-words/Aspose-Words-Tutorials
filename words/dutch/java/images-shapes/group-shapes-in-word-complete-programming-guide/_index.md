---
category: general
date: 2026-08-14
description: Groep vormen in Word met Java met behulp van Aspose.Words. Leer hoe je
  een rechthoekvorm maakt, de afmetingen van de vorm instelt en meerdere vormen groepeert
  in een leeg Word‑document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: nl
lastmod: 2026-08-14
og_description: Groep vormen in Word met Aspose.Words voor Java. Maak een leeg Word‑document,
  creëer een rechthoekvorm, stel de afmetingen van de vorm in en groepeer meerdere
  vormen binnen enkele minuten.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Vormen groeperen in Word – Java‑voorbeeld voor ontwikkelaars
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Vormen groeperen in Word – volledige programmeergids
url: /nl/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Groepeer vormen in Word – volledige programmeergids

Als je **vormen in Word wilt groeperen**, leidt deze tutorial je door het hele proces met Java en Aspose.Words. Je leert hoe je een **leeg Word‑document maakt**, een **rechthoekige vorm creëert**, **vormafmetingen instelt**, en uiteindelijk **meerdere vormen groepeert** zodat ze zich gedragen als één object.

Werken met vormen in een Word‑bestand voelt vaak als tekenen op een canvas zonder penseel. Aan het einde van deze gids heb je een herbruikbare code‑snippet die je in elk Java‑project kunt plaatsen, of je nu rapporten, facturen of aangepaste sjablonen genereert.

## Wat je nodig hebt

- Java 8 of nieuwer
- Aspose.Words for Java (de nieuwste versie, bijv. 24.9)
- Een IDE zoals IntelliJ IDEA of Eclipse
- Basiskennis van object‑georiënteerd programmeren

Al deze vereisten zijn gratis te installeren, en de onderstaande code compileert met één Maven‑dependency:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Stap 1: Maak een leeg Word‑document en initialiseert de builder

Het eerste wat je moet doen is **een leeg Word‑document maken**. Dit geeft je een schoon canvas waarop je later vormen kunt invoegen.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` vertegenwoordigt het volledige *.docx*-bestand, terwijl `DocumentBuilder` de helper is die alinea's, tabellen en vormen invoegt. Het initialiseren van beide objecten is de basis voor elke Word‑automatiseringstaak.

## Stap 2: Voeg een groepsvorm‑container toe

Een **groepsvorm** werkt als een map die andere vormen kan bevatten. Eerst maken we de container met een vaste grootte van 400 pt × 200 pt.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

De methode `insertGroupShape` retourneert een `GroupShape`‑object. Alle daaropvolgende vormen die je als één eenheid wilt behandelen, moeten aan dit object worden toegevoegd.

## Stap 3: Maak rechthoekige vormen en stel vormafmetingen in

Nu **creëren we rechthoekige vorm‑objecten**, configureren we hun grootte en positioneren we ze binnen de groep. Deze stap laat ook zien hoe je **vormafmetingen** nauwkeurig **instelt**.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

Beide rechthoeken delen dezelfde afmetingen, maar hun `left`‑eigenschappen verschillen, zodat ze naast elkaar verschijnen. Je kunt `setTop` en `setLeft` aanpassen om elke gewenste lay‑out te realiseren.

## Stap 4: Sla het document op dat de gegroepeerde rechthoeken bevat

Nadat de vormen zich in de groep bevinden, sla je simpelweg het `Document` op. Het resulterende bestand toont twee rechthoeken die samen bewegen wanneer ze worden geselecteerd.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Het uitvoeren van het programma maakt `GroupShape.docx` aan in de werkmap. Open het in Microsoft Word, selecteer één rechthoek, en je zult merken dat de hele groep als één geheel beweegt — precies wat **groepeer vormen in Word** beoogt.

![Group shapes in Word example](group-shapes.png){alt="Voorbeeld van gegroepeerde vormen in Word"}

*Figuur: Twee rechthoekige vormen gegroepeerd in een Word‑document.*

## Pro‑tip: Hergebruik dezelfde groepsvorm

Als je later meer vormen wilt toevoegen (bijv. cirkels, tekstvakken), bewaar dan een referentie naar `groupShape` en blijf `appendChild` aanroepen. Dit voorkomt dat je de container opnieuw moet maken en zorgt ervoor dat alle leden gesynchroniseerd blijven.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## Randgevallen en veelgestelde vragen

- **Wat als de vormen overlappen?** Overlapping is toegestaan; Word rendert ze in de volgorde waarin ze zijn toegevoegd. Gebruik `setZOrder` als je een expliciete stapeling nodig hebt.
- **Kan ik vormen groeperen over verschillende pagina's heen?** Nee. Een `GroupShape` is beperkt tot één pagina omdat het coördinatensysteem paginagerelateerd is.
- **Erven gegroepeerde vormen opmaak?** Elk kind behoudt zijn eigen opmaak (vulkleur, lijntype). Om een uniforme stijl toe te passen, iterate over `groupShape.getChildNodes()` en stel de eigenschappen programmatically in.

## Volledige broncode ter referentie

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Het uitvoeren van het programma produceert een DOCX‑bestand waarin de twee rechthoeken **gegroepeerd** zijn. Het selecteren van een willekeurige rechthoek verplaatst beide, wat bevestigt dat je succesvol **meerdere vormen hebt gegroepeerd**.

## Conclusie

Je weet nu hoe je **vormen in Word kunt groeperen** met Java, van **het bouwen van een leeg Word‑document** tot **het creëren van een rechthoekige vorm**, **het instellen van vormafmetingen**, en uiteindelijk **het groeperen van meerdere vormen** tot één verplaatsbaar object. Dit patroon schaalt naar elk aantal vormen en kan worden gecombineerd met tekst, afbeeldingen of grafieken om rijke, programmatische documenten te bouwen.

### Wat is de volgende stap?

- Verken **groeperen van meerdere vormen** met verschillende types (ellipsen, pijlen, tekstvakken).
- Pas vulkleuren of randen toe door `shape.getFillColor()` en `shape.getLine().setColor()` aan te roepen.
- Voeg de gegroepeerde vorm in een tabelcel in voor gestructureerde rapporten.
- Combineer deze aanpak met mail‑merge om gepersonaliseerde contracten te genereren die merk‑grafische elementen bevatten.

Voel je vrij om te experimenteren, de afmetingen aan te passen of extra inhoud in te sluiten. Zodra je het groeperen onder de knie hebt, worden je Word‑automatiseringsscripts veel flexibeler en beter onderhoudbaar. Veel programmeerplezier!

## Wat moet je hierna leren?


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}