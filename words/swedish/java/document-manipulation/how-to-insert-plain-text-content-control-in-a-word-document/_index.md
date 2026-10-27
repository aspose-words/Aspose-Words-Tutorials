---
category: general
date: 2026-10-26
description: Lär dig att infoga en enkeltext‑innehållskontroll med Aspose.Words i
  C#. Steg‑för‑steg‑guide som täcker StructuredDocumentTag, titlar och tagg‑ID:n.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: sv
lastmod: 2026-10-26
og_description: Infoga en vanlig textinnehållskontroll med Aspose.Words i C#. Följ
  den här guiden för att lägga till titlar, tagg‑ID:n och anpassa utseendet.
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: Infoga en enkel textinnehållskontroll i Word med C# – komplett guide
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man infogar en enkeltextinnehållskontroll i ett Word‑dokument med C#
url: /sv/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga innehållskontroll för vanlig text i ett Word‑dokument med C#

Om du behöver **infoga en innehållskontroll för vanlig text** i en Word‑fil visar den här handledningen exakt hur du gör det med Aspose.Words för .NET. Oavsett om du bygger en dokumentgenereringstjänst eller automatiserar formulärskapande, låter stegen nedan dig lägga till ett återanvändbart, redigerbart område som slutanvändare kan fylla i.

Du kommer att lära dig hur du skapar ett `Document`, använder `DocumentBuilder` för att placera en Structured Document Tag (SDT) för vanlig text, sätter en vänlig titel och tilldelar en unik tag‑identifierare. Guiden förklarar också vanliga variationer – såsom att ändra utseendet eller nästla kontroller – så att du kan anpassa lösningen till vilket projekt som helst.

## Förutsättningar

Innan du börjar, se till att du har:

- .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.6+)
- En giltig Aspose.Words för .NET‑licens (eller en gratis utvärderingsnyckel)
- Visual Studio 2022 eller någon C#‑kompatibel IDE
- Grundläggande kunskap om C#‑syntax

> **Pro tip:** Om du använder den fria utvärderingen, kom ihåg att den genererade dokumentfilen kommer att innehålla ett vattenmärke. En licensierad version tar bort det automatiskt.

## Så här infogar du en innehållskontroll för vanlig text med Aspose.Words

Kärnan i lösningen är en trestegsprocess:

1. **Skapa ett `Document` och en `DocumentBuilder`.**  
2. **Infoga en Structured Document Tag (SDT) för vanlig text med standardutseende.**  
3. **Tilldela en titel och en tag‑identifierare till SDT:n.**  

Varje steg förklaras nedan, med komplett körbar kod.

### Steg 1: Initiera dokumentet och byggaren

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representerar hela Word‑filen, medan `DocumentBuilder` tillhandahåller metoder som `InsertParagraph`, `InsertImage` och, avgörande för den här handledningen, `InsertStructuredDocumentTag`. Att initiera dem först ger dig en canvas att placera **innehållskontrollen för vanlig text** på.

### Steg 2: Infoga innehållskontrollen för vanlig text (SDT)

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` talar om för Aspose.Words att skapa en **innehållskontroll för vanlig text**, som beter sig som en enkel textruta som användare kan redigera. `SdtAppearance.Default` renderar kontrollen med en subtil bakgrund, vilket gör det tydligt i dokumentet att området är redigerbart.

> **Varför använda `SdtAppearance.Default`?**  
> Standardutseendet är den mest universellt kompatibla stilen över Word‑versioner. Om du vill ha ett utan kantlinjer kan du senare byta till `SdtAppearance.Hidden`.

### Steg 3: Sätt en titel och en tag‑identifierare

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Title** (`sdt.Title`) visas i Word’s *Content Controls*‑panel och hjälper slutanvändare att förstå fältets syfte.  
- **Tag** (`sdt.Tag`) är en utvecklar‑orienterad identifierare som du senare kan söka efter via `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
- **PlaceholderName** ger gråmarkerad vägledningstext, vilket förbättrar användarupplevelsen.

Kodsnutten ovan bildar ett självständigt program som du kan kompilera och köra. Efter körning kommer `output.docx` att innehålla en enda innehållskontroll för vanlig text med titeln *MyTag* och taggen *TagId*.

