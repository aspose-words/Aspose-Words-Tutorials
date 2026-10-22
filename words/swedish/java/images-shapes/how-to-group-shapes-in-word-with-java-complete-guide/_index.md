---
category: general
date: 2026-10-16
description: Lär dig hur du grupperar former i Word med Java. Den här handledningen
  visar hur du lägger till en rektangel, ställer in formens storlek och dimensioner
  samt sparar dokumentet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: sv
lastmod: 2026-10-16
og_description: Gruppera former i Word med Java. Lägg till rektangelform, ställ in
  formens storlek och dimensioner, och skapa professionella dokument programatiskt.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Gruppera former i Word med Java – steg‑för‑steg guide
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Hur man grupperar former i Word med Java – komplett guide
url: /sv/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man grupperar former i Word med Java – komplett guide

Om du behöver **gruppera former i Word** programatiskt, ger den här handledningen dig en färdig‑att‑köra lösning. Du kommer att se hur du **lägger till en rektangelform**, justerar dess storlek, sätter formens dimensioner och slutligen sparar en DOCX‑fil som innehåller en grupperad rektangel och en ellips.

Att gruppera former i Word är användbart för att bygga komplexa diagram, skapa återanvändbara grafiska komponenter, eller helt enkelt hålla relaterade objekt tillsammans när dokumentet redigeras senare. Koden använder Aspose.Words for Java‑biblioteket, som fungerar med alla moderna JDK:er och kräver inte att Microsoft Word är installerat.

## Förutsättningar

| Krav | Orsak |
|-------------|--------|
| Java 17 (or later) | Biblioteket riktar sig mot moderna Java‑körningar. |
| Aspose.Words for Java (latest version) | Tillhandahåller klasserna `Document`, `DocumentBuilder`, `GroupShape` och `Shape` som används i exemplet. |
| An IDE or build tool (Maven/Gradle) | För att kompilera och köra provet. |
| Basic knowledge of Java syntax | Behövs för att förstå kodflödet. |

Lägg till Aspose.Words‑beroendet i ditt projekt. För Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

Eller för Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## Översikt av lösningen

Handledningen följer ett tydligt **problem → lösning → förklaring**‑mönster:

1. **Skapa ett nytt Word‑dokument** och hämta en `DocumentBuilder`.  
2. **Infoga en `GroupShape`‑behållare** som kommer att hålla flera former.  
3. **Lägg till en rektangel**, sätt dess bredd/höjd (steg **set shape size**), och fäst den i gruppen.  
4. **Lägg till en ellips**, placera den i samma grupp, och sätt även dess dimensioner.  
5. **Spara** dokumentet till disk.

Varje steg innehåller **varför**‑delen bakom koden, så att du förstår vad API‑et gör och hur du kan anpassa det till andra scenarier.

## Steg 1: Skapa dokumentet och en DocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Varför detta är viktigt:** `Document` representerar hela DOCX‑filen, medan `DocumentBuilder` är ett verktyg som låter dig infoga innehåll utan att behöva hantera låg‑nivå nodhantering. Att skapa dem först ger dig en ren arbetsyta för alla efterföljande formoperationer.

## Steg 2: Infoga en GroupShape‑behållare

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

En `GroupShape` fungerar som en **mapp** för ritobjekt. När du flyttar, roterar eller tar bort gruppen följer alla underordnade former automatiskt. Detta är kärnan i **group shapes in word**.

## Steg 3: Lägg till en rektangel‑form – koden för rektangelformen

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – `Shape`‑konstruktorn får `ShapeType.RECTANGLE`, vilket instruerar Aspose.Words att rendera en rektangulär kontur.  
- **set shape size** – `setWidth` och `setHeight` definierar **formens dimensioner** i punkter (1 pt = 1/72 tum). Detta är det vanligaste sättet att kontrollera visuell storlek.  
- **Why we use `appendChild`** – Det fäster rektangeln till `GroupShape` så att den rör sig tillsammans med gruppen.

## Steg 4: Lägg till en ellips och placera den i gruppen

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

Ellipsen demonstrerar **set shape dimensions** bortom en enkel rektangel. Genom att anropa `setLeft` styr vi den horisontella förskjutningen inom gruppen, vilket är användbart när man arrangerar flera objekt.

## Steg 5: Spara dokumentet

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

När du öppnar *GroupShapeDemo.docx* i Microsoft Word kommer du att se en rektangel och en ellips låsta tillsammans i en enda grupp. Att markera någon av formerna markerar hela gruppen—precis vad du förväntar dig när **group shapes in word**.

## Fullt, körbart exempel

När alla delar sätts ihop är här den kompletta källfilen som du kan kopiera in i din IDE:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### Förväntat resultat

- En fil med namnet **GroupShapeDemo.docx** visas i projektmappen.  
- När filen öppnas i Word visas två former (en rektangel och en ellips) som är grupperade tillsammans.  
- Att dra någon av formerna flyttar hela gruppen, vilket bekräftar att **group shapes in word** fungerar som avsett.

## Vanliga varianter och kantfall

| Scenario | Vad som ska ändras | Varför |
|----------|--------------------|--------|
| **Olika formtyper** (t.ex. triangel) | Use `ShapeType.TRIANGLE` or any other enum value when constructing `Shape`. | Gör att du kan bygga mer komplexa diagram. |
| **Ställa in fyllningsfärg** | Call `shape.getFillColor().setColor(Color.BLUE);` after creating the shape. | Förbättrar det visuella utseendet utan att påverka gruppering. |
| **Rotera gruppen** | `groupShape.setRotationAngle(45);` | Roterar alla underordnade former tillsammans, användbart för ikoner. |
| **Lägga till text i en form** | `shape.appendChild(new Paragraph(document));` then add a `Run` with text. | Gör att formen fungerar som en etikett eller förklarande text. |
| **Spara till en ström** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Användbart för webbtjänster som returnerar dokumentet direkt. |

### Proffstips

När du behöver **set shape dimensions** baserat på dynamisk data (t.ex. en streckkodslängd), beräkna bredden/höjden i punkter först:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

Detta undviker hårdkodade värden och gör din kod anpassningsbar.

## Slutsats

Du vet nu hur du **group shapes in Word** med Java, hur du **add rectangle shape**, och hur du **set shape size** och **set shape dimensions** med kortfattad, produktionsklar kod. Genom att följa stegen ovan kan du skapa återanvändbara grafikgrupper, bädda in dem i automatiserade rapporter eller bygga anpassade diagramverktyg utan att någonsin öppna Word manuellt.

### Vad blir nästa?

- Utforska variationer av **add rectangle shape** såsom rundade hörn (`ShapeType.RECTANGLE` med `setCornerRadius`).  
- Kombinera **group shapes in word** med tabeller eller diagram för rikare dokument.  
- Titta på Aspose.Words‑API:t för **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) för att styra hur omgivande text interagerar med dina grupperade grafikobjekt.

Känn dig fri att experimentera, anpassa **rectangle shape code**, och dela dina resultat

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word‑dokument Java – Lägg till rektangelform med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Skapa rektangelform i Word med Java – Fullständig guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Skapa gruppform i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}