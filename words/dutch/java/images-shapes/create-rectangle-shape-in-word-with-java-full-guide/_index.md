---
category: general
date: 2026-02-15
description: Maak een rechthoekvorm in een Word‑document met Java. Leer hoe je een
  vormschaduw toevoegt, het Word‑document opslaat en een rechthoekvorm toevoegt met
  Aspose.Words.
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: nl
og_description: Maak een rechthoekvorm in een Word‑bestand met Java. Deze gids laat
  zien hoe je een vormschaduw toevoegt, een Word‑document opslaat en stap voor stap
  een rechthoekvorm toevoegt.
og_title: Maak een rechthoekvorm – Java Aspose.Words Tutorial
tags:
- Aspose.Words
- Java
- Document Automation
title: Rechthoekvorm maken in Word met Java – Volledige gids
url: /nl/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm maken in Word met Java – Volledige gids

Heb je ooit een **rechthoekvorm** in een Word‑bestand moeten **maken**, maar wist je niet waar te beginnen? Je bent niet de enige—veel ontwikkelaars lopen tegen die muur aan bij het automatiseren van rapporten of facturen. Het goede nieuws? Met Aspose.Words for Java kun je in een handvol regels een rechthoek creëren, er een mooie schaduw aan geven en het Word‑document opslaan.

In deze tutorial lopen we alles door wat je nodig hebt: van het initialiseren van een leeg document, tot het configureren van een schaduw, tot het uiteindelijk opslaan van het bestand. Aan het einde weet je **hoe je vormschaduw** toevoegt, hoe je **vormschaduw** toevoegt, en hoe je **rechthoekvorm** toevoegt aan elk Word‑document dat je genereert. Geen externe documentatie nodig—alleen pure, uitvoerbare code.

## Vereisten

- Java 8 of nieuwer (de API werkt ook met Java 11+).  
- Aspose.Words for Java‑bibliotheek (versie 23.9 of later).  
- Een IDE zoals IntelliJ IDEA of Eclipse—elk werkt.  
- Basiskennis van Java‑syntaxis.

> **Pro tip:** Als je Maven gebruikt, voeg dan de Aspose.Words‑dependency toe aan je `pom.xml` en laat de IDE de rest afhandelen.

---

## Stap 1: Een nieuw document initialiseren – Hoe **rechthoekvorm** te **maken**  

Allereerst: je hebt een schoon canvas nodig. In Aspose.Words is dat canvas een `Document`‑object.

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

De `Document`‑klasse vertegenwoordigt het volledige .docx‑bestand. Beschouw het als het notitieboek waarin je later **rechthoekvorm** en de bijbehorende schaduw **toevoegt**.

## Stap 2: De rechthoek bouwen – **Rechthoekvorm** **toevoegen**  

Nu bouwen we de rechthoek daadwerkelijk. We stellen de grootte, lay‑out en vulkleur in.

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

Waarom `INLINE`‑wrap? Omdat we willen dat de vorm zich gedraagt als een alinea—perfect voor eenvoudige rapporten. Je kunt dit wijzigen naar `TOPBOTTOM` als je later tekst om de vorm heen wilt laten vloeien.

## Stap 3: Een schaduw toepassen – **Hoe vormschaduw** toe te passen**  

Een platte rechthoek ziet er een beetje saai uit. Een schaduw geeft diepte en maakt het document meer afgewerkt. Hier beantwoorden we praktisch “**hoe vormschaduw** toe te passen”.

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

Elke eigenschap doet iets specifieks:

- `setVisible(true)` zet de schaduw aan.  
- `setColor` kiest een donkergrijs voor een subtiel effect.  
- `setBlurRadius` bepaalt hoe zacht de randen verschijnen.  
- `setOffsetX/Y` verplaatst de schaduw naar rechts en omlaag, alsof er een lichtbron is.  
- `setTransparency` maakt de schaduw een beetje doorschijnend, zodat de vorm de ster blijft.

