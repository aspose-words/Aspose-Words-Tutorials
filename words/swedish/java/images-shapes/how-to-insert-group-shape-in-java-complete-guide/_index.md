---
category: general
date: 2026-07-16
description: hur man infogar gruppform i Java med Aspose.Words – lägg till rektangel,
  ange formens dimensioner och skapa färgad rektangel och cirkel
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: sv
lastmod: 2026-07-16
og_description: 'hur man infogar gruppform i Java: en praktisk guide för att lägga
  till rektangelform, ställa in formens dimensioner och skapa färgad rektangel och
  cirkel med Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Infoga gruppform i Java – Fullständig Aspose.Words-handledning
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: hur man infogar gruppform i Java – Komplett guide
url: /sv/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hur man infogar gruppform i Java – Komplett guide

Har du någonsin funderat **hur man infogar gruppform** i ett Word‑dokument med Java? Du är inte ensam. Oavsett om du bygger en rapportgenerator eller en dynamisk flyer‑skapare, håller gruppering av former din layout prydlig och din kod hanterbar.

I den här handledningen går vi igenom de exakta stegen för att **lägga till rektangel‑form**, **sätta formens dimensioner**, och **skapa färgad rektangel** samt **skapa färgad cirkel** med Aspose.Words‑biblioteket. När du är klar har du ett körbart program som producerar en .docx‑fil med en blå rektangel och en röd cirkel snyggt inbäddade i en grupp.

## Förutsättningar

Innan vi dyker ner, se till att du har:

- Java 17 (eller någon nyare JDK) installerad och konfigurerad.
- Maven eller Gradle för att hantera beroenden.
- Aspose.Words for Java 23.9 eller nyare – du kan hämta det från Maven Central.
- En grundläggande förståelse för Java‑syntax – inget avancerat behövs.

Om du saknar någon av dessa, hämta JDK:n från Oracles webbplats och lägg till Aspose.Words‑beroendet i din `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Nu när grunderna är på plats, låt oss sätta igång.

## hur man infogar gruppform – Översikt

Kärnidén är enkel: skapa ett `Document`, öppna en `DocumentBuilder`, infoga en **gruppform**, och släpp sedan individuella former (en rektangel och en cirkel) i den gruppen. Gruppen fungerar som en behållare, så att flytta den senare förflyttar allt innanför – perfekt för komplexa layouter.

Nedan är den kompletta, körklara koden. Kopiera och klistra in den i en ny Java‑klass som heter `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Pro tip:** Värdena för `setLeft` och `setTop` är relativa till gruppens ursprung, inte sidan. Detta gör det enkelt att ompositionera hela gruppen senare.

### Vad hände precis?

1. **Document & Builder** – Vi skapar en tom Word‑fil och en `DocumentBuilder` som låter oss infoga innehåll.
2. **Group Shape** – `builder.insertGroupShape()` skapar en behållare. Tänk på den som en mapp för ritobjekt.
3. **Blue Rectangle** – Vi instansierar en `Shape` av typen `RECTANGLE`, sätter storlek, position och fyller den med blått – det är steget **create colored rectangle**.
4. **Red Circle** – Samma mönster, men med `ELLIPSE` för en perfekt cirkel, sedan fyller vi den med rött – det är delen **create colored circle**.
5. **Saving** – Slutligen sparar vi allt till `GroupShapeDemo.docx`.

Kör programmet (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) och öppna den resulterande filen. Du bör se en blå rektangel till vänster och en röd cirkel till höger, båda låsta inuti en enda gruppruta.

## Lägga till en rektangel‑form

Om du bara behöver en rektangel utan gruppering kan du hoppa över anropet `insertGroupShape()` och lägga till rektangeln direkt i dokumentets kropp. Att gruppera ger dock flexibiliteten att flytta, rotera eller ta bort flera former på en gång.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Observera hur vi använde logiken **add rectangle shape** här. Rektangeln visas på sidan som ett fristående objekt. I de flesta verkliga scenarier vill du ha gruppen, eftersom den bevarar relativ positionering.

## Sätta formens dimensioner

När du ser metoder som `setWidth` och `setHeight`, kom ihåg att de tar emot **points** (1/72 tum). Om du föredrar millimeter, konvertera först:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

Detta kodsnutt demonstrerar **set shape dimensions** med en enhetskonvertering – praktiskt när dina design‑specifikationer kommer från en UI‑mockup som använder metriska enheter.

## Skapa en färgad rektangel

Att färga en form är så enkelt som att anropa `getFill().setForeColor()`. Du kan skicka vilken `java.awt.Color` som helst. Vill du ha en gradient? Använd `setForeColor` för startfärgen och `setBackColor` för slutfärgen.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

Det är ett snabbt sätt att **create colored rectangle** med en gradientfyllning istället för en solid färg.

## Skapa en färgad cirkel

Cirklar är bara ellipser med lika bredd och höjd. Samma färglogik gäller:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

Om du behöver en transparent fyllning, sätt alfakanalen:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Nu har du bemästrat tekniken **create colored circle**.

## Spara dokumentet

Aspose.Words låter dig exportera till många format: DOCX, PDF, HTML, PNG, du bestämmer. För den här demonstrationen håller vi oss till DOCX eftersom det bevarar vektorformerna perfekt.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

Att byta `SaveFormat` är allt som krävs för att generera en PDF‑version av samma grupperade konstverk.

## Vanliga fallgropar & hur man undviker dem

- **Glömt att lägga till formen i gruppen?** Formen visas på sidan men flyttar sig inte med gruppen. Anropa alltid `group.appendChild(yourShape)`.

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}