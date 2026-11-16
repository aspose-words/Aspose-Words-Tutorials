---
category: general
date: 2026-11-15
description: Skapa en rektangel i Word med Java och lär dig hur du lägger till former
  i Word, sätter formens dimensioner och sparar Word-dokumentet effektivt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: sv
lastmod: 2026-11-15
og_description: Skapa en rektangel i ett Word‑dokument med Java. Lär dig att lägga
  till former i Word, ange formens dimensioner och spara Word‑dokumentet på några
  minuter.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Skapa rektangel i Word med Java – steg‑för‑steg guide
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Skapa rektangel i ett Word‑dokument med Java
url: /sv/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangel‑form i ett Word‑dokument med Java

Om du behöver **skapa rektangel‑form** i ett Word‑dokument visar den här guiden exakt hur du gör det med Java. Du får se hur du **lägger till former i Word**, styr **set shape dimensions**, och slutligen **sparar Word‑dokument** utan att lämna din IDE.

I avsnitten som följer får du ett komplett, körbart exempel, en förklaring av varje rad och tips för vanliga fallgropar såsom storleksproblem och dokumentkompatibilitet. Inga externa referenser behövs – bara Aspose.Words for Java‑biblioteket.

## Vad du kommer att lära dig

* Hur du initierar ett `Document` och en `DocumentBuilder`.
* Hur du infogar en **group shape** och placerar en rektangel i den.
* Hur du **definierar formens storlek** med `setWidth` och `setHeight`.
* Hur du **sparar Word‑dokument** i `.docx`‑format.
* Hantering av edge‑cases för olika sidstorlekar och DPI‑inställningar.

### Förutsättningar

* Java 17 eller senare (koden kompilerar även med Java 8).
* Aspose.Words for Java 23.10 eller nyare – du kan hämta det från Maven Central.
* Grundläggande förståelse för Java‑syntax och objekt‑orienterade koncept.

> **Pro tip:** Om du planerar att lägga till fler former senare (t.ex. cirklar eller textrutor), håll dem i samma `GroupShape`. Detta gör det mycket enklare att flytta, rotera eller formatera hela samlingen.

## Steg 1: Initiera dokumentet och buildern

Det första steget är att skapa en tom Word‑fil och en `DocumentBuilder` som låter dig skriva innehåll.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Varför detta är viktigt:* Ett `Document` representerar hela filen, medan `DocumentBuilder` erbjuder hög‑nivå‑metoder för att infoga text, tabeller och **shapes**. Utan buildern skulle du behöva manipulera låg‑nivå‑noder manuellt.

## Steg 2: Infoga en gruppform för att hålla flera former

En **group shape** fungerar som en behållare; du kan lägga till flera former och behandla dem som ett enda objekt senare (t.ex. flytta eller rotera tillsammans).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Varför använda en gruppform?* Om du senare bestämmer dig för att lägga till pilar, cirklar eller etiketter runt rektangeln, håller gruppen allt i linje. Det förenklar också arbetsflödet **add shapes to Word** eftersom du bara behöver ett anrop till `appendChild` för varje ny form.

## Steg 3: Skapa rektangel‑formen

Nu skapar vi den faktiska rektangeln som kommer att ligga i gruppen. `Shape`‑konstruktorn behöver det ägande `Document`‑objektet och typen av form du vill ha.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Varför en rektangel?* `ShapeType.RECTANGLE` är den vanligaste primitiva formen för att markera sektioner, skapa platshållare eller rita enkla UI‑mock‑ups direkt i Word.

## Steg 4: Definiera rektangelns storlek

Att sätta dimensionerna är där **set shape dimensions** blir viktigt. Du kan använda vilken måttenhet som helst som stöds av Aspose.Words; standard är punkter (1 pt = 1/72 tum).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Obs:** Om du föredrar millimeter, anropa `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` där `1.39 in ≈ 35 mm`. Detta visar flexibiliteten i **define shape size**.

