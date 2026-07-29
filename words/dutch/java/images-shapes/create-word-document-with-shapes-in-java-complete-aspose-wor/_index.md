---
category: general
date: 2026-07-29
description: Maak een Word‑document in Java met Aspose.Words. Leer een rechthoekvorm
  in te voegen, vormen te groeperen in Word en het document snel op te slaan als docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: nl
lastmod: 2026-07-29
og_description: Maak een Word‑document in Java met Aspose.Words. Voeg een rechthoekvorm
  toe, groepeer vormen in Word en sla het document binnen enkele minuten op als docx.
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: Maak Word-document met vormen – Java Aspose.Words-tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Maak Word-document met vormen in Java – Complete Aspose.Words-gids
url: /nl/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-document maken met vormen in Java – Complete Aspose.Words-gids

Heb je je ooit afgevraagd hoe je **word document** programmatically kunt maken en kunt voorzien van aangepaste graphics? Je bent niet de enige. Of je nu een rapport met gemarkeerde secties moet genereren of een flyer on‑the‑fly wilt ontwerpen, het beheersen van vormverwerking in Word kan je uren handmatig werk besparen.

In deze tutorial lopen we stap voor stap door hoe je **word document** maakt met Aspose.Words for Java, **rectangle shape** **invoegt**, **shapes groepeert in Word**, en uiteindelijk **document opslaat als docx**. Aan het einde heb je een volledig werkend voorbeeld dat je in elk project kunt gebruiken.

## What You’ll Walk Away With

- Een nieuw Word‑bestand dat volledig uit Java‑code is gegenereerd.  
- Twee verschillende vormen (een rechthoek en een ellips) die aan de pagina worden toegevoegd.  
- Die vormen samengevoegd met de **group shapes in word**‑API, zodat ze zich gedragen als één object.  
- Het bestand opgeslagen op schijf als een standaard `.docx` dat zonder problemen in Microsoft Word opent.  

Geen externe tools, geen ingewikkelde XML‑hacks—alleen nette, getypeerde Java en Aspose.Words.

---

## Prerequisites

Voordat we beginnen, zorg dat je het volgende hebt:

1. **Java Development Kit (JDK) 8 of nieuwer** – de code richt zich op Java 8+.  
2. **Aspose.Words for Java** JAR (download de nieuwste versie van de Maven Central repository).  
3. Een eenvoudige IDE (IntelliJ IDEA, Eclipse, of zelfs een simpele teksteditor).  

Als je dit allemaal hebt, geweldig—laten we van start gaan.

---

## Step‑by‑Step Implementation

Hieronder splitsen we het proces op in hapklare stappen. Elke stap bevat een code‑fragment, een korte uitleg, en een tip die je misschien niet in de officiële docs vindt.

### ## Create Word Document with Shapes Using Aspose.Words

Het eerste wat je nodig hebt is een leeg Word‑bestand om mee te werken. Aspose.Words maakt dit een één‑regelige opdracht.

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Waarom dit belangrijk is:**  
`Document` is de container voor alles—tekst, tabellen, afbeeldingen en vormen. `DocumentBuilder` is de vriendelijke helper die je content laat toevoegen zonder te worstelen met low‑level objecten. Zie het als een pen die direct op de pagina schrijft.

> **Pro tip:** Als je wilt beginnen met een template (bijv. een bedrijfsbriefhoofd), vervang `new Document()` door `new Document("template.docx")`.

### ## Insert Rectangle Shape and Other Shapes

Nu voegen we een blauwe rechthoek en een groene ellips toe. De rechthoek demonstreert het **insert rectangle shape**‑keyword, terwijl de ellips laat zien dat je vrijelijk verschillende vormtypen kunt combineren.

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**Wat er onder de motorkap gebeurt:**  
Elke oproep van `insertShape` maakt een `Shape`‑object aan en voegt het automatisch toe aan de huidige alinea. De methoden `setLeft`/`setTop` positioneren de vorm relatief aan de paginamarges, gemeten in punten (1 pt = 1/72 in). Door deze getallen aan te passen kun je vormen overal plaatsen waar je wilt.

> **Veelgestelde vraag:** *Kan ik in plaats van een effen kleur een afbeelding toevoegen?*  
> Zeker—vervang simpelweg de vulkleur door een afbeelding met `shape.getFill().setImage("path/to/image.png")`.

### ## Group Shapes in Word for Easy Manipulation

Twee losse objecten zijn prima, maar vaak wil je ze samen verplaatsen. Daar komt **group shapes in word** van pas.

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**Waarom groeperen?**  
Wanneer vormen gegroepeerd zijn, wordt elke transformatie—verplaatsen, roteren, schalen—toegepast op de hele collectie. Dit bootst het gedrag na dat je krijgt wanneer je handmatig meerdere vormen in de Word‑UI selecteert en op *Group* klikt. Het vereenvoudigt ook latere code omdat je slechts één object hoeft aan te passen in plaats van vele.

> **Edge case:** Als je later moet degrouperen, roep `group.getParentNode().removeChild(group)` aan en voeg de kinderen afzonderlijk opnieuw in.

### ## Save Document as DOCX and Verify Output

Tot slot slaan we het bestand op. Deze stap voldoet aan de **save document as docx**‑vereiste.

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**Wat je kunt verwachten:**  
Open het gegenereerde `GroupShapeExample.docx` in Microsoft Word. Je ziet een blauwe rechthoek en een groene ellips, netjes gegroepeerd. Sleep de groep rond—beide vormen bewegen samen, precies zoals je van de UI zou verwachten.

> **Tip:** Gebruik `SaveFormat.PDF` als je een PDF‑versie nodig hebt; dezelfde code werkt zonder wijzigingen.

### ## Full Working Example and Common Pitfalls

Hieronder staat de volledige, kant‑en‑klaar werkende Java‑klasse. Kopieer‑plak hem in je project, pas de output‑map aan, en klik op *Run*.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### Common Pitfalls & How to Avoid Them

| Issue | Why It Happens | Fix |
|-------|----------------|-----|
| **`NullPointerException` on `builder`** | Forgetting to instantiate `DocumentBuilder` after creating `Document`. | Ensure `new DocumentBuilder(doc)` runs before any shape insertion. |
| **Shapes appear off‑page** | Using pixel values instead of points, or not accounting for margins. | Remember that Aspose.Words expects points; 72 pt = 1 in. Adjust `setLeft`/`setTop` accordingly. |
| **Group disappears after save** | Adding shapes to the group *after* the group has been saved. | Always group before calling `doc.save()`. |
| **File not found on save** | Output directory doesn’t exist. | Create the directory programmatically (`new File("output").mkdirs();`) or use an existing path. |

---

## Conclusion

We’ve just **create word document** from scratch, **add shapes to word**, **insert rectangle shape**, **group shapes in word**, and finally **save document as docx**—all with a handful of lines of Java. The power of Aspose.Words lies in its clear object model; you can treat a Word file like a canvas, paint on it with shapes, and then export it wherever you need.

Feeling adventurous? Try swapping the rectangle for a star, add text inside the shapes using `Shape.getTextBox()`, or experiment with rotation (`shape.setRotationAngle(45)`). The API is rich, and the possibilities are practically endless.

Got questions about more advanced scenarios—like linking shapes to bookmarks or exporting to PDF with embedded fonts? Drop a comment below, and we’ll dive deeper together. Happy coding!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step‑by‑step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}