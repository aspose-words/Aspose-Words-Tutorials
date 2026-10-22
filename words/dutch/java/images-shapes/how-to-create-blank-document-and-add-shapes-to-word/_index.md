---
category: general
date: 2026-09-18
description: Maak een leeg document en voeg vormen toe aan Word met Aspose.Words –
  leer hoe je een driehoekvorm en meer kunt toevoegen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: nl
lastmod: 2026-09-18
og_description: Maak een leeg document in Word met Aspose.Words en leer hoe je een
  driehoekvorm, gegroepeerde vormen en andere grafische elementen kunt invoegen. Volg
  deze volledige gids.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: Maak een leeg document en voeg vormen toe aan Word – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Hoe een leeg document aanmaken en vormen toevoegen in Word
url: /nl/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een leeg document te maken en vormen toe te voegen aan Word

Als je een **blank document** moet maken en het vervolgens wilt verrijken met grafische elementen, laat deze gids je precies zien hoe. We lopen stap voor stap door het maken van een Word‑bestand vanaf nul en **vormen toevoegen aan Word**, inclusief **how to insert triangle**‑vorm, met behulp van Aspose.Words for Java.

Je voltooit de tutorial met een kant‑klaar *.docx*-bestand dat een gegroepeerde vorm met een driehoek bevat. De stappen behandelen alles van projectconfiguratie tot het opslaan van het uiteindelijke **create word document**. Er zijn geen externe tools nodig, behalve Aspose.Words.

## Vereisten

* Java 17 of later geïnstalleerd  
* Maven of Gradle voor afhankelijkheidsbeheer  
* Een Aspose.Words for Java‑licentie (de gratis evaluatie werkt voor deze demo)  

Als je een ander buildsysteem verkiest, pas dan de afhankelijkheidssyntaxis dienovereenkomstig aan. De code werkt op elk platform dat Java ondersteunt.

## Leeg document maken met Aspose.Words

De eerste bewerking is om **blank document** in het geheugen te **creëren**. Aspose.Words biedt een `Document`‑klasse die een Word‑bestand zonder inhoud vertegenwoordigt.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

De `new Document()`‑constructor bouwt een lege *.docx*-structuur, die je later kunt vullen met alinea's, tabellen of grafische elementen. Omdat het document leeg is, heb je volledige controle over elk element dat je toevoegt.

## Vormen toevoegen aan Word – een groepsvorm invoegen

Een groepsvorm stelt je in staat om meerdere grafische elementen als één eenheid te behandelen. Dit is handig wanneer je meerdere vormen tegelijk wilt verplaatsen of van grootte wilt wijzigen.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` is de primaire API voor het toevoegen van inhoud. De `insertGroupShape`‑aanroep maakt een container van 300 × 300 punten (ongeveer 4 × 4 inch). Na deze aanroep staat de cursor *binnen* de groep, klaar voor extra vormen.

### Waarom een groepsvorm gebruiken?

Groeperen houdt gerelateerde grafische elementen uitgelijnd en maakt het eenvoudiger om uniforme opmaak toe te passen. Als je later besluit de driehoek te verplaatsen, beweegt de hele groep mee, waardoor de lay-out behouden blijft.

## Hoe een driehoekvorm in de groep in te voegen

Nu behandelen we **how to insert triangle** vorm. De driehoek is een van de ingebouwde `ShapeType`‑waarden.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

De `moveTo`‑aanroep zorgt ervoor dat het invoegpunt van de builder de eerste alinea van de groep is. `insertShape` voegt vervolgens een driehoek van 60 × 60 punten toe. Omdat de cursor zich binnen de groep bevindt, wordt de driehoek een kind van de groepsvorm.

**Add triangle shape** tips:

* De grootte wordt gemeten in punten; 72 punten is gelijk aan één inch. Pas de afmetingen aan op jouw lay-out.  
* Als je een andere oriëntatie nodig hebt, gebruik dan `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` om de vorm binnen de groep uit te lijnen.  
* De driehoek erft de vul- en lijneigenschappen van de groep, tenzij je ze overschrijft met `shape.getFillColor()` of `shape.getStrokeColor()`.

## Document opslaan – create word document

Na het construeren van de grafische elementen sla je het bestand op. Deze stap voltooit de **create word document**‑operatie.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` schrijft de in‑memory representatie naar schijf als een standaard Word‑document. Je kunt `ExtendedGroup.docx` openen in Microsoft Word, LibreOffice, of elke viewer die het OOXML‑formaat ondersteunt. Het bestand toont een gegroepeerde vorm met een driehoek, precies zoals door de code is opgebouwd.

## Volledig uitvoerbaar voorbeeld

Door alle onderdelen samen te voegen, hier is het volledige programma dat je kunt kopiëren, compileren en uitvoeren:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### Verwacht resultaat

Wanneer je `ExtendedGroup.docx` opent, zie je een enkele groepsvorm die het midden van de pagina inneemt. Binnen die groep verschijnt een kleine driehoek op de standaardpositie. De driehoek kan worden geselecteerd en verplaatst als onderdeel van de groep, wat bevestigt dat **add shapes to word** naar behoren heeft gewerkt.

## Veelgestelde vragen en randgevallen

| Vraag | Antwoord |
|----------|--------|
| *Kan ik meer dan één vorm in de groep toevoegen?* | Ja. Na het invoegen van de driehoek, houd de cursor binnen de groep en roep `builder.insertShape` opnieuw aan met een andere `ShapeType`. |
| *Wat als ik de driehoek rood wil hebben?* | Haal de `Shape` op die wordt geretourneerd door `insertShape` en roep `shape.getFillColor().setColor(Color.RED)` aan. |
| *Werkt dit met oudere .doc‑bestanden?* | Aspose.Words slaat op in het formaat dat je opgeeft. Gebruik `doc.save("file.doc", SaveFormat.DOC)` om een legacy Word‑document te maken. |
| *Hoe wijzig ik de rand van de groep?* | Gebruik `group.getStrokeColor().setColor(Color.BLUE)` en `group.setLineWeight(2.0)` om de omtrek aan te passen. |
| *Is er een manier om de driehoek te roteren?* | Roep `shape.getRotation()` aan om een hoek in graden in te stellen. |

## Pro‑tips

* **Reuse the builder** – het aanmaken van een nieuwe `DocumentBuilder` voor elke vorm veroorzaakt overhead. Houd één enkele builder per document.  
* **Unit conversion** – als je met millimeters werkt, converteer ze naar punten (`points = mm * 2.83465`).  
* **Performance** – voor grote documenten, roep `doc.updatePageLayout()` slechts één keer aan nadat alle vormen zijn toegevoegd.

## Conclusie

Je weet nu hoe je **create blank document**, **add shapes to Word**, en specifiek **how to insert triangle** vorm kunt gebruiken met Aspose.Words for Java. Het volledige voorbeeld toont de volledige workflow van een leeg bestand tot een opgeslagen **create word document** dat een gegroepeerde driehoek bevat.

Vanaf hier kun je extra `ShapeType`‑waarden verkennen, aangepaste opmaak toepassen, of meerdere groepen combineren om complexe diagrammen te bouwen. Experimenteer met verschillende groottes, kleuren en posities om Word‑automatisering in Java onder de knie te krijgen.

--- 

*Klaar om je volgende rapport te automatiseren? Clone het voorbeeld, pas de afmetingen aan, en integreer de code vandaag nog in je eigen applicatie.*

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}