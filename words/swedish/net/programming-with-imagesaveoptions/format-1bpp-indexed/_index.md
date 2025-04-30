---
"description": "Lär dig hur du konverterar ett Word-dokument till en 1Bpp indexerad bild med hjälp av Aspose.Words för .NET. Följ vår steg-för-steg-guide för enkel konvertering."
"linktitle": "Format 1Bpp Indexerad"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Format 1Bpp Indexerad"
"url": "/sv/net/programming-with-imagesaveoptions/format-1bpp-indexed/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Format 1Bpp Indexerad

## Introduktion

Har du någonsin undrat hur man sparar ett Word-dokument som en svartvit bild med bara några rader kod? Då har du tur! Idag dyker vi in i ett smart litet knep med Aspose.Words för .NET som låter dig konvertera dina dokument till 1Bpp indexerade bilder. Detta format är perfekt för vissa typer av digital arkivering, utskrift eller när du behöver spara utrymme. Vi kommer att bryta ner varje steg för att göra det hur enkelt som helst. Redo att komma igång? Nu kör vi!

## Förkunskapskrav

Innan vi smutsar ner händerna finns det några saker du behöver ha på plats:

- Aspose.Words för .NET: Se till att du har biblioteket installerat. Du kan [ladda ner den här](https://releases.aspose.com/words/net/).
- .NET-utvecklingsmiljö: Visual Studio är ett bra alternativ, men du kan använda vilken miljö du är bekväm med.
- Grundläggande kunskaper i C#: Oroa dig inte, vi ska hålla det enkelt, men lite förtrogenhet med C# hjälper.
- Ett Word-dokument: Ha ett exempel på ett Word-dokument redo att konverteras.

## Importera namnrymder

Först och främst måste vi importera de nödvändiga namnrymderna. Detta är avgörande eftersom det låter oss komma åt de klasser och metoder vi behöver från Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 1: Konfigurera din dokumentkatalog

Du måste ange sökvägen till din dokumentkatalog. Det är här ditt Word-dokument lagras och där den konverterade bilden kommer att sparas.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Ladda Word-dokumentet

Nu ska vi ladda Word-dokumentet till en Aspose.Words-fil. `Document` objekt. Det här objektet representerar din Word-fil och låter dig manipulera den.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Steg 3: Konfigurera alternativ för att spara bilder

Nästa steg är att ställa in `ImageSaveOptions`Det är här magin händer. Vi konfigurerar den för att spara bilden i PNG-format med 1Bpp indexerat färgläge.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png: Detta anger att vi vill spara dokumentet som en PNG-bild.
- PageSet(1): Detta indikerar att vi bara konverterar den första sidan.
- ImageColorMode.BlackAndWhite: Detta ställer in bilden till svartvitt.
- ImagePixelFormat.Format1bppIndexed: Detta ställer in bildformatet till 1Bpp indexerat.

## Steg 4: Spara dokumentet som en bild

Slutligen sparar vi dokumentet som en bild med hjälp av `Save` metod för `Document` objekt.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## Slutsats

Och där har du det! Med bara några få rader kod har du förvandlat ditt Word-dokument till en indexerad bild på 1Bpp med hjälp av Aspose.Words för .NET. Den här metoden är otroligt användbar för att skapa bilder med hög kontrast och ett utrymmeseffektivt format från dina dokument. Nu kan du enkelt integrera detta i dina projekt och arbetsflöden. Lycka till med kodningen!

## Vanliga frågor

### Vad är en 1Bpp indexerad bild?
En indexerad bild på 1 Bpp (1 bit per pixel) är ett svartvitt bildformat där varje pixel representeras av en enda bit, antingen 0 eller 1. Detta format är mycket utrymmeseffektivt.

### Kan jag konvertera flera sidor i ett Word-dokument samtidigt?
Ja, det kan du. Ändra `PageSet` egendom i `ImageSaveOptions` att inkludera flera sidor eller hela dokumentet.

### Behöver jag en licens för att använda Aspose.Words för .NET?
Ja, Aspose.Words för .NET kräver en licens för full funktionalitet. Du kan få en [tillfällig licens här](https://purchase.aspose.com/temporary-license/).

### Vilka andra bildformat kan jag konvertera mitt Word-dokument till?
Aspose.Words stöder olika bildformat inklusive JPEG, BMP och TIFF. Ändra helt enkelt `SaveFormat` i `ImageSaveOptions`.

### Var kan jag hitta mer dokumentation om Aspose.Words för .NET?
Du kan hitta detaljerad dokumentation på [Dokumentationssida för Aspose.Words för .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}