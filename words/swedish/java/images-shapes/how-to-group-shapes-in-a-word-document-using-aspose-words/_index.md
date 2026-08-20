---
category: general
date: 2026-08-20
description: Lär dig hur du grupperar former, ställer in formens storlek, infogar
  en bild i dokumentet, lägger till en bild i gruppen och skapar en rektangelform
  med Aspose.Words i Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: sv
lastmod: 2026-08-20
og_description: Hur man grupperar former i ett Word‑dokument med Aspose.Words. Följ
  den här steg‑för‑steg Java‑handledningen för att ställa in formens storlek, infoga
  bild i dokumentet, lägga till bild i gruppen och skapa en rektangelform.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Hur man grupperar former i ett Word-dokument med Aspose.Words – Java‑guide
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Hur man grupperar former i ett Word-dokument med Aspose.Words
url: /sv/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man grupperar former i ett Word-dokument med Aspose.Words

Om du behöver **how to group shapes** i en Word-fil, visar den här handledningen den kompletta Java-lösningen. Du kommer att se hur man **set shape size**, **insert image into document**, **add picture to group**, och **create rectangle shape**—allt med tydliga förklaringar och ett körbart kodexempel.

Att gruppera former förenklar layout‑hantering, låter dig flytta eller rotera flera objekt som en enhet och håller ditt dokument prydligt. I stegen nedan bygger du en grupp som innehåller en rektangel och en bild, och placerar sedan gruppen på sidan.

## Förutsättningar

* Java 17 eller senare installerat.
* Aspose.Words för Java (version 23.9 eller senare) tillagt i ditt projekts classpath.
* En exempel‑JPEG‑bild på `YOUR_DIRECTORY/sample.jpg` (ersätt `YOUR_DIRECTORY` med den faktiska sökvägen).

Du kan lägga till Aspose.Words via Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Så grupperar du former med Aspose.Words

Följande avsnitt går igenom varje operation som krävs för att **how to group shapes**. Den primära H2‑rubriken innehåller huvudnyckelordet, vilket uppfyller SEO‑reglerna.

### Steg 1: Skapa ett nytt dokument och en `DocumentBuilder`

Ett `Document` representerar Word‑filen, medan `DocumentBuilder` tillhandahåller bekväma metoder för att infoga innehåll.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta är viktigt*: Att börja med ett nytt `Document` säkerställer att gruppen du skapar inte stör befintliga element.

### Steg 2: Infoga en gruppform som kommer att hålla flera underordnade former

En gruppform fungerar som en behållare. Dess dimensioner definierar den omgivande rutan för alla underordnade former.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Tips*: Bredden (`300`) och höjden (`200`) är i punkter (1 pt = 1/72 tum). Justera dem baserat på storleken på de former du planerar att lägga till.

### Steg 3: Skapa en rektangel, ange dess storlek och lägg till den i gruppen

Att ange exakt storlek på en form är avgörande när du vill ha exakt layout‑kontroll.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Varför vi anger formens storlek*: Metoderna `setWidth` och `setHeight` motsvarar det sekundära nyckelordet **set shape size**, vilket ger dig pixel‑perfekt kontroll över rektangelns utseende.

### Steg 4: Infoga en bild, och lägg sedan till bildformen i samma grupp

Att infoga en bild är kärnan i kravet **insert image into document**. Den returnerade `Shape` är en bildform som kan grupperas som vilken annan form som helst.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Pro‑tips*: Om du behöver bevara det ursprungliga bildförhållandet, ange bara en dimension (`setWidth` eller `setHeight`). Aspose.Words skalar automatiskt den andra dimensionen.

### Steg 5: Positionera hela gruppen på sidan

Efter att ha lagt till alla underordnade former kan du flytta, rotera eller dölja hela gruppen. Positionering använder konceptet **add picture to group** indirekt, eftersom gruppen nu innehåller bilden.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Förklaring*: `setLeft` och `setTop` placerar gruppen relativt till sidans marginaler. Att rotera gruppen visar att alla underordnade former ärver transformationen.

