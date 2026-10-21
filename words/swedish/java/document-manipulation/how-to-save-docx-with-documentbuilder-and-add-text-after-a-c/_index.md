---
category: general
date: 2026-10-07
description: Lär dig hur du sparar docx med DocumentBuilder, infogar en vanlig textkontroll
  och lägger till text efter kontrollen i en enda guide.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx with DocumentBuilder
- add text after control
- insert plain text control
language: sv
lastmod: 2026-10-07
og_description: Spara docx med DocumentBuilder, infoga en vanlig textkontroll och
  lägg till text efter kontrollen med Aspose.Words för Java i den här steg‑för‑steg‑handledningen.
og_image_alt: Screenshot showing a DOCX file created with DocumentBuilder after inserting
  a plain text control
og_title: Spara docx med DocumentBuilder – infoga enkeltextkontroll och lägg till
  text efter kontrollen
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save docx with DocumentBuilder, insert plain text control,
    and add text after control in a single guide.
  headline: How to save docx with DocumentBuilder and add text after a control
  type: TechArticle
- description: Learn how to save docx with DocumentBuilder, insert plain text control,
    and add text after control in a single guide.
  name: How to save docx with DocumentBuilder and add text after a control
  steps:
  - name: Prerequisites
    text: '* Java 17 or newer installed. * Maven 3.6+ for dependency management. *
      Basic familiarity with Java syntax and object‑oriented programming.'
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for constructing Word documents
      programmatically. * `insertStructuredDocumentTag` creates a **plain text control**
      (also called an SDT) that appears as a content control in Word. * Setting `Title`
      and `PlaceholderName` provides metadata and a hint for the end‑u'
  - name: Expected output screenshot (alt text for accessibility)
    text: '*Alt text:* “Word document showing a plain text content control labeled
      CustomerName followed by the line ‘After the tag’.”'
  type: HowTo
tags:
- Aspose.Words
- Java
- DocumentBuilder
title: Hur man sparar docx med DocumentBuilder och lägger till text efter en kontroll
url: /sv/java/document-manipulation/how-to-save-docx-with-documentbuilder-and-add-text-after-a-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man sparar docx med DocumentBuilder och lägger till text efter en kontroll

Om du behöver **save docx with DocumentBuilder**, visar den här handledningen exakt hur du gör det. Du kommer att se hur du **insert plain text control**, sätter dess titel och platshållare, och sedan **add text after control** så att det slutliga dokumentet läses naturligt.

I avsnitten nedan täcker vi allt från projektuppsättning till kantfalls‑hantering, så att du kan kopiera‑klistra in ett komplett, körbart exempel i ditt eget Java‑projekt. Inga externa referenser krävs – bara koden och förklaringarna som finns här.

## Vad du kommer att lära dig

* Hur du konfigurerar Aspose.Words för Java i ett Maven‑projekt.  
* Hur du **insert plain text control** (en Structured Document Tag) med `DocumentBuilder`.  
* Hur du **add text after control** så att det omgivande innehållet flyter korrekt.  
* Hur du **save docx with DocumentBuilder** till en vald mapp.  
* Tips för att anpassa kontrollens utseende, hantera tomma platshållare och återanvända byggaren för flera taggar.

### Förutsättningar

* Java 17 eller nyare installerat.  
* Maven 3.6+ för beroendehantering.  
* Grundläggande kunskap om Java‑syntax och objekt‑orienterad programmering.

---

## Steg 1: Ställ in Maven‑projektet och lägg till Aspose.Words

Först, skapa ett nytt Maven‑projekt (eller lägg till i ett befintligt). Inkludera Aspose.Words för Java‑beroendet i din `pom.xml`:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version at the time of writing -->
    </dependency>
</dependencies>
```

> **Pro tip:** Aspose.Words är ett kommersiellt bibliotek, men en gratis utvärderingslicens fungerar för utveckling. Registrera dig på Aspose‑webbplatsen för att få en licensfil och ladda den vid körning för att undvika vattenstämplar.

## Steg 2: Skapa Java‑klassen och importera nödvändiga typer

Skapa en klass med namnet `DocxBuilderDemo`. Importera de klasser som behövs för att arbeta med `DocumentBuilder`, `StructuredDocumentTag` och utseende‑enum‑en.

```java
package com.example.docx;

import com.aspose.words.*;

public class DocxBuilderDemo {

    public static void main(String[] args) throws Exception {
        // Initialize the license if you have one (optional)
        // License license = new License();
        // license.setLicense("Aspose.Words.Java.lic");

        // Step 3: Build the document and insert the plain text control
        buildDocument();
    }

    private static void buildDocument() throws Exception {
        // Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text Structured Document Tag (SDT) with default appearance
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, SdtAppearanceTags.DEFAULT);

        // Set the tag's title and placeholder text to guide the user
        sdt.setTitle("CustomerName");
        sdt.setPlaceholderName("Enter name");

        // Step 4: Add regular content after the SDT
        builder.writeln("After the tag");