## Steg 5: Lägg till rektangeln i gruppformen

Genom att lägga till rektangeln i den tidigare skapade gruppen får den visas i dokumentet.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

Vid detta tillfälle är rektangeln placerad i gruppens övre‑vänstra hörn. Du kan senare flytta den med `rectangle.setLeft(...)` och `rectangle.setTop(...)` om du behöver exakt placering.

## Steg 6: (Valfritt) Spara dokumentet för att se resultatet

Till sist skriver du dokumentet till disk. Detta är steget **save Word document** som producerar en `.docx`‑fil som du kan öppna i Microsoft Word, LibreOffice eller Google Docs.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

När programmet körs skapas `RectangleShapeDemo.docx` som innehåller en enda rektangel i en gruppform. När du öppnar filen ser du en enkel vit rektangel – exakt den storlek du definierade.

### Förväntat resultat

* En Word‑fil med namnet `RectangleShapeDemo.docx`.
* I det första stycket en gruppform som innehåller en 100 pt × 50 pt rektangel.
* Ingen text har lagts till, så rektangeln visas på en tom sida.

## Vanliga variationer och edge cases

| Situation | Hur du anpassar koden |
|-----------|-----------------------|
| **Olika sidstorlek** (t.ex. A4) | Anropa `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` innan du infogar formen. |
| **Högre DPI för utskrift** | Multiplicera bredd/höjd med önskad DPI‑faktor, t.ex. `rectangle.setWidth(200 * 2);` för dubbel upplösning. |
| **Lägga till en textetikett i rektangeln** | Skapa en `Shape` av typen `TEXT_BOX`, sätt `setWidth`/`setHeight` så att de matchar rektangeln, och lägg sedan till den i samma `GroupShape`. |
| **Rotera rektangeln** | Använd `rectangle.setRotationAngle(45);` för att rotera 45 grader medurs. |
| **Spara som PDF istället för DOCX** | Byt ut `document.save("output.docx");` mot `document.save("output.pdf");` – samma API fungerar för PDF och bevarar rektangeln. |

## Pro‑tips för en robust implementation

1. **Återanvänd buildern** – efter att du har infogat gruppformen kan du fortsätta lägga till stycken eller tabeller utan att skapa en ny builder‑instans.
2. **Frigör resurser** – även om Java‑soppsamlaren hanterar de flesta objekt, förhindrar ett explicit anrop till `document.close();` (vid användning av strömmar) fil‑handtags‑läckage.
3. **Validera dimensioner** – innan du anropar `setWidth`/`setHeight`, säkerställ att värdena är positiva; negativa värden kastar `IllegalArgumentException`.
4. **Versionskompatibilitet** – koden fungerar med Aspose.Words 23.x och senare. Äldre versioner kan kräva `Shape.setSize(width, height)` istället för separata setters.

## Fullt, körbart exempel

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Resultatverifiering:** Öppna `output/RectangleShapeDemo.docx` i Microsoft Word. Du bör se en rektangel av den angivna storleken centrerad högst upp på första sidan. Om rektangeln verkar för liten, justera värdena som skickas till `setWidth` och `setHeight`.

## Slutsats

Du vet nu hur du **create rectangle shape** i ett Word‑dokument med Java, hur du **add shapes to Word** via en `GroupShape`, hur du **set shape dimensions** och **define shape size**, och slutligen hur du **save Word document** för vidare distribution. Samma mönster fungerar för andra formtyper, så du kan bygga komplexa diagram programatiskt.

### Vad blir nästa steg?

* Utforska **add shapes to Word** genom att infoga cirklar, pilar eller textrutor.
* Kombinera flera former till en enda `GroupShape` och applicera transformationer (rotera, spegelvänd).
* Generera rapporter som bäddar in diagram som former, och sedan **save Word document** som PDF för delning.

Känn dig fri att experimentera med dimensioner, färger och placering för att passa ditt specifika scenario. Lycka till med kodandet!


## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Create word document java – hide shape and set fill color](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}