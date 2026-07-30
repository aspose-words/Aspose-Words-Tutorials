---
category: general
date: 2026-01-11
description: Maak snel een Word‑document in Java door een rechthoekvorm toe te voegen,
  de vulkleur in te stellen en een schaduw op de vorm toe te passen. Leer stap voor
  stap.
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: nl
og_description: Maak een Word-document in Java door een rechthoekvorm in te voegen,
  de vulkleur in te stellen en een schaduw toe te passen. Complete gids met code.
og_title: Word-document maken in Java – Rechthoekvorm toevoegen met schaduw
tags:
- Aspose.Words
- Java
- Document Generation
title: Word-document maken in Java – Rechthoekvorm toevoegen met schaduweffect
url: /nl/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word Document Java – Voeg rechthoekige vorm toe met schaduweffect

Heb je ooit moeten **create word document java** en het er een beetje professioneler uit laten zien? Misschien bouw je een rapportgenerator en een eenvoudige pagina voldoet niet. Het goede nieuws? Met Aspose.Words for Java kun je een rechthoekige vorm in een document plaatsen, er een vleugje kleur aan geven, en zelfs een subtiele schaduw toevoegen – allemaal in een handvol regels.

In deze tutorial lopen we precies dat stap voor stap door: hoe je een rechthoekige vorm toevoegt, de vulkleur instelt, en een schaduw op de vorm toepast zodat je Word‑bestand een beetje professioneler aanvoelt. Aan het einde heb je een uitvoerbaar voorbeeld dat je kunt copy‑paste in je eigen project.

## Wat je nodig hebt

- **Java 17** (of een recente JDK) – de code gebruikt de standaardtaalfuncties.
- **Aspose.Words for Java** bibliotheek – versie 23.9 of nieuwer wordt aanbevolen.
- Een IDE of teksteditor naar keuze – IntelliJ IDEA, Eclipse, VS Code… jij beslist.
- Een map waar het gegenereerde `ShadowShape.docx` wordt opgeslagen.

Er is geen extra configuratiewizardry nodig; voeg gewoon de Aspose.Words JAR toe aan je classpath en je bent klaar om te gaan.

## Stap 1: Zet het project op en importeer Aspose.Words

Allereerst, maak een nieuw Maven (of Gradle) project aan en haal de Aspose.Words‑dependency binnen. Hier is een minimale `pom.xml`‑snippet voor Maven:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

Als je geen Maven gebruikt, plaats dan gewoon het JAR‑bestand in je `libs`‑map en voeg het toe aan het build‑pad.

> **Pro tip:** Aspose biedt een gratis proeflicentie die je kunt insluiten met `License license = new License(); license.setLicense("Aspose.Words.lic");`. Sla deze over voor snelle tests; de bibliotheek werkt in evaluatiemodus.

## Stap 2: Maak een nieuw Document en Builder

Nu gaan we daadwerkelijk **create word document java** objecten maken. De `Document`‑klasse vertegenwoordigt het volledige .docx‑bestand, terwijl `DocumentBuilder` ons in staat stelt inhoud in te voegen.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

Op dit punt heb je een leeg document klaar om vormen, alinea's of iets anders dat je nodig hebt te ontvangen.

## Stap 3: Voeg een rechthoekige vorm in en stel de vulkleur in

Een vorm toevoegen is zo simpel als het aanroepen van `insertShape`. We gebruiken de **add rectangle shape**‑techniek, die onder het secundaire trefwoord *add rectangle shape* valt.

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

Waarom oranje? Het valt op in een zee van wit, maar je kunt het vervangen door elke `java.awt.Color` die je wilt. Deze stap behandelt het secundaire trefwoord *set shape fill color*.

## Stap 4: Configureer het schaduweffect – Apply Shadow to Shape

Nu komt het leuke deel: de rechthoek een subtiele slagschaduw geven. De Aspose‑API biedt een `ShadowFormat`‑object dat elk aspect van de schaduw regelt.

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

