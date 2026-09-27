---
category: general
date: 2026-09-27
description: Skapa ett tomt Word‑dokument i Java och gruppera former med Aspose.Words.
  Lär dig att ange formens storlek, ange formens fyllningsfärg och lägga till ett
  barn i gruppen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: sv
lastmod: 2026-09-27
og_description: Skapa ett tomt Word‑dokument i Java med Aspose.Words. Den här handledningen
  visar hur man grupperar former i Word, ställer in formens storlek, sätter fyllningsfärg
  för formen och lägger till ett barn i gruppen.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Skapa ett tomt Word‑dokument och gruppera former i Java – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Hur man skapar ett tomt Word‑dokument och grupperar former i Java
url: /sv/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så skapar du ett tomt Word‑dokument och grupperar former i Java

Om du behöver **skapa ett tomt Word‑dokument** programatiskt visar den här guiden exakt hur du gör det med Aspose.Words for Java. Du får också lära dig att **gruppera former i Word**, ange varje forms storlek, applicera en fyllningsfärg och **lägga till ett barn i gruppen** så att objekten beter sig som en enhet.

Att arbeta med Word‑filer från kod sparar dig från manuellt formatering och gör det möjligt att automatiskt generera rapporter, kontrakt eller marknadsföringsbroschyrer. I slutet av den här handledningen har du ett körbart Java‑program som producerar en `.docx`‑fil som innehåller en blå rektangel och en bild, båda grupperade tillsammans.

## Förutsättningar

Innan du börjar, se till att du har:

- Java 17 (eller någon nyare JDK) installerad.
- Maven eller Gradle för att hantera beroenden.
- En Aspose.Words for Java‑licens (den kostnadsfria utvärderingen fungerar för testning).
- En exempelbildfil (t.ex. `sample.jpg`) placerad i en mapp som du kan referera till från koden.

> **Pro tip:** Håll dina bildfiler i en `resources`‑katalog och ladda dem med `ClassLoader.getResourceAsStream` för att undvika hårdkodade absoluta sökvägar.

## Steg 1: Skapa ett tomt Word‑dokument och lägg till en GroupShape

Det första steget är att instansiera ett nytt `Document`‑objekt, som representerar en tom Word‑fil, och sedan infoga en `GroupShape`. Gruppen fungerar som en behållare för alla former du lägger till senare.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Varför detta är viktigt:* En `GroupShape` låter dig flytta, rotera eller formatera flera former tillsammans, vilket är avgörande för komplexa layouter som diagram eller vattenstämplar.

## Steg 2: Infoga en rektangel och **ange formens storlek**

Skapa nu en rektangel, definiera dess dimensioner och lägg till den i gruppen. Detta demonstrerar operationen **ange formens storlek**.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Förklaring:* `setWidth` och `setHeight` styr den exakta storleken på formen i punkter (1 punkt = 1/72 tum). Justera dessa värden för att passa dina layout‑krav.

## Steg 3: **Ange formens fyllningsfärg** för rektangeln

Rektangelns bakgrund sätts till blå med `setFillColor`. Du kan använda vilken `java.awt.Color`‑konstant som helst eller skapa en egen RGB‑färg.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Varför det är användbart:* Fyllningsfärger hjälper till att visuellt särskilja objekt, särskilt när du senare exporterar dokumentet till PDF eller skriver ut det.

## Steg 4: Infoga en bild och **lägg till ett barn i gruppen**

Lägg nu till en bild i samma `GroupShape`. Bilden infogas via `DocumentBuilder.insertImage`, och sedan läggs den till i gruppen så att den flyttas tillsammans med rektangeln.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Edge case:* Om bildsökvägen är felaktig kastar Aspose.Words ett `FileNotFoundException`. Använd en relativ sökväg eller ladda bilden från resurser för att undvika detta problem.

## Steg 5: **Spara dokumentet med de grupperade formerna**

Till sist skriver du dokumentet till disk. Den resulterande filen kommer att innehålla rektangeln och bilden grupperade tillsammans.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Förväntat resultat

- En fil med namnet `GroupShape.docx` visas i den angivna katalogen.
- När du öppnar filen i Microsoft Word ser du en tom sida med en blå rektangel och den valda bilden, båda markerade som ett enda objekt (du kan flytta eller ändra storlek på dem tillsammans).

![create blank word document with grouped shapes](/images/grouped-shapes.png "create blank word document with grouped shapes")

*Skärmdumpen ovan visar de slutgiltiga grupperade formerna i det nyss skapade Word‑dokumentet.*

## Vanliga variationer och extra tips

| Situation | Hur du hanterar det |
|-----------|---------------------|
| **Flera bilder** | Infoga varje bild med `builder.insertImage` och anropa `group.appendChild(picture)` för varje bild. |
| **Olika formtyper** | Använd `ShapeType.OVAL`, `ShapeType.LINE` osv. när du konstruerar `Shape`‑objektet. |
| **Ändra gruppens position** | Efter att ha lagt till alla barn, sätt `group.setLeft(x)` och `group.setTop(y)` för att flytta hela gruppen. |
| **Exportera till PDF** | Anropa `doc.save("output.pdf")` efter gruppering; PDF‑filen bevarar grupperingarna. |
| **Licenshantering** | Om du kör utvärderingsversionen visas ett vattenstämpel. Installera en giltig licens för att ta bort den. |

## Slutsats

Du vet nu hur du **skapar ett tomt Word‑dokument**, infogar en **GroupShape**, **anger formens storlek**, **anger formens fyllningsfärg** och **lägger till ett barn i gruppen** med Aspose.Words for Java. Detta mönster låter dig bygga komplexa, programatiska layouter som senare kan redigeras i Word eller exporteras till andra format.

Nästa steg är att utforska hur du **grupperar former i Word** med textrutor, lägger till hyperlänkar på former eller automatiserar genereringen av flersidiga rapporter. Samma principer gäller – skapa bara fler former, konfigurera deras egenskaper och lägg till dem i samma grupp.

Lycka till med kodandet!


## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}