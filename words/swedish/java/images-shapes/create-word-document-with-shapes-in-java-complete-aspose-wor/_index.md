---
category: general
date: 2026-07-29
description: Skapa ett Word‑dokument i Java med Aspose.Words. Lär dig att infoga en
  rektangel, gruppera former i Word och spara dokumentet som docx snabbt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: sv
lastmod: 2026-07-29
og_description: Skapa Word‑dokument i Java med Aspose.Words. Infoga rektangelform,
  gruppera former i Word och spara dokumentet som docx på några minuter.
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: Skapa Word-dokument med former – Java Aspose.Words-handledning
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
title: Skapa Word-dokument med former i Java – Komplett Aspose.Words-guide
url: /sv/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument med former i Java – Komplett Aspose.Words-guide

Har du någonsin undrat hur man **create word document** programatiskt och strör in anpassade grafik? Du är inte ensam. Oavsett om du behöver generera en rapport med markerade sektioner eller designa en flyer i farten, kan behärskning av formhantering i Word spara dig timmar av manuellt arbete.

I den här handledningen går vi igenom de exakta stegen för att **create word document** med Aspose.Words för Java, **insert rectangle shape**, **group shapes in Word**, och slutligen **save document as docx**. I slutet har du ett fullt körbart exempel som du kan släppa in i vilket projekt som helst.

## Vad du får med dig

- En ny Word-fil genererad helt från Java-kod.  
- Två distinkta former (en rektangel och en ellips) tillagda på sidan.  
- Dessa former samlade tillsammans med **group shapes in word** API, vilket får dem att fungera som ett enda objekt.  
- Filen sparas på disk som en standard `.docx` som öppnas i Microsoft Word utan problem.  

Inga externa verktyg, inga krångliga XML-hack—bara ren, typad Java och Aspose.Words.

---

## Förutsättningar

Innan vi dyker ner, se till att du har:

1. **Java Development Kit (JDK) 8 eller nyare** – koden riktar sig mot Java 8+.  
2. **Aspose.Words for Java** JAR (du kan hämta den senaste versionen från Maven Central‑arkivet).  
3. En enkel IDE (IntelliJ IDEA, Eclipse, eller till och med en enkel textredigerare).  

Om du har dem, toppen—låt oss börja.

---

## Steg‑för‑steg-implementation

Nedan delar vi upp processen i små steg. Varje steg innehåller ett kodexempel, en kort förklaring och ett tips du kanske inte hittar i den officiella dokumentationen.

### ## Skapa Word-dokument med former med Aspose.Words

Det första du behöver är en tom Word-fil att arbeta med. Aspose.Words gör detta till en enradig kod.

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Varför detta är viktigt:**  
`Document` är behållaren för allt—text, tabeller, bilder och former. `DocumentBuilder` är den vänliga hjälparen som låter dig lägga till innehåll utan att kämpa med lågnivå‑objekt. Tänk på det som en penna som skriver direkt på sidan.

> **Pro‑tips:** Om du planerar att börja med en mall (t.ex. ett företagsbrevhuvud), ersätt `new Document()` med `new Document("template.docx")`.

### ## Infoga rektangel‑form och andra former

Nu lägger vi till en blå rektangel och en grön ellips. Rektangeln demonstrerar nyckelordet **insert rectangle shape**, medan ellipsen visar att du fritt kan blanda olika formtyper.

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

**Vad som händer under huven?**  
Varje anrop till `insertShape` skapar ett `Shape`‑objekt och lägger automatiskt till det i det aktuella stycket. Metoderna `setLeft`/`setTop` positionerar formen relativt sidmarginalerna, mätt i punkter (1 pt = 1/72 in). Genom att justera dessa siffror kan du placera former var du vill.

> **Vanlig fråga:** *Kan jag lägga till en bild istället för en solid färg?*  
> Absolut—byt bara fyllningsfärgen mot en bild med `shape.getFill().setImage("path/to/image.png")`.

### ## Gruppera former i Word för enkel manipulation

Att ha två separata objekt är okej, men ofta vill du flytta dem tillsammans. Det är där **group shapes in word** briljerar.

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**Varför gruppera?**  
När former är grupperade gäller alla transformationer—flytt, rotation, storleksändring—på hela samlingen. Detta speglar beteendet du får när du manuellt markerar flera former i Word‑gränssnittet och trycker på *Group*. Det förenklar också senare kod eftersom du bara behöver justera ett objekt istället för många.

> **Edge case:** Om du senare behöver avgruppera, anropa `group.getParentNode().removeChild(group)` och sätt in barnen individuellt igen.

### ## Spara dokument som DOCX och verifiera resultatet

Till sist sparar vi filen. Detta steg uppfyller kravet **save document as docx**.

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**Vad du kan förvänta dig:**  
Öppna den genererade `GroupShapeExample.docx` i Microsoft Word. Du kommer att se en blå rektangel och en grön ellips, snyggt grupperade. Dra gruppen runt—båda formerna flyttar sig tillsammans, precis som du skulle förvänta dig i UI.

> **Tips:** Använd `SaveFormat.PDF` om du behöver en PDF‑version; samma kod fungerar utan ändringar.

### ## Fullt fungerande exempel och vanliga fallgropar

Nedan är den kompletta, körklara Java‑klassen. Kopiera‑klistra in den i ditt projekt, justera utdatamappen och tryck på *Run*.

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

#### Vanliga fallgropar & hur man undviker dem

| Issue | Why It Happens | Fix |
|-------|----------------|-----|
| **`NullPointerException` on `builder`** | Glömmer att instansiera `DocumentBuilder` efter att ha skapat `Document`. | Se till att `new DocumentBuilder(doc)` körs innan någon forminfogning. |
| **Shapes appear off‑page** | Använder pixelvärden istället för punkter, eller tar inte hänsyn till marginaler. | Kom ihåg att Aspose.Words förväntar sig punkter; 72 pt = 1 in. Justera `setLeft`/`setTop` därefter. |
| **Group disappears after save** | Lägger till former i gruppen *efter* att gruppen har sparats. | Alltid gruppera innan du anropar `doc.save()`. |
| **File not found on save** | Utdatamappen finns inte. | Skapa mappen programatiskt (`new File("output").mkdirs();`) eller använd en befintlig sökväg. |

---

## Slutsats

Vi har just **create word document** från grunden, **add shapes to word**, **insert rectangle shape**, **group shapes in word**, och slutligen **save document as docx**—allt med ett fåtal rader Java. Kraften i Aspose.Words ligger i dess tydliga objektmodell; du kan behandla en Word‑fil som en duk, måla på den med former och sedan exportera den var du än behöver.

Känner du dig äventyrlig? Prova att byta ut rektangeln mot en stjärna, lägg till text inuti formerna med `Shape.getTextBox()`, eller experimentera med rotation (`shape.setRotationAngle(45)`). API:et är rikt, och möjligheterna är praktiskt taget oändliga.

Har du frågor om mer avancerade scenarier—som att länka former till bokmärken eller exportera till PDF med inbäddade teckensnitt? Lämna en kommentar nedan, så dyker vi djupare tillsammans. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Skapa Word-dokument Java – Lägg till rektangel‑form med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Skapa gruppform i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Skapa rektangel‑form i Word med Aspose.Words – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}