> **Opmerking:** Als je ooit een gekleurde schaduw nodig hebt, geef dan een andere `java.awt.Color` door aan `setColor`.

## Stap 4: De vorm in het document invoegen  

Met de rechthoek en zijn schaduw klaar, voegen we deze toe aan de eerste sectie van het document.

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

Toevoegen aan de body plaatst de vorm waar een nieuwe alinea zou staan. Als je de rechthoek op een specifieke locatie wilt, kun je `insertBefore` gebruiken of de `Paragraph`‑collectie manipuleren.

## Stap 5: **Word‑document opslaan** – Bewaar je werk  

De laatste stap is het bestand naar schijf schrijven. Dit is het moment waarop je daadwerkelijk **Word‑document opslaat**.

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Vervang `YOUR_DIRECTORY` door een absoluut of relatief pad op jouw machine. Na het uitvoeren van het programma, open `ShadowShape.docx` in Microsoft Word—je zou een lichtgrijze rechthoek met een zachte donkere schaduw moeten zien.

![Diagram dat een rechthoekvorm met schaduw toont, gemaakt met Aspose.Words](https://example.com/rectangle-shadow.png "rechthoekvorm met schaduw maken")

---

## Veelgestelde vragen & randgevallen  

### Wat als ik meerdere rechthoeken nodig heb?  

Herhaal gewoon **Stap 2** en **Stap 3** in een lus, waarbij je `setWidth`, `setHeight` of `setFillColor` per iteratie aanpast. Zorg ervoor dat elke vorm een unieke variabelenaam krijgt of bewaar ze in een lijst.

### Kan ik exporteren naar PDF in plaats van DOCX?  

Zeker. Nadat de vorm is toegevoegd, roep je `document.save("output.pdf")` aan. Aspose.Words verzorgt de conversie en behoudt de schaduw.

### Hoe zit het met oudere Word‑versies?  

Gebruik de overload `document.save("file.doc", SaveFormat.DOC)`. De API degradeert automatisch de functies, maar let op dat sommige schaduwstijlen er iets anders uit kunnen zien in legacy‑formaten.

### Hoe verander ik de richting van de schaduw?  

Pas `setOffsetX` en `setOffsetY` aan. Een positieve X verplaatst de schaduw naar rechts, een negatieve naar links. Een positieve Y verplaatst naar beneden, een negatieve naar boven. Speel met die getallen om een lichtbron vanuit elke hoek te simuleren.

---

## Tips voor werken met vormen  

- **Vormen groeperen**: Als je een label naast de rechthoek nodig hebt, maak dan een `GroupShape` en voeg zowel de rechthoek als een `TextBox` toe.  
- **Z‑order is belangrijk**: Gebruik `shape.moveToFront()` of `shape.moveToBack()` om te bepalen welke vorm bovenop verschijnt.  
- **Prestaties**: Het toevoegen van honderden vormen kan traag zijn. Groepeer ze in één sectie en roep daarna één keer `document.updatePageLayout()` aan.

---

## Samenvatting  

We hebben behandeld hoe je een **rechthoekvorm** in een Word‑document maakt met Java, hoe je **vormschaduw** toevoegt, en hoe je het **Word‑document** opslaat met het resultaat. De volledige, uitvoerbare code staat in de bovenstaande fragmenten, en je begrijpt nu het “waarom” achter elke eigenschap—zodat je kleuren, vervaging en offsets kunt aanpassen aan elk ontwerp.

Klaar voor de volgende uitdaging? Probeer de rechthoek te combineren met een grafiek, of exporteer het bestand als PDF en bekijk hoe de schaduw wordt weergegeven. Je kunt ook **rechthoekvorm** **toevoegen** binnen tabellen voor stijlvolle rapportlay‑outs.

Veel plezier met coderen, en moge je documenten er altijd net zo scherp uitzien als je code!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}