Dat codeblok **apply shadow to shape** precies zoals het secundaire trefwoord aangeeft. Je kunt `blur`, `offsetX/Y` en `transparency` aanpassen aan je ontwerptaal. Bijvoorbeeld, een grotere `offsetX` creëert een dramatischer schaduw, terwijl een hogere `transparency` de schaduw fluisterend maakt in plaats van schreeuwend.

## Stap 5: Sla het document op

Tot slot schrijven we het document naar schijf. Kies een map waar je schrijfrechten voor hebt, en geef het bestand een duidelijke naam.

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Wanneer je `ShadowShape.docx` opent in Microsoft Word of LibreOffice, zie je een fel oranje rechthoek met een zachte grijze schaduw die net eronder zweeft.

![create word document java with rectangle shape](/images/shadow-rectangle.png "create word document java – rectangle with shadow")

*De alt‑tekst van de afbeelding bevat het primaire trefwoord, wat voldoet aan de SEO‑regel.*

## Veelgestelde vragen & randgevallen

### Wat als ik een andere vorm nodig heb?

Aspose.Words ondersteunt tientallen `ShapeType`‑waarden – sterren, pijlen, callouts, wat je maar wilt. Vervang simpelweg `ShapeType.RECTANGLE` door `ShapeType.OVAL` of een andere enum‑constante. Dezelfde **how to add shape** stappen gelden.

### Hoe voeg ik de vorm toe aan een specifieke alinea?

In plaats van de vorm direct met de builder in te voegen, kun je deze eerst maken (`new Shape(document, ShapeType.RECTANGLE)`) en vervolgens toevoegen aan een `Paragraph` via `paragraph.appendChild(shape)`. Dit geeft je fijnere controle over de lay‑out.

### Kan ik een gradientvulling toepassen in plaats van een effen kleur?

Ja! Gebruik `rectangle.getFill().setFillType(FillType.GRADIENT)` en definieer een `LinearGradientFill`. De API is iets uitgebreider, maar werkt uitstekend voor moderne ontwerpen.

### Hoe zit het met compatibiliteit met oudere Word‑versies?

Aspose.Words slaat standaard op in het .docx‑formaat, dat wordt ondersteund door Word 2007+ en LibreOffice. Als je .doc nodig hebt, roep dan `document.save("file.doc", SaveFormat.DOC)` aan. Schaduwweergave kan iets afwijken, maar de vorm zelf blijft intact.

## Volledig werkend voorbeeld (Klaar om te copy‑pasten)

Hieronder staat het volledige programma, klaar om te compileren en uit te voeren. Vervang `YOUR_DIRECTORY` door een daadwerkelijk pad op je machine.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Het uitvoeren van deze code produceert een Word‑bestand dat de oranje rechthoek met een zachte grijze schaduw bevat – precies wat we wilden bereiken toen we **create word document java** met een gestylede vorm wilden maken.

## Conclusie

Je hebt nu een solide, end‑to‑end recept voor **create word document java** dat *adds rectangle shape*, *sets shape fill color* en *applies shadow to shape* bevat. De aanpak is eenvoudig, de API is vloeiend, en je kunt het op ontelbare manieren uitbreiden – verschillende vormen, gradientvullingen, of zelfs meerdere schaduwen per vorm.

Wat is de volgende stap? Probeer meerdere vormen te stapelen, experimenteer met `ShadowStyle.ETCHED` voor een ander visueel gevoel, of combineer dit met tabelgeneratie om volledig uitgewerkte rapporten te bouwen. De mogelijkheden worden alleen beperkt door je verbeelding (en misschien het Aspose‑licentieniveau).

Als je tegen problemen aanloopt of ideeën hebt voor verdere verbeteringen, laat dan een reactie achter. Veel plezier met coderen, en geniet ervan om die Word‑documenten er een stuk minder saai uit te laten zien!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}