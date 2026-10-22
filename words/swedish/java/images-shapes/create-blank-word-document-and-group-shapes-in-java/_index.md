---
category: general
date: 2026-08-23
description: Skapa ett tomt Word‑dokument med Aspose.Words för Java, lär dig hur du
  grupperar former, färglägger rektangelformen och sparar dokumentet som docx på några
  minuter.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: sv
lastmod: 2026-08-23
og_description: Skapa ett tomt Word‑dokument med Aspose.Words för Java, se sedan hur
  du grupperar former, färglägger rektangelformen och sparar dokumentet som docx på
  ett effektivt sätt.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Skapa ett tomt Word‑dokument och gruppera former i Java – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Skapa ett tomt Word‑dokument och gruppera former i Java
url: /sv/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa tomt Word-dokument och gruppera former i Java

Om du behöver **create blank Word document** programatiskt, gör Aspose.Words for Java det enkelt. Denna handledning visar exakt hur du **create blank Word document**, infogar en **group shapes in Word**, applicerar **color rectangle shape**, och slutligen **save document as docx**. I slutet har du ett återanvändbart kodexempel som du kan lägga in i vilket Java‑projekt som helst.

Du kommer att lära dig:

* Den erforderliga Maven/Gradle‑beroendet för Aspose.Words.
* Hur man instansierar ett tomt dokument och en `DocumentBuilder`.
* De exakta stegen för **how to group shapes** i en `GroupShape`.
* Hur man sätter fyllningsfärger på rektangelformer.
* Bästa praxis för **save document as docx** och var du hittar utdatafilen.

Ingen förkunskap om Aspose.Words antas, men du bör vara bekväm med grundläggande Java‑utveckling och ha en JDK 8 eller nyare installerad.

---

## Förutsättningar

| Krav | Version / Detalj |
|-------------|-------------------|
| Java Development Kit | 8 or higher |
| Build tool | Maven 3+ or Gradle 6+ |
| Aspose.Words for Java | 23.12 or later (the latest version at the time of writing) |
| IDE (optional) | IntelliJ IDEA, Eclipse, VS Code, or any Java‑compatible editor |

---

## Steg 1: Lägg till Aspose.Words i ditt projekt

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** Om du använder en företagsproxy, konfigurera Maven/Gradle för att hämta paketet från Aspose‑arkivet enligt beskrivningen i den officiella dokumentationen.

---

## Steg 2: **Create blank Word document** med en builder

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document`‑konstruktorn skapar en tom `.docx`‑behållare i minnet. `DocumentBuilder` ger dig ett flytande API för att lägga till innehåll, inklusive former.

---

## Steg 3: Infoga en **group shapes in Word**‑behållare

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

En `GroupShape` fungerar som en mini‑canvas. Alla former som läggs till den flyttas tillsammans, vilket är exakt **how to group shapes** för layout‑konsistens.

---

## Steg 4: Lägg till den första **color rectangle shape** (röd)

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

`ShapeType.RECTANGLE`‑konstanten skapar en enkel rektangel. Genom att anropa `getFill().setForeColor(...)` styr du **color rectangle shape**. Du kan ersätta `java.awt.Color.RED` med någon `java.awt.Color`‑konstant eller ett eget RGB‑värde.

---

## Steg 5: Lägg till den andra **color rectangle shape** (grön) och placera den

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

Att sätta `setLeft` (eller `setTop`) flyttar formen relativt till det övre‑vänstra hörnet av **group shapes in Word**‑behållaren. Detta demonstrerar **how to group shapes** med exakt positionering.

---

## Steg 6: **Save document as docx** och verifiera resultatet

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`save`‑metoden skriver automatiskt en `.docx`‑fil eftersom filändelsen är `.docx`. Om du behöver ett annat format (t.ex. PDF), skicka in rätt `SaveFormat`‑enum.

> **Tip:** Se till att målkatalogen (`output/` i detta exempel) finns eller skapa den programatiskt med `new File("output").mkdirs();`.

---

## Fullständig källkod för snabb kopiering‑och‑klistra

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**Förväntat resultat:** När du öppnar `GroupShapeDemo.docx` i Microsoft Word visas en enda sida som innehåller två färgade rektanglar (röd till vänster, grön till höger) som flyttar tillsammans när du markerar gruppen.

---

## Vanliga frågor och hantering av kantfall

| Fråga | Svar |
|----------|--------|
| *Kan jag lägga till fler än två former i samma grupp?* | Ja. Anropa `groupShape.appendChild(yourShape)` för varje ytterligare form. Gruppen kommer automatiskt att ändra storlek för att passa de mest avlägsna gränserna, eller så kan du manuellt justera dess bredd/höjd. |
| *Vad händer om jag behöver en annan formtyp (t.ex. ellips)?* | Byt ut `ShapeType.RECTANGLE` mot `ShapeType.ELLIPSE`. Samma fyllnads‑färglogik gäller. |
| *Behöver jag avlasta `Document`‑objektet?* | Aspose.Words hanterar inhemska resurser internt. När JVM avslutas frigörs resurserna. För långvariga applikationer, anropa `doc.dispose();` om du använder **Aspose.Words for Java (Native)**‑versionen. |
| *Hur ändrar jag Z‑ordningen så att en rektangel visas överst?* | Använd `groupShape.insertAfter(shape, referenceShape);` eller `groupShape.insertBefore(shape, referenceShape);` för att omordna barn inom gruppen. |
| *Kan jag gruppera former över olika sektioner?* | Nej. En `GroupShape` måste finnas inom ett enda stycke eller formbehållare. För att gruppera över sektioner, skapa separata grupper i varje sektion. |

---

## Slutsats

Du vet nu hur du **create blank Word document** med Aspose.Words for Java, **group shapes in Word**, applicerar **color rectangle shape**‑stil, och **save document as docx**. Detta mönster kan skalas till mer komplexa layouter — lägg bara till ytterligare former, justera förskjutningar och eventuellt sätt in text, bilder eller hyperlänkar i gruppen.

**Nästa steg** du kan utforska:

* [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
* [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
* [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}