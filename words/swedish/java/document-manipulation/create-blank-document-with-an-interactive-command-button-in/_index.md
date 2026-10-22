---
category: general
date: 2026-09-18
description: Skapa ett tomt dokument i Java och lägg till en ActiveX‑knapp. Lär dig
  hur du infogar en kommandoknapp, bygger ett interaktivt formulär och sparar ett
  Word‑dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: sv
lastmod: 2026-09-18
og_description: Skapa ett tomt dokument i Java och bädda in en ActiveX‑kommandoknapp.
  Följ den här steg‑för‑steg‑guiden för att bygga ett interaktivt formulär och spara
  Word‑filen.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Skapa ett tomt dokument med en interaktiv kommandoknapp i Word
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Skapa ett tomt dokument med en interaktiv kommandoknapp i Word med Java
url: /sv/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ett tomt dokument med en interaktiv kommandoknapp i Word med Java

Om du behöver **create blank document** som innehåller en klickbar knapp, visar den här guiden exakt hur du gör det med Aspose.Words for Java. Du kommer att lära dig att bygga ett interaktivt formulär, lägga till en ActiveX‑knapp och slutligen spara Word‑filen—allt i några korta steg.

Att bädda in en kommandoknapp förvandlar en statisk .docx till ett funktionellt formulär som slutanvändare kan interagera med direkt i Microsoft Word. Denna handledning täcker också **how to insert command button**, hantering av vanliga fallgropar och hur man utökar lösningen för mer komplexa formulär.

## Förutsättningar

* Java 17 eller senare (koden kompileras med JDK 17+)
* Aspose.Words for Java 23.9 eller nyare – biblioteket tillhandahåller `Document`, `DocumentBuilder` och `Forms2OleControl`.
* En IDE eller byggverktyg (Maven/Gradle) som kan lägga till Aspose.Words‑beroendet.
* Grundläggande kunskap om Java‑syntax och Word‑dokumentkoncept.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Steg 1: Skapa ett tomt dokument

Den första operationen är att instansiera ett nytt `Document`‑objekt. Detta objekt representerar en tom Word‑fil som är redo för innehåll.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Att skapa ett tomt dokument ger dig en ren canvas, vilket är viktigt när du vill **create word document** programatiskt utan någon förhands‑existerande mall.

## Steg 2: Initiera en DocumentBuilder

`DocumentBuilder` är huvudklassen för att lägga till text, tabeller och formulärkontroller. Den arbetar på det `Document` du just skapade.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Byggaren behåller den aktuella infogningspunkten, så efterföljande kommandon påverkar rätt plats i filen.

## Steg 3: Infoga en Forms2Ole‑kommandoknappkontroll

Aspose.Words exponerar klassen `Forms2OleControl` för ActiveX‑kontroller. För att **add activex button** begär du en `COMMANDBUTTON`‑typ från byggaren.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

`insertForms2OleControl`‑metoden infogar kontrollen på byggarens aktuella markörplats. Eftersom kontrollen är ett ActiveX‑objekt fungerar den endast i skrivbordsversionen av Microsoft Word, inte i Word Online.

## Steg 4: Konfigurera knappens utseende och position

Du kan ställa in knappens rubrik, storlek och placering med kontrollens set‑metoder. Positionsvärden mäts i punkter (1 punkt = 1/72 tum).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Varför konfigurera dessa egenskaper?* Att sätta `Top` och `Left` säkerställer att knappen visas där du förväntar dig på sidan, medan `Caption` definierar den användarsynliga etiketten. Om du hoppar över bredd/höjd tilldelar Word standarddimensioner, vilket kanske inte matchar din design.

### Proffstips
Om du planerar att lägga till flera kontroller, anropa `builder.moveToDocumentEnd()` före varje infogning för att undvika överlappande objekt.

## Steg 5: Spara dokumentet med den inbäddade kommandoknappen

Slutligen skriver du dokumentet till disk. Filändelsen måste vara `.docx` (eller `.doc` för äldre Word‑versioner) för att bevara ActiveX‑kontrollen.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

När du öppnar `CommandButton.docx` i Microsoft Word kommer du att se en knapp med etiketten **Click Me**. Att klicka på den utlöser standard‑ActiveX‑åtgärden (som som standard inte gör något). Du kan senare bifoga ett makro eller VBA‑script för att definiera anpassat beteende.

## Hur man infogar kommandoknapp i ett befintligt formulär (valfritt)

Om du redan har ett formulär med textfält och vill **create interactive form** som inkluderar en knapp, följ dessa extra steg:

1. Läs in det befintliga dokumentet: `Document doc = new Document("ExistingForm.docx");`
2. Flytta byggaren till önskad plats: `builder.moveToParagraph(5, 0); // 6:e stycket, första noden`
3. Infoga knappen som visat i Steg 3.
4. Justera knappens `Top`/`Left` baserat på styckets layout.

Detta tillvägagångssätt låter dig berika vilken förbyggd Word‑mall som helst med en ActiveX‑knapp utan att återskapa hela filen.

## Kantfall och felsökning

| Situation | Vad att kontrollera | Rekommenderad åtgärd |
|-----------|---------------------|----------------------|
| Knappen visas inte i Word | Se till att du öppnade filen i skrivbordsversionen av Word (Word Online tar bort ActiveX). | Öppna filen i Word 2016+ på skrivbordet. |
| Rubriken är avkortad | Verifiera att knappens bredd är tillräckligt stor för att rymma texten. | Öka `setWidth` tills rubriken får plats. |
| Spara kastar `IOException` | Bekräfta att målkatalogen finns och att du har skrivbehörighet. | Skapa katalogen eller kör programmet med förhöjda rättigheter. |
| Flera knappar överlappar | Byggarens markör kanske inte har flyttats efter den föregående infogningen. | Anropa `builder.moveToDocumentEnd()` innan du infogar varje ny kontroll. |

## Fullt körbart exempel

Nedan är ett komplett, självständigt Java‑program som du kan kopiera, kompilera och köra. Det demonstrerar **create blank document**, **add activex button** och **save word document** i ett flöde.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Förväntad output**

```
Document created: CommandButton.docx
```

När du öppnar `CommandButton.docx` visas en enda sida med en knapp märkt **Click Me** placerad 100 pt från toppen och vänster kant.

## Slutsats

Du vet nu hur du **create blank document**, bäddar in en **ActiveX button**, och förvandlar en vanlig Word‑fil till ett **interactive form**. Genom att behärska **how to insert command button** kan du utöka detta mönster för att lägga till kryssrutor, kombinationsrutor eller till och med anpassad VBA‑driven logik.

Nästa, överväg att utforska dessa relaterade ämnen:

* **Create interactive form** med textfält (`builder.insertField`)  
* **Add activex button** som kör ett VBA‑macro (`builder.insertOleObject`)  
* **Create word document** från en mall med `Document(docTemplatePath)`  
* Konvertera den resulterande .docx till PDF samtidigt som knappen bevaras (obs: PDF kommer att rendera knappen som en statisk bild).

Känn dig fri att experimentera med knappens storlek, position och rubrik för att matcha din UI‑design. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man skapar formulärfält och lägger till innehåll med DocumentBuilder i Aspose.Words för Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Skapa Vba‑projekt i Word‑dokument](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Skapa nytt Word‑dokument](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}