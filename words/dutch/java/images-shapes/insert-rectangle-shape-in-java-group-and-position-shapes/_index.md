---
category: general
date: 2026-07-26
description: Voeg een rechthoekvorm in Java toe met Aspose.Words. Leer hoe je de vormgrootte
  instelt, de vorm positioneert en hoe je vormen groepeert in een DOCX‑bestand.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: nl
lastmod: 2026-07-26
og_description: Voeg een rechthoekvorm in Java toe om rijke DOCX‑graphics te maken.
  Volg deze stapsgewijze handleiding om de vormgrootte in te stellen, de vorm te positioneren
  en vormen moeiteloos te groeperen.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Rechthoekvorm invoegen in Java – Beheers groeperen en positioneren
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Rechthoekvorm invoegen in Java – Groepeer en positioneer vormen
url: /nl/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm invoegen in Java – Groeperen en positioneren van vormen

Heb je ooit **insert rectangle shape** nodig gehad in een Word-document terwijl je Java-code schrijft? Je bent niet de enige—ontwikkelaars die rapporten, facturen of aangepaste sjablonen bouwen, lopen hier voortdurend tegenaan. Het goede nieuws is dat je met een paar regels Aspose.Words for Java kunt **insert rectangle shape**, **set shape size**, **position shape**, en zelfs **how to group shapes** zodat ze als één geheel bewegen.

In deze gids lopen we het volledige proces door, van het maken van een leeg document tot het opslaan van een `.docx` dat twee rechthoeken netjes gegroepeerd bevat. Aan het einde weet je **how to add rectangle** objecten, hun afmetingen te controleren, ze precies te plaatsen waar je wilt, en ze te bundelen in een herbruikbare groep. Er zijn geen externe bibliotheken nodig buiten Aspose.Words, en de code werkt met Java 8‑plus.

## Vereisten

- Java 8 of nieuwer geïnstalleerd (ik gebruik JDK 17, maar alles wat Maven ondersteunt werkt)
- Aspose.Words for Java 23.9 of later – voeg de dependency toe aan je `pom.xml` of download de JAR
- Een basisbegrip van Java-syntaxis (als je een `main`‑methode kunt schrijven, ben je klaar)
- Een IDE of teksteditor naar keuze (IntelliJ IDEA, Eclipse, VS Code…)

> **Pro tip:** Als je Maven gebruikt, ziet de dependency er als volgt uit:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Nu we de basis hebben gelegd, laten we in de code duiken.

## Rechthoekvorm invoegen en de grootte instellen

Het eerste wat je doet, is een nieuw `Document` en een `DocumentBuilder` aanmaken. De builder is je “pen” die vormen op de pagina tekent. Hieronder **insert rectangle shape** en stellen we meteen **set shape size** in op 100 × 80 punten.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Let op hoe de `setWidth`/`setHeight`‑aanroepen **set shape size** in punten (1 pt ≈ 1/72 inch). Je kunt ook `setSize` gebruiken als je één methode verkiest, maar de expliciete aanroepen maken de intentie glashelder.

## Vorm positioneren op de pagina

Nadat we de eerste rechthoek hebben, moeten we de tweede **position shape** zodat deze niet overlapt met de eerste. Positioneren werkt op dezelfde manier: je stelt de `Left`‑ en `Top`‑eigenschappen in ten opzichte van de oorsprong van de groep.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

Als je je afvraagt waarom we `setLeft` gebruiken in plaats van `setX`, is dat omdat Aspose.Words het klassieke Windows GDI‑coördinatensysteem hanteert—`Left` is de horizontale offset, `Top` de verticale offset. Het aanpassen van deze waarden stelt je in staat de lay-out fijn af te stemmen zonder te rommelen met tabellen of alinea's.

## Hoe vormen groeperen

Je vraagt je misschien af: “Waarom in hemelsnaam een groep?” Groeperen is logisch wanneer je wilt dat vormen samen bewegen, als één geheel roteren, of een gemeenschappelijke stijl delen. In het bovenstaande fragment hebben we al een `GroupShape` gemaakt via `builder.insertGroupShape`. Dat object is in wezen een container—denk aan een map die andere vormbestanden bevat.

