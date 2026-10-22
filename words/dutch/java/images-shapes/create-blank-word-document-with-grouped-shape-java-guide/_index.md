---
category: general
date: 2026-07-20
description: Maak een leeg Word‑document in Java met Aspose.Words. Leer hoe je een
  groep maakt, een rechthoekvorm invoegt en een afbeelding in de vorm inbedt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: nl
lastmod: 2026-07-20
og_description: Maak een leeg Word‑document in Java met Aspose.Words. Deze gids laat
  zien hoe je een groep maakt, een rechthoekvorm invoegt en een afbeelding in de vorm
  inbedt voor dynamische Word‑bestanden.
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: Maak een leeg Word‑document met gegroepeerde vorm – Java‑gids
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Maak een leeg Word‑document met gegroepeerde vorm – Java‑gids
url: /nl/java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document met gegroepeerde vorm – Java‑gids

Heb je je ooit afgevraagd hoe je **een leeg Word‑document kunt maken** dat al een mooi gegroepeerde vorm bevat? Misschien bouw je een rapport‑sjabloon, of heb je een tijdelijke aanduiding nodig voor een logo en een bijschrift. Hoe dan ook, het probleem is algemeen: je begint met een leeg bestand, moet vervolgens een groep toevoegen, een rechthoek erin plaatsen en tenslotte een afbeelding insluiten – allemaal programmatically.

In deze tutorial lopen we een compleet, kant‑klaar Java‑voorbeeld door dat precies dat doet. Je leert **hoe je een groep maakt**, **een rechthoek‑vorm invoegt**, en **een afbeelding aan een Word‑document toevoegt** binnen dezelfde groep. Aan het einde heb je een Word‑bestand dat eruitziet als een gepolijst sjabloon, klaar voor verdere aanpassing.

> **Wat je krijgt:** een volledig functionele Java‑klasse, stap‑voor‑stap uitleg, tips voor het omgaan met bestandspaden, en een voorbeeld van de verwachte output. Geen externe documentatie nodig – alles wat je nodig hebt staat hier.

---

## Maak een leeg Word‑document – Stapsgewijze overzicht

Het eerste dat we nodig hebben is een echt leeg Word‑bestand. Aspose.Words maakt dit eenvoudig: instantiate gewoon de `Document`‑klasse met de standaardconstructor. Dit geeft je een schoon canvas, gelijk aan het openen van Word en klikken op **New → Blank document**.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Waarom beginnen met een leeg document?**  
> Een leeg document garandeert dat er geen verborgen stijlen of secties zijn die interfereren met de vormen die je later toevoegt. Het houdt ook de bestandsgrootte minimaal, wat handig is wanneer je tientallen bestanden in een batch‑taak genereert.

## Hoe een groep te maken en vormen toe te voegen

Een **group shape** is in wezen een container die meerdere child‑shapes kan bevatten – zie het als een map voor tekenobjecten. Door te groeperen kun je de hele set verplaatsen, van grootte veranderen of roteren met één opdracht.

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

De `insertGroupShape`‑methode retourneert een `GroupShape`‑object dat we zullen gebruiken als ouder voor de rechthoek en de afbeelding. De grootte wordt uitgedrukt in points (1 point = 1/72 inch), dus 200 points geeft je ongeveer een 2,78 × 2,78 inch‑vak.

> **Pro tip:** Als je wilt dat de groep transparant is, stel dan `group.setFillColor(Color.getWhite());` in na het aanmaken.

Nu de groep bestaat, moeten we de builder vertellen waar de volgende vormen geplaatst moeten worden. De cursor van de builder moet zich binnen de eerste alinea van de groep bevinden.

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

## Rechthoek‑vorm invoegen binnen de groep

Een rechthoek wordt vaak gebruikt als tijdelijke aanduiding voor tekst of als visuele aanwijzing. Het toevoegen als de **eerste child** van de groep zorgt ervoor dat het achter eventuele volgende afbeeldingen staat.

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

De rechthoek erft het coördinatensysteem van de groep, dus de grootte van 100 × 50 point wordt standaard gecentreerd. Je kunt het verder stijlen – een rand toevoegen, de vulkleur wijzigen, of een schaduw toepassen – door het geretourneerde `Shape`‑object te benaderen.

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

