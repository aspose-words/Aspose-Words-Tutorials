---
category: general
date: 2026-10-13
description: Lär dig hur du skapar grupperade former i Word med Java. Den här guiden
  visar hur du infogar en gruppform, lägger till en linje i gruppen och grupperar
  flera former i hela Word‑dokumentet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: sv
lastmod: 2026-10-13
og_description: Skapa grupperade former i Word med Java. Följ den här kompletta handledningen
  för att infoga en gruppform, lägga till en linje i gruppen och gruppera flera former
  i Word‑dokument.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Skapa grupperade former i Word med Java – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Hur man skapar grupperade former i ett Word‑dokument med Java
url: /sv/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar grupperade former i ett Word‑dokument med Java

Om du behöver **create grouped shapes** i en Microsoft Word‑fil från Java, guidar den här handledningen dig genom hela processen. Du kommer att se hur man **insert group shape**, placerar en rektangel och en linje i samma behållare, och slutligen sparar dokumentet med de grupperade grafikerna.

Att gruppera former gör det enkelt att flytta, ändra storlek eller formatera flera ritobjekt som en enhet – perfekt för diagram, flödesscheman eller anpassade siddekorationer. I slutet av den här guiden kommer du att kunna **add line to group**, **group multiple shapes word** dokument, och återanvända samma teknik för valfritt antal former.

## Förutsättningar

- Java 17 eller senare installerat på din utvecklingsmaskin.  
- En Aspose.Words for Java‑licens (eller en gratis utvärdering).  
- Ett Maven‑ eller Gradle‑projekt där du kan lägga till Aspose.Words‑beroendet:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

Inga ytterligare bibliotek krävs.

## Steg 1: Infoga gruppformens behållare

Det första steget är att **insert group shape** i dokumentet. Denna behållare kommer att hålla alla efterföljande former.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` skapar ett tomt `Shape`‑objekt av typen `GROUPSHAPE`. Tänk på det som en transparent duk som kan innehålla andra ritobjekt.

## Steg 2: Lägg till en rektangel i gruppen

En rektangel fungerar ofta som den visuella bakgrunden för en grupp former.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

Att sätta `Left` och `Top` till `0` placerar rektangeln i gruppens övre‑vänstra hörn. Du kan ändra dessa värden för att förskjuta formen inom gruppen.

## Steg 3: **Add line to group** – skapa en linjeform

Nu **add line to group**. Linjen kommer att visas under rektangeln.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

`Top`‑egenskapen flyttar linjen 60 punkter under rektangeln, vilket skapar en enkel staplad layout. Du kan också sätta `Left` om du behöver horisontell förskjutning.

## Steg 4: Spara dokumentet med de grupperade formerna

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

När du öppnar `GroupShapeDemo.docx` i Microsoft Word kommer du att se en enda grupp som innehåller både rektangeln och linjen. Att markera gruppen låter dig flytta båda formerna tillsammans, vilket visar att du framgångsrikt har **group multiple shapes word**.

## Fullt, körbart exempel

Nedan är det kompletta programmet med alla import‑ och felhanteringsrutiner. Kopiera det till din IDE, ersätt `YOUR_DIRECTORY` med en befintlig mappväg, och kör.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Förväntat resultat

- En fil med namnet `GroupShapeDemo.docx` skapas i mål‑mappen.  
- När du öppnar filen i Word visas ett enda grupperat objekt som innehåller en rektangel överst och en linje under den.  
- När du drar i gruppen flyttas båda formerna tillsammans, vilket bekräftar att du har **created grouped shapes** framgångsrikt.

## Tips och vanliga fallgropar

- **Pro tip:** Om du behöver rotera eller formatera enskilda former i gruppen, anropa respektive set‑metoder (`setRotation`, `getFill().setForeColor` osv.) innan du lägger till dem i gruppen. Gruppen bevarar dessa visuella egenskaper.  
- **Watch out for:** Att glömma att sätta `Top`‑egenskapen för linjen kan göra att den överlappar rektangeln, vilket får gruppen att se rörig ut.  
- **Edge case:** När du lägger till fler än två former, kom ihåg att varje barns koordinater är relativa till gruppens ursprung (0,0). Planera layouten därefter.  
- **Performance note:** Att gruppera ett stort antal former (hundratals) kan öka filstorleken något, men det förenklar senare redigering i Word.

## Hur man **group multiple shapes word** dokument programatiskt

Mönstret ovan – skapa en gruppbehållare, konfigurera varje barnform och lägg till den – fungerar för valfritt antal former: cirklar, bilder, textrutor osv. Upprepa helt enkelt stegen “create shape → set properties → append” innan du anropar `doc.save()`.

Om du behöver **add line to group** efter att gruppen redan innehåller andra former, kan du hämta den befintliga gruppen med:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

Detta visar att du kan modifiera en grupp när som helst under dokumentets livscykel.

## Slutsats

Du vet nu hur du **create grouped shapes** i ett Word‑dokument med Java och Aspose.Words. Genom att **insert group shape**, **add line to group** och **group multiple shapes word** kan du bygga komplexa ritningar som beter sig som ett enda objekt – idealiskt för diagram, mallar och automatiserad rapportgenerering.

Nästa steg, utforska dessa relaterade ämnen:

- **Applying styles to grouped shapes** – lär dig hur du sätter fyllningsfärger, kanter och effekter för alla barn på en gång.  
- **Exporting grouped shapes to PDF** – se hur samma grupp bevaras när du konverterar dokumentet.  
- **Animating shapes with VBA** – kombinera Java‑genererade grupper med Word‑makron för interaktiva dokument.

Känn dig fri att experimentera med olika formtyper, storlekar och positioner. Gruppering ger dig flexibiliteten att behandla många objekt som ett, vilket förenklar både kod och användarinteraktion. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}