        // Step 5: Save the resulting document – this is where we **save docx with DocumentBuilder**
        String outputPath = "output/SDT.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### Varför detta fungerar

* `DocumentBuilder` är det primära API‑et för att programatiskt konstruera Word‑dokument.  
* `insertStructuredDocumentTag` skapar en **plain text control** (även kallad en SDT) som visas som en innehållskontroll i Word.  
* Att sätta `Title` och `PlaceholderName` ger metadata och en ledtråd till slutanvändaren.  
* `writeln` lägger till ett nytt stycke **after the control**, vilket uppfyller kravet **add text after control**.  
* Slutligen sparar `doc.save` **saves docx with DocumentBuilder** till filsystemet.

## Steg 3: Kör exemplet och verifiera resultatet

1. Kompilera projektet med `mvn clean compile`.  
2. Kör `DocxBuilderDemo`‑klassen (`mvn exec:java -Dexec.mainClass="com.example.docx.DocxBuilderDemo"`).  
3. Öppna `output/SDT.docx` i Microsoft Word eller LibreOffice.

Du bör se ett dokument som innehåller:

* En innehållskontroll med titeln **CustomerName** och platshållaren “Enter name”.  
* Texten **After the tag** på nästa rad.

### Förväntad skärmbild (alt‑text för tillgänglighet)

*Alt text:* “Word‑dokument som visar en plain text‑innehållskontroll märkt CustomerName följt av raden ‘After the tag’.”

## Steg 4: Anpassa kontrollens utseende (valfritt)

Om du vill att kontrollen ska se annorlunda ut – t.ex. en ram eller en skuggad bakgrund – använd `SdtAppearanceTags`‑enumerationen:

```java
// Insert a plain‑text control with a bounding box appearance
StructuredDocumentTag sdtBox = builder.insertStructuredDocumentTag(
        StructuredDocumentTagType.PLAIN_TEXT, SdtAppearanceTags.BOUNDING_BOX);
sdtBox.setTitle("OrderNumber");
sdtBox.setPlaceholderName("Enter order #");
```

Du kan upprepa mönstret **add text after control** för varje tagg du infogar:

```java
builder.writeln("First line after first tag");
builder.writeln("Second line after second tag");
```

## Steg 5: Hantera flera kontroller och återanvända byggaren

När du genererar formulär behöver du ofta flera kontroller. Samma `DocumentBuilder`‑instans kan infoga många taggar sekventiellt:

```java
String[] titles = {"FirstName", "LastName", "Email"};
for (String title : titles) {
    StructuredDocumentTag tag = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, SdtAppearanceTags.DEFAULT);
    tag.setTitle(title);
    tag.setPlaceholderName("Enter " + title.toLowerCase());
    builder.writeln(" "); // Add a space so the next tag starts on a new line
}
builder.writeln("All fields added above.");
```

Loopen visar hur du **save docx with DocumentBuilder** efter en batch av **add text after control**‑operationer, vilket håller koden koncis.

## Kantfall och felsökning

| Situation | Vad du bör hålla utkik efter | Rekommenderad åtgärd |
|-----------|------------------------------|----------------------|
| **Missing output directory** | `doc.save` kastar `FileNotFoundException` | Se till att katalogen finns (`new File("output").mkdirs();`) innan du anropar `save`. |
| **Control appears empty in Word** | Platshållaren visas inte | Verifiera att du sätter `setPlaceholderName` **after** att taggen har infogats. |
| **License not loaded** | Vattenstämpeln “Aspose.Words Evaluation” visas | Ladda en giltig licensfil som visas i Steg 2. |
| **Unicode characters are corrupted** | Icke‑ASCII‑text visas som � | Spara dokumentet med `SaveFormat.DOCX` (standard) och säkerställ att dina källfiler är UTF‑8‑kodade. |

## Fullt fungerande exempel (klar att kopiera‑klistra in)

```java
package com.example.docx;

import com.aspose.words.*;

import java.io.File;

public class DocxBuilderDemo {

    public static void main(String[] args) throws Exception {
        // Optional: load license to remove evaluation watermark
        // License license = new License();
        // license.setLicense("Aspose.Words.Java.lic");

        // Ensure the output folder exists
        File outDir = new File("output");
        if (!outDir.exists()) outDir.mkdirs();

        // Build the document
        buildDocument(outDir.getAbsolutePath() + "/SDT.docx");
    }

    private static void buildDocument(String outputPath) throws Exception {
        // 1️⃣ Create a new document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a plain‑text Structured Document Tag (SDT)
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, SdtAppearanceTags.DEFAULT);
        sdt.setTitle("CustomerName");
        sdt.setPlaceholderName("Enter name");

        // 3️⃣ Add regular content after the SDT – this satisfies **add text after control**
        builder.writeln("After the tag");

        // 4️⃣ Save the resulting document – this is the core **save docx with DocumentBuilder** step
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Att köra den här klassen producerar samma `SDT.docx`‑fil som beskrivits tidigare.

---

## Slutsats

Du vet nu hur du **save docx with DocumentBuilder**, **insert plain text control** och **add text after control** med Aspose.Words för Java. Det kompletta kodexemplet demonstrerar projektuppsättning, kontrollskapande, innehållsinsättning och fil‑sparande i ett enda, självständigt arbetsflöde.

Från och med nu kan du:

* Experimentera med andra `StructuredDocumentTagType`‑värden (t.ex. `RICH_TEXT` eller `DATE`).  
* Kombinera flera kontroller för att bygga komplexa formulär.  
* Applicera anpassad styling på de omgivande styckena för ett polerat utseende.

Känn dig fri att anpassa mönstret för dina egna dokument‑genereringsbehov, och dela dina resultat i kommentarerna eller på GitHub. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger vidare på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man skapar formulärfält och lägger till innehåll med DocumentBuilder i Aspose.Words för Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Spara docx som pdf med Java – Komplett steg‑för‑steg‑guide](/words/english/java/document-conversion-and-export/save-docx-as-pdf-with-java-complete-step-by-step-guide/)
- [Spara docx som markdown i Java – Komplett steg‑för‑steg‑guide](/words/english/java/document-conversion-and-export/save-docx-as-markdown-in-java-complete-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}