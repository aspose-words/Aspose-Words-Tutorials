---
category: general
date: 2026-09-24
description: Lär dig hur du skapar ett tomt Word‑dokument i Java och grupperar former
  som rektanglar och linjer med Aspose.Words. Inkluderar steg‑för‑steg‑kod.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: sv
lastmod: 2026-09-24
og_description: Skapa ett tomt Word‑dokument i Java och lär dig hur du grupperar former,
  lägger till en rektangel och ställer in formens storlek med Aspose.Words.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Skapa ett tomt Word‑dokument och gruppera former i Java – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Hur man skapar ett tomt Word‑dokument och grupperar former i Java
url: /sv/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett tomt Word‑dokument och grupperar former i Java

Om du behöver **skapa ett tomt Word‑dokument** och sedan organisera flera ritobjekt, visar den här guiden exakt hur du gör. Med Aspose.Words för Java kan du infoga en gruppform, lägga till en rektangel, rita en linje och styra varje forms storlek och position – allt i ett enda körbart program.

Du får gå igenom varje steg, från att initiera dokumentet till att spara den slutgiltiga `.docx`‑filen. I slutet förstår du **hur man grupperar former**, **lägger till rektangel** och **sätter formens storlek** så att dina Word‑filer ser ut exakt som du tänkt dig.

## Förutsättningar

- Java 17 eller senare (koden kompileras med vilken modern JDK som helst)
- Aspose.Words för Java‑biblioteket (ladda ner från [Aspose‑webbplatsen](https://products.aspose.com/words/java))
- En IDE eller ett byggverktyg (Maven/Gradle) som kan lägga till Aspose.Words‑JAR‑filen i classpath
- Grundläggande kunskaper i Java‑syntax

> **Proffstips:** Använd Maven för beroendehantering; lägg till `com.aspose:aspose-words:23.12` (eller den senaste versionen) i din `pom.xml`.

## Steg 1: Skapa ett tomt Word‑dokument

Den första uppgiften är att **skapa ett tomt Word‑dokument**. Detta ger dig en ren canvas som du senare kan infoga former i.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Varför detta är viktigt:* Ett `Document`‑objekt representerar hela `.docx`‑filen. Att börja med ett tomt dokument säkerställer att ingen dold formatering stör de former du kommer att lägga till.

## Steg 2: Infoga en gruppform – behållaren för flera objekt

En **gruppform** fungerar som en behållare som låter dig flytta, ändra storlek eller rotera flera former tillsammans. Detta är kärnan i **hur man grupperar former** i Word.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Förklaring:* Metoden `insertGroupShape` skapar ett `GroupShape`‑objekt och placerar det på den aktuella markörens position. Alla efterföljande former som du `appendChild` till den här gruppen behandlas som en enhet.

## Steg 3: Lägg till en rektangel och sätt dess storlek

Nu **lägger vi till en rektangel** i gruppen och **sätter formens storlek** exakt.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Varför du måste sätta formens storlek:* Bredd och höjd styr hur rektangeln visas på sidan. Metoderna `setLeft` och `setTop` positionerar rektangeln relativt gruppens ursprung, vilket ger dig pixel‑perfekt layoutkontroll.

## Steg 4: Lägg till en linje och konfigurera dess dimensioner

En linje är ett annat vanligt ritobjekt. Vi kommer att **lägga till rektangel‑liknande logik** på en linje, vilket visar att samma storleksprinciper gäller.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Viktigt:* Även om en linje saknar höjd använder du fortfarande `setWidth` för att definiera dess längd. Positionering (`setLeft`, `setTop`) följer samma koordinatsystem som övriga former.

## Steg 5: Spara dokumentet med grupperade former

Till sist sparar du ändringarna genom att spara dokumentet. Detta skapar en `.docx`‑fil som du kan öppna i Microsoft Word för att verifiera resultatet.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Förväntat resultat:** När du öppnar `GroupShapeDemo.docx` visas en tom sida som innehåller en grupperad rektangel och linje. Om du markerar någon av formerna markeras hela gruppen, så att du kan flytta dem tillsammans.

## Vanliga frågor och hantering av kantfall

| Fråga | Svar |
|----------|--------|
| *Kan jag lägga till fler än två former i gruppen?* | Ja. Anropa `group.appendChild(yourShape)` för varje extra form. |
| *Vad händer om jag behöver en annan enhet (t.ex. centimeter) för storlek?* | Aspose.Words använder punkter (1 punkt = 1/72 tum). Konvertera med `Points = centimeters * 28.3465`. |
| *Behåller gruppen sin layout när dokumentet öppnas på en annan maskin?* | Absolut. Alla storleks‑ och positionsdata lagras i `.docx`‑filen, vilket gör layouten portabel. |
| *Hur avgrupperar jag former senare?* | Hämta `GroupShape`‑objektet, iterera sedan över `group.getChildNodes(NodeType.SHAPE, true)` och flytta varje barn ut ur gruppen. |
| *Vad händer om jag vill rotera hela gruppen?* | Använd `group.setRotationAngle(double angleInDegrees)` innan du sparar. |

## Fullt, körbart exempel

Nedan är hela programmet som du kan kopiera och klistra in i din IDE. Det innehåller alla nödvändiga import‑satser och kommentarer.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Kör programmet, öppna `GroupShapeDemo.docx` i Microsoft Word, så ser du de grupperade formerna exakt som beskrivs.

## Slutsats

Du vet nu hur du **skapar ett tomt Word‑dokument**, **grupperar former i Word**, **lägger till rektangel** och **sätter formens storlek** med Aspose.Words för Java. Genom att placera former i ett `GroupShape` får du full kontroll över gemensam positionering, skalning och rotation – perfekt för diagram, flödesscheman eller anpassade grafikobjekt som bäddas in i automatiserade rapporter.

**Nästa steg:**  
- Utforska **hur man grupperar former** med mer komplexa objekt som bilder eller textrutor.  
- Experimentera med `setRotationAngle` för att rotera hela gruppen.  
- Kombinera denna teknik med mail‑merge för att generera personliga dokument som innehåller varumärkesgrafik.

Anpassa gärna koden för dina egna projekt och dela dina resultat i kommentarerna!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Skapa rektangel i Word med Java – Fullständig guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Skapa Word‑dokument Java – Lägg till rektangel med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Skapa gruppform i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}