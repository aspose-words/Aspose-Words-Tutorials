---
category: general
date: 2026-07-16
description: Ställ in knappens storlek programatiskt i ett Word‑dokument med Aspose.Words
  för Java. Lär dig hur du infogar en ActiveX‑knapp, anger knappens placering och
  mer.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: sv
lastmod: 2026-07-16
og_description: Ställ in knappstorlek i ett Word‑dokument med Java. Denna steg‑för‑steg‑guide
  visar hur man infogar en ActiveX‑knapp, ställer in knappens placering och programatiskt
  lägger till knappen.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Ställ in knappstorlek i Word med Java – Fullständig Aspose.Words-handledning
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Ställ in knappstorlek i Word med Java – Komplett Aspose.Words-guide
url: /sv/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in knappstorlek i Word med Java – Komplett Aspose.Words-guide

Har du någonsin funderat på hur du **ställer in knappstorlek** i en Word‑fil utan att öppna UI‑gränssnittet? Du är inte ensam. När du behöver generera ett formulärifyllt dokument i farten – till exempel ett introduktionspaket med en “Submit”-knapp – sparar ett programatiskt tillvägagångssätt timmar av manuellt arbete.

I den här handledningen går vi igenom exakt hur du **infogar ActiveX‑knapp**, justerar dess dimensioner, placerar den korrekt och slutligen sparar filen. När du är klar kan du **programmeringsmässigt lägga till knapp**‑kontroller i vilket Word‑dokument som helst med Aspose.Words för Java.

## Förutsättningar – Vad du behöver innan du börjar

- **Java Development Kit (JDK) 8+** – koden körs på vilken modern JDK som helst.  
- **Aspose.Words for Java**‑biblioteket (ladda ner den senaste JAR‑filen från den officiella webbplatsen).  
- En **IDE** du föredrar – IntelliJ IDEA, Eclipse eller till och med en enkel textredigerare fungerar.  
- Grundläggande kunskap om Java‑syntax; ingen djup Word‑automatiseringskunskap krävs.

> *Pro tip:* Håll Aspose.Words‑JAR‑filen på ditt projekts classpath, annars får du `ClassNotFoundException` så snart du försöker importera `com.aspose.words.*`.

## Steg 1: Skapa ett nytt Word‑dokument

Det första vi gör är att starta ett tomt dokument och en `DocumentBuilder`. Tänk på buildern som en penna som låter oss rita vad som helst i filen.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Varför detta är viktigt:** `Document`‑objektet representerar hela .docx‑filen, medan `DocumentBuilder` är arbetshästen som låter oss infoga stycken, tabeller och – ja – ActiveX‑kontroller.

## Steg 2: Infoga ActiveX‑knapp – “Infoga ActiveX‑knapp”-ögonblicket

Nu infogar vi faktiskt **activex‑knapp** i dokumentet. Aspose.Words erbjuder en bekväm metod `insertForms2OleControl` som returnerar ett `Forms2OleControl`‑objekt.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *Vad händer under huven?* `Forms2OleControlType.COMMAND_BUTTON` talar om för Word att vi vill ha en klassisk CommandButton, samma typ som du skulle dra från fliken Developer i UI‑gränssnittet.

## Steg 3: Ställ in knappstorlek och -position – Kärnlogiken för “Set Button Size”

Här kommer huvudnyckelordet i spel. Vi **ställer in knappstorlek** och även **ställer in knappens position** så att kontrollen visas exakt där vi vill ha den på sidan.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Varför du bör bry dig:** Punkt är den inbyggda måttenheten i Word (1 punkt = 1/72 tum). Genom att justera `setLeft`, `setTop`, `setWidth` och `setHeight` får du pixel‑perfekt kontroll – ingen mer “det ser rätt ut på min skärm men inte på skrivaren”.

> *Vanligt fallgropp:* Att glömma att ange antingen bredd eller höjd lämnar knappen i standardstorlek, vilket kan bli för litet att klicka på. Ange alltid båda.

## Steg 4: Spara dokumentet – “Create Word Document Button” slutfört

Till sist skriver vi filen till disk. Namnet antyder att vi **skapar en Word‑dokument‑knapp** i en .docx.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

När du öppnar `CommandButtonDemo.docx` i Microsoft Word ser du en **Submit**‑knapp placerad 100 pt från vänster kant och 150 pt från toppen, med storleken 80 × 30 pt. Att klicka på den i UI‑gränssnittet triggar standard‑ActiveX‑beteendet (som du senare kan koppla till VBA om så önskas).

### Förväntad utskriftsbild

![Word-dokument som visar den infogade knappen med den inställda knappstorleken](https://example.com/images/set-button-size.png "Skärmdump av en Word-fil där knappstorleken har ställts in med Aspose.Words för Java")

*Alt‑text:* set button size in a Word document using Java

## Steg 5 (Valfritt): Lägg till fler kontroller eller stilisera knappen

Om du behöver **programmeringsmässigt lägga till knapp**‑kontroller utöver en enda Submit‑knapp, upprepa bara infogningsblocket med nya namn och rubriker. Du kan också justera teckensnitt, bakgrundsfärg eller till och med binda VBA‑makron senare.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Tips:* Håll alla knappdimensioner konsekventa för ett professionellt utseende. Ett snabbt sätt är att lagra bredd/höjd i konstanter.

## Vanliga frågor & kantfall

### “Kan jag ställa in knappstorlek med centimeter istället för punkter?”
Word‑API:t accepterar bara punkter, men du kan konvertera centimeter till punkter (`points = cm * 28.3465`). Skriv en liten hjälpfunktion om du föredrar metriska enheter.

### “Vad händer om jag vill att knappen ska visas på en specifik sida?”
Efter att ha infogat knappen kan du flytta markören till en viss sida med `builder.moveToPage(pageNumber)`. Infoga kontrollen direkt efter flytten och ställ sedan in dess position som ovan.

### “Fungerar detta med .doc (Word 97‑2003)‑filer?”
Ja – Aspose.Words hanterar automatiskt äldre format. Ändra bara filändelsen i `doc.save("Demo.doc")`.

## Fullt, körbart exempel

Nedan är hela programmet som du kan kopiera‑klistra in i en Java‑klass och köra omedelbart (förutsatt att Aspose.Words‑JAR‑filen finns på classpath).

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Kör programmet, öppna den genererade `CommandButtonDemo.docx`, och du kommer att se två snyggt dimensionerade knappar redo för interaktion.

## Slutsats – Du har bemästrat att ställa in knappstorlek i Word

Vi har just gått igenom en komplett, end‑to‑end‑lösning för **set button size** och **set button location** med Aspose.Words för Java. Genom att följa stegen kan du **infoga activex‑knapp**, **programmeringsmässigt lägga till knapp**‑kontroller och slutligen **skapa word document button**‑element som beter sig exakt som du behöver.

Vad blir nästa steg? Prova att bädda in knappen i en tabellcell, eller fäst ett VBA‑makro som validerar formulärfält innan inskickning. Samma mönster fungerar för andra ActiveX‑kontroller som kryssrutor eller kombinationsrutor – byt bara `Forms2OleControlType.COMMAND_BUTTON` mot rätt enum‑värde.

Om du stöter på problem, lämna en kommentar nedan. Lycka till med kodandet, och njut av kraften i automatiserad Word‑dokumentgenerering!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to remove footers from Word documents using Aspose.Words for Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java&#58; Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}