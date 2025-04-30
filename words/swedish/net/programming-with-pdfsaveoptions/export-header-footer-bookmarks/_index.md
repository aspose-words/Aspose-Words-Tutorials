---
"description": "Lär dig hur du exporterar bokmärken för sidhuvud och sidfot från ett Word-dokument till PDF med hjälp av Aspose.Words för .NET med vår steg-för-steg-guide."
"linktitle": "Exportera Word-dokumentets sidhuvud, sidfot, bokmärken till PDF-dokument"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Exportera Word-dokumentets sidhuvud, sidfot, bokmärken till PDF-dokument"
"url": "/sv/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exportera Word-dokumentets sidhuvud, sidfot, bokmärken till PDF-dokument

## Introduktion

Att konvertera Word-dokument till PDF är en vanlig uppgift, särskilt när du vill dela eller arkivera dokument samtidigt som du behåller deras formatering. Ibland innehåller dessa dokument viktiga bokmärken i sidhuvuden och sidfoten. I den här handledningen går vi igenom processen att exportera dessa bokmärken från ett Word-dokument till en PDF med hjälp av Aspose.Words för .NET.

## Förkunskapskrav

Innan vi dyker in, se till att du har följande:

- Aspose.Words för .NET: Du måste ha Aspose.Words för .NET installerat. Du kan ladda ner det från [här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Konfigurera din utvecklingsmiljö. Du kan använda Visual Studio eller någon annan .NET-kompatibel IDE.
- Grundläggande kunskaper i C#: Bekantskap med C#-programmering krävs för att kunna följa kodexemplen.

## Importera namnrymder

Först och främst måste du importera de nödvändiga namnrymderna i ditt C#-projekt. Lägg till dessa rader högst upp i din kodfil:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Låt oss dela upp processen i enkla steg.

## Steg 1: Initiera dokumentet

Det första steget är att ladda ditt Word-dokument. Så här gör du:

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

I det här steget anger du helt enkelt sökvägen till din dokumentkatalog och laddar Word-dokumentet.

## Steg 2: Konfigurera PDF-sparalternativ

Därefter måste du konfigurera alternativen för att spara PDF-filen för att säkerställa att bokmärken i sidhuvuden och sidfoten exporteras korrekt.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

Här håller vi på att sätta upp `PdfSaveOptions`Den `DefaultBookmarksOutlineLevel` egenskapen anger konturnivån för bokmärken, och `HeaderFooterBookmarksExportMode` Egenskapen säkerställer att endast den första förekomsten av bokmärken i sidhuvuden och sidfötter exporteras.

## Steg 3: Spara dokumentet som PDF

Slutligen, spara ditt dokument som en PDF med de konfigurerade alternativen.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

I det här steget sparar du dokumentet till den angivna sökvägen med de alternativ du har konfigurerat.

## Slutsats

Och där har du det! Genom att följa dessa steg kan du enkelt exportera bokmärken från sidhuvuden och sidfoten i ett Word-dokument till en PDF med hjälp av Aspose.Words för .NET. Den här metoden säkerställer att viktiga navigeringshjälpmedel i ditt dokument bevaras i PDF-format, vilket gör det enklare för läsare att navigera genom dokumentet.

## Vanliga frågor

### Kan jag exportera alla bokmärken från Word-dokumentet till PDF?

Ja, det kan du. I `PdfSaveOptions`, kan du justera inställningarna så att alla bokmärken inkluderas om det behövs.

### Vad händer om jag vill exportera bokmärken från dokumentets brödtext även?

Du kan konfigurera `OutlieOptions` in `PdfSaveOptions` för att inkludera bokmärken från dokumentets brödtext.

### Är det möjligt att anpassa bokmärkesnivåerna i PDF-filen?

Absolut! Du kan anpassa `DefaultBookmarksOutlineLevel` egenskap för att ange olika konturnivåer för dina bokmärken.

### Hur hanterar jag dokument utan bokmärken?

Om ditt dokument inte har några bokmärken genereras PDF-filen utan bokmärkeskontur. Se till att ditt dokument innehåller bokmärken om du behöver dem i PDF-filen.

### Kan jag använda den här metoden för andra dokumenttyper som DOCX eller RTF?

Ja, Aspose.Words för .NET stöder olika dokumenttyper, inklusive DOCX, RTF och andra.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}