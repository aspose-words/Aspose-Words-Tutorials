---
title: Exportera Word-dokument sidfotsbokmärken till PDF-dokument
linktitle: Exportera Word-dokument sidfotsbokmärken till PDF-dokument
second_title: Aspose.Words Document Processing API
description: Lär dig hur du exporterar sidhuvuden och sidfotsbokmärken från ett Word-dokument till PDF med Aspose.Words för .NET med vår steg-för-steg-guide.
weight: 10
url: /sv/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exportera Word-dokument sidfotsbokmärken till PDF-dokument

## Introduktion

Att konvertera Word-dokument till PDF är en vanlig uppgift, särskilt när du vill dela eller arkivera dokument samtidigt som formateringen bevaras. Ibland innehåller dessa dokument viktiga bokmärken i sidhuvuden och sidfötter. I den här handledningen går vi igenom processen att exportera dessa bokmärken från ett Word-dokument till en PDF med Aspose.Words för .NET.

## Förutsättningar

Innan vi dyker in, se till att du har följande:

- Aspose.Words för .NET: Du måste ha Aspose.Words för .NET installerat. Du kan ladda ner den från[här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Ställ in din utvecklingsmiljö. Du kan använda Visual Studio eller någon annan .NET-kompatibel IDE.
- Grundläggande kunskaper i C#: Förtrogenhet med C#-programmering krävs för att följa med kodexemplen.

## Importera namnområden

Först och främst måste du importera de nödvändiga namnrymden i ditt C#-projekt. Lägg till dessa rader överst i din kodfil:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Låt oss dela upp processen i steg som är lätta att följa.

## Steg 1: Initiera dokumentet

Det första steget är att ladda ditt Word-dokument. Så här kan du göra det:

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

I det här steget anger du helt enkelt sökvägen till din dokumentkatalog och laddar Word-dokumentet.

## Steg 2: Konfigurera PDF-sparalternativ

Därefter måste du konfigurera PDF-sparalternativen för att säkerställa att bokmärken i sidhuvuden och sidfötter exporteras korrekt.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

 Här sätter vi upp`PdfSaveOptions` . De`DefaultBookmarksOutlineLevel` egenskapen ställer in konturnivån för bokmärken och`HeaderFooterBookmarksExportMode` egenskapen säkerställer att endast den första förekomsten av bokmärken i sidhuvuden och sidfötter exporteras.

## Steg 3: Spara dokumentet som PDF

Slutligen, spara ditt dokument som en PDF med de konfigurerade alternativen.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

I det här steget sparar du dokumentet till den angivna sökvägen med de alternativ du har konfigurerat.

## Slutsats

Och där har du det! Genom att följa dessa steg kan du enkelt exportera bokmärken från sidhuvuden och sidfötter i ett Word-dokument till en PDF med Aspose.Words för .NET. Denna metod säkerställer att viktiga navigeringshjälpmedel i ditt dokument bevaras i PDF-format, vilket gör det lättare för läsare att navigera genom ditt dokument.

## FAQ's

### Kan jag exportera alla bokmärken från Word-dokumentet till PDF?

 Ja, det kan du. I den`PdfSaveOptions`, kan du justera inställningarna för att inkludera alla bokmärken om det behövs.

### Vad händer om jag också vill exportera bokmärken från dokumentets brödtext?

 Du kan konfigurera`OutlineOptions` i`PdfSaveOptions` för att inkludera bokmärken från dokumentets brödtext.

### Är det möjligt att anpassa bokmärkesnivåerna i PDF-filen?

 Absolut! Du kan anpassa`DefaultBookmarksOutlineLevel` egenskap för att ställa in olika konturnivåer för dina bokmärken.

### Hur hanterar jag dokument utan bokmärken?

Om ditt dokument inte har några bokmärken kommer PDF:en att skapas utan bokmärkeskonturer. Se till att ditt dokument innehåller bokmärken om du behöver dem i PDF:en.

### Kan jag använda den här metoden för andra dokumenttyper som DOCX eller RTF?

Ja, Aspose.Words för .NET stöder olika dokumenttyper, inklusive DOCX, RTF och andra.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
