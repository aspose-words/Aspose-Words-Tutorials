---
category: general
date: 2026-08-07
description: Hämta fotnotseparator med Aspose.Words för .NET. Lär dig hur du extraherar
  fot- och slutnotseparatorer, inspekterar nodtyper och modifierar dem i C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: sv
lastmod: 2026-08-07
og_description: Hämta fotnotseparator med Aspose.Words för .NET. Denna guide visar
  hur du extraherar fotnot- och slutnotseparatorer, kontrollerar deras nodtyper och
  sparar ändringar.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: hämta fotnotseparator i C# – steg‑för‑steg Aspose.Words‑handledning
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: hämta fotnotseparator i C# – komplett Aspose.Words-guide
url: /sv/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hämta fotnotseparator i C# – komplett Aspose.Words guide

Om du behöver **retrieve footnote separator** från ett Word‑dokument visar den här handledningen exakt hur du gör det med Aspose.Words för .NET. Oavsett om du bygger en dokument‑behandlingstjänst eller rensar upp fotnotformatering, kommer du att se ett komplett, körbart exempel som extraherar både fotnot‑ och slutnotseparatorer.

I den här guiden kommer du att lära dig hur du laddar en `.docx`‑fil, anropar egenskaperna `FootnoteSeparator` och `EndnoteSeparator`, inspekterar de returnerade `Node`‑objekten och eventuellt ersätter separatorlinjen. Ingen extern dokumentation krävs—allt du behöver finns nedan.

## Förutsättningar

* .NET 6.0 eller senare (koden fungerar också på .NET Framework 4.7.2)
* Aspose.Words for .NET NuGet‑paket (version 24.9 eller nyare)
* Ett Word‑dokument som innehåller fotnoter och/eller slutnoter (t.ex. `Footnotes.docx`)

Du kan lägga till Aspose.Words‑paketet med följande CLI‑kommando:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Steg 1: Ställ in projektet och importera namnrymder

Skapa ett nytt konsolprojekt eller lägg till koden i ett befintligt. De nödvändiga `using`‑direktiven listas nedan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Dessa namnrymder ger dig åtkomst till `Document`‑klassen, `Node`‑hierarkin och `NodeType`‑enumerationen som behövs för **retrieve footnote separator**‑operationer.

## Steg 2: Ladda dokumentet som innehåller fotnoter och slutnoter

Den första operationen i alla Aspose.Words‑arbetsflöden är att ladda källfilen. Ersätt platshållarens sökväg med den faktiska platsen för din `.docx`.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

Att ladda filen förbereder det interna nodträdet, vilket är avgörande för **retrieve footnote separator** eftersom separatornoderna finns i det trädet.

## Steg 3: Hämta fotnotseparatornoden

Nu kan du **retrieve footnote separator** genom att komma åt `FootnoteSeparator`‑egenskapen på `Document`‑objektet. Denna nod representerar linjen som separerar fotnoter från huvudtexten.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

`NodeType` kommer att vara `Paragraph` för en standardseparatorlinje. Att känna till nodtypen hjälper dig att avgöra om du behöver ändra separatorn eller ersätta den helt.

## Steg 4: Hämta slutnotseparatornoden

På samma sätt kan du **retrieve endnote separator** med hjälp av `EndnoteSeparator`‑egenskapen. Denna nod separerar slutnoter från huvudinnehållet.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

Båda separatornoderna delar samma `NodeType` (`Paragraph`) i de flesta dokument, men de kan anpassas oberoende.

## Steg 5: Inspektera eller ändra separatorns innehåll (valfritt)

Om du behöver ändra separatorns visuella utseende—t.ex. ersätta en rad streck med en tunn linje—kan du redigera `Paragraph`‑noden direkt. Nedan är ett exempel som ersätter standardseparatortexten med en anpassad sträng.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

Efter att ha ändrat noderna kan du spara dokumentet för att se förändringarna i Word.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Förväntad konsolutmatning

När du kör programmet med den ursprungliga `Footnotes.docx` bör du se något liknande:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

Om du öppnar `Footnotes_Updated.docx` i Microsoft Word kommer fotnot- och slutnotseparatorerna att visa den anpassade text du infogade.

## Vanliga frågor och specialfall

**Vad händer om dokumentet saknar fotnoter?**  
`FootnoteSeparator`‑egenskapen returnerar fortfarande en `Paragraph`‑nod eftersom Word alltid inkluderar en separator‑platshållare. Noden blir tom, så du kan säkert lägga till innehåll eller lämna den som den är.

**Kan jag hämta separatorn för ett specifikt avsnitt?**  
Fotnot- och slutnotseparatorer gäller för hela dokumentet, inte för specifika avsnitt. Om du behöver kontroll på avsnitts‑nivå måste du arbeta med `Section.FootnoteOptions` och `Section.EndnoteOptions` istället för de globala separatornoderna.

**Fungerar detta med .NET Core?**  
Ja. Aspose.Words för .NET är plattformsoberoende, och samma kod körs på Windows, Linux och macOS med .NET 6+.

**Vilken nodtyp kan jag förvänta mig?**  
Både `FootnoteSeparator` och `EndnoteSeparator` returnerar en `Paragraph`‑nod (`NodeType.Paragraph`). Om du stöter på en annan typ kan dokumentet vara korrupt, och du bör ladda om eller validera källfilen.

## Fullständig källkod för snabb kopiering

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

Kopiera koden till en `Program.cs`‑fil, justera filsökvägarna och kör `dotnet run`. Programmet demonstrerar hela **retrieve footnote separator**‑arbetsflödet, från att ladda dokumentet till att spara förändringarna.

## Slutsats

Du vet nu hur du **retrieve footnote separator** och **endnote separator retrieval** med Aspose.Words för .NET, inspekterar deras `document node type` och eventuellt ersätter deras innehåll. Denna teknik låter dig automatisera fotnotformatering, generera anpassade separatorlinjer eller validera dokumentstruktur i vilken C#‑applikation som helst.

Nästa steg kan vara att utforska relaterade ämnen som **C# footnote extraction** för enskilda fotnottexter, eller lära dig hur du **modify footnote reference marks** med `FootnoteOptions`. Båda koncepten bygger direkt på nod‑trädsgrunderna som behandlats här.

Lycka till med kodandet, och känn dig fri att experimentera med olika separatorstilar för att matcha ditt projekts varumärke!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Working With Footnote And Endnote](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}