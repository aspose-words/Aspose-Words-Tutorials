---
"description": "Lär dig hur du lägger till och anpassar sidhuvuden och sidfot i Word-dokument med Aspose.Words för .NET. Den här steg-för-steg-guiden säkerställer professionell dokumentformatering."
"linktitle": "Skapa sidhuvud/sidfot"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Skapa sidhuvud/sidfot"
"url": "/sv/net/working-with-headers-and-footers/create-header-footer/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Skapa sidhuvud/sidfot

## Introduktion

Att lägga till sidhuvuden och sidfot i dina dokument kan förbättra deras professionalism och läsbarhet. Med Aspose.Words för .NET kan du enkelt skapa och anpassa sidhuvuden och sidfot för dina Word-dokument. I den här handledningen guidar vi dig genom processen steg för steg, så att du kan implementera dessa funktioner sömlöst.

## Förkunskapskrav

Innan du börjar, se till att du har följande:

- Aspose.Words för .NET: Ladda ner och installera från [nedladdningslänk](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Till exempel Visual Studio, för att skriva och köra din kod.
- Grundläggande kunskaper i C#: Förståelse för C# och .NET framework.
- Exempeldokument: Ett exempeldokument för att tillämpa sidhuvuden och sidfoten, eller skapa ett nytt enligt handledningen.

## Importera namnrymder

Först måste du importera de namnrymder som behövs för att komma åt Aspose.Words-klasserna och metoderna.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## Steg 1: Definiera dokumentkatalogen

Definiera katalogen där ditt dokument ska sparas. Detta hjälper till att hantera sökvägen effektivt.

```csharp
// Sökvägen till dokumentkatalogen
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## Steg 2: Skapa ett nytt dokument

Skapa ett nytt dokument och en `DocumentBuilder` för att underlätta tillägg av innehåll.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 3: Konfigurera sidinställningar

Ställ in sidinställningarna, inklusive om den första sidan ska ha ett annat sidhuvud/sidfot.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## Steg 4: Lägg till en rubrik på första sidan

Gå till sidhuvudsavsnittet för första sidan och konfigurera sidhuvudtexten.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## Steg 5: Lägg till en primär rubrik

Gå till den primära rubriksektionen och infoga en bild och text.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Infoga en bild i sidhuvudet
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## Steg 6: Lägg till en primär sidfot

Gå till den primära sidfotssektionen och skapa en tabell för att formatera sidfotsinnehållet.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// Lägg till sidnumrering
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## Steg 7: Lägg till innehåll och sidbrytningar

Flytta till slutet av dokumentet, lägg till en sidbrytning och skapa ett nytt avsnitt med andra sidinställningar.

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## Steg 8: Kopiera sidhuvuden och sidfot från föregående avsnitt

Om du vill återanvända sidhuvuden och sidfot från ett tidigare avsnitt, kopiera dem och gör nödvändiga ändringar.

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## Slutsats

Genom att följa dessa steg kan du effektivt lägga till och anpassa sidhuvuden och sidfot i dina Word-dokument med hjälp av Aspose.Words för .NET. Detta förbättrar ditt dokuments utseende och professionalism, vilket gör det mer läsbart och engagerande.

## Vanliga frågor

### Vad är Aspose.Words för .NET?

Aspose.Words för .NET är ett bibliotek som gör det möjligt för utvecklare att skapa, redigera och konvertera Word-dokument programmatiskt inom .NET-applikationer.

### Kan jag lägga till bilder i sidhuvudet eller sidfoten?

Ja, du kan enkelt lägga till bilder i sidhuvudet eller sidfoten med hjälp av `DocumentBuilder.InsertImage` metod.

### Hur ställer jag in olika sidhuvuden och sidfot för första sidan?

Du kan ange olika sidhuvuden och sidfot för första sidan genom att använda `DifferentFirstPageHeaderFooter` egendomen tillhörande `PageSetup` klass.

### Var kan jag hitta mer dokumentation om Aspose.Words?

Du kan hitta omfattande dokumentation om [Aspose.Words API-dokumentationssida](https://reference.aspose.com/words/net/).

### Finns det stöd för Aspose.Words?

Ja, Aspose erbjuder support genom sina [supportforum](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}