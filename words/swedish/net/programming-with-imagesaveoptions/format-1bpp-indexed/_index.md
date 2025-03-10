---
title: Format 1Bpp Indexerad
linktitle: Format 1Bpp Indexerad
second_title: Aspose.Words Document Processing API
description: Lär dig hur du konverterar ett Word-dokument till en indexerad bild på 1 Bpp med Aspose.Words för .NET. Följ vår steg-för-steg-guide för enkel konvertering.
weight: 10
url: /sv/net/programming-with-imagesaveoptions/format-1bpp-indexed/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Format 1Bpp Indexerad

## Introduktion

Har du någonsin undrat hur man sparar ett Word-dokument som en svartvit bild med bara några rader kod? Nåväl, du har tur! Idag dyker vi in i ett snyggt litet trick med Aspose.Words för .NET som låter dig konvertera dina dokument till 1Bpp indexerade bilder. Det här formatet är perfekt för vissa typer av digital arkivering, utskrift eller när du behöver spara utrymme. Vi kommer att dela upp varje steg för att göra det så enkelt som en plätt. Redo att börja? Låt oss dyka in!

## Förutsättningar

Innan vi smutsar ner händerna är det några saker du måste ha på plats:

-  Aspose.Words för .NET: Se till att du har biblioteket installerat. Du kan[ladda ner den här](https://releases.aspose.com/words/net/).
- .NET-utvecklingsmiljö: Visual Studio är ett bra alternativ, men du kan använda vilken miljö du är bekväm med.
- Grundläggande kunskaper om C#: Oroa dig inte, vi ska hålla det enkelt, men lite bekantskap med C# kommer att hjälpa.
- Ett Word-dokument: Ha ett exempel på Word-dokument redo att konverteras.

## Importera namnområden

Först och främst måste vi importera de nödvändiga namnrymden. Detta är avgörande eftersom det tillåter oss att komma åt de klasser och metoder vi behöver från Aspose.Words.

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

 Låt oss nu ladda Word-dokumentet i en Aspose.Words`Document` objekt. Detta objekt representerar din Word-fil och låter dig manipulera den.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Steg 3: Konfigurera bildsparalternativ

 Därefter måste vi ställa in`ImageSaveOptions`Det är här magin händer. Vi konfigurerar den för att spara bilden i PNG-format med 1Bpp indexerat färgläge.

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

 Slutligen sparar vi dokumentet som en bild med hjälp av`Save` metod för`Document` objekt.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## Slutsats

Och där har du det! Med bara några rader kod har du förvandlat ditt Word-dokument till en indexerad bild på 1 Bpp med Aspose.Words för .NET. Den här metoden är otroligt användbar för att skapa utrymmeseffektiva bilder med hög kontrast från dina dokument. Nu kan du enkelt integrera detta i dina projekt och arbetsflöden. Glad kodning!

## FAQ's

### Vad är en 1Bpp indexerad bild?
En 1Bpp (1 bit per pixel) indexerad bild är ett svartvitt bildformat där varje pixel representeras av en enda bit, antingen 0 eller 1. Detta format är mycket utrymmeseffektivt.

### Kan jag konvertera flera sidor i ett Word-dokument samtidigt?
 Ja, det kan du. Ändra`PageSet` egendom i`ImageSaveOptions` för att inkludera flera sidor eller hela dokumentet.

### Behöver jag en licens för att använda Aspose.Words för .NET?
 Ja, Aspose.Words för .NET kräver en licens för full funktionalitet. Du kan få en[tillfällig licens här](https://purchase.aspose.com/temporary-license/).

### Vilka andra bildformat kan jag konvertera mitt Word-dokument till?
 Aspose.Words stöder olika bildformat inklusive JPEG, BMP och TIFF. Ändra helt enkelt`SaveFormat` i`ImageSaveOptions`.

### Var kan jag hitta mer dokumentation om Aspose.Words för .NET?
 Du kan hitta detaljerad dokumentation på[Aspose.Words för .NET dokumentationssida](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