![Diagram som visar infogning av innehållskontroll för vanlig text i ett Word‑dokument](image.png){alt="infoga innehållskontroll för vanlig text"}

## Förstå StructuredDocumentTag (SDT) och dess egenskaper

En **Structured Document Tag** (SDT) är den underliggande objektmodellen för Word‑innehållskontroller. De mest relevanta egenskaperna för att infoga en kontroll för vanlig text är:

| Egenskap | Syfte | Vanliga värden |
|----------|-------|----------------|
| `SdtType` | Bestämmer kontrolltyp (vanlig text, rik text, bild osv.) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | Visuell stil för kontrollen | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | Mänskligt läsbar namn som visas i *Content Controls*-panelen | Valfri kort sträng |
| `Tag` | Maskinläsbar identifierare som används i kod | Alfanumerisk sträng |
| `PlaceholderName` | Text som visas när kontrollen är tom | Anpassad hint‑text |

När du sätter `SdtType.PlainText` begränsar Word innehållet till vanliga tecken och förhindrar rik formatering. Detta gör kontrollen idealisk för enkla formulärfält som *Namn*, *E‑post* eller *Telefonnummer*.

### Variationer du kan behöva

| Scenario | Kodändring |
|----------|------------|
| **Ingen visuell skuggning** (utan kantlinje) | Använd `SdtAppearance.Hidden` istället för `Default`. |
| **Skrivskyddat fält** | Efter infogning, sätt `sdt.LockContentControl = true`. |
| **Förifylla med data** | Sätt `sdt.Text = "John Doe";` efter att taggen skapats. |
| **Flera kontroller i en tabell** | Infoga SDT:n i en tabellcell med `builder.InsertCell();` innan anropet `InsertStructuredDocumentTag`. |

## Vanliga fallgropar och hur du undviker dem

1. **Glömmer att sätta en titel** – Word skapar fortfarande kontrollen, men användarna ser ingen meningsfull beskrivning i *Content Controls*-panelen. Tilldela alltid `sdt.Title`.  
2. **Använder fel `SdtType`** – Om du behöver vanlig text men av misstag väljer `RichText`, kommer kontrollen att tillåta formatering, vilket kan bryta efterföljande bearbetning. Dubbelkolla enum‑värdet.  
3. **Sparar till en skrivskyddad mapp** – Anropet `doc.Save` kastar ett `UnauthorizedAccessException`. Säkerställ att målkatalogen är skrivbar eller använd `Path.GetTempPath()` för testning.  
4. **Licens ej tillämpad** – Utan en giltig licens innehåller det genererade dokumentet ett utvärderingsvattenmärke. Applicera licensen tidigt i ditt program:  

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## Fullt, körbart exempel

Nedan är hela programmet, redo att kopieras och klistras in i ett nytt konsolprojekt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Förväntad output:** När du öppnar `output.docx` i Microsoft Word visas en textrad *“Please fill in the following field:”* följt av ett ljusgrått inramat område märkt *MyTag*. Platshållaren *Enter your text here* visas i ljusgrått tills användaren skriver.

## Slutsats

Du vet nu hur du **infogar en innehållskontroll för vanlig text** i ett Word‑dokument med Aspose.Words för .NET. Handledningen täckte initiering av ett `Document`, infogning av en `StructuredDocumentTag` av typen `PlainText` och anpassning av dess titel, tag och platshållare. Genom att förstå `SdtAppearance`‑alternativen och vanliga fallgropar kan du tryggt bygga formulär, mallar och automatiserade rapporter som förlitar sig på redigerbara innehållskontroller.

### Vad är nästa steg?

- Utforska andra SDT‑typer såsom `RichText` eller `ComboBox` för rullgardinsmenyer.  
- Kombinera flera innehållskontroller i tabeller eller upprepa dem med `RepeatingSection`.  
- Använd `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` för att läsa eller ändra kontrollvärden programatiskt.

Känn dig fri att experimentera med variationerna som visades tidigare och integrera mönstret i dina större dokument‑genereringspipeline. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [How to create content control in C# with Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}