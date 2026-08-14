---
category: general
date: 2026-08-14
description: Gruppera former i Word med Java med Aspose.Words. Lär dig hur du skapar
  en rektangel, ställer in formens dimensioner och grupperar flera former i ett tomt
  Word‑dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: sv
lastmod: 2026-08-14
og_description: Gruppera former i Word med Aspose.Words för Java. Skapa ett tomt Word‑dokument,
  skapa en rektangel, ange formens dimensioner och gruppera flera former på några
  minuter.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Gruppera former i Word – Java‑exempel för utvecklare
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Gruppera former i Word – komplett programmeringsguide
url: /sv/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gruppera former i Word – komplett programmeringsguide

Om du behöver **gruppera former i Word**, går den här handledningen dig igenom hela processen med Java och Aspose.Words. Du kommer att lära dig hur du **skapar ett tomt Word-dokument**, **skapar en rektangelform**, **sätter formens dimensioner**, och slutligen **grupperar flera former** så att de beter sig som ett enda objekt.

Att arbeta med former i en Word-fil känns ofta som att rita på en duk utan pensel. I slutet av den här guiden har du ett återanvändbart kodsnutt som du kan klistra in i vilket Java‑projekt som helst, oavsett om du genererar rapporter, fakturor eller anpassade mallar.

## Vad du behöver

- Java 8 eller nyare
- Aspose.Words för Java (senaste versionen, t.ex. 24.9)
- En IDE såsom IntelliJ IDEA eller Eclipse
- Grundläggande kunskap om objekt‑orienterad programmering

Alla dessa förutsättningar är gratis att installera, och koden nedan kompileras med ett enda Maven‑beroende:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Steg 1: Skapa ett tomt Word‑dokument och initiera byggaren

Det första du måste göra är att **skapa ett tomt Word‑dokument**. Detta ger dig en ren duk som du senare kan infoga former på.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representerar hela *.docx*-filen, medan `DocumentBuilder` är hjälpen som infogar stycken, tabeller och former. Att initiera båda objekten är grunden för alla Word‑automatiseringsuppgifter.

## Steg 2: Infoga en gruppform‑behållare

En **gruppform** fungerar som en mapp som kan innehålla andra former. Först skapar vi behållaren med en fast storlek på 400 pt × 200 pt.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

`insertGroupShape`‑metoden returnerar ett `GroupShape`‑objekt. Alla efterföljande former som du vill behandla som en enhet måste läggas till i detta objekt.

## Steg 3: Skapa rektangelformer och sätt formens dimensioner

Nu **skapar vi rektangelform**‑objekt, konfigurerar deras storlek och placerar dem i gruppen. Detta steg visar också hur man **sätter formens dimensioner** exakt.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

Båda rektanglarna har samma dimensioner, men deras `left`‑egenskaper skiljer sig, så de visas sida‑vid‑sida. Du kan ändra `setTop` och `setLeft` för att arrangera vilken layout du behöver.

## Steg 4: Spara dokumentet som innehåller de grupperade rektanglarna

När formerna är i gruppen sparar du helt enkelt `Document`. Den resulterande filen visar två rektanglar som rör sig tillsammans när de markeras.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

När programmet körs skapas `GroupShape.docx` i arbetskatalogen. Öppna den i Microsoft Word, markera en rektangel, och du kommer att märka att hela gruppen rör sig som en enhet – exakt vad **gruppera former i Word** är avsett att göra.

![Group shapes in Word example](group-shapes.png){alt="Exempel på grupperade former i Word"}

*Figur: Två rektangelformer grupperade tillsammans i ett Word‑dokument.*

## Proffstips: Återanvända samma gruppform

Om du senare behöver lägga till fler former (t.ex. cirklar, textrutor), behåll en referens till `groupShape` och fortsätt anropa `appendChild`. Detta undviker att skapa om behållaren och säkerställer att alla medlemmar förblir synkroniserade.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## Kantfall och vanliga frågor

- **Vad händer om formerna överlappar?** Överlappning är tillåten; Word renderar dem i den ordning de lades till. Använd `setZOrder` om du behöver explicit stapling.
- **Kan jag gruppera former över olika sidor?** Nej. En `GroupShape` är begränsad till en enda sida eftersom dess koordinatsystem är sidrelativt.
- **Ärver grupperade former formatering?** Varje barn behåller sin egen formatering (fyllningsfärg, linjestil). För att tillämpa en enhetlig stil, iterera över `groupShape.getChildNodes()` och sätt egenskaper programatiskt.

## Fullständig källkod för referens

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

När programmet körs produceras en DOCX‑fil där de två rektanglarna är **grupperade**. Att markera någon rektangel flyttar båda, vilket bekräftar att du framgångsrikt har **grupperat flera former**.

## Slutsats

Du vet nu hur du **grupperar former i Word** med Java, från **att skapa ett tomt Word‑dokument** till **att skapa rektangelform**, **sätta formens dimensioner**, och slutligen **gruppera flera former** till ett enda, flyttbart objekt. Detta mönster kan skalas till valfritt antal former och kan kombineras med text, bilder eller diagram för att bygga rika, programatiska dokument.

### Vad blir nästa?

- Utforska **gruppera flera former** med olika typer (ellipser, pilar, textrutor).
- Applicera fyllningsfärger eller kanter genom att anropa `shape.getFillColor()` och `shape.getLine().setColor()`.
- Infoga den grupperade formen i en tabellcell för strukturerade rapporter.
- Kombinera detta tillvägagångssätt med kopplad utskrift (mail‑merge) för att generera personliga kontrakt som inkluderar varumärkta grafik.

Känn dig fri att experimentera, anpassa dimensionerna eller bädda in ytterligare innehåll. När du behärskar gruppering blir dina Word‑automatiseringsskript mycket mer flexibla och underhållbara. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Använda dokumentformer i Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Skapa Word‑dokument Java – Lägg till rektangelform med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Skapa gruppform i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}