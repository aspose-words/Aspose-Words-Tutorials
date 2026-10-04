---
category: general
date: 2026-10-04
description: Lär dig hur du initierar DocumentBuilder för ett nytt dokument och lägger
  till en ActiveX‑knapp med Aspose.Words i Java. Steg‑för‑steg‑guide med fullständig
  kod.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: sv
lastmod: 2026-10-04
og_description: Initiera DocumentBuilder för ett nytt dokument och bädda in en ActiveX‑kommandoknapp
  med Aspose.Words Java API. Följ den här korta handledningen.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: Initiera DocumentBuilder för ett nytt dokument – komplett Aspose.Words‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Hur man initierar DocumentBuilder för ett nytt dokument med Aspose.Words
url: /sv/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man initierar DocumentBuilder för ett nytt dokument med Aspose.Words

Om du behöver **initiera DocumentBuilder för ett nytt dokument** i ett Java‑projekt, visar den här handledningen de exakta stegen. Du kommer att se hur du skapar en tom Word‑fil, bifogar en ActiveX‑knapp och sparar resultatet – allt med ett enda, självständigt kodexempel.

Att programatiskt arbeta med Word‑dokument innebär ofta att hantera lågnivådetaljer som formulärkontroller. I slutet av den här guiden kommer du att kunna bädda in en ActiveX‑knapp utan att lämna din IDE, vilket är användbart för att generera mallar, automatiserade rapporter eller interaktiva formulär.

## Förutsättningar

* Java 17 eller senare installerat  
* Maven 3.8+ (eller Gradle om du föredrar)  
* En Aspose.Words for Java‑licens (gratis provversion fungerar för testning)  
* Grundläggande kunskap om Java‑syntax  

Om du är ny på Aspose.Words, så erbjuder biblioteket ett hög‑nivå‑API för att skapa, redigera och spara Word‑dokument. Klassen `DocumentBuilder` är huvudingångspunkten för att konstruera dokumentinnehåll.

## Steg 1: Ställ in Maven‑projektet

Skapa ett nytt Maven‑projekt (eller lägg till i ett befintligt) och inkludera Aspose.Words‑beroendet:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Proffstips:** Håll biblioteksversionen uppdaterad; nyare versioner lägger till stöd för ytterligare formulärkontroller och förbättrar prestanda.

## Steg 2: Initiera `DocumentBuilder` för ett nytt dokument

Kärnan i handledningen är **initiera DocumentBuilder för ett nytt dokument**‑operationen. Du skapar först en tom `Document`‑instans och skickar sedan den till `DocumentBuilder`‑konstruktorn.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta är viktigt:* Initiering av `DocumentBuilder` binder byggaren till ett specifikt `Document`‑objekt, vilket gör att du kan lägga till stycken, tabeller eller formulärkontroller direkt i det dokumentet. Utan detta steg skulle byggaren sakna ett mål att arbeta på.

## Steg 3: Infoga en ActiveX‑kommandomakroknapp‑kontroll

Aspose.Words exponerar klassen `Forms2OleControl` för att bädda in äldre ActiveX‑kontroller. Följande kod lägger till en **Forms2OleControl‑kommandomakroknapp** på den aktuella markörpositionen.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### Vad är en ActiveX‑kommandomakroknapp?

En ActiveX‑kommandomakroknapp är ett äldre UI‑element som kan köra makron eller utlösa händelser när en användare klickar på den i ett Word‑dokument. Även om moderna Office‑versioner föredrar innehållskontroller, förlitar sig många företagsmallar fortfarande på ActiveX för bakåtkompatibilitet.

## Steg 4: Spara dokumentet

Efter att ha infogat kontrollen anropar du helt enkelt `save`. Filen kommer att innehålla ActiveX‑knappen och kan öppnas i Microsoft Word.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

När du öppnar `ActiveXButton.docx` i Word ser du en knapp med etiketten **Click Me**. Att klicka på knappen gör ingenting om du inte bifogar ett makro, men själva kontrollen är fullt funktionell.

## Fullt, körbart exempel

Nedan är det kompletta programmet som du kan kopiera‑och‑klistra in i `src/main/java/com/example/ActiveXButtonDemo.java`. Det innehåller alla importeringar och felhantering som behövs för ett snabbt test.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Förväntat resultat**

```
Document saved to output/ActiveXButton.docx
```

Öppna den genererade filen i Microsoft Word 2016 eller senare; du bör se en knapp med etiketten *Click Me* placerad högst upp på den första sidan.

## Vanliga variationer och kantfall

| Scenario | Adjustment |
|----------|------------|
| **Lägg till knappen i ett specifikt stycke** | Flytta byggarens markör med `builder.moveToParagraph(index, NodeType.PARAGRAPH);` innan du anropar `insertForms2OleControl`. |
| **Ställ in knappens storlek** | Använd `commandButton.setWidth(100);` och `commandButton.setHeight(30);` för att definiera dimensioner i punkter. |
| **Lägg till ett makro på knappen** | Efter att ha sparat dokumentet, öppna det i Word, aktivera fliken Utvecklare och bifoga ett VBA‑makro till knappen manuellt (ActiveX‑kontroller kan inte skriptas direkt från Aspose.Words). |
| **Mål .doc (binärt) format** | Ändra `doc.save(outputPath, SaveFormat.DOC);` för att producera en äldre Word 97‑2003‑fil. |
| **Kör på Android** | Använd Aspose.Words för Android via dess Java‑API; samma kod fungerar så länge biblioteket är inkluderat i APK‑filen. |

## Felsökningstips

* **`java.lang.NoClassDefFoundError`** – Se till att Aspose.Words‑JAR‑filen finns på klassvägen. Maven lägger automatiskt till den; för manuella byggen, placera JAR‑filen i `libs/` och lägg till den i ditt IDE:s bibliotek.  
* **Button does not appear in Word** – Verifiera att alternativet *Show legacy forms* är aktiverat i Word:s Trust Center (`File → Options → Trust Center → Trust Center Settings → Macro Settings`).  
* **License exception** – Om du kör koden utan en giltig licens kommer Aspose.Words att infoga ett vattenstämpel. Registrera en gratis provversion eller köp en licens för att ta bort den.

## Slutsats

Du vet nu hur du **initierar DocumentBuilder för ett nytt dokument**, infogar en ActiveX‑kommandomakroknapp och sparar resultatet med Aspose.Words för Java. Detta mönster låter dig generera interaktiva Word‑mallar programatiskt, vilket är särskilt praktiskt för automatiserad rapportering eller formulär‑drivna arbetsflöden.

Härifrån kan du utforska ytterligare formulärkontroller (`Forms2OleControlType.CHECKBOX`, `COMBOBOX`, etc.), kombinera knappen med anpassade VBA‑makron, eller generera fullständiga dokument som inkluderar tabeller, bilder och formatering – allt med samma `DocumentBuilder`‑arbetsflöde.

---

*Redo att bygga mer komplex Word‑automation? Kolla in våra guider om **insert table with DocumentBuilder**, **apply styles programmatically**, och **export to PDF with Aspose.Words**.*

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig behärska ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man skapar formulärfält och lägger till innehåll med DocumentBuilder i Aspose.Words för Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Hur man sparar dokument som PDF med Aspose.Words för Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Lägg till ett vattenstämpel i ett dokument med Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}