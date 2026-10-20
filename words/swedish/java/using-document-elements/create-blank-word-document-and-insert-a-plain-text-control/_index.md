---
category: general
date: 2026-09-18
description: Skapa ett tomt Word‑dokument med C# och ange platshållartext, spara sedan
  dokumentet som docx. Lär dig att infoga en vanlig textkontroll och lägga till ett
  platshållarnamn.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: sv
lastmod: 2026-09-18
og_description: Skapa ett tomt Word-dokument med C#. Ställ in platshållartext, infoga
  en vanlig textkontroll, lägg till ett platshållarnamn och spara dokumentet som docx.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Skapa tomt Word-dokument med platshållartext – C#‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Skapa ett tomt Word‑dokument och infoga en vanlig textkontroll
url: /sv/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ett tomt Word-dokument och infoga en plain‑text‑kontroll

Om du behöver **create blank Word document** programatiskt, visar den här guiden hur du gör det med C#. Du kommer att lära dig att **insert plain text control**, **set placeholder text**, **add placeholder name**, och slutligen **save document as docx**. Stegen är helt självständiga, så du kan kopiera koden till vilket .NET‑projekt som helst och köra det omedelbart.

Att arbeta med Word‑filer kräver ofta en ren utgångspunkt – ett tomt dokument som redan innehåller de kontroller som dina användare ska fylla i. I slutet av den här tutorialen kommer du att ha en `.docx`‑fil som innehåller en plain‑text‑content‑control med en hjälpsam placeholder, följt av vanligt innehåll.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.6+)
- En referens till **Aspose.Words for .NET**‑biblioteket (tillgängligt via NuGet `Install-Package Aspose.Words`)
- Grundläggande kunskap om C#‑konsolapplikationer
- Skrivrättighet till den utdatamapp du anger i `doc.save(...)`

## Vad du kommer att bygga

Det slutgiltiga dokumentet (`SDT.docx`) innehåller:

1. En tom Word‑fil (det **blank Word document** du skapade)
2. En plain‑text‑content‑control (steg **insert plain text control**)
3. Placeholder‑text som visas i kontrollen tills användaren skriver något (steg **set placeholder text**)
4. Ett placeholder‑namn som kan användas för programmatisk åtkomst senare (steg **add placeholder name**)
5. En rad med vanligt text efter kontrollen, som visar att normalt innehåll kan följa

## Steg 1: Skapa ett tomt Word-dokument

Den första operationen är att instansiera ett tomt `Document`‑objekt. Detta objekt representerar ett helt nytt, **blank Word document**, i minnet.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*Varför detta är viktigt:* Ett tomt `Document` ger dig full kontroll över varje element du lägger till, vilket säkerställer att inga dolda stilar eller sektioner stör den content‑control du kommer att infoga senare.

## Steg 2: Initiera en DocumentBuilder

`DocumentBuilder` är hjälparklassen som låter dig skriva in i `Document`. Den spårar den aktuella markörpositionen och tillhandahåller metoder för att infoga alla typer av Word‑objekt.

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta är viktigt:* Att använda en `DocumentBuilder` förenklar processen att lägga till en **plain‑text control** eftersom byggaren vet exakt var insättningen ska ske.

## Steg 3: Infoga plain‑text‑kontroll

Nu lägger vi till en **plain‑text content control** (även känd som Structured Document Tag, eller SDT). Kontrolltypen `StructuredDocumentTagType.PLAIN_TEXT` talar om för Word att behandla innehållet som vanlig text, inte rik formatering.

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*Varför detta är viktigt:* Metoden `InsertStructuredDocumentTag` skapar kontrollen och returnerar en referens (`sdt`) som du kan vidare konfigurera, t.ex. genom att lägga till placeholder‑text eller ett anpassat namn.

## Steg 4: Ställ in placeholder‑text och lägg till placeholder‑namn

Placeholder‑text ger användarna en visuell ledtråd om vad de ska skriva. Steget **add placeholder name** tilldelar en programmatisk identifierare som du kan fråga efter senare med `doc.GetChildNodes` eller liknande API:er.

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*Varför detta är viktigt:* `SetPlaceholderName` styr den grå hint‑texten som visas i content‑control. Att sätta `Tag` (åtgärden **add placeholder name**) låter dig lokalisera kontrollen i dokumentträdet utan att skanna hela filen.

## Steg 5: Lägg till vanligt innehåll efter kontrollen

För att bevisa att dokumentet fortsätter normalt efter kontrollen skriver vi en enkel textrad.

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## Steg 6: Spara dokument som docx

Till sist sparar vi det minnes‑dokumentet till disk. Detta är operationen **save document as docx** som skapar filen du kan öppna i Microsoft Word.

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*Varför detta är viktigt:* Att använda `.docx`‑formatet säkerställer maximal kompatibilitet med moderna versioner av Word, Google Docs och andra Office‑kompatibla verktyg.

## Komplett, körbart exempel

Nedan är hela programmet som du kan kopiera in i ett console‑app‑projekt. Ersätt `YOUR_DIRECTORY` med en faktisk sökväg på din maskin.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Förväntat resultat

- När du öppnar `SDT.docx` i Word visas en tom grå ruta med texten **Enter text…** inuti.
- Rutan är en plain‑text content control; du kan skriva direkt i den.
- Under rutan visas raden **After the tag.** som vanlig stycketext.

Om placeholder‑texten inte visas, kontrollera att du använder en recent version av Aspose.Words (v23.1 eller senare) och att dokumentet öppnas i en Word‑version som stödjer content‑controls (Word 2007+).

## Vanliga variationer och kantfall

| Scenario | Hur du anpassar koden |
|----------|-----------------------|
| **Multiple placeholders** | Call `InsertStructuredDocumentTag` again with a different tag ID and placeholder name. |
| **Rich‑text control** | Use `StructuredDocumentTagType.RichText` instead of `PlainText`. |
| **Setting default text** | After insertion, assign `sdt.Text = "Default value";` – this text replaces the placeholder when the document loads. |
| **Saving to a stream** | Replace `doc.Save(outputPath);` with `doc.Save(stream, SaveFormat.Docx);` to send the file over HTTP. |
| **Changing placeholder color** | Use `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;` (requires `using System.Drawing`). |

## Pro‑tips

- **Reuse the tag ID**: Att hålla taggen (`MyTag`) konsekvent över dokument gör att du kan automatisera datapopulering senare med `doc.Range.Replace` eller `StructuredDocumentTagCollection`.
- **Avoid hard‑coded paths**: Använd `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` för en portabel utdataplats.
- **Performance**: Om du behöver generera tusentals dokument, skapa en enda `Document`‑mall med SDT redan närvarande, och klona den med `doc.Clone()` för varje iteration.

## Slutsats

Du vet nu hur du **create blank Word document**, **insert plain text control**, **set placeholder text**, **add placeholder name**, och **save document as docx** med Aspose.Words för .NET. Detta mönster utgör grunden för att bygga formulärifyllda Word‑mallar, automatiserade rapporter eller någon lösning som kräver användar‑redigerbara placeholders.

Känn dig fri att experimentera med andra kontrolltyper, kombinera flera placeholders, eller integrera denna kod i ett web‑API som returnerar den genererade `.docx`‑filen direkt till anroparna. För nästa steg, utforska **populate a content control with data programmatically** eller **convert the generated Word file to PDF** med Aspose.Words inbyggda konverteringsfunktioner. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Infoga textinmatningsformulärfält i Word-dokument](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Skapa ett Word-dokument med tabell med Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Skapa Word-dokument med sidhuvud och sidfot med Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}