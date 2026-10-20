---
category: general
date: 2026-10-20
description: Hoe vormen te groeperen in Aspose.Words voor Java – leer hoe je een rechthoekvorm
  invoegt, ze groepeert en het document opslaat in één handleiding.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: nl
lastmod: 2026-10-20
og_description: Hoe vormen te groeperen in Aspose.Words voor Java. Deze tutorial laat
  zien hoe je een rechthoekvorm invoegt, ze groepeert en het resultaat exporteert.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Hoe vormen groeperen in Aspose.Words voor Java – stap‑voor‑stap gids
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Hoe vormen groeperen in Aspose.Words voor Java
url: /nl/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe vormen groeperen in Aspose.Words voor Java

Als je **how to group shapes** in een Word-document wilt gebruiken met Aspose.Words for Java, laat deze gids je de volledige workflow zien. Je leert hoe je **insert rectangle shape** kunt invoegen, een tweede rechthoek toevoegt, de twee vormen groepeert, en uiteindelijk het bestand opslaat — allemaal met duidelijke, uitvoerbare code.

Vormen groeperen is handig wanneer je meerdere tekeningen als één geheel wilt verplaatsen, roteren of opmaken. Of je nu een rapporttemplate, een diagram of een aangepaste flyer maakt, het beheersen van vormgroepering bespaart tijd en houdt je lay-out consistent.

In deze tutorial leer je:

* Een nieuw `Document` en een `DocumentBuilder` maken.
* **How to insert rectangle** vormen met precieze afmetingen.
* De rechthoeken groeperen in een `GroupShape`.
* Het document opslaan en het resultaat verifiëren.

> **Voorwaarde** – Je moet Aspose.Words for Java (v23.12 of later) aan je project hebben toegevoegd. Maven‑gebruikers kunnen de onderstaande afhankelijkheid opnemen.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## Wat je nodig hebt

| Item | Reden |
|------|--------|
| Java 17+ | Moderne taalfeatures en betere prestaties |
| Aspose.Words for Java | Biedt de `DocumentBuilder`, `Shape` en `GroupShape` API's |
| An IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | Om het voorbeeld te compileren en uit te voeren |
| Write permission to a folder | Het document wordt op schijf opgeslagen |

---

## Hoe een rechthoekvorm in te voegen

De eerste stap is het maken van een `Document` en een `DocumentBuilder`. De builder biedt methoden zoals `insertShape` om tekenobjecten te plaatsen.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Waarom dit belangrijk is** – Het gebruik van `insertShape` is de standaardmethode om **how to insert rectangle** objecten in Aspose.Words in te voegen. Het voegt de vorm automatisch toe aan de huidige alinea van het document, zodat je geen low‑level OpenXML hoeft te beheren.

---

## Posities van rechthoeken aanpassen (optioneel)

Als de tweede rechthoek een aangepaste locatie ten opzichte van de eerste nodig heeft, kun je de `left`- en `top`-eigenschappen aanpassen. Deze stap is optioneel maar vaak vereist voor een precieze diagramlay-out.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Pro tip:** Alle afmetingen zijn in punten (1 pt ≈ 1/72 in). Gebruik `convertPointsToPixels` als je pixelwaarden nodig hebt voor UI‑gebaseerde berekeningen.

---

## Hoe vormen te groeperen

Nu de rechthoeken bestaan, kun je ze in een `GroupShape` plaatsen. Groeperen zorgt ervoor dat de twee rechthoeken zich gedragen als één object — verplaatsen, roteren of opmaken van de groep beïnvloedt beide vormen.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Waarom groeperen werkt** – `GroupShape` erft van `Shape`, zodat je de groep kunt behandelen als elk ander tekenobject. Wanneer je `appendChild` aanroept, worden de vormen uit hun oorspronkelijke locatie verwijderd en kinderen van de groep.

---

## Het document opslaan met de gegroepeerde vormen

Schrijf tenslotte het document naar schijf. Het bestand zal één `GroupShape` bevatten met twee rechthoeken erin.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Verwacht resultaat

Open `GroupShape.docx` in Microsoft Word:

* Je ziet twee rechthoeken (blauw en groen) naast elkaar gepositioneerd.
* Het selecteren van een van de rechthoeken selecteert de hele groep — slepen verplaatst beide samen.
* De groep heeft een dunne rode rand, wat bevestigt dat de `GroupShape`‑eigenschappen zijn toegepast.

Als je met de rechtermuisknop op de groep klikt en **Group → Ungroup** kiest, keren de rechthoeken terug naar onafhankelijke vormen, wat aantoont dat de groeperingsoperatie omkeerbaar is.

---

## Veelvoorkomende variaties en randgevallen

| Situatie | Hoe te handelen |
|-----------|------------------|
| **More than two shapes** | Insert each shape, then append all to the same `GroupShape`. |
| **Different shape types** (e.g., ellipse, picture) | Use `builder.insertShape(ShapeType.ELLIPSE, …)` or `builder.insertImage(...)` before appending. |
| **Scaling the group** | Call `group.setWidth(newWidth)` or `group.setHeight(newHeight)`; children scale proportionally. |
| **Rotating the group** | `group.setRotationAngle(45);` rotates the whole collection around its center. |
| **Preserving original positions** | Store each shape’s `left`/`top` before grouping and restore after ungrouping if needed. |

---

## Volledig, uitvoerbaar voorbeeld

Hieronder staat de volledige Java‑klasse die je kunt kopiëren en plakken in je IDE. Het bevat alle imports, foutafhandeling en commentaren voor duidelijkheid.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

Voer het programma uit, open het resulterende `GroupShape.docx`, en je ziet de gegroepeerde rechthoeken precies zoals beschreven.

---

## Conclusie

Je weet nu **how to group shapes** in Aspose.Words for Java, van het maken van een document tot het invoegen van rechthoekvormen, het aanpassen van hun posities, en uiteindelijk het groeperen met `GroupShape`. Deze techniek stelt je in staat meerdere tekeningen als één entiteit te behandelen, waardoor lay-outaanpassingen en visuele consistentie eenvoudiger worden.

**Volgende stappen**

* Verken **how to insert rectangle** vormen met verschillende vulpatronen of randen.
* Combineer **insert rectangle shape** met tekstvakken om gelabelde diagrammen te maken.
* Experimenteer met het roteren of schalen van de groep om complexere graphics te produceren.

Voel je vrij de code aan te passen voor andere vormtypen, grotere groepen, of dynamische documentgeneratiescenario's. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Rechthoekvorm invoegen in Java – Groeperen en positioneren van vormen](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [Hoe een groepvorm in Java invoegen – Complete Guide](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [Hoe schaduw instellen op een vorm in Aspose.Words – Complete Guide](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}