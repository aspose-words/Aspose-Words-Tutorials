---
category: general
date: 2026-11-22
description: Ställ in platshållartext i en Word‑innehållskontroll med C#. Lär dig
  hur du skapar en anpassad tagg, infogar en vanlig textkontroll och lägger till en
  platshållare till taggen med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: sv
lastmod: 2026-11-22
og_description: Ställ in platshållartext i en Word‑innehållskontroll med C#. Den här
  handledningen visar hur du skapar en anpassad tagg, infogar en vanlig textkontroll
  och lägger till en platshållare i taggen för bättre dokumentinteraktivitet.
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: Ange platshållartext i en Word‑innehållskontroll – C#‑guide
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Ange platshållartext i en Word‑innehållskontroll med C#
url: /sv/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ange platshållartext i en Word-innehållskontroll med C#

Om du behöver **ange platshållartext** i ett Word-dokument programatiskt, visar den här guiden exakt hur du gör det. Med Aspose.Words för .NET kan du skapa en anpassad tagg, infoga en ren‑text‑kontroll och lägga till en platshållare till taggen så att dokumentet är redo för användarinmatning.

I den här handledningen kommer du att lära dig hur du **skapar en anpassad tagg**, **infogar en innehållskontroll**, och **lägger till en platshållare till taggen** samtidigt som koden hålls kortfattad och produktionsklar. Inga externa verktyg krävs—bara ett .NET‑projekt och Aspose.Words‑biblioteket.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 SDK eller senare installerat  
* En giltig Aspose.Words för .NET-licens (eller en gratis utvärderingsnyckel)  
* Grundläggande kunskap om C# och Visual Studio (eller någon annan IDE du föredrar)  

Följande avsnitt förutsätter att du har skapat ett konsolprojekt med namnet `WordPlaceholderDemo`.

## Steg 1: Installera Aspose.Words

Add the NuGet package to your project:

```bash
dotnet add package Aspose.Words
```

> **Proffstips:** Använd flaggan `--version` för att låsa paketet till den senaste stabila versionen (t.ex. `Aspose.Words.NET 24.9`).

## Steg 2: Läs in källdokumentet och skapa en `DocumentBuilder`

Det första du gör är att läsa in en befintlig `.docx`‑fil (eller skapa ett nytt tomt dokument) och instansiera en `DocumentBuilder`. Buildern ger dig ett flytande API för att infoga kontroller och text.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Den här koden **lägger grunden** för att infoga en innehållskontroll. `DocumentBuilder` arbetar direkt på `doc`‑objektet, så alla ändringar du gör reflekteras automatiskt.

## Steg 3: Skapa en anpassad tagg (StructuredDocumentTag)

En *anpassad tagg* i Word kallas **StructuredDocumentTag (SDT)**. Du kan tänka dig den som en innehållskontroll som bär en unik identifierare. Att skapa en är kärnan i steget **create custom tag**.

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

`InsertStructuredDocumentTag`‑metoden tar två argument:

1. Typen av kontroll (`PlainText` i detta fall).  
2. En sträng som unikt identifierar taggen (`"MyTag"`).  

Genom att använda en **custom tag** kan du senare hitta eller manipulera kontrollen programatiskt.

## Steg 4: Ange en titel för åtkomlighet

En titel förbättrar åtkomlighet och gör det enklare att hitta kontrollen i Word‑gränssnittet.

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

`Title`‑egenskapen är valfri, men att lägga till den är en bästa praxis när du **add placeholder to tag** för en bättre användarupplevelse.

## Steg 5: Lägg till platshållartext till taggen

Nu kommer huvudmålet: **set placeholder text**. Denna text visas när kontrollen är tom och guidar användaren om vad som ska skrivas.

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

`PlaceholderText`‑egenskapen är exakt vad du behöver för att **add placeholder to tag**. Den fungerar som den grå hint du ser i moderna formulärfält.

## Steg 6: Spara det modifierade dokumentet

Efter att ha konfigurerat kontrollen, skriv dokumentet tillbaka till disk.

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

När du öppnar `output.docx` i Microsoft Word kommer du att se en ren‑text‑innehållskontroll märkt “CustomerName” med platshållaren “Enter name…”. När du klickar i kontrollen tas platshållaren bort, så att användaren kan skriva.

### Förväntat resultat

* En Word‑fil (`output.docx`) som innehåller en enda ren‑text‑innehållskontroll.  
* Kontrollen visar platshållaren “Enter name…” tills användaren skriver något.  
* Kontrollens tagg‑identifierare är `MyTag`, som du senare kan fråga med `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.

## Steg 7: Hur man infogar en innehållskontroll på annat ställe (avancerat)

Om du behöver **how to insert content control** på en specifik plats—t.ex. efter ett visst stycke—använd `MoveTo`‑metoden innan du infogar taggen:

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

Detta kodsnutt demonstrerar **insert plain text control** flera gånger i samma dokument.

## Vanliga fallgropar och hur man undviker dem

| Problem | Varför det händer | Lösning |
|-------|----------------|-----|
| Placeholder not visible | The control already contains text (even a space) | Ensure `sdt.Text` is empty before setting `PlaceholderText`. |
| Tag identifier collision | Re‑using the same tag name (`MyTag`) in the same document | Use unique identifiers for each `StructuredDocumentTag`. |
| License exception | Running without a valid Aspose.Words license | Apply a license file (`license.SetLicense("Aspose.Words.lic")`) at the start of `Main`. |
| Document not saved | Forgetting to call `doc.Save` or using a read‑only path | Verify the output path is writable and call `doc.Save`. |

## Fullt fungerande exempel

Nedan är det kompletta programmet som du kan kopiera‑klistra in i `Program.cs`. Det inkluderar alla steg—**create custom tag**, **how to insert content control**, **add placeholder to tag**, och **insert plain text control**—i ett sammanhängande flöde.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

Kör programmet med `dotnet run`. Efter körning, öppna `output.docx` för att verifiera att båda kontrollerna visar sina respektive platshållare.

## Nästa steg

* **Anpassa utseende** – Använd `sdt.Font` för att ändra teckenstorlek, färg eller stil i kontrollen.  
* **Binda till XML‑data** – Utforska `sdt.XmlMapping` om du behöver att kontrollen mappar  

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Set Placeholder Text in Aspose.Words – Complete C# Guide](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}