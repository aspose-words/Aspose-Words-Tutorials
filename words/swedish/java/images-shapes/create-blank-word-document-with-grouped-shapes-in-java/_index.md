---
category: general
date: 2026-08-07
description: Skapa ett tomt Word‑dokument med grupperade former i Java med Aspose.Words.
  Lär dig hur du grupperar former, ställer in formens storlek och lägger till former
  i Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: sv
lastmod: 2026-08-07
og_description: Skapa ett tomt Word‑dokument med grupperade former i Java. Följ den
  här guiden för att ställa in formens storlek, lägga till former i Word och lära
  dig hur du grupperar former.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Skapa tomt Word-dokument med grupperade former – Java-handledning
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Skapa tomt Word-dokument med grupperade former i Java
url: /sv/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa tomt Word‑dokument med grupperade former i Java

Om du behöver **skapa tomt Word‑dokument** som innehåller flera former arrangerade som en enhet, visar den här handledningen exakt hur du gör. Du får ett komplett, körbart exempel som demonstrerar **hur man grupperar form**‑objekt, justerar deras dimensioner och **lägger till former i Word** med Aspose.Words för Java.

Guiden går igenom varje steg – från projektuppsättning till sparande av den färdiga .docx‑filen – så att du kan kopiera koden direkt in i ditt eget program. Inga externa referenser krävs, och lösningen fungerar med Aspose.Words 23.9 eller senare.

## Förutsättningar

Innan du börjar, se till att du har:

* Java 17 (eller någon annan stödjande JDK)
* Maven eller Gradle för beroendehantering
* En Aspose.Words för Java‑licens (eller en tillfällig utvärderingsnyckel)
* En exempelbildfil (t.ex. `sample.jpg`) placerad i en känd katalog

Om någon av dessa komponenter saknas, installera dem först; resten av handledningen förutsätter att miljön är klar.

## Steg 1: Lägg till Aspose.Words i ditt projekt

Lägg till Aspose.Words‑beroendet i din `pom.xml` (Maven) eller `build.gradle` (Gradle). Detta bibliotek tillhandahåller klasserna `Document`, `DocumentBuilder`, `GroupShape` och `Shape` som används senare.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Varför detta är viktigt:** Utan biblioteket finns inga av Word‑bearbetnings‑API:erna tillgängliga, och du kan inte **skapa tomt Word‑dokument** programatiskt.

## Steg 2: Skapa ett tomt Word‑dokument

Den första konkreta handlingen är att instansiera ett `Document`‑objekt, vilket representerar ett **tomt Word‑dokument** i minnet.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* skapar ett **tomt Word‑dokument** med standardinställningar (A4‑sida, standardmarginaler). Den medföljande `DocumentBuilder` låter dig infoga innehåll vid den aktuella markörpositionen.

## Steg 3: Infoga en gruppform (hur man grupperar form)

En *gruppform* fungerar som en behållare för andra former. I detta steg lär du dig **hur man grupperar form**‑objekt så att de flyttas tillsammans.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

Metoden `insertGroupShape` placerar behållaren vid builderns markörposition. Gruppering är avgörande när du vill behandla flera ritningar som en enda enhet – detta är kärnan i **group shapes word**‑funktionaliteten.

## Steg 4: Skapa en rektangel och ange dess storlek

Lägg nu till en rektangel i gruppen. Detta demonstrerar **set shape size**, vilket är nödvändigt för exakt layout.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Varför ange dimensioner?* Genom att explicit anropa `setWidth` och `setHeight` garanteras att rektangeln visas exakt som avsett, oavsett dokumentets standardform‑stilar.

## Steg 5: Infoga en bild och lägg till den i gruppen

Att lägga till en bild visar ett annat vanligt användningsfall för **add shapes to word**. Bilden blir en del av samma grupp och flyttar tillsammans med rektangeln.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

Om bildfilen saknas kastar Aspose.Words ett undantag. Ett praktiskt tips är att verifiera sökvägen i förväg:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## Steg 6: Spara dokumentet som innehåller de grupperade formerna

Till sist, skriv ut det **tomma Word‑dokumentet** (nu fyllt med en gruppform) till disk.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

När du öppnar `GroupShapeDemo.docx` i Microsoft Word ser du ett enda grupperat objekt som innehåller en rektangel och en bild. Att markera någon del av gruppen flyttar hela behållaren, vilket bekräftar att formerna har **grupperats** korrekt.

### Förväntat resultat

* En fil med namnet `GroupShapeDemo.docx` i den angivna katalogen.  
* När filen öppnas visas en 300 × 200‑punkts behållare med:  
  * En 100 × 50‑punkts rektangel placerad på (20, 20).  
  * En bild placerad på (150, 30) i samma behållare.

## Kantfall och variationer

| Situation | Hur du hanterar det |
|-----------|---------------------|
| **Olika sidstorlek** | Anropa `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` innan du infogar gruppen. |
| **Flera grupper** | Upprepa steg 3‑5 med en ny `GroupShape`‑instans; varje grupp kan placeras oberoende. |
| **Rotera former** | Använd `shape.setRotationAngle(45.0);` för att rotera en rektangel eller bild innan du lägger till den i gruppen. |
| **Icke‑bildformer** | Skapa `Shape`‑objekt av typen `ShapeType.ELLIPSE`, `ShapeType.LINE` osv., och lägg till dem på samma sätt som rektangeln. |
| **Stora bilder** | Skala bilden med `picture.setWidth(80.0); picture.setHeight(60.0);` för att hålla gruppen inom sina ursprungliga gränser. |

Dessa variationer låter dig anpassa kärnmönstret till ett brett spektrum av dokumentgenererings‑scenarier.

## Praktiska tips från erfarenhet

* **Proffstips:** Ställ in gruppens `RelativeHorizontalPosition` och `RelativeVerticalPosition` till `RelativeHorizontalPosition.PAGE` respektive `RelativeVerticalPosition.PAGE` om du vill att gruppen ska förankras till sidan snarare än markören.  
* **Se upp för:** Att lägga till en form som överskrider gruppens dimensioner; formen kommer att beskäras i Word. Justera gruppens storlek med `group.setWidth()` och `group.setHeight()` efter behov.  
* **Prestanda‑notering:** Om du genererar många dokument i en loop, återanvänd en enda `DocumentBuilder`‑instans och anropa `doc.clone()` för att minska overhead för objekt‑skapande.

## Slutsats

Du vet nu hur du **skapar tomt Word‑dokument** som innehåller en grupperad samling former med Aspose.Words för Java. Handledningen täckte hela arbetsflödet: installera biblioteket, skapa dokumentet, infoga en grupp, **set shape size**, **add shapes to word**, och spara resultatet.

Härifrån kan du utforska mer avancerade funktioner såsom att gruppera diagram, applicera stilar på enskilda former, eller exportera dokumentet till PDF. Alla dessa ämnen bygger på samma principer som demonstrerats i den här guiden.

---


## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}