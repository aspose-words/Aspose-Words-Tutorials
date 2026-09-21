---
category: general
date: 2026-09-21
description: Skapa ett Word‑dokument programatiskt med Java. Lär dig hur du grupperar
  former i Word, infogar en rektangel, ställer in formens storlek och lägger till
  former i ett Word‑dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: sv
lastmod: 2026-09-21
og_description: 'Skapa Word-dokument programatiskt med Java: den här guiden visar
  hur du grupperar former i Word, infogar rektangelformer, ställer in formens storlek
  och lägger till former i ett Word-dokument.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Skapa Word-dokument programatiskt, gruppera former i Java
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Skapa Word-dokument programatiskt, gruppera former i Java
url: /sv/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument programatiskt, gruppera former i Java

Om du behöver **skapa Word-dokument programatiskt**, guidar den här handledningen dig genom en komplett lösning. Du kommer att se hur du **grupperar former i Word**, infogar en rektangel, ställer in dess storlek och lägger till andra former – allt med Java och Aspose.Words for Java-biblioteket.

Handledningen täcker varje steg från projektuppsättning till att spara den färdiga .docx-filen. I slutet kommer du att kunna generera ett Word-dokument som innehåller en rektangel och en bild inneslutna i en enda grupp, vilket gör det enkelt att flytta eller ändra storlek på dem tillsammans. Ingen tidigare erfarenhet av Aspose.Words API krävs, men du bör ha en grundläggande Java‑utvecklingsmiljö.

## Förutsättningar

* Java Development Kit (JDK) 8 eller nyare  
* Maven eller Gradle för beroendehantering  
* Aspose.Words for Java 23.9 (eller den senaste versionen) – biblioteket är gratis för utvärdering  
* En bildfil (t.ex. `sample.jpg`) placerad i en känd katalog  

Att ha dessa saker redo säkerställer att koden körs utan ytterligare konfiguration.

## Steg 1: Ställ in projektet och importera Aspose.Words

Skapa ett Maven‑projekt (eller lägg till beroendet i din befintliga `pom.xml`):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Om du föredrar Gradle, lägg till följande i `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

När beroendet har lösts, importera de nödvändiga klasserna i din Java‑källfil:

```java
import com.aspose.words.*;
import java.io.File;
```

## Steg 2: Skapa Word-dokumentet programatiskt

Den första operationen i alla automationsscenario är att instansiera ett `Document`‑objekt och en `DocumentBuilder`. Buildern förenklar insättning av text, bilder och former.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

På den här punkten finns dokumentet bara i minnet. Du kan nu börja lägga till former.

## Steg 3: Infoga en rektangel – hur man infogar en rektangel

En rektangel är en grundläggande `Shape` med `ShapeType.RECTANGLE`. Du styr dess dimensioner med `setWidth`, `setHeight` och placerar den med `setTop` och `setLeft`.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Varför detta är viktigt:** Att ställa in storlek och position explicit (`set shape size word`) garanterar att rektangeln visas exakt där du förväntar dig, oavsett dokumentets standardlayout.

## Steg 4: Infoga en bild – lägg till former i Word-dokument

`DocumentBuilder` kan infoga en bild direkt från en filsökväg. Efter insättningen kan du omplacera bilden precis som någon annan form.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

Både rektangeln och bilden är nu oberoende former i dokumentet.

## Steg 5: Gruppera former – hur man grupperar former i Word

Att gruppera former är användbart när du vill flytta eller ändra storlek på dem som en enhet. Aspose.Words tillhandahåller en `GroupShape`‑behållare för detta ändamål.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

När gruppen sparas behandlar Word de två barnen som ett logiskt objekt. Du kan senare markera gruppen och dra den, och både rektangeln och bilden följer med.

## Steg 6: Spara dokumentet

Skriv slutligen dokumentet till disk. Sökvägen måste vara skrivbar för Java‑processen.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Att köra `main`‑metoden producerar en fil med namnet **GroupShapeExample.docx**. Öppna den i Microsoft Word för att se en rektangel och en bild låsta tillsammans i en grupp. När du markerar gruppen kan du flytta båda objekten samtidigt, vilket bekräftar att gruppering lyckades.

## Förväntat resultat

* En Word‑fil (`GroupShapeExample.docx`) placerad i den katalog du angav.  
* I filen visas en rektangel (ljusgrå fyllning) i övre‑vänstra hörnet, och bilden ligger direkt under den.  
* Båda objekten är en del av en enda grupp, så att dra det ena flyttar det andra.

## Vanliga variationer och kantfall

| Situation | Rekommendation |
|-----------|----------------|
| **Olika bildformat** | Aspose.Words stöder PNG, BMP, GIF och TIFF. Använd rätt filändelse i `insertImage`. |
| **Negativa dimensioner** | API:et kastar `ArgumentException`. Validera alltid bredd och höjd innan du anropar `setWidth` / `setHeight`. |
| **Stora dokument** | Att gruppera många former kan öka filstorleken. Överväg att slå ihop former till en enda bild när prestanda är viktigt. |
| **Kompatibilitet med Word-versioner** | GroupShape fungerar med Word 2007 (`.docx`) och senare. För äldre `.doc`‑filer kommer gruppen att plattas ut. |
| **Dynamisk positionering** | Använd beräkningar baserade på sidstorlek (`doc.getFirstSection().getPageSetup().getPageWidth()`) om du behöver adaptiv placering. |

**Proffstips:** Efter att du har skapat gruppen kan du ändra

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word-dokument Java – Lägg till rektangel med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Skapa rektangel i Word med Java – Fullständig guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Skapa gruppform i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}