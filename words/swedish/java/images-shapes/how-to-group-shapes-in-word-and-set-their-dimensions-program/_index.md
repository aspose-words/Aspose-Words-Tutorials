---
category: general
date: 2026-11-25
description: Hur man grupperar former i Word med Java och hur man anger formens dimensioner
  i en DOCX‑fil med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: sv
lastmod: 2026-11-25
og_description: Hur du grupperar former i Word med Aspose.Words Java API och snabbt
  ställer in formens storlek i Word. Följ den kompletta steg‑för‑steg‑lösningen.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Hur man grupperar former i Word och ställer in deras dimensioner – Java‑guide
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Hur man grupperar former i Word och sätter deras dimensioner programmässigt
url: /sv/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man grupperar former i Word och ställer in deras dimensioner programatiskt

Om du behöver **how to group shapes in Word** och kontrollera deras exakta storlek, visar den här guiden en komplett, körbar lösning. Med Aspose.Words for Java kan du skapa en rektangel, en ellips, lägga till dem i en `GroupShape` och sedan **how to set shape dimensions** såsom bredd och höjd i en enda DOCX-fil.

Du kommer att lära dig hur du:

* Skapar ett nytt Word-dokument från grunden.  
* Infogar en `GroupShape` (nytt API i version 24.9).  
* Lägger till en rektangel och en ellips i gruppen.  
* **Set shape size Word** exakt med `setWidth` och `setHeight`.  
* Sparar dokumentet till disk.

Ingen extern verktyg behövs—bara Java 17+, Maven och Aspose.Words for Java-biblioteket.

## Förutsättningar

* Java Development Kit 17 eller nyare.  
* Maven (eller Gradle) för beroendehantering.  
* Aspose.Words for Java 24.9 eller senare (`GroupShape`-API:t introducerades i 24.9).  
* Grundläggande kunskap om Java-syntax och objekt‑orienterade koncept.

Om du ännu inte har lagt till Aspose.Words i ditt projekt, inkludera följande Maven‑beroende:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Steg 1: Skapa ett nytt dokument och en DocumentBuilder

`Document`-klassen representerar hela Word-filen, medan `DocumentBuilder` ger ett bekvämt sätt att lägga till innehåll.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Varför detta steg?*  
Att skapa ett nytt `Document` ger dig en ren arbetsyta. `DocumentBuilder` är den hög‑nivå hjälpen som låter dig infoga stycken, tabeller och, i detta fall, former.

## Steg 2: Infoga en GroupShape (nytt API i version 24.9)

En `GroupShape` fungerar som en behållare; varje form du lägger till blir en del av samma visuella grupp.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Varför använda `GroupShape`?*  
Att gruppera former förenklar att flytta, rotera eller applicera formatering på flera objekt samtidigt. API:t lades till i 24.9, så äldre versioner kommer inte att kunna kompilera den här raden.

## Steg 3: Skapa en rektangel, sätt dess storlek och lägg till den i gruppen

Här demonstrerar vi **how to set shape dimensions** för en rektangel.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Varför sätta bredd och höjd explicit?*  
Word lagrar formens storlek i punkter. Genom att anropa `setWidth` och `setHeight` styr du det exakta visuella fotavtrycket, vilket är viktigt när du behöver exakt layout eller vid export till PDF.

## Steg 4: Skapa en ellips, sätt dess storlek och lägg till den i samma grupp

Samma **set shape size word**-teknik fungerar för alla formtyper.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Varför lägga till ellipsen i samma `GroupShape`?*  
Båda formerna kommer att röra sig tillsammans som en enhet. Detta är användbart för att skapa ikoner, logotyper eller komplexa diagram som måste förbli justerade.

## Steg 5: Spara dokumentet med de grupperade formerna

Till sist, spara DOCX-filen till disk.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

Kör du detta program får du en fil med namnet **GroupShape.docx** som innehåller en rektangel och en ellips grupperade tillsammans. När du öppnar filen i Microsoft Word kommer du att se att de två formerna beter sig som ett enda objekt—du kan dra, ändra storlek eller rotera dem tillsammans.

### Förväntat resultat

* Ett Word-dokument (`GroupShape.docx`) med en sida.  
* En `GroupShape` som innehåller en 100 × 50 pt rektangel och en 80 × 80 pt ellips.  
* Att markera någon av formerna markerar hela gruppen.

## Vanliga frågor och specialfall

### Hur ändrar man positionen för de grupperade formerna?

Efter att ha skapat `GroupShape` kan du sätta dess `left` och `top` egenskaper:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

Dessa koordinater mäts också i punkter.

### Vad händer om jag behöver lägga till fler än två former?

`GroupShape` fungerar som vilken annan behållarnod som helst. Anropa `groupShape.appendChild(yourShape)` för varje ytterligare form. API:t begränsar inte antalet barn.

### Kan jag applicera stil (fyllningsfärg, linjebredd) på enskilda former?

Ja. Varje `Shape`-objekt exponerar formateringsegenskaper:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Fungerar koden med äldre Aspose.Words-versioner?

`insertGroupShape`-metoden introducerades i version 24.9. Om du använder en tidigare version måste du skapa en `GroupShape` manuellt via nodträdet, vilket är mer komplicerat. Uppgradering är den rekommenderade vägen.

## Proffstips

* **Använd punkter för konsekvens** – Words interna enhet är punkten (1/72 tum). Konvertering från pixlar eller centimeter kan leda till oväntade storlekar.  
* **Gruppera innan positionering** – Positionera `GroupShape` efter att du har lagt till alla dess barn; annars kan du behöva räkna om offsetar.  
* **Återanvänd DocumentBuilder** – Du kan infoga flera grupper i samma dokument genom att flytta byggarens markör (`builder.moveTo`) före varje `insertGroupShape`‑anrop.

## Slutsats

Du har nu ett komplett, end‑to‑end‑exempel på **how to group shapes in Word** och **how to set shape dimensions** med Aspose.Words for Java. Handledningen täckte att skapa ett dokument, infoga en `GroupShape`, lägga till en rektangel och en ellips, sätta deras exakta storlek och spara resultatet.  

Härifrån kan du utforska:

* Att lägga till textrutor eller bilder i samma grupp.  
* Att animera grupperade former med Words smart‑art‑funktioner (via API:t).  
* Att exportera de grupperade formerna till PDF eller SVG för webbbruk.

Känn dig fri att experimentera med olika formtyper, storlekar och positioner—gruppering ger dig kraftfull kontroll över komplexa layouter i Word-dokument.

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man skapar ett tomt Word-dokument och grupperar former i Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [Hur man grupperar former i Word med Java – komplett guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}