> **Waarom dit belangrijk is:** Als je later besluit een bijschrift toe te voegen of het hele diagram te roteren, hoef je alleen de groep aan te passen, niet elke rechthoek afzonderlijk.

## Hoe een rechthoek aan een groep toevoegen

Het toevoegen van **how to add rectangle** aan de groep gebeurt simpelweg door `group.appendChild(rectangle)` aan te roepen. Intern werkt Aspose.Words de interne collectie van de groep bij en berekent automatisch de omhullende rechthoek opnieuw zodat de groep nog steeds binnen de opgegeven breedte en hoogte past.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

Je kunt experimenteren met andere `ShapeType`s—`ShapeType.ELLIPSE`, `ShapeType.TRIANGLE`, enz.—en hetzelfde `appendChild`‑patroon werkt.

## Document opslaan

Tot slot slaan we het document op schijf op. Het pad kan absoluut of relatief zijn; zorg er gewoon voor dat de map bestaat.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

Wanneer je `GroupShape.docx` opent in Microsoft Word, zie je twee rechthoeken naast elkaar, beide vergrendeld binnen een lichtgrijze doos. Het selecteren van de grijze doos markeert beide rechthoeken tegelijk—bewijs dat **how to group shapes** echt werkt.

![Gegroepeerde rechthoeken in een Word‑document](placeholder-image.png){: .center-image alt="Voorbeeld van insert rectangle shape met twee rechthoeken gegroepeerd in een door Java gegenereerd DOCX‑bestand"}

*Afbeeldings‑alt‑tekst (SEO):* **insert rectangle shape example showing two rectangles grouped in a Java‑generated DOCX file**.

## Verwachte output

- Een `GroupShape.docx`‑bestand in de `output`‑map.
- In het document: een 400 × 200 pt‑groep die twee rechthoeken bevat (100 × 80 pt en 120 × 60 pt) gepositioneerd op (20, 30) en (150, 50) respectievelijk.
- De groep heeft een dunne zwarte rand en een lichtgrijze vulling, waardoor de groepering visueel duidelijk is.

Open het bestand en probeer de grijze doos te slepen—beide rechthoeken moeten samen bewegen. Als dat niet gebeurt, controleer dan of je `group.appendChild` voor elke vorm hebt aangeroepen.

## Veelvoorkomende valkuilen & randgevallen

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **Rechthoeken verschijnen buiten de pagina** | `Left`/`Top`‑waarden overschrijden de afmetingen van de groep | Vergroot de groepsgrootte (`insertGroupShape(width, height)`) of verklein de offsets |
| **Groep verdwijnt na opslaan** | De `Width`/`Height` van de groep zijn ingesteld op 0 | Geef niet‑nul afmetingen op bij het aanroepen van `insertGroupShape` |
| **Vormkleuren zien er verkeerd uit** | Standaardvulling is transparant; Word kan het weergeven als wit | Stel expliciet `setFillColor` in of gebruik `ShapeStyle` |
| **Uitzondering `ArgumentOutOfRangeException`** | Gebruik van negatieve coördinaten | Houd `Left` en `Top` niet‑negatief |

Deze vroeg aanpakken bespaart je de “waarom verdwijnt mijn vorm?”‑hoofdpijn die veel nieuwkomers ervaren.

## Samenvatting & volgende stappen

We hebben de volledige levenscyclus van **insert rectangle shape** in Java behandeld: een document maken, **set shape size**, **position shape**, **how to group shapes**, en **how to add rectangle** aan die groep. Het volledige, uitvoerbare voorbeeld staat in het code‑blok hierboven, en je kunt het direct in een Maven‑project plakken om het resultaat te zien.

Wat is het volgende? Overweeg te experimenteren met:

- Tekst toevoegen binnen elke rechthoek via

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}