---
category: general
date: 2026-10-20
description: Skapa ett tomt Word‑dokument med Aspose.Words och lär dig hur du använder
  taggar, lägger till innehållskontroll, sätter platshållare och sparar Word‑dokumentet
  som docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to use tags
- add content control
- how to set placeholder
- save word document docx
language: sv
lastmod: 2026-10-20
og_description: Skapa ett tomt Word‑dokument med Aspose.Words. Denna handledning förklarar
  hur man använder taggar, lägger till innehållskontroll, ställer in platshållare
  och sparar Word‑dokumentet som docx.
og_image_alt: Screenshot of a blank Word document containing a content control placeholder
og_title: Skapa ett tomt Word‑dokument och lägg till innehållskontroll – C#‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create blank Word document using Aspose.Words and learn how to use
    tags, add content control, set placeholder, and save Word document docx.
  headline: Create blank Word document and add content control in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Skapa ett tomt Word‑dokument och lägg till innehållskontroll i C#
url: /sv/java/document-manipulation/create-blank-word-document-and-add-content-control-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ett tomt Word‑dokument och lägg till innehållskontroll i C#

Om du behöver **skapa ett tomt Word‑dokument** programatiskt, guidar den här artikeln dig genom hela processen med Aspose.Words för .NET. Du får se **hur man använder taggar**, lägga till en **innehållskontroll**, ange ett **platshållar‑text**, och slutligen **spara Word‑dokumentet docx** till disk.

Handledningen täcker allt du behöver veta för att generera en återanvändbar mall som senare kan fyllas i av en användare eller ett annat system. När du är klar har du en .docx‑fil som innehåller en ren‑text Structured Document Tag (SDT) redo för datainmatning.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 eller senare installerat.  
* Visual Studio 2022 (eller någon annan C#‑IDE du föredrar).  
* Aspose.Words för .NET NuGet‑paket (`Aspose.Words`) tillagt i ditt projekt.  
* Grundläggande kunskap om C#‑syntax.

Dessa saker säkerställer att koden körs utan extra konfiguration.

## Skapa tomt Word‑dokument med Aspose.Words

Det första steget är att instansiera ett `Document`‑objekt, som representerar en tom Word‑fil, samt en `DocumentBuilder` som låter dig redigera dess innehåll.

```csharp
// Step 1: Initialise a new blank document and a builder to edit it
Document doc = new Document();               // Represents an empty .docx file
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` är tomt från början, så du **skapar ett tomt Word‑dokument**. `DocumentBuilder` erbjuder metoder för att infoga text, tabeller och, viktigt för den här handledningen, Structured Document Tags (SDT).

## Hur man använder taggar: infoga en ren‑text Structured Document Tag

Structured Document Tags är den underliggande Word‑funktionen som kallas *innehållskontroller*. För att demonstrera **hur man använder taggar**, infogar vi en ren‑text SDT och ger den en identifierare.

```csharp
// Step 2: Insert a plain‑text Structured Document Tag (SDT) with an ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "TagId");
```

Metoden `InsertStructuredDocumentTag` skapar kontrollen och placerar markören inuti den, redo för vidare konfiguration.

## Lägg till innehållskontroll: ange titel och platshållare

En innehållskontroll blir användbar när du tillhandahåller användarvänlig metadata. Här **lägger vi till innehållskontroll**‑detaljer såsom en titel och en platshållare som visas som grå hint‑text i taggen.

```csharp
// Step 3: Set user‑friendly metadata for the SDT
sdt.Title = "CustomerName";                 // Visible name in the Word UI
sdt.PlaceholderName = "Enter name";         // Placeholder text shown to the user
```

Att sätta `Title` hjälper användare att förstå kontrollens syfte, medan `PlaceholderName` uppfyller kravet **hur man anger platshållare**.

## Infoga det faktiska innehållet som ska visas i SDT‑n

Nu skriver vi standardinnehållet som ska visas när dokumentet öppnas. I många scenarier kan du låta det vara tomt, men att lägga till ett exempelvärde klargör kontrollens beteende.

```csharp
// Step 4: Add the actual content that will appear inside the SDT
builder.Write("John Doe");
```

Anropet `Write` placerar texten i den tidigare skapade SDT‑n, så platshållaren ersätts av det angivna värdet.

## Spara Word‑dokument docx till en fil

Det sista steget är att skriva dokumentet till disk. Detta uppfyller delen **spara word document docx** i handledningen.

```csharp
// Step 5: Save the document to a file
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
    "SDT.docx");
doc.Save(outputPath);
```

Efter körning hittar du `SDT.docx` på ditt skrivbord. När du öppnar filen i Microsoft Word visas en ren‑text innehållskontroll med titeln *CustomerName* och platshållaren “Enter name” (synlig när kontrollen är tom) samt texten “John Doe”.

## Fullt körbart exempel

Nedan är hela programmet som du kan kopiera, klistra in och köra som en konsolapplikation.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialise a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text Structured Document Tag (SDT) with an ID
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, "TagId");

        // Set user‑friendly metadata for the SDT
        sdt.Title = "CustomerName";
        sdt.PlaceholderName = "Enter name";

        // Add the actual content that will appear inside the SDT
        builder.Write("John Doe");

        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "SDT.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

