---
category: general
date: 2026-10-20
description: Hur man grupperar former i Aspose.Words för Java – lär dig hur du infogar
  en rektangel, grupperar dem och sparar dokumentet i en enda guide.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: sv
lastmod: 2026-10-20
og_description: Hur man grupperar former i Aspose.Words för Java. Denna handledning
  visar hur man infogar en rektangel, grupperar dem och exporterar resultatet.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Hur man grupperar former i Aspose.Words för Java – steg‑för‑steg guide
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
title: Hur man grupperar former i Aspose.Words för Java
url: /sv/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man grupperar former i Aspose.Words för Java

Om du behöver **hur man grupperar former** i ett Word‑dokument med Aspose.Words för Java, visar den här guiden hela arbetsflödet. Du kommer att lära dig hur du **infogar rektangelform**, lägger till en andra rektangel, grupperar de två formerna och slutligen sparar filen – allt med tydlig, körbar kod.

Att gruppera former är användbart när du vill flytta, rotera eller formatera flera ritningar som en enhet. Oavsett om du bygger en rapportmall, ett diagram eller en anpassad flyer, sparar kunskapen om formgruppering tid och håller layouten konsekvent.

I den här handledningen kommer du att:

* Skapa ett nytt `Document` och en `DocumentBuilder`.
* **Hur man infogar rektangel**‑former med exakta dimensioner.
* Gruppera rektanglarna i ett `GroupShape`.
* Spara dokumentet och verifiera resultatet.

> **Förutsättning** – Du måste ha Aspose.Words för Java (v23.12 eller senare) tillagt i ditt projekt. Maven‑användare kan inkludera beroendet som visas nedan.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## Vad du behöver

| Artikel | Orsak |
|------|--------|
| Java 17+ | Moderna språkfunktioner och bättre prestanda |
| Aspose.Words for Java | Tillhandahåller `DocumentBuilder`, `Shape` och `GroupShape` API:er |
| En IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | För att kompilera och köra exemplet |
| Skrivbehörighet till en mapp | Dokumentet kommer att sparas på disk |

---

## Hur man infogar rektangelform

Det första steget är att skapa ett `Document` och en `DocumentBuilder`. Buildern ger dig metoder som `insertShape` för att placera ritobjekt.

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

> **Varför detta är viktigt** – Att använda `insertShape` är det standardmässiga sättet **hur man infogar rektangel**‑objekt i Aspose.Words. Det lägger automatiskt till formen i dokumentets aktuella stycke, så du behöver inte hantera låg‑nivå OpenXML.

---

## Justera rektangelpositioner (valfritt)

Om den andra rektangeln behöver en anpassad placering i förhållande till den första, kan du ändra dess `left`‑ och `top`‑egenskaper. Detta steg är valfritt men ofta nödvändigt för exakt diagramlayout.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Proffstips:** Alla mått är i punkter (1 pt ≈ 1/72 in). Använd `convertPointsToPixels` om du behöver pixelvärden för UI‑baserade beräkningar.

---

## Hur man grupperar former

Nu när rektanglarna finns, kan du placera dem i ett `GroupShape`. Gruppering får de två rektanglarna att bete sig som ett enda objekt – att flytta, rotera eller formatera gruppen påverkar båda formerna.

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

> **Varför gruppering fungerar** – `GroupShape` ärver från `Shape`, så du kan behandla gruppen exakt som vilket annat ritobjekt som helst. När du anropar `appendChild` tas formerna bort från sin ursprungliga plats och blir barn till gruppen.

---

## Spara dokumentet som innehåller de grupperade formerna

Slutligen skriver du dokumentet till disk. Filen kommer att innehålla ett enda `GroupShape` med två rektanglar inuti.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Förväntat resultat

Öppna `GroupShape.docx` i Microsoft Word:

* Du kommer att se två rektanglar (blå och grön) placerade sida‑vid‑sida.
* Att markera någon av rektanglarna markerar hela gruppen – att dra flyttar båda tillsammans.
* Gruppen har en tunn röd kant, vilket bekräftar att `GroupShape`‑egenskaperna har tillämpats.

Om du högerklickar på gruppen och väljer **Group → Ungroup**, återgår rektanglarna till oberoende former, vilket visar att gruppering kan ångras.

---

## Vanliga variationer och kantfall

| Situation | Hur man hanterar det |
|-----------|----------------------|
| **Mer än två former** | Infoga varje form och lägg sedan till alla i samma `GroupShape`. |
| **Olika formtyper** (t.ex. ellips, bild) | Använd `builder.insertShape(ShapeType.ELLIPSE, …)` eller `builder.insertImage(...)` innan du lägger till dem. |
| **Skala gruppen** | Anropa `group.setWidth(newWidth)` eller `group.setHeight(newHeight)`; barnen skalas proportionellt. |
| **Rotera gruppen** | `group.setRotationAngle(45);` roterar hela samlingen kring dess centrum. |
| **Bevara ursprungliga positioner** | Spara varje forms `left`/`top` innan gruppering och återställ efter avgruppering om så behövs. |

---

## Fullt, körbart exempel

Nedan är den kompletta Java‑klassen som du kan kopiera‑klistra in i din IDE. Den innehåller alla imports, felhantering och kommentarer för tydlighet.

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

Kör programmet, öppna den resulterande `GroupShape.docx`, och du kommer att se de grupperade rektanglarna exakt som beskrivits.

---

## Slutsats

Du vet nu **hur man grupperar former** i Aspose.Words för Java, från att skapa ett dokument till att infoga rektangelformer, justera deras positioner och slutligen gruppera dem med `GroupShape`. Denna teknik låter dig behandla flera ritningar som en enda enhet, vilket förenklar layoutjusteringar och visuell konsistens.

**Nästa steg**

* Utforska **hur man infogar rektangel**‑former med olika fyllningsmönster eller kanter.
* Kombinera **infoga rektangelform** med textrutor för att skapa märkta diagram.
* Experimentera med att rotera eller skala gruppen för att skapa mer komplex grafik.

Känn dig fri att anpassa koden för andra formtyper, större grupper eller dynamiska dokumentgenereringsscenarier. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Infoga rektangelform i Java – Gruppera och placera former](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [hur man infogar gruppform i Java – Komplett guide](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [Hur man sätter skugga på en form i Aspose.Words – Komplett guide](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}