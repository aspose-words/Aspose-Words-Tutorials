---
category: general
date: 2026-08-14
description: Skapa en docx ActiveX‑knapp i Java med Aspose.Words. Lär dig hur du programatiskt
  lägger till en formulärknapp i Word och sparar dokumentet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: sv
lastmod: 2026-08-14
og_description: Skapa ActiveX‑knapp i docx med Java och Aspose.Words. Denna guide
  visar hur du lägger till en formulärknapp i Word, konfigurerar den och sparar filen.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: Skapa docx ActiveX‑knapp i Java – steg‑för‑steg‑handledning
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: Skapa docx ActiveX‑knapp i Java – komplett programmeringsguide
url: /sv/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa docx ActiveX‑knapp i Java – komplett programmeringsguide

Om du behöver **create docx ActiveX button** i Java, guidar den här guiden dig genom hela processen. Du kommer att se hur du lägger till en formulärknapp i Word, konfigurerar dess egenskaper och skapar en färdig‑att‑använda .docx‑fil.

Att arbeta med ActiveX‑kontroller är ett vanligt krav när man automatiserar äldre Word‑formulär. I den här tutorialen kommer du att lära dig att **add form button word** dokument med hjälp av Aspose.Words for Java‑biblioteket, så att du kan bädda in interaktiva kontroller utan manuell redigering.

## Vad du behöver

* Java 17 eller senare (koden kompileras med tidigare versioner, men Java 17 rekommenderas).
* Aspose.Words for Java 23.10 eller nyare – ladda ner JAR‑filen från Aspose‑webbplatsen eller lägg till Maven‑beroendet.
* En IDE (IntelliJ IDEA, Eclipse eller VS Code) eller en enkel textredigerare och kommandorads‑byggverktyg.
* Grundläggande kunskap om Java‑syntax och objekt‑orienterad programmering.

## Så skapar du docx ActiveX button med Aspose.Words

Följande steg visar den exakta sekvensen som krävs för att **create docx ActiveX button**‑objekt och bädda in dem i ett Word‑dokument.

### Steg 1: Ställ in projektet och importera Aspose.Words

Lägg till Aspose.Words‑beroendet i din `pom.xml` om du använder Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Eller, om du föredrar Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

När beroendet har lösts, importera de nödvändiga klasserna i din Java‑källfil:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

Dessa importeringar ger dig åtkomst till `Document`, `DocumentBuilder` och `Forms2OleControl`‑API‑et som används för att infoga ActiveX‑kontroller.

### Steg 2: Skapa ett nytt tomt dokument

Instansiera ett `Document`‑objekt, som representerar en tom Word‑fil redo att ta emot innehåll.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

Att skapa dokumentet först säkerställer att den efterföljande buildern arbetar på en ren canvas.

### Steg 3: Initiera en DocumentBuilder

`DocumentBuilder` erbjuder ett flytande gränssnitt för att infoga text, bilder och kontroller. Anslut den till dokumentet du just skapade.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

Buildern spårar den aktuella markörpositionen i dokumentet, så nästa infogning sker exakt där du behöver den.

### Steg 4: Infoga en ActiveX CommandButton‑kontroll

Använd metoden `insertForms2OleControl` för att bädda in en ActiveX `CommandButton`. Denna metod returnerar en `Forms2OleControl`‑instans som du kan konfigurera vidare.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

Vid detta tillfälle innehåller .docx‑filen en platshållare för en knapp, men den har ännu ingen visuell rubrik eller storlek.

### Steg 5: Konfigurera knappens egenskaper

Ställ in kontrollens namn, rubrik och layout‑attribut. Dessa värden bestämmer hur knappen visas i Word och hur du senare kan referera till den via VBA eller automationsskript.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **Pro tip:** Word mäter positioner i punkter (1 pt ≈ 1/72 in). Justera `setTop` och `setLeft` för att aligna knappen med omgivande innehåll.

### Steg 6: Spara dokumentet

Skriv slutligen dokumentet till disk. Använd filändelsen `.docx` för att behålla filen i det moderna Office Open XML‑formatet.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

När du öppnar den resulterande filen i Microsoft Word kommer du att se en **Submit**‑knapp placerad på de koordinater du angav. Att klicka på knappen i Word kommer inte att utlösa någon åtgärd om du inte bifogar VBA‑kod, men kontrollen är fullt funktionell för formulärbaserade arbetsflöden.

## Vanliga frågor och specialfall

| Fråga | Svar |
|----------|--------|
| **Behöver jag en speciell Word‑version?** | ActiveX‑kontroller stöds i skrivbordsversionen av Microsoft Word på Windows. De är inte tillgängliga i Word för Mac eller Word Online. |
| **Kan jag använda detta med `.doc`‑filer?** | Ja. Spara dokumentet med filändelsen `.doc` (`document.save("ActiveXButton.doc")`). Samma API fungerar för det äldre binära formatet. |
| **Vad händer om knappen inte visas?** | Säkerställ att **File → Options → Trust Center → Trust Center Settings → ActiveX Settings** tillåter ActiveX‑kontroller. Verifiera också att dokumentet inte öppnas i “Protected View”. |
| **Kan jag lägga till andra ActiveX‑kontroller?** | Absolut. Byt ut `Forms2OleControlType.COMMAND_BUTTON` mot `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` osv. |
| **Finns det någon storleksgräns?** | Kontrollens storlek begränsas endast av sidlayouten. Mycket stora dimensioner kan orsaka layout‑översvämning. |

## Fullt, körbart exempel

Nedan finns en komplett Java‑klass som du kan kopiera, kompilera och köra. Den inkluderar alla importeringar, huvudmetoden och inline‑kommentarer för tydlighet.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Förväntat resultat:** Efter att programmet har körts visas `ActiveXButton.docx` i arbetskatalogen. När du öppnar den i Microsoft Word visas en klickbar **Submit**‑knapp placerad nära övre‑vänstra hörnet på första sidan.

## Slutsats

Du vet nu hur du **create docx ActiveX button**‑objekt i Java med Aspose.Words, och du har sett hur du **add form button word** dokument programatiskt. Stegen – att sätta upp projektet, skapa ett dokument, infoga kontrollen, konfigurera dess egenskaper och spara – täcker hela arbetsflödet från början till slut.

Nästa steg kan vara att utforska:

* Lägga till VBA‑makron som svarar på knapptryckningen.
* Bädda in andra ActiveX‑kontroller såsom kryssrutor eller listrutor.
* Automatisera genereringen av flersidiga formulär med flera interaktiva element.

Känn dig fri att experimentera med storlekar, positioner och rubriker för att matcha dina specifika formulärdesign‑krav. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}