## Afbeelding toevoegen aan Word‑document – afbeelding insluiten in vorm

Nu het leuke deel: **afbeelding insluiten in vorm**. We voegen een JPEG‑afbeelding in als de tweede child van dezelfde groep. Omdat de cursor nog steeds binnen de groep staat, wordt de afbeelding automatisch een child‑node.

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

Als het afbeeldingsbestand niet wordt gevonden, gooit Aspose.Words een `FileNotFoundException`. Om dat te voorkomen, plaats `sample.jpg` in de werkmap van het project of gebruik een absoluut pad.

> **Wat als je een ander afbeeldingsformaat nodig hebt?**  
> Aspose.Words ondersteunt PNG, BMP, GIF, TIFF en zelfs SVG. Verander gewoon de bestandsextensie en de bibliotheek regelt de conversie.

## Het document opslaan en het resultaat bekijken

Tot slot slaan we het in‑memory document op naar schijf. Het resulterende `.docx`‑bestand bevat één pagina met een gegroepeerde vorm die zowel de rechthoek als de afbeelding bevat.

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

Wanneer je `output.docx` opent in Microsoft Word, zou je een 200 × 200‑point groep in de linkerbovenhoek moeten zien. Binnen de groep zit een lichtgrijze rechthoek bovenaan, en direct eronder verschijnt de opgegeven afbeelding, perfect uitgelijnd.

![Grouped shape example](grouped-shape.png){:alt="Screenshot of a blank Word document with a grouped shape containing a rectangle and an embedded image"}

## Veelvoorkomende variaties en edge‑case handling

| Scenario | Wat te wijzigen | Waarom het belangrijk is |
|----------|----------------|--------------------------|
| **Verschillende groepsgrootte** | Pas de parameters van `insertGroupShape(width, height)` aan | Grotere groepen kunnen complexere lay-outs bevatten. |
| **Meerdere afbeeldingen** | Roep `builder.insertImage()` herhaaldelijk aan na elke keer naar de alinea van de groep te verplaatsen | Elke aanroep voegt een nieuw child‑object toe; je kunt ze ook positioneren met `Shape.setLeft()` / `setTop()`. |
| **Dynamische afbeeldingspaden** | Gebruik `String.format("images/%s.jpg", imageName)` | Maakt de code herbruikbaar voor batch‑verwerking. |
| **Opslaan als PDF** | Vervang `doc.save("output.pdf")` | Aspose.Words kan on‑the‑fly converteren, zodat je direct PDF’s kunt genereren. |
| **De groep roteren** | `group.setRotation(45);` | Handig voor decoratieve watermerken of gestileerde kopteksten. |

## Verwachte output en verificatie

Na het uitvoeren van de klasse:

1. `output.docx` verschijnt in de projectmap.  
2. Het openen van het bestand toont één pagina met een gegroepeerde vorm.  
3. Binnen de groep staat de rechthoek links‑boven, en de afbeelding zit er direct onder.  
4. Het selecteren van de groep in Word markeert beide child‑objecten, wat bevestigt dat ze echt gegroepeerd zijn.

Als een van deze stappen mislukt, controleer dan het afbeeldingspad en zorg ervoor dat de Aspose.Words‑JAR op je classpath staat.

## Conclusie

Je weet nu **hoe je een leeg Word‑document maakt** en het verrijkt met een gegroepeerde vorm die een rechthoek en een ingesloten afbeelding bevat. Door **hoe je een groep maakt**, **een rechthoek‑vorm invoegt**, en **een afbeelding aan een Word‑document toevoegt** onder de knie te krijgen, kun je geavanceerde Word‑sjablonen volledig in code bouwen – zonder handmatige aanpassingen.

Klaar voor de volgende uitdaging? Probeer tekstvakken toe te voegen binnen dezelfde groep, of experimenteer met verschillende vormstijlen om bij je bedrijfsbranding te passen. Je kunt zelfs een volledige rapportenbibliotheek genereren waarbij elk document met deze exacte lay-out begint.

Veel plezier met coderen, en deel gerust je eigen variaties in de reacties hieronder!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak Word‑document Java – Voeg rechthoek‑vorm toe met schaduweffect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Hoe formulier‑velden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words voor Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Hoe PDF‑documenten te maken met Aspose.Words voor Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}