**Förväntad output**

```
Document saved to: C:\Users\<YourUser>\Desktop\SDT.docx
```

När du öppnar `SDT.docx` ser du ett enda stycke med texten “John Doe” inuti en innehållskontroll märkt *CustomerName*. Om du tar bort “John Doe” visas platshållaren “Enter name” i grått, vilket demonstrerar att logiken **hur man anger platshållare** fungerar.

## Vanliga varianter och kantfall

| Scenario | Vad som ändras | Varför det är viktigt |
|----------|----------------|-----------------------|
| **Flera innehållskontroller** | Anropa `InsertStructuredDocumentTag` upprepade gånger med olika ID:n och titlar. | Gör det möjligt att bygga komplexa mallar med många ifyllbara fält. |
| **Rich‑text innehållskontroll** | Använd `StructuredDocumentTagType.RichText` istället för `PlainText`. | Gör det möjligt att använda fetstil, kursiv eller inbäddade bilder i kontrollen. |
| **Upprepande sektion** | Använd `StructuredDocumentTagType.RepeatingSection`. | Användbart för tabeller där rader läggs till dynamiskt. |
| **Spara till en ström** | Ersätt `doc.Save(outputPath)` med `doc.Save(stream, SaveFormat.Docx)`. | Gör att du kan skicka filen via HTTP eller lagra den i en databas. |
| **Kompatibilitet med äldre Word‑versioner** | Spara med `doc.Save(outputPath, SaveFormat.Doc)`. | Genererar en `.doc`‑fil för Word 2003/2007‑kompatibilitet. |

Dessa varianter visar hur du kan utöka det grundläggande **lägg till innehållskontroll**‑mönstret för att möta mer avancerade krav.

## Tips och bästa praxis

* **Proffstips:** Tilldela meningsfulla ID:n (`TagId`) som matchar den datamodell du senare ska binda till. Detta gör programmatisk uppdatering enkel.  
* **Se upp för:** att glömma att sätta `PlaceholderName` när kontrollen ska guida användaren; platshållaren blir då tom, vilket kan vara förvirrande.  
* **Prestanda‑notering:** Att skapa många SDT:n i ett enda dokument är resurssnålt, men om du genererar tusentals kontroller bör du överväga att återanvända en enda `DocumentBuilder`‑instans som i exemplet.

## Slutsats

Du vet nu hur du **skapar ett tomt Word‑dokument**, **hur man använder taggar**, **lägger till innehållskontroll**, **anger platshållare**, och **sparar Word‑dokumentet docx** med Aspose.Words för .NET. Det kompletta exemplet demonstrerar en praktisk mall som kan integreras i större dokument‑genereringspipeline.

Nästa steg kan vara:

* Utforska **lägg till innehållskontroll** för tabeller och bilder.  
* Automatisera ifyllnad av platshållare från en databas.  
* Konvertera den genererade `.docx`‑filen till PDF eller HTML för webbläsarleverans.

Känn dig fri att experimentera med olika taggtyper och platshållartexter för att anpassa dokumentet efter ditt programs behov. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i egna projekt.

- [How to Add Content Control and Create Word Document with Aspose – Complete](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)
- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}