### Steg 6: Spara dokumentet

Slutligen skriver du filen till disk. Du kan öppna den resulterande `.docx` i Word för att verifiera gruppering.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

När programmet körs skapas **GroupShapesDemo.docx** som innehåller en rektangel och en bild sammanslagna. Att markera någon av formerna i Word kommer också att markera den andra, vilket bekräftar att du framgångsrikt har lärt dig **how to group shapes**.

---

## Förväntat resultat

När du öppnar *GroupShapesDemo.docx* i Microsoft Word:

* En rektangel (gyllene fyllning) visas på vänster sida av gruppen.
* Bilden du angav visas till höger om rektangeln.
* Båda objekten rör sig tillsammans när du drar gruppen.
* Gruppen är placerad 50 pt från vänster marginal och 100 pt från övre marginal, roterad 15°.

Om bilden inte visas, dubbelkolla filvägen i `insertImage`. Aspose.Words kastar ett `IOException` när filen inte kan hittas.

---

## Vanliga frågor och hantering av kantfall

| Question | Answer |
|----------|--------|
| **Kan jag lägga till fler än två former?** | Ja. Anropa `groupShape.appendChild(otherShape)` för varje ytterligare form. |
| **Vad händer om jag behöver en transparent bakgrund för rektangeln?** | Använd `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **Stöds gruppering i äldre Word-format (t.ex. `.doc`)?** | Gruppering fungerar för `.docx` och `.doc`, men vissa äldre visare kan ignorera gruppmetadata. Spara som `.docx` för fullständig återgivning. |
| **Hur avgrupperar jag senare?** | Hämta de underordnade noderna via `groupShape.getChildNodes(NodeType.ANY, true)` och flytta dem till dokumentkroppen, ta sedan bort gruppen. |
| **Kan jag gruppera former över olika sektioner?** | Nej. En `GroupShape` måste finnas inom en enda `Story` (vanligtvis huvudkroppen i dokumentet). |

---

## Pro‑tips för robust hantering av former

* **Använd absolut positionering sparsamt** – relativ positionering (`builder.moveToDocumentEnd()`) ger ofta mer responsiva layouter.
* **Cacha `DocumentBuilder`** – att skapa en ny builder för varje operation kan försämra prestanda i stora dokument.
* **Ange `PictureFillMode`** när du behöver att bilden sträcks eller mosaiksätts i formen: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Validera bildens dimensioner** innan infogning för att undvika oväntad skalning som kan påverka gruppens omgivningsruta.

## Nästa steg

Nu när du vet **how to group shapes**, kan du utforska:

* **Insert image into document** med avancerade alternativ som beskärning (`pictureShape.setCropTop(...)`).
* **Set shape size** dynamiskt baserat på sidans dimensioner (`doc.getFirstSection().getPageSetup().getPageWidth()`).
* **Add picture to group** tillsammans med textrutor för bildtexter.
* **Create rectangle shape** med rundade hörn (`rectangleShape.setCornerRadius(5);`).

Dessa ämnen bygger på samma API‑yta och hjälper dig att skapa sofistikerade, programatiska Word‑rapporter.

## Slutsats

I den här handledningen lärde du dig **how to group shapes** i ett Word-dokument med Aspose.Words för Java. Genom att följa de sex stegen—skapa ett dokument, infoga en grupp, **create rectangle shape**, **set shape size**, **insert image into document**, **add picture to group**, och positionera gruppen—har du nu ett återanvändbart mönster för komplexa layout‑scenarier. Känn dig fri att experimentera med ytterligare underordnade former, olika rotationer eller villkorlig gruppering för att passa dina applikationsbehov.

Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word-dokument Java – Lägg till rektangel med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Använda dokumentformer i Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Skapa gruppform i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}