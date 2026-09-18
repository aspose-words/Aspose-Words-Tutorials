---
category: general
date: 2026-09-18
description: Skapa ett tomt dokument och infoga former i Word med Aspose.Words – lär
  dig hur du lägger till en triangel och mer.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: sv
lastmod: 2026-09-18
og_description: Skapa ett tomt dokument i Word med Aspose.Words och lär dig hur du
  infogar en triangel, grupperar former och annan grafik. Följ den här kompletta guiden.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: Skapa ett tomt dokument och lägg till former i Word – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Hur man skapar ett tomt dokument och lägger till former i Word
url: /sv/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett tomt dokument och lägger till former i Word

Om du behöver **create blank document** och sedan berika det med grafik, visar den här guiden exakt hur. Vi går igenom att skapa en Word‑fil från början och **add shapes to Word**, inklusive **how to insert triangle**‑formen, med hjälp av Aspose.Words för Java.

Du avslutar tutorialen med en färdig *.docx*-fil som innehåller en grupperad form som håller en triangel. Stegen täcker allt från projektuppsättning till att spara den slutgiltiga **create word document**. Inga externa verktyg krävs utöver Aspose.Words.

## Förutsättningar

* Java 17 eller senare installerat  
* Maven eller Gradle för beroendehantering  
* En Aspose.Words för Java-licens (den fria utvärderingen fungerar för den här demonstrationen)  

Om du föredrar ett annat byggsystem, justera beroendesyntaxen därefter. Koden fungerar på alla plattformar som stödjer Java.

## Skapa tomt dokument med Aspose.Words

Den första operationen är att **create blank document** i minnet. Aspose.Words tillhandahåller en `Document`‑klass som representerar en Word‑fil utan något innehåll.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

`new Document()`‑konstruktorn bygger en tom *.docx*-struktur, som du senare kan fylla med stycken, tabeller eller grafik. Eftersom dokumentet är tomt har du full kontroll över varje element du lägger till.

## Lägg till former i Word – infoga en gruppform

En gruppform låter dig behandla flera grafikobjekt som en enhet. Detta är användbart när du vill flytta eller ändra storlek på flera former samtidigt.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` är det primära API‑et för att lägga till innehåll. Anropet `insertGroupShape` skapar en behållare som är 300 × 300 punkter (ungefär 4 × 4 tum). Efter detta anrop placeras markören *inuti* gruppen, redo för ytterligare former.

### Varför använda en gruppform?

Gruppering håller relaterad grafik justerad och gör det enklare att tillämpa enhetlig formatering. Om du senare bestämmer dig för att flytta triangeln, flyttas hela gruppen tillsammans, vilket bevarar layouten.

## Hur man infogar triangel‑form i gruppen

Nu behandlar vi **how to insert triangle**‑formen. Triangeln är ett av de inbyggda `ShapeType`‑värdena.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

`moveTo`‑anropet säkerställer att byggarens infogningspunkt är det första stycket i gruppen. `insertShape` lägger sedan till en triangel som är 60 × 60 punkter. Eftersom markören är inuti gruppen blir triangeln ett barn till gruppformen.

**Add triangle shape** tips:

* Storleken mäts i punkter; 72 punkter motsvarar en tum. Justera dimensionerna efter din layout.  
* Om du behöver en annan orientering, använd `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` för att justera formen inom gruppen.  
* Triangeln ärver gruppens fyllnings- och linjestilar om du inte åsidosätter dem med `shape.getFillColor()` eller `shape.getStrokeColor()`.

## Spara dokumentet – create word document

Efter att ha konstruerat grafiken sparar du filen. Detta steg slutför **create word document**‑operationen.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` skriver den minnesbaserade representationen till disk som ett standard‑Word‑dokument. Du kan öppna `ExtendedGroup.docx` i Microsoft Word, LibreOffice eller någon annan visare som stödjer OOXML‑formatet. Filen visar en grupperad form som innehåller en triangel, exakt som koden byggde.

## Fullt körbart exempel

När alla delar sätts ihop, här är det kompletta programmet som du kan kopiera, kompilera och köra:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### Förväntat resultat

När du öppnar `ExtendedGroup.docx` kommer du att se en enda gruppform som upptar mitten av sidan. Inuti den gruppen visas en liten triangel på standardpositionen. Triangeln kan väljas och flyttas som en del av gruppen, vilket bekräftar att **add shapes to word** fungerade som avsett.

## Vanliga frågor och edge cases

| Fråga | Svar |
|----------|--------|
| *Kan jag lägga till mer än en form i gruppen?* | Ja. Efter att ha infogat triangeln, håll markören i gruppen och anropa `builder.insertShape` igen med en annan `ShapeType`. |
| *Vad händer om jag behöver att triangeln ska vara röd?* | Hämta `Shape` som returneras av `insertShape` och anropa `shape.getFillColor().setColor(Color.RED)`. |
| *Fungerar detta med äldre .doc‑filer?* | Aspose.Words sparar i det format du anger. Använd `doc.save("file.doc", SaveFormat.DOC)` för att skapa ett äldre Word‑dokument. |
| *Hur ändrar jag gruppens kantlinje?* | Använd `group.getStrokeColor().setColor(Color.BLUE)` och `group.setLineWeight(2.0)` för att anpassa konturen. |
| *Finns det ett sätt att rotera triangeln?* | Anropa `shape.getRotation()` för att sätta en vinkel i grader. |

## Pro‑tips

* **Reuse the builder** – att skapa en ny `DocumentBuilder` för varje form ger extra overhead. Behåll en enda builder per dokument.  
* **Unit conversion** – om du arbetar med millimeter, konvertera dem till punkter (`points = mm * 2.83465`).  
* **Performance** – för stora dokument, anropa `doc.updatePageLayout()` endast en gång efter att alla former har lagts till.

## Slutsats

Du vet nu hur man **create blank document**, **add shapes to Word**, och specifikt **how to insert triangle**‑formen med Aspose.Words för Java. Det kompletta exemplet demonstrerar hela arbetsflödet från en tom fil till ett sparat **create word document** som innehåller en grupperad triangel.

Härifrån kan du utforska ytterligare `ShapeType`‑värden, tillämpa anpassad styling eller kombinera flera grupper för att bygga komplexa diagram. Experimentera med olika storlekar, färger och positioner för att bemästra Word‑automatisering i Java.

--- 

*Redo att automatisera din nästa rapport? Klona exemplet, justera dimensionerna och integrera koden i din egen applikation